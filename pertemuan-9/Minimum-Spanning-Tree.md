# 3. Minimum Spanning Tree (MST)

## 3.1 Konsep Minimum Spanning Tree

Minimum Spanning Tree (MST) adalah salah satu konsep penting pada struktur data graph berbobot (*weighted graph*). MST digunakan untuk mencari sekumpulan sisi (*edge*) yang dapat menghubungkan seluruh simpul (*vertex*) dalam graph dengan total bobot minimum tanpa membentuk siklus (*cycle*).

Konsep ini sering digunakan pada berbagai permasalahan dunia nyata, seperti:

* Pembangunan jaringan listrik dengan biaya kabel paling murah.
* Pemasangan jaringan internet antar kota.
* Jalur distribusi air atau gas.
* Pembuatan jalur jalan dengan biaya minimum.

Misalnya terdapat beberapa kota yang ingin dihubungkan dengan kabel internet:

| Kota | Terhubung ke | Biaya |
| ---- | ------------ | ----- |
| A    | B            | 4     |
| A    | C            | 2     |
| B    | C            | 1     |
| B    | D            | 5     |
| C    | D            | 8     |
| C    | E            | 10    |
| D    | E            | 2     |

Tujuannya adalah memilih jalur-jalur dengan total biaya paling kecil namun seluruh kota tetap saling terhubung.

Pada graph, MST memiliki beberapa karakteristik penting:

* Semua vertex harus terhubung.
* Tidak boleh ada cycle.
* Jumlah edge pada MST selalu `jumlah_vertex - 1`.
* Total bobot edge harus minimum.

Contoh sederhana:

```text
Graph Awal:

A --4-- B
| \      |
2  1     5
|    \   |
C --8-- D
 \      /
   10  2
      E

MST:

A --2-- C
      /
     1
    /
   B --5-- D --2-- E
```

Total biaya MST:

```text
2 + 1 + 5 + 2 = 10
```

---

# 3.2 Algoritma untuk MST

Terdapat dua algoritma utama yang paling sering digunakan untuk mencari MST:

1. Kruskal Algorithm
2. Prim Algorithm

---

# 3.3 Kruskal Algorithm

## 3.3.1 Konsep Kruskal

Algoritma Kruskal bekerja dengan cara:

1. Mengurutkan seluruh edge berdasarkan bobot terkecil.
2. Memilih edge satu per satu dari bobot terkecil.
3. Edge akan dimasukkan ke MST jika tidak membentuk cycle.
4. Proses berhenti ketika jumlah edge MST adalah `vertex - 1`.

Algoritma ini sangat erat hubungannya dengan Disjoint Set karena Disjoint Set digunakan untuk mendeteksi cycle.

---

## 3.3.2 Cara Kerja Kruskal

Misalkan terdapat graph berikut:

| Edge | Bobot |
| ---- | ----- |
| B-C  | 1     |
| A-C  | 2     |
| A-B  | 4     |
| D-E  | 2     |
| B-D  | 5     |
| C-D  | 8     |
| C-E  | 10    |

### Langkah 1 — Urutkan Edge

Urutan edge dari terkecil:

```text
B-C (1)
A-C (2)
D-E (2)
A-B (4)
B-D (5)
C-D (8)
C-E (10)
```

---

### Langkah 2 — Pilih Edge Satu per Satu

#### Ambil B-C (1)

Belum membentuk cycle → ambil.

```text
MST = {B-C}
```

#### Ambil A-C (2)

Belum membentuk cycle → ambil.

```text
MST = {B-C, A-C}
```

#### Ambil D-E (2)

Belum membentuk cycle → ambil.

```text
MST = {B-C, A-C, D-E}
```

#### Ambil A-B (4)

Membentuk cycle:

```text
A → C → B
```

Karena sudah terhubung, edge ini dilewati.

#### Ambil B-D (5)

Belum membentuk cycle → ambil.

```text
MST = {B-C, A-C, D-E, B-D}
```

Jumlah edge sudah `5 - 1 = 4`, maka proses selesai.

---

## 3.3.3 Implementasi Kruskal dengan Disjoint Set

```java
import java.util.*;

class Edge implements Comparable<Edge> {
    String source;
    String destination;
    int weight;

    public Edge(String source, String destination, int weight) {
        this.source = source;
        this.destination = destination;
        this.weight = weight;
    }

    @Override
    public int compareTo(Edge other) {
        return this.weight - other.weight;
    }
}

class DisjointSet {
    private Map<String, String> parent = new HashMap<>();

    public void makeSet(String node) {
        parent.put(node, node);
    }

    public String find(String node) {
        if (!parent.get(node).equals(node)) {
            parent.put(node, find(parent.get(node)));
        }
        return parent.get(node);
    }

    public void union(String a, String b) {
        String rootA = find(a);
        String rootB = find(b);

        if (!rootA.equals(rootB)) {
            parent.put(rootA, rootB);
        }
    }
}

public class KruskalMST {
    public static void main(String[] args) {

        List<Edge> edges = new ArrayList<>();

        edges.add(new Edge("A", "B", 4));
        edges.add(new Edge("A", "C", 2));
        edges.add(new Edge("B", "C", 1));
        edges.add(new Edge("B", "D", 5));
        edges.add(new Edge("C", "D", 8));
        edges.add(new Edge("C", "E", 10));
        edges.add(new Edge("D", "E", 2));

        Collections.sort(edges);

        DisjointSet ds = new DisjointSet();

        String[] nodes = {"A", "B", "C", "D", "E"};

        for (String node : nodes) {
            ds.makeSet(node);
        }

        List<Edge> mst = new ArrayList<>();
        int totalWeight = 0;

        for (Edge edge : edges) {

            String rootSource = ds.find(edge.source);
            String rootDestination = ds.find(edge.destination);

            // Jika belum terhubung, maka ambil edge
            if (!rootSource.equals(rootDestination)) {

                mst.add(edge);
                totalWeight += edge.weight;

                ds.union(edge.source, edge.destination);
            }
        }

        System.out.println("Minimum Spanning Tree:");

        for (Edge edge : mst) {
            System.out.println(
                edge.source + " - " +
                edge.destination + " : " +
                edge.weight
            );
        }

        System.out.println("Total Bobot: " + totalWeight);
    }
}
```

