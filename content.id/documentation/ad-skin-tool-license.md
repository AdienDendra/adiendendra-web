---
title: "Panduan Lisensi AD Skin Tool"
translationKey: "ad-skin-tool-license"
summary: "Memulai trial, membeli dan mengaktifkan lisensi, mengelola perangkat, serta memahami validasi online dan akses offline."
description: "Panduan jendela License AD Skin Tool, meliputi trial 48 jam, checkout, aktivasi lisensi, deaktivasi perangkat, validasi otomatis, dan akses offline."
date: 2026-10-06T22:23:00+11:00
lastmod: 2026-11-22T18:40:45+11:00
tags: ["maya", "ad-skin-tool", "lisensi", "dokumentasi", "tutorial"]
categories: ["documentation"]
comments: true
showToc: true
TocOpen: true
ShowReadingTime: false
ShowPostNavLinks: false
---

Panduan ini membahas jendela **License** AD Skin Tool, mulai dari memulai trial dan pembelian lisensi hingga aktivasi, pengelolaan perangkat, serta penggunaan offline.

Panduan instalasi dan workflow tersedia di [Dokumentasi & Tutorial AD Skin Tool](/id/documentation/ad-skin-tool-tutorial/). Informasi harga, kompatibilitas, dan download tersedia di [halaman produk AD Skin Tool](/id/3dtools/ad-skin-tool/).

## Membuka jendela License

Buka AD Skin Tool di Maya, lalu klik **License** di pojok kanan atas. Jendela ini menampilkan status lisensi komputer yang digunakan serta tindakan yang tersedia sesuai status tersebut.

Membuka Maya, AD Skin Tool, atau jendela **License**, maupun mencoba fitur berlisensi, **tidak** otomatis memulai trial. Periode 48 jam baru dimulai setelah tombol **Start 48-Hour Trial** diklik.

<!-- Saran GIF: open-license-window.gif -->

## Memulai trial 48 jam

Trial AD Skin Tool memberikan akses penuh ke seluruh fitur selama 48 jam. Untuk memulainya:

1. Pastikan komputer terhubung ke internet.
2. Buka jendela **License**.
3. Klik **Start 48-Hour Trial**.
4. Tunggu sampai status berubah menjadi **Trial active**.

Periode 48 jam dihitung berdasarkan waktu server dan terus berjalan meskipun Maya ditutup atau komputer dimatikan. Reset data lisensi lokal tidak akan memulai ulang atau memperpanjang trial. Waktu berakhirnya trial ditampilkan di jendela **License** sesuai waktu lokal komputer.

Setelah trial berakhir, status berubah menjadi **Trial ended** dan sebagian besar fitur tidak lagi dapat digunakan.

<!-- Saran GIF: start-trial.gif -->

## Membeli lisensi setelah trial

Klik **Buy License** untuk membuka halaman checkout AD Skin Tool melalui browser. Freemius memproses pembayaran sebagai *Merchant of Record*.

Jika kode promo peluncuran tersedia di jendela **License**, klik **Have a promotional code?** pada halaman checkout dan masukkan kodenya. Pastikan potongan harga tercantum dalam total pembayaran, lalu periksa harga akhir, pajak yang berlaku, dan ketentuan checkout sebelum menyelesaikan pembelian.

<!-- Saran GIF: buy-license-checkout.gif -->

## Menerima dan menjaga license key

Setelah pesanan selesai, Freemius mengirim email berisi license key AD Skin Tool ke alamat yang dimasukkan saat checkout. Simpan email konfirmasi, license key, dan invoice sebagai arsip.

Jika email belum diterima setelah beberapa menit:

1. Periksa folder Spam, Junk, dan Promotions.
2. Cari email dengan kata **AD Skin Tool** atau **Freemius**.
3. Periksa kotak masuk dari alamat email yang digunakan saat checkout.
4. Jika email tetap tidak ditemukan, hubungi [hello@adiendendra.com](mailto:hello@adiendendra.com) dengan menyertakan alamat email pembelian dan deskripsi singkat masalahnya.

