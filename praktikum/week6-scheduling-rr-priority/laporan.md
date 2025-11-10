
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
1. Makna Hasil Percobaan
Hasil percobaan menunjukkan bahwa setiap perintah atau program yang dijalankan oleh pengguna selalu melibatkan interaksi antara aplikasi, kernel, dan perangkat keras.
Melalui pengamatan menggunakan perintah seperti strace atau dmesg, terlihat bahwa aplikasi melakukan serangkaian system call untuk meminta layanan dari kernel, seperti membaca file, menulis data, atau mengakses perangkat.
Hal ini membuktikan bahwa kernel berperan sebagai pengendali utama sistem, yang memastikan setiap proses berjalan dengan aman, tertib, dan tidak langsung mengakses perangkat keras tanpa izin.

2. Hubungan Hasil dengan Teori
Fungsi Kernel: Secara teori, kernel merupakan inti dari sistem operasi yang bertanggung jawab atas manajemen proses, memori, dan perangkat keras. Hasil percobaan memperlihatkan hal ini secara nyata, karena semua aktivitas aplikasi selalu melewati kernel.
System Call: Teori menyebutkan bahwa system call adalah jembatan komunikasi antara ruang pengguna (user space) dan ruang kernel (kernel space). Percobaan membuktikan konsep ini, karena tanpa system call, program tidak bisa berinteraksi dengan sistem file atau perangkat.
Arsitektur OS: Hasil percobaan juga memperkuat teori arsitektur sistem operasi. Dalam OS dengan arsitektur monolitik seperti Linux, banyak fungsi kernel dijalankan secara langsung di ruang kernel untuk efisiensi. Sedangkan pada sistem dengan arsitektur hybrid seperti Windows, beberapa fungsi dijalankan di ruang pengguna untuk meningkatkan keamanan dan stabilitas.

3. Perbedaan Hasil di Lingkungan OS yang Berbeda (Linux vs Windows)
Aspek	Linux	Windows
Arsitektur Kernel	Monolitik (semua layanan inti berada di kernel)	Hybrid (gabungan monolitik dan mikrokernel)
Transparansi Proses	Terbuka — dapat dilihat dengan alat seperti strace atau dmesg	Tertutup — perlu alat khusus seperti Process Monitor
Kemudahan Analisis	Mudah dianalisis karena bersifat open-source	Lebih sulit karena sistem tertutup
Kinerja & Keamanan	Lebih efisien dan fleksibel, cocok untuk pengembangan	Lebih stabil dan aman untuk penggunaan umum

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
