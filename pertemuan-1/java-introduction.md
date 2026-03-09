# Java Introduction

# 1. Variabel dan Tipe Data
## 1.1 Variabel 
adalah tempat untuk menyimpan data di dalam program <br><br>
Berikut struktur penulisannya:
```
dataType variableName = value;
```
## 1.2 Tipe Data
Tipe data di Java dibagi menjadi 2 yaitu: <br>
- Primitive: `int`, `long`, `float`, `double`, `boolean`, `char`, dsb <br>
- Non Primitive: `Integer`, `Float`, `Double`, `String`, dsb
## Apa bedanya
Perbedaan utama antara **Primitive Data Types** dan **Non-Primitive Data Types** terletak pada cara penyimpanan data, fitur yang dimiliki, serta penggunaannya dalam program Java.

| Aspek | Primitive Data Type | Non-Primitive Data Type |
|------|---------------------|-------------------------|
| Bentuk | Tipe data dasar | Berupa objek atau class |
| Penyimpanan | Menyimpan nilai langsung | Menyimpan referensi/alamat objek |
| Method | Tidak memiliki method | Memiliki method |
| Nilai awal | Memiliki default value | Defaultnya `null` |
| Diawali | Huruf kecil | Huruf Besar |
---
### Contoh Program 

```java
//Primitive
public class Main { 
    public static void main(String[] args) {
        int umur = 20;
        double tinggi = 165.5;
        char grade = 'A';
        boolean lulus = true;
    }
}
```

```java
//Non Primitive
public class Main {
    public static void main(String[] args) {
        String nama = "Hana";
        ArrayList<String> namaMahasiswa = new ArrayList<>();
        System.out.println("Jumlah karakter nama: " + nama.length());
    }
}
```
# 2. Operators
## 1.1 Arithmetic Operators
## 1.2 Assignment Operators
## 1.3 Comparison Operators
## 1.4 Logical Operator

| Operator | Nama | Deskripsi | Contoh |
|----------|------|-----------|--------|
| && | Logika AND | Mengembalikan nilai true jika kedua statement benar | x < 9 && x > 5 |
| \|\| | Logika OR | Mengembalikan nilai true jika salah satu statement benar | x < 9 \|\| x > 11 |
| ! | Logika NOT | Membalikkan nilai boolean (true menjadi false, dan sebaliknya) | !(x < 9) |
---