Jaga kerahasiaan license key. Hindari memublikasikannya, menampilkannya dalam rekaman tutorial, atau menyertakan key lengkap pada screenshot.

## Mengaktifkan lisensi berbayar

Aktivasi lisensi memerlukan koneksi internet. Setelah komputer terhubung:

1. Kembali ke Maya dan buka jendela **License**.
2. Salin license key lengkap dari email pembelian Freemius atau akun pelanggan.
3. Tempelkan key ke kolom **License Key**.
4. Klik **Activate License**.
5. Tunggu sampai status berubah menjadi **License active**.

Aktivasi yang berhasil menampilkan:

> **License active**  
> This device is licensed and ready to use.  
> Next auto-validation: *tanggal dan waktu*.  
> Offline access available until: *tanggal dan waktu*.

Setiap lisensi Individual dapat aktif pada maksimal **dua perangkat pribadi**. Jika kedua slot sudah terpakai, lakukan deaktivasi pada perangkat yang tidak lagi digunakan sebelum mengaktifkan perangkat lain.

<!-- Saran GIF: activate-license.gif -->

## Memahami validasi otomatis dan akses offline

Lisensi AD Skin Tool bersifat perpetual. Dua tanggal pada jendela **License** menunjukkan jadwal validasi online dan batas akses offline, **bukan tanggal kedaluwarsa lisensi yang dibeli**.

| Teks pada jendela License | Artinya |
|---|---|
| **Next auto-validation** | Jadwal pemeriksaan lisensi online berikutnya, biasanya tujuh hari setelah aktivasi atau validasi terakhir yang berhasil. |
| **Offline access available until** | Batas masa akses offline yang tersimpan tanpa koneksi ke server, biasanya 30 hari setelah aktivasi atau validasi terakhir yang berhasil. |

Setelah jadwal **Next auto-validation** tercapai, AD Skin Tool otomatis memeriksa status lisensi saat tool dibuka atau fitur berlisensi digunakan. Proses ini tidak memerlukan tindakan manual.

Jika komputer sementara tidak terhubung ke internet, status dapat berubah menjadi **Working offline**. Fitur berlisensi tetap tersedia hingga batas akses offline yang ditampilkan. AD Skin Tool mencoba validasi lagi saat dibuka berikutnya. Setelah koneksi pulih, klik **Retry Now** untuk melakukan pemeriksaan langsung.

Setiap validasi online yang berhasil memperbarui kedua tanggal berdasarkan waktu pemeriksaan terakhir. Jika komputer tetap offline melewati batas akses tersebut, fitur berlisensi akan diblokir dan jendela **License** menampilkan:

> **Online check required**  
> Offline access has ended.  
> Connect to the internet and click Retry Now to validate your license.

Untuk memulihkan akses, sambungkan kembali komputer ke internet, klik **Retry Now**, lalu tunggu hingga status kembali menjadi **License active**.

## Deactivate This Device

Gunakan **Deactivate This Device** untuk melepas slot aktivasi yang terhubung ke komputer saat ini. Langkah ini berguna sebelum komputer dijual, diformat ulang, sistem operasinya diinstal ulang, atau lisensi dipindahkan ke perangkat pribadi lain.

1. Pastikan komputer yang memiliki aktivasi aktif terhubung ke internet.
2. Buka jendela **License**.
3. Klik **Deactivate This Device**.
4. Periksa dialog konfirmasi, kemudian klik **Deactivate**.

Deaktivasi yang berhasil membebaskan satu dari dua slot perangkat dan menghapus data lisensi berbayar yang disimpan secara lokal oleh AD Skin Tool. Komputer yang sama dapat diaktifkan kembali menggunakan license key yang sama.

Deaktivasi **tidak** membatalkan pembelian, mencabut lisensi, menonaktifkan komputer lain, atau menghapus pesanan. Jika server tidak dapat dihubungi, data lisensi lokal tetap disimpan agar proses deaktivasi dapat dicoba lagi dengan aman.

