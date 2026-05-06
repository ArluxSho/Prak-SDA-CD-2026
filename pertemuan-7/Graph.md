## Graph

### 1. Pengertian Graph Dasar

Graph adalah struktur data non-linear yang terdiri dari sekumpulan titik yang saling terhubung. Graph digunakan untuk merepresentasikan jaringan di dunia nyata, seperti jaringan jalan raya, pertemanan di media sosial, atau topologi jaringan komputer.<br>

Graph terdiri dari dua komponen utama:

- Vertex (Node/Simpul) : Entitas atau data itu sendiri (biasanya dilambangkan dengan huruf atau angka)
- Edge (Sisi/Garis) : Jalur yang menghubungkan dua buah Vertex.

Berdasarkan Arahnya (Direction), Graph dibagi menjadi dua:

- Undirected Graph (Graph Tak Berarah): Sisi tidak memiliki arah. Jika ada edge antara A dan B, maka A bisa ke B dan B bisa ke A (komunikasi dua arah).
- Directed Graph (Graph Berarah / Digraph): Sisi memiliki arah. Jika ada edge dari A ke B, kita hanya bisa pergi dari A ke B, tidak berlaku sebaliknya kecuali ada edge lain dari B ke A.

### 2. Representasi Graph

Agar Graph dapat diolah oleh program, kita perlu menerjemahkannya ke dalam bentuk struktur data. Ada dua cara paling umum yang digunakan:

#### 2.1 Adjacency Matrix

