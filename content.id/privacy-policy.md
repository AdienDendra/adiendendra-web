+++
title = "Kebijakan Privasi"
translationKey = "privacy-policy"
description = "Cara website ini dan AD Skin Tools memproses data website, support, komentar, transaksi, licensing, dan perangkat lokal."
date = 2026-09-09T20:58:00+10:00
lastmod = 2026-09-11T20:58:00+10:00
comments = false
showToc = true
TocOpen = true
ShowReadingTime = false
ShowPostNavLinks = false
+++

**Tanggal berlaku: 11 September 2026**

Kebijakan Privasi ini menjelaskan bagaimana situs web `adiendendra.com` dan AD Skin Tools mengelola dan memproses informasi. Situs web beserta produk ini dioperasikan oleh Adien Dendra. Pertanyaan mengenai privasi dapat dikirimkan ke [hello@adiendendra.com](mailto:hello@adiendendra.com).

Kebijakan ini tidak menyatakan bahwa tidak ada data yang dikumpulkan sama sekali. Infrastruktur situs web, email, komentar, penyedia layanan pembayaran, dan sistem lisensi secara teknis tetap perlu memproses sejumlah informasi terbatas agar dapat beroperasi.

## 1. Kunjungan website dan hosting

Situs web ini merupakan situs statis berbasis Hugo yang di-host melalui Cloudflare Pages dan didistribusikan lewat jaringan Cloudflare. Cloudflare dapat memproses informasi keamanan dan permintaan teknis seperti:

- Alamat IP dan perkiraan lokasi jaringan.
- URL yang diakses, tanggal, serta waktu akses.
- Informasi browser, perangkat, sistem operasi, dan request header.
- Catatan cache, performa, error, pencegahan penyalahgunaan, serta peristiwa keamanan (security events).

Cloudflare dapat memasang cookie keamanan yang esensial jika diperlukan oleh fitur perlindungannya. Situs web ini tidak memasang penjejak iklan (advertising trackers) atau cookie iklan pihak ketiga.

Situs ini menggunakan `localStorage` pada browser untuk menyimpan preferensi tampilan mode terang atau gelap pengunjung. Fitur penyaring (filter) 3D Tools beroperasi secara lokal di dalam browser dan tidak mengirimkan pilihan penyaring tersebut ke server.

Silakan baca <a href="https://www.cloudflare.com/privacypolicy/" target="_blank" rel="noopener noreferrer" aria-label="Cloudflare Privacy Policy, dibuka di tab baru">Kebijakan Privasi Cloudflare</a> dan <a href="https://developers.cloudflare.com/fundamentals/reference/policies-compliances/cloudflare-cookies/" target="_blank" rel="noopener noreferrer" aria-label="dokumentasi Cloudflare Cookies, dibuka di tab baru">Dokumentasi Cookie Cloudflare</a> untuk informasi lebih lanjut mengenai pemrosesan data oleh Cloudflare.

## 2. Konten eksternal yang digunakan situs web

Situs web ini memuat sumber daya Mermaid dan KaTeX dari jaringan distribusi konten (Content Delivery Network / CDN) jsDelivr. Halaman utama juga memuat foto profil dari GitHub. Saat sumber daya ini dimuat, penyedia layanan terkait dapat menerima informasi permintaan standar seperti alamat IP pengunjung, browser header, sumber daya yang diminta, dan stempel waktu (timestamp).

## 3. Email dan dukungan teknis
Situs web ini menggunakan tautan email. Jika Anda mengirimkan email, informasi yang diproses dapat mencakup:

- Alamat email dan nama tampilan Anda.
- Pesan, lampiran, dan informasi teknis yang Anda pilih untuk berikan.
- Referensi pesanan dan riwayat dukungan teknis jika relevan.

Informasi ini digunakan untuk merespons pertanyaan seputar instalasi, lisensi, kompatibilitas, privasi, serta kendala teknis produk. Email diproses oleh penyedia layanan email yang digunakan oleh pengirim dan penerima.

Mohon untuk tidak mengirimkan kunci lisensi secara utuh, aset produksi yang bersifat rahasia, kata sandi, atau informasi sensitif lainnya kecuali jika memang diperlukan dan metode pengiriman yang aman telah disepakati.

