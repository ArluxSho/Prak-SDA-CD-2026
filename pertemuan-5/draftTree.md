## 5. Traversal

## 6. Implementasi

Berikut adalah kode fullnya:

```Java
import java.util.ArrayList;

class Node{
    int data;
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
        if (index < 0 || index >= childrenNode.size()) {
            System.out.println("Child node dengan index " + index + " dari parent node '" + this.data + "' tidak ditemukan di dalam range index 0 - " + childrenNode.size());
            return;
        }

        childrenNode.remove(index);
        System.out.println("Child node dari parent node '" + this.data + "' dengan index " + index + " berhasil dihapus");
    }

    private void _traversal(Node node, int depth) {
        for (int i = 0; i < depth; i++) {
            System.out.print("---");
        }
        System.out.println("> " + node.data);

        for (Node child : node.childrenNode) {
            _traversal(child, depth+1);
        }
    }

    public void traversal(){
        _traversal(this, 0);
    }

    private void _post_traversal(Node node, int depth) {
        for (Node child : node.childrenNode) {
            _post_traversal(child, depth+1);
        }
        for (int i = 0; i < depth; i++) {
            System.out.print("---");
        }
        System.out.println("> " + node.data);
    }

    public void post_traversal(){
        _post_traversal(this, 0);
    }
}

public class TreeMain {
    public static void main(String[] args) {
        Node root = new Node(25);
        Node childNode_1 = new Node(1);
        Node childNode_2 = new Node(4);
        Node childNode_3 = new Node(7);
        Node childNode_1_1 = new Node(66);
        Node childNode_1_2 = new Node(67);
        Node childNode_2_1 = new Node(100);
        Node childNode_2_2 = new Node(120);
        Node childNode_3_1 = new Node(135);
        Node childNode_3_1_1 = new Node(138);

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

        childNode_1.remove_with_index(20);
        childNode_1.remove_with_index(0);

        System.out.println("");

        root.traversal();
    }
}

```

## 7. Contoh

### a. Struktur Folder

```
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
```

### b. DOM HTML

![DOM HTML](https://www.w3schools.com/js/pic_htmltree.gif)

### c. Taxonomic Categorie

![Taxonomic](https://media.geeksforgeeks.org/wp-content/uploads/20230712110802/Taxonomy.png)

## 8. Latihan

a. Jelaskan Root, Leaf, Edge, dan Height!<br>
b. Dalam algoritma Preorder Traversal, urutan langkah yang benar saat mengunjungi setiap node adalah ...<br>
c. Dalam algoritma Postorder Traversal, urutan langkah yang benar saat mengunjungi setiap node adalah ...<br>
d. Root (A) punya anak B (kiri) dan C (kanan). B punya anak D (kiri). Gambarkan dan jelaskan hasil Preorder dan Postorder traversal-nya!<br>
