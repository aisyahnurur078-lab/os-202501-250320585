
# Laporan Praktikum Minggu [X]
Topik: Virtualisasi Menggunakan Virtual Machine

---

## Identitas
- **Nama**  : Aisyah Nurur Rohmah 
- **NIM**   : 250320585  
- **Kelas** : 1DSRA

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  
1.Menginstal perangkat lunak virtualisasi (VirtualBox/VMware).
2.Membuat dan menjalankan sistem operasi guest di dalam VM.
3.Mengatur konfigurasi resource VM (CPU, RAM, storage).
4.Menjelaskan mekanisme proteksi OS melalui virtualisasi.
5.Menyusun laporan praktikum instalasi dan konfigurasi VM secara sistematis.

---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
Poin-poin utama teori tersebut meliputi: 
1.Abstraksi Perangkat Keras (Hardware Abstraction): Teori ini melibatkan lapisan perangkat lunak, yang disebut hypervisor, yang bertindak sebagai perantara antara perangkat keras fisik dan mesin virtual. Hypervisor mengabstraksikan sumber daya fisik (CPU, memori, penyimpanan, jaringan) dan menyajikannya sebagai sumber daya virtual kepada setiap VM [1]. Ini memungkinkan beberapa "komputer" mandiri berjalan secara bersamaan di satu mesin fisik.
2.Isolasi (Isolation): Setiap mesin virtual beroperasi secara terpisah dari VM lainnya dan dari sistem operasi host (jika ada). Kegagalan atau masalah keamanan dalam satu VM tidak akan mempengaruhi kinerja atau stabilitas VM lainnya, memastikan lingkungan yang aman dan terisolasi untuk setiap aplikasi atau sistem operasi .
3.Enkapsulasi (Encapsulation): Seluruh lingkungan VM, termasuk sistem operasi, aplikasi, konfigurasi, dan data, dienkapsulasi ke dalam satu atau beberapa file (misalnya, file disk virtual). Ini mempermudah pengelolaan, pencadangan, pemindahan (migrasi), dan kloning VM antar host fisik yang berbeda, tanpa perlu menginstal ulang seluruh sistem .
4.Pembagian Sumber Daya (Resource Sharing): Meskipun setiap VM diisolasi, mereka berbagi kumpulan sumber daya perangkat keras fisik yang sama. Hypervisor mengelola dan mengalokasikan sumber daya ini secara dinamis sesuai kebutuhan masing-masing VM, memaksimalkan utilisasi perangkat keras dan efisiensi biaya dibandingkan dengan menjalankan setiap sistem operasi pada perangkat keras fisik terpisah .
5.Emulasi (Emulation) (Opsional, tergantung jenis hypervisor): Dalam beberapa kasus, terutama dengan hypervisor Tipe 2 (hosted), sebagian atau seluruh perangkat keras diemulasikan dalam perangkat lunak. Ini memungkinkan sistem operasi tamu berjalan bahkan jika instruksi CPU-nya tidak didukung secara native oleh host, meskipun dengan biaya kinerja yang lebih tinggi [1]. Namun, kebanyakan hypervisor modern menggunakan virtualisasi penuh (full virtualization) yang didukung oleh ekstensi perangkat keras (seperti Intel VT-x atau AMD-V) untuk kinerja yang mendekati native. 





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
1.Isolasi Lingkungan: Mesin virtual menyediakan lingkungan yang sepenuhnya terisolasi dan aman untuk menjalankan aplikasi atau sistem operasi yang berbeda pada satu perangkat keras fisik, mencegah konflik antar perangkat lunak .
2.Efisiensi Sumber Daya: Virtualisasi memaksimalkan penggunaan sumber daya perangkat keras fisik yang mendasarinya dengan mengonsolidasikan beban kerja, yang mengarah pada pengurangan biaya perangkat keras dan operasional secara signifikan .
3.Portabilitas dan Skalabilitas: VM mudah dipindahkan atau "dimigrasikan" antar host fisik yang berbeda tanpa gangguan, dan dapat dengan cepat diduplikasi atau ditingkatkan skalanya untuk memenuhi permintaan yang berubah-ubah .
4.Pengujian dan Pengembangan yang Aman: VM menawarkan cara yang aman dan terkendali bagi pengembang dan administrator TI untuk menguji perangkat lunak baru, menerapkan patch keamanan, atau menjalankan sistem operasi lama tanpa membahayakan lingkungan produksi utama . 

