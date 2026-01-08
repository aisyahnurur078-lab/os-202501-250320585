
# Laporan Praktikum Minggu [X]
Topik :Manajemen Memori – Page Replacement (FIFO & LRU)

---

## Identitas
- **Nama**  : [Aisyah Nurur Rohmah]  
- **NIM**   : [250320585]  
- **Kelas** : [1DSRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  
1.Mengimplementasikan algoritma page replacement FIFO dalam program.
2.Mengimplementasikan algoritma page replacement LRU dalam program.
3.Menjalankan simulasi page replacement dengan dataset tertentu.
4.Membandingkan performa FIFO dan LRU berdasarkan jumlah page fault.
5.Menyajikan hasil simulasi dalam laporan yang sistematis.

---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
1.Konsep Memori Virtual: Dasar utama adalah memori virtual, sebuah teknik manajemen memori yang memungkinkan eksekusi proses yang mungkin tidak sepenuhnya dimuat ke dalam memori fisik. Teknik ini menciptakan ilusi memori yang lebih besar dari yang sebenarnya tersedia, dengan memindahkan blok data (halaman/ pages) antara RAM dan penyimpanan sekunder (seperti hard drive) sesuai kebutuhan [1].
2.Kebutuhan Page Replacement: Ketika memori fisik penuh dan proses membutuhkan halaman baru, maka harus ada halaman yang dikeluarkan untuk memberikan ruang. Algoritma page replacement digunakan untuk menentukan halaman mana yang paling optimal untuk dikeluarkan, dengan tujuan meminimalkan page fault (situasi di mana halaman yang dibutuhkan tidak ada di memori fisik) [1].
3.Algoritma FIFO (First-In, First-Out): Algoritma ini didasarkan pada prinsip antrean sederhana. Halaman yang dipilih untuk dikeluarkan adalah halaman yang paling lama berada di memori (yang pertama masuk), tanpa mempertimbangkan seberapa sering halaman tersebut digunakan. Algoritma ini mudah diimplementasikan tetapi seringkali tidak efisien karena bisa mengeluarkan halaman yang masih sering diakses [2].
4.Algoritma LRU (Least Recently Used): Algoritma ini didasarkan pada asumsi lokalitas referensi, yaitu halaman yang telah digunakan baru-baru ini kemungkinan besar akan digunakan lagi dalam waktu dekat. LRU memilih halaman yang paling jarang digunakan dalam periode waktu terbaru untuk dikeluarkan, menjadikannya lebih efisien daripada FIFO dalam banyak skenario, meskipun implementasinya lebih kompleks (membutuhkan pencatatan waktu atau urutan penggunaan halaman) [2]. 


---

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.  
2. Perintah yang dijalankan.  
3. File dan kode yang dibuat.  
4. Commit message yang digunakan.

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
uname -a
lsmod | head
dmesg | head
```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)

---

## Analisis
- Jelaskan makna hasil percobaan.  
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  

---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.
1.Tujuan Utama: Algoritma penggantian halaman bertujuan untuk memutuskan halaman mana di memori fisik yang harus dikeluarkan (di-swap out) untuk memberi ruang bagi halaman baru, memaksimalkan penggunaan memori dan meminimalkan page fault [1].
2.FIFO (First-In, First-Out): Algoritma ini mengeluarkan halaman tertua yang pertama kali masuk ke dalam memori, tanpa mempertimbangkan seberapa sering halaman tersebut diakses. Keunggulannya adalah kesederhanaan dan kemudahan implementasi, tetapi kelemahannya adalah potensial terjadinya Anomali Belady (peningkatan page fault meskipun jumlah bingkai memori bertambah) [1].
3.LRU (Least Recently Used): LRU mengeluarkan halaman yang paling jarang digunakan dalam waktu terdekat (paling lama tidak diakses). Algoritma ini bekerja lebih baik daripada FIFO karena mempertimbangkan perilaku akses masa lalu untuk memprediksi masa depan, sehingga umumnya menghasilkan tingkat page fault yang lebih rendah [1].
4.Perbedaan Kinerja: Secara umum, LRU memberikan kinerja yang lebih optimal untuk sebagian besar pola akses memori dibandingkan FIFO, karena LRU berusaha mempertahankan halaman yang aktif digunakan di dalam memori [1].
5.Kompleksitas Implementasi: Meskipun lebih efisien, LRU lebih kompleks untuk diimplementasikan dan membutuhkan dukungan perangkat keras khusus untuk melacak waktu atau urutan akses halaman, sedangkan FIFO hanya membutuhkan antrian sederhana [1]. 


---

## Quiz
1. Apa perbedaan utama FIFO dan LRU? 
   **Jawaban:** Perbedaan utama FIFO (First-In, First-Out) dan LRU (Least Recently Used) terletak pada kriteria penggantian item di cache: FIFO mengganti item berdasarkan urutan kedatangan (yang paling lama masuk akan keluar), sementara LRU mengganti item yang paling jarang digunakan baru-baru ini, dengan asumsi item yang baru digunakan lebih mungkin digunakan lagi. FIFO sederhana namun tidak mempertimbangkan frekuensi penggunaan, sedangkan LRU lebih kompleks karena butuh melacak penggunaan, tapi umumnya memberikan kinerja lebih baik dengan mengurangi kesalahan cache (page faults). 
 
2.Mengapa FIFO dapat menghasilkan Belady’s Anomaly?  
   **Jawaban:**Mekanisme terjadinya hal ini pada FIFO adalah sebagai berikut:
1.FIFO Tidak Mempertimbangkan Masa Depan: Algoritma FIFO hanya melacak urutan kedatangan halaman dan selalu mengeluarkan halaman yang paling lama berada di memori utama, terlepas dari apakah halaman tersebut mungkin dibutuhkan lagi segera atau tidak [1].
2. Perubahan Pola Akses Memori: Ketika jumlah bingkai bertambah, urutan halaman yang dikeluarkan oleh FIFO berubah. Dalam beberapa pola akses memori (reference string) tertentu, "halaman tua" yang seharusnya tetap berada di memori utama (karena akan segera diakses kembali) justru dikeluarkan, digantikan oleh halaman yang mungkin tidak akan diakses dalam waktu dekat [1].
3. Contoh Spesifik: Sebagai contoh konkret, pada pola akses memori 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5:
>Dengan 3 bingkai halaman, FIFO menghasilkan 9 kesalahan halaman.
>Namun, dengan 4 bingkai halaman, FIFO menghasilkan 10 kesalahan halaman [1]. 


3. [Pertanyaan 3]  
   **Jawaban:**  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
