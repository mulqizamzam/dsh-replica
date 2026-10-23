# Panduan Pemula — DSH Replica

Panduan ini ditujukan untuk pengguna yang baru mulai memakai **DeepSeek Harness (DSH)** dan ingin memahami proyek DSH Replica dari awal.

## 1. Apa itu DSH Replica?

DSH Replica adalah kumpulan 11 alur kerja untuk membantu merancang dan membangun **produk baru dengan fungsi serupa** aplikasi referensi. Alurnya mencakup riset fitur, arsitektur teknis, desain, implementasi, pengujian, branding, peluncuran, dan persiapan deployment.

Proyek ini tidak dimaksudkan untuk menyalin kode sumber, logo, tulisan, aset berlisensi, katalog, atau API privat milik aplikasi lain. Gunakan sumber publik yang boleh diakses dan akun milik Anda sendiri.

## 2. Status repo saat ini — baca sebelum instalasi

Repo GitHub ini sedang disiapkan. Pada saat panduan ini ditulis, source bundle lengkap **belum** ada di GitHub; repo baru berisi dokumentasi awal. Karena itu, mengkloning repo ini saja belum cukup untuk memasang plugin.

Jangan jalankan perintah instalasi dari repo ini sebelum folder dan berkas proyek lengkap tersedia. Bila Anda menerima arsip source lengkap dari pengelola proyek, ekstrak arsip tersebut ke folder kerja tersendiri. Setelah seluruh source dipublikasikan ke GitHub, bagian ini dapat diperbarui menjadi prosedur instalasi yang langsung bisa diikuti.

## 3. Istilah dasar

- **DSH / DeepSeek Harness:** lingkungan tempat plugin dan skill digunakan.
- **Skill:** instruksi terfokus untuk menyelesaikan satu jenis pekerjaan. DSH Replica membundel sebelas Skill.
- **Bundle/plugin:** paket yang mendaftarkan Skill agar dapat ditemukan dan dimuat oleh Harness.
- **Clean-room rebuild:** membuat implementasi baru berdasarkan pemahaman atas fungsi dan alur, bukan menyalin kode atau aset aplikasi referensi.
- **Preflight:** daftar pemeriksaan yang harus lulus sebelum merilis atau melakukan deployment.

## 4. Alur kerja yang disarankan

Jangan mencoba membangun seluruh aplikasi sekaligus. Mulailah dari lingkup kecil dan jalankan alurnya secara bertahap:

1. **Recon (replica-recon)** — pilih platform dan fitur inti, lalu dokumentasikan layar, alur pengguna, sumber referensi, serta daftar fitur.
2. **Arsitektur (replica-architect)** — tentukan stack, skema data, API, aturan akses, dan urutan pengerjaan.
3. **Desain (replica-design)** — buat token warna, tipografi, jarak, komponen, dan cek kontras.
4. **Build (replica-build)** — bangun satu alur utama sampai berfungsi sebelum menambah semua layar.
5. **Backend (replica-backend)** — implementasikan autentikasi, database, pembayaran, email, dan integrasi melalui API resmi.
6. **Testing (replica-test)** — uji alur normal dan kasus gagal; catat bug dengan bukti.
7. **Parity (replica-diff)** — ukur fitur yang sudah selesai dan daftar yang masih kurang.
8. **Riset masukan (replica-entrepreneur)** — analisis ulasan publik yang nyata dan tertaut; jangan mengarang kutipan atau angka.
9. **Branding (replica-brand)** — buat nama, warna, dan suara brand Anda sendiri; periksa sisa identitas aplikasi referensi.
10. **Peluncuran (replica-launch)** — siapkan landing page, harga, dan listing dengan klaim yang dapat dibuktikan.
11. **Deployment (replica-deploy)** — jalankan seluruh preflight. Jangan menerbitkan apa pun ke produksi tanpa persetujuan eksplisit dari pemilik proyek.

Skill dapat dipakai terpisah bila pekerjaan memang hanya memerlukan satu langkah, tetapi artefak yang dihasilkan tiap langkah sebaiknya disimpan dan diperbarui secara konsisten.

