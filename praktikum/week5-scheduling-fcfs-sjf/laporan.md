
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

1.Perbandingan rata-rata Waiting Time (WT) dan Turnaround Time (TAT) — FCFS vs SJF
Di bawah ini aku gunakan contoh proses untuk mengilustrasikan perbandingan (non-preemptive):

Proses:

P1: arrival=0, burst=8
P2: arrival=1, burst=4
P3: arrival=2, burst=2
P4: arrival=3, burst=1

> Hasil perhitungan (langkah & rumus singkat)

Rumus:
Start time: saat CPU mulai mengeksekusi proses.
Finish time = start + burst.
WT = start − arrival.
TAT = finish − arrival.


FCFS (First Come First Served) — eksekusi berdasarkan urutan kedatangan

Urutan eksekusi: P1 → P2 → P3 → P4
Gantt: |P1(0–8)|P2(8–12)|P3(12–14)|P4(14–15)|

Tabel (FCFS):

P1: WT = 0,  TAT = 8
P2: WT = 7,  TAT = 11
P3: WT = 10, TAT = 12
P4: WT = 11, TAT = 12


Rata-rata FCFS:

Avg WT = (0 + 7 + 10 + 11) / 4 = 7.0
Avg TAT = (8 + 11 + 12 + 12) / 4 = 10.75

SJF (Shortest Job First) — non-preemptive, pilih job terpendek dari yang sudah datang
Urutan eksekusi: P1 → P4 → P3 → P2  (karena setelah P1 selesai pada t=8, P4(1), P3(2) dan P2(4) tersedia — pilih yang burst paling kecil dulu)
Gantt: |P1(0–8)|P4(8–9)|P3(9–11)|P2(11–15)|

Tabel (SJF):

P1: WT = 0,  TAT = 8
P4: WT = 5,  TAT = 6
P3: WT = 7,  TAT = 9
P2: WT = 10, TAT = 14

Rata-rata SJF:

Avg WT = (0 + 5 + 7 + 10) / 4 = 5.5
Avg TAT = (8 + 6 + 9 + 14) / 4 = 9.25
Interpretasi & kapan masing-masing lebih unggul

2.Kapan SJF lebih unggul daripada FCFS
Bila durasi (burst) proses bervariasi besar dan ada banyak proses pendek → SJF menurunkan rata-rata WT dan TAT (lihat contoh: Avg WT 5.5 vs 7.0).
Ideal untuk meningkatkan throughput dan mengurangi rata-rata waktu tunggu di sistem batch atau lingkungan non-interaktif.
Catatan: SJF mengasumsikan tersedia estimasi burst (atau perkiraan) dan dapat menyebabkan starvation pada job panjang.
Kapan FCFS lebih baik / dipilih daripada SJF
Bila sederhana dan tidak ingin overhead estimasi (FCFS mudah diimplementasikan).
Bila urutan kedatangan sudah menguntungkan (mis. proses pendek datang lebih dulu) sehingga SJF tidak memberi keuntungan signifikan.
Bila keadilan historis lebih penting (FCFS melayani sesuai urutan kedatangan tanpa memfavoritkan job pendek).
Untuk sistem di mana preemption/estimasi sulit atau tidak tersedia, FCFS lebih aman.

3) Kesimpulan singkat 

1. SJF secara teori/praktik dapat menurunkan rata-rata waiting time dan turnaround time dibanding FCFS ketika ada variasi besar dalam burst time dan estimasi durasi bisa dibuat.
2. FCFS lebih sederhana dan lebih adil terhadap urutan kedatangan, cocok ketika estimasi burst tidak tersedia atau overhead harus diminimalkan.
3. Pemilihan algoritma harus menimbang tujuan sistem: optimasi performa (SJF) vs kesederhanaan/keadilan dan rendahnya overhead (FCFS).

## Kesimpulan

1. Setiap algoritma memiliki karakteristik dan tujuan berbeda:
FCFS menekankan urutan kedatangan proses, sementara SJF memprioritaskan proses dengan waktu eksekusi paling pendek untuk meningkatkan efisiensi.
2. SJF secara teori memberikan kinerja yang lebih baik dalam rata-rata waktu tunggu dan turnaround time dibanding FCFS, namun membutuhkan estimasi burst time yang tidak selalu mudah.
3. FCFS lebih sederhana dan mudah diterapkan, tetapi dapat menimbulkan convoy effect yang memperlambat kinerja jika proses panjang datang lebih dulu.
4. SJF dapat menyebabkan starvation, karena proses panjang dapat terus tertunda jika selalu ada proses pendek yang datang.
5. Pemilihan algoritma penjadwalan harus disesuaikan dengan kebutuhan sistem, apakah lebih memprioritaskan kesederhanaan (FCFS) atau performa optimal (SJF).


## Quiz

1️⃣ Perbedaan utama antara FCFS dan SJF

Aspek	FCFS (First Come First Served)	SJF (Shortest Job First)

Dasar pemilihan	Urutan kedatangan proses	Durasi burst time terpendek
Sifat	Non-preemptive	Bisa preemptive / non-preemptive
Tingkat keadilan	Adil sesuai antrian	Lebih mengutamakan proses pendek
Potensi masalah	Convoy effect	Starvation proses panjang

2️⃣ Mengapa SJF menghasilkan rata-rata waktu tunggu minimum?

Karena SJF mendahulukan proses yang paling cepat selesai, sehingga:
Proses pendek tidak menunggu lama
Waktu tunggu proses lain juga lebih efisien karena proses pendek cepat keluar dari CPU
Urutan eksekusinya secara teori optimal secara matematis untuk meminimalkan Average Waiting Time (Shortest processing time → optimal scheduling)
Prinsipnya: “yang cepat diselesaikan lebih dulu untuk menurunkan antrian.”

3️⃣ Kelemahan SJF pada sistem interaktif

1. Burst time sulit diprediksi
Sistem interaktif punya proses yang dinamis dan sulit diestimasi durasinya.
2. Risiko starvation
Proses panjang bisa terus tertunda jika banyak proses pendek datang.
3. Tidak responsif terhadap pengguna yang menunggu lama
Tidak cocok untuk lingkungan yang menuntut respon cepat dan adil untuk semua pengguna.
4. Perhitungan dan estimasi menambah overhead
Tidak sesederhana FCFS.

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
