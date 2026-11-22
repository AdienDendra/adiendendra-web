---
title: "Dokumentasi & Tutorial AD Skin Tool"
translationKey: "ad-skin-tool-tutorial"
summary: "Panduan untuk workflow AD Skin Tool di Autodesk Maya."
description: "Panduan load mesh, pengelolaan influence, bind, flood, smooth, visualisasi skin weights, mirror, dan transfer dengan AD Skin Tool."
date: 2026-09-11T10:00:00+10:00
lastmod: 2026-11-22T18:47:20+11:00
tags: ["maya", "ad-skin-tool", "dokumentasi", "tutorial"]
categories: ["documentation"]
comments: true
showToc: true
TocOpen: true
ShowReadingTime: false
ShowPostNavLinks: false
---

Panduan ini menjelaskan fungsi setiap kontrol AD Skin Tool dan pengaruhnya pada scene Maya, mulai dari setup skinCluster hingga mirror dan transfer skin weights.

Untuk harga, kompatibilitas, dan ketersediaan rilis, bisa dilihat di [halaman produk AD Skin Tool](/id/3dtools/ad-skin-tool/).

## Instalasi dan membuka tool

Download paket yang sesuai dengan versi Maya, sistem operasi, dan arsitektur prosesor yang akan digunakan. Ikuti petunjuk instalasi di dalam ZIP, karena setiap paket dibuat untuk kombinasi versi Maya dan platform tertentu.

Untuk ZIP v1.0.0, buka tab Python di **Script Editor** Maya, lalu jalankan perintah pada langkah 5 di `README.txt`. Jika paket berisi folder `ad_skin_tool`, gunakan:

```python
from ad_skin_tool import launch

launch.show(
    reload=False,
    auto_refresh=False,
)
```

AD Skin Tool terbuka sebagai Maya workspace control yang bisa di-dock atau dibiarkan floating. **Tool Help** menyediakan referensi singkat dan environment diagnostics, sedangkan **License** membuka pengaturan trial, aktivasi lisensi, dan perangkat. Alur lisensi selengkapnya ada di [Panduan Lisensi AD Skin Tool](/id/documentation/ad-skin-tool-license/).

## Alur kerja yang direkomendasikan

1. Pilih polygon mesh atau salah satu component-nya, lalu klik **Load Mesh**.
2. Tambahkan atau pilih joint yang diperlukan di bagian **Joints / Influences**.
3. Atur **Blend** dan **Iterations** untuk operasi yang akan dijalankan.
4. Jalankan **Bind Skin**, **Add Influence**, **Flood**, atau **Smooth** pada mesh yang aktif.
5. Gunakan panel **Mirror** atau **Transfer** untuk workflow mirror dan transfer skin weights.
6. Periksa status setelah setiap operasi. Detail diagnostics juga tersedia di Maya Script Editor.

> Selection di Maya menentukan scope setiap operasi. Sebelum menjalankan perintah, periksa apakah selection aktif berupa mesh, component, joint, atau tidak ada selection.

## Mesh / Skin Context

### Load Mesh

Pilih polygon mesh atau salah satu vertex, edge, maupun face-nya, lalu klik **Load Mesh**. Mesh tersebut menjadi context aktif di AD Skin Tool dan tidak berubah ketika selection di Maya berganti. Untuk pindah ke mesh lain, pilih mesh baru lalu klik **Load Mesh** lagi.

Panel ini menampilkan:

- **Skin Cluster:** skinCluster pada mesh aktif, atau `<no skinCluster>` jika mesh belum memiliki skinCluster.
- **Loaded Mesh:** nama transform yang digunakan oleh Bind, Add Influence, Flood, Smooth, dan Skin Weight Visual.
- **Listed Joints:** jumlah bind dan pending joint yang sedang ditampilkan dalam influence list.

Saat mesh yang sudah memiliki skinCluster di-load, daftar joint otomatis menampilkan influence yang ada. Untuk mesh tanpa skinCluster, daftar dimulai dari kosong sehingga joint bisa ditambahkan sebelum bind.

{{< collapse title="Load Mesh demonstration" collapse="true">}}
![Load Mesh demonstration](/images/documentation/ad-skin-tool/01-load-mesh.gif)
{{< /collapse >}}

