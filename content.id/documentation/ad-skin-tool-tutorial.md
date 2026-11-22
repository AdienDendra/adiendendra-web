---
title: "Dokumentasi & Tutorial AD Skin Tool"
translationKey: "ad-skin-tool-tutorial"
summary: "Panduan penggunaan AD Skin Tool untuk rigging dan skin weighting di Autodesk Maya."
description: "Pelajari cara load mesh, mengelola influence, bind, flood, smooth, mirror, dan transfer skin weights dengan AD Skin Tool."
date: 2026-09-11T10:00:00+10:00
lastmod: 2026-10-06T22:23:00+11:00
tags: ["maya", "ad-skin-tool", "dokumentasi", "tutorial"]
categories: ["documentation"]
comments: true
showToc: true
TocOpen: true
ShowReadingTime: false
ShowPostNavLinks: false
---

Panduan ini membahas alur kerja AD Skin Tool, mulai dari load mesh dan mengelola influence hingga mirror dan transfer skin weights. Kita akan melihat fungsi setiap kontrol serta kapan fitur tersebut digunakan di Maya.

Informasi harga, kompatibilitas, dan download tersedia di [halaman produk AD Skin Tool](/id/3dtools/ad-skin-tool/).

## Instalasi dan menjalankan tool

Download ZIP yang sesuai dengan versi Maya, sistem operasi, dan arsitektur prosesor yang kamu gunakan. Ikuti petunjuk instalasi di dalam ZIP karena setiap build dibuat untuk kombinasi versi Maya dan platform tertentu.

Untuk ZIP v1.0.0, buka tab Python di **Script Editor** Maya, lalu jalankan perintah pada langkah 5 di `README.txt` yang disertakan. Jika paket berisi folder `ad_skin_tool`, gunakan:

```python
from ad_skin_tool import launch

launch.show(
    reload=False,
    auto_refresh=False,
)
```

AD Skin Tool akan terbuka sebagai panel Maya yang bisa di-dock atau dibiarkan floating. **Tool Help** berisi referensi singkat dan informasi diagnostik. Lewat **License**, kamu bisa memulai trial, mengaktifkan lisensi, dan mengelola perangkat. Detailnya ada di [Panduan Lisensi AD Skin Tool](/id/documentation/ad-skin-tool-license/).

## Alur kerja singkat

1. Pilih polygon mesh atau salah satu component-nya, lalu klik **Load Mesh**.
2. Tambahkan atau pilih joint yang diperlukan pada **Joints / Influences**.
3. Atur **Blend** dan **Iterations** sesuai operasi yang ingin dijalankan.
4. Jalankan **Bind Skin**, **Add Influence**, **Flood**, atau **Smooth** pada mesh yang aktif.
5. Gunakan panel **Mirror** atau **Transfer** jika ingin menyalin weights antar-sisi atau antar-mesh.
6. Periksa status setelah setiap operasi. Untuk detailnya, lihat output di Maya Script Editor.

> Selection di Maya memengaruhi hasil setiap operasi. Sebelum menjalankan perintah, periksa apakah kamu sedang memilih mesh aktif, component, joint, atau tidak memilih apa pun.

## Mesh / Skin Context

### Load Mesh

Pilih polygon mesh atau salah satu vertex, edge, maupun face-nya, lalu klik **Load Mesh**. Mesh tersebut akan tetap aktif di AD Skin Tool meskipun kamu memilih object lain di Maya. Untuk pindah ke mesh lain, cukup pilih mesh baru dan klik **Load Mesh** lagi.

Panel ini menampilkan:

- **Skin Cluster:** skinCluster pada mesh aktif, atau `<no skinCluster>` jika mesh belum memiliki skinCluster.
- **Loaded Mesh:** nama transform yang digunakan oleh Bind, Add Influence, Flood, Smooth, dan Skin Weight Visual.
- **Listed Joints:** jumlah bound influence dan pending joint yang tampil di daftar.

Saat kamu load mesh yang sudah memiliki skinCluster, daftar joint otomatis menampilkan influence yang ada. Jika mesh belum di-bind, daftarnya dimulai dari kosong sehingga kamu bisa menambahkan joint terlebih dahulu.

{{< collapse title="Load Mesh demonstration" collapse="true">}}
![Load Mesh demonstration](/images/documentation/ad-skin-tool/01-load-mesh.gif)
{{< /collapse >}}