## 4. Pembelian melalui Lemon Squeezy

Saat penjualan dibuka, Lemon Squeezy akan menyediakan alur checkout dan bertindak sebagai Merchant of Record. Lemon Squeezy dapat mengumpulkan dan memproses informasi yang diperlukan untuk pembayaran, pajak, pencegahan penipuan, pengiriman digital, pengembalian dana (refund), dan sanggahan pembayaran (chargeback), mencakup:

- Nama pelanggan, email, negara penagihan, dan rincian alamat tagihan.
- Informasi pembayaran dan pengenal (identifier) transaksi.
- Informasi produk, pesanan, pajak, pengembalian dana, dan sanggahan pembayaran.
- Informasi perangkat, jaringan, pencegahan penipuan, dan penggunaan alur checkout.

Rincian kartu pembayaran dikelola langsung oleh Lemon Squeezy beserta penyedia pembayaran rekannya, bukan oleh situs web ini atau basis data lisensi AD Skin Tools. Pemrosesan oleh Lemon Squeezy diatur dalam <a href="https://www.lemonsqueezy.com/privacy" target="_blank" rel="noopener noreferrer" aria-label="Lemon Squeezy Privacy Policy, dibuka di tab baru">Kebijakan Privasi</a> dan <a href="https://www.lemonsqueezy.com/buyer-terms" target="_blank" rel="noopener noreferrer" aria-label="Lemon Squeezy Buyer Terms, dibuka di tab baru">Syarat Pembeli</a> milik mereka.

Layanan lisensi AD Skin Tools dirancang untuk tidak menyimpan nama atau alamat email pelanggan yang diterima dari webhook Lemon Squeezy.

## 5. Uji coba dan lisensi berbayar

AD Skin Tools berkomunikasi dengan layanan lisensi yang di-host di AWS (Amazon Web Services) saat pengguna memulai masa uji coba, atau melakukan aktivasi, validasi, maupun deaktivasi lisensi berbayar.

Layanan lisensi dapat memproses:

- Sidik jari perangkat (device fingerprint) yang dihasilkan oleh tool yang terpasang.
- Digest pseudonim (pseudonymous digest) yang diturunkan dari fingerprint tersebut.
- Kunci lisensi (licence key) saat proses aktivasi atau validasi.
- Nilai pencarian kunci lisensi yang di-hash (hashed lookup value), alih-alih menyimpan kunci mentah pada penyimpanan permanen.
- Status masa uji coba, lisensi, aktivasi, slot perangkat, hak akses (entitlement), dan pencabutan lisensi (revocation).
- Stempel waktu server, tanggal validasi, tanggal kadaluarsa, dan hasil permintaan.
- Metadata jaringan dan keamanan standar yang diproses oleh infrastruktur AWS.

Aplikasi dirancang sedemikian rupa agar device fingerprint dan kunci lisensi mentah tidak pernah ditulis ke basis data lisensi maupun log aplikasi. Meski demikian, pengenal pseudonim (pseudonymous identifiers) tetap dianggap sebagai data yang berkaitan dengan perangkat dan dikelola secara aman.

Informasi lisensi digunakan untuk menyediakan masa uji coba 48 jam, menerapkan batas dua perangkat, menerbitkan hak akses yang tertanda secara digital (signed entitlements), mendukung penggunaan offline, memvalidasi lisensi, mencegah penyalahgunaan ulang masa uji coba, serta mencabut lisensi apabila terjadi pengembalian dana, pembalikan transaksi, atau pembatalan pesanan yang sah.

## 6. Informasi lokal di komputer pelanggan

AD Skin Tools menyimpan data hak akses lokal (local entitlement) dan cache lisensi di komputer pelanggan. Data ini dapat berisi informasi penambatan perangkat pseudonim (pseudonymous device binding), status lisensi atau uji coba, data hak akses tertandatangani, stempel waktu validasi, serta informasi batas waktu penggunaan offline.

Informasi lokal ini diperlukan untuk menjalankan masa uji coba dan masa tenggang offline (offline grace period) pada lisensi berbayar. Menghapus atau mengubah data ini tidak menjamin dimulainya masa uji coba baru dan mungkin mengharuskan produk terhubung kembali ke layanan lisensi.

