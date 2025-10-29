
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

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
> Mahasiswa mampu memecahkan masalah
> Mahasiswa mampu mengelola sumber daya secara efisien
> Mahasiswa mampu memahami bagaimana perangkat lunak dan keras berkomunikassi
> Mahasiswa mampu merancang sistem yang stabil
---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.

🧩 1. Teori Sistem Operasi

Teori ini menjadi dasar utama dalam percobaan arsitektur sistem operasi. Fokusnya adalah bagaimana sistem operasi mengatur sumber daya komputer dan menyediakan layanan bagi pengguna serta apli:
.Manajemen sumber daya (resource management): CPU, memori, perangka
.Abstraksi: Sistem operasi menyembunyikan detail perangkat keras melalui antarmuka yang mudah digunakan.
.Proteksi dan keamanan: Mengatur hak akses antar proses agar tidak saling mengganggu.
.Konkurensi: Menangani proses yang berjalan bersamaan (multitasking, multiprogramming).

## Langkah Praktikum
Lingkungan Pengaturan

Pastikan Linux (Ubuntu/WSL) sudah terinstal.
Pastikan Git sudah dikonfigurasi dengan benar:
git config --global user.name "Nama Anda"
git config --global user.email "email@contoh.com"
Diskusi Konsep

Baca materi pengantar tentang komponen OS.
identifikasi komponen yang ada pada Linux/Windows/Android.
Eksperimen Dasar Jalankan perintah berikut di terminal:

uname -a
whoami
lsmod | head
dmesg | head
Katat dan analisis modul kernel yang ditampilkan.

Membuat Diagram Arsitektur

Buat diagram hubungan antara User → System Call → Kernel → Hardware.
Gunakan draw.io atau Mermaid .
Simpan hasil di:
praktikum/week1-intro-arsitektur-os/screenshots/diagram-os.png
Penulisan Laporan

Tuliskan hasil pengamatan, analisis, dan kesimpulan ke dalam laporan.md.
Tambahkan tangkapan layar hasil terminal ke folder screenshots/.
Komit & Dorong

git add .
git commit -m "Minggu 1 - Arsitektur Sistem Operasi dan Kernel"
git push origin main

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

1. Menjelaskan makna hasil percobaan
Hasil percobaan menggambarkan bagaimana kernel berfungsi sebagai inti sistem operasi, yang mengatur komunikasi antara software (user space) dan hardware (kernel space).
2. Menghubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS)
Hasil percobaan dapat dikaitkan dengan teori sebagai berikut:
Teori	Hubungannya dengan Hasil Percobaan
Fungsi Kernel	Kernel bertugas mengatur CPU, memori, dan perangkat I/O. Jika hasil percobaan menunjukkan waktu akses file atau respon sistem berbeda, itu berarti kernel sedang melakukan manajemen sumber daya sesuai kebijakan tertentu (misalnya, scheduling atau buffering).
System Call	Saat program memanggil layanan OS (misalnya read(), write(), fork()), kernel mengeksekusi system call. Percobaan yang mengamati system call menunjukkan interaksi antara user mode dan kernel mode.
Arsitektur OS	Hasil dapat menggambarkan bagaimana struktur OS (monolithic, microkernel, modular) memengaruhi kinerja. Contohnya, sistem berbasis microkernel mungkin lebih lambat karena lebih banyak context switch dibandingkan monolithic kernel.
3. Perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)
Aspek	Linux	Windows
Jenis Kernel	Monolithic (namun modular, banyak fungsi di dalam kernel).	Hybrid (gabungan microkernel dan monolithic).
System Call Interface	Terbuka, standar POSIX — dapat diamati langsung melalui terminal (misalnya strace).	Tertutup dan kompleks, tidak sepenuhnya POSIX compliant.
Kinerja Proses	Proses ringan, efisien pada multitasking dan server.	Optimasi lebih kuat untuk GUI dan aplikasi pengguna.
Keamanan & Hak Akses	Berbasis izin (permission) ketat per file dan user.	Lebih kompleks, dengan ACL (Access Control List).
Hasil Percobaan Umum	Respon system call lebih cepat, transparansi tinggi (mudah diamati).	Lebih lambat untuk eksperimen kernel-level, banyak fungsi tersebut.

Jadi perbedaan hasil antara Linux dan Windows umumnya disebabkan oleh perbedaan arsitektur kernel, model system call, serta cara pengelolaan sumber daya.
Linux biasanya menunjukkan hasil yang lebih mudah dianalisis dan transparan untuk penelitian sistem operasi 

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini

Dari hasil percobaan mengenai arsitektur sistem operasi dan kernel dapat disimpulkan bahwa kernel memiliki peran utama sebagai inti sistem operasi yang bertugas mengatur komunikasi antara perangkat keras dan perangkat lunak. Melalui mekanisme system call, aplikasi di user space dapat meminta layanan sistem seperti pengelolaan memori, proses, dan perangkat I/O yang dijalankan oleh kernel di kernel space.

Hasil pengamatan menunjukkan bahwa perbedaan arsitektur kernel, seperti monolithic kernel pada Linux dan hybrid kernel pada Windows, memengaruhi kinerja, efisiensi, serta transparansi sistem. Linux cenderung lebih terbuka dan mudah dianalisis pada level kernel, sementara Windows memiliki struktur lebih kompleks namun stabil untuk lingkungan pengguna umum.

Secara keseluruhan, percobaan ini memperlihatkan bahwa arsitektur kernel dan mekanisme system call sangat menentukan kinerja, keamanan, dan interaksi sistem operasi dalam menjalankan tugasnya mengelola sumber daya komputer.


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