## Joints / Influences

### Bound influence dan pending joint

Ada dua jenis joint yang bisa muncul dalam daftar:

- **Bound influence** sudah menjadi bagian dari skinCluster pada mesh aktif dan ditampilkan dengan warna hijau.
- **Pending joint** sudah ada di scene dan masuk ke daftar, tetapi belum ditambahkan ke skinCluster. Joint ini ditampilkan dengan warna putih.

Pilih satu atau beberapa joint di Maya, lalu klik **Add Joints To The List**. Jika mesh belum di-bind, joint tersebut akan digunakan oleh **Bind Skin**. Jika mesh sudah memiliki skinCluster, joint baru tetap berstatus pending sampai kamu memilihnya di daftar dan menjalankan **Add Influence**.

Untuk mencari joint dalam daftar influence yang panjang, pilih joint tersebut di Maya lalu klik **Select Joints In The List**. Baris yang cocok akan langsung disorot.

### Sort, Search, dan Pin

- **A to Z** dan **Z to A** untuk mengurutkan nama joint yang ditampilkan.
- **Pending Joints** menempatkan pending joint di bagian atas daftar. Opsi ini hanya tersedia jika ada pending joint.
- **Search** menyaring baris yang ditampilkan tanpa mengubah skinCluster.
- **Pin** hanya menampilkan baris joint yang dipilih. Pilih joint di daftar, lalu klik ikon pin. Matikan Pin untuk kembali ke tampilan daftar yang difilter seperti biasa.
- **Reset** mengosongkan mesh aktif, daftar joint, Search, Pin, dan pengaturan smoothing di dalam tool.

### Lock dan menu klik kanan

Klik ikon lock di samping joint untuk mengunci atau membukanya. Pada bound influence, ini mengikuti status lock di skinCluster. Untuk pending joint, status lock disimpan sementara di AD Skin Tool sampai joint ditambahkan.

Klik kanan pada daftar joint untuk mengakses perintah tambahan:

- Lock atau unlock baris yang dipilih maupun baris di luar selection.
- Memilih seluruh pending joint.
- Menghapus pending joint yang dipilih, yang tidak dipilih, atau semuanya. Perintah ini tidak menghapus bound influence.
- Memilih vertex yang memiliki weight bukan nol dari bind influence yang dipilih.
- Memilih satu atau seluruh joint dalam daftar di Maya.
- Menjadikan satu joint terpilih sebagai **Global Owner**, atau menghapus pengaturan Global Owner.

**Global Owner** bersifat opsional. Jika mesh memiliki bagian terpisah (*detached secondary region*), kamu bisa memilih joint yang akan menjadi owner bagian tersebut setelah proses local assignment pada Bind, Add Influence, atau Flood. Biasanya fitur ini tidak perlu diaktifkan jika hasil otomatisnya sudah sesuai. Global Owner yang aktif ditandai warna kuning dan hanya berlaku untuk mesh yang sedang di-load.

{{< collapse title="Joint List demonstration" collapse="true">}}
![Joint List demonstration](/images/documentation/ad-skin-tool/02-joint-list.gif)
{{< /collapse >}}

## Blend dan Iterations

Pengaturan ini digunakan oleh **Bind Skin**, **Add Influence**, **Flood**, dan **Smooth**:

- **Blend** (`0.000`–`1.000`) menentukan seberapa kuat smoothing mengubah weight berdasarkan vertex di sekitarnya. Nilai rendah lebih mempertahankan blocking, sedangkan nilai tinggi menghasilkan smoothing yang lebih kuat.
- **Iterations** (`0`–`10`) menentukan berapa kali smoothing dijalankan. Semakin tinggi nilainya, semakin luas pengaruh smoothing ke vertex di sekitarnya.

Pada Bind Skin, Add Influence, dan Flood, **Iterations 0** menghasilkan hard blocking tanpa smoothing. Untuk menjalankan **Smooth**, gunakan Iterations `1` atau lebih. Nilai default-nya adalah Blend `0.250` dan Iterations `0`.

## Bind Skin

Gunakan **Bind Skin** jika mesh aktif belum memiliki skinCluster.

1. Load polygon mesh yang belum di-bind.
2. Tambahkan minimal dua joint ke daftar.
3. Jika diperlukan, pilih Global Owner.
4. Atur Blend dan Iterations. Gunakan Iterations `0` untuk hasil hard blocking, atau nilai di atas `0` jika ingin smoothing.
5. Klik **Bind Skin** dan tunggu prosesnya selesai.

