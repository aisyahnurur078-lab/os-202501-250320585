
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Aisyah Nurur Rohmah]  
- **NIM**   : [250320585]  
- **Kelas** : [1DSRA]

---

## Tujuan
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.
>Mengidentifikasi empat kondisi penyebab deadlock (mutual exclusion, hold and wait, no preemption, circular wait).
>Menjelaskan mekanisme sinkronisasi menggunakan semaphore atau monitor.
>Menganalisis dan memberikan solusi untuk kasus deadlock.
>Berkolaborasi dalam tim untuk menyusun laporan analisis.
>Menyajikan hasil studi kasus secara sistematis.


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

1. Sebutkan empat kondisi utama penyebab deadlock
> Mutual Exclusion – Sumber daya tidak dapat digunakan bersama pada waktu bersamaan.
> Hold and Wait – Proses memegang satu sumber daya sambil menunggu sumber daya lain.
> No Preemption – Sumber daya tidak bisa diambil paksa dari proses yang sedang menggunakannya.
> Circular Wait – Terjadi rantai proses yang saling menunggu sumber daya satu sama lain secara melingkar.

2. Mengapa sinkronisasi diperlukan dalam sistem operasi?
>Sinkronisasi diperlukan untuk:
>Menghindari konflik saat beberapa proses mengakses data bersama (race condition).
>Menjamin konsistensi data dan urutan eksekusi yang benar.
>Mencegah terjadinya deadlock dan starvation.

3. Jelaskan perbedaan antara semaphore dan monitor
Aspek	Semaphore	Monitor
Tipe Mekanisme	Primitive (variabel counter)	Struktur tingkat tinggi (objek sinkronisasi)
Penggunaan	Menggunakan operasi wait() dan signal()	Menggunakan prosedur dan variabel kondisi
Kompleksitas	Lebih manual, rawan kesalahan	Lebih mudah dan aman digunakan
Dukungan Bahasa	Tersedia di hampir semua OS	Biasanya didukung di bahasa tingkat tinggi (Java, C#, dsb.)


## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