![geeksforgeeks](https://media.geeksforgeeks.org/wp-content/uploads/20200604170814/add-and-remove-edge-in-adjacency-matrix-representation-initial1.jpg)
referensi: geeksforgeeks.org<br>

Adjacency Matrix merepresentasikan graph menggunakan array 2 dimensi (matriks) berukuran $V$ $x$ $V$, dimana $V$ adalah jumlah vertex. Gampangnya:

- Jika ada edge dari vertex $i$ ke vertex $j$, maka nilai matrix[i][j] = 1.
- Jika tidak ada edge, maka nilainya 0.

- Kelebihan: Sangat cepat untuk mengecek apakah dua vertex saling terhubung, yaitu $O(1)$.<br>
- Kekurangan: Memakan banyak memori, yaitu $O(V^2)$, terutama jika graph-nya "renggang" (sparse graph / sedikit edge).<br>

Terdapat 2 operasi dalam Adjacency Matrix yaitu add dan remove. Berikut implementasi Adjacency Matrix di Java:

```java
// Java program to add and remove edge
// in the adjacency matrix of a graph

class GraphMatrix {

    // Number of vertices
    private int n;

    // Adjacency matrix
    private int[][] g;

    // Constructor
    GraphMatrix(int x)
    {
        this.n = x;
        g = new int[n][n];
    }

    // Function to display adjacency matrix
    public void displayAdjacencyMatrix()
    {
        // Displaying the 2D matrix
        for (int i = 0; i < n; ++i) {
            System.out.println();
            for (int j = 0; j < n; ++j) {
                System.out.print(" " + g[i][j]);
            }
        }
        System.out.println();
    }

    // Function to update adjacency
    // matrix for edge insertion
    public void addEdge(int x, int y)
    {
        // Checks if the vertices exists
        if ((x < 0) || (x >= n)) {
            System.out.println("Vertex " + x + " does not exist!");
            return;
        }
        if ((y < 0) || (y >= n)) {
            System.out.println("Vertex " + y + " does not exist!");
            return;
        }

        // Checks if it is a self edge
        if (x == y) {
            System.out.println("Same Vertex!");
        } else {
            // Insert edge (Directed Graph)
            g[y][x] = 1;

            // Delete comment below for Undirected Graph
            // g[x][y] = 1;
        }
    }

    // Function to update adjacency
    // matrix for edge removal
    public void removeEdge(int x, int y)
    {
        // Checks if the vertices exists
        if ((x < 0) || (x >= n)) {
            System.out.println("Vertex " + x + " does not exist!");
            return;
        }
        if ((y < 0) || (y >= n)) {
            System.out.println("Vertex " + y + " does not exist!");
            return;
        }

        // Checks if it is a self edge
        if (x == y) {
            System.out.println("Same Vertex!");
        } else {
            // Remove edge
            g[y][x] = 0;

            // Delete comment below for Undirected Graph
            // g[x][y] = 0;
        }
    }
}

// Driver Code
public class Main {
    public static void main(String[] args)
    {
        int N = 6;
        GraphMatrix obj = new GraphMatrix(N);

        // Inserting edges
        obj.addEdge(0, 1);
        obj.addEdge(0, 2);
        obj.addEdge(0, 3);
        obj.addEdge(0, 4);
        obj.addEdge(1, 3);
        obj.addEdge(2, 3);
        obj.addEdge(2, 4);
        obj.addEdge(2, 5);
        obj.addEdge(3, 5);

        System.out.println("Adjacency matrix after edge insertions:");
        obj.displayAdjacencyMatrix();

        obj.removeEdge(2, 3);

        System.out.println("\nAdjacency matrix after edge removal:");
        obj.displayAdjacencyMatrix();
    }
}
```

<b>perhatikan kembali jika ingin menggunakan direct dan undirected</b>

#### 2.1 Adjacency List

![geeksforgeeks](https://www.programiz.com/sites/tutorial2program/files/adjacency-list-representation.png)
reference: programiz.com <br>

Adjacency List merepresentasikan graph sebagai Array yang berisi List (atau LinkedList). Indeks dari array mewakili vertex, dan List pada indeks tersebut berisi semua vertex tetangga yang terhubung langsung dengannya.

- Kelebihan: Sangat hemat memori untuk graph yang renggang karena hanya menyimpan edge yang benar-benar ada. Kompleksitas ruangnya $O(V + E)$.
- Kekurangan: Butuh waktu lebih lama untuk mengecek keberadaan edge spesifik dibanding matriks.

Terdapat 2 operasi dalam Adjacency Matrix yaitu add dan remove. Berikut implementasi Adjacency List di Java:

```java
import java.util.LinkedList;

class GraphList {
    // Jumlah vertex (node)
    private int V;

    // Array dari LinkedList untuk menyimpan daftar ketetanggaan
    private LinkedList<Integer>[] adjList;

    // Constructor
    public GraphList(int vertices) {
        this.V = vertices;

        // Inisialisasi ukuran array sebanyak jumlah vertex
        adjList = new LinkedList[V];

        // Inisialisasi LinkedList kosong untuk setiap elemen array
        for (int i = 0; i < V; i++) {
            adjList[i] = new LinkedList<>();
        }
    }

    // Method untuk menambahkan Edge
    public void addEdge(int source, int destination) {
        // Cek validitas node
        if (source < 0 || source >= V || destination < 0 || destination >= V) {
            System.out.println("Vertex tidak valid!");
            return;
        }

        // Tambahkan destination ke list milik source
        adjList[source].add(destination);

        // Gunakan dibawah jika Undirected
        // adjList[destination].add(source);
    }

    // Method untuk menghapus Edge
    public void removeEdge(int source, int destination) {
        if (source < 0 || source >= V || destination < 0 || destination >= V) {
            System.out.println("Vertex tidak valid!");
            return;
        }

        // Menghapus destination dari list source.
        adjList[source].remove((Integer) destination);

        // Gunakan dibawah jika Undirected
        // adjList[destination].remove((Integer) source);
    }

    // Method untuk menampilkan Graph
    public void displayGraph() {
        System.out.println("Representasi Adjacency List:");
        for (int i = 0; i < V; i++) {
            System.out.print("Vertex " + i + " terhubung ke: ");

            // Loop melalui isi LinkedList pada index i
            for (Integer node : adjList[i]) {
                System.out.print(node + " ");
            }
            System.out.println();
        }
    }
}

// Driver Code
public class Graph {
    public static void main(String[] args) {
        int V = 5; // Kita buat graph dengan 5 vertex
        GraphList graph = new GraphList(V);

        // Menambahkan edge
        graph.addEdge(0, 1);
        graph.addEdge(0, 4);
        graph.addEdge(1, 2);
        graph.addEdge(1, 3);
        graph.addEdge(1, 4);
        graph.addEdge(2, 3);
        graph.addEdge(3, 4);

        // Tampilkan graph awal
        graph.displayGraph();

        System.out.println("\nMenghapus edge antara 1 dan 4:");
        graph.removeEdge(1, 4);

        // Tampilkan graph setelah penghapusan
        graph.displayGraph();
    }
}
```

<b>perhatikan kembali jika ingin menggunakan direct dan undirected</b>