## Joints / Influences

### Bind dan pending joint

Daftar ini dapat berisi dua jenis joint:

- **Bind influence** sudah menjadi bagian dari skinCluster pada mesh aktif dan ditampilkan dengan warna hijau.
- **Pending joint** sudah ada di scene dan masuk ke daftar, tetapi belum menjadi influence pada skinCluster. Joint ini ditampilkan dengan warna putih.

Pilih satu atau beberapa joint di Maya, lalu klik **Add Joints To The List**. Pada mesh tanpa skinCluster, joint tersebut akan digunakan oleh **Bind Skin**. Pada mesh yang sudah di-skin, joint baru tetap berstatus pending sampai dipilih di daftar dan diproses menggunakan **Add Influence**.

Untuk mencari joint dalam influence list yang panjang, pilih joint tersebut di Maya lalu klik **Select Joints In The List**. Baris yang sesuai akan disorot.

### Sort, Search, dan Pin

- **A to Z** dan **Z to A** untuk mengurutkan nama joint yang ditampilkan.
- **Pending Joints** menempatkan pending joint di bagian atas daftar. Opsi ini hanya tersedia jika ada pending joint.
- **Search** memfilter row yang terlihat tanpa mengubah skinCluster.
- **Pin** hanya menampilkan baris joint yang dipilih. Pilih baris joint, lalu klik ikon pin. Matikan Pin untuk kembali ke daftar yang difilter seperti biasa.
- **Reset** mengosongkan mesh aktif, daftar joint, Search, Pin, dan pengaturan smoothing di dalam tool.

### Lock dan menu klik kanan

Klik ikon lock di samping joint untuk mengunci atau membukanya. Pada bind influence, status lock mengikuti skinCluster. Untuk pending joint, statusnya disimpan sementara di AD Skin Tool.

Klik kanan pada daftar joint untuk membuka perintah tambahan:

- Lock atau unlock baris yang dipilih maupun baris di luar selection (*inverse selection*).
- Memilih seluruh pending joint.
- Menghapus pending joint yang dipilih, yang tidak dipilih, atau semuanya. Perintah ini tidak menghapus bind influence.
- Memilih vertex yang memiliki weight bukan nol dari bind influence yang dipilih.
- Memilih satu atau seluruh listed joint di Maya scene.
- Menetapkan satu selected joint sebagai **Global Owner**, atau membersihkan Global Owner saat ini.

**Global Owner** bersifat opsional. Pada mesh dengan detached secondary region, fitur ini menentukan joint yang menjadi owner region tersebut setelah local assignment pada Bind, Add Influence, atau Flood. Biarkan tidak aktif jika hasil assignment otomatis sudah sesuai. Global Owner yang aktif ditandai warna kuning dan hanya berlaku pada mesh yang sedang di-load.

{{< collapse title="Joint List demonstration" collapse="true">}}
![Joint List demonstration](/images/documentation/ad-skin-tool/02-joint-list.gif)
{{< /collapse >}}

## Blend dan Iterations

Control ini digunakan bersama oleh **Bind Skin**, **Add Influence**, **Flood**, dan **Smooth**:

- **Blend** memiliki rentang `0.000` sampai `1.000` dan mengatur seberapa kuat smoothing mengubah weight berdasarkan vertex di sekitarnya. Nilai rendah lebih mempertahankan blocking, sedangkan nilai tinggi menghasilkan smoothing yang lebih kuat.
- **Iterations** memiliki rentang `0` sampai `10` dan menentukan berapa kali smoothing dijalankan. Semakin tinggi nilainya, semakin jauh pengaruh smoothing menyebar ke vertex di sekitarnya.

Pada Bind Skin, Add Influence, dan Flood, **Iterations 0** mempertahankan hasil hard blocking. **Smooth** membutuhkan Iterations `1` atau lebih. Nilai default adalah Blend `0.250` dan Iterations `0`.

## Bind Skin

Gunakan **Bind Skin** untuk membuat skinCluster awal pada unskinned loaded mesh.

