
# Laporan Praktikum Minggu [III]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Aisyah Nurur Rohmah]  
- **NIM**   : [250320585]  
- **Kelas** : [1DSRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini:  
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.
>Menggunakan perintah ls, pwd, cd, catuntuk navigasi file dan direktori.
>Menggunakan chmoddan chownuntuk manajemen hak akses file.
>Menjelaskan hasil output dari perintah dasar Linux.
>Menyusun laporan praktikum dengan struktur yang benar.
>Mengunggah dokumentasi hasil ke Git Repository tepat waktu.


## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan
1. Konsep Sistem Operasi
Sistem operasi (Operating System/OS) adalah perangkat lunak yang berfungsi sebagai penghubung antara pengguna (user) dan perangkat keras komputer (hardware). Sistem operasi mengatur seluruh aktivitas komputer seperti pengelolaan proses, memori, file, perangkat keras, serta komunikasi antar sistem.
Linux merupakan salah satu sistem operasi yang termasuk dalam keluarga UNIX-like, yang bersifat open source dan multiuser-multitasking, artinya dapat digunakan oleh banyak pengguna secara bersamaan dan dapat menjalankan banyak proses pada waktu yang sama.
2. Kernel Linux
Kernel merupakan inti dari sistem operasi. Ia bertugas mengontrol semua sumber daya sistem, termasuk CPU, memori, dan perangkat keras lainnya.
Fungsi utama kernel meliputi:
Manajemen proses: mengatur proses yang sedang berjalan (menjadwalkan, menghentikan, dan melanjutkan proses).
Manajemen memori: mengalokasikan dan mengontrol penggunaan memori untuk setiap proses.
Manajemen sistem file: mengatur penyimpanan, pembuatan, dan penghapusan file.
Manajemen perangkat: mengatur komunikasi antara perangkat keras dan perangkat lunak.
Manajemen keamanan: mengatur hak akses pengguna terhadap sistem.
3. Shell
Shell adalah antarmuka antara pengguna dan sistem operasi yang menerima perintah (command) dari pengguna dan meneruskannya ke kernel untuk dieksekusi.
Beberapa jenis shell di Linux:
Bash (Bourne Again Shell)
Zsh (Z Shell)
Ksh (Korn ).
4. Struktur Sistem File Linux
Sistem file Linux memiliki struktur hierarki tunggal yang dimulai dari root (/). Semua file dan direktori berada di bawah root.
Contoh struktur:
/
├── bin     → berisi perintah dasar sistem
├── etc     → berisi file konfigurasi sistem
├── home    → berisi direktori pengguna
├── dev     → berisi file perangkat
├── tmp     → file sementara
├── var     → file log dan variabel
5. Manajemen Proses
Linux adalah multitasking OS, yang berarti dapat menjalankan banyak proses sekaligus.
Setiap proses memiliki Process ID (PID) dan dikontrol oleh kernel melalui scheduler.
Perintah umum:
ps → melihat daftar proses
top → memantau proses aktif
kill → menghentikan proses
6. Manajemen Pengguna dan Hak Akses
Linux memiliki sistem user management yang kuat, dengan pembagian hak akses:
Root (administrator)
User biasa
Hak akses file dibagi menjadi:
r (read) → membaca file
w (write) → menulis/me (execute) → menjalankan program
Percobaan bisa melibatkan perintah chmod, chown, dan sudo.
Kesimpulan Teori
Percobaan Linux didasari oleh konsep arsitektur sistem operasi, kernel, manajemen sumber daya, dan komunikasi antara user–kernel. Dengan memahami teori ini, pengguna dapat mengenal cara kerja internal Linux serta mengoperasikan sistem secara efisien melalui perintah dan pengelolaan proses.

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.  
2. Perintah yang dijalankan.  
3. File dan kode yang dibuat.  
4. Commit message yang digunakan.
1.Lingkungan Pengaturan
Gunakan Linux (Ubuntu/WSL).
Pastikan folder kerja berada di dalam direktori repositori Git praktikum:
praktikum/week3-linux-fs-permission/

2.Eksperimen 1 – Navigasi Sistem File Jalankan perintah berikut:
pwd
ls -l
cd /tmp
ls -a
Jelaskan hasil tiap perintah.
Catat direktori aktif, isi folder, dan file tersembunyi (jika ada).

3.Eksperimen 2 – Membaca File Jalankan perintah:
cat /etc/passwd | head -n 5
Menjelaskan isi file dan struktur barisnya (user, UID, GID, home, shell)
.
4.Eksperimen 3 – Izin & Kepemilikan Buat file baru:
echo "Hello <NAME><NIM>" > percobaan.txt
ls -l percobaan.txt
chmod 600 percobaan.txt
ls -l percobaan.txt
Analisis perbedaan sebelum dan sesudah chmod.
Ubah file pemilik (jika memiliki izin sudo):
sudo chown root percobaan.txt
ls -l percobaan.txt
Catat hasil.

5.Eksperimen 4 – Dokumentasi
Ambil tangkapan layar hasil terminal dan simpan di:
praktikum/week3-linux-fs-permission/screenshots/
Tambahkan hasil analisis pada laporan.md.
Komit & Dorong

git add .
git commit -m "Minggu 3 - Linux File System & Permission"
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
