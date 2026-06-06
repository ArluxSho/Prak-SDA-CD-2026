# Penugasan Praktikum – Pertemuan 3

## Materi
- Analisis Kompleksitas Algoritma dengan (Runtime)
## Deskripsi Tugas

Buatlah dan jalankan **program Java sederhana** untuk membandingkan waktu eksekusi (*runtime*) antara `ArrayList` dan `LinkedList` saat melakukan penambahan data di awal indeks.

Silakan gunakan dan amati kode dasar berikut:

### 1. `ArrayListTest.java`
```java
import java.util.ArrayList;

public class ArrayListTest {

    public static void main(String[] args) {

        ArrayList<Integer> arrayList = new ArrayList<>();
        int n1 = 1000; // ubah nilai ini

        System.out.println("\nMemulai untuk n = " + n1 + "...");

        
        long start1 = System.nanoTime();

        for (int i = 0; i < n1; i++) {
            arrayList.add(0, i);
        }

        long end1 = System.nanoTime();

        System.out.println("Waktu eksekusi ArrayList : " + (end1 - start1) + " ns");

        //kalian bisa copy paste kode diatas untuk langsung mencoba beberapa n sekaligus

    }
}
```

### 2. `LinkedListTest.java`
```java
import java.util.LinkedList;

public class LinkedListTest {

    public static void main(String[] args) {

        LinkedList<Integer> linkedList = new LinkedList<>();
        int n1 = 1000; // ubah nilai ini

        System.out.println("\nMemulai untuk n = " + n1 + "...");

        
        long start1 = System.nanoTime();

        for (int i = 0; i < n1; i++) {
            linkedList.add(0, i);
        }

        long end1 = System.nanoTime();
        
        System.out.println("Waktu eksekusi LinkedList : " + (end1 - start1) + " ns");

    }
}
```

**Tugas Praktikan:**
Ubah nilai `n` pada kedua kode di atas menjadi beberapa variasi (misalnya: `1000`, `50000`, dan `150000`). Amati struktur data mana yang mengalami perlambatan paling signifikan saat datanya besar.

## Pertanyaan Analisis Kompleksitas Algoritma

Jawablah pertanyaan berikut di dalam file PDF laporan Anda berdasarkan hasil eksperimen *runtime* dari kode dasar yang telah diberikan.

1. **Membaca Hasil Runtime**
  Jalankan kedua program untuk `n = 1000`, `n = 50000`, dan `n = 150000`.
  Tuliskan tabel hasil *runtime* sederhana, lalu simpulkan pola pertumbuhan waktunya pada `ArrayList` dan `LinkedList`.

2. **Big O Operasi di Awal List**
  Berdasarkan kode `add(0, i)`, tentukan kompleksitas waktu operasi tersebut pada:
  	- `ArrayList`
  	- `LinkedList`

	Berikan alasan singkat yang mengaitkan jawaban dengan proses di memori/struktur data.

3. **Analisis Perbandingan**
  Saat `n` besar (misalnya `n = 100000` atau lebih), mengapa selisih *runtime* kedua struktur data bisa semakin jauh?
  Jelaskan hubungan antara jumlah elemen, proses pergeseran elemen pada array, dan efeknya terhadap waktu eksekusi total.

4. **Studi Kasus Perubahan Skenario**
  Ubah skenario menjadi penambahan data di **akhir** list dengan `add(i)` (tanpa indeks).
  Prediksi struktur data mana yang lebih efisien untuk skenario ini, lalu validasi dengan eksperimen singkat dan jelaskan hasilnya.

**Bonus (Opsional):**
Ganti salah satu pengujian dengan `ArrayDeque` menggunakan `addFirst()` untuk `n = 100000`.
Bandingkan *runtime* terhadap `LinkedList`, kemudian jelaskan kenapa performanya bisa mendekati atau bahkan lebih baik.

## Ketentuan

1. Program harus menggunakan:
   - `ArrayList`
   - `LinkedList`
2. Program harus dapat **dijalankan tanpa error**
3. Sertakan **comment (`//`) pada bagian penting kode**, terutama jika Anda melakukan modifikasi.
4. Sertakan **screenshot hasil program ketika dijalankan** untuk menunjukkan perbedaan *runtime*-nya.

## Nilai tambah

- Kalau kalian menambahkan algoritma selain yang sudah ada dan menjelaskan apa yang terjadi saat algoritma berjalan beserta kompleksitasnya. 
- Bisa menampilkan space complexity

## Format Pengumpulan

1. File program Java disatukan dalam folder/zip dengan format nama:

  `kelas_PSDA02_NIM_NAMA.zip`

Contoh:

  `C_PSDA02_L0124063_MuhammadIrfan.zip`

2. Screenshot hasil program dijalankan serta kesimpulan singkat analisis *runtime* dalam format PDF:

  `kelas_PSDA02_NIM_NAMA.pdf`

Contoh:

  `C_PSDA02_L0124063_MuhammadIrfan.pdf`

## Deadline

Batas waktu pengumpulan tugas adalah:

**Kamis, 10 April 2026**
```