Bind Skin menggunakan **semua joint dalam daftar**, bukan hanya baris yang disorot. AD Skin Tool menentukan region permukaan untuk setiap joint, membuat skinCluster, menulis weight, lalu memperbarui daftar agar influence yang baru di-bind langsung terlihat.

{{< collapse title="Bind Skin demonstration" collapse="true">}}
![Bind Skin demonstration](/images/documentation/ad-skin-tool/03-bind-skin.gif)
{{< /collapse >}}

## Add Influence

Gunakan **Add Influence** untuk menambahkan joint ke skinCluster yang sudah ada dan memberikan weight pada region lokal joint tersebut.

1. Pilih joint baru di Maya, lalu klik **Add Joints To The List**.
2. Di daftar influence, pilih pending joint yang ingin ditambahkan.
3. Pastikan pending joint tersebut tidak terkunci.
4. Atur Blend dan Iterations.
5. Klik **Add Influence**.

Hanya pending joint yang dipilih yang ditambahkan. Influence lama tetap berada dalam skinCluster, sementara joint baru menerima region lokalnya. Setelah selesai, joint tersebut menjadi bound influence dan tetap terpilih di daftar.

{{< collapse title="Add Influence demonstration" collapse="true">}}
![Add Influence demonstration](/images/documentation/ad-skin-tool/04-add-influence.gif)
{{< /collapse >}}

## Flood

**Flood** menghitung ulang region weight untuk joint yang dipilih. Joint tersebut harus sudah menjadi bound influence.

1. Pilih satu atau beberapa bound influence di daftar joint.
2. Di Maya, pilih vertex, edge, atau face pada mesh aktif untuk memproses component tertentu. Untuk memproses seluruh mesh, pilih object mesh-nya.
3. Atur Blend dan Iterations.
4. Klik **Flood**.

Jika kamu memilih component, Flood bekerja pada area selection tersebut. Maya Soft Selection juga didukung, dan falloff-nya akan memengaruhi hasil. Jika kamu memilih object mesh aktif, AD Skin Tool akan meminta konfirmasi sebelum memproses seluruh mesh.

Dengan Iterations `0`, Flood menghasilkan hard blocking pada region yang diproses. Gunakan Iterations di atas `0` untuk menambahkan smoothing sesuai nilai Blend. Pending joint akan diabaikan meskipun ikut dipilih bersama bound influence—gunakan Add Influence untuk menambahkannya terlebih dahulu. Target Flood yang dipilih harus dalam keadaan unlocked; weight pada influence lain yang terkunci tetap dilindungi.

{{< collapse title="Flood demonstration" collapse="true">}}
![Flood demonstration](/images/documentation/ad-skin-tool/05-flood.gif)
{{< /collapse >}}

## Smooth

**Smooth** meratakan skin weights pada component yang dipilih atau pada seluruh mesh aktif.

1. Di Maya, pilih vertex, edge, atau face pada mesh aktif. Untuk smooth seluruh mesh, pilih object mesh-nya.
2. Atur Blend dan set Iterations ke `1` atau lebih.
3. Klik **Smooth**.

Smooth tidak memerlukan pemilihan joint di daftar. Pada component mode, hasilnya mengikuti falloff Maya Soft Selection. Pada object mode, tool meminta konfirmasi sebelum memproses seluruh mesh. Weight pada locked influence tetap dipertahankan, dan vertex tanpa weight yang bisa ditulis akan dilewati.

{{< collapse title="Smooth demonstration" collapse="true">}}
![Smooth demonstration](/images/documentation/ad-skin-tool/06-smooth.gif)
{{< /collapse >}}

## Skin Weight Visual

**Skin Weight Visual** menampilkan weight dari satu bound influence langsung pada mesh aktif, tanpa mengubah skin weights yang tersimpan.

1. Load mesh yang sudah memiliki skinCluster.
2. Pilih tepat satu bind influence di dalam list.
3. Pilih display mode:
   - **Spectrum:** hitam, biru, hijau, kuning, oranye, merah, dan putih.
   - **Heat:** hitam, merah, oranye, kuning, dan putih.
   - **Grayscale:** hitam melalui abu-abu hingga putih.
