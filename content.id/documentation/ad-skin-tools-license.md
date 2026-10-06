---
title: "Panduan Lisensi AD Skin Tool"
translationKey: "ad-skin-tools-license"
summary: "Memulai trial, membeli dan mengaktifkan lisensi, mengelola perangkat, serta memahami validasi online dan akses offline."
description: "Panduan customer untuk License AD Skin Tool, termasuk trial 48 jam, checkout, aktivasi, deaktivasi perangkat, validasi otomatis, dan akses offline."
date: 2026-10-06T22:23:00+11:00
lastmod: 2026-10-06T22:23:00+11:00
tags: ["maya", "ad-skin-tools", "lisensi", "dokumentasi", "tutorial"]
categories: ["documentation"]
comments: true
showToc: true
TocOpen: true
ShowReadingTime: false
ShowPostNavLinks: false
---

Panduan ini menjelaskan tentang **License**, mulai dari cara mengaktifasi trial, membeli AD Skin Tool, mengaktifkan license key, memindahkan activation antar device, dan menggunakan tool secara offline.

Untuk instalasi dan workflow tool, dapat dibaca di [Dokumentasi & Tutorial AD Skin Tool](/id/documentation/ad-skin-tools/). Untuk harga, kompatibilitas, dan download, dapat ke [halaman produk AD Skin Tool](/id/3dtools/ad-skin-tools/).

## Membuka window License

Buka AD Skin Tool di Maya, kemudian klik tombol **License** di pojok kanan atas. License akan menampilkan status lisensi untuk komputer yang sedang digunakan dan action yang tersedia untuk status tersebut.

Membuka Maya, AD Skin Tool, jendela License, atau protected action **tidak** akan memulai trial. Trial akan dimulai ketika Anda menekan **Start 48-Hour Trial**.

<!-- Saran GIF: open-license-window.gif -->

## Memulai trial 48 jam

Trial AD Skin Tool hanya belaku selama 48 jam, akses ini terbuka ke seluruh fitur. Cara mengaktifkan trial:

1. Komputer terhubung ke internet.
2. Buka jendela **License**.
3. Klik **Start 48-Hour Trial**.
4. Tunggu sampai status berubah menjadi **Trial active**.

Periode 48 jam dihitung menggunakan waktu server. Waktunya tetap berjalan ketika Maya atau komputer ditutup, dan reset data lisensi lokal tidak akan memulai ulang atau memperpanjang trial. Pada jendela License akan menampilkan waktu berakhirnya trial sesuai waktu lokal komputer yang Anda gunakan.

Setelah periodenya selesai, status berubah menjadi **Trial ended** dan sebagian besar fitur pada tool tidak dapat digunakan.

<!-- Saran GIF: start-trial.gif -->

## Membeli lisensi setelah trial

Klik tombol **Buy License** untuk membuka checkout AD Skin Tool untuk terhubung ke web browser. Checkout tersebut disediakan oleh Lemon Squeezy sebagai penyedia pembayaran dan *Merchant of Record*.

Sebelum membayar, pastikan checkout menampilkan **AD Skin Tool**, kemudian periksa harga, mata uang, pajak, dan total akhir. Field yang tersedia dapat sedikit berbeda berdasarkan metode pembayaran dan negara billing.

| Bagian checkout | Data yang diisi |
|---|---|
| Email | Gunakan alamat yang dapat Anda akses. Konfirmasi order dan license key akan dikirim ke alamat ini. |
| Metode pembayaran | Pilih salah satu metode yang ditawarkan di checkout, seperti kartu debit/kredit atau PayPal. |
| Detail kartu | Untuk pembayaran dengan kartu debit/kredit, masukkan nomor kartu, tanggal kedaluwarsa, dan security code. |
| Nama dan alamat billing | Masukkan nama cardholder, negara, alamat billing, kota, state atau region jika diminta, dan kode pos. |
| Tax ID number | Opsional. Isi hanya jika berlaku untuk pembelian Anda. |
| Discount code | Opsional. Masukkan kode yang masih valid, lalu periksa kembali total akhir. |

Pada form pembayaran mungkin ada opsi penyimpanan informasi pembayaran untuk checkout yang lebih cepat. Pilihan ini bersifat opsional dan tidak diperlukan untuk menerima atau menggunakan lisensi AD Skin Tool.

Setelah tertera harga total, selesaikan pembayaran melalui tombol yang menampilkan **Pay** dan jumlah pembayaran. Jangan tutup halaman checkout sebelum ada konfirmasi bahwa order telah selesai.

