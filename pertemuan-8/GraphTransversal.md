# Graph Transversal

## 1. Pengertian Graph Transversal

Graph Traversal adalah proses mengunjungi setiap vertex (simpul) dalam sebuah graph secara sistematis berdasarkan aturan tertentu. Traversal digunakan untuk memahami struktur graph, mencari jalur, atau memastikan semua node telah dikunjungi.

Dalam graph, traversal tidak sesederhana seperti pada array atau linked list, karena:

- Graph bisa memiliki banyak jalur
- Bisa terdapat siklus (cycle)
- Tidak selalu semua node saling terhubung

Oleh karena itu, diperlukan algoritma khusus agar proses traversal berjalan dengan benar tanpa mengunjungi node yang sama berulang kali.

## 2. Jenis Graph Transversal

Terdapat dua metode utama dalam traversal graph, yaitu Depth First Search (DFS) dan Breadth First Search (BFS). Kedua metode ini memiliki cara kerja yang berbeda dalam menjelajahi graph.

### 2.1. Depth First Search (DFS)

Depth First Search (DFS) adalah metode traversal yang mengunjungi node dengan cara menelusuri satu jalur sedalam mungkin sebelum kembali (backtracking) untuk menjelajahi jalur lainnya. Artinya, DFS akan:

- Masuk ke satu cabang
- Terus turun sampai tidak ada node lagi
- Kemudian kembali ke node sebelumnya untuk mencari cabang lain

#### Ilustrasi Cara Kerja DFS 

Misalnya terdapat graph seperti berikut:

```
0 → 1 → 2
↓
3
```

Jika traversal dimulai dari node 0, maka urutan DFS bisa menjadi:

```
0 → 1 → 2 → (kembali) → 3
```

#### Langkah-langkah DFS

1. Mulai dari node awal
2. Tandai node sebagai sudah dikunjungi (visited)
3. Kunjungi salah satu tetangga yang belum dikunjungi
4. Ulangi proses tersebut secara rekursif
5. Jika tidak ada tetangga, kembali ke node sebelumnya

Secaea implisit, DFS menggunakan Stack melalui rekursi.

#### Implementasi DFS (Adjacency List - Java)

```Java
import java.util.LinkedList;

class GraphDFS {
    private int V;
    private LinkedList<Integer>[] adj;

    // Constructor
    public GraphDFS(int v) {
        this.V = v;
        adj = new LinkedList[v];

        for (int i = 0; i < v; i++) {
            adj[i] = new LinkedList<>();
        }
    }

    // Menambahkan edge
    public void addEdge(int source, int destination) {
        adj[source].add(destination);

        // Gunakan jika undirected
        // adj[destination].add(source);
    }

    // Fungsi DFS
    public void DFS(int start) {
        boolean[] visited = new boolean[V];
        dfsHelper(start, visited);
    }

    // Fungsi rekursif
    private void dfsHelper(int node, boolean[] visited) {
        visited[node] = true;
        System.out.print(node + " ");

        for (Integer neighbor : adj[node]) {
            if (!visited[neighbor]) {
                dfsHelper(neighbor, visited);
            }
        }
    }
}
```

Dimana: 

- visited[] digunakan untuk menandai node yang sudah dikunjungi agar tidak terjadi loop tak terbatas
- Fungsi dfsHelper() berjalan secara rekursif untuk menjelajahi node
- Setiap node yang dikunjungi langsung ditandai sebelum melanjutkan ke tetangga

#### Kelebihan dan Kekurangan DFS 

Kelebihan:

- Cocok untuk eksplorasi mendalam
- Digunakan pada backtracking dan pencarian solusi

Kekurangan:

- Tidak menjamin jalur terpendek
- Bisa menyebabkan stack overflow pada graph besar

### 2.2. Breadth First Search (BFS)

Breadth First Search (BFS) adalah metode traversal yang mengunjungi node berdasarkan tingkat (level), yaitu semua tetangga dari suatu node dikunjungi terlebih dahulu sebelum melanjutkan ke tingkat berikutnya.

#### Ilustrasi Cara Kerja BFS

Misalnya graph:

```
0 → 1 → 2
↓
3
```

Urutan BFS dari node 0:

```
0 → 1 → 3 → 2
```

#### Langkah-langkah BFS

1. Masukkan node awal ke dalam queue
2. Tandai sebagai visited
3. Ambil node dari queue
4. Masukkan semua tetangga yang belum dikunjungi ke queue
5. Ulangi hingga queue kosong

BFS menggunakan struktur data Queue.

#### Implementasi BFS 

```Java
import java.util.*;

class GraphBFS {
    private int V;
    private LinkedList<Integer>[] adj;

    public GraphBFS(int v) {
        this.V = v;
        adj = new LinkedList[v];

        for (int i = 0; i < v; i++) {
            adj[i] = new LinkedList<>();
        }
    }

    public void addEdge(int source, int destination) {
        adj[source].add(destination);

        // Gunakan jika undirected
        // adj[destination].add(source);
    }

    public void BFS(int start) {
        boolean[] visited = new boolean[V];
        Queue<Integer> queue = new LinkedList<>();

        visited[start] = true;
        queue.add(start);

        while (!queue.isEmpty()) {
            int node = queue.poll();
            System.out.print(node + " ");

            for (Integer neighbor : adj[node]) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    queue.add(neighbor);
                }
            }
        }
    }
}
```

Dimana:

- Queue digunakan untuk menyimpan node yang akan dikunjungi
- Node pertama yang masuk akan diproses lebih dulu (FIFO)
- Node ditandai sebagai visited saat dimasukkan ke queue untuk menghindari duplikasi


#### Kelebihan dan Kekurangan BFS

Kelebihan:

- Menemukan jalur terpendek pada graph tanpa bobot
- Lebih terstruktur

Kekurangan:

- Menggunakan lebih banyak memori dibanding DFS

## 3. Perbandingan Graph Transversal antara DFS dan BFS 

| Aspek         | DFS         | BFS         |
| ------------- | ----------- | ----------- |
| Cara kerja    | Dalam       | Lebar       |
| Struktur      | Stack       | Queue       |
| Shortest path | Tidak       | Ya          |
| Memori        | Lebih hemat | Lebih besar |
| Kompleksitas Waktu |  O(V + E) | O(V + E) |
| Kompleksitas Ruang |  O (V) | O(V) |
