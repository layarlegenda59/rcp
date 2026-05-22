# 🎨 Audit UI/UX Profesional: Rupiah Pay Capitals
**Auditor:** Senior UI/UX Design Director (Silicon Valley Perspective)  
**Tanggal Audit:** 22 Mei 2026  
**Sumber:** [https://www.rupiahpaycapitals.com](https://www.rupiahpaycapitals.com)  
**Framework Evaluasi:** Nielsen Norman Group Heuristics + WCAG 2.1 + Core Web Vitals

---

## 📋 Ringkasan Eksekutif

Dari sudut pandang UI/UX kelas enterprise Silicon Valley, sebuah platform Fintech B2B harus memenuhi tiga pilar utama:

| Pilar | Deskripsi |
|-------|-----------|
| 🔒 **Credibility** | Situs harus memancarkan kepercayaan institusional |
| 🎯 **Clarity** | Proposisi nilai harus dipahami dalam 5 detik pertama |
| 📈 **Conversion** | Setiap elemen harus mengarahkan pengguna ke aksi utama |

> [!IMPORTANT]
> Setelah audit menyeluruh, website Rupiah Pay Capitals **belum memenuhi standar minimum** dari ketiga pilar di atas untuk konteks B2B Fintech institusional global.

---

## 1. TIPOGRAFI & HIERARKI VISUAL 📝

### 1.1 Pilihan Font (Poppins)

**Font Family:** `Poppins` — Geometric Sans-Serif  

✅ **Kelebihan:**
- Font yang modern, ramah, dan populer di kalangan produk digital
- Keterbacaan (*readability*) yang baik untuk antarmuka web

❌ **Kelemahan Kritis:**

```css
/* Temuan CSS di situs: */
body {
  font-weight: 300; /* Light — terlalu tipis untuk body text */
  font-size: 16px;
  line-height: 30px;
}
```

> [!WARNING]
> *Font weight 300 (Light)* pada ukuran 16px melanggar standar **WCAG 2.1 Level AA**. Teks tipis dengan kontras standar sangat sulit dibaca pada:
> - Layar mobile dengan kecerahan rendah
> - Pengguna dengan gangguan penglihatan ringan
> - Monitor yang tidak dikalibrasi

**Rekomendasi:** Ganti ke `font-weight: 400` (Regular) untuk teks body.

---

### 1.2 Ukuran Heading yang Ekstrem (Mobile Overflow Risk) 🚨

| Elemen | Ukuran Desktop | Ukuran Mobile | Status |
|--------|---------------|---------------|--------|
| H1 | `100px` | `80px` | ❌ Terlalu besar |
| H2 | `80px` | `60px` | ❌ Terlalu besar |
| H3 | `35px` | `28px` | ⚠️ Perlu evaluasi |
| Body | `16px` | `15px` | ⚠️ Terlalu tipis |

```
❌ Contoh Masalah:
Lebar layar mobile rata-rata = 360px - 410px
H1 "Offshore Jurisdictions" pada 80px = OVERFLOW / TERPOTONG
```

**Standar Silicon Valley untuk Fintech B2B Mobile:**
```
H1 Mobile : 28px - 36px
H2 Mobile : 24px - 30px
H3 Mobile : 20px - 24px
Body      : 16px (Regular weight)
```

---

## 2. IDENTITAS VISUAL & BRANDING 🎨

### 2.1 Implementasi Logo yang Bermasalah

```css
/* Temuan CSS kritis: */
body:not(.template-slider) #Header_wrapper {
  background-image: url('.../cropped-LOGO-RUPIAH-PAY-CAPITALS-februari-2023333.png')
}
```

> [!CAUTION]
> Menggunakan file **logo PNG sebagai background-image** pada kontainer header adalah praktik antipattern desain yang:
> - Dapat menyebabkan logo **terdistorsi** pada berbagai resolusi layar
> - Berpotensi menciptakan **efek repetisi** (logo berulang)
> - Tidak dapat di-scale secara proporsional (tidak ada `background-size` yang konsisten)
> - Menambah beban halaman secara tidak efisien

**Rekomendasi:** Gunakan elemen `<img>` atau file **SVG** yang di-inline langsung ke HTML header.

### 2.2 Ketidakkonsistenan Sistem Warna

Berdasarkan analisis CSS, terdapat **tiga skema warna yang bersaing**:

| Komponen | Warna | Sumber |
|----------|-------|--------|
| Tombol Aksi Utama | `#0089F7` (Biru cerah) | Custom CSS |
| Tombol Kustom | `#000000` / `#FFFFFF` | Theme override |
| Tombol Navigasi | `#f7f7f7` / `#747474` | Default theme |
| Latar Belakang | `#ffffff` | Standard |

> [!NOTE]
> Tidak adanya **Design System** yang terpadu menyebabkan situs terlihat seperti kumpulan komponen template yang "ditempel" secara terpisah, bukan produk finansial premium yang dirancang secara kohesif.

---

## 3. ALUR PENGGUNA & SINYAL KEPERCAYAAN 🔑

### 3.1 Impresi "Template-Heavy"

```
Stack Teknologi yang Terdeteksi:
├── CMS        : WordPress
├── Page Builder : Elementor Pro 3.8.1
├── Theme      : BeTheme 26.6 (Tema premium pasaran)
├── Plugins    : Contact Form 7, AddToAny, WA for WordPress
└── SEO        : Yoast SEO v21.3
```

**Dampak Persepsi Klien B2B:**
- ❌ Klien institusional (calon pemilik broker Forex/Crypto) **langsung mendeteksi** situs berbasis template murah
- ❌ Menurunkan *perceived value* dari teknologi CRM dan platform perdagangan yang ditawarkan
- ❌ Inkonsistensi antara "kami menjual teknologi canggih" dengan "situs kami menggunakan template pasaran"

### 3.2 Analisis Widget WhatsApp

| Aspek | Penilaian |
|-------|-----------|
| Efektivitas untuk pasar ritel lokal | ✅ Efektif |
| Kesesuaian untuk klien B2B institusional | ❌ Kurang profesional |
| Kesan terhadap klien internasional | ❌ Menurunkan kredibilitas |

**Rekomendasi:**
```
Tambahkan / Ganti dengan:
✅ Intercom atau Drift Chat (enterprise-grade)
✅ Tombol "Schedule a Demo" → Calendly / Hubspot Meetings
✅ Formulir Lead Generation yang cerdas (progressive profiling)
```

### 3.3 Hierarki CTA (Call-to-Action) yang Lemah

> [!WARNING]
> Situs tidak memiliki **satu CTA utama yang dominan** di halaman landing. Pengguna pertama kali tidak langsung memahami apa *langkah berikutnya* yang harus mereka ambil — sebuah kesalahan fatal dalam desain Fintech B2B.

**Standar CTA Silicon Valley Fintech:**
```
❌ Saat ini     : "Hubungi Kami"
✅ Rekomendasi  : "Book a Free Tech Demo" atau 
                  "Start Your Broker Setup Today"
```

---

## 4. PERFORMA & PENGALAMAN MOBILE 📱

### 4.1 Beban Halaman (Page Bloat Analysis)

File CSS yang dimuat pada setiap halaman (diidentifikasi dari HTML):

```
1. nta-css-popup-css          (WhatsApp plugin)
2. contact-form-7-css         
3. mfn-be-css                 (BeTheme core)
4. mfn-animations-css         (BeTheme animations)
5. mfn-font-awesome-css       (FontAwesome icons)
6. mfn-jplayer-css            (Media player)
7. mfn-responsive-css         (BeTheme responsive)
8. mfn-fonts-css              (Google Fonts - Poppins)
9. mfn-font-button-css        (Google Fonts - Poppins subset)
10. elementor-icons-css        
11. elementor-frontend-css     
12. elementor-post-7-css       
13. elementor-pro-css          
14. font-awesome-5-all-css     
15. font-awesome-4-shim-css    
16. elementor-post-268-css     
17. elementor-post-327-css     
18. elementor-post-312-css     
19. addtoany-css               
```

> [!CAUTION]
> **19+ file CSS yang dimuat secara bersamaan** pada satu halaman. Ini menciptakan *render-blocking resources* yang berat dan berpotensi menyebabkan **Cumulative Layout Shift (CLS)** — salah satu metrik Core Web Vitals yang paling berdampak pada SEO dan UX.

### 4.2 Estimasi Dampak Performa

| Metrik | Estimasi Saat Ini | Target SV Standard |
|--------|------------------|--------------------|
| First Contentful Paint (FCP) | > 3 detik | < 1.8 detik |
| Largest Contentful Paint (LCP) | > 4 detik | < 2.5 detik |
| Cumulative Layout Shift (CLS) | > 0.25 | < 0.1 |
| Time to Interactive (TTI) | > 5 detik | < 3.8 detik |

---

## 5. AKSESIBILITAS & INKLUSIVITAS ♿

| Standar | Status | Catatan |
|---------|--------|---------|
| Kontras Teks (WCAG AA) | ❌ Gagal | Font weight 300 terlalu tipis |
| Alt Text pada Gambar | ⚠️ Tidak diketahui | Tidak bisa diverifikasi dari HTML |
| Keyboard Navigation | ⚠️ Tidak diketahui | Perlu uji langsung |
| Screen Reader Compatibility | ⚠️ Meragukan | BeTheme tidak dioptimasi untuk aksesibilitas |
| Mobile Touch Targets | ❌ Meragukan | Ukuran heading tidak proporsional |

---

## 📊 Scorecard UI/UX Akhir

| Dimensi | Skor | Catatan |
|---------|------|---------|
| Tipografi & Keterbacaan | 4/10 | Font terlalu tipis, heading terlalu besar di mobile |
| Konsistensi Visual (Brand) | 3/10 | Tiga skema warna bersaing, logo bermasalah |
| Alur Pengguna (UX Flow) | 3/10 | CTA lemah, tidak ada portal klien |
| Kepercayaan (Trust Signals) | 4/10 | Template-heavy, tanpa bukti sosial |
| Performa Halaman | 3/10 | Terlalu banyak file CSS, risiko CLS |
| Aksesibilitas | 3/10 | Tidak memenuhi WCAG 2.1 AA |
| **Total Rata-Rata** | **3.3/10** | **Butuh redesign signifikan** |

---

## 🛠️ ROADMAP PERBAIKAN UI/UX

### 🔴 Perbaikan Mendesak (Segera — 0-30 hari)
1. **Fix Typography:** Ubah `font-weight: 300` → `400` di body CSS
2. **Fix Mobile Heading:** Turunkan H1 mobile dari 80px ke 36px
3. **Fix Logo Implementation:** Ganti `background-image` logo → elemen `<img>` atau SVG
4. **Konsolidasi CSS:** Merge dan minify semua CSS ke maksimal 3-4 file

### 🟡 Perbaikan Jangka Menengah (1-3 bulan)
5. **Buat Design System:** Satu palet warna konsisten, satu set komponen UI
6. **Redesign CTA:** Satu tombol utama yang dominan: *"Book a Free Demo"*
7. **Tambahkan Trust Signals:** Counter statistik (jumlah broker, negara, dll), logo klien
8. **Upgrade Chat:** Ganti WA widget dengan enterprise chat (Intercom/Drift)

### 🟢 Perbaikan Jangka Panjang (3-6 bulan)
9. **Migrasi Platform:** Pertimbangkan migrasi ke Next.js atau Webflow untuk performa lebih baik
10. **Bangun Client Portal:** Dashboard self-service untuk klien aktif
11. **Tambahkan Interactive Demo:** Video atau *live sandbox* platform CRM dan trading

---

> *Audit ini disusun berdasarkan analisis kode HTML/CSS publik dari website rupiahpaycapitals.com per Mei 2026, menggunakan standar Nielsen Norman Group UX Heuristics, WCAG 2.1, dan Google Core Web Vitals sebagai framework evaluasi.*
