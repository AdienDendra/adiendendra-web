+++
title = "AD Skin Tool"
translationKey = "ad-skin-tool"
summary = "Pengeditan skin weight berbasis region, visualisasi viewport, serta workflow Mirror dan Transfer dengan preview untuk Autodesk Maya."
description = "AD Skin Tool untuk Maya 2023 sampai 2027. Bind, flood, smooth, visualisasi, mirror, dan transfer skin weights dengan kontrol region dan preview."
date = 2026-08-14T21:09:27+10:00
lastmod = 2026-11-22T19:10:02+11:00

featured = true
resource_type = "maya-tool"
resource_label = "Maya Tool"
access = "commercial"
access_label = "Komersial"
compatibility = "Maya 2023 sampai 2027"
preview_label = "AD"
weight = 1

hideMeta = false
comments = false
showToc = false
ShowReadingTime = false
ShowPostNavLinks = false
+++

AD Skin Tool menggabungkan pengeditan skin weights, pengelolaan influence, dan pemeriksaan weight dalam satu workflow Autodesk Maya. Flood berbasis region, smoothing pada komponen, dan visualisasi weight di viewport membantu proses blocking dan refinement. Mirror dan Transfer juga memiliki tahapan preview sesuai fungsi masing-masing.

<div class="product-facts" aria-label="Ringkasan produk">
  <div class="product-fact"><span>Harga</span><strong>US$25, sekali bayar</strong></div>
  <div class="product-fact"><span>Trial</span><strong>48 jam, seluruh fitur</strong></div>
  <div class="product-fact"><span>Lisensi</span><strong>Perpetual, maksimal dua perangkat</strong></div>
  <div class="product-fact"><span>Kompatibilitas</span><strong>Maya 2023 sampai 2027, sesuai build</strong></div>
</div>

<div class="product-actions">
  <a class="product-download-button" href="#kompatibilitas-dan-unduhan">Download AD Skin Tool</a>
  <a class="product-download-button product-download-button--secondary" href="#video-demo">Tonton Video Demo</a>
</div>

## Video Demo

Video singkat berikut memperlihatkan workflow utama AD Skin Tool di Maya. Penjelasan tiap operasi tersedia di [dokumentasi AD Skin Tool](/id/documentation/ad-skin-tool-tutorial/).

<div class="product-demo-frame">
  <iframe
    src="https://www.youtube-nocookie.com/embed/YW-Ko5yevRg"
    title="Video demo workflow AD Skin Tool"
    loading="lazy"
    referrerpolicy="strict-origin-when-cross-origin"
    allowfullscreen>
  </iframe>
</div>

