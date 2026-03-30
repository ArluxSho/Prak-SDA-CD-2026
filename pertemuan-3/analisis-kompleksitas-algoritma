# Analisis Kompleksitas Algoritma

## 1. Pengantar

Bayangkan kalian diminta untuk memindahkan 100 barang dari suatu tempat ke tempat lain. Lalu kalian berpikir kira kira biar ga capek, harus pakai cara apa ya? Tidak mungkin bolak balik 100 kali. Pasti kalian berpikir, lebih baik pake mobil atau kendaraan sehingga bisa bawa banyak barang dalam 1 kali jalan. Kira kira seperti itu konsep dari kompleksitas dalam pemrograman. Kita tidak hanya peduli apakah sebuah program benar, tapi juga apakah program tersebut efisien.

## 2. Konsep Kompleksitas

Terdapat 2 jenis utama kompleksitas

- Time Complexity (Kompleksitas Waktu)
- Space Complexity (Kompleksitas Memori)

### 2.1 Time Complexity (Kompleksitas Waktu)

Time Complexity digunakan untuk mengukur seberapa lama suatu algoritma berjalan berdasarkan ukuran input (n), bukan dalam detik, tapi dalam jumlah operasi yang dilakukan. Contohnya seperti berapa kali loop berjalan,berapa kali perbandingan dilakukan, dan lainnya

### 2.2 Space Complexity (Kompleksitas Memori)

Space Complexity digunakan untuk mengukur berapa banyak memori tambahan yang dibutuhkan algoritma saat dijalankan. Seperti membuat variabel baru, array, rekursi, dan lainnya.

## 3. Big-O Notation

Sebenarnya terdapat banyak jenis asimtotik seperti teta dan omega, tetapi kita kan bahas Big-O. Big-O adalah cara untuk menyatakan batas atas (worst-case) dari kompleksitas algoritma.

| Fungsi Big-O | Nama       |
| ------------ | ---------- |
| O(1)         | Konstan    |
| O(log N)     | Logaritmik |
| O(N)         | Linear     |
| O(N log N)   | n log n    |
| O(N^2)       | Kuadratik  |
| O(N^m)       | Polinomial |
| O(N!)        | Faktorial  |

### 3.1 O(1) Konstan

```java
System.out.println("Selamat Datang");
```

### 3.2 O(N) Linear

```java
int i, n = 8;
for (i = 1; i <= n; i++) {
	System.out.println("Hello, world!");
}
```

### 3.3 O(N^2) Kuadratik

```java
int[] data = {1, 2, 3};

for (int i = 0; i < data.length; i++) {
    for (int j = 0; j < data.length; j++) {
        System.out.println(data[i] + " pasang dengan " + data[j]);
    }
}
```

### 3.4 O(log N) Logaritmik

```java
int n = 100;

while (n > 1) {
    n = n / 2;
    System.out.println("Sisa n: " + n);
}
```

### 3.5 O(N log N) Linearritmik

```java
int n = 8;
int totalOperasi = 0;

// Loop Luar: Berjalan n kali (O(n))
for (int i = 0; i < n; i++) {

    // Loop Dalam: Berjalan secara logaritmik (O(log n))
    int j = n;
    while (j > 1) {
        j = j / 2;
        totalOperasi++;
        System.out.println("Loop i ke-" + i + ", j sekarang: " + j);
    }
}

System.out.println("Total operasi untuk n=" + n + " adalah " + totalOperasi);
```

### Perbandingan

![alt text](image-1.png)

<!-- referensi: https://blog.stackademic.com/how-to-calculate-big-o-notation-time-complexity-5504bed8d292 -->