4. Pilih **Off** untuk mengembalikan normal mesh shading.

Jika **Live Joint Selection** dalam posisi **On**, memilih bound joint di Maya juga akan menyorot joint tersebut di daftar dan memperbarui tampilan weight-nya. Gunakan **Off** jika ingin tetap melihat weight dari influence yang sama meskipun selection di Maya berubah.

Tampilan weight akan diperbarui setelah operasi yang relevan, Undo, dan Redo. Ini hanya visualisasi sementara di viewport; tidak ada colour data yang di-bake ke skin weights.

{{< collapse title="Skin Weight Visual demonstration" collapse="true">}}
![Skin Weight Visual demonstration](/images/documentation/ad-skin-tool/07-skin-weight-visual.gif)
{{< /collapse >}}

## Mirror Skin Weights Posed Mesh

**Mirror** menyimpan pasangan vertex (*persistent vertex pairing*) agar skin weights tetap bisa di-mirror saat karakter berada dalam pose. Jika bind-reference geometry tersedia, pairing dibuat dari geometry tersebut, sehingga kamu tidak perlu mengembalikan karakter ke bind pose.

### Register mirror pairing

1. Pilih mesh yang ingin di-mirror, lalu klik **Load Mirror Mesh**. Mesh untuk Mirror terpisah dari mesh aktif pada panel utama.
2. Pilih symmetry plane:
   - **YZ** melakukan mirror melintasi X.
   - **XZ** melakukan mirror melintasi Y.
   - **XY** melakukan mirror melintasi Z.
3. Pilih **Direction** source-to-target pada axis tersebut.
4. Atur koordinat centre plane. Kamu bisa memasukkan nilainya langsung, atau memilih centre component maupun transform mesh, lalu klik **Register Selected** agar nilainya dihitung dari selection.
5. Atur **Tolerance**. Mulai dari default `0.001`, lalu naikkan seperlunya hingga pasangan vertex simetris dapat ditemukan.
6. Masukkan marker nama joint untuk **Left** dan **Right**, misalnya `L` / `R`, `L_` / `R_`, atau `_l` / `_r`. Marker bisa berada di awal, tengah, atau akhir nama joint, tetapi keduanya harus berbeda.
7. Klik **Preview Pairing**.

Preview menampilkan jumlah vertex pair yang valid, centre vertex, unmatched vertex, ambiguous vertex, dan maximum pairing error. Vertex yang perlu diperiksa akan dipilih di Maya. Preview tidak menimpa pairing yang sudah tersimpan.

Jika hasil Preview valid, klik **Register Pairing**. Pasangan vertex akan disimpan pada mesh dan bisa digunakan kembali. Jika pairing sudah ada, tombol berubah menjadi **Replace Pairing...** dan meminta konfirmasi. Setelah topology berubah, jalankan Preview lagi lalu ganti pairing lama.

### Terapkan hasil mirror

1. Load mesh yang memiliki skinCluster dan pairing Mirror yang valid.
2. Atur Direction dan periksa kembali marker Left/Right.
3. Untuk memproses seluruh mesh, jangan pilih component atau pilih seluruh region yang sudah terdaftar.
4. Untuk component mode, pilih component donor hanya dari satu sisi. Pasangan vertex di sisi lainnya akan menjadi target.
5. Klik **Mirror Skin Weights**.

Direction menentukan sisi yang menjadi donor weight. Joint influence dipasangkan berdasarkan marker Left/Right. Weight pada target influence yang terkunci tetap dipertahankan. Pada component mode, jangan memilih kedua sisi dari region Mirror yang sama.

Tombol **Reset** pada Mirror mengosongkan mesh aktif dan pengaturan panel Mirror. Pairing yang sudah tersimpan di mesh tidak ikut terhapus.

{{< collapse title="Mirror demonstration" collapse="true">}}
![Mirror demonstration](/images/documentation/ad-skin-tool/08-mirror-optimized.gif)
{{< /collapse >}}

## Transfer Skin Weights

**Transfer** memproyeksikan skin weights dari satu atau beberapa source mesh yang sudah di-skin ke satu atau beberapa target mesh. Source menyediakan referensi influence dan weight; Target menerima hasil transfernya.

### Register source dan target

