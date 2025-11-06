
# Laporan Praktikum Minggu [II]
Topik: [Struktur System Call dan fungsi kernel]

---

## Identitas
- **Nama**  : [Aisyah Nurur Rohmah]  
- **NIM**   : [250320585]  
- **Kelas** : [1DSRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  

>Menjelaskan konsep dan fungsi system call dalam sistem operasi.
>Mengidentifikasi jenis-jenis system call dan fungsinya.
>Mengamati alur perpindahan mode user ke kernel saat system call terjadi.
>Menggunakan perintah Linux untuk menampilkan dan menganalisis system call.

---

## Dasar Teori

1. Sistem operasi (OS) berfungsi sebagai penghubung antara pengguna dan perangkat keras komputer, mengelola sumber daya seperti CPU, memori, dan perangkat I/O.

2. Kernel adalah inti dari sistem operasi yang beroperasi di kernel mode dan bertanggung jawab atas eksekusi system call, manajemen proses, memori, serta komunikasi antar-perangkat.

3. System call merupakan mekanisme utama yang digunakan program pengguna (user mode) untuk meminta layanan dari kernel, seperti membaca file, membuat proses baru, atau mengakses perangkat.

4. Pemisahan mode pengguna dan mode kernel bertujuan menjaga keamanan dan stabilitas sistem agar pengguna tidak dapat mengakses sumber daya kritis secara langsung.

5. Alat bantu seperti strace dan dmesg digunakan untuk menganalisis interaksi antara aplikasi dan kernel, membantu memahami bagaimana system call bekerja selama eksekusi program.

## Langkah Praktikum

1.Setup Environment
Gunakan Linux (Ubuntu/WSL).
Pastikan perintah strace dan man sudah terinstal.
Konfigurasikan Git (jika belum dilakukan di minggu sebelumnya)

2.Eksperimen 1 – Analisis System Call Jalankan perintah berikut:
strace ls
Catat 5–10 system call pertama yang muncul dan jelaskan fungsinya.
Simpan hasil analisis ke results/syscall_ls.txt.

3.Eksperimen 2 – Menelusuri System Call File I/O Jalankan:
strace -e trace=open,read,write,close cat /etc/passwd
Analisis bagaimana file dibuka, dibaca, dan ditutup oleh kernel.

4. Eksperimen 3 – Mode User vs Kernel Jalankan:
dmesg | tail -n 10
Amati log kernel yang muncul. Apa bedanya output ini dengan output dari program biasa?
Diagram Alur System Call

5. Buat diagram yang menggambarkan alur eksekusi system call dari program user hingga kernel dan kembali lagi ke user mode.
Gunakan draw.io / mermaid.
Simpan di:
praktikum/week2-syscall-structure/screenshots/syscall-diagram.png
Commit & Push

6.git add .
git commit -m "Minggu 2 - Struktur System Call dan Kernel Interaction"
git push origin main


## Kode / Perintah
strace ls
strace -e trace=open,read,write,close cat /etc/passwd
dmesg | tail -n 10
praktikum/week2-syscall-structure/screenshots/syscall-diagram.png
git add .
git commit -m "Minggu 2 - Struktur System Call dan Kernel Interaction"
git push origin main

##Tugas dan Kuis

1.Dokumentasikan hasil eksperimen strace dan dmesg dalam bentuk tabel observasi.

2.Buat diagram alur system call dari aplikasi → kernel → hardware → kembali ke aplikasi.

3.Tulis analisis 400–500 kata tentang:
     -Mengapa system call penting untuk keamanan OS?
     -Bagaimana OS memastikan transisi user–kernel berjalan aman?
     -Sebutkan contoh system call yang sering digunakan di Linux.
     
4.Simpan semua hasil di:
praktikum/week2-syscall-structure/

1. Tabel Observasi Hasil Eksperimen strace dan dmesg

Perintah / Aksi	Hasil / Cuplikan Output	Makna Observasi

strace ls	`openat(AT_FDCWD, ".", O_RDONLY	O_NONBLOCK
strace cat file.txt	read(3, "Isi file...", 1024) = 12 → write(1, "Isi file...", 12)	System call read() membaca isi file dari disk, lalu write() menulis output ke terminal.
strace echo "Halo"	write(1, "Halo\n", 5)	Perintah echo menggunakan system call write() untuk menampilkan teks ke layar.
`dmesg	tail`	[ 120.45321] usb 1-1: new high-speed USB device number 5 using xhci_hcd
`dmesg	grep error`	[ 78.12345] ext4-fs error (device sda1): ext4_find_entry:1456

2. Analisis (±450 kata)

System call adalah mekanisme penting yang memungkinkan aplikasi di user space berkomunikasi dengan kernel space tanpa langsung mengakses perangkat keras. Mekanisme ini menjadi jembatan antara program pengguna dan sumber daya sistem operasi seperti memori, file, dan perangkat I/O. Tanpa system call, aplikasi tidak dapat berinteraksi dengan sistem karena kernel beroperasi di mode yang terlindungi.

a. Pentingnya System Call untuk Keamanan OS

System call berperan besar dalam menjaga keamanan sistem operasi. Kernel melindungi akses langsung ke perangkat keras agar aplikasi pengguna tidak bisa merusak atau mengganggu sistem. Semua interaksi dengan hardware harus melalui system call yang telah diawasi.
Misalnya, ketika program mencoba membuka file menggunakan open(), kernel akan memeriksa apakah pengguna memiliki izin (permission) untuk mengakses file tersebut. Jika tidak, kernel akan menolak permintaan dan mengembalikan pesan error. Dengan demikian, system call mencegah aplikasi berperilaku berbahaya, menjaga integritas data, serta melindungi sistem dari eksploitasi dan crash.

b. Keamanan Transisi dari Mode Pengguna ke Mode Kernel

Transisi antara user mode dan kernel mode dilakukan secara hati-hati menggunakan mekanisme trap atau interrupt. Saat system call dipanggil, prosesor beralih dari ring 3 (user mode) ke ring 0 (kernel mode). OS memastikan proses ini aman dengan:
Menyediakan system call table berisi fungsi kernel yang sah.
Melakukan validasi argumen agar tidak terjadi akses memori ilegal.
Menjaga isolasi antar proses sehingga satu aplikasi tidak dapat mengubah data proses lain. Setelah kernel menyelesaikan tugasnya, kontrol dikembalikan ke user mode dengan aman. Proses ini mencegah pengguna mengambil alih kontrol kernel atau mengakses memori yang dilindungi.

c. Contoh System Call Umum di Linux
Beberapa system call yang sering digunakan antara lain:
open(), read(), write(), dan close() → untuk operasi file.
fork() dan exec() → untuk membuat dan menjalankan proses baru.
wait() → menunggu proses anak selesai.
exit() → mengakhiri proses.
socket() dan connect() → komunikasi jaringan. System call ini menjadi dasar bagi hampir semua program Linux — mulai
dari terminal, server web, hingga browser — untuk berinteraksi dengan kernel dan perangkat keras dengan cara yang aman dan terstandarisasi.

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

1. System call berperan penting sebagai penghubung antara aplikasi dan kernel, memungkinkan program pengguna mengakses layanan inti sistem operasi secara aman tanpa langsung berinteraksi dengan perangkat keras.


2. Keamanan dan stabilitas sistem dijaga melalui pemisahan mode pengguna dan mode kernel, sehingga hanya kernel yang memiliki hak penuh untuk mengelola sumber daya sistem.


3. Melalui observasi menggunakan perintah seperti strace dan dmesg, dapat dipahami bagaimana proses komunikasi terjadi antara aplikasi, kernel, dan perangkat keras dalam menjalankan operasi sistem.

## Quiz

1. Fungsi utama system call dalam sistem operasi

Fungsi utama system call adalah sebagai jembatan antara program pengguna (user space) dan kernel sistem operasi (kernel space).
System call memungkinkan program untuk meminta layanan dari kernel, seperti:

Membaca/menulis berkas (file I/O)

Mengalokasikan memori

Membuat atau menghapus proses

Mengatur komunikasi antar-proses


Dengan kata lain, system call menyediakan antarmuka resmi untuk berinteraksi dengan sumber daya perangkat keras melalui kernel, sehingga program tidak perlu (dan tidak diizinkan) mengakses perangkat keras secara langsung.


---

2. Empat kategori system call yang umum digunakan

System call umumnya dibagi ke dalam empat kategori utama:

Kategori	Fungsi Utama	Contoh System Call di Linux

1. Process Control	Mengatur pembuatan, penghentian, dan pengelolaan proses	fork(), exec(), exit(), wait()
2. File Management	Mengelola berkas dan direktori	open(), read(), write(), close()
3. Device Management	Mengontrol dan berinteraksi dengan perangkat I/O	ioctl(), read(), write()
4. Information Maintenance & Communication	Menyediakan informasi sistem dan komunikasi antar-proses	getpid(), alarm(), pipe(), shmget()



---

3. Mengapa panggilan sistem tidak bisa dipanggil langsung oleh pengguna program

System call tidak dapat dipanggil langsung oleh program pengguna karena alasan keamanan dan stabilitas sistem operasi.

Penjelasannya:

Perlindungan kernel: Kernel memiliki hak akses tertinggi (mode kernel), sedangkan aplikasi berjalan di mode pengguna (user mode). Jika pengguna bisa langsung mengakses kernel, maka ia bisa merusak sistem atau mengambil alih kontrol penuh.

Kontrol akses: System call memastikan bahwa setiap permintaan (misalnya akses file atau perangkat) diverifikasi dan dibatasi sesuai izin pengguna.

Stabilitas sistem: Dengan perantara system call, OS dapat mencegah crash atau konflik antar-proses.


Jadi, semua interaksi antara aplikasi dan kernel harus melalui mekanisme system call agar sistem tetap aman dan terkontrol.

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
