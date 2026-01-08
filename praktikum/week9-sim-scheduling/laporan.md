
# Laporan Praktikum Minggu [IX]
Topik: [Simulasi Algoritma Penjadwalan CPU]

---

## Identitas
- **Nama**  : [Aisyah Nurur Rohmah]  
- **NIM**   : [250320585]  
- **Kelas** : [1DSRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini:
>Membuat program simulasi algoritma penjadwalan FCFS dan/atau SJF.
>Menjalankan program dengan dataset uji yang diberikan atau dibuat sendiri.
>Menyajikan output simulasi dalam bentuk tabel atau grafik.
>Menjelaskan hasil simulasi secara tertulis.
>Mengunggah kode dan laporan ke Git repository dengan rapi dan tepat waktu.
---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
1.CPU Scheduling bertujuan mengatur urutan eksekusi proses agar penggunaan CPU menjadi efisien dan waktu tunggu proses dapat diminimalkan.
2.FCFS (First Come First Served) mengeksekusi proses berdasarkan urutan kedatangan tanpa mempertimbangkan lama waktu eksekusi.
3.SJF (Shortest Job First) memilih proses dengan burst time paling kecil sehingga secara teori menghasilkan rata-rata waiting time paling minimum.
4.Waiting Time dan Turnaround Time merupakan metrik utama untuk mengevaluasi kinerja algoritma penjadwalan CPU.
5.Algoritma non-preemptive mengeksekusi proses hingga selesai sebelum berpindah ke proses lain, seperti yang diterapkan pada simulasi FCFS dan SJF.


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
1.Trade-off Kinerja: Tidak ada satu algoritma tunggal yang optimal untuk semua situasi. Setiap algoritma memiliki kekuatan dan kelemahannya masing-masing dalam hal kriteria yang berbeda, seperti throughput, waktu tunggu (waiting time), atau waktu penyelesaian (turnaround time) [1].
2.Pentingnya Burst Time: Algoritma yang mempertimbangkan waktu eksekusi (burst time) tugas, seperti Shortest Job Next (SJN), cenderung memberikan waktu tunggu dan waktu penyelesaian rata-rata yang lebih baik dibandingkan dengan algoritma yang tidak mempertimbangkannya, seperti FCFS [1].
3.Aging dan Starvation: Simulasi sering menunjukkan masalah "kelaparan" (starvation) pada algoritma berbasis prioritas murni, di mana tugas berprioritas rendah mungkin tidak pernah dieksekusi. Solusi seperti aging (peningkatan prioritas seiring waktu) diperlukan untuk mengatasi masalah ini secara efektif [1].
4.Responsivitas Round Robin: Algoritma Round Robin (RR) sangat efektif dalam sistem interaktif karena memberikan waktu respons yang cepat dan adil untuk semua proses dengan membagi waktu CPU menjadi irisan waktu (time slice). Namun, kinerjanya sangat bergantung pada ukuran time slice yang dipilih [1]. 
---

## Quiz
1. Mengapa simulasi diperlukan untuk menguji algoritma scheduling?  
   **Jawaban:**Simulasi diperlukan untuk menguji algoritma *scheduling* karena memungkinkan pengujian yang **aman, terkontrol, dan efisien** tanpa mengganggu sistem nyata, serta memudahkan **perbandingan kinerja** antar algoritma (waktu tunggu, turnaround time, utilisasi CPU).

2.apa perbedaan hasil simulasi dengan perhitungaqn manual jika dataset besar?
   **Jawaban:** jika dataset besar, perbedaan hasil antara simulasi dan perhitungan manual adalah:

>Simulasi: lebih akurat dan konsisten, mampu menangani data besar dan kompleks tanpa kesalahan manusia.

>Perhitungan manual: tidak efisien, rawan kesalahan, dan sering disederhanakan sehingga hasilnya kurang presisi.j 
3. algoritma mana yang lebih mudah diimplementasikan ? jelaskan!  
   **Jawaban:**Algoritma yang **paling mudah diimplementasikan adalah FCFS (First Come First Served)**.

**Penjelasan:**
FCFS sederhana karena proses dijalankan sesuai urutan kedatangan tanpa perhitungan tambahan seperti prioritas atau *time quantum*. Implementasinya cukup menggunakan **antrian (queue)**, sehingga mudah dipahami, dikodekan, dan dianalisis dibanding algoritma lain seperti SJF, Priority, atau Round Robin.
  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
