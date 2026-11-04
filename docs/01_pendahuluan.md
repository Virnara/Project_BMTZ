## 1. Pendahuluan

### 1.1 Tujuan Dokumen
Dokumen Software Requirements Specification (SRS) ini mendefinisikan kebutuhan awal subsistem Donasi Berulang dan Kanal Pembayaran Digital. Dokumen menjadi bahan koordinasi bagi PIC/klien, BA, pengembang, penguji, serta kelompok lain yang bertukar data dengan subsistem ini.

### 1.2 Ruang Lingkup Awal
Berdasarkan workbook proyek, ruang lingkup awal subsistem mencakup pendaftaran kesediaan donasi berulang beserta nominal, jadwal/periode, dan peruntukan; penagihan berkala melalui Payment Gateway Artivisi sesuai kemampuan metode yang disetujui; pencatatan hasil penagihan; pemberitahuan terkait penagihan; jeda atau pembatalan donasi berulang; serta pembuatan tautan pembayaran satu kali yang dapat dibagikan dan dipantau.

Ringkasan rapat yang tersedia juga menyebut pengingat otomatis, pembayaran oleh donatur, pertukaran data donasi, dan penggunaan data transaksi untuk tanda terima serta pelaporan. Karena mekanisme pembayaran berulang pada kedua sumber belum sepenuhnya selaras, alur penagihan otomatis/autodebit dan alur pengingat untuk pembayaran manual ditandai **[PERLU KLARIFIKASI]**.

### 1.3 Tujuan Sistem
Tujuan awalnya adalah membantu donatur mendaftarkan donasi berulang, mengelola jadwal dan statusnya, mendukung pemrosesan atau pemantauan pembayaran sesuai mekanisme yang disetujui, serta menyediakan catatan transaksi yang dapat digunakan oleh subsistem terkait.

### 1.4 Istilah dan Singkatan

| Istilah | Arti |
| :--- | :--- |
| **SRS** | Software Requirements Specification; dokumen kebutuhan perangkat lunak. |
| **BA** | Business Analyst; peran yang menggali, menganalisis, dan mendokumentasikan kebutuhan. |
| **CRM** | Customer Relationship Management; pengelolaan hubungan dan data donatur. |
| **Payment Gateway** | Layanan pihak ketiga yang memproses pembayaran dan mengembalikan status transaksi. |
| **API** | Application Programming Interface; kontrak pertukaran data antar sistem. |
| **FR** | Functional Requirement; kebutuhan fungsional. |
| **NFR** | Non-Functional Requirement; kebutuhan kualitas atau batasan. |
| **Retry** | Percobaan ulang atas penagihan yang gagal; aturan rinci harus dikonfirmasi. |

### 1.5 Referensi yang Digunakan
1. Workbook Proyek “Donasi Berulang dan Kanal Pembayaran Digital” (Kelompok 4).
2. Workbook portofolio/kanal yang menjelaskan ketergantungan lintas kelompok semester 5.
3. Ringkasan Rapat Pengembangan Sistem Donasi dan CRM, 23 Oktober 2026.
4. Dokumentasi Payment Gateway Artivisi dan kontrak API antarkelompok: belum tersedia/final dalam bahan yang ditinjau.

---
