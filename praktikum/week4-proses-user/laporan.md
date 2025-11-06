
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

Gunakan Linux (Ubuntu/WSL).
Pastikan Anda sudah login sebagai user non-root.
Siapkan folder kerja:
praktikum/week4-proses-user/
2.Eksperimen 1 – Identitas User Jalankan perintah berikut:

whoami
id
groups
Jelaskan setiap output dan fungsinya.
Buat user baru (jika memiliki izin sudo):
sudo adduser praktikan
sudo passwd praktikan
Uji login ke user baru.
3.Eksperimen 2 – Monitoring Proses Jalankan:

ps aux | head -10
top -n 1
Jelaskan kolom penting seperti PID, USER, %CPU, %MEM, COMMAND.
Simpan tangkapan layar top ke:
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
6.Amati hierarki proses dan identifikasi proses induk (init/systemd).
Catat hasilnya dalam laporan.
Commit & Push
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
