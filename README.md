# Ahdam Ashari / 202412039
# Muhammad Aditya Januar / 202412049
# 🕒 Presensi Karyawan — Turn Around SBU JPP PKT

## 📘 Deskripsi Proyek
Aplikasi web sederhana untuk mencatat **presensi (check-in dan check-out)** karyawan pada kegiatan **Turn Around SBU Jasa Pelayanan Pabrik (JPP)** — Pupuk Kaltim.  
Website ini dibuat dengan **HTML, CSS, dan JavaScript**, menyimpan data di **LocalStorage**, dan dapat mengekspor data ke **CSV**.

---

## 🎯 Tujuan Proyek
- Mempermudah pencatatan kehadiran karyawan lintas perusahaan kontraktor.
- Menggantikan pencatatan manual berbasis kertas.
- Menyediakan data presensi secara cepat dan efisien.

---

## ⚙️ Fitur Utama
- ✅ Pilihan daftar perusahaan + input “Lainnya”
- ✅ Check-in & check-out otomatis atau manual
- ✅ Pencarian data karyawan
- ✅ Ekspor data ke CSV
- ✅ Penyimpanan data di LocalStorage
- ✅ Desain ringan & responsif (HTML + CSS murni)

---

## 🧩 Software Configuration Management (SCM)

### 🔹 Configuration Items (CI)
| Jenis CI | Deskripsi | Lokasi |
|-----------|------------|--------|
| Kode Sumber | Website utama | `index.html` |
| Dokumentasi | Panduan proyek | `README.md` |
| Gambar | Logo, latar belakang | `/images/`, `P4 (1).jpg` |
| Data Lokal | Simpan di browser | LocalStorage key: `presensi_jpp_pkt_v3` |

### 🔹 Penamaan & Labeling
- `index.html` → kode utama  
- `v3` → versi penyimpanan local  
- Folder `.github/` → otomatisasi CI/CD

---

## 🧭 Version Control (Git)

### 🔹 Platform
Menggunakan **GitHub** sebagai repository version control.

### 🔹 Branching Strategy
| Branch | Keterangan |
|---------|-------------|
| `main` | Versi rilis stabil |
| `development` | Tahap pengujian & integrasi |
| `feature/*` | Pengembangan fitur baru |
| `hotfix/*` | Perbaikan cepat bug |

### 🔹 Alur Workflow
```bash
# Clone repo
git clone https://github.com/<user>/presensi-jpp-pkt.git

# Buat branch fitur baru
git checkout -b feature/add-export-csv

# Tambah dan commit perubahan
git add .
git commit -m "Menambahkan fitur ekspor CSV"

# Merge ke development
git checkout development
git merge feature/add-export-csv

# Setelah uji, merge ke main
git checkout main
git merge development