1. Pilih satu atau beberapa source mesh yang sudah memiliki skinCluster, lalu klik **Add Selected** di bagian **Sources**. Kamu boleh memilih component, tetapi AD Skin Tool tetap mendaftarkan seluruh mesh sebagai donor.
2. Pilih satu atau beberapa target mesh atau component-nya, lalu klik **Add Selected** di bagian **Targets**. Mesh target didaftarkan sekarang; selection component baru diperiksa saat kamu menjalankan Preview Transfer.
3. Gunakan **Remove Selected** atau **Clear** untuk mengubah daftar. Satu mesh tidak bisa menjadi Source sekaligus Target.

Klik kanan pada salah satu daftar untuk memilih object yang disorot atau seluruh object terdaftar di Maya.

### Menentukan area target

Daftar Target menentukan mesh mana saja yang ikut dalam transfer. Saat kamu menjalankan Preview, component selection di Maya hanya memengaruhi area pada target terdaftar yang sesuai:

| Kondisi target saat Preview | Scope yang digunakan |
|---|---|
| Tidak ada component yang dipilih pada target terdaftar | Seluruh target mesh diproses |
| Component dipilih pada target yang sudah memiliki skinCluster | Hanya vertex target yang dipilih yang diproses |
| Component dipilih pada target tanpa skinCluster | Component target dilewati; mesh harus di-bind terlebih dahulu |
| Target tanpa skinCluster digunakan sebagai whole object | SkinCluster baru dapat dibuat saat Apply |

Component mode dan object mode bisa digabung dalam satu transfer. Misalnya, satu target hanya memproses vertex yang dipilih, sementara target lain memproses seluruh mesh. Memilih component pada mesh yang tidak terdaftar tidak akan menambahkan mesh tersebut ke transfer.

### Preview dan Apply

1. Pilih component target yang ingin diproses, atau biarkan tanpa component selection untuk object mode.
2. Klik **Preview Transfer**.
3. Periksa ringkasan status: target yang terdaftar, aktif, atau dilewati; vertex yang diminta dan bisa ditulis; baris yang terkunci atau kosong; serta maximum source distance.
4. Jika Preview valid, klik **Transfer Skin Weights**.

Preview mencari titik source terdekat untuk setiap target dan menyimpan kecocokannya untuk Apply. Tahap ini tidak mengubah weight. Jika daftar Source/Target, component selection, skinCluster, atau urutan influence berubah setelah Preview, jalankan Preview kembali sebelum Apply.

Saat Apply:

- Target tanpa skinCluster dalam object mode akan menerima skinCluster baru.
- Source influence yang belum ada pada target akan ditampilkan sebelum ditambahkan.
- Locked target influence akan ditampilkan dan dilewati agar nilainya tetap dipertahankan.
- Jika ada influence yang perlu ditambahkan atau dilewati karena terkunci, tool menampilkan **Cancel** dan **Proceed**. Cancel mempertahankan Preview tanpa mengubah apa pun.
- Transfer dan adaptive boundary smoothing berjalan sebagai satu operasi. Jika transfer ke beberapa target gagal, perubahan akan di-rollback agar tidak meninggalkan hasil yang hanya diterapkan sebagian.

Tombol **Reset** pada Transfer mengosongkan daftar Source, Target, dan Preview saat ini. Reset tidak membatalkan transfer yang sudah diterapkan; gunakan Maya Undo untuk mengembalikan perubahan tersebut.

{{< collapse title="Transfer demonstration" collapse="true">}}
![Transfer demonstration](/images/documentation/ad-skin-tool/09-transfer-optimized.gif)
{{< /collapse >}}

## Status, Undo, dan Diagnostics

Setiap operasi menampilkan ringkasan hasil di bawah panelnya dan laporan lebih detail di Maya Script Editor. Periksa keduanya jika Preview hanya berhasil sebagian atau ada vertex yang dilewati karena influence terkunci, donor weight tidak bisa digunakan, geometry tidak cocok, atau component selection tidak valid.

Bind, Add Influence, Flood, Smooth, Mirror, dan Transfer mendukung Maya Undo. Jika hasilnya tidak sesuai harapan, gunakan Undo sebelum melanjutkan edit yang lain.

Jika memerlukan bantuan, buka **Tool Help** dan klik **Copy Diagnostics**. Kirim laporan yang disalin beserta penjelasan singkat masalahnya ke [hello@adiendendra.com](mailto:hello@adiendendra.com). Jangan mengirim asset produksi yang bersifat rahasia atau license key lengkap.
