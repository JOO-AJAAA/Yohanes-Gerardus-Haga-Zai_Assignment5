# Ringkasan Tugas Sesi 5 — Spatial Data (Python)

Dokumen ini menjelaskan secara singkat **apa yang dibuat** di notebook _Task Sesi 5_Working with Spatial Data Python.ipynb_ dan **kegunaannya**, dengan bahasa yang lebih mudah dipahami.

## Gambaran Umum

Di notebook ini kamu:

- Mengambil data peta berbentuk **polygon** (area/ wilayah) dari sebuah API.
- Menampilkan data tersebut ke peta interaktif.
- Mengolah bentuk wilayah untuk beberapa kebutuhan analisis sederhana (misalnya membuat “zona sekitar”, merapikan bentuk, memotong area, menggabungkan area, dan menghitung luas).
- Menyimpan hasilnya ke beberapa file **GeoJSON** agar bisa dipakai lagi (misalnya dibuka di QGIS/ArcGIS atau dipakai untuk tugas lanjutan).

## Penjelasan Tiap Bagian (Bahasa Ringan)

### 1) Ambil & Tampilkan Data Polygon dari API

**Yang dibuat:** data wilayah dari sumber online + peta interaktif.

**Gunanya:**

- Memastikan datanya berhasil diambil.
- Melihat bentuk wilayah secara cepat di peta (cek apakah lokasinya sudah benar).

### 2) Konversi ke GeoDataFrame & Cek CRS

**Yang dibuat:** data peta dalam format yang lebih enak untuk diolah di Python.

**Gunanya:**

- Supaya langkah-langkah berikutnya (buffer, clip, dissolve, dll.) bisa dilakukan dengan rapi.
- Memastikan “sistem koordinat” data konsisten, jadi hasilnya tidak melenceng.

### 3) Buffer Polygon (100 meter)

**Yang dibuat:** “zona penyangga” sekitar wilayah sejauh 100 meter.

**Gunanya:**

- Untuk melihat area pengaruh/area sekitar objek.
- Contoh pemakaian: zona aman, area cakupan, atau jarak layanan di sekitar suatu wilayah.

### 4) Simplify Polygon

**Yang dibuat:** versi bentuk wilayah yang lebih sederhana (detail kecil dikurangi).

**Gunanya:**

- Peta jadi lebih ringan dan cepat ditampilkan.
- Cocok untuk visualisasi atau ringkasan, saat detail tinggi tidak terlalu dibutuhkan.

### 5) Clip Polygon dengan Bounding Box

**Yang dibuat:** hasil potongan wilayah hanya pada area tertentu (kotak batas / area fokus).

**Gunanya:**

- Membatasi analisis agar fokus ke area tertentu saja.
- Mengurangi data yang terlalu luas supaya lebih cepat diproses.

### 6) Dissolve Polygon Berdasarkan KELAS

**Yang dibuat:** penggabungan polygon berdasarkan kategori/kelas (misalnya atribut `KELAS`).

**Gunanya:**

- Membuat ringkasan per kategori.
- Lebih mudah melihat total area/bentuk gabungan untuk tiap kelas.

### 7) Union Seluruh Polygon

**Yang dibuat:** satu polygon gabungan besar dari semua wilayah.

**Gunanya:**

- Mendapatkan “batas luar” keseluruhan area.
- Berguna untuk overview dan analisis global.

### 8) Tambah Kolom Luas (km²)

**Yang dibuat:** kolom baru berisi luas wilayah dalam km².

**Gunanya:**

- Membandingkan ukuran antar wilayah.
- Membuat laporan sederhana (misalnya luas per area).

### 9) Export Subset Berdasarkan Filter

**Yang dibuat:** hanya sebagian data (contoh: satu `KECAMATAN`) disimpan sebagai file terpisah.

**Gunanya:**

- Fokus analisis pada satu area tertentu.
- Membuat file yang lebih kecil untuk dibagikan/ditampilkan.

## File Output (Hasil yang Disimpan)

Notebook ini menghasilkan beberapa file GeoJSON berikut:

- `buffer_100m.geojson`
  - Isi: wilayah + “zona 100 meter” di sekelilingnya.
  - Cocok untuk: analisis area sekitar.

- `simplified_buffer_50m.geojson`
  - Isi: bentuk wilayah yang lebih sederhana (lebih ringan).
  - Cocok untuk: visualisasi cepat.

- `clipped_bbox.geojson`
  - Isi: wilayah yang sudah dipotong hanya di area fokus.
  - Cocok untuk: analisis area kecil.

- `dissolved_by_kelas.geojson`
  - Isi: wilayah gabungan per `KELAS`.
  - Cocok untuk: ringkasan per kategori.

- `union_all.geojson`
  - Isi: gabungan semua wilayah jadi satu.
  - Cocok untuk: batas total/overview.

- `data_with_area_km2.geojson`
  - Isi: data asli + kolom luas (km²).
  - Cocok untuk: laporan/analisis luas.

- `subset_buahbatu.geojson` (atau `subset_<nama_kecamatan>.geojson`)
  - Isi: data yang sudah difilter untuk satu kecamatan.
  - Cocok untuk: fokus ke area tertentu.

## Cara Melihat Hasilnya (Paling Mudah)

- Buka file `.geojson` di aplikasi peta seperti **QGIS** (drag & drop).
- Atau tetap lihat di notebook dengan peta interaktif (Folium).

---

Kalau kamu mau, saya bisa juga bantu:

- merapikan teks penjelasan di dalam notebook agar konsisten (lebih “narasi”), atau
- menambahkan 1 bagian “Kesimpulan” singkat di akhir notebook.