## 5. Contoh permintaan untuk memulai

Setelah bundle lengkap dipasang dan Skill tersedia di DSH, Anda dapat meminta dengan bahasa biasa, misalnya:

- “Bantu saya memetakan fitur inti aplikasi penjadwalan dari halaman dokumentasi publik. Buat daftar sumber dengan URL dan bedakan fakta dari dugaan.”
- “Baca hasil recon dan sarankan arsitektur sederhana untuk MVP. Jelaskan trade-off setiap pilihan.”
- “Buat token desain yang orisinal dan periksa kontras aksesibilitasnya.”
- “Buat rencana pengujian untuk alur registrasi dan pemesanan, termasuk kasus gagal.”
- “Audit kesiapan rilis. Jangan deploy atau mengubah layanan produksi tanpa izin saya.”

Berikan konteks yang cukup: aplikasi/platform, siapa pengguna produk baru, fitur yang akan dibangun, stack yang sudah dipakai, dan batasan waktu/biaya.

## 6. Persyaratan dan pemeriksaan lokal

Alat Python proyek dirancang menggunakan standard library dan membutuhkan **Python 3.8 atau lebih baru**. Jika Anda mengembangkan atau menjalankan source Harness dari checkout-nya, manifest Harness yang diperiksa pada saat porting mensyaratkan **Node.js 22.19.x atau lebih baru dalam jalur 22.x, atau Node.js 24.x ke atas**. Kebutuhan runtime dapat berubah; periksa dokumentasi versi Harness yang Anda gunakan.

Setelah source lengkap tersedia, dari direktori root proyek, jalankan pemeriksaan yang disertakan:

~~~bash
python scripts/validate_dsh_plugin.py .
python -m unittest discover -s tests -v
node tests/test_provider.mjs
python skills/replica-design/contrast.py skills/replica-design/tokens.json
~~~

Jika perintah gagal, baca pesan error dan perbaiki penyebabnya. Jangan melewati preflight hanya untuk membuat rilis tampak hijau. Jika Anda baru mengunduh repo ini dan perintah/berkas tersebut belum ada, itu sesuai dengan status repo yang belum lengkap—jangan membuat berkas pengganti secara manual.

## 7. Keamanan dan hal yang tidak boleh dilakukan

- Jangan minta atau menyimpan password, token API, kartu pembayaran, atau kredensial produksi dalam chat, berkas source, atau log.
- Gunakan API publik/resmi sesuai persyaratannya; jangan mengakses endpoint privat aplikasi referensi.
- Jangan melakukan scraping massal atau pengujian beban pada aplikasi referensi.
- Semua ulasan, angka, dan kutipan harus berasal dari bukti yang nyata dan menyertakan URL.
- Referensi screenshot hanya untuk analisis dan tidak boleh ikut dikirim sebagai aset produk baru.
- Jangan memakai logo, tulisan, ilustrasi, foto, font berlisensi, atau identitas brand milik aplikasi referensi tanpa hak yang sesuai.
- Pastikan brand baru telah diperiksa; hasil pemeriksaan nama bukan jaminan legalitas.
- Jangan melakukan deployment produksi sampai test, parity, brand sweep, listing checks, dan pemeriksaan operasional lulus serta Anda menyetujui langkah go-live.

## 8. Di mana mencari bantuan?

- [Repo DSH Replica](https://github.com/mulqizamzam/dsh-replica)
- [Repo resmi DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness)
- [Repo asal Replica Skill Pack](https://github.com/Jakeschincariol/replica-skill) — sumber alur kerja berlisensi MIT.

Jika Anda menemukan bug, sertakan versi DSH, sistem operasi, perintah yang dijalankan, pesan error yang relevan, serta langkah reproduksi. Hapus rahasia/kredensial dari log sebelum membagikannya.

## Lisensi dan atribusi

Proyek sumber memakai lisensi MIT. Pertahankan pemberitahuan lisensi dan atribusi upstream pada distribusi turunan. DSH Replica bukan produk resmi atau proyek yang didukung DeepSeek.
