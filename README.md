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

## 🪲 Bug Ditemukan dan Solusi Perbaikan

Selama pengembangan proyek **Presensi Karyawan — Turn Around SBU JPP PKT**, ditemukan beberapa bug dan potensi error logika pada kode JavaScript utama (`index.html`). Berikut hasil audit dan perbaikannya:

---

### 1️⃣ Bug: Nilai `datetime-local` tidak valid (detik disertakan)
**Kode Asli:**
```js
function nowLocalInputValue() {
  const d = new Date();
  const p = n => String(n).padStart(2,'0');
  return `${d.getFullYear()}-${p(d.getMonth()+1)}-${p(d.getDate())}T${p(d.getHours())}:${p(d.getMinutes())}:${p(d.getSeconds())}`;
}
### solusi
function nowLocalInputValue() {
  const d = new Date();
  const p = n => String(n).padStart(2,'0');
  return `${d.getFullYear()}-${p(d.getMonth()+1)}-${p(d.getDate())}T${p(d.getHours())}:${p(d.getMinutes())}`;
}

### Bug tombol
document.querySelectorAll('input[name="inMode"]').forEach(el => {
  el.addEventListener('change', () => {
    checkInTime.disabled = (el.value === 'auto');
  });
});
document.querySelectorAll('input[name="outMode"]').forEach(el => {
  el.addEventListener('change', () => {
    checkOutTime.disabled = (el.value === 'auto');
  });
});


### solusi
if (mode === 'manual' && !checkInTime.value) {
  return alert('Waktu manual harus diisi sebelum menyimpan!');
}


### Bug tombol hapus semua
btnClear.addEventListener('click', () => {
  if (!confirm('Hapus semua data presensi?')) return;
  localStorage.removeItem(STORAGE_KEY);
  renderTable(); // ← tambahan agar tabel ikut disegarkan
});


### solusi
company.addEventListener('change', () => {
  if (company.value === 'lainnya') {
    companyOtherWrap.style.display = 'block';
  } else {
    companyOtherWrap.style.display = 'none';
    companyOther.value = ''; // reset nilai jika bukan 'lainnya'
  }
});


### solusi bug duplikasi data
const isDuplicate = data.some(r => r.nik === id && r.type === rec.type && r.waktu === rec.waktu);
if (isDuplicate) return alert('Data duplikat: entri ini sudah tersimpan.');


### Bug tampilan warna
label { color: #e9edf4; }

### Bug localstorage penuh
try {
  localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
} catch(e) {
  alert('Gagal menyimpan data: kapasitas penyimpanan browser penuh.');
}




