
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
