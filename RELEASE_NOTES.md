# Catatan Rilis (Release Notes) - v1.1.0

**Tanggal Rilis:** 21 Oktober 2026  
**Pengembang:** Syaifudin Zuhri  
**Instansi:** Kementerian Investasi dan Hilirisasi / BKPM  
**File Installer:** `LabelSetup.exe` (v1.1.0)

---

## Ringkasan Pembaruan (Release Highlights)

Versi 1.1.0 menghadirkan perombakan arsitektur besar-besaran (*Modern Clean Architecture*), dukungan multi-database tingkat enterprise, sistem autentikasi modern Microsoft Azure Active Directory, antarmuka Dark Mode mutakhir dengan performa instan tanpa lag, serta penyematan background logo animasi.

---

### Fitur Baru & Peningkatan Utama

#### 1. Dukungan Multi-Database Lengkap (Enterprise Ready)
* **Kini mendukung 4 tipe database**:
  * **SQLite** (Database lokal tersemat)
  * **Microsoft SQL Server** (Mendukung port kustom, instance name `\SQLEXPRESS`, dan trust certificate)
  * **MySQL / MariaDB**
  * **PostgreSQL**
* Pengaturan database interaktif di menu **Pengaturan (Settings)** dengan fitur:
  * Pembuatan database otomatis jika belum ada di server.
  * Uji koneksi (*Test Connection*) instan dengan pesan diagnostik detail.
  * Dialog konfirmasi restart aplikasi langsung setelah menyimpan konfigurasi baru.
  * Default bawaan SQL Server: `10.1.31.166:1433`.

#### 2. Autentikasi Pengguna Microsoft Azure Active Directory (MSAL / Entra ID)
* Layar login modern sebelum jendela utama terbuka.
* Mendukung login akun Microsoft organisasi / Single Sign-On (SSO).
* Sesi login tersimpan aman secara otomatis (*silent login*) menggunakan cache token lokal.
* Menu profil pengguna dan opsi keluar (*Logout / Ganti Akun*) di pojok kanan atas jendela utama.
* Pengaturan Tenant ID dan Client ID Azure AD yang dapat disesuaikan di menu Settings.

#### 3. Tampilan Modern, Dark Mode, & Background Animasi
* **Tema Dark & Light Mode yang Persisten**:
  * Menggunakan palet warna Zinc modern yang nyaman di mata.
  * Terintegrasi dengan Windows 10/11 DWM Immersive Dark Mode.
  * Pilihan tema otomatis tersimpan permanen dan tidak ter-reset saat aplikasi di-restart.
* **Tabel DataGridView Modern**:
  * Tombol aksi (*Edit* ✏️ dan *Hapus/Restore* 🗑️/↩️) didesain ulang menjadi *Flat Pill Buttons* elegan.
  * Border horizontal minimalis, menghilangkan garis kisi vertikal kaku.
  * Dropdown ukuran label (`ComboBoxTemplate`) sepenuhnya mendukung tema gelap.
* **Background Logo Animasi (Floating & Breathing Effect)**:
  * Logo resmi beranimasi halus (melayang & berdenyut) di latar belakang layar login dan area kosong tabel.
  * Menggunakan *alpha transparency* cerdas sehingga teks data tetap 100% terbaca jelas.
  * Hemat resource (menggunakan double-buffered GDI+ dan otomatis pause saat jendela diminimalkan).

#### 4. Pengurutan Data Terhapus & Optimasi Kecepatan (Tanpa Lag)
* **Single-Arrow Sorting pada Kolom Hapus**:
  * Klik header kolom "Hapus" untuk mengelompokkan data terhapus dan data aktif (Ascending ▲ / Descending ▼ / Reset).
  * Menampilkan satu panah indikator sistem yang bersih.
* **Pemuatan Data Cepat (Zero-Lag Checkbox)**:
  * Menghilangkan jeda/freeze saat mencentang *"Tampilkan Data Terhapus"*.
  * Master data Satker dan Barang di-cache di memori sehingga tidak membebani jaringan database setiap kali filter diubah.

#### 5. Sistem Pembaruan Otomatis (Auto-Updater)
* Terhubung langsung dengan repositori GitHub rilis resmi: `https://github.com/syzuhri/Cetak-Label-BMN`.
* Pengecekan versi baru di latar belakang secara hening (*seamless background check*).
* Dialog unduh pembaruan terintegrasi dengan progress bar dan tombol langsung pasang (*One-Click Update & Restart*).

---

### Panduan Instalasi & Pembaruan
1. Unduh `LabelSetup.exe` versi 1.1.0 dari repositori rilis GitHub.
2. Jalankan `LabelSetup.exe` dan ikuti panduan di layar.
3. Installer sudah menyertakan driver **Brother b-PAC Client Component 3.4 (32-bit)** dan konfigurasi database siap pakai.
