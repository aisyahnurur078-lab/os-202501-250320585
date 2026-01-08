
# Laporan Praktikum Minggu [X]
Topik: Simulasi dan Deteksi Deadlock

---

## Identitas
- **Nama**  : Aisyah Nurur Rohmah  
- **NIM**   : 250320585 
- **Kelas** : 1DSRA

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  
1.Membuat program sederhana untuk mendeteksi deadlock.
2.Menjalankan simulasi deteksi deadlock dengan dataset uji.
3.Menyajikan hasil analisis deadlock dalam bentuk tabel.
4.Memberikan interpretasi hasil uji secara logis dan sistematis.
5.Menyusun laporan praktikum sesuai format yang ditentukan.2..

---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
1.Definisi Deadlock: Deadlock adalah suatu kondisi di mana dua atau lebih proses atau thread terblokir secara permanen karena masing-masing menunggu sumber daya yang sedang dipegang oleh proses lain dalam kelompok tersebut, sehingga tidak ada yang dapat melanjutkan eksekusi.
2.Empat Kondisi Coffman: Teori utama yang mendasari terjadinya deadlock adalah empat kondisi Coffman, yang harus terpenuhi secara simultan:
 1.Pengecualian Bersama (Mutual Exclusion): Sumber daya hanya dapat digunakan oleh satu proses pada satu waktu.
 2.Menahan dan Menunggu (Hold and Wait): Sebuah proses menahan satu sumber daya sambil menunggu (meminta) sumber daya lain yang sedang dipegang oleh proses lain.
 3.Tanpa Pengambilalihan (No Preemption): Sumber daya yang sudah dialokasikan tidak dapat diambil secara paksa dari proses yang memegangnya, tetapi harus dilepaskan secara sukarela oleh proses tersebut setelah selesai digunakan.
 4.Tanpa Pengambilalihan (No Preemption): Sumber daya yang sudah dialokasikan tidak dapat diambil secara paksa dari proses yang memegangnya, tetapi harus dilepaskan secara sukarela oleh proses tersebut setelah selesai digunakan.
3.Model Sistem Sumber Daya (Resource Allocation Graph): Simulasi dan deteksi deadlock sering kali menggunakan representasi grafis, yaitu grafik alokasi sumber daya. Teori ini memodelkan hubungan antara proses (simpul) dan sumber daya (simpul) untuk memvisualisasikan alokasi dan permintaan sumber daya. Keberadaan siklus (perputaran) dalam grafik ini merupakan indikasi adanya deadlock, terutama jika setiap jenis sumber daya hanya memiliki satu instans.
4.Algoritma Deteksi Deadlock: Percobaan simulasi mengimplementasikan algoritma untuk memeriksa status sistem secara berkala guna mengidentifikasi deadlock. Algoritma ini bekerja dengan memeriksa grafik alokasi sumber daya atau menggunakan metode lain (seperti variasi algoritma Banker) untuk menemukan adanya kondisi tunggu melingkar.
5.Strategi Penanganan Deadlock: Teori ini mencakup pendekatan yang berbeda dalam menangani deadlock setelah terdeteksi, yaitu pemulihan (recovery). Metode pemulihan melibatkan penghentian satu atau lebih proses (process termination) atau pengambilalihan sumber daya (resource preemption) untuk memutus siklus deadlock. 



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
1.Definisi Deadlock: Deadlock adalah suatu kondisi di mana dua atau lebih proses dalam sistem komputer saling menunggu sumber daya yang sedang dipegang oleh proses lain, sehingga tidak ada proses yang dapat melanjutkan eksekusinya (kebuntuan).
2.Penyebab Utama: Terjadinya deadlock dipicu oleh terpenuhinya empat kondisi Coffman secara bersamaan: mutual exclusion (sumber daya hanya dapat digunakan oleh satu proses pada satu waktu), hold and wait (proses memegang sumber daya sambil menunggu sumber daya lain), no preemption (sumber daya tidak dapat diambil paksa), dan circular wait (kondisi tunggu melingkar antar proses).
3.Tujuan Simulasi: Simulasi deadlock bertujuan untuk mereplikasi skenario kondisi kebuntuan dalam lingkungan terkontrol (seperti pada kasus "Dining Philosophers Problem") untuk memahami cara kerja, mengidentifikasi penyebab, dan mengevaluasi solusi penanganan deadlock.
4.Metode Deteksi: Deteksi deadlock dilakukan dengan memeriksa status alokasi sumber daya sistem secara berkala, sering kali menggunakan alat visual seperti grafik alokasi sumber daya (resource allocation graph) atau wait-for graph.
5.Hasil Deteksi: Jika dalam pemeriksaan ditemukan adanya siklus (cycle) atau perputaran dalam grafik alokasi sumber daya, maka sistem berada dalam kondisi tidak aman dan berpotensi mengalami deadlock. Penanganan selanjutnya memerlukan intervensi seperti terminasi proses atau resource preemption untuk memulihkan sistem. 


