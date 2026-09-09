+++
title = "Kebijakan Privasi"
translationKey = "privacy-policy"
description = "Cara website ini dan AD Skin Tools memproses data website, support, komentar, transaksi, licensing, dan perangkat lokal."
date = 2026-09-09T20:58:00+10:00
lastmod = 2026-09-09T20:58:00+10:00
comments = false
showToc = true
TocOpen = true
ShowReadingTime = false
ShowPostNavLinks = false
+++

**Tanggal berlaku: 9 September 2026**

Kebijakan Privasi ini menjelaskan cara website `architecture.adiendendra.com` dan AD Skin Tools memproses informasi. Website dan produk dioperasikan oleh Adien Dendra di Sydney, Australia. Pertanyaan mengenai privasi dapat dikirimkan ke [hello@adiendendra.com](mailto:hello@adiendendra.com).

Kebijakan ini tidak menyatakan bahwa tidak ada data yang dikumpulkan. Infrastruktur website, email, komentar, payment provider, dan licensing service perlu memproses informasi terbatas agar dapat beroperasi.

## 1. Kunjungan website dan hosting

Website ini merupakan static site Hugo yang di-host melalui Cloudflare Pages dan dikirimkan melalui jaringan Cloudflare. Cloudflare dapat memproses informasi teknis request dan security seperti:

- Alamat IP dan perkiraan lokasi jaringan.
- URL yang diminta serta tanggal dan waktu request.
- Informasi browser, perangkat, sistem operasi, dan request header.
- Cache, performance, error, abuse-prevention, dan security event.

Cloudflare dapat memasang strictly necessary security cookies ketika fitur perlindungannya memerlukannya. Website ini tidak dengan sengaja mengonfigurasi advertising tracker atau third-party advertising cookies.

Website menggunakan `localStorage` browser untuk mengingat pilihan tema terang atau gelap. Filter 3D Tools lokal berjalan di browser dan tidak mengirim pilihan filter ke server.

Lihat <a href="https://www.cloudflare.com/privacypolicy/" target="_blank" rel="noopener noreferrer" aria-label="Cloudflare Privacy Policy, dibuka di tab baru">Cloudflare Privacy Policy</a> dan <a href="https://developers.cloudflare.com/fundamentals/reference/policies-compliances/cloudflare-cookies/" target="_blank" rel="noopener noreferrer" aria-label="dokumentasi Cloudflare Cookies, dibuka di tab baru">Cloudflare Cookies</a> untuk informasi tentang pemrosesan oleh Cloudflare.

## 2. Konten eksternal yang digunakan website

Website saat ini memuat resource Mermaid dan KaTeX dari content-delivery network jsDelivr. Homepage juga memuat profile image dari GitHub. Ketika resource tersebut dimuat, provider dapat menerima informasi request biasa seperti alamat IP pengunjung, browser header, resource yang diminta, dan timestamp.

Saat ini belum ada third-party video player yang ditanamkan pada product page AD Skin Tools. Kebijakan ini akan diperbarui ketika provider video demo ditambahkan.

## 3. Email dan support

Website menggunakan link email dan bukan contact form. Jika Anda mengirim email, informasi yang diproses dapat mencakup:

- Alamat email dan display name.
- Pesan, attachment, dan informasi teknis yang Anda pilih untuk diberikan.
- Order reference dan riwayat support jika relevan.

Informasi tersebut digunakan untuk menjawab pertanyaan mengenai instalasi, licensing, kompatibilitas, privasi, dan masalah teknis terkait produk. Email diproses oleh email provider yang digunakan pengirim dan penerima.

Jangan mengirim full licence key, asset produksi rahasia, password, atau informasi sensitif lain kecuali benar-benar diperlukan dan metode transfer yang sesuai telah disepakati.

## 4. Komentar

Komentar dimatikan pada halaman AD Skin Tools dan halaman kebijakan, tetapi Isso comment system tersedia pada beberapa halaman blog dan proyek.

Jika Anda mengirim komentar, Isso dapat memproses:

- Isi komentar, halaman terkait, dan timestamp.
- Nama, alamat email, atau website opsional yang Anda berikan.
- Status moderation dan informasi anti-abuse.
- Informasi teknis jaringan, termasuk alamat IP yang dianonimkan sebagian.

Isi komentar yang disetujui dan display name yang diberikan dapat ditampilkan secara publik. Alamat email digunakan untuk administrasi atau notifikasi dan tidak dengan sengaja ditampilkan secara publik.

Komentar disimpan dalam self-hosted Isso SQLite database. Traffic menuju layanan melewati Cloudflare dan notifikasi moderation dapat dikirim menggunakan Google SMTP. Jangan menuliskan informasi pribadi yang rahasia atau sensitif dalam komentar publik.

## 5. Pembelian melalui Lemon Squeezy

Ketika penjualan dibuka, Lemon Squeezy akan menyediakan checkout dan bertindak sebagai Merchant of Record. Lemon Squeezy dapat mengumpulkan serta memproses informasi yang diperlukan untuk pembayaran, pajak, fraud prevention, pengiriman digital, refund, dan chargeback, termasuk:

- Nama customer, email, negara penagihan, dan billing details.
- Informasi pembayaran dan transaction identifier.
- Informasi produk, order, pajak, refund, dan chargeback.
- Informasi perangkat, jaringan, fraud-prevention, dan penggunaan checkout.

Detail kartu pembayaran ditangani oleh Lemon Squeezy dan payment provider-nya, bukan oleh website ini atau AD Skin Tools licensing database. Pemrosesan oleh Lemon Squeezy diatur oleh <a href="https://www.lemonsqueezy.com/privacy" target="_blank" rel="noopener noreferrer" aria-label="Lemon Squeezy Privacy Policy, dibuka di tab baru">Privacy Policy</a> dan <a href="https://www.lemonsqueezy.com/buyer-terms" target="_blank" rel="noopener noreferrer" aria-label="Lemon Squeezy Buyer Terms, dibuka di tab baru">Buyer Terms</a> mereka.

AD Skin Tools licensing service dirancang agar tidak menyimpan nama atau alamat email customer yang diterima dari Lemon Squeezy webhook.

## 6. Trial dan paid licensing

AD Skin Tools berkomunikasi dengan licensing service yang di-host di Amazon Web Services ketika user memulai trial atau mengaktifkan, memvalidasi, maupun menonaktifkan lisensi berbayar.

Licensing service dapat memproses:

- Device fingerprint yang dibuat oleh tool yang terpasang.
- Digest pseudonim yang dibuat dari fingerprint tersebut.
- Licence key ketika melakukan aktivasi atau validasi.
- Hashed licence-key lookup value dan bukan raw key dalam persistent storage.
- Status trial, lisensi, aktivasi, device slot, entitlement, dan revocation.
- Server timestamp, tanggal validasi, tanggal kedaluwarsa, dan hasil request.
- Metadata jaringan dan security standar yang diproses oleh infrastruktur AWS.

Aplikasi dirancang agar raw device fingerprint dan raw licence key tidak ditulis ke licensing database maupun application logs. Identitas pseudonim tetap merupakan data yang berkaitan dengan sebuah perangkat dan diperlakukan sebagaimana mestinya.

Informasi licensing digunakan untuk menyediakan trial 48 jam, menerapkan batas dua perangkat, menerbitkan signed entitlement, mendukung penggunaan offline, memvalidasi lisensi, mencegah reset trial, dan mencabut lisensi setelah refund, reversal, atau event lain yang benar-benar membatalkan hak lisensi.

## 7. Informasi lokal di komputer customer

AD Skin Tools menyimpan entitlement dan licensing cache secara lokal di komputer customer. Informasi ini dapat berisi pseudonymous device binding, status lisensi atau trial, signed entitlement data, validation timestamp, dan informasi offline expiry.

Informasi lokal tersebut diperlukan untuk menjalankan trial dan paid offline grace period. Menghapus atau mengubahnya tidak menjamin trial baru dan dapat mengharuskan produk tersambung kembali ke licensing service.

