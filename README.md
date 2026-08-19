# Information Systems Technology Audit Report
### Organization: Werdy's Kitchen
- **Audited System:** Werdy's Kitchen Web Application (Food Ordering & Transaction Management)
- **Audit Period:** May 6, 2026 - June 5, 2026
- **Auditor:** Muhammad Daffa Al Fansyah
- **Standards & Frameworks:** ISO/IEC 27001 (Security & Backup), ISO/IEC 25010 (Software Quality & Usability), COBIT

---

## Ringkasan Eksekutif (Executive Summary)
Audit Sistem Informasi pada **Werdy's Kitchen** dilakukan untuk mengevaluasi efektivitas, keandalan, dan tata kelola sistem berbasis web yang digunakan untuk operasional pemesanan makanan, pelacakan pesanan via email, formulir checkout, hingga manajemen dashboard admin.

Secara umum, sistem telah memiliki kontrol dasar yang memadai untuk proses autentikasi admin, manajemen menu, pencatatan transaksi, dan riwayat pesanan. Namun, ditemukan beberapa area kelemahan berisiko *High* dan *Moderate* yang memerlukan tindakan mitigasi dan perbaikan agar operasional berjalan optimal, stabil, dan aman.

---

## Berkas Laporan Audit (Deliverables)

| Dokumen | Deskripsi | Format |
| :--- | :--- | :---: |
| **[INFORMATION SYSTEMS TECHNOLOGY AUDIT REPORT.pdf](./INFORMATION%20SYSTEMS%20TECHNOLOGY%20AUDIT%20REPORT.pdf)** | Laporan utama audit teknologi sistem informasi yang memuat metodologi, profil sistem, evaluasi kontrol, temuan audit (*findings*), dan rekomendasi strategis. | PDF |
| **[EVIDENCE COLLECTION.pdf](./EVIDENCE%20COLLECTION.pdf)** | Kumpulan bukti audit (*audit evidence*) mencakup hasil *Inquiry, Observation, Inspection, Re-performance, CAATs,* dan *Sampling*. | PDF |

---

## Matriks Temuan Audit (Audit Findings Matrix)

| No | Temuan Audit (*Audit Finding*) | Kategori / Standar Acuan | Tingkat Risiko (*Risk Level*) |
| :---: | :--- | :--- | :---: |
| **01** | **Backup Data Belum Dilakukan Secara Berkala** | ISO/IEC 27001 Annex A.12 (Backup) | **High** |
| **02** | **Fitur *Generate Report* Belum Berfungsi** | ISO/IEC 25010 (Functional Suitability) | **High** |
| **03** | **Stabilitas Website Menurun / Terjadi *Crash* Saat Transaksi Berulang** | ISO/IEC 25010 (Performance Efficiency) | **High** |
| **04** | **Dashboard Summary Tidak Menampilkan Data Riil (*Real-Time*)** | ISO/IEC 25010 (Functional Suitability) | **Moderate** |
| **05** | **Tampilan Antarmuka (UI/UX) Belum Optimal (Logo navbar, banner terpotong, info About Us kurang)** | ISO/IEC 25010 (Usability & UI Aesthetics) | **Moderate** |
| **06** | **Integrasi Link *Contact Us* / Media Sosial Menghasilkan Error 404** | ISO/IEC 25010 (Functional Suitability) | **Moderate** |

---

## Rincian Temuan & Rekomendasi Perbaikan

### 1. [HIGH] Backup Data Belum Berkala
- **Kondisi:** Prosedur backup database belum terjadwal secara periodik sehingga berisiko tinggi saat terjadi kegagalan sistem.
- **Dampak:** Potensi kehilangan data transaksi pelanggan dan proses pemulihan (*disaster recovery*) yang lambat.
- **Rekomendasi:** Terapkan mekanisme backup database otomatis secara berkala (harian/mingguan), simpan cadangan pada media terpisah/cloud storage, serta lakukan simulasi *data recovery* berkala.

