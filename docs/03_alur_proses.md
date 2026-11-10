## 3. Alur Proses

### 3.1 Alur Utama Konseptual
1. Donatur membuka tautan informasi kampanye.
2. Donatur melihat informasi program dan memilih opsi donasi berulang jika tersedia.
3. Donatur memasukkan nominal, jadwal/periode, dan peruntukan sesuai pilihan yang disediakan.
4. Sistem menyimpan kesediaan donasi dan referensi jadwal setelah data/consent yang diwajibkan terpenuhi.
5. Sistem menjalankan mekanisme yang kelak disetujui: pengingat untuk pembayaran manual dan/atau penagihan melalui gateway. Mekanisme ini belum boleh dianggap final.
6. Sistem menerima atau memperoleh status transaksi dari sumber yang disepakati.
7. Jika pembayaran terverifikasi berhasil, sistem meneruskan catatan donasi ke kelompok 1 dan menyediakan data yang dibutuhkan untuk tanda terima serta rekonsiliasi/pelaporan sesuai kontrak.
8. Sistem memperbarui status kesediaan donasi dan menyediakan status yang diperlukan kelompok 11 untuk komunikasi.

*Alur ini sengaja berhenti pada tingkat konseptual karena perbedaan antara alur pembayaran manual dan penagihan otomatis belum diselesaikan. Alur final baru ditetapkan setelah klarifikasi.*

### 3.2 Alur Alternatif dan Kondisi Tidak Normal

| ID | Kondisi | Respons sistem yang dibutuhkan dalam draft | Status keputusan |
| :--- | :--- | :--- | :--- |
| **ALT-01** | Pembayaran gagal | Catat hasil gagal dari sumber terverifikasi, pertahankan referensi transaksi, dan sediakan status untuk pemantauan/rekonsiliasi. Apakah dilakukan retry, kapan, dan berapa kali mengikuti kebijakan yang disetujui. | [DASAR TERSEDIA] bahwa kegagalan perlu ditangani; aturan retry [PERLU KLARIFIKASI]. Workbook menyebut retry terjadwal sebagai lingkup awal, tetapi detailnya harus diverifikasi. |
| **ALT-02** | Status pembayaran terlambat/pending/tidak diterima | Jangan menyatakan berhasil atau gagal tanpa dasar. Simpan status sementara jika didukung, lakukan pemeriksaan ulang sesuai kontrak, dan hindari pencatatan donasi ganda. | [PERLU KLARIFIKASI] untuk status gateway, waktu tunggu, dan mekanisme pemeriksaan ulang. |
| **ALT-03** | Donatur tidak membayar setelah pengingat | Catat bahwa pembayaran belum terkonfirmasi. Aturan pengingat lanjutan, masa tunggu, dan dampak pada status donasi perlu mengikuti keputusan bisnis. | [PERLU KLARIFIKASI]. |
| **ALT-04** | API kelompok 1 gagal menerima data donasi | Catat kegagalan integrasi dan referensi transaksi; jangan menghilangkan catatan sumber. Mekanisme pengiriman ulang harus mencegah duplikasi. | [PERLU KLARIFIKASI] untuk retry, idempotensi, dan tanggung jawab pemulihan. |
| **ALT-05** | Pengiriman data ke rekonsiliasi/pelaporan gagal | Catat kegagalan dan pertahankan data transaksi yang dibutuhkan untuk sinkronisasi ulang. | [PERLU KLARIFIKASI] untuk kanal, jadwal sinkronisasi, dan pemilik penanganan. |
| **ALT-06** | Pengiriman tanda terima gagal | Jangan mengubah status pembayaran hanya karena tanda terima gagal dikirim. Catat kegagalan terpisah dari status transaksi; aturan pengiriman ulang perlu ditetapkan. | [PERLU KLARIFIKASI]. |
| **ALT-07** | Permintaan jeda/pembatalan saat tagihan sedang diproses | Periksa status dan aturan efektif jeda/pembatalan sebelum mengubah jadwal; hindari menjanjikan bahwa transaksi yang sudah berjalan pasti dapat dihentikan. | Workbook menyebut fitur jeda/batal; aturan waktu efektif [PERLU KLARIFIKASI]. |
| **ALT-08** | Permintaan tagihan/hasil gateway terduplikasi | Gunakan referensi transaksi unik dan mekanisme pencegahan pencatatan ganda yang disepakati. | Kebutuhan mencegah duplikasi [PERLU KLARIFIKASI] pada detail teknis dan kontrak. |