---

# 3.4 Analisis Kruskal Algorithm

## 3.4.1 Kompleksitas Waktu

Kompleksitas utama Kruskal berasal dari proses sorting edge.

Jika:

* V = jumlah vertex
* E = jumlah edge

Maka:

```text
Sorting Edge = O(E log E)
```

Sedangkan operasi Disjoint Set:

```text
Find dan Union = O(α(n))
```

Sehingga total kompleksitas:

```text
O(E log E)
```

Karena proses sorting mendominasi.

---

## 3.4.2 Kelebihan Kruskal

* Mudah diimplementasikan.
* Sangat cocok untuk sparse graph (edge sedikit).
* Efisien jika dikombinasikan dengan Disjoint Set.

---

## 3.4.3 Kekurangan Kruskal

* Harus melakukan sorting edge terlebih dahulu.
* Kurang optimal untuk dense graph (edge sangat banyak).

---

# 3.5 Prim Algorithm

## 3.5.1 Konsep Prim

Berbeda dengan Kruskal yang memilih edge terkecil secara global, Prim bekerja dengan:

1. Memulai dari satu vertex.
2. Memilih edge terkecil yang terhubung ke MST.
3. Menambahkan vertex baru ke MST.
4. Mengulangi proses sampai semua vertex terhubung.

Prim lebih mirip proses “memperluas wilayah”.

---

## 3.5.2 Cara Kerja Prim

Misalkan graph:

```text
A --2-- C
|       |
4       8
|       |
B --5-- D --2-- E
```

### Langkah-langkah

Mulai dari A.

#### Dari A

Pilih edge terkecil:

```text
A-C = 2
```

#### Dari {A, C}

Pilih edge terkecil menuju vertex luar:

```text
A-B = 4
```

#### Dari {A, B, C}

Pilih:

```text
B-D = 5
```

#### Dari {A, B, C, D}

Pilih:

```text
D-E = 2
```

Selesai.

---

# 3.6 Implementasi Prim Algorithm

```java
import java.util.*;

class Edge {
    String destination;
    int weight;

    public Edge(String destination, int weight) {
        this.destination = destination;
        this.weight = weight;
    }
}

public class PrimMST {

    private static Map<String, List<Edge>> graph = new HashMap<>();

    public static void addEdge(String source, String destination, int weight) {

        graph.putIfAbsent(source, new ArrayList<>());
        graph.putIfAbsent(destination, new ArrayList<>());

        graph.get(source).add(new Edge(destination, weight));
        graph.get(destination).add(new Edge(source, weight));
    }

    public static void prim(String start) {

        Set<String> visited = new HashSet<>();

        PriorityQueue<Edge> pq =
            new PriorityQueue<>((a, b) -> a.weight - b.weight);

        visited.add(start);

        pq.addAll(graph.get(start));

        int totalWeight = 0;

        System.out.println("Minimum Spanning Tree:");

        while (!pq.isEmpty()) {

            Edge current = pq.poll();

            if (visited.contains(current.destination)) {
                continue;
            }

            visited.add(current.destination);

            System.out.println(
                "Ke " + current.destination +
                " dengan bobot " + current.weight
            );

            totalWeight += current.weight;

            for (Edge next : graph.get(current.destination)) {

                if (!visited.contains(next.destination)) {
                    pq.offer(next);
                }
            }
        }

        System.out.println("Total Bobot: " + totalWeight);
    }

    public static void main(String[] args) {

        addEdge("A", "B", 4);
        addEdge("A", "C", 2);
        addEdge("B", "C", 1);
        addEdge("B", "D", 5);
        addEdge("C", "D", 8);
        addEdge("D", "E", 2);

        prim("A");
    }
}
```

---

# 3.7 Perbandingan Kruskal dan Prim

| Aspek         | Kruskal                      | Prim                  |
| ------------- | ---------------------------- | --------------------- |
| Pendekatan    | Memilih edge global terkecil | Memperluas vertex     |
| Struktur Data | Disjoint Set                 | Priority Queue        |
| Cocok Untuk   | Sparse graph                 | Dense graph           |
| Deteksi Cycle | Ya                           | Tidak perlu eksplisit |
| Kompleksitas  | O(E log E)                   | O(E log V)            |

---

# 3.8 Hubungan Disjoint Set dengan MST

Disjoint Set sangat penting pada algoritma Kruskal karena digunakan untuk:

* Mengecek apakah dua vertex sudah berada dalam kelompok yang sama.
* Mencegah terbentuknya cycle.
* Menggabungkan kelompok vertex setelah edge dipilih.

Tanpa Disjoint Set, proses pengecekan cycle akan menjadi jauh lebih lambat.

aman tentang MST sangat penting karena konsep ini banyak digunakan pada jaringan komputer, optimasi biaya, routing, dan sistem distribusi modern.
