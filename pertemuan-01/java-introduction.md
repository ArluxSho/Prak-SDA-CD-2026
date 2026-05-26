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

# 3. JAVA CONTROL FLOW

Control Flow adalah mekanisme yang menentukan **alur eksekusi program** berdasarkan kondisi atau perulangan.

Control flow memungkinkan program untuk:

- Mengambil keputusan
- Mengulang proses
- Mengontrol jalannya program

---

## 3.1 If-Else Statement

`if-else` digunakan untuk menjalankan kode berdasarkan **kondisi tertentu**.

Jika kondisi bernilai **true**, maka kode di dalam blok `if` akan dijalankan.  
Jika kondisi bernilai **false**, maka kode di dalam blok `else` akan dijalankan.

---

Contoh Program: 

```java
public class Main {
    public static void main(String[] args) {

        int time = 20;

        if (time < 18) {
            System.out.println("Good day.");
        } else {
            System.out.println("Good evening.");
        }

    }
}
```

## 3.2 Switch Statement

`switch` digunakan untuk memilih salah satu dari banyak kemungkinan nilai. Struktur ini sering digunakan ketika kita memiliki banyak pilihan kondisi berdasarkan satu variabel.

Contoh program:
```java
public class Main {
    public static void main(String[] args) {

        int day = 4;

        switch (day) {

            case 1:
                System.out.println("Monday");
                break;

            case 2:
                System.out.println("Tuesday");
                break;

            case 3:
                System.out.println("Wednesday");
                break;

            case 4:
                System.out.println("Thursday");
                break;

            case 5:
                System.out.println("Friday");
                break;

            case 6:
                System.out.println("Saturday");
                break;

            case 7:
                System.out.println("Sunday");
                break;
        }

    }
}
```

--

## 3.3 For Loop 

`for` loop digunakan untuk melakukan perulangan dengan jumlah yang diketahui. Struktur dasanya:

```java
for (inisialisasi; kondisi; increment/decrement)
```

Contoh program: 

```java
public class Main {
    public static void main(String[] args) {

        for (int i = 0; i < 5; i++) {
            System.out.println(i);
        }

    }
}
```

--

## 3.4 While Loop

`while` loop digunakan untuk melakukan perulangan selama kondisi bernilai true. Contoh program:

```java
public class Main {
    public static void main(String[] args) {

        int i = 0;

        while (i < 5) {
            System.out.println(i);
            i++;
        }

    }
}
```

-- 

## 3.5 Do-While Loop

`do-while` mirip dengan `while`, tetapi kondisi aka dijalankan minimal satu kali sebelum kondisi diperiksa. Contoh program:

```java
public class Main {
    public static void main(String[] args) {

        int i = 0;

        do {
            System.out.println(i);
            i++;
        } while (i < 5);

    }
}
```

--

## 3.6 Break and Continue 

Dalam perulangan, kita dapat menggunakan break yang digunakan untuk menghentikan loop secara langsung, dan continue digunakan untuk melewati iterasi saat ini dan melanjutkan ke iterasi berikutnya. Contoh program:

```java
public class Main {
    public static void main(String[] args) {

        for (int i = 0; i < 10; i++) {

            if (i == 5) {
                break; // Keluar dari loop ketika i sama dengan 5
            }

            if (i % 2 == 0) {
                continue; // Lewatkan iterasi ketika i adalah angka genap
            }

            System.out.println(i); // Hanya mencetak angka ganjil dari 0 hingga 9
        }

    }
}
```

--

# 4. Java-Arrays

Array digunakan untuk menyimpan banyak nilai dalam satu variabel. Semua elemen dalam array memiliki tipe data yang sama. Contoh program:

```java
public class Main {
    public static void main(String[] args) {

        // Deklarasi dan inisialisasi array
        int[] myNumbers = {10, 20, 30, 40, 50};

        // Mengakses elemen array
        System.out.println(myNumbers[0]); // Output: 10

        // Mengubah elemen array
        myNumbers[1] = 25;
        System.out.println(myNumbers[1]); // Output: 25

        // Panjang array
        System.out.println(myNumbers.length); // Output: 5

    }
}
```
