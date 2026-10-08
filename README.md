# LAPORAN PRAKTIKUM DESAIN WEB A
## Pertemuan 4: Box Model, Class Reusable, dan Responsive Layout (Studi Kasus Arunika Studio)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![Status](https://img.shields.io/badge/Status-Selesai-success)

---

## 📋 Identitas Praktikan

| | |
|---|---|
| **Nama** | Ilham Baihaqi |
| **NIM** | 4525210029 |
| **Program Studi** | Teknik Informatika |
| **Fakultas** | Teknik |
| **Universitas** | Universitas Pancasila |
| **Mata Kuliah** | Praktikum Desain Web A |
| **Pertemuan** | 4 |

---

## 1. Tujuan Praktikum

1. Membangun ulang halaman web menjadi dua *file*: `index.html` (struktur) dan `style.css` (tampilan).
2. Menerapkan *box model*: `box-sizing`, `padding`, `margin`, `border`, dan `border-radius`.
3. Membuat minimal dua **class reusable** yang dapat dipakai ulang.
4. Menerapkan satu ***media query*** di bawah 768px agar halaman nyaman di ponsel.
5. Menyusun tiga *card* layanan dengan **Flexbox** yang berubah menjadi satu kolom pada layar kecil.
6. Menjaga seluruh kode CSS tetap terpusat dalam satu *file* eksternal.

---

## 2. Dasar Teori

### 2.1 Box Model
Setiap elemen HTML dianggap sebagai kotak yang terdiri dari lapisan berikut (dari dalam ke luar): **content → padding → border → margin**.

| Lapisan | Fungsi |
|---|---|
| **Content** | Isi elemen (teks atau gambar) |
| **Padding** | Ruang di dalam elemen, antara isi dan border |
| **Border** | Garis tepi elemen |
| **Margin** | Jarak elemen dengan elemen lain di luarnya |

Dengan `box-sizing: border-box`, nilai `width` sudah **termasuk** padding dan border, sehingga ukuran elemen lebih mudah diperhitungkan.

### 2.2 Class Reusable
*Class* adalah selector yang ditulis dengan titik (`.nama-class`) dan dipanggil lewat atribut `class="..."`. Disebut *reusable* karena satu aturan CSS dapat dipakai berkali-kali pada elemen yang berbeda tanpa menulis ulang kodenya.

### 2.3 Flexbox
Flexbox adalah model tata letak satu dimensi. Dengan `display: flex`, elemen anak disusun sejajar dalam satu baris (`flex-direction: row`) atau satu kolom (`flex-direction: column`).

| Properti | Fungsi |
|---|---|
| `display: flex` | Mengaktifkan Flexbox pada elemen induk |
| `flex-direction` | Arah susunan elemen anak (baris atau kolom) |
| `flex: 1` | Membuat elemen anak membagi lebar secara merata |
| `gap` | Jarak antar elemen anak |
| `justify-content` | Perataan elemen anak pada sumbu utama |
| `align-items` | Perataan elemen anak pada sumbu silang |

### 2.4 Media Query
*Media query* adalah aturan CSS yang hanya berlaku pada kondisi tertentu, misalnya lebar layar.

```css
@media (max-width: 767px) {
  /* aturan khusus layar di bawah 768px */
}
```

---

## 3. Alat dan Bahan

| Kategori | Keterangan |
|---|---|
| **Bahasa** | HTML5 dan CSS3 |
| **Text Editor** | Visual Studio Code _(sesuaikan)_ |
| **Browser** | Google Chrome / Microsoft Edge _(sesuaikan)_ |
| **Version Control** | Git dan GitHub |
| **Aset Gambar** | Tidak ada (logo dibuat dengan CSS) |

---

## 4. Struktur Proyek

