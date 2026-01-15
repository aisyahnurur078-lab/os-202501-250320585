
# Laporan Praktikum Minggu [VII]
Topik: [Sinkronisasi Proses dan Masalah Deadlock"]

---

## Identitas
- **Nama**  : [Aisyah Nurur Rohmah(250320585), Aulia Zahra(250320580), Safyra Azzahro(250320586)  
- **Kelas** : [1DSRA]

---

## Tujuan
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.
>Mengidentifikasi empat kondisi penyebab deadlock (mutual exclusion, hold and wait, no preemption, circular wait).
>Menjelaskan mekanisme sinkronisasi menggunakan semaphore atau monitor.
>Menganalisis dan memberikan solusi untuk kasus deadlock.
>Berkolaborasi dalam tim untuk menyusun laporan analisis.
>Menyajikan hasil studi kasus secara sistematis.


## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
1.Kondisi Berlomba (Race Condition): Situasi di mana beberapa proses mengakses dan memanipulasi data bersamaan pada waktu yang sama. Hasil akhir dari eksekusi ini bergantung pada urutan eksekusi proses, yang dapat menyebabkan hasil yang tidak konsisten atau salah. Sinkronisasi diperlukan untuk mencegah kondisi ini dengan memastikan hanya satu proses yang dapat mengakses sumber daya kritis pada satu waktu tertentu.
2.Bagian Kritis (Critical Section): Segmen kode dalam suatu proses di mana sumber daya bersama (seperti variabel bersama, file, atau perangkat keras) diakses. Prinsip utamanya adalah jaminan adanya pengecualian bersama (mutual exclusion), yang berarti ketika satu proses menjalankan bagian kritisnya, proses lain tidak diizinkan masuk ke bagian kritis yang sama.
3.Pengecualian Bersama (Mutual Exclusion): Mekanisme mendasar untuk menyelesaikan kondisi berlomba. Ini memastikan bahwa tidak lebih dari satu proses dapat mengeksekusi bagian kritisnya pada saat tertentu. Ini adalah salah satu syarat utama yang harus dipenuhi untuk mencegah deadlock.
4.Deadlock: Kondisi kebuntuan di mana dua atau lebih proses saling menunggu sumber daya yang sedang dipegang oleh proses lain, sehingga tidak ada proses yang dapat melanjutkan eksekusi. Empat kondisi Coffman yang diperlukan dan bersamaan untuk terjadinya deadlock adalah:
>Pengecualian Bersama (Mutual Exclusion): Sumber daya harus bersifat tidak dapat dibagi (non-sharable).
>Genggam dan Tunggu (Hold and Wait): Proses memegang satu sumber daya sambil menunggu sumber daya lain.
>Tanpa Prelasi (No Preemption): Sumber daya yang dialokasikan tidak dapat diambil secara paksa; sumber daya harus dilepaskan secara sukarela oleh proses yang memegangnya.
>Tunggu Melingkar (Circular Wait): Terdapat rantai melingkar dari proses-proses yang saling menunggu sumber daya.
5.Solusi Sinkronisasi (misalnya, Semaphore dan Monitor): Metode perangkat lunak atau perangkat keras yang digunakan untuk mengimplementasikan pengecualian bersama dan mengelola akses ke sumber daya bersama. Semaphore (counting atau binary) dan monitor adalah contoh primitif sinkronisasi yang umum digunakan dalam percobaan untuk mengontrol interaksi antar proses dan mencegah kondisi berlomba. 


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
- Jelaskan makna hasil percobaan.  
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  

-Makna hasil percobaan sinkronisasi proses dan deadlock berkaitan erat dengan bagaimana kernel sistem operasi mengimplementasikan fungsi-fungsi manajemen sumber daya, yang diekspos melalui system call. Perbedaan mendasar dalam arsitektur kernel (monolitik vs. hibrida) menyebabkan hasil yang berbeda antara Linux dan Windows. 
-Makna Hasil Percobaan dan Hubungannya dengan Teori
Hasil percobaan sinkronisasi proses (misalnya, penggunaan mutex, semaphore, atau critical section) akan menunjukkan hal-hal berikut: 
Pencegahan Race Condition: Hasil yang benar secara konsisten (misalnya, nilai akhir variabel bersama selalu benar) menunjukkan bahwa mekanisme sinkronisasi berhasil mencegah race condition. Kegagalan (nilai tidak konsisten) berarti ada kelemahan dalam kode sinkronisasi atau mekanisme OS yang digunakan.
Overhead Kinerja: Waktu eksekusi yang diukur dapat menunjukkan overhead yang terkait dengan penggunaan mekanisme sinkronisasi. Setiap kali proses melakukan system call (seperti wait() atau signal()) untuk mengakses sumber daya yang dilindungi, terjadi peralihan konteks (context switch) ke mode kernel, yang memakan waktu. Semakin sering atau kompleks sinkronisasi, semakin besar overhead-nya.
Kemunculan Deadlock: Jika percobaan dirancang untuk mensimulasikan kondisi deadlock (misalnya, empat kondisi Coffman: mutual exclusion, hold and wait, no preemption, dan circular wait), hasilnya akan menunjukkan apakah sistem operasi (atau kode program) dapat mendeteksi, menghindari, atau pulih dari kondisi tersebut. 
-perbedaannya
hasil percobaan Anda mungkin menunjukkan bahwa Linux memiliki kinerja sedikit lebih konsisten untuk tugas sinkronisasi tertentu karena arsitektur monolitiknya yang ramping, sementara Windows mungkin menunjukkan perilaku yang berbeda dalam penanganan deadlock karena pendekatannya yang lebih terotomatisasi dalam beberapa kasus. 

---

## Kesimpulan
1.Sinkronisasi Proses adalah Kebutuhan Mendesak: Dalam sistem multiprogramming, sinkronisasi proses sangat penting untuk memastikan konsistensi data dan mencegah race condition (kondisi pacu) [1, 2, 4]. Ini memungkinkan banyak proses untuk mengakses sumber daya bersama secara terkoordinasi dan aman.
2.Deadlock adalah Masalah Serius dari Akses Bersamaan: Deadlock terjadi ketika dua proses atau lebih saling menunggu sumber daya yang dipegang oleh proses lain, menyebabkan semua proses terhenti [1, 2, 5]. Ini adalah konsekuensi potensial dari sinkronisasi yang tidak tepat dan dapat melumpuhkan seluruh sistem jika tidak dikelola.
3.Diperlukan Strategi untuk Menangani Deadlock: Mengatasi deadlock membutuhkan pendekatan yang disengaja [1, 2, 5]. Strategi umum meliputi:
>Pencegahan (Prevention): Memastikan setidaknya satu dari empat kondisi deadlock tidak terjadi [1, 2, 5].
>Penghindaran (Avoidance): Menggunakan algoritma, seperti Algoritma Banker, untuk alokasi sumber daya yang aman secara dinamis [1, 2, 5].
>Deteksi dan Pemulihan (Detection and Recovery): Membiarkan deadlock terjadi, mendeteksinya, lalu memulihkan sistem (misalnya, dengan menghentikan satu atau lebih proses) [1, 2, 5]. 

---

## Quiz

1. Sebutkan empat kondisi utama penyebab deadlock
> Mutual Exclusion – Sumber daya tidak dapat digunakan bersama pada waktu bersamaan.
> Hold and Wait – Proses memegang satu sumber daya sambil menunggu sumber daya lain.
> No Preemption – Sumber daya tidak bisa diambil paksa dari proses yang sedang menggunakannya.
> Circular Wait – Terjadi rantai proses yang saling menunggu sumber daya satu sama lain secara melingkar.

2. Mengapa sinkronisasi diperlukan dalam sistem operasi?
>Sinkronisasi diperlukan untuk:
>Menghindari konflik saat beberapa proses mengakses data bersama (race condition).
>Menjamin konsistensi data dan urutan eksekusi yang benar.
>Mencegah terjadinya deadlock dan starvation.

3. Jelaskan perbedaan antara semaphore dan monitor
Aspek	Semaphore	Monitor
Tipe Mekanisme	Primitive (variabel counter)	Struktur tingkat tinggi (objek sinkronisasi)
Penggunaan	Menggunakan operasi wait() dan signal()	Menggunakan prosedur dan variabel kondisi
Kompleksitas	Lebih manual, rawan kesalahan	Lebih mudah dan aman digunakan
Dukungan Bahasa	Tersedia di hampir semua OS	Biasanya didukung di bahasa tingkat tinggi (Java, C#, dsb.)


## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
