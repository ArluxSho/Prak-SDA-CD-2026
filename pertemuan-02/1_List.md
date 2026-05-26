# 1. Konsep List

List adalah struktur data yang berguna untuk menampung banyak elemen. 
List bersifat : 
- dinamis, bisa diubah seiring waktu.
- terurut, elemen disimpan dalam urutan tertentu.
- dapat diubah (mutable), bisa diubah setelah list dibuat.
- bisa menampung berbagai tipe data.
- dan bisa diindeks. 

Liar ada 2 jenis yaitu **array list** dan **linked list**.

## 1.1. Array List
Implementasi list yang menggunakan array sebagai penampung internalnya.

Kelebihan: Akses elemen di posisi tertentu sangat cepat (O(1)) Kekurangan: Proses penyisipan atau penghapusan di tengah membutuhkan waktu lama (O(N)) karena harus menggeser elemen lain.


### Deklarasi

Contoh:

```Java
import java.util.ArrayList; // import kelas ArrayList

public class Main {
  public static void main(String[] args) {
    ArrayList<String> namaArrayList = new ArrayList<String>(); // Membuat object dari kelas ArrayList
  }
}
```

### Operasi

Menambahkan elemen di akhir:

```Java
ArrayList<String> cats = new ArrayList<String>();

cats.add("Persia");
```

Menambahkan elemen di suatu indeks:

```Java
cats.add("Munchkin");
cats.add(1, "Angora");
```

Merubah elemen di suatu indeks:

```Java
cats.set(0, "Spinx");
```

Menghapus elemen sebuah indeks:

```Java
cats.remove(0);
```

Menghapus seluruh elemen:

```Java
cats.clear();
```

Mengakses elemen di suatu indeks:

```Java
cats.get(0);
```

Iterasi seluruh elemen:

```Java
for (int i = 0; i < cats.size(); i++) {
      System.out.println(cats.get(i));
    }
```

## 1.2. Linked List
Implementasi list di mana setiap elemen menyimpan nilai dan referensi (pointer) ke elemen berikutnya.

Kelebihan: Penyisipan dan penghapusan elemen sangat cepat(O(1)) karena tidak perlu menggeser elemen. Kekurangan: akses elemen di posisi tertentu lambat (O(N)) karena harus menelusuri rantai dari awal.
### Deklarasi

Contoh:

```Java
import java.util.LinkedList; // import kelas LinkedList

public class Main {
  public static void main(String[] args) {
    LinkedList<String> namaLinkedList = new LinkedList<String>(); // Membuat object dari kelas LinkedList
  }
}
```

### Operasi

| Methods       | Deskripsi                                         |
| ------------- | ------------------------------------------------- |
| addFirst()    | Menambahkan elemen di awal                        |
| addLast()     | Menambahkan elemen di akhir                       |
| removeFirst() | Menghapus elemen di indeks pertama (indeks ke- 0) |
| removeLast()  | Menghapus elemen di indeks terakhir               |
| getFirst()    | Mengakses elemen di indeks pertama (indeks ke- 0) |
| getLast()     | Mengakses elemen di indeks terakhir               |

## Selengkapnya

- [Java Array List](https://www.tpointtech.com/java-arraylist)
- [Java Linked List](https://www.tpointtech.com/java-linkedlist)
