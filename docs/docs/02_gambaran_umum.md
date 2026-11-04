## 2. Gambaran Umum Sistem

### 2.1 Gambaran Produk
Subsistem mengelola informasi dan status kesediaan donasi berulang serta proses terkait pembayaran sesuai batas lingkup yang disepakati. Subsistem tidak boleh menganggap pembayaran berhasil hanya karena donatur memulai proses atau karena permintaan ke gateway dikirim; status harus berdasarkan hasil yang dapat diverifikasi.

### 2.2 Aktor dan Pihak Terkait

| Aktor/pihak | Tanggung jawab awal | Status |
| :--- | :--- | :--- |
| **Donatur** | Melihat informasi, memilih donasi berulang, memberikan data/consent yang diperlukan, membayar atau mengelola status donasi sesuai fitur yang disepakati. | [DASAR TERSEDIA]; detail consent dan metode pembayaran perlu klarifikasi. |
| **Staf internal Baitulmal Tazkia** | Memasukkan dan mengelola data internal, termasuk segmentasi donatur sesuai hasil rapat. | [DASAR TERSEDIA]. |
| **Subsistem Donasi Berulang (kelompok kita)** | Mengelola kesediaan/jadwal/status donasi berulang, menghubungkan proses pembayaran, dan menyediakan data sesuai kontrak. | [DASAR TERSEDIA]; batas data final perlu disepakati. |
| **Payment Gateway Artivisi** | Memproses pembayaran/penagihan dan memberikan status transaksi sesuai fitur yang didukung. | [DASAR TERSEDIA] dalam workbook; metode dan kontrak teknis perlu klarifikasi. |
| **Kelompok 1 — Penerimaan Donasi dan Akun Donatur** | Menerima catatan donasi melalui kontrak API kelompok tersebut. Workbook portofolio menyebut kelompok 4 menitipkan donasi melalui API kelompok 1. | [DASAR TERSEDIA]; payload dan endpoint belum final. |
| **Kelompok 5 — Rekonsiliasi dan Settlement** | Menggunakan hasil penagihan berulang sebagai sumber rekonsiliasi. | [DASAR TERSEDIA] pada workbook portofolio; format data dan status perlu disepakati. |
| **Kelompok 11 — Hubungan Donatur dan Komunikasi** | Menggunakan status kesediaan donasi berulang untuk proses komunikasi. | [DASAR TERSEDIA] pada workbook portofolio; data dan waktu sinkronisasi perlu disepakati. |
| **Modul tanda terima** | Menggunakan informasi transaksi terverifikasi untuk mendukung pengiriman tanda terima. Pemilik modul dan API perlu dipastikan. | [PERLU KLARIFIKASI] untuk batas pemilik dan kontrak. |
| **Modul pelaporan** | Menggunakan data transaksi sesuai kebutuhan pelaporan. Batas dengan Rekonsiliasi dan Settlement perlu dipastikan. | [PERLU KLARIFIKASI] untuk pemilik, data, dan kontrak. |

### 2.3 Batas Tanggung Jawab dan Pertukaran Data

| Hubungan | Data yang mungkin dikirim/diterima | Batas tanggung jawab/status |
| :--- | :--- | :--- |
| **Subsistem kita ↔ Payment Gateway Artivisi** | Permintaan pembayaran/penagihan, identitas referensi transaksi, nominal, jadwal/token jika metode dan persetujuan mendukung; respons berisi ID transaksi dan status. | Gateway bertanggung jawab memproses pembayaran. Nama field, token, autentikasi, status, callback/webhook, timeout, dan retry policy [PERLU KLARIFIKASI]. Jangan menyimpan data pembayaran sensitif tanpa dasar dan aturan yang disetujui. |
| **Subsistem kita → Kelompok 1: Penerimaan Donasi dan Akun Donatur** | Catatan donasi hasil pembayaran yang terverifikasi: referensi donasi/transaksi, nominal, waktu, identitas donatur sesuai kontrak, peruntukan, dan status. | Workbook menyebut donasi dititipkan melalui API kelompok 1. Field wajib, ID unik, idempotensi, respons sukses/gagal, dan cara koreksi [PERLU KLARIFIKASI]. Gunakan data contoh terlebih dahulu. |
| **Subsistem kita → Kelompok 5: Rekonsiliasi dan Settlement** | Data tagihan/hasil pembayaran, referensi gateway, nominal, waktu, status sukses/gagal/pending, dan referensi untuk pencocokan. | Kelompok 5 menggunakan hasil penagihan sebagai sumber rekonsiliasi. Skema, frekuensi, dan status final [PERLU KLARIFIKASI]. Rekonsiliasi rekening bukan tanggung jawab subsistem kita. |
| **Subsistem kita → Kelompok 11: Hubungan Donatur dan Komunikasi** | Status kesediaan donasi berulang, jadwal/periode, status aktif/jeda/batal jika fitur tersebut disetujui, dan data minimum yang dibutuhkan untuk komunikasi. | Workbook menyebut kelompok 11 mengambil status kesediaan donasi. Kanal, payload, izin akses, dan frekuensi sinkronisasi [PERLU KLARIFIKASI]. Konten dan penjadwalan komunikasi berkala berada pada kelompok terkait menurut workbook. |
| **Subsistem kita → Modul tanda terima** | Data transaksi yang telah terverifikasi berhasil, referensi donasi, nominal, waktu, dan informasi tanda terima yang disetujui. | Pemilik modul, field tanda terima, pemicu pengiriman, dan API [PERLU KLARIFIKASI]. Jangan membuat tanda terima sukses jika status transaksi belum terverifikasi. |
| **Subsistem kita → Modul pelaporan** | Catatan transaksi dan status terverifikasi yang diperlukan untuk laporan. | Tujuan laporan, pemilik, dan apakah data disalurkan melalui kelompok 5 atau modul terpisah [PERLU KLARIFIKASI]. |

*Catatan: tabel ini merupakan batas awal untuk koordinasi. Ini bukan kontrak API final. Detail endpoint, skema payload, validasi, autentikasi, kode error, retry, dan kepemilikan data harus disepakati lintas kelompok.*

### 2.4 Batasan dan Asumsi Awal
* Staf internal mengelola data internal; tim pengembang membangun sistem, bukan menjalankan pengelolaan data harian. [DASAR TERSEDIA dari ringkasan rapat].
* Pemrosesan pembayaran dilakukan oleh Payment Gateway Artivisi sesuai metode yang didukung. [DASAR TERSEDIA dari workbook].
* Akses data antarsubsistem dilakukan melalui API/kontrak integrasi, bukan akses langsung ke basis data kelompok lain. [DASAR TERSEDIA dari workbook portofolio].
* Transfer, VA, dan e-wallet hanya dapat dinyatakan didukung setelah kemampuan integrasi dikonfirmasi. [PERLU KLARIFIKASI].
* Pengingat otomatis dan autodebit adalah mekanisme berbeda. Apakah keduanya masuk versi ini masih [PERLU KLARIFIKASI].
* Identitas visual awal mengikuti arahan rapat: navy blue dan putih. Detail desain tetap perlu disesuaikan dengan identitas resmi organisasi.

---
