
# Laporan Praktikum Minggu [IX]
Topik: [Simulasi Algoritma Penjadwalan CPU]

---

## Identitas
- **Nama**  : [Aisyah Nurur Rohmah]  
- **NIM**   : [250320585]  
- **Kelas** : [1DSRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.

---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.

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
