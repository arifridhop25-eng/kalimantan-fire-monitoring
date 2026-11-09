# Kalimantan Fire Monitoring System

Prototype WebGIS dashboard sisi-klien untuk visualisasi data kebakaran hutan dan lahan di Kalimantan.

## Menjalankan
1. Ekstrak ZIP.
2. Buka folder di Visual Studio Code.
3. Jalankan `index.html` menggunakan ekstensi Live Server.
4. Pastikan internet aktif karena Leaflet dan pustaka pendukung dimuat dari CDN.

## Format data
- GeoJSON: unggah `.geojson` atau `.json`.
- Shapefile: kompres komponen `.shp`, `.shx`, `.dbf`, dan `.prj` ke satu ZIP lalu unggah.
- CSV: kolom koordinat harus dikenali sebagai `latitude`/`longitude`, `lat`/`lon`, atau `x`/`y`.
- Excel: sheet pertama dibaca; kolom koordinat sama seperti CSV.
- GeoTIFF: unggah `.tif`/`.tiff` dengan CRS/georeferensi valid. Renderer awal menggunakan grayscale dan perlu disesuaikan untuk raster kategorikal.
- PNG/JPG: perlu memasukkan batas koordinat utara, selatan, timur, dan barat.
- GPKG: ekspor layer dari QGIS ke GeoJSON (EPSG:4326) terlebih dahulu.

## Catatan penting
- File diproses secara lokal di browser; tidak ada penyimpanan permanen/server.
- GeoJSON yang diunggah sebaiknya menggunakan EPSG:4326.
- GeoTIFF besar dapat menghabiskan memori browser. Untuk produksi, gunakan Cloud Optimized GeoTIFF (COG) dan layanan tile.
- Statistik luas membaca atribut `area_ha`, `luas_ha`, `luas_hektar`, `area_km2`, atau `luas_km2`. Pastikan satuan dan definisinya benar.
- Filter tahun/provinsi berlaku pada layer vektor yang mempunyai atribut yang dikenali. Raster dan image overlay tidak difilter.
- Dashboard ini prototipe, bukan sistem peringatan dini atau sumber data hotspot otomatis.
- Untuk penggunaan publik/produksi, tambahkan backend, autentikasi, database spasial (misalnya PostGIS), validasi data, metadata, dan kebijakan keamanan.
