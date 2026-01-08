
# Laporan Praktikum Minggu [XIII]
Topik: Docker – Resource Limit (CPU & Memori)

---

## Identitas
- **Nama**  : Aisyah Nurur Rohmah  
- **NIM**   : 250320585 
- **Kelas** : 1DSRA

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  
1.Menulis Dockerfile sederhana untuk sebuah aplikasi/skrip.
2.Membangun image dan menjalankan container.
3.Menjalankan container dengan pembatasan CPU dan memori.
4.Mengamati dan menjelaskan perbedaan eksekusi container dengan dan tanpa limit resource.
5.Menyusun laporan praktikum secara runtut dan sistematis.

---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
1.Isolasi melalui Namespace Linux: Docker memanfaatkan fitur namespaces kernel Linux untuk menyediakan lingkungan yang terisolasi untuk setiap kontainer. Setiap kontainer memiliki namespace tersendiri untuk ID proses (PID), jaringan, sistem file, dan lain-lain, yang membuatnya tampak seolah-olah berjalan pada mesin yang terpisah. Isolasi ini merupakan prasyarat agar pembatasan sumber daya pada satu kontainer tidak memengaruhi host atau kontainer lainnya [1, 2].
2.Manajemen dan Pembatasan Sumber Daya melalui cgroups (Control Groups): Mekanisme utama untuk menerapkan batas CPU dan memori adalah melalui cgroups. Cgroups memungkinkan administrator sistem untuk mengalokasikan, memprioritaskan, melarang, dan mengontrol penggunaan sumber daya sistem (CPU, memori, disk I/O, dll.) oleh sekelompok proses [1, 2]. Docker menggunakan subsistem memori dan CPU dari cgroups untuk menetapkan batas yang ditentukan pengguna.
3.Mekanisme Batas Memori (Memory Limit): Dalam percobaan, batas memori Docker bekerja dengan menetapkan "batas keras" (hard limit) pada total RAM yang dapat digunakan oleh kontainer. Ketika kontainer mencapai batas ini, kernel Linux akan menghentikan paksa proses yang menggunakan memori berlebih untuk mencegah kehabisan memori pada sistem host secara keseluruhan (melalui Out-Of-Memory Killer atau OOM Killer) [2].
4.Mekanisme Batas CPU (CPU Limit): Pembatasan CPU tidak menghentikan proses, tetapi mengatur alokasi waktu pemrosesan. Ini dapat dilakukan dengan dua cara utama:
1.Berbagi CPU (CPU Shares): Menentukan prioritas relatif. Jika ada permintaan CPU yang tinggi, kontainer dengan shares lebih banyak akan mendapatkan jatah CPU yang lebih besar secara proporsional [2].
2.Batas Periode dan Kuota (CFS Quota): Menentukan batas absolut penggunaan CPU. Misalnya, kontainer dapat dibatasi hanya menggunakan 50% dari satu inti CPU penuh dalam periode waktu tertentu, terlepas dari beban sistem host [2]. 

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

---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.
1.Isolasi dan Stabilitas Host: Pembatasan sumber daya Docker sangat penting untuk mencegah satu kontainer memonopoli CPU atau memori sistem host, yang dapat menyebabkan ketidakstabilan atau mengganggu kontainer lain dan aplikasi host itu sendiri .
2.Sintaks Konfigurasi: Batas ini ditetapkan menggunakan flag khusus pada perintah docker run. Contohnya, memori diatur dengan --memory (atau -m) dan --memory-swap, sedangkan CPU diatur dengan --cpus, --cpu-shares, atau --cpuset-cpus .
3.Manajemen Efisiensi: Fitur ini memungkinkan administrator untuk mengelola dan mendistribusikan sumber daya fisik secara efisien di antara berbagai layanan atau aplikasi, memastikan setiap kontainer menerima jatah sumber daya yang diperlukan untuk beroperasi secara efektif .
4.Kontrol Granular: Docker menyediakan kontrol yang terperinci. Pengguna dapat menentukan batas keras (hard limits), seperti jumlah memori maksimum absolut, atau batas lunak (soft limits), seperti pembagian CPU relatif, yang memungkinkan penyesuaian fleksibel terhadap beban kerja yang berbeda .
5.Peningkatan Performa yang Terukur: Dengan menentukan batas sumber daya, pengguna dapat memastikan performa aplikasi yang lebih konsisten dan terukur, mencegah masalah performa yang disebabkan oleh "perampokan" sumber daya atau kehabisan memori (Out-Of-Memory/OOM) .


---

## Quiz
1. Mengapa container perlu dibatasi CPU dan memori?  
   **Jawaban:**Kontainer perlu dibatasi CPU dan memorinya untuk menjamin stabilitas dan kinerja sistem secara keseluruhan, mencegah satu kontainer rakus sumber daya (resource hogging) yang bisa membuat kontainer lain atau host mogok (OOMKilled), menghemat biaya (terutama di cloud), dan memastikan alokasi sumber daya yang adil antar aplikasi, sehingga semua berjalan optimal dan efisien. Batasan ini menciptakan lingkungan yang seimbang dan dapat diprediksi. 
  
2.  Apa perbedaan VM dan container dalam konteks isolasi resource? 
   **Jawaban:** Perbedaan utama terletak pada tingkat isolasi dan penggunaan sumber daya: VM (Virtual Machine) mengisolasi sepenuhnya dengan menjalankan sistem operasi (OS) sendiri di atas hypervisor, memberikan isolasi kuat tapi boros sumber daya; sementara Container berbagi kernel OS host dan hanya mengemas aplikasi beserta dependensinya, menawarkan isolasi lebih ringan dan efisien sumber daya, namun kurang aman dibandingkan VM karena berbagi kernel yang sama. 
 
3.  Apa dampak limit memori terhadap aplikasi yang boros memori?
   **Jawaban:**Pembatasan limit memori dapat berdampak signifikan terhadap aplikasi yang boros memori. Aplikasi semacam itu akan cenderung mengalami beberapa masalah utama, yaitu:
1. Peningkatan penggunaan swap space: Ketika aplikasi kehabisan memori fisik yang tersedia, sistem operasi akan mulai memindahkan data dari RAM ke ruang swap di hard disk atau SSD . Proses ini jauh lebih lambat daripada mengakses RAM, yang menyebabkan penurunan kinerja yang drastis, sering kali membuat aplikasi terasa lamban atau tidak responsif .
2. Waktu respons yang lambat: Karena keterlambatan yang disebabkan oleh swapping, aplikasi akan membutuhkan waktu lebih lama untuk memproses permintaan, memuat data, atau melakukan tugas lainnya .
3.Risiko crash (out-of-memory error): Jika aplikasi terus meminta memori melebihi batas yang diizinkan dan swap space juga habis, sistem operasi, atau runtime environment-nya (misalnya, JVM), pada akhirnya akan menghentikan aplikasi secara paksa, yang dikenal sebagai out-of-memory (OOM) error . Hal ini sering kali merupakan dampak paling parah, yang menyebabkan hilangnya data atau ketidaktersediaan layanan.
4.Peningkatan beban sistem: Penggunaan swap yang berlebihan tidak hanya memperlambat aplikasi yang boros memori, tetapi juga dapat memengaruhi kinerja aplikasi lain yang berjalan pada sistem yang sama karena perebutan sumber daya I/O disk . 


---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