[Tonton video demo di YouTube](https://www.youtube.com/watch?v=YW-Ko5yevRg)

## Workflow Utama

- **Flood berbasis region:** Menghitung ulang region dari joint yang sudah menjadi bind influence. Component selection dan Maya Soft Selection menentukan area yang diproses, sedangkan Blend dan Iterations mengatur hasilnya.
- **Smooth:** Meratakan skin weights pada komponen yang dipilih atau seluruh mesh dengan tetap menghormati locked influences dan Soft Selection falloff.
- **Bind dan Add Influence:** Melakukan bind geometry dan menambahkan influence ke skinCluster yang sudah ada melalui satu antarmuka.
- **Skin Weight Visual:** Memeriksa distribusi weight langsung di viewport Maya. Tampilan visual ini bersifat sementara dan tidak mengubah skin weights yang tersimpan.
- **Mirror pada posed mesh:** Melakukan preview dan registrasi vertex pairing sebelum mirror weight. Pairing yang tersimpan dapat digunakan kembali pada posed mesh tanpa mengembalikan karakter ke bind pose.
- **Transfer dengan Preview:** Mendaftarkan source surface yang sudah memiliki skin weights dan target mesh, memeriksa correspondence melalui preview, lalu menerapkan weight pada komponen atau keseluruhan mesh yang memenuhi syarat.

### Preview workflow

Contoh berikut menggunakan GIF yang sama dengan dokumentasi lengkap AD Skin Tool.

<div class="product-workflow-grid">
  <figure class="product-workflow-card">
    <img src="/images/documentation/ad-skin-tool/05-flood.gif" alt="Operasi Flood AD Skin Tool menggunakan bind influence dan komponen mesh yang dipilih di Maya" loading="lazy" decoding="async">
    <figcaption><strong>Flood berbasis region</strong><span>Blocking dan refinement weight dalam area komponen yang dipilih.</span></figcaption>
  </figure>
  <figure class="product-workflow-card">
    <img src="/images/documentation/ad-skin-tool/07-skin-weight-visual.gif" alt="Skin Weight Visual menampilkan distribusi skin weights pada viewport Maya" loading="lazy" decoding="async">
    <figcaption><strong>Skin Weight Visual</strong><span>Memeriksa distribusi weight langsung di viewport Maya.</span></figcaption>
  </figure>
</div>

Demonstrasi [Mirror, Transfer, dan Smooth](/id/documentation/ad-skin-tool-tutorial/) lainnya tersedia di tutorial.

## Harga, Trial, dan Lisensi

Harga AD Skin Tool adalah **US$25** dengan pembayaran satu kali dan **lisensi Individual perpetual**. Setiap lisensi dapat digunakan pada maksimal **dua perangkat pribadi**. Tidak ada biaya berlangganan. Versi mayor AD Skin Tool yang dirilis kemudian mungkin dijual terpisah.

Trial memberikan akses penuh ke seluruh fitur selama **48 jam**. Periode ini hanya dimulai setelah **Start 48-Hour Trial** dipilih pada jendela **License**, bukan ketika Maya atau tool dibuka. Koneksi internet diperlukan untuk memulai trial, tetapi pembelian tidak diwajibkan.

Setelah instalasi, tombol **Buy License** pada jendela **License** membuka checkout Freemius. Kode promo peluncuran yang tersedia ditampilkan di dalam tool. Pajak yang berlaku dan total pembayaran akhir ditampilkan sebelum transaksi diselesaikan.

## Kompatibilitas dan Unduhan

Pilih paket yang sesuai dengan versi Maya, sistem operasi, dan arsitektur prosesor. Setiap ZIP dibuat untuk versi Maya dan platform tertentu.

| Sistem operasi | Arsitektur | Maya 2023 | Maya 2024 | Maya 2025 | Maya 2026 | Maya 2027 |
|---|---|---|---|---|---|---|
| Windows | x86-64 | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2023-cp39-windows-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2024-cp310-windows-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2025-cp311-windows-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2026-cp311-windows-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2027-cp313-windows-x86_64.zip) |
| Linux | x86-64 | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2023-cp39-linux-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2024-cp310-linux-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2025-cp311-linux-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2026-cp311-linux-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2027-cp313-linux-x86_64.zip) |
| macOS | Intel | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2023-cp39-macos-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2024-cp310-macos-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2025-cp311-macos-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2026-cp311-macos-x86_64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2027-cp313-macos-x86_64.zip) |
| macOS | Apple Silicon | Tidak tersedia | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2024-cp310-macos-arm64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2025-cp311-macos-arm64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2026-cp311-macos-arm64.zip) | [ZIP](https://github.com/AdienDendra/ad-skin-tool-downloads/releases/download/v1.0.0/ad-skin-tool-native-maya2027-cp313-macos-arm64.zip) |

Build macOS Apple Silicon tersedia mulai Maya 2024. Build untuk Maya 2023 tidak tersedia pada arsitektur tersebut.

## Instalasi dan Aktivasi

1. Download ZIP yang sesuai dengan instalasi Maya, lalu ikuti petunjuk instalasi di dalam paket.
2. Buka AD Skin Tool di Maya, kemudian buka jendela **License**.
3. Pilih **Start 48-Hour Trial** untuk memulai trial, atau gunakan **Buy License** dan **Activate License** untuk lisensi yang sudah dibeli.

Freemius mengirim license key ke alamat email yang digunakan saat checkout. [Panduan Lisensi](/id/documentation/ad-skin-tool-license/) membahas aktivasi, deaktivasi perangkat, validasi, penggunaan offline, dan troubleshooting.

## Validasi Online dan Akses Offline

Lisensi berbayar biasanya divalidasi secara online setiap **tujuh hari**. Setiap validasi online yang berhasil memperbarui akses offline hingga **30 hari**. Jika periode tersebut berakhir tanpa koneksi yang berhasil, validasi online diperlukan sebelum fitur berlisensi dapat digunakan kembali.

Lisensi perpetual tidak kedaluwarsa hanya karena masa akses offline berakhir. Penjelasan lengkap tersedia di [Panduan Lisensi](/id/documentation/ad-skin-tool-license/).

## Pertanyaan Umum

**Apakah trial dimulai secara otomatis?**

Tidak. Trial 48 jam baru dimulai ketika **Start 48-Hour Trial** dipilih pada jendela **License**.

**Apakah koneksi internet harus selalu aktif?**

Tidak. Lisensi berbayar yang valid tetap mendukung penggunaan offline selama periode akses 30 hari yang masih berlaku. Koneksi berikutnya memungkinkan validasi online memperbarui periode tersebut.

**Apakah lisensi dapat dipindahkan ke komputer lain?**

Bisa. Lakukan deaktivasi pada komputer yang tidak lagi digunakan untuk membebaskan salah satu dari dua slot perangkat, lalu aktifkan komputer baru dengan license key yang sama. Prosesnya dijelaskan di [Panduan Lisensi](/id/documentation/ad-skin-tool-license/).

## Bantuan dan Ketentuan Pembelian

Bantuan terkait instalasi, lisensi, aktivasi perangkat, kompatibilitas, dan kendala teknis produk tersedia melalui [hello@adiendendra.com](mailto:hello@adiendendra.com).

**Freemius** menangani checkout, pembayaran, dan email pembelian sebagai Merchant of Record. Trial 48 jam disarankan untuk memastikan kompatibilitas dan kesesuaian workflow sebelum membeli. Periksa harga akhir, pajak, dan ketentuan refund saat checkout. Pembelian pada umumnya bersifat final, sesuai ketentuan checkout dan hak konsumen yang berlaku.

---

Autodesk dan Maya adalah merek dagang terdaftar atau merek dagang milik Autodesk, Inc., dan/atau anak perusahaan maupun afiliasinya di Amerika Serikat dan negara lainnya. AD Skin Tool serta Adien Dendra tidak berafiliasi dengan, disponsori, didukung, atau disetujui oleh Autodesk.
