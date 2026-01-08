
# Laporan Praktikum Minggu [III]
Manajemen file dan izin linux

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

## Langkah Praktikum.
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

## Kode / Perintah
praktikum/week3-linux-fs-permission/
pwd
ls -l
cd /tmp
ls -a
cat /etc/passwd | head -n 5
echo "Hello <NAME><NIM>" > percobaan.txt
ls -l percobaan.txt
chmod 600 percobaan.txt
ls -l percobaan.txt
sudo chown root percobaan.txt
ls -l percobaan.txt
praktikum/week3-linux-fs-permission/screenshots/
git add .
git commit -m "Minggu 3 - Linux File System & Permission"
git push origin main
## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)

---

## Analisis
1. Menjelaskan makna hasil percobaan
Hasil percobaan menunjukkan bagaimana sistem operasi (OS) bekerja dalam mengatur komunikasi antara aplikasi pengguna (user space) dan kernel (kernel space).
Ketika program dijalankan, instruksi biasa diproses oleh CPU dalam mode pengguna, tetapi jika program membutuhkan layanan sistem (misalnya membaca file, mencetak data, atau mengakses perangkat keras), maka terjadi system call yang memindahkan kontrol ke mode kernel.
Maknanya, hasil percobaan memperlihatkan bahwa kernel bertanggung jawab penuh atas pengelolaan sumber daya dan menjaga agar pengguna tidak mengakses hardware secara langsung.

2. Menghubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS)
>Fungsi Kernel:
-Kernel berfungsi sebagai inti dari sistem operasi yang mengatur:
-Manajemen proses (menjalankan dan menghentikan program),
-Manajemen memori (alokasi RAM),
-Manajemen perangkat keras (I/O, disk, printer, dll).
-Hasil percobaan biasanya memperlihatkan bahwa tanpa kernel, proses tidak dapat berinteraksi dengan hardware secara aman.

>System Call:
System call adalah “jembatan” antara program pengguna dan kernel.
Misalnya, pada percobaan menjalankan perintah seperti ls, open(), atau write(), program tersebut tidak langsung mengakses disk tetapi memanggil system call yang diteruskan ke kernel.
Ini membuktikan teori bahwa setiap akses ke sumber daya dilakukan melalui system call, bukan langsung dari user mode.

>Arsitektur OS:
Jika hasil menunjukkan bahwa semua layanan dijalankan dalam satu ruang (monolitik), berarti OS menggunakan arsitektur monolitik seperti Linux.
Sedangkan jika layanan inti dipisah ke proses kecil (microkernel), hasil menunjukkan OS seperti Windows NT atau Minix.
Jadi hasil percobaan memperkuat teori bahwa arsitektur menentukan cara kernel menangani sistem call dan komponen sistem.

3. Perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)
Perbedaan hasil antara Linux dan Windows terletak pada kinerja, stabilitas, fleksibilitas, dan cara mengelola sistem file. Linux umumnya lebih unggul dalam hal kecepatan dan stabilitas, terutama pada perangkat keras lama, karena sifatnya yang open-source dan modular, sedangkan Windows lebih mengutamakan kemudahan penggunaan melalui antarmuka grafis (GUI) dan ekosistem aplikasi yang lebih terintegrasi.

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.

1. Kernel berperan sebagai inti sistem operasi yang mengatur seluruh aktivitas perangkat keras dan perangkat lunak agar berjalan terkoordinasi dengan aman dan efisien.

2. System call menjadi penghubung antara program pengguna dan kernel, memungkinkan aplikasi mengakses layanan sistem tanpa berinteraksi langsung dengan perangkat keras.

3. Perbedaan arsitektur OS (Linux dan Windows) memengaruhi cara kernel bekerja — Linux yang bersifat monolitik lebih terbuka dan cepat, sedangkan Windows dengan pendekatan microkernel lebih terstruktur dan aman.

#Quis
1. Fungsi dari perintah chmod
Perintah chmod (change mode) digunakan untuk mengubah izin (permission) akses file atau direktori di sistem operasi Linux/Unix.
Dengan chmod, kita bisa menentukan siapa saja yang boleh:
membaca (read - r),
menulis/mengubah (write - w), dan
menjalankan (execute - x) file atau folder.
Contoh:
chmod 755 script.sh
Artinya: pemilik bisa baca, tulis, dan jalankan; sedangkan pengguna lain hanya bisa baca dan jalankan.

2. Arti dari kode izin rwxr-xr--
Kode ini menunjukkan hak akses untuk tiga kelompok pengguna:
Bagian	Pengguna	Hak Akses	Arti
rwx	Pemilik (owner)	read, write, execute	Pemilik bisa membaca, mengubah, dan menjalankan file
r-x	Grup (group)	read, execute	Anggota grup hanya bisa membaca dan menjalankan file
r--	Lainnya (others)	read only	Pengguna lain hanya bisa membaca file
Jadi, rwxr-xr-- berarti:
> Pemilik penuh akses, grup hanya bisa baca/jalankan, dan orang lain hanya bisa membaca.

3. Perbedaan antara chown dan chmod
Perintah	Fungsi Utama	Contoh Penggunaan
chmod	Mengubah izin akses (read/write/execute) pada file atau folder.	chmod 644 file.t
chown	Mengubah kepemilikan (owner dan group) dari file atau folder.	chown user1:group1 file.txt
Kesimpulan:
chmod → mengatur apa yang bisa dilakukan pengguna.
chown → mengatur siapa pemilik file atau direktori.

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
