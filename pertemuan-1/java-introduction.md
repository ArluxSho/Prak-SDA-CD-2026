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
| Diawali | Huruf kecil | Huruf besar |
---
### Contoh Program 

```java
//Primitive
public class Main { 
    public static void main(String[] args) {
        int umur = 20;
        double tinggi = 183.12;
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
## 2.1 Arithmetic Operators

| Operator | Nama | Deskripsi | Contoh |
|----------|------|-----------|--------|
| + | Addition | Digunakan untuk menjumlahkan dua nilai | 5 + 3 = 8 |
| - | Subtraction | Digunakan untuk mengurangi suatu nilai dengan nilai lain | 10 - 4 = 6 |
| * | Multiplication | Digunakan untuk mengalikan dua nilai | 4 * 3 = 12 |
| / | Division | Digunakan untuk membagi suatu nilai dengan nilai lain | 10 / 2 = 5 |
| % | Modulus | Menghasilkan sisa hasil pembagian | 10 % 3 = 1 |
| ++ | Increment | Menambah nilai variabel sebesar 1 | x++ atau ++x |
| -- | Decrement | Mengurangi nilai variabel sebesar 1 | x-- atau --x |
---
*jangan lupa perbedaan x++ dan ++x*
```
x++ = nilai digunakan dulu, baru ditambah 1
++x = nilai ditambah dulu, baru digunakan
```


## 2.2 Assignment Operators

| Operator | Contoh |
|----------|--------|
| = | x = 10 |
| += | x += 5 (x = x + 5) |
| -= | x -= 3 (x = x - 3) |
| *= | x *= 2 (x = x * 2) |
| /= | x /= 4 (x = x / 4) |
| %= | x %= 3 (x = x % 3) |
| ^= | x ^= 1 (x = x^1) |
---

## 2.3 Comparison Operators

| Operator | Nama | Contoh |
|----------|------|--------|
| == | Equal to | x == 1 |
| != | Not equal to | x != 1 |
| > | Greater than | x > 1 |
| < | Less than | x < 1 |
| >= | Greater than or equal to | x >= 1 |
| <= | Less than or equal to | x <= 1 |
---

## 2.4 Logical Operator

| Operator | Nama | Deskripsi | Contoh |
|----------|------|-----------|--------|
| && | Logika AND | Mengembalikan nilai true jika kedua statement benar | x < 9 && x > 5 |
| \|\| | Logika OR | Mengembalikan nilai true jika salah satu statement benar | x < 9 \|\| x > 11 |
| ! | Logika NOT | Membalikkan nilai boolean (true menjadi false, dan sebaliknya) | !(x < 9) |
---