```
Tugas_Arunika_Studio/
├── index.html                      # Halaman utama (struktur)
├── css/
│   └── style.css                   # Seluruh aturan tampilan
├── screenshots/
│   ├── tampilan-desktop.png  # Hasil tampilan desktop
│   └── tampilan-mobile.png   # Hasil tampilan mobile
├── ringkasan-dan-peran.md          # Ringkasan 150-250 kata dan catatan peran
└── README.md                       # Laporan praktikum
```

---

## 5. Pembahasan dan Hasil

### 5.1 Studi Kasus

Arunika Studio membutuhkan *landing page* sederhana yang tetap nyaman pada desktop dan ponsel. Konten terdiri dari *header*, *hero*, tiga layanan, dan *footer*. Masalah utamanya adalah kode CSS tidak boleh tersebar, serta tiga *card* harus berubah menjadi satu kolom pada layar kecil.

**Deskripsi:** Halaman dibuat dalam satu kotak utama berlatar putih dengan sudut membulat, berwarna hijau tosca dan aksen koral.

### 5.2 Menghubungkan HTML dengan CSS

Seluruh gaya berada di satu *file* eksternal sehingga kode tidak tersebar.

```html
<head>
  <link rel="stylesheet" href="css/style.css">
</head>
```

### 5.3 Struktur HTML

```html
<div class="page">
  <header>   <!-- logo dan navigasi -->
  <section id="hero">     <!-- judul, deskripsi, tombol -->
  <section id="layanan">  <!-- tiga card layanan -->
  <footer>   <!-- email dan hak cipta -->
</div>
```

| Bagian | Fungsi |
|---|---|
| `<header>` | Nama studio dan menu navigasi |
| `#hero` | Logo lingkaran, judul utama, deskripsi, dan tombol |
| `#layanan` | Tiga *card* layanan: Web Design, Web Development, Branding |
| `<footer>` | Alamat email dan hak cipta |

### 5.4 Penerapan Box Model

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.page {
  max-width: 880px;
  margin: 0 auto;
  background-color: #ffffff;
  border-radius: 24px;
  overflow: hidden;
}
```

- `*` me-reset margin dan padding bawaan browser, lalu `border-box` membuat lebar elemen sudah mencakup padding dan border.
- `margin: 0 auto` memusatkan kotak utama (nilai `auto` membagi sisa ruang kiri-kanan secara sama).
- `border-radius` membulatkan sudut, dan `overflow: hidden` memastikan isi tidak keluar dari sudut yang membulat.

### 5.5 Class Reusable

Dua class reusable yang dibuat:

```css
.heading {
  font-size: 24px;
  color: #0f5e56;
  text-align: center;
  padding-bottom: 10px;
  margin-bottom: 25px;
  border-bottom: 3px dotted #ff6b6b;
}

.btn {
  display: inline-block;
  padding: 12px 30px;
  background-color: #ff6b6b;
  color: #ffffff;
  font-weight: bold;
  text-decoration: none;
  border-radius: 50px;
}

.btn:hover {
  background-color: #0f5e56;
}
```

| Class | Dipakai untuk | Penerapan Box Model |
|---|---|---|
| `.heading` | Judul section ("Layanan Kami") | `padding-bottom`, `margin-bottom`, `border-bottom` |
| `.btn` | Tombol "Lihat Layanan" | `padding`, `border-radius` |

Kedua class dapat dipakai ulang di bagian mana pun tanpa menulis ulang aturannya.

### 5.6 Tiga Card dengan Flexbox

```css
.service-list {
  display: flex;
  gap: 18px;
}