---

## Quiz
1. Apa perbedaan antara deadlock prevention, avoidance, dan detection?  
   **Jawaban:** Pencegahan (Prevention) berarti mencegah salah satu dari 4 syarat deadlock terjadi (sumber daya tidak bisa dibagi, tahan dan tunggu, tanpa perebutan, tunggu melingkar) dengan membatasi permintaan, sering mengorbankan efisiensi; Penghindaran (Avoidance) (seperti Algoritma Banker) memastikan sistem selalu dalam "kondisi aman" dengan menganalisis kebutuhan di masa depan dan menolak alokasi yang bisa menyebabkan deadlock, lebih fleksibel tapi butuh info lebih banyak; sedangkan Deteksi (Detection) membiarkan deadlock terjadi, lalu mendeteksinya (misal pakai Wait-For Graph) dan melakukan pemulihan (menghentikan proses/merebut sumber daya) setelah deadlock teridentifikasi, fokus pada pemulihan daripada pencegahan. 

2. Mengapa deteksi deadlock tetap diperlukan dalam sistem operasi?  
   **Jawaban:**Deteksi deadlock tetap penting karena dapat membekukan sistem, membuang sumber daya, menurunkan kinerja, dan menyebabkan frustrasi pengguna, sehingga sistem operasi perlu mengidentifikasi situasi ini secara berkala menggunakan teknik seperti graf alokasi sumber daya, agar dapat melakukan pemulihan (menghentikan proses, mengambil alih sumber daya), menjaga keandalan dan efisiensi sistem operasi. 
  
3. Apa kelebihan dan kekurangan pendekatan deteksi deadlock?  
   **Jawaban:**Kelebihan Pendekatan Deteksi Deadlock:
1.Pemanfaatan Sumber Daya yang Lebih Tinggi: Pendekatan ini memungkinkan sistem untuk beroperasi pada tingkat utilisasi sumber daya yang lebih tinggi dibandingkan dengan metode pencegahan (deadlock prevention) yang bersifat konservatif. Pencegahan sering kali memblokir permintaan yang mungkin tidak akan menyebabkan deadlock, sementara deteksi hanya mengintervensi ketika deadlock benar-benar terdeteksi [1].
2.Fleksibilitas: Pendekatan ini tidak membatasi cara permintaan sumber daya dibuat, memberikan fleksibilitas yang lebih besar dalam desain dan eksekusi program [1].
3.Efisiensi dalam Situasi Jarang Terjadi: Jika deadlock jarang terjadi, overhead untuk deteksi dan pemulihan mungkin lebih rendah daripada overhead berkelanjutan dari algoritma pencegahan atau penghindaran (deadlock avoidance) yang lebih kompleks [1].
Kekurangan Pendekatan Deteksi Deadlock:
1.Overhead Kinerja: Secara berkala, algoritma deteksi deadlock harus dijalankan untuk memeriksa keberadaan siklus pada graf alokasi sumber daya. Proses ini membutuhkan sumber daya CPU dan waktu tambahan, yang dapat memperlambat kinerja sistem secara keseluruhan [1].
Kompleksitas Pemulihan: Setelah deadlock terdeteksi, sistem harus memulihkan diri. Pemulihan sering kali melibatkan penghentian (termination) satu atau lebih proses atau preemption sumber daya, yang bisa menjadi rumit dan menyebabkan hilangnya pekerjaan yang telah dilakukan oleh proses yang dipilih untuk dihentikan (victim process) [1].
2.Waktu Deteksi Tidak Pasti: Terdapat penundaan antara terjadinya deadlock yang sebenarnya dan deteksi oleh algoritma, yang berarti sumber daya mungkin tetap tidak dapat digunakan selama periode penundaan ini [1].
3.Masalah Starvation: Jika kebijakan pemilihan proses korban (victim selection) dalam pemulihan tidak adil, proses yang sama dapat berulang kali dipilih sebagai korban, yang menyebabkan starvation (kelaparan) sumber daya secara permanen [1]. 
   

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
