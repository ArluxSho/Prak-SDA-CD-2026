# ShortestPath - Djisktra Algorithm

## A. Pengenalan Algoritma Djikstra

<img src="image.png" alt="alt text" width="500" />

Algoritma Dijkstra adalah salah satu algoritma paling populer dalam teori graf yang digunakan untuk mencari jalur terpendek (shortest path) dari satu titik awal (source node) ke semua titik lainnya pada sebuah graf yang berbobot (weighted graph). Djikstra menggunakan komponen utama graf seperti pertemuan kemarin yaitu Node/Vertex, Edge, dan Weight.

## B. Cara Kerja Utama

<img src="https://i.sstatic.net/O8Nkm.png" alt="alt text" width="500" />
<img src="https://i.sstatic.net/22e9W.png" alt="alt text" width="500" />

Algoritma Dijkstra menggunakan prinsip Greedy (Tamak). Artinya, di setiap langkahnya, algoritma ini akan selalu memilih Node terdekat yang belum dikunjungi yang memiliki bobot paling kecil saat itu.<br><br>

Secara garis besar, berikut adalah intuisi cara kerjanya:

1. Inisialisasi: Berikan jarak awal $= 0$ untuk Node asal, dan jarak tak terhingga ($\infty$) untuk semua Node lainnya (karena kita belum tahu jalurnya).
2. Pilih yang Terdekat: Lihat semua Node yang belum dikunjungi, lalu pilih Node dengan jarak total terkecil dari Node asal.
3. Pembaruan Jarak (Relaxation): Dari Node yang terpilih, periksa semua Node tetangganya yang belum dikunjungi. Hitung ulang jaraknya. Jika lewat jalur baru ini ternyata lebih dekat daripada jarak yang dicatat sebelumnya, perbarui datanya.
4. Tandai Selesai: Tandai Node yang sudah diperiksa tadi sebagai "Sudah Dikunjungi" agar tidak diproses ulang.
5. Ulangi: Lakukan terus langkah ini sampai semua Node berhasil dikunjungi.

Untuk contoh dan visualisasinya dapat dilihat di [di sini](https://www.geeksforgeeks.org/dijkstras-shortest-path-algorithm-greedy-algo-7/).

## C. Priority Queue pada Dijkstra

Priority Queue adalah struktur data yang selalu mengambil elemen dengan prioritas tertinggi terlebih dahulu. Pada Dijkstra, ```prioritas = jarak terkecil``` jadi node dengan distance paling kecil akan diproses lebih dulu. Tanpa priority queue, progra, akan menjadi lebih lambat karena harus mencari node terkecil secara manual dan membutuhkan scanning ke seluruh node. 

### I. Cara Kerja Priority Queue

Misalnya queue berisi:

```
(B,10)
(C,3)
(D,7)
```

Maka saat poll() dipanggil:

```
(C,3)
```

akan keluar terlebih dahulu karena memiliki jarak terkecil.

### II. Operasi pada Priority Queue

| Operasi   | Fungsi                        |
| --------- | ----------------------------- |
| add()     | menambahkan data              |
| poll()    | mengambil prioritas tertinggi |
| peek()    | melihat elemen teratas        |
| isEmpty() | mengecek queue kosong         |

### III. Implementasi Pirority Queue di Java

```java
PriorityQueue<Node> pq =
        new PriorityQueue<>();
```

Agar bisa dibandingkan, class Node harus menggunakan:

```java
Comparable
```

## D. Struktur Node untuk Dijkstra

```java
class Node implements Comparable<Node> {

    int tujuan;
    int jarak;

    Node(int tujuan, int jarak) {
        this.tujuan = tujuan;
        this.jarak = jarak;
    }

    @Override
    public int compareTo(Node other) {
        return this.jarak - other.jarak;
    }
}
```

Dengan 
```java
return this.jarak - other.jarak;
```
Memiliki arti bahwa node dengan jarak terkecil mendapatkan prioritas yang lebih tinggi atau diutamakan.

## E. Implementasi Dijkstra di Java

```java
import java.util.*;

public class Dijkstra {

    static class Edge {
        int tujuan;
        int bobot;

        Edge(int tujuan, int bobot) {
            this.tujuan = tujuan;
            this.bobot = bobot;
        }
    }

    static class Node
            implements Comparable<Node> {

        int vertex;
        int jarak;

        Node(int vertex, int jarak) {
            this.vertex = vertex;
            this.jarak = jarak;
        }

        @Override
        public int compareTo(Node other) {
            return this.jarak - other.jarak;
        }
    }

    public static void dijkstra(
            List<List<Edge>> graph,
            int source
    ) {

        int V = graph.size();

        int[] distance = new int[V];

        Arrays.fill(distance, Integer.MAX_VALUE);

        distance[source] = 0;

        PriorityQueue<Node> pq =
                new PriorityQueue<>();

        pq.add(new Node(source, 0));

        while (!pq.isEmpty()) {

            Node current = pq.poll();

            int u = current.vertex;

            for (Edge edge : graph.get(u)) {

                int v = edge.tujuan;
                int bobot = edge.bobot;

                if (distance[u] + bobot
                        < distance[v]) {

                    distance[v] =
                            distance[u] + bobot;

                    pq.add(
                        new Node(
                            v,
                            distance[v]
                        )
                    );
                }
            }
        }

        for (int i = 0; i < V; i++) {

            System.out.println(
                "Jarak ke node "
                + i + " = "
                + distance[i]
            );
        }
    }
}
```

## F. Kompleksitas Dijkstra

Dengan Priority Queue

```O((V+E)logV)```

Keterangan:

V = jumlah vertex
E = jumlah edge

## G. Kelebihan dan Kekurangan

Dijkstra memiliki kelebihan:

1. Cepat untuk weighted graph karena sangat efisien untuk graph berbobot positif.
2. Banyak digunakan di dunia nyata, seperti _Google Maps, GPS, Routing jaringan, dan Game pathfinding_.

Namun, Dijkstra memiliki kekurangan:

1. Tidak mendukung bobot negatif karena hasilnya bisa salah.
2. Untuk graph tertentu, algoritma lain seperti ```Bellman-Ford, Floyd-Warshall, dan A*``` lebih optimal untuk digunakan

## H. Referensi
Algoritma Dijkstra
https://www.geeksforgeeks.org/dsa/dijkstras-shortest-path-algorithm-greedy-algo-7/