.service-card {
  flex: 1;
  padding: 22px;
  background-color: #f0faf8;
  border-top: 5px solid #0f5e56;
  border-radius: 14px;
}
```

`display: flex` menyusun tiga *card* sejajar, dan `flex: 1` pada tiap *card* membuat lebarnya sama rata. `gap` memberi jarak antar *card*.

### 5.7 Media Query (di Bawah 768px)

```css
@media (max-width: 767px) {
  header {
    flex-direction: column;
    gap: 10px;
  }

  #hero h2 {
    font-size: 24px;
  }

  .service-list {
    flex-direction: column;
  }
}
```

Pada lebar layar di bawah 768px, `flex-direction: column` mengubah susunan tiga *card* dari berjajar menjadi **satu kolom**. Header dan ukuran judul juga disesuaikan agar nyaman dibaca di ponsel.

**Hasil tampilan desktop:**
<img width="1280" height="1021" alt="tampilan-desktop" src="https://github.com/user-attachments/assets/b7974139-e084-4e44-820d-a118c93de989" />


**Hasil tampilan mobile:**
<img width="375" height="1457" alt="tampilan-mobile" src="https://github.com/user-attachments/assets/4bc45ace-9e4e-4cd6-9d21-180ee4732724" />


---

## 6. Perbandingan Tampilan Desktop dan Mobile

| Aspek | Desktop (≥ 768px) | Mobile (< 768px) |
|---|---|---|
| **Header** | Nama studio di kiri, menu di kanan | Nama studio di atas, menu di bawah (rata tengah) |
| **Judul hero** | 32px | 24px |
| **Card layanan** | Tiga kolom sejajar | Satu kolom ke bawah |
| **Padding section** | Lebih lega | Lebih ringkas |

---

## 7. Rekap Properti CSS yang Digunakan

| Kategori | Properti |
|---|---|
| **Teks** | `color`, `font-family`, `font-size`, `font-weight`, `line-height`, `text-align`, `text-decoration` |
| **Latar** | `background-color` |
| **Box model** | `box-sizing`, `width`, `max-width`, `height`, `margin`, `padding`, `padding-bottom`, `margin-bottom` |
| **Border** | `border`, `border-top`, `border-bottom`, `border-radius` |
| **Layout** | `display: flex`, `flex-direction`, `flex`, `gap`, `justify-content`, `align-items` |
| **Efek** | `box-shadow`, `overflow` |
| **Selector** | elemen, class (`.`), id (`#`), turunan (`.brand span`), pseudo-class (`:hover`) |
| **Responsive** | `@media (max-width: 767px)` |

---

## 8. Cara Menjalankan

1. **Clone repositori**
```bash
   git clone https://github.com/IlhamBaihaqi24/Prak_DW_A-Pertemuan-4.git
```
2. **Masuk ke folder proyek**
```bash
   cd Prak_DW_A-Pertemuan-4
```
3. **Buka file HTML di browser**: `index.html`, dengan klik dua kali atau memakai ekstensi *Live Server* di VS Code.
4. **Uji tampilan mobile**: tekan `F12` di browser, lalu aktifkan *Toggle Device Toolbar* (`Ctrl + Shift + M`).

> ⚠️ Folder `css/` harus berada satu level dengan `index.html`, dan penulisan path harus persis sama (perhatikan huruf besar/kecil).

---

## 10. Kesimpulan

Dari praktikum Pertemuan 4 ini dapat disimpulkan bahwa:

1. Halaman web yang rapi dapat dibangun dari dua *file* saja, yaitu `index.html` untuk struktur dan `style.css` untuk tampilan.
2. **Box model** (`padding`, `border`, `margin`) beserta `box-sizing: border-box` membuat pengaturan jarak dan ukuran elemen lebih terukur.
3. **Class reusable** seperti `.heading` dan `.btn` mengurangi pengulangan kode dan mempermudah perawatan.
4. **Flexbox** memudahkan penyusunan tiga *card* yang sejajar dengan lebar sama rata.
5. Satu ***media query*** di bawah 768px sudah cukup untuk mengubah tiga *card* menjadi satu kolom sehingga halaman tetap nyaman di ponsel.

Materi ini menjadi dasar sebelum melanjutkan ke tata letak yang lebih kompleks pada pertemuan berikutnya.

---

<p align="center">
  <sub>© 2026 Ilham Baihaqi (4525210029) · Teknik Informatika · Universitas Pancasila</sub>
</p>
