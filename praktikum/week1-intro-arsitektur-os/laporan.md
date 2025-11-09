
# Laporan Praktikum Minggu [l]
Topik:Arsitektur Sistem Operasi 

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
git config --global user.name "Nama Anda"
git config --global user.email "email@contoh.com"
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
1. [tiga persamaan fungsi utama sistem operasi.] 
   **Jawaban:**
  a. Manajemen Sumber Daya (Resource Management)
OS mengatur dan mengelola seluruh sumber daya komputer seperti CPU, memori, perangkat penyimpanan, dan perangkat input/output agar dapat digunakan secara efisien oleh berbagai program dan pengguna.
Contohnya: mengatur giliran proses yang memakai CPU (CPU scheduling), mengalokasikan memori untuk program yang berjalan, dan mengatur akses ke hard disk.
b. Manajemen File dan Sistem I/O (File and Input/Output Management)
OS menyediakan cara untuk menyimpan, mengatur, membaca, menulis, dan menghapus file, serta mengontrol komunikasi antara perangkat keras (hardware) dan perangkat lunak (software).
Contohnya: mengatur sistem berkas (file system), driver perangkat, dan operasi seperti membuka atau menutup file.
c. Manajemen Proses dan Pengguna (Process and User Management)
OS bertanggung jawab untuk membuat, menjalankan, menghentikan, dan mengatur komunikasi antar proses. Selain itu, OS juga menangani keamanan dan hak akses pengguna.
Contohnya: mengatur multitasking (beberapa program berjalan bersamaan) dan memastikan tiap pengguna memiliki hak akses sesuai perannya.

 3. [menjelaskan perbedaan antara mode kernel dan mode pengguna ]
   **Jawaban:**
1. Mode Kernel (Kernel Mode) adalah mode istimewa di mana sistem operasi memiliki akses penuh ke seluruh sumber daya komputer, termasuk perangkat keras.
Ciri-ciri:
-Dapat menjalankan instruksi sistem yang kritis (misalnya mengakses memori, CPU, dan perangkat keras).
-Jika terjadi kesalahan di mode kernel, seluruh sistem bisa crash (gagal total).
-Digunakan oleh bagian inti sistem operasi (kernel) dan driver perangkat.
Contoh:
Ketika OS mengatur proses, mengelola memori, atau mengakses disk langsung, semua berjalan di mode kernel.
 2. Mode Pengguna (User Mode) adalah mode di mana program aplikasi biasa berjalan dengan akses terbatas terhadap sumber daya sistem.
Ciri-ciri:
-Tidak dapat langsung mengakses perangkat keras atau memori inti.
-Jika terjadi kesalahan, hanya program itu saja yang berhenti, bukan seluruh sistem.
-Program yang butuh akses kernel harus meminta lewat system call.
Contoh:
Aplikasi seperti Microsoft Word, browser, atau game berjalan di mode pengguna dan memanggil layanan OS lewat system call (misalnya untuk menyimpan foto 
4. [Menunjuk contoh OS dengan arsitektur monolitik dan mikrokernel ]
   **Jawaban:**  
Berikut contoh sistem operasi berdasarkan jenis arsitekturnya:
1. Arsitektur Monolitik adalah jenis sistem operasi di mana seluruh komponen inti (seperti manajemen memori, proses, file system, dan driver perangkat) dijalankan dalam satu ruang kernel. Semua bagian kernel saling terhubung langsung tanpa pemisahan modul besar.
Contoh OS dengan arsitektur monolitik:
-MS-DOS
-UNIX
-Linux (seperti Ubuntu, Debian, Fedora
 2. Arsitektur mikrokernel
Pada arsitektur mikrokernel, hanya fungsi-fungsi dasar sistem operasi yang dijalankan di kernel (seperti komunikasi antar proses dan manajemen memori sederhana). Komponen lain seperti driver, file system, dan manajemen perangkat dijalankan di mode pengguna.
Contoh OS dengan arsitektur mikrokernel:
-MINIX
-QNX
-Mach (digunakan pada macOS dan iOS)
## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?
- menjadi mahasiswa baru di universitas putra bangsa dan langsung mendapatkan banyak tugas 
- Bagaimana cara Anda mengatasinya?
- mengatasinya dengan menjakani dengan lapang dada,jiga saat mengerjakan tugas saya tidak paham saya akan bertanya kpn teman.

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