---

## Quiz
1. Apa perbedaan antara host OS dan guest OS?
   **Jawaban:**Perbedaan utamanya adalah OS Host adalah sistem operasi utama yang berjalan langsung pada perangkat keras fisik, mengelola sumber daya, sedangkan Guest OS (OS Tamu) adalah sistem operasi yang diinstal dan berjalan di dalam Mesin Virtual (VM) di atas Host OS, berfungsi sebagai lingkungan terisolasi yang "menyewa" sumber daya dari Host. Host menyediakan fondasi dan mengontrol perangkat keras, sementara Guest beroperasi secara independen di VM, memungkinkan Anda menjalankan beberapa sistem operasi berbeda (misalnya Windows, Linux, macOS) secara bersamaan pada satu komputer fisik. 
  
2.  Apa peran hypervisor dalam virtualisasi? 
   **Jawaban:**  Peran utamanya meliputi : 
1.Abstraksi Perangkat Keras: Hypervisor memisahkan sistem operasi dan aplikasi dari perangkat keras fisik yang mendasarinya. Setiap VM "melihat" perangkat keras virtualnya sendiri, meskipun semuanya berbagi sumber daya fisik yang sama [1].
2.Manajemen Sumber Daya: Ia mengendalikan alokasi sumber daya fisik seperti CPU, memori, penyimpanan, dan jaringan ke berbagai VM. Ini memastikan bahwa VM yang berbeda dapat berjalan secara bersamaan tanpa mengganggu satu sama lain [1].
3.Isolasi dan Keamanan: Setiap VM beroperasi dalam lingkungan yang terisolasi. Jika satu VM mengalami crash atau disusupi, VM lainnya pada host yang sama tetap aman dan berjalan normal [1].
4.Emulasi (Opsional): Dalam beberapa kasus, hypervisor dapat meniru (mengemulasi) perangkat keras yang berbeda dari yang sebenarnya tersedia, memungkinkan sistem operasi tamu berjalan di lingkungan yang tidak didukung secara asli oleh perangkat keras host [1].
5.Mengaktifkan Konsolidasi Server: Dengan memungkinkan banyak server virtual berjalan pada satu mesin fisik yang kuat, hypervisor membantu organisasi menghemat ruang fisik, energi, dan biaya pemeliharaan, yang mengarah pada efisiensi pusat data yang lebih baik [1]. 

3.Mengapa virtualisasi meningkatkan keamanan sistem?  
 **Jawaban:**Virtualisasi meningkatkan keamanan sistem dengan beberapa cara: 
1.Isolasi (Sandboxing): Mesin virtual (VM) beroperasi dalam lingkungan yang terisolasi dari host fisik dan VM lainnya. Jika satu VM disusupi oleh malware atau ancaman keamanan lainnya, ancaman tersebut tidak dapat dengan mudah menyebar ke sistem host atau VM lainnya, sehingga membatasi kerusakan.
2.Pengurangan Permukaan Serangan (Attack Surface Reduction): Dengan menggunakan VM, administrator dapat membuat sistem yang didedikasikan untuk satu fungsi atau aplikasi saja. Hal ini memungkinkan penonaktifan layanan atau fitur yang tidak diperlukan, sehingga mengurangi potensi titik masuk bagi penyerang [2, 3].
3.Pemulihan Bencana dan Snapshot: Platform virtualisasi sering kali menyertakan fitur snapshot dan kloning yang mudah digunakan. Hal ini memungkinkan administrator untuk dengan cepat mengembalikan VM yang disusupi ke status sebelumnya yang bersih (snapshot), atau membuat VM baru dari templat yang aman, mempercepat proses pemulihan setelah insiden keamanan [1, 3].
4.Pengujian yang Aman: Lingkungan virtual menawarkan tempat yang aman untuk menguji aplikasi baru, patch perangkat lunak, atau bahkan menganalisis malware tanpa membahayakan sistem produksi yang kritis [1, 3].
5.Penyebaran Patch dan Pembaruan yang Lebih Cepat: Organisasi dapat menggunakan lingkungan virtual untuk mengotomatiskan dan mempercepat proses penerapan patch keamanan dan pembaruan sistem di banyak mesin secara bersamaan [1]. 



---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
