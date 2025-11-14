
# Laporan Praktikum Minggu [V]
Topik: Penjadwalan CPU – FCFS dan SJF 


## Identitas
- **Nama**  : [Aisyah Nurur Rohmah]  
- **NIM**   : [250320585]  
- **Kelas** : [1DSRA]

---

## Tujuan  
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.
> Menghitung waiting time dan turnaround time untuk algoritma FCFS dan SJF.
> Menyajikan hasil perhitungan dalam tabel yang rapi dan mudah dibaca.
> Membandingkan performa FCFS dan SJF berdasarkan hasil analisis.
> Menjelaskan kelebihan dan kekurangan masing-masing algoritma.
> Menyimpulkan kapan algoritma FCFS atau SJF lebih sesuai digunakan.

---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
Berikut dasar teori yang mendasari percobaan Penjadwalan CPU – FCFS dan SJF 
1️⃣ FCFS (First Come First Served)

1. Non-preemptive scheduling
Proses dieksekusi sesuai urutan kedatangan (pertama datang → pertama dilayani).
2. Implementasi sederhana
Menggunakan Ready Queue dengan mekanisme FIFO (First In First Out).
3. Cocok untuk beban kerja ringan
Tidak memerlukan perhitungan prioritas atau estimasi waktu eksekusi.
4. Masalah convoy effect
Proses panjang dapat menghambat proses pendek di belakangnya → waktu tunggu rata-rata bisa tinggi.
5. Tidak mempertimbangkan waktu proses
Tidak optimal untuk lingkungan yang membutuhkan response time cepat.
---
2️⃣ SJF (Shortest Job First)

1. Berbasis estimasi durasi proses
Proses dengan Burst Time paling pendek mendapat CPU terlebih dahulu.
2. Waktu tunggu rata-rata minimal
Secara teori, SJF memberikan performance terbaik dalam hal average waiting time.
3. Tersedia dalam dua mode
Non-preemptive → proses yang sudah berjalan tidak dihentikan
Preemptive (SRTF) → proses baru yang lebih pendek dapat men-preempt proses berjalan
4. Perlu prediksi waktu CPU
Burst time sering diestimasi menggunakan teknik seperti exponential averaging.
5. Risiko starvation
Proses panjang dapat terus tertunda jika selalu ada proses pendek yang datang.

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

1. Setiap algoritma memiliki karakteristik dan tujuan berbeda:
FCFS menekankan urutan kedatangan proses, sementara SJF memprioritaskan proses dengan waktu eksekusi paling pendek untuk meningkatkan efisiensi.
2. SJF secara teori memberikan kinerja yang lebih baik dalam rata-rata waktu tunggu dan turnaround time dibanding FCFS, namun membutuhkan estimasi burst time yang tidak selalu mudah.
3. FCFS lebih sederhana dan mudah diterapkan, tetapi dapat menimbulkan convoy effect yang memperlambat kinerja jika proses panjang datang lebih dulu.
4. SJF dapat menyebabkan starvation, karena proses panjang dapat terus tertunda jika selalu ada proses pendek yang datang.
5. Pemilihan algoritma penjadwalan harus disesuaikan dengan kebutuhan sistem, apakah lebih memprioritaskan kesederhanaan (FCFS) atau performa optimal (SJF).


## Quiz
1. [Pertanyaan 1]  
   **Jawaban:**  
2. [Pertanyaan 2]  
   **Jawaban:**  
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
