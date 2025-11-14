
# Laporan Praktikum Minggu [IV]
Topik: Manajemen Proses dan User di Linux


## Identitas
- **Nama**  : [Aisyah Nurur Rohmah]  
- **NIM**   : [250320585]  
- **Kelas** : [1DSRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.
>Menjelaskan konsep proses dan user dalam sistem operasi Linux.
>Menampilkan daftar proses yang sedang berjalan dan statusnya.
>Menggunakan perintah untuk membuat dan mengelola user.
>Menghentikan atau mengontrol proses tertentu menggunakan PID.
>Menjelaskan kaitan antara manajemen user dan keamanan sistem.

---

## Dasar Teori

1. Interaksi Manusia-Komputer (HCI)
HCI adalah bidang studi yang berfokus pada desain, evaluasi, dan implementasi sistem komputasi interaktif untuk digunakan oleh manusia, serta studi tentang fenomena utama di sekitarnya. 
Tujuan utama: Memastikan interaksi antara manusia dan komputer seefektif dan seefisien mungkin.
Penerapan dalam percobaan user: Percobaan ini mengevaluasi bagaimana pengguna berinteraksi dengan sistem atau produk, mengukur aspek seperti efisiensi, tingkat kesalahan, dan waktu yang dibutuhkan untuk menyelesaikan tugas. 
2. Pengalaman Pengguna (User Experience - UX)
UX mencakup semua aspek pengalaman pengguna saat menggunakan suatu produk, termasuk kemudahan penggunaan, relevansi konten, dan bagaimana perasaan pengguna saat memakainya. 
Tujuan utama: Menciptakan pengalaman yang positif, bermakna, dan relevan bagi pengguna.
Penerapan dalam percobaan user: Percobaan sering kali fokus pada kepuasan subjektif pengguna, kemudahan memahami cara kerja produk, dan pencapaian tujuan pengguna melalui produk tersebut. 
3. Antarmuka Pengguna (User Interface - UI)
UI adalah titik interaksi antara pengguna dan produk, yang mencakup semua elemen visual dan interaktif. 
Tujuan utama: Merancang antarmuka yang estetis dan mudah digunakan, yang berfungsi sebagai penghubung antara pengguna dan sistem.
Prinsip yang mendasari: Berpusat pada pengguna, konsistensi, responsif, kesederhanaan, dan minimalisasi kesalahan. 
4. Usability Testing (Pengujian Kegunaan)
Dasar Teori: Metode ini didasari oleh prinsip-prinsip kegunaan (usability) yang dikemukakan oleh para ahli seperti Jacob Nielsen. Pengujian kegunaan melibatkan pengguna nyata untuk mengevaluasi fungsi produk, mengidentifikasi masalah, dan meningkatkan pengalaman pengguna secara keseluruhan.
Fokus Pengujian:
Efektivitas: Apakah pengguna dapat mencapai tujuan mereka secara akurat dan lengkap?
Efisiensi: Berapa banyak sumber daya (waktu, langkah) yang dibutuhkan pengguna untuk mencapai tujuan?
Kepuasan: Seberapa puas pengguna dengan pengalaman interaksi tersebut? 
Secara ringkas, dasar teori untuk percobaan proses user adalah pemahaman mendalam tentang perilaku manusia, psikologi kognitif dalam interaksi dengan teknologi, dan prinsip-prinsip desain yang berpusat pada pengguna (user-centered design/UCD) untuk menciptakan sistem yang efektif dan memuaskan. 
---
## Langkah Praktikum

1.Setup Environment
GLingkungan Pengaturan

Gunakan Linux (Ubuntu/WSL).
Pastikan Anda sudah login sebagai user non-root.
Siapkan folder kerja:
praktikum/week4-proses-user/
2.Eksperimen 1 – Identitas Pengguna Jalankan perintah berikut:

whoami
id
groups
Menjelaskan setiap keluaran dan fungsinya.
Buat pengguna baru (jika memiliki izin sudo):
sudo adduser praktikan
sudo passwd praktikan
Uji login ke user baru.
3.Eksperimen 2 – Monitoring Proses Jalankan:

ps aux | head -10
top -n 1
menjelaskan kolom penting seperti PID, USER, %CPU, %MEM, COMMAND.
Simpan tangkapan layar topke:
praktikum/week4-proses-user/screenshots/top.png
4.Eksperimen 3 – Kontrol Proses

Jalankan program latar belakang:
sleep 1000 &
ps aux | grep sleep
Catat PID proses sleep.
Hentikan proses:
kill <PID>
Pastikan proses telah berhenti dengan ps aux | grep sleep.
5.Eksperimen 4 – Analisis Hierarki Proses Jalankan:

pstree -p | head -20
Amati proses hierarki dan identifikasi proses induk ( init/ systemd).
Catat hasilnya dalam laporan.
6.Komit & Dorong

git add .
git commit -m "Minggu 4 - Manajemen Proses & User"
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
1. Makna Hasil Percobaan
Hasil percobaan menunjukkan bagaimana interaksi antara aplikasi, sistem operasi, dan perangkat keras terjadi melalui system call.
Ketika program dijalankan, proses tersebut tidak berkomunikasi langsung dengan perangkat keras, tetapi melalui kernel.
Dari hasil percobaan (misalnya menggunakan perintah seperti strace atau dmesg), dapat terlihat bahwa:
Setiap perintah aplikasi menghasilkan serangkaian system call (seperti open(), read(), write(), close()).
Kernel bertugas menangani panggilan ini dan mengatur akses sumber daya secara aman dan efisien.
Artinya, percobaan ini membuktikan bahwa kernel menjadi jembatan utama antara pengguna dan perangkat keras, serta memastikan sistem tetap stabil dan terlindungi dari akses ilegal.

2. Hubungan Hasil dengan Teori

Fungsi Kernel: Teori menyebutkan bahwa kernel memiliki peran utama dalam manajemen proses, memori, dan perangkat keras. Hasil percobaan mendukung teori ini karena terlihat kernel selalu menangani permintaan aplikasi melalui system call.

System Call: Dalam teori, system call adalah antarmuka resmi untuk mengakses layanan kernel. Dari hasil percobaan, terlihat bahwa tanpa system call, aplikasi tidak bisa berinteraksi dengan sistem file, jaringan, atau perangkat keras.

Arsitektur OS: Teori arsitektur sistem operasi (monolitik vs mikrokernel) menjelaskan bagaimana system call diimplementasikan. Pada Linux (monolitik), sebagian besar layanan sistem berjalan di kernel mode, sedangkan pada sistem mikrokernel (contoh: Windows dengan model hybrid), sebagian layanan dijalankan di ruang pengguna untuk meningkatkan keamanan dan modularitas.

3. Perbedaan Hasil di Lingkungan OS Berbeda (Linux vs Windows)

Aspek	Linux	Windows

Jenis Kernel	Monolitik	Hybrid (campuran monolitik & mikrokernel)
Akses System Call	Terbuka, bisa diamati dengan alat seperti strace	Tertutup, perlu alat khusus seperti Process Monitor
Transparansi Proses	Proses kernel dan system call mudah diamati secara detail	Lebih sulit diamati karena sistem tertutup dan proteksi lebih ketat
Efisiensi & Kustomisasi	Lebih efisien dan fleksibel untuk modifikasi	Lebih stabil untuk pengguna umum, tapi kurang terbuka untuk pengembangan kernel

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.
1. Kernel berfungsi sebagai penghubung utama antara aplikasi pengguna dan perangkat keras, sehingga setiap perintah yang dijalankan oleh program akan melewati kernel melalui mekanisme system call.

2. System call membuktikan peran penting sistem operasi dalam mengatur akses sumber daya, menjaga keamanan, dan memastikan proses berjalan dengan terkontrol.

3. Perbedaan arsitektur OS (Linux dan Windows) memengaruhi cara kerja system call — Linux lebih terbuka dan transparan, sedangkan Windows lebih tertutup namun fokus pada stabilitas dan keamanan sistem.

## Quiz
1. Fungsi dari Proses init atau systemd dalam Sistem Linux
init atau systemd adalah proses pertama yang dijalankan oleh kernel setelah sistem dinyalakan (PID 1).
Fungsinya:
1. Menginisialisasi sistem dan menyiapkan lingkungan kerja (menjalankan skrip startup).
2. Mengatur dan menjalankan semua layanan (services) serta proses background (daemon).
3. Memantau dan mengelola proses yang berjalan selama sistem aktif, serta menangani proses anak yang berhenti (zombie).
Saat ini, sebagian besar distro Linux modern menggunakan systemd karena lebih cepat, efisien, dan mendukung parallel booting.
2. Perbedaan antara kill dan killall
Aspek	kill	killall
Fungsi utama	Mengirim sinyal ke proses tertentu berdasarkan PID (Process ID).	Mengirim sinyal ke semua proses dengan nama tertentu.
Contoh perintah	kill 1234 → mengakhiri proses dengan PID 1234	killall firefox → mengakhiri semua proses bernama firefox
Penggunaan umum	Digunakan jika kamu tahu PID dari proses target.	Digunakan jika kamu tahu nama program, bukan PID.
3. Alasan User root Memiliki Hak Istimewa di Sistem Linux
root adalah superuser, yaitu pengguna dengan akses penuh terhadap seluruh sistem.
Hak istimewa ini diperlukan agar root dapat:

1. Mengelola sistem secara menyeluruh (menginstal paket, mengubah konfigurasi, membuat/menghapus pengguna).

2. Mengakses dan memodifikasi semua file, termasuk file sistem yang dilindungi.

3. Melakukan operasi administratif seperti mounting, network configuration, atau service control.
   
Karena itu, penggunaan akun root harus hati-hati — kesalahan perintah dapat merusak sistem secara permanen.

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
