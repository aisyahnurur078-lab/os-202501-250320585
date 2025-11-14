
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
>Menghitung waiting time dan turnaround time pada algoritma RR dan Priority.
>Menyusun tabel hasil perhitungan dengan benar dan sistematis.
>Membandingkan performa algoritma RR dan Priority.
>Menjelaskan pengaruh time quantum dan prioritas terhadap keadilan eksekusi proses.
>Menarik kesimpulan mengenai efisiensi dan keadilan kedua algoritma.
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
1. Kernel berperan sebagai inti sistem operasi yang mengatur komunikasi antara aplikasi dan perangkat keras melalui mekanisme system call, sehingga proses berjalan aman dan terkontrol.

2. System call menjadi jembatan penting antara ruang pengguna dan ruang kernel, membuktikan bahwa setiap aktivitas program selalu melibatkan layanan dari kernel.

3. Perbedaan arsitektur sistem operasi (Linux dan Windows) memengaruhi cara system call dijalankan — Linux lebih terbuka dan efisien, sedangkan Windows lebih tertutup dan berfokus pada stabilitas serta keamanan.




## Quiz
1. Perbedaan Utama antara Round Robin dan Priority Scheduling
Aspek	Round Robin (RR)	Priority Scheduling
Dasar Penjadwalan	Setiap proses mendapatkan waktu eksekusi bergilir (time quantum) secara bergantian.	Setiap proses dijalankan berdasarkan tingkat prioritas yang telah ditentukan.
Keadilan (Fairness)	Sangat adil karena semua proses mendapat jatah waktu sama.	Kurang adil karena proses prioritas tinggi bisa terus mendominasi CPU.
Cocok untuk	Sistem time-sharing dan multitasking interaktif.	Sistem yang membutuhkan penanganan cepat untuk tugas penting.
Kemungkinan Starvation	Hampir tidak ada, karena setiap proses pasti mendapat giliran.	Dapat terjadi jika proses prioritas rendah terus tertunda.

2. Pengaruh Besar/Kecilnya Time Quantum terhadap Performa Sistem
Time quantum terlalu kecil → proses sering berganti (context switching meningkat), menyebabkan overhead besar dan sistem menjadi kurang efisien.
Time quantum terlalu besar → proses besar bisa mendominasi CPU terlalu lama, membuat proses lain menunggu terlalu lama dan sistem terasa kurang responsif.

3. Mengapa Algoritma Priority Dapat Menyebabkan Starvation
Starvation (kelaparan proses) terjadi ketika proses prioritas rendah tidak pernah mendapat giliran CPU karena selalu ada proses dengan prioritas lebih tinggi yang datang lebih dulu.
Contohnya: jika banyak proses prioritas tinggi terus masuk, proses prioritas rendah akan terus tertunda dan tidak pernah dieksekusi.
Untuk mengatasi hal ini, digunakan teknik aging, yaitu menaikkan prioritas proses yang menunggu terlalu lama, agar tetap mendapat kesempatan menjalankan CPU.

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