<!-- Saran GIF: buy-license-checkout.gif -->

## Menerima dan menjaga license key

Setelah order berhasil, Lemon Squeezy akan mengirim email ke alamat yang digunakan saat checkout. Email tersebut berisi license key yang diperlukan oleh AD Skin Tool.

Jika email belum diterima setelah beberapa menit:

1. Periksa folder Spam, Junk, dan Promotions.
2. Cari email dengan kata **AD Skin Tool** atau **Lemon Squeezy**.
3. Pastikan Anda memeriksa alamat yang sama dengan yang digunakan saat checkout.
4. Jika masih belum ada, hubungi [hello@adiendendra.com](mailto:hello@adiendendra.com) dengan menyertakan email order dan deskripsi singkat masalahnya.

Jaga kerahasiaan license key. Jangan memublikasikannya, menampilkannya dalam rekaman tutorial, atau mengirimkan key lengkap di screenshot.

## Mengaktifkan lisensi berbayar

Untuk mengaktifasi tool dibutuhkan koneksi internet. Setelah dipastikan terhubung dengan internet:

1. Kembali ke Maya dan buka jendela **License**.
2. Salin license key lengkap dari email Lemon Squeezy.
3. Masukan **License Key** ke text box.
4. Klik **Activate License**.
5. Tunggu sampai status berubah menjadi **License active**.

Aktivasi yang berhasil menampilkan:

> **License active**  
> This device is licensed and ready to use.  
> Next auto-validation: *tanggal dan waktu*.  
> Offline access available until: *tanggal dan waktu*.

Setiap lisensi Individual dapat aktif pada maksimal **dua perangkat pribadi**. Jika kedua slot sudah digunakan, deactivate salah satu perangkat yang tidak lagi diperlukan sebelum mengaktifkan perangkat lain.

<!-- Saran GIF: activate-license.gif -->

## Memahami validasi otomatis dan akses offline

AD Skin Tool adalah tool yang bersifat perpetual, dua tanggal pada jendela License merupakan periode validasi, **bukan tanggal berakhirnya lisensi yang telah dibeli**.

| Teks pada jendela License | Artinya |
|---|---|
| **Next auto-validation** | Tanggal berikutnya saat tool perlu memperbarui status lisensinya secara online. Normalnya tujuh hari setelah aktivasi atau validasi terakhir yang berhasil. |
| **Offline access available until** | Tanggal terakhir ketika akses offline terverifikasi yang tersimpan masih dapat digunakan tanpa koneksi internet ker server. Normalnya 30 hari setelah aktivasi atau validasi terakhir yang berhasil. |

Setelah waktu **Next auto-validation** tercapai, tool mencoba melakukan validasi secara otomatis ketika AD Skin Tool dibuka atau ketika fitur digunakan. Anda tidak perlu menekan tombol apa pun, license otomatis akan memverifikasi ke server.

Jika komputer sementara tidak terhubung ke internet, status dapat menampilkan **Working offline**. Fitur pada tool akan tetap tersedia sampai tanggal offline access yang ada pada tampilan. Tool akan mencoba kembali pada pembukaan tool berikutnya, dan **Retry Now** dapat digunakan untuk langsung memeriksa kembali setelah koneksi internet terhubung.

Setiap validasi online yang berhasil akan memajukan kedua tanggal tersebut dari waktu pemeriksaan yang berhasil. Jika komputer tetap offline sampai tanggal offline access terlewati, fitur tool akan terblokir dan akan ada tampilan:

> **Online check required**  
> Offline access has ended.  
> Connect to the internet and click Retry Now to validate your license.

Untuk menaktifkannya kembali, hubungkan kembali komputer ke internet, klik **Retry Now**, lalu tunggu sampai status **License active** muncul kembali.

## Deactivate This Device

Gunakan **Deactivate This Device** untuk melepas slot aktivasi komputer yang Anda gunakan, misalnya jika ada case untuk menjual, memformat atau menginstall ulang komputer, atau ketika Anda memindahkan lisensi ke perangkat pribadi lainnya.

1. Hubungkan komputer yang sedang aktif ke internet.
2. Buka jendela **License**.
3. Klik **Deactivate This Device**.
4. Periksa dialog konfirmasi, kemudian klik **Deactivate**.

Deactivation yang berhasil akan melepas satu dari dua slot perangkat dan menghapus data lisensi berbayar yang disimpan AD Skin Tool pada komputer tersebut. Komputer yang sama dapat diaktifkan kembali menggunakan license key yang sama.