## 8. Alasan informasi diproses

Informasi yang dijelaskan dalam kebijakan ini diproses untuk:

- Mengirimkan, mengamankan, dan melakukan troubleshooting website.
- Menampilkan konten serta mengingat preference penting website.
- Memublikasikan dan memoderasi komentar pada halaman yang mengaktifkannya.
- Menjawab pertanyaan support dan privasi.
- Memproses pembelian dan pengiriman digital.
- Memulai trial serta mengaktifkan, memvalidasi, menonaktifkan, atau mencabut lisensi.
- Mencegah fraud, abuse, license sharing, dan reset trial tanpa izin.
- Memenuhi kewajiban accounting, pajak, consumer protection, dispute, dan hukum.

## 9. Service provider dan pengungkapan

Informasi hanya dibagikan jika secara wajar diperlukan untuk menjalankan fungsi tersebut, menaati hukum, atau melindungi layanan. Provider terkait saat ini mencakup Cloudflare, jsDelivr, GitHub, email provider, Google SMTP untuk notifikasi komentar, Lemon Squeezy untuk commerce, dan Amazon Web Services untuk licensing.

Provider tersebut dapat memproses informasi di negara selain Australia berdasarkan privacy terms dan pengaturan infrastrukturnya masing-masing.

Adien Dendra tidak menjual informasi pribadi untuk tujuan advertising.

## 10. Retensi

Retensi bergantung pada jenis informasi serta kebutuhan operasional atau hukum:

- Website dan security logs mengikuti pengaturan serta praktik retensi hosting provider.
- Email support disimpan selama diperlukan untuk menyelesaikan permintaan, mempertahankan riwayat support, mencegah abuse, atau memenuhi kewajiban hukum.
- Komentar tetap disimpan selama diskusi terkait dipublikasikan atau hingga moderation maupun permintaan penghapusan yang sah mengharuskan penghapusan, dengan memperhatikan kebutuhan backup dan security.
- Transaction record disimpan oleh Lemon Squeezy dan provider terkait sesuai kebutuhan pembayaran, pajak, fraud, dispute, dan hukum.
- Licensing record dan pseudonymous device record dapat disimpan selama lifecycle trial atau lisensi dan selama diperlukan untuk menerapkan status perangkat, refund, fraud, dan revocation.

Informasi dapat disimpan lebih lama jika diwajibkan hukum, terdapat dispute aktif, atau diperlukan untuk fraud prevention maupun security investigation. Informasi akan dihapus atau dianonimkan ketika tidak lagi diperlukan secara wajar, dengan memperhatikan kebutuhan tersebut.

## 11. Security

Langkah teknis dan organisasi yang wajar digunakan untuk melindungi informasi, termasuk koneksi jaringan terenkripsi, pseudonymous device identifier, hashed licence-key lookup, pembatasan akses layanan, serta menghindari raw key dan raw fingerprint dalam application logs. Tidak ada metode transmisi atau penyimpanan yang dapat dijamin sepenuhnya aman.

## 12. Permintaan akses, koreksi, dan penghapusan

Anda dapat menghubungi [hello@adiendendra.com](mailto:hello@adiendendra.com) untuk meminta akses, koreksi, atau penghapusan informasi pribadi yang dikendalikan oleh Adien Dendra. Informasi yang cukup mungkin diperlukan untuk memverifikasi permintaan dan menemukan record terkait.

Sebagian informasi mungkin perlu dipertahankan untuk keperluan hukum, transaksi, fraud prevention, security, atau integritas lisensi. Permintaan mengenai checkout atau data pembayaran yang dikendalikan Lemon Squeezy juga perlu ditujukan kepada Lemon Squeezy.

## 13. Perubahan kebijakan

Kebijakan ini dapat diperbarui ketika website, video provider, commerce flow, licensing service, atau persyaratan hukum berubah. Tanggal berlaku akan diperbarui ketika perubahan material dipublikasikan.
