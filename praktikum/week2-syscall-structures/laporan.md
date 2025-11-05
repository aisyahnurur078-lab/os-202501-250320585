
# Laporan Praktikum Minggu [II]
Topik: [Struktur System Operasi dan fungsi kernel]

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
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.

---

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.  
2. Perintah yang dijalankan.  
3. File dan kode yang dibuat.  
4. Commit message yang digunakan.

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

2. Diagram Alur System Call

Berikut diagram alur sederhana dari aplikasi hingga hardware dan kembali:

+--------------------------+
|     Aplikasi (User)     |
|  Contoh: 'cat file.txt' |
+------------+-------------+
             |
             | 1. System Call (read)
             v
+--------------------------+
|   Kernel Mode (OS)       |
| - Mengecek izin akses    |
| - Mengatur resource I/O  |
| - Panggil driver terkait |
+------------+-------------+
             |
             | 2. Akses Hardware
             v
+--------------------------+
|   Hardware (Disk, CPU)   |
| - Baca/ambil data file   |
+------------+-------------+
             |
             | 3. Kembali ke Kernel
             v
+--------------------------+
|   Kernel Mode (OS)       |
| - Menyalin hasil ke memori |
+------------+-------------+
             |
             | 4. Kembali ke Aplikasi
             v
+--------------------------+
|   Aplikasi (User Space)  |
| - Menampilkan hasil ke layar |
+--------------------------+

3. Analisis (±450 kata)

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
Tuliskan 2–3 poin kesimpulan dari praktikum ini.

---

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