### 2. [HIGH] Fitur Generate Report Tidak Berfungsi
- **Kondisi:** Tombol/fitur pembuatan laporan pada admin dashboard belum dapat mengekspor rekapitulasi data transaksi.
- **Dampak:** Admin dan pemilik bisnis kesulitan memperoleh laporan penjualan otomatis untuk evaluasi finansial/operasional.
- **Rekomendasi:** Perbaiki integrasi query modul pelaporan dengan database agar dapat mengekspor data transaksi (PDF/Excel) secara valid.

### 3. [HIGH] Kestabilan Website saat Transaksi Berulang
- **Kondisi:** Pengujian *re-performance* menemukan sistem mengalami gangguan/lambat (*crash*) saat menerima transaksi pemesanan berulang dalam waktu berdekatan.
- **Dampak:** Hambatan operasional pemesanan dan potensi hilangnya transaksi pelanggan.
- **Rekomendasi:** Lakukan optimasi kode sumber, *load testing*, optimasi query database, dan manajemen alokasi resource server.

### 4. [MODERATE] Dashboard Summary Tidak Menampilkan Data Aktual
- **Kondisi:** Ringkasan statistik (produk terjual, order diproses) tidak ter-update secara *real-time* setelah transaksi baru masuk.
- **Dampak:** Informasi monitoring operasional yang diterima admin menjadi bias/tidak akurat.
- **Rekomendasi:** Perbarui sinkronisasi trigger / event data dashboard agar merefleksikan perubahan status transaksi secara otomatis.

### 5. [MODERATE] Tampilan Antarmuka (UI/UX) Belum Optimal
- **Kondisi:** Logo tidak muncul di navbar, gambar banner terpotong (*cropping*), dan konten halaman *About Us* belum lengkap.
- **Dampak:** Mengurangi estetika profesionalitas dan pengalaman pengguna (*user experience*).
- **Rekomendasi:** Perbaiki styling CSS/responsiveness banner & logo navbar, serta lengkapi profil bisnis pada halaman *About Us*.

### 6. [MODERATE] Link Contact Us Menghasilkan Error 404
- **Kondisi:** Tautan media sosial pada halaman kontak belum terhubung ke akun resmi yang aktif.
- **Dampak:** Menghambat saluran komunikasi pelanggan dengan pengelola bisnis.
- **Rekomendasi:** Perbaiki routing URL dan pastikan seluruh tautan media sosial mengarah ke akun aktif resmi Werdy's Kitchen.

---

## Rencana Tindak Lanjut (Action Plan)

| No | Tindakan Perbaikan (*Action Item*) | Penanggung Jawab | Target Penyelesaian | Status |
| :---: | :--- | :---: | :---: | :---: |
| 1 | Penjadwalan & otomatisasi backup database ke cloud storage | Owner / Dev | 30 Nov 2026 | Open |
| 2 | Perbaikan dan pengujian fitur *Generate Report* | Owner / Dev | 15 Des 2026 | Open |
| 3 | Integrasi *real-time* statistik transaksi pada dashboard summary | Owner / Dev | 15 Des 2026 | Open |
| 4 | Optimasi resource sistem dan *load testing* performa website | Owner / Dev | 31 Des 2026 | Open |
| 5 | Perbaikan logo navbar, layout banner, dan konten *About Us* | Owner / Dev | 20 Nov 2026 | Open |
| 6 | Pembaruan tautan resmi pada menu *Contact Us* | Owner / Dev | 20 Nov 2026 | Open |

---

## Metodologi Audit
1. **Inquiry:** Wawancara langsung dengan pemilik bisnis dan admin sistem.
2. **Observation:** Pengamatan langsung terhadap alur kerja website dan dashboard admin.
3. **Inspection:** Pemeriksaan dokumen konfigurasi, database, dan antarmuka.
4. **Re-performance:** Pengujian ulang skenario checkout dan pesanan berulang.
5. **CAATs & Sampling:** Pengujian bantuan komputer dan sampling data transaksi.

---
*Laporan ini disusun oleh Muhammad Daffa Al Fansyah sebagai hasil audit independen sistem informasi Werdy's Kitchen.*
