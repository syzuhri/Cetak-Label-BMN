# Catatan Rilis (Release Notes) - v1.2.6

**Tanggal Rilis:** 30 Oktober 2026  
**Pengembang:** Syaifudin Zuhri  
**Instansi:** Kedeputian Teknologi Informasi Penanaman Modal Kementerian Investasi Hilirisasi/BKPM  
**File Installer:** `LabelSetup.exe` (v1.2.6)

---

## Ringkasan Pembaruan (Release Highlights) - v1.2.6

Versi 1.2.6 menghadirkan penguatan keamanan kredensial database tingkat tinggi dan fitur pembaca catatan rilis langsung di dalam aplikasi:

1. **🔐 Enkripsi Kredensial Database App.config (AES-256 & PBKDF2)**:
   - Seluruh string koneksi database yang tersimpan di file `App.config` dan `LabelPortable.dll.config` kini dienkripsi secara penuh menggunakan standar **AES-256-CBC** dengan derivasi kunci **PBKDF2 SHA-256 (100.000 iterasi)** dan dynamic Initialization Vector (IV).
   - *Power user* maupun pengguna tingkat lanjut tidak dapat membaca password, username, maupun host database secara mentah (*plaintext*) melalui text editor di luar aplikasi.
   - Proses enkripsi dan dekripsi berjalan secara transparan dan otomatis di balik layar, tetap mendukung kompatibilitas mundur jika admin memasukkan string baru.
2. **📜 Tombol Catatan Rilis (Changelog) di Halaman Tentang**:
   - Ditambahkan tombol **"Catatan Rilis"** di samping tombol *Periksa Pembaruan* pada halaman **Tentang**.
   - Pengguna kini dapat membaca seluruh riwayat versi dan detail pembaruan kapan saja melalui jendela pembaca (*Changelog Window*) berdesain Fluent Mica.
3. **⚡ Tombol Cepat Restart Now pada Banner Notifikasi Pembaruan & Pengaturan**:
   - Banner notifikasi otomatis pembaruan di latar belakang kini secara visual menyertakan tombol **Restart Now** langsung di bar notifikasi hijau.
   - Peringatan banner restart di halaman Pengaturan kini secara konsisten menampilkan tombol aksi **Restart Now** saat pergantian jenis database.

---

# Catatan Rilis (Release Notes) - v1.2.5

**Tanggal Rilis:** 30 Oktober 2026  
**Pengembang:** Syaifudin Zuhri  
**Instansi:** Kedeputian Teknologi Informasi Penanaman Modal Kementerian Investasi Hilirisasi/BKPM  
**File Installer:** `LabelSetup.exe` (v1.2.5)

---

## Ringkasan Pembaruan (Release Highlights) - v1.2.5

Versi 1.2.5 menyempurnakan migrasi otomatis pengaturan koneksi cloud pada mesin pengguna serta perbaikan installer:

1. **☁️ Auto-Migrasi Pengaturan Cloud di Halaman Pengaturan**:
   - Memperbarui pengaturan legacy (seperti `localhost` pada MySQL atau IP lokal lama `10.2.237.99` pada PostgreSQL) secara otomatis menjadi koneksi cloud resmi (TiDB Cloud MySQL, Neon Cloud PostgreSQL, Azure SQL, dan MongoDB Atlas).
   - Tombol **Reset ke Default** kini mereset seluruh koneksi database ke konfigurasi cloud resmi bawaan.
2. **📦 Pembaruan Konfigurasi Installer**:
   - Memastikan file `LabelPortable.dll.config` selalu diperbarui saat update aplikasi sehingga koneksi cloud langsung aktif, dengan tetap memproteksi database lokal (`db\label.db`, `db\label.litedb`) agar tidak tertimpa.

---

# Catatan Rilis (Release Notes) - v1.2.4

**Tanggal Rilis:** 30 Oktober 2026  
**Pengembang:** Syaifudin Zuhri  
**Instansi:** Kedeputian Teknologi Informasi Penanaman Modal Kementerian Investasi Hilirisasi/BKPM  
**File Installer:** `LabelSetup.exe` (v1.2.4)

---

## Ringkasan Pembaruan (Release Highlights) - v1.2.4

Versi 1.2.4 menghadirkan konfigurasi cloud bawaan siap pakai untuk seluruh mesin database yang didukung, integrasi otomatis SSL/TLS, serta tombol aksi cepat restart aplikasi:

1. **☁️ Integrasi Penuh 4 Layanan Database Cloud Bawaan**:
   - **Microsoft Azure SQL Database**: Terintegrasi langsung dengan enkripsi TLS dan bypass sertifikat (`labelbmn.database.windows.net`, DB: `free-sql-db-6520239`).
   - **MongoDB Atlas Cloud (NoSQL)**: Terintegrasi dengan connection string SRV Atlas (`cluster0.9klqlcl.mongodb.net`, DB: `bmn_label`).
   - **PostgreSQL Cloud (Neon Serverless)**: Terintegrasi dengan koneksi SSL pooler Singapore (`ep-cold-shadow-ao8womre-pooler.c-2.ap-southeast-1.aws.neon.tech`, DB: `neondb`).
   - **MySQL Cloud (TiDB Serverless)**: Terintegrasi dengan koneksi TLS aman (`gateway01.ap-southeast-1.prod.aws.tidbcloud.com:4000`, DB: `bmn_label`).
2. **🔄 Tombol "Restart Now" Terpadu**:
   - Banner notifikasi pembaruan di bilah atas kini memiliki tombol instan `[ Restart Now ]`.
   - Simpan pengaturan database kini menampilkan dialog peringatan dengan tombol `[ Restart Now ]` dan `[ Nanti Saja ]`, serta tombol cepat di footer pengaturan.
3. **🔒 Negosiasi SSL/TLS Otomatis**:
   - Penambahan parameter `SslMode=Preferred` pada MySQL dan `SSL Mode=Prefer;Trust Server Certificate=true` pada PostgreSQL untuk konektivitas mulus antara lokal dan cloud tanpa kendala sertifikat.

---

# Catatan Rilis (Release Notes) - v1.2.3

**Tanggal Rilis:** 30 Oktober 2026  
**Pengembang:** Syaifudin Zuhri  
**Instansi:** Kedeputian Teknologi Informasi Penanaman Modal Kementerian Investasi Hilirisasi/BKPM  
**File Installer:** `LabelSetup.exe` (v1.2.3)

---

## Ringkasan Pembaruan (Release Highlights) - v1.2.3

Versi 1.2.3 menghadirkan penyempurnaan stabilitas, optimasi batch restore berkecepatan tinggi, perbaikan integrasi Azure Cloud & SQL Database, serta penyelarasan antarmuka:

1. **⚡ Optimasi Batch Restore & Sync Cloud (Super Cepat)**:
   - Restorasi puluhan ribu data tiket label kini menggunakan pengelompokan batch (100 baris per transaksi), memangkas waktu restore dari ~15 menit menjadi hanya ~5-10 detik.
2. **🛡️ Perbaikan Skema Azure SQL & String Truncation**:
   - Menangani panjang kolom `deleted_row` menjadi `NVARCHAR(50)` dengan auto-migrasi otomatis saat inisialisasi tabel, mencegah error truncation saat memulihkan label terhapus.
3. **🔐 Upfront Single-Consent Azure AD / Microsoft Login**:
   - Izin akun Microsoft (`User.Read` dan `Files.ReadWrite.AppFolder`) kini diminta sekaligus di awal login, menghilangkan pop-up persetujuan berulang saat membuka menu Backup & Sync.
4. **🎨 Tata Letak Rata Tengah Modern**:
   - Penyelarasan kartu konten pada halaman **Pengaturan Sistem** dan **Sinkronisasi & Backup** menjadi rata tengah (*center-aligned*) sehingga seimbang dan nyaman di layar lebar.
5. **🔒 Proteksi Database Lokal Saat Update**:
   - Installer `LabelSetup.exe` memproteksi file database lokal (`label.db`, `label.litedb`) dan setting aplikasi agar tidak tertimpa saat instalasi update.

---

# Catatan Rilis (Release Notes) - v1.2.0

**Tanggal Rilis:** 29 Oktober 2026  
**Pengembang:** Syaifudin Zuhri  
**Instansi:** Kedeputian Teknologi Informasi Penanaman Modal Kementerian Investasi Hilirisasi/BKPM  
**File Installer:** `LabelSetup.exe` (v1.2.0)

---

## Ringkasan Pembaruan (Release Highlights)

