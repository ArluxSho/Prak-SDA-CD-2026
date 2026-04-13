## 5. Traversal

## 6. Implementasi

Berikut adalah kode fullnya:

```Java
import java.util.ArrayList;

class Node{
    int data;   // tipe data bebas, berfungsi untuk menyimpan data
    ArrayList<Node> childrenNode = new ArrayList<>();

    // cunstructor
    Node(int data) {
        this.data = data;
    }

    // Method
    public void insert(Node new_node) {
        childrenNode.add(new_node);
    }

    public void remove_with_index(int index) {
        // memeriksa ketersediaan index yang dicari
        // jika index out of bound
        if (index < 0 || index >= childrenNode.size()) {
            System.out.println("Child node dengan index " + index + " dari parent node '" + this.data + "' tidak ditemukan di dalam range index 0 - " + childrenNode.size());
            return;
        }

        // jika index child node ditemukan
        childrenNode.remove(index);
        System.out.println("Child node dari parent node '" + this.data + "' dengan index " + index + " berhasil dihapus");
    }

    private void _traversal(Node node, int depth) {
        for (int i = 0; i < depth; i++) {     // memperhatikan kedalaman tree
            System.out.print("---");         // untuk memudahkan pembacaan tree
        }
        System.out.println("> " + node.data);

        for (Node child : node.childrenNode) {
            _traversal(child, depth+1);
        }
    }

    public void traversal(){
        _traversal(this, 0);    // mengambil dari kedalaman 0
    }

    private void _post_traversal(Node node, int depth) {
        for (Node child : node.childrenNode) {  // akan rekursi dulu baru di-print
            _post_traversal(child, depth+1);
        }
        for (int i = 0; i < depth; i++) {       // memperhatikan kedalaman tree
            System.out.print("---");          // untuk memudahkan pembacaan tree
        }
        System.out.println("> " + node.data);
    }

    public void post_traversal(){
        _post_traversal(this, 0);    // mengambil dari kedalaman 0
    }
}

public class TreeMain {
    public static void main(String[] args) {
        Node root = new Node(35);
        Node childNode_1 = new Node(1);
        Node childNode_2 = new Node(3);
        Node childNode_3 = new Node(6);
        Node childNode_1_1 = new Node(83);
        Node childNode_1_2 = new Node(100);
        Node childNode_2_1 = new Node(135);
        Node childNode_2_2 = new Node(143);
        Node childNode_3_1 = new Node(190);
        Node childNode_3_1_1 = new Node(2);

        root.insert(childNode_1);
        root.insert(childNode_2);
        root.insert(childNode_3);
        childNode_1.insert(childNode_1_1);
        childNode_1.insert(childNode_1_2);
        childNode_2.insert(childNode_2_1);
        childNode_2.insert(childNode_2_2);
        childNode_3.insert(childNode_3_1);
        childNode_3_1.insert(childNode_3_1_1);

        root.traversal();

        System.out.println("");

        childNode_1.remove_with_index(100);
        childNode_1.remove_with_index(1);

        System.out.println("");

        root.traversal();
    }
}

/* Output

    > 35
    ---> 1
    ------> 83
    ------> 100
    ---> 3
    ------> 135
    ------> 143
    ---> 6
    ------> 190
    ---------> 2

    Child node dengan index 100 dari parent node '1' tidak ditemukan di dalam range index 0 - 2
    Child node dari parent node '1' dengan index 1 berhasil dihapus

    > 35
    ---> 1
    ------> 83
    ---> 3
    ------> 135
    ------> 143
    ---> 6
    ------> 190
    ---------> 2

*/
```

## 7. Contoh

### a. Struktur Folder

project/
├── src/
│ └── index.html
| └── style.css
| └── script.js
|
├── docs/
│ └── user-stories.md
| └── backlog.md
│  
└── README.md

### b. DOM HTML

![DOM HTML](https://www.w3schools.com/js/pic_htmltree.gif)

### c. Taxonomic Categorie

![Taxonomic](https://media.geeksforgeeks.org/wp-content/uploads/20230712110802/Taxonomy.png)

## 8. Latihan

a. Jelaskan Root, Leaf, Edge, dan Height!
b. Dalam algoritma Preorder Traversal, urutan langkah yang benar saat mengunjungi setiap node adalah ...
c. Dalam algoritma Postorder Traversal, urutan langkah yang benar saat mengunjungi setiap node adalah ...
d. Root (A) punya anak B (kiri) dan C (kanan). B punya anak D (kiri). Gambarkan dan jelaskan hasil Preorder dan Postorder traversal-nya!
