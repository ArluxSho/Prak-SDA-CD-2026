# 13. Binary Search

Binary Search adalah algoritma pencarian yang digunakan untuk mencari data pada array yang sudah terurut. Cara kerjanya dengan mengecek elemen tengah terlebih dahulu, lalu membuang setengah area pencarian yang sudah pasti tidak mungkin berisi target.

Kalau dibandingkan dengan Linear Search, Binary Search jauh lebih cepat untuk data yang besar. Linear Search mengecek data dari awal satu per satu, sedangkan Binary Search selalu membagi area pencarian menjadi dua bagian.

Contoh array yang bisa digunakan:

```java
int[] data = {3, 7, 12, 18, 24, 31, 42};
```

Array di atas sudah terurut dari kecil ke besar, jadi aman digunakan untuk Binary Search.

## Syarat Utama

Syarat Binary Search hanya satu, tetapi penting:

> Data harus sudah terurut.

Jika data belum terurut, hasil pencarian bisa salah karena Binary Search mengambil keputusan berdasarkan urutan data.

Contoh data yang belum bisa langsung digunakan:

```java
int[] data = {12, 3, 42, 7, 24, 18, 31};
```

Data tersebut harus diurutkan terlebih dahulu sebelum dicari dengan Binary Search.

## Konsep Left, Right, dan Mid

Binary Search memakai tiga penanda utama:

- `left` untuk batas kiri pencarian
- `right` untuk batas kanan pencarian
- `mid` untuk index tengah dari area pencarian

Nilai awalnya seperti berikut:

```java
int left = 0;
int right = arr.length - 1;
```

Untuk mencari posisi tengah, gunakan:

```java
int mid = left + (right - left) / 2;
```

Rumus tersebut lebih aman dibanding `(left + right) / 2`, terutama jika ukuran array sangat besar.

## Cara Kerja

Langkah Binary Search:

1. Tentukan `left` di index pertama.
2. Tentukan `right` di index terakhir.
3. Hitung `mid`.
4. Bandingkan `arr[mid]` dengan target.
5. Jika sama, data ditemukan.
6. Jika target lebih kecil dari `arr[mid]`, geser pencarian ke kiri.
7. Jika target lebih besar dari `arr[mid]`, geser pencarian ke kanan.
8. Ulangi sampai data ditemukan atau `left` melewati `right`.

## Simulasi

Misalkan terdapat array berikut:

```text
Index:  0   1   2   3   4   5   6
Data :  3   7   12  18  24  31  42
```

Target yang dicari adalah `31`.

Iterasi 1:

```text
left = 0
right = 6
mid = 0 + (6 - 0) / 2
mid = 3
```

Nilai tengahnya adalah:

```text
arr[3] = 18
```

Karena `31 > 18`, pencarian dilanjutkan ke kanan.

```text
left = mid + 1
left = 4
```

Iterasi 2:

```text
left = 4
right = 6
mid = 4 + (6 - 4) / 2
mid = 5
```

Nilai tengahnya adalah:

```text
arr[5] = 31
```

Karena `arr[5]` sama dengan target, data ditemukan pada index `5`.

## Contoh Penerapan

Berikut source code untuk menerapkan Binary Search pada array `{3, 7, 12, 18, 24, 31, 42}`.

```java
public class BinarySearch {

    static int binarySearch(int[] arr, int target) {
        int left = 0;
        int right = arr.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == target) {
                return mid;
            } else if (target < arr[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }

        return -1;
    }

    public static void main(String[] args) {
        int[] data = {3, 7, 12, 18, 24, 31, 42};
        int target = 31;

        int hasil = binarySearch(data, target);

        if (hasil != -1) {
            System.out.println("Data ditemukan pada index: " + hasil);
        } else {
            System.out.println("Data tidak ditemukan");
        }
    }
}
```

Output:

```text
Data ditemukan pada index: 5
```

## Penjelasan Program

Bagian ini digunakan untuk menentukan area awal pencarian:

```java
int left = 0;
int right = arr.length - 1;
```

Selama `left <= right`, berarti area pencarian masih ada.

```java
while (left <= right) {
```

Setiap perulangan, program mencari index tengah:

```java
int mid = left + (right - left) / 2;
```

Jika nilai tengah sama dengan target, function langsung mengembalikan index tersebut.

```java
if (arr[mid] == target) {
    return mid;
}
```

Jika target lebih kecil dari nilai tengah, area kanan tidak perlu dicek.

```java
right = mid - 1;
```

Jika target lebih besar dari nilai tengah, area kiri tidak perlu dicek.

```java
left = mid + 1;
```

Jika perulangan selesai dan data tidak ditemukan, function mengembalikan `-1`.

```java
return -1;
```

## Kompleksitas

Binary Search memiliki kompleksitas waktu:

- Best case: `O(1)`
- Average case: `O(log n)`
- Worst case: `O(log n)`

Best case terjadi ketika target langsung berada di tengah array. Worst case terjadi ketika pencarian terus membagi area sampai data ditemukan atau sampai area pencarian habis.

Contoh jumlah pengecekan maksimal:

| Jumlah Data | Maksimal Pengecekan |
|---:|---:|
| 8 | 3 |
| 16 | 4 |
| 32 | 5 |
| 1.000 | sekitar 10 |
| 1.000.000 | sekitar 20 |

## Perbandingan dengan Linear Search

| Aspek | Linear Search | Binary Search |
|---|---|---|
| Syarat data | Tidak harus terurut | Harus terurut |
| Cara kerja | Mengecek satu per satu | Membagi area pencarian |
| Best case | `O(1)` | `O(1)` |
| Worst case | `O(n)` | `O(log n)` |
| Cocok untuk | Data kecil atau belum terurut | Data besar dan sudah terurut |

## Contoh dengan Input User

Program berikut menerima target dari input user.

```java
import java.util.Scanner;

public class BinarySearchInput {

    static int binarySearch(int[] arr, int target) {
        int left = 0;
        int right = arr.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == target) {
                return mid;
            } else if (target < arr[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }

        return -1;
    }

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        int[] data = {4, 9, 15, 21, 27, 33, 40};

        System.out.print("Masukkan angka yang dicari: ");
        int target = input.nextInt();

        int hasil = binarySearch(data, target);

        if (hasil != -1) {
            System.out.println("Data ditemukan pada index: " + hasil);
        } else {
            System.out.println("Data tidak ditemukan");
        }

        input.close();
    }
}
```

Contoh output:

```text
Masukkan angka yang dicari: 40
Data ditemukan pada index: 6
```

## Kesalahan Umum

Beberapa kesalahan yang sering terjadi pada Binary Search:

- Menggunakan Binary Search pada array yang belum terurut.
- Salah mengubah nilai `left` dan `right`.
- Menggunakan kondisi perulangan yang keliru.
- Tidak mengembalikan nilai ketika data tidak ditemukan.

Contoh kesalahan:

```java
if (target < arr[mid]) {
    left = mid + 1;
}
```

Kode tersebut salah karena jika target lebih kecil dari nilai tengah, pencarian seharusnya bergerak ke kiri.

Kode yang benar:

```java
if (target < arr[mid]) {
    right = mid - 1;
}
```

## Latihan

1. Gunakan array berikut, lalu cari angka `27`.

```java
int[] data = {4, 9, 15, 21, 27, 33, 40};
```

Output yang diharapkan:

```text
Data ditemukan pada index: 4
```

2. Gunakan array yang sama, lalu cari angka `100`.

Output yang diharapkan:

```text
Data tidak ditemukan
```

3. Modifikasi program agar target pencarian berasal dari input user menggunakan `Scanner`.

## Kesimpulan

Binary Search digunakan untuk mencari data pada array yang sudah terurut. Algoritma ini bekerja dengan mengecek bagian tengah, lalu menentukan apakah pencarian lanjut ke kiri atau ke kanan.

Hal penting yang perlu diingat:

- Data harus sudah terurut.
- Gunakan `left`, `right`, dan `mid` untuk membatasi area pencarian.
- Jika target lebih kecil dari nilai tengah, cari ke kiri.
- Jika target lebih besar dari nilai tengah, cari ke kanan.
- Jika data tidak ditemukan, kembalikan `-1`.
- Kompleksitas waktunya adalah `O(log n)`.
