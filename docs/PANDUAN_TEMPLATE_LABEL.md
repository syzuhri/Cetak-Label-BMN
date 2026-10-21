# Panduan Desain Template Label Kustom (.lbx) Brother P-touch

Aplikasi **Cetak Label BMN** mendukung penggunaan template desain kustom berformat `.lbx` yang dibuat menggunakan software **Brother P-touch Editor**.

---

## 1. Aturan Penamaan Objek (Object Name)

Agar data dari aplikasi dapat terhubung otomatis ke template label saat dicetak, setiap objek teks, barcode, atau logo pada Brother P-touch Editor **wajib diberi nama (Object Name)** sesuai daftar di bawah ini (menggunakan huruf kecil).

### Cara Mengatur Object Name di Brother P-touch Editor:
1. Buka file `.lbx` Anda di **Brother P-touch Editor**.
2. Klik kanan pada objek (teks, barcode, atau gambar), lalu pilih **Properties**.
3. Pilih tab **Expanded** (atau **Name** pada versi tertentu).
4. Masukkan nama pada kolom **Object Name** persis sesuai tabel di bawah.
5. Klik **OK** dan Simpan (`Ctrl + S`).

---

## 2. Daftar Field & Status Kebutuhan

| Object Name | Tipe Objek di P-touch | Status | Keterangan Data | Contoh Tampilan |
| :--- | :--- | :--- | :--- | :--- |
| **`nup`** | Text | **Wajib** | Nomor Urut Pendaftaran aset BMN | `000001` |
| **`bcd`** | Barcode / QR Code | **Sangat Disarankan** | Gabungan barcode `[satker].[barang].[nup]` | `021.01.999999.3050105001.000001` |
| **`nama_barang`** | Text | **Opsional** | Nama/uraian jenis barang BMN | `LAPTOP DELL LATITUDE 5420` |
| **`kode_barang`** | Text | **Opsional** | Kode Klasifikasi Barang BMN | `3.05.01.05.001` |
| **`kode_satker`** | Text | **Opsional** | Kode Satuan Kerja | `021.01.999999` |
| **`nama_satker`** | Text | **Opsional** | Nama Satuan Kerja / Unit Kerja | `Kementerian Investasi / BKPM` |
| **`tahun`** | Text | **Opsional** | Tahun Perolehan BMN | `2024` |
| **`merek`** | Text | **Opsional** | Merk / Tipe Aset | `Dell Latitude 5420` |
| **`dbrl`** | Text | **Opsional** | Ruangan / Penanggung Jawab BMN | `Ruang Rapat Utama Lt. 3` |
| **`objLogo`** | Picture / Image | **Opsional** | Gambar logo instansi yang diatur di aplikasi | Logo Garuda / Logo Instansi |

> [!NOTE]
> - Objek yang berstatus **Opsional** boleh dihilangkan dari template jika ukuran label kecil (misalnya pita 18 mm atau 12 mm).
> - Aplikasi tidak akan error jika sebuah objek opsional tidak ditemukan di template; aplikasi hanya mengisi objek yang tersedia pada desain template Anda.
> - Objek `bcd` dapat berupa **Barcode 1D (Code 128 / Code 39)** maupun **Barcode 2D (QR Code)**.

---

## 3. Langkah Menggunakan Template Kustom di Aplikasi

1. Buka aplikasi **Cetak Label BMN**.
2. Pada dropdown **Ukuran Template**, pilih menu paling bawah: **"📁 Pilih Template Kustom (.lbx)..."**.
3. Cari dan pilih file template `.lbx` yang telah Anda buat.
4. Template Anda akan otomatis muncul di daftar pilihan dengan awalan `Custom: [NamaFile].lbx`.
5. Tentukan range data yang ingin dicetak, lalu klik **Cetak Label**.

---

*Hak Cipta © 2026 Kementerian Investasi Hilirisasi / BKPM - Syaifudin Zuhri*