Deactivation **tidak** membatalkan pembelian, mencabut lisensi, menonaktifkan komputer lain, atau menghapus order customer. Jika proses deactivation tidak dapat terhubung ke server, lisensi lokal akan tetap disimpan agar prosesnya dapat dicoba kembali dengan aman.

Jika komputer lama hilang atau sudah tidak dapat diakses, hubungi [hello@adiendendra.com](mailto:hello@adiendendra.com) untuk bantuan dan jangan membagikan license key.

<!-- Saran GIF: deactivate-this-device.gif -->

## Control lain pada jendela License

| Control | Kegunaan |
|---|---|
| **Retry Now** | Langsung mencoba kembali request trial atau lisensi berbayar yang tersimpan ketika status saat ini membolehkannya. Terutama digunakan setelah koneksi internet pulih atau waktu komputer sudah diperbaiki. |
| **Reset Local License Data** | Action pemulihan hanya ditampilkan ketika data lisensi lokal perlu diperbaiki. Action ini menghapus data lisensi di komputer tersebut, tetapi tidak melepas slot perangkat di server dan tidak memulai ulang atau memperpanjang trial. Gunakan hanya ketika License menginstruksikannya. |
| **Buy License** | Membuka checkout resmi di default web browser. |
| **Update** atau **Upgrade** | Hanya muncul ketika rilis baru yang sesuai tersedia. Tombol ini membuka halaman resmi AD Skin Tool, AD Skin Tool tidak menginstal software secara diam-diam atau mengubah lisensi saat ini. |

## Status yang umum ditampilkan

| Status | Arti dan tindakan yang diperlukan |
|---|---|
| **Trial available** | Trial belum dimulai. Hubungkan komputer ke internet dan klik **Start 48-Hour Trial** ketika Anda siap. |
| **Trial active** | Seluruh fitur terproteksi tersedia sampai waktu berakhirnya trial yang ditampilkan. |
| **Trial ended** | Aktifkan lisensi berbayar untuk kembali menggunakan fitur yang terproteksi. |
| **License active** | Komputer ini sudah aktif dan fitur aktif secara penuh. |
| **Checking license** | Pemeriksaan online otomatis sedang berjalan. Fitur tetap tersedia selama pemeriksaan. |
| **Working offline** | Pemeriksaan online tidak dapat diselesaikan, tetapi periode offline yang tersimpan masih valid. Pulihkan koneksi sebelum tanggal offline access. |
| **Online check required** | Akses offline sudah berakhir. Hubungkan komputer ke internet dan klik **Retry Now**. |
| **License not found** | Pastikan key lengkap disalin dari email pembelian yang benar, kemudian coba lagi. |
| **Device inactive** | Perangkat ini sudah tidak aktif. Masukkan key dan aktifkan kembali jika slot perangkat masih tersedia. |
| **License inactive** | Lisensi sudah tidak aktif. Gunakan lisensi valid lain atau hubungi support. |
| **Temporarily unavailable** | Service tidak dapat dihubungi. Periksa koneksi internet dan coba kembali nanti. |
| **Computer clock needs attention** | Perbaiki tanggal, waktu, dan time zone komputer, lalu coba validasi online kembali. |
| **Local license data needs repair** | Gunakan **Reset Local License Data** ketika ditawarkan, lalu mulai trial atau lakukan aktivasi kembali. |
| **License checking unavailable** | Instal ulang package resmi AD Skin Tool. Jika pesan tetap muncul, hubungi support. |

Jika aktivasi melaporkan bahwa batas perangkat sudah tercapai, deactivate AD Skin Tool pada salah satu perangkat yang tidak lagi digunakan. Jika perangkat tersebut tidak dapat diakses, hubungi support.

## Bantuan lisensi

Untuk bantuan lisensi, kirim email ke [hello@adiendendra.com](mailto:hello@adiendendra.com) dengan menyertakan:

- Sistem operasi dan versi Maya, dapat dilihat secara lengkap melalui tombol Tool Help, kemudian Copy Diagnostics.
- Judul status dan pesan lengkap yang terlihat pada jendela License.
- Deskripsi singkat mengenai tindakan yang dilakukan saat masalah terjadi.
- Alamat email pembelian jika diperlukan untuk mencari order.

Jangan pernah mengirim license key, detail kartu pembayaran, password, atau file AD Skin Tool.