1. Load polygon mesh yang belum di skin.
2. Tambahkan setidaknya dua joint ke dalam list.
3. Jika diperlukan, tetapkan Global Owner.
4. Tentukan Blend dan Iterations. Gunakan Iterations `0` untuk hard initial blocking atau nilai positif untuk menyertakan smoothing.
5. Klik **Bind Skin** dan tunggu sampai operasi selesai.

Bind Skin menggunakan **seluruh joint dalam daftar**, bukan hanya baris yang disorot. Tool menentukan region permukaan untuk setiap joint, membuat skinCluster, menulis weight, lalu memperbarui daftar dengan influence yang baru di-bind.

{{< collapse title="Bind Skin demonstration" collapse="true">}}
![Bind Skin demonstration](/images/documentation/ad-skin-tool/03-bind-skin.gif)
{{< /collapse >}}

## Add Influence

Gunakan **Add Influence** ketika mesh sudah memiliki skinCluster dan perlu ditambahkan joint baru beserta region weight-nya.

1. Pilih joint baru di Maya dan klik **Add Joints To The List**.
2. Di influence list, pilih pending joint yang ingin ditambahkan.
3. Pastikan pending row tersebut tidak terkunci.
4. Atur Blend dan Iterations.
5. Klik **Add Influence**.

Hanya pending joint yang dipilih yang ditambahkan. Influence lama tetap berada dalam skinCluster, sementara region untuk joint baru diperbarui. Setelah selesai, joint tersebut menjadi bind influence dan tetap terpilih di daftar.

{{< collapse title="Add Influence demonstration" collapse="true">}}
![Add Influence demonstration](/images/documentation/ad-skin-tool/04-add-influence.gif)
{{< /collapse >}}

## Flood

**Flood** menghitung ulang region weight untuk **bind influence** yang dipilih.

1. Pilih satu atau beberapa joint yang sudah memiliki influence di UI list.
2. Di Maya scene, pilih vertex, edge, atau face pada loaded mesh untuk component operation. Untuk memproses seluruh mesh, cukup pilih mesh object.
3. Atur Blend dan Iterations.
4. Klik **Flood**.

Jika component dipilih, Flood hanya memproses area selection tersebut. Maya Soft Selection juga didukung, dan falloff-nya memengaruhi hasil. Jika object mesh aktif yang dipilih, tool akan meminta konfirmasi sebelum memproses seluruh mesh.

Dengan Iterations `0`, Flood menghasilkan hard blocking pada region yang diproses. Iterations di atas `0` menambahkan smoothing sesuai nilai Blend. Pending joint tetap diabaikan meskipun ikut dipilih bersama bind influence, jadi gunakan Add Influence untuk menambahkannya. Target Flood yang dipilih harus unlocked, sedangkan weight pada influence lain yang terkunci tetap terlindungi.

{{< collapse title="Flood demonstration" collapse="true">}}
![Flood demonstration](/images/documentation/ad-skin-tool/05-flood.gif)
{{< /collapse >}}

## Smooth

Smooth meratakan skin weight saat ini pada component selection atau pada seluruh loaded mesh.

1. Di Maya, pilih vertex, edge, atau face pada loaded mesh. Untuk melakukan smooth pada seluruh mesh, pilih loaded mesh object.
2. Atur Blend dan set Iterations ke `1` atau lebih.
3. Klik **Smooth**.

Smooth tidak memerlukan joint yang dipilih di daftar. Pada component mode, hasilnya mengikuti falloff Maya Soft Selection. Pada object mode, tool meminta konfirmasi sebelum memproses seluruh mesh. Weight pada locked influence tetap dipertahankan, dan vertex tanpa writable weight dilewati.

{{< collapse title="Smooth demonstration" collapse="true">}}
![Smooth demonstration](/images/documentation/ad-skin-tool/06-smooth.gif)
{{< /collapse >}}

## Skin Weight Visual

Skin Weight Visual menampilkan weight dari satu bind influence langsung pada mesh aktif tanpa mengubah data skin weights yang tersimpan.

1. Load mesh yang sudah memiliki skinCluster.
2. Pilih tepat satu bind influence di dalam list.
3. Pilih display mode:
   - **Spectrum:** hitam, biru, hijau, kuning, oranye, merah, dan putih.
   - **Heat:** hitam, merah, oranye, kuning, dan putih.
   - **Grayscale:** hitam melalui abu-abu hingga putih.
4. Pilih **Off** untuk mengembalikan normal mesh shading.

Saat **Live Joint Selection** dalam posisi **On**, memilih bind joint di Maya juga akan menyorot joint tersebut di daftar dan memperbarui visualisasi weight-nya. Gunakan **Off** untuk mempertahankan influence yang ditampilkan meskipun selection di Maya berubah.

Visualisasi diperbarui setelah operasi weight yang relevan, Undo, dan Redo. Tampilan ini hanya sementara di viewport dan tidak melakukan bake colour data ke skin weights.

{{< collapse title="Skin Weight Visual demonstration" collapse="true">}}
![Skin Weight Visual demonstration](/images/documentation/ad-skin-tool/07-skin-weight-visual.gif)
{{< /collapse >}}

## Mirror Skin Weights Posed Mesh

Mirror menyimpan pasangan vertex (*persistent vertex pairing*) agar weight tetap bisa di-mirror saat karakter berada dalam pose. Jika bind-reference geometry tersedia, pairing dibuat dari geometry tersebut tanpa perlu mengembalikan karakter ke bind pose.

### Register mirror pairing

1. Pilih mesh yang akan di mirror, kemudian klik **Load Mirror Mesh**. Context ini terpisah dari context utama Load Mesh.
2. Pilih symmetry plane:
   - **YZ** melakukan mirror melintasi X.
   - **XZ** melakukan mirror melintasi Y.
   - **XY** melakukan mirror melintasi Z.
3. Pilih **Direction** source-to-target pada axis tersebut.
4. Atur koordinat centre plane. Nilainya bisa dimasukkan langsung, atau dihitung dari selection dengan memilih centre component maupun mesh transform lalu klik **Register Selected**.
5. Atur **Tolerance**. Mulai dari nilai default `0.001`, lalu naikkan secukupnya untuk menemukan symmetrical counterpart yang valid.
6. Masukkan literal joint name marker untuk **Left** dan **Right**, misalnya `L` / `R`, `L_` / `R_`, atau `_l` / `_r`. Marker dapat berupa prefix, suffix, atau infix, tetapi keduanya harus berbeda.
7. Klik **Preview Pairing**.

Preview menampilkan jumlah legal pair, centre vertex, unmatched vertex, ambiguous vertex, dan maximum pairing error. Vertex yang bermasalah dipilih di Maya untuk diperiksa. Preview tidak menimpa pairing yang sudah tersimpan.

Jika hasil Preview valid, klik **Register Pairing**. Pasangan vertex disimpan pada mesh dan dapat digunakan kembali. Jika pairing sudah ada, tombol berubah menjadi **Replace Pairing...** dan meminta konfirmasi. Perubahan topology membuat pairing lama tidak berlaku, sehingga Preview dan Replace Pairing perlu dijalankan ulang.

### Terapkan mirrored weights

1. Load mirror mesh yang memiliki registered pairing valid dan skinCluster.
2. Atur Direction dan pastikan Left/Right marker benar.
3. Untuk mode seluruh mesh, jangan memilih mesh component atau pilih seluruh registered region.
4. Untuk mode component selection, pilih donor component hanya dari satu sisi. Registered counterpart akan menjadi target.
5. Klik **Mirror Skin Weights**.

Direction yang dipilih menentukan sisi yang mendonorkan weight. Joint influence dipasangkan menggunakan literal Left/Right marker. Nilai locked target influence tetap dipertahankan. Jangan memilih kedua sisi dari mirror region yang sama dalam component mode.

Tombol **Reset** pada Mirror mengosongkan mesh aktif di panel Mirror dan pengaturannya saat ini. Pairing yang tersimpan pada mesh tidak ikut terhapus.

{{< collapse title="Mirror demonstration" collapse="true">}}
![Mirror demonstration](/images/documentation/ad-skin-tool/08-mirror-optimized.gif)
{{< /collapse >}}

## Transfer Skin Weights

Transfer memproyeksikan skin weights dari satu atau beberapa skinned source mesh ke target mesh. Source menyediakan referensi influence dan weight, sedangkan Target menerima hasil transfer.

### Register source dan target

1. Pilih satu atau beberapa skinned source mesh, lalu klik **Add Selected** pada **Sources**. Component juga bisa dipilih, tetapi seluruh source mesh tetap didaftarkan sebagai donor.
2. Pilih satu atau beberapa target mesh atau component-nya, lalu klik **Add Selected** pada **Targets**. Mesh target langsung didaftarkan, sedangkan component scope diperiksa saat Preview Transfer dijalankan.
3. Gunakan **Remove Selected** atau **Clear** untuk mengubah masing-masing list. Satu mesh tidak dapat diregistrasikan sebagai source sekaligus target.

Klik kanan pada salah satu list untuk memilih highlighted object atau semua registered object di list tersebut di Maya scene.

### Memahami target scope

Daftar Target menentukan mesh yang ikut dalam transfer. Saat Preview dijalankan, component selection di Maya hanya mengubah scope untuk target terdaftar yang sesuai:

| Kondisi target saat Preview | Scope yang digunakan |
|---|---|
| Tidak ada component yang dipilih pada registered target | Seluruh target mesh diproses |
| Component dipilih pada registered skinned target | Hanya selected target vertex yang diproses |
| Component dipilih pada unskinned target | Component target dilewati dan harus di-bind terlebih dahulu |
| Unskinned target digunakan sebagai whole object | Target skinCluster baru dapat dibuat saat Apply |

Component mode dan object mode dapat digunakan dalam satu transfer. Misalnya, satu target memproses selected vertex, sedangkan target lain memproses seluruh mesh. Component pada mesh yang tidak terdaftar tidak akan ditambahkan ke transfer.

### Preview dan Apply

1. Atur target component selection yang diinginkan, atau biarkan registered target tanpa component untuk object mode.
2. Klik **Preview Transfer**.
3. Periksa status summary yang mencakup registered, active, dan skipped target, requested dan writable vertex, locked atau empty row, serta maximum source distance.
4. Jika Preview valid, klik **Transfer Skin Weights**.

Preview menghitung dan menyimpan pasangan titik source terdekat (*closest-source correspondence*) untuk digunakan saat Apply. Tahap ini tidak mengubah weight. Jika daftar Source/Target, component scope, skinCluster, atau influence order berubah setelah Preview, jalankan Preview kembali.

Saat Apply:

- Object unskinned target akan menerima skinCluster baru.
- Source influence yang belum ada pada existing target akan ditampilkan sebelum ditambahkan.
- Locked target influence akan ditampilkan dan dilewati sehingga nilainya tidak berubah.
- Jika salah satu kondisi tersebut ada, tool menampilkan **Cancel** dan **Proceed**. Cancel mempertahankan Preview dan tidak melakukan perubahan.
- Transfer dan adaptive boundary smoothing dijalankan sebagai satu operasi. Jika transfer ke beberapa target gagal, perubahan di-rollback agar tidak meninggalkan partial result.

Tombol **Reset** pada Transfer membersihkan registered Source dan Target list serta Preview saat ini. Reset tidak membatalkan transfer yang sudah diterapkan, sehingga pembatalan perlu dilakukan melalui Maya Undo.

{{< collapse title="Transfer demonstration" collapse="true">}}
![Transfer demonstration](/images/documentation/ad-skin-tool/09-transfer-optimized.gif)
{{< /collapse >}}

## Status, Undo, dan diagnostics

Setiap operasi menampilkan ringkasan hasil di bawah panelnya dan laporan detail di Maya Script Editor. Periksa keduanya jika Preview hanya berhasil sebagian atau vertex dilewati karena influence terkunci, donor weight tidak bisa ditulis, geometry tidak cocok, atau component scope tidak valid.

Operasi Bind, Add Influence, Flood, Smooth, Mirror, dan Transfer yang sudah diterapkan mengikuti Maya Undo workflow. Jika hasil tidak sesuai dengan yang diinginkan, gunakan Maya Undo sebelum melanjutkan pengeditan yang lain.

Untuk menghubungi support, buka **Tool Help** lalu klik **Copy Diagnostics**. Sertakan environment report dan penjelasan singkat masalahnya. Jangan mengirim asset produksi rahasia atau license key lengkap. Support tersedia melalui [hello@adiendendra.com](mailto:hello@adiendendra.com).
