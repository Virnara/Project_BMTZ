## 4.3 Kebutuhan Antarmuka Pengguna (UI Mockup)

Berikut adalah rancangan antarmuka pengguna (*UI Mockup/Wireframe*) yang dipetakan berdasarkan Kebutuhan Fungsional (FR-001 sampai FR-015) untuk Sistem Donasi Berulang Baitulmal Tazkia. Antarmuka terbagi menjadi dua kelompok pengguna: Sisi Donatur (Antarmuka Publik/Portal) dan Sisi Admin/Staf BMT. Seluruh tampilan mengadopsi tema warna *Navy Blue* dan Putih sesuai NFR-006.

---

### 4.3.1 Antarmuka Sisi Donatur

1. **Halaman Kampanye & Opsi Donasi (FR-001 & FR-002)**
   * **Deskripsi:** Menampilkan informasi program/kampanye donasi, progres penghimpunan dana, serta pilihan jenis donasi (Sekali Donasi / Donasi Berulang).
   * **Kondisi Khusus/Galat:** Jika tautan tidak valid atau program tidak mendukung donasi berulang, sistem menampilkan pesan peringatan.
   * **Elemen Utama:** Foto/Judul Kampanye, Bar Progres Dana, Tombol Donasi Berulang.

2. **Formulir Pengaturan Donasi Berulang (FR-003)**
   * **Deskripsi:** Formulir bagi donatur untuk menetapkan komitmen donasi berkala.
   * **Elemen Utama:** 
     * Nominal Donasi (Chip pilihan Rp50.000, Rp100.000, Rp250.000, atau input manual)
     * Periode (Dropdown: Bulanan)
     * Tanggal Tagihan (Dropdown pilihan tanggal: 1, 15, 25)
     * Identitas Donatur (Nama, Nomor HP/WhatsApp, Email opsional)
     * Kotak Persetujuan Syarat & Ketentuan.

3. **Status Pendaftaran & Konfirmasi (FR-004)**
   * **Deskripsi:** Menampilkan konfirmasi keberhasilan penyimpanan jadwal donasi berulang lengkap dengan Kode Referensi (contoh: DB-001) dan ringkasan komitmen.

4. **Halaman Pembayaran Gateway & Hasil Transaksi (FR-006 & FR-007)**
   * **Deskripsi:** Antarmuka pengalihan ke payment gateway untuk memilih metode pembayaran (Transfer Bank, Virtual Account, E-Wallet) serta halaman status hasil transaksi (Terkonfirmasi/Berhasil, Pembayaran Sedang Diperiksa/Pending, atau Pembayaran Gagal).

5. **Portal Kelola Donasi Berulang (FR-011 & FR-012)**
   * **Deskripsi:** Fitur verifikasi (OTP/Nomor HP) bagi donatur untuk mengelola status komitmen donasi.
   * **Fungsi Utama:**
     * Menjeda sementara jadwal penagihan donasi (*Pause*)
     * Membatalkan komitmen donasi berulang (*Cancel*)
     * Notifikasi batas penagihan yang sedang diproses.

---

### 4.3.2 Antarmuka Sisi Admin (Back-Office Staf BMT)

1. **Halaman Utama / Dashboard Executif (FR-010 & A2)**
   * **Deskripsi:** Ringkasan metrik performa sistem untuk memantau Total Donatur Aktif, Dana Terhimpun Bulan Ini, Jumlah Donasi Dijeda, dan Transaksi Pending.

2. **Tabel Manajemen Donatur & Detail Donasi (FR-007, FR-008 & A3/A5)**
   * **Deskripsi:** Area daftar donatur berulang beserta status operasional, riwayat transaksi, dan status integrasi antarsistem (Penerimaan Donasi, Rekonsiliasi, Tanda Terima).

3. **Form Input Donasi Manual oleh Admin (A4)**
   * **Deskripsi:** Formulir khusus staf untuk mendaftarkan kesediaan autodebit donatur secara langsung melalui back-office.

4. **Generator Tautan Pembayaran Satu Kali (FR-014 & A7)**
   * **Deskripsi:** Fitur pembuatan tautan *one-time payment link* secara instant dengan kustomisasi nominal, peruntukan dana, serta masa berlaku tautan.

5. **Log Integrasi & Anti-Duplikasi (FR-009, FR-010, FR-015 & A6)**
   * **Deskripsi:** Tampilan audit sistem untuk memantau trafik API ke modul eksternal (Kelompok 1, Kelompok 5, Payment Gateway) beserta indikator penanganan duplikasi transaksi (*Duplikat Diabaikan*).