## 7. Alasan pemrosesan informasi

Informasi yang dijelaskan dalam kebijakan ini diproses untuk:

- Menyediakan, mengamankan, dan mengatasi masalah teknis pada situs web.
- Menampilkan konten situs dan menyimpan preferensi esensial.
- Merespons permintaan dukungan teknis dan pertanyaan privasi.
- Memproses transaksi pembelian dan pengiriman produk digital.
- Memulai masa uji coba serta mengaktifkan, memvalidasi, menonaktifkan, atau mencabut lisensi.
- Mencegah penipuan, penyalahgunaan, pembagian lisensi, dan peretasan masa uji coba secara tidak sah.
- Memenuhi kewajiban akuntansi, perpajakan, perlindungan konsumen, penanganan sengketa, dan ketentuan hukum.

## 8. Penyedia layanan dan pengungkapan data

Informasi hanya diungkapkan jika secara wajar diperlukan untuk menjalankan fungsi-fungsi tersebut, mematuhi hukum, atau melindungi layanan. Penyedia layanan terkait saat ini meliputi Cloudflare, jsDelivr, GitHub, penyedia email, Google SMTP untuk notifikasi komentar, Lemon Squeezy untuk transaksi, dan AWS (Amazon Web Services) untuk sistem lisensi.

Informasi pribadi tidak pernah dijual oleh Adien Dendra untuk keperluan periklanan.

## 9. Retensi data

Jangka waktu penyimpanan (retensi) data bergantung pada jenis informasi serta kebutuhan operasional atau hukum:

- Log keamanan dan situs web mengikuti pengaturan serta praktik retensi dari penyedia hosting.
- Email dukungan teknis disimpan selama diperlukan untuk menyelesaikan kendala, mencatat riwayat bantuan, mencegah penyalahgunaan, atau memenuhi kewajiban hukum.
- Catatan transaksi disimpan oleh Lemon Squeezy dan penyedia terkait sesuai dengan persyaratan pembayaran, pajak, pencegahan penipuan, penanganan sengketa, dan hukum.
- Catatan lisensi dan perangkat pseudonim dapat disimpan selama masa aktif uji coba atau lisensi, serta selama diperlukan untuk menerapkan aturan batas perangkat, pengembalian dana, pencegahan penipuan, dan status pencabutan lisensi.

Informasi dapat disimpan lebih lama apabila diwajibkan oleh hukum, sengketa yang sedang berjalan, pencegahan penipuan, atau penyelidikan keamanan. Data akan dihapus atau dianonimkan jika tidak lagi dibutuhkan secara wajar.

## 10. Keamanan

Langkah-langkah teknis dan organisasional yang wajar diterapkan untuk melindungi informasi, mencakup enkripsi koneksi jaringan, pengenal perangkat pseudonim, pencarian kunci lisensi terenkripsi (hashed lookup), pembatasan akses layanan, serta penghindaran kunci mentah dan sidik jari mentah pada log aplikasi. Meski demikian, tidak ada metode transmisi atau penyimpanan data yang dapat dijamin aman secara mutlak.

## 11. Permintaan akses, koreksi, dan penghapusan data

Anda dapat menghubungi [hello@adiendendra.com](mailto:hello@adiendendra.com) untuk mengajukan permintaan akses, koreksi, atau penghapusan informasi pribadi yang dikelola oleh Adien Dendra. Informasi verifikasi secukupnya mungkin diperlukan untuk mengonfirmasi identitas Anda dan menemukan catatan data yang relevan.

Sebagian informasi mungkin perlu tetap disimpan untuk alasan hukum, catatan transaksi, pencegahan penipuan, keamanan, atau integritas lisensi. Permintaan terkait data checkout atau pembayaran yang dikelola oleh Lemon Squeezy juga perlu ditujukan secara langsung kepada Lemon Squeezy.

## 12. Perubahan kebijakan

Kebijakan ini dapat diperbarui sewaktu-waktu apabila terdapat perubahan pada situs web, penyedia video, alur transaksi, layanan lisensi, atau ketentuan hukum. Tanggal berlaku akan diperbarui setiap kali ada perubahan substansial yang diterbitkan.