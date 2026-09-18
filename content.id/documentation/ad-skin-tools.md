---
title: "AD Skin Tools Dokumentasi & Tutorial"
translationKey: "ad-skin-tools-getting-started"
summary: "Panduan untuk workflow AD Skin Tools di Autodesk Maya."
description: "Cara meload mesh, mengelola influence, bind, flood, smooth, memvisualisasikan, mirror, dan transfer skin weight dengan AD Skin Tools."
date: 2026-09-11T10:00:00+10:00
lastmod: 2026-09-11T20:30:00+10:00
tags: ["maya", "ad-skin-tools", "dokumentasi", "tutorial"]
categories: ["documentation"]
comments: false
showToc: true
TocOpen: true
ShowReadingTime: false
ShowPostNavLinks: false
---

Tutorial ini mengikuti urutan AD Skin Weights Tool dari atas ke bawah dan menjelaskan setiap control terhadap Maya scene yang sedang digunakan.

Untuk harga, kompatibilitas, dan ketersediaan rilis, bisa dilihat di [halaman produk AD Skin Tools](/id/3dtools/ad-skin-tools/).

## Instalasi dan membuka tool

Gunakan download yang sesuai dengan versi Autodesk Maya, sistem operasi, dan arsitektur processor Anda. Extract package mengikuti petunjuk instalasi yang disertakan bersama download; package yang dibuat secara spesifik untuk versi Maya dan target sistem operasinya.

Buka **Script Editor** di Maya, lalu pindah ke tab Python, dan jalankan:

```python
import ad_skin_tools.launch as ad_skin_tools

ad_skin_tools.show(
    reload=False,
    auto_refresh=False,
)
```

Tool akan terbuka sebagai Maya workspace control dan dapat di dock atau dibiarkan floating. **Tool Help** membuka referensi singkat serta environment diagnostics. **License** membuka jendela trial, activation, dan device management.

## Urutan penggunaan yang direkomendasikan

1. Pilih polygon mesh atau salah satu componentnya, lalu klik **Load Mesh**.
2. Tambahkan atau pilih joint yang diperlukan di bagian **Joints / Influences**.
3. Atur **Blend** dan **Iterations** untuk operasi yang akan dijalankan.
4. Gunakan **Bind Skin**, **Add Influence**, **Flood**, atau **Smooth** untuk loaded mesh.
5. Gunakan utility **Mirror** dan **Transfer** yang terpisah ketika workflow tersebut diperlukan.
6. Baca status setelah setiap operasi. Diagnostics yang lebih terperinci juga dicetak di Maya Script Editor.

> Maya selection memiliki fungsi yang berbeda untuk setiap operasi. Sebelum menjalankannya, periksa apakah yang sedang dipilih adalah loaded object, component, joint, atau tidak ada selection sama sekali.

## Mesh / Skin Context

### Load Mesh

Pilih satu polygon mesh, atau vertex, edge, maupun face milik mesh tersebut, kemudian klik **Load Mesh**. Tool akan menyimpan mesh itu sebagai working context. Mengubah Maya selection setelahnya tidak akan mengganti loaded context; untuk bekerja pada mesh yang lain, maka pilih mesh tersebut dan klik **Load Mesh** kembali.

Panel ini menampilkan:

- **Skin Cluster:** skinCluster yang ada pada loaded mesh, atau `<no skinCluster>` jika mesh belum di skin.
- **Loaded Mesh:** nama transform yang sedang digunakan oleh workflow Bind, Add Influence, Flood, Smooth, dan visualisation.
- **Listed Joints:** jumlah bind dan pending joint yang sedang ditampilkan dalam influence list.

Ketika skinned mesh dimuat, list otomatis diisi dengan influence yang sudah dimiliki skinCluster. Ketika unskinned mesh dimuat, tool membuat working context kosong yang siap diisi joint sebelum binding.

{{< collapse title="Load Mesh demonstration" collapse="true">}}
![Load Mesh demonstration](/images/documentation/ad-skin-tools/01-load-mesh.gif)
{{< /collapse >}}

## Joints / Influences

### Bind dan pending joint

List dapat berisi dua jenis joint:

- **Bind influence** sudah menjadi bagian dari skinCluster pada loaded mesh dan ditampilkan dengan warna hijau.
- **Pending joint** sudah ada di scene dan di dalam list, tetapi belum ditambahkan ke skinCluster pada loaded mesh dengan warna putih.

Pilih satu atau beberapa joint di Maya, kemudian klik **Add Joints To The List**. Pada unskinned loaded mesh, joint tersebut menjadi kumpulan joint yang digunakan oleh **Bind Skin**. Pada skinned loaded mesh, joint yang baru dimasukkan akan tetap berstatus pending sampai dipilih di dalam list dan diproses menggunakan **Add Influence**.

Pilih joint di Maya scene lalu klik **Select Joints In The List** untuk menemukan dan menyorot row yang sesuai. Ini berguna ketika influence list yang sangat panjang didalam window.

### Sort, Search, dan Pin

- **A to Z** dan **Z to A** untuk mengurutkan nama joint yang ditampilkan.
- **Pending Joints** memindahkan pending list joint ke atas dan hanya tersedia ketika pending joint ada.
- **Search** memfilter row yang terlihat tanpa mengubah skinCluster.
- **Pin** mempertahankan hanya row yang sedang dipilih dan terlihat di layar. Pilih joint pada row terlebih dahulu, kemudian klik ikon pin. Matikan Pin untuk mengembalikan filtered list normal.
- **Reset** membersihkan loaded mesh context, joint list, search, pin, dan smoothing setting di dalam tool.

### Lock dan context-menu actions

Klik lock control pada sebuah row untuk mengunci atau membuka joint tersebut. Untuk bind influence, control ini mengikuti influence lock pada skinCluster; untuk pending joint, lock state disimpan sementara di dalam tool.

Klik kanan pada joint list untuk membuka action tambahan:

- Lock atau unlock selected row maupun inverse selection.
- Memilih seluruh pending joint.
- Menghapus pending joint yang dipilih, inverse-selected, atau semuanya. Bind influence tidak terhapus oleh perintah removal ini.
- Memilih vertex yang memiliki weight bukan nol dari bind influence yang dipilih.
- Memilih satu atau seluruh listed joint di Maya scene.
- Menetapkan satu selected joint sebagai **Global Owner**, atau membersihkan Global Owner saat ini.

**Global Owner** bersifat opsional. Fitur ini memberikan owner yang eksplisit untuk detached secondary region setelah conservative local assignment yang digunakan oleh Bind, Add Influence, dan Flood. Biarkan tidak aktif jika local assignment normal sudah memberikan hasil yang diinginkan. Global Owner aktif ditampilkan dengan warna kuning dan hanya berlaku pada loaded mesh context saat ini.

{{< collapse title="Joint List demonstration" collapse="true">}}
![Joint List demonstration](/images/documentation/ad-skin-tools/02-joint-list.gif)
{{< /collapse >}}

## Blend dan Iterations

Control ini digunakan bersama oleh **Bind Skin**, **Add Influence**, **Flood**, dan **Smooth**:

- **Blend** memiliki rentang `0.000` sampai `1.000` dan mengatur seberapa kuat setiap smoothing untuk menggeser weight dari neighbouring vertex. Nilai rendah lebih mempertahankan blocking saat ini; nilai tinggi menghasilkan efek smoothing yang lebih kuat.
- **Iterations** memiliki rentang `0` sampai `10`. Semakin banyak iterations, semakin jauh hasil diratakan melalui neighbouring vertex.

Untuk Bind Skin, Add Influence, dan Flood, **Iterations 0** mempertahankan hasil dalam hard blocking mode. **Smooth** memerlukan Iterations `1` atau lebih. Nilai default adalah Blend `0.250` dan Iterations `0`.

## Bind Skin

Gunakan **Bind Skin** untuk membuat skinCluster awal pada unskinned loaded mesh.

1. Load polygon mesh yang belum di skin.
2. Tambahkan setidaknya dua joint ke dalam list.
3. Jika diperlukan, tetapkan Global Owner.
4. Tentukan Blend dan Iterations. Gunakan Iterations `0` untuk hard initial blocking atau nilai positif untuk menyertakan smoothing.
5. Klik **Bind Skin** dan tunggu sampai operasi selesai.

Bind Skin menggunakan **seluruh joint list**, bukan hanya row yang sedang disorot. Tool menghitung natural surface ownership untuk listed joint, membuat satu skinCluster, menulis hasilnya, lalu memperbarui context agar influence yang baru di bind muncul dalam list.

{{< collapse title="Bind Skin demonstration" collapse="true">}}
![Bind Skin demonstration](/images/documentation/ad-skin-tools/03-bind-skin.gif)
{{< /collapse >}}

## Add Influence

Gunakan **Add Influence** ketika loaded mesh sudah memiliki skinCluster dan satu atau beberapa joint baru perlu mengambil natural surface regionnya.

1. Pilih joint baru di Maya dan klik **Add Joints To The List**.
2. Di influence list, pilih pending joint yang ingin ditambahkan.
3. Pastikan pending row tersebut tidak terkunci.
4. Atur Blend dan Iterations.
5. Klik **Add Influence**.

Hanya pending joint yang dipilih yang akan ditambahkan. Existing influence tetap menjadi bagian dari skinCluster, sementara tool memperbarui region yang diklaim oleh influence baru. Setelah selesai, row yang ditambahkan berubah menjadi bind influence dan tetap terpilih di dalam list.

{{< collapse title="Add Influence demonstration" collapse="true">}}
![Add Influence demonstration](/images/documentation/ad-skin-tools/04-add-influence.gif)
{{< /collapse >}}

## Flood

Flood menghitung ulang natural region yang dimiliki oleh **bind influence** yang dipilih.

1. Pilih satu atau beberapa joint yang sudah memiliki influence di UI list.
2. Di Maya scene, pilih vertex, edge, atau face pada loaded mesh untuk component operation. Untuk memproses seluruh mesh, cukup pilih mesh object.
3. Atur Blend dan Iterations.
4. Klik **Flood**.

Jika component dipilih, hanya component scope yang berhasil di resolve yang akan diproses. Pada mode ini juga bisa menggunakan Maya Soft Selection, hasilnya akan terpengaruh oleh falloffnya. Jika object loaded mesh yang dipilih, maka tool akan meminta konfirmasi sebelum memproses seluruh mesh.

Dengan Iterations `0`, Flood menulis hard regional result. Iterations menerapkan smoothing pada affected region menggunakan nilai Blend saat ini. Pending Joints yang ikut dipilih bersama bind influence akan diabaikan; jika ingin menambahkan Pending Joints gunakan Add Influence untuk joint. Selected Flood target harus dalam keadaan unlocked, jika terkunci makan nilai influence lain tetap terlindungi.

{{< collapse title="Flood demonstration" collapse="true">}}
![Flood demonstration](/images/documentation/ad-skin-tools/05-flood.gif)
{{< /collapse >}}

## Smooth

Smooth meratakan skin weight saat ini pada component selection atau pada seluruh loaded mesh.

1. Di Maya, pilih vertex, edge, atau face pada loaded mesh. Untuk melakukan smooth pada seluruh mesh, pilih loaded mesh object.
2. Atur Blend dan set Iterations ke `1` atau lebih.
3. Klik **Smooth**.

Smooth tidak memerlukan joint row untuk dipilih. Component mode mengikuti Maya Soft Selection falloff. Untuk object mode menampilkan konfirmasi sebelum diproses. Nilai locked influence tetap tidak berubah dan vertex yang tidak memiliki writable weight akan dilewati.

{{< collapse title="Smooth demonstration" collapse="true">}}
![Smooth demonstration](/images/documentation/ad-skin-tools/06-smooth.gif)
{{< /collapse >}}

## Skin Weight Visual

Skin Weight Visual menampilkan weight dari satu bind influence langsung pada loaded mesh tanpa mengubah skin weight yang tersimpan.

1. Load mesh yang sudah memiliki skinCluster.
2. Pilih tepat satu bind influence di dalam list.
3. Pilih display mode:
   - **Spectrum:** hitam, biru, hijau, kuning, oranye, merah, dan putih.
   - **Heat:** hitam, merah, oranye, kuning, dan putih.
   - **Grayscale:** hitam melalui abu-abu hingga putih.
4. Pilih **Off** untuk mengembalikan normal mesh shading.

Jika **Live Joint Selection** diset ke **On**, memilih listed bind joint di Maya scene juga akan memilih dan menampilkannya dalam UI list serta memperbarui weight visual yang aktif. Set ke **Off** jika Anda ingin displayed influence tetap sama ketika Maya scene selection berubah.

Visual akan diperbarui setelah weight operation yang relevan, Undo, dan Redo. Ini adalah temporary display session dan tidak melakukan bake colour data ke dalam skin weight.

{{< collapse title="Skin Weight Visual demonstration" collapse="true">}}
![Skin Weight Visual demonstration](/images/documentation/ad-skin-tools/07-skin-weight-visual.gif)
{{< /collapse >}}

## Mirror Skin Weights Posed Mesh

Mirror menggunakan persistent vertex pairing agar dapat bekerja secara konsisten pada skinned mesh yang sedang dalam posed state. Pairing diregistrasikan dari bind-reference geometry jika tersedia, sehingga karakter tidak perlu dikembalikan ke bind pose hanya untuk menerapkan mirrored weight.

### Register mirror pairing

1. Pilih mesh yang akan di mirror, kemudian klik **Load Mirror Mesh**. Context ini terpisah dari context utama Load Mesh.
2. Pilih symmetry plane:
   - **YZ** melakukan mirror melintasi X.
   - **XZ** melakukan mirror melintasi Y.
   - **XY** melakukan mirror melintasi Z.
3. Pilih **Direction** source-to-target pada axis tersebut.
4. Atur centre plane coordinate. Anda dapat mengetik nilainya langsung, atau memilih centre component yang sesuai maupun mesh transform lalu klik **Register Selected** untuk menghitungnya dari selection.
5. Atur **Tolerance**. Mulai dari nilai default `0.001`; naikkan secukupnya untuk menemukan symmetrical counterpart yang valid.
6. Masukkan literal joint name marker untuk **Left** dan **Right**, misalnya `L` / `R`, `L_` / `R_`, atau `_l` / `_r`. Marker dapat berupa prefix, suffix, atau infix, tetapi keduanya harus berbeda.
7. Klik **Preview Pairing**.

Preview menampilkan jumlah legal pair, centre vertex, unmatched vertex, ambiguous vertex, dan maximum pairing error. Problem vertex dipilih di Maya agar dapat diperiksa. Preview tidak menimpa registered pairing yang sudah ada.

Setelah Preview lengkap dan valid, klik **Register Pairing**. Geometry pairing disimpan pada mesh dan dapat digunakan kembali. Jika mesh sudah memiliki pairing data, tombol berubah menjadi **Replace Pairing...** dan meminta konfirmasi sebelum menggantinya. Perubahan topology akan membuat pairing lama obsolete; jalankan kembali Preview dan Replace Pairing.

### Terapkan mirrored weights

1. Load mirror mesh yang memiliki registered pairing valid dan skinCluster.
2. Atur Direction dan pastikan Left/Right marker benar.
3. Untuk mode seluruh mesh, jangan memilih mesh component atau pilih seluruh registered region.
4. Untuk mode component selection, pilih donor component hanya dari satu sisi. Registered counterpart akan menjadi target.
5. Klik **Mirror Skin Weights**.

Direction yang dipilih menentukan sisi yang mendonorkan weight. Joint influence dipasangkan menggunakan literal Left/Right marker. Nilai locked target influence tetap dipertahankan. Jangan memilih kedua sisi dari mirror region yang sama dalam component mode.

Tombol **Reset** pada Mirror membersihkan active Mirror Mesh dan current UI option. Reset tidak menghapus persistent pairing yang sudah tersimpan pada mesh.

{{< collapse title="Mirror demonstration" collapse="true">}}
![Mirror demonstration](/images/documentation/ad-skin-tools/08-mirror.gif)
{{< /collapse >}}

## Transfer Skin Weights

Transfer memproyeksikan weight dari satu atau beberapa skinned source surface ke satu atau beberapa target mesh. Source adalah canonical donor: target influence dan weight diresolve dari registered source.

### Register source dan target

1. Pilih satu atau beberapa skinned source mesh, kemudian klik **Add Selected** di bagian **Sources**. Source component boleh dipilih, tetapi owning meshnya yang diregistrasikan sebagai donor surface.
2. Pilih satu atau beberapa target mesh atau componentnya, kemudian klik **Add Selected** di bagian **Targets**. Registration menyimpan owning target mesh; active component scope baru dievaluasi ketika Preview Transfer dijalankan.
3. Gunakan **Remove Selected** atau **Clear** untuk mengubah masing-masing list. Satu mesh tidak dapat diregistrasikan sebagai source sekaligus target.

Klik kanan pada salah satu list untuk memilih highlighted object atau semua registered object di list tersebut di Maya scene.

### Memahami target scope

Registered Target list menentukan mesh mana yang berpartisipasi. Maya component selection ketika Preview dijalankan hanya mengubah scope untuk registered target yang sesuai:

| Kondisi target saat Preview | Scope yang digunakan |
|---|---|
| Tidak ada component yang dipilih pada registered target | Seluruh target mesh diproses |
| Component dipilih pada registered skinned target | Hanya selected target vertex yang diproses |
| Component dipilih pada unskinned target | Component target dilewati dan harus di-bind terlebih dahulu |
| Unskinned target digunakan sebagai whole object | Target skinCluster baru dapat dibuat saat Apply |

Mixed scope, artinya dalam satu operasi, satu target dapat menggunakan selected component sementara registered target lain tetap menggunakan whole object. Component dari unregistered mesh tidak akan memasukkan mesh tersebut ke dalam transfer.

### Preview dan Apply

1. Atur target component selection yang diinginkan, atau biarkan registered target tanpa component untuk object mode.
2. Klik **Preview Transfer**.
3. Periksa status summary: registered, active, dan skipped target; requested dan writable vertex; locked atau empty row; serta maximum source distance.
4. Jika Preview valid, klik **Transfer Skin Weights**.

Preview menghitung dan menyimpan exact closest-source correspondence yang akan digunakan oleh Apply; Preview tidak menulis weight. Jika source atau target registration, target component scope, skinCluster, atau influence order berubah setelah Preview, jalankan Preview kembali.

Saat Apply:

- Object unskinned target akan menerima skinCluster baru.
- Source influence yang belum ada pada existing target akan ditampilkan sebelum ditambahkan.
- Locked target influence akan ditampilkan dan dilewati sehingga nilainya tidak berubah.
- Jika salah satu kondisi tersebut ada, tool menampilkan **Cancel** dan **Proceed**. Cancel mempertahankan Preview dan tidak melakukan perubahan.
- Transfer dan adaptive boundary smoothing diterapkan sebagai satu operasi. Multi-target operation yang gagal akan di roll back agar tidak meninggalkan partial result.

Tombol **Reset** pada Transfer membersihkan registered Source dan Target list serta Preview saat ini. Reset tidak membatalkan transfer yang sudah diterapkan; gunakan Maya Undo untuk itu.

{{< collapse title="Transfer demonstration" collapse="true">}}
![Transfer demonstration](/images/documentation/ad-skin-tools/09-transfer.gif)
{{< /collapse >}}

## Status, Undo, dan diagnostics

Setiap operasi menampilkan hasil singkat di bawah sectionnya dan mencetak report yang lebih terperinci di Maya Script Editor. Baca keduanya ketika Preview bersifat partial atau ketika vertex dilewati karena lock, tidak adanya writable donor weight, unmatched geometry, atau component scope yang tidak valid.

Operasi Bind, Add Influence, Flood, Smooth, Mirror, dan Transfer yang sudah diterapkan mengikuti Maya Undo workflow. Jika hasil tidak sesuai dengan yang diinginkan, gunakan Maya Undo sebelum melanjutkan pengeditan yang lain.

Untuk meminta support, buka **Tool Help**, klik **Copy Diagnostics**, lalu sertakan environment report yang disalin bersama penjelasan singkat mengenai masalahnya. Jangan sertakan confidential production asset atau licence key lengkap. Support tersedia melalui [hello@adiendendra.com](mailto:hello@adiendendra.com).