Versi 1.2.0 menghadirkan modernisasi antarmuka pengguna berbasis **Windows 11 Fluent Design (WPF-UI)** dan peningkatan runtime ke **.NET 9.0 Windows (C# 13)**, menghasilkan pengalaman pengguna yang jauh lebih intuitif, estetis, dan sangat responsif. Seluruh fungsionalitas inti pencetakan label Brother b-PAC, multi-database, serta autentikasi Azure AD tetap terjaga dengan peningkatan kenyamanan operasional.

---

### Fitur Baru & Peningkatan Utama v1.2.0

#### 1. Desain Antarmuka Windows 11 Fluent (WPF-UI)
* **Tema Adaptif Dark & Light Mode**:
  * Dilengkapi tombol toggle tema (Matahari / Bulan) di TitleBar untuk beralih mode terang dan gelap secara instan.
  * Seluruh teks, kartu, dialog, dan elemen data otomatis beradaptasi dengan kontras yang optimal.
* **Navigasi Sidebar Modern**:
  * Menu samping Fluent (Cetak Label, Data Barang, Satuan Kerja, Pengaturan, Tentang).
  * Menu **Sign Out** terintegrasi di bagian bawah sidebar dengan konfirmasi keluar dan pembersihan sesi aman.

#### 2. Manajemen Data & Grid Responsif
* **Single-Click Checkbox**:
  * Centang/batalkan pilihan data cukup dengan 1 kali klik instan tanpa jeda edit-mode.
  * Pelebaran kolom ceklis dan penomoran urut baris (`No`) untuk kenyamanan identifikasi data.
  * Pembagian lebar kolom yang proporsional antara `Nama Barang` dan `Merek / Tipe`.
* **Toolbar Aksi 3 Tingkat Terstruktur**:
  * **Tingkat 1**: Pencarian live, pemilihan template label, pemilihan printer Brother, dan tombol Cetak Label Utama.
  * **Tingkat 2**: Tambah Data, Edit Data dinamis (muncul saat 1 item dipilih atau klik dua kali pada baris), Hapus Data dinamis (single/multi-select), Pulihkan Data, serta Impor & Ekspor Excel.
  * **Tingkat 3**: Tombol *Pilih Semua*, *Batal Pilih* (dinamis aktif/nonaktif), dan Ceklis *Tampilkan Data Terhapus* berdampingan secara rapi beserta indikator jumlah item terpilih.
* **Visualisasi Data Terhapus yang Elegan**:
  * Data terhapus ditampilkan dengan efek strikethrough dan warna redup yang nyaman di mata tanpa mengaburkan teks.

#### 3. Dialog Cetak Range Modern & Dropdown Template Ramah Pengguna
* **Dialog Print Range Fluent**:
  * Jika tombol cetak diklik saat tidak ada item yang dicentang, aplikasi menampilkan dialog modern yang meminta pengguna memasukkan nomor urut baris yang ingin dicetak (contoh: `1-10` atau `5`).
* **Pilihan Template Label Ramah Pengguna**:
  * Dropdown template menampilkan ukuran label yang jelas: **`Label Size 18`**, **`Label Size 24`**, dan **`Label Size 36`** (memetakan otomatis ke file `.lbx` b-PAC).

---

# Catatan Rilis (Release Notes) - v1.1.0

**Tanggal Rilis:** 21 Oktober 2026  
**Pengembang:** Syaifudin Zuhri  
**Instansi:** Kementerian Investasi dan Hilirisasi / BKPM  
**File Installer:** `LabelSetup.exe` (v1.1.0)

---

## Ringkasan Pembaruan (Release Highlights)

Versi 1.1.0 menghadirkan perombakan arsitektur besar-besaran (*Modern Clean Architecture*), dukungan multi-database tingkat enterprise, sistem autentikasi modern Microsoft Azure Active Directory, antarmuka Dark Mode mutakhir dengan performa instan tanpa lag, fitur template kustom Brother P-touch (`.lbx`), serta integrasi dokumen panduan terperinci.

---

### Fitur Baru & Peningkatan Utama

#### 1. Dukungan Template Label Kustom (`.lbx`) & Panduan Desain
* **Pemilihan Template Kustom Dinamis**:
  * Pengguna kini dapat memilih file template `.lbx` buatan sendiri secara langsung melalui dropdown ukuran label: *"📁 Pilih Template Kustom (.lbx)..."*.
  * Mendukung pencarian file `.lbx` dari folder mana saja tanpa harus menaruh file di direktori aplikasi.
* **Dialog & Dokumen Panduan Template**:
  * Tersedia menu bantuan baru: *"📋 Panduan Desain Template Label (.lbx)..."* yang dapat dibuka langsung dari tombol Bantuan `?`.
  * Tabel aturan Object Name Brother P-touch Editor:
    * **Wajib**: `nup` (Nomor Urut Pendaftaran aset).
    * **Sangat Disarankan**: `bcd` (Barcode 1D / QR Code gabungan `satker.barang.nup`).
    * **Opsional**: `nama_barang`, `kode_barang`, `kode_satker`, `nama_satker`, `tahun`, `merek`, `dbrl`, dan `objLogo`.
  * Tersedia dokumen lengkap di `docs/PANDUAN_TEMPLATE_LABEL.md`.

#### 2. Performa Grid Instan & Perbaikan Pengurutan (Zero-Lag Sorting)
* **Pengurutan Kolom Hapus (Single-Arrow Sorting)**:
  * Klik header kolom "Hapus" untuk mengelompokkan data terhapus dan data aktif secara instan (*Ascending* ▲: Aktif di atas -> *Descending* ▼: Terhapus di atas -> *Reset*).
  * Menggunakan satu panah indikator sistem yang bersih.
* **Penghapusan Timer Invalidate Grid**:
  * Menghilangkan rendering loop pada DataGridView sehingga proses klik checkbox *"Tampilkan Data Terhapus"*, sorting kolom, dan navigasi data berjalan responsif pada 60 FPS tanpa freeze/jeda.
* **Caching Data Master**:
  * Data referensi Satker dan Barang di-cache di memori sehingga tidak membebani query database berulang kali saat filter diubah.

#### 3. Dukungan Multi-Database Lengkap (Enterprise Ready)
* **Kini mendukung 4 tipe database**:
  * **SQLite** (Database lokal tersemat)
  * **Microsoft SQL Server** (Mendukung server IP `10.1.31.166`, port kustom, instance name `\SQLEXPRESS`, dan trust certificate)
  * **MySQL / MariaDB**
  * **PostgreSQL**
* Pengaturan database interaktif di menu **Pengaturan (Settings)** dengan fitur:
  * Pembuatan skema database otomatis jika belum ada di server.
  * Uji koneksi (*Test Connection*) instan dengan pesan diagnostik detail.
  * Dialog konfirmasi restart aplikasi langsung setelah menyimpan konfigurasi baru.

#### 4. Autentikasi Pengguna Microsoft Azure Active Directory (MSAL / Entra ID)
* Layar login modern sebelum jendela utama terbuka.
* Mendukung login akun Microsoft organisasi / Single Sign-On (SSO).
* Sesi login tersimpan aman secara otomatis (*silent login*) menggunakan cache token lokal.
* Menu profil pengguna dan opsi keluar (*Logout / Ganti Akun*) di pojok kanan atas jendela utama.
* Pengaturan Tenant ID dan Client ID Azure AD yang dapat disesuaikan di menu Settings.

#### 5. Tampilan Modern & Tema Gelap Persisten
* **Tema Dark & Light Mode yang Persisten**:
  * Menggunakan palet warna Zinc modern yang nyaman di mata.
  * Terintegrasi dengan Windows 10/11 DWM Immersive Dark Mode.
  * Pilihan tema otomatis tersimpan permanen dan tidak ter-reset saat aplikasi di-restart.
* **Tabel DataGridView Modern**:
  * Tombol aksi (*Edit* ✏️ dan *Hapus/Restore* 🗑️/↩️) didesain ulang menjadi *Flat Pill Buttons* elegan.
  * Border horizontal minimalis, menghilangkan garis kisi vertikal kaku.

#### 6. Sistem Pembaruan Otomatis (Auto-Updater)
* Terhubung langsung dengan repositori GitHub rilis resmi: `https://github.com/syzuhri/Cetak-Label-BMN`.
* Pengecekan versi baru di latar belakang secara hening (*seamless background check*).
* Dialog unduh pembaruan terintegrasi dengan progress bar dan tombol langsung pasang (*One-Click Update & Restart*).

---

### Panduan Instalasi & Pembaruan
1. Unduh `LabelSetup.exe` versi 1.1.0 dari repositori rilis GitHub.
2. Jalankan `LabelSetup.exe` dan ikuti panduan di layar.
3. Installer sudah menyertakan driver **Brother b-PAC Client Component 3.4 (32-bit)** dan konfigurasi database siap pakai.