Jika komputer lama hilang atau tidak lagi dapat diakses, hubungi [hello@adiendendra.com](mailto:hello@adiendendra.com) untuk mendapatkan bantuan. Jangan membagikan license key.

<!-- Saran GIF: deactivate-this-device.gif -->

## Kontrol lain pada jendela License

| Kontrol | Kegunaan |
|---|---|
| **Retry Now** | Mengulangi permintaan trial atau lisensi berbayar yang tersimpan jika status saat ini memungkinkan. Gunakan setelah koneksi internet pulih atau masalah pada komputer teratasi. |
| **Reset Local License Data** | Hanya ditampilkan ketika data lisensi lokal memerlukan perbaikan. Menghapus data lisensi pada komputer tanpa membebaskan slot perangkat di server atau memulai ulang maupun memperpanjang trial. Gunakan hanya jika diminta oleh jendela **License**. |
| **Buy License** | Membuka halaman checkout resmi melalui browser default. |
| **Update** atau **Upgrade** | Hanya muncul jika tersedia versi terbaru yang kompatibel. Membuka halaman resmi AD Skin Tool tanpa menginstal software di latar belakang atau mengubah lisensi saat ini. |

## Status yang umum ditampilkan

| Status | Arti dan tindakan yang diperlukan |
|---|---|
| **Trial available** | Trial belum dimulai. Hubungkan komputer ke internet, lalu klik **Start 48-Hour Trial** saat siap memulai. |
| **Trial active** | Seluruh fitur berlisensi dapat digunakan hingga waktu berakhirnya trial yang ditampilkan. |
| **Trial ended** | Aktifkan lisensi berbayar untuk kembali menggunakan fitur berlisensi. |
| **License active** | Lisensi aktif pada komputer ini dan seluruh fitur berlisensi siap digunakan. |
| **Checking license** | Pemeriksaan online otomatis sedang berlangsung. Fitur berlisensi tetap tersedia selama proses validasi. |
| **Working offline** | Pemeriksaan online tidak dapat diselesaikan, tetapi akses offline yang tersimpan masih berlaku. Sambungkan kembali komputer ke internet sebelum batas akses offline. |
| **Online check required** | Akses offline telah berakhir. Hubungkan komputer ke internet, lalu klik **Retry Now**. |
| **License not found** | Pastikan license key sudah disalin lengkap dari email pembelian, lalu coba lagi. |
| **Device inactive** | Perangkat ini tidak lagi aktif. Masukkan license key dan lakukan aktivasi kembali jika slot perangkat masih tersedia. |
| **License inactive** | Lisensi tidak lagi aktif. Gunakan lisensi valid lain atau hubungi support. |
| **Temporarily unavailable** | Layanan tidak dapat dihubungi. Periksa koneksi internet dan coba lagi nanti. |
| **Computer clock needs attention** | Perbaiki tanggal, waktu, dan zona waktu komputer, lalu ulangi validasi online. |
| **Local license data needs repair** | Gunakan **Reset Local License Data** jika tersedia, lalu mulai trial jika masih memungkinkan atau aktifkan lisensi. |
| **License checking unavailable** | Instal ulang paket resmi AD Skin Tool. Jika pesan tetap muncul, hubungi support. |

Jika batas perangkat tercapai saat aktivasi, nonaktifkan AD Skin Tool pada perangkat yang tidak lagi digunakan. Hubungi support jika perangkat tersebut sudah tidak dapat diakses.

## Bantuan lisensi

Untuk bantuan terkait lisensi, kirim email ke [hello@adiendendra.com](mailto:hello@adiendendra.com) dengan informasi berikut:

- Sistem operasi dan versi Maya. Klik **Tool Help**, lalu **Copy Diagnostics** untuk menyalin detailnya.
- Judul status dan pesan lengkap yang ditampilkan pada jendela **License**.
- Deskripsi singkat mengenai tindakan yang sedang dilakukan saat masalah terjadi.
- Alamat email pembelian jika diperlukan untuk menemukan pesanan.

Jangan pernah mengirim license key, detail kartu pembayaran, kata sandi, atau file AD Skin Tool.
