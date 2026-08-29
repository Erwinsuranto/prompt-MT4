# prompt-MT4

# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```
Lanjutkan project mt-info dari kondisi repository SAAT INI.

Jangan mengulang baseline yang sudah selesai. Jangan mengubah strategi trading, dataset, atau membuat synthetic data.

Prioritas sekarang:

1. Selesaikan perubahan bridge.py yang saat ini masih uncommitted.
   - Perubahan tersebut sudah diverifikasi:
     - versi final: 23 test OK
     - full suite: 398 passed
   - Pastikan test baru untuk regression Bug 3 dan Bug 4 tetap ada.
   - Jalankan test yang relevan dan full test suite.
   - Jika semuanya tetap PASS, commit perubahan tersebut.
   - Gunakan commit message:
     fix(bridge): retry undelivered signals and survive filesystem races

2. Setelah commit berhasil, audit python/xausr/telegram.py.
   Fokus hanya pada masalah yang sudah ditemukan:
   - coverage sekitar 50%
   - Exception handling pada send()
   - kegagalan kirim Telegram jangan menyebabkan signal hilang tanpa retry
   - periksa apakah ada filesystem/network race atau partial failure yang perlu ditangani
   - jangan mengubah kontrak API yang sudah ada tanpa alasan
   - jangan membuat behavior baru yang tidak diperlukan

3. Tambahkan unit test yang benar-benar membuktikan bug/behavior yang ditemukan.
   - Jangan membuat test dekoratif hanya untuk menaikkan coverage.
   - Test harus menguji behavior nyata.
   - Jangan membutuhkan koneksi Telegram/network nyata.
   - Gunakan mock/fake dependency jika diperlukan.

4. Jalankan:
   - test telegram yang relevan
   - full test suite

5. Jangan commit perubahan telegram.py dulu jika masih ada failure atau behavior belum jelas.
   Jika test semuanya PASS, laporkan perubahan dan tunggu instruksi saya sebelum commit.

Strict rules:
- Jangan menyentuh dataset XAUUSD.
- Jangan membuat synthetic market data.
- Jangan mengubah setup A/B/C/D.
- Jangan menambah indikator trading.
- Jangan melakukan auto-trading.
- Jangan membuat Telegram signal baru.
- Jangan mengubah threshold strategi.
- Jangan mengklaim akurasi.
- Jangan menggunakan network Telegram nyata untuk test.
- Jangan menjalankan test Gorouter.app.
- NVIDIA dan TokenHarbor.ai tidak perlu disentuh pada tahap ini.

Di akhir, tampilkan ringkasan:
1. commit bridge berhasil atau tidak
2. file telegram.py yang berubah
3. test yang ditambahkan
4. hasil full test suite
5. status git
6. langkah berikutnya yang paling aman

Kerjakan langsung dari repository /root/mt-info dan jangan berhenti hanya untuk meminta konfirmasi pada langkah yang sudah jelas di atas.
```
# 
```
Lanjutkan project mt-info dari kondisi sekarang.

Prioritas:
1. Jangan mengubah dataset, threshold, strategy, indikator, keputusan A/B/C/D/E, atau baseline yang sudah terbukti.
2. Jangan membuat data XAUUSD sintetis/palsu dan jangan mengklaim hasil yang belum bisa diverifikasi.
3. Fokus hanya pada pekerjaan yang bisa dilakukan di VPS saat ini.
4. Periksa kembali perubahan bridge.py dan tests/test_bridge.py yang saat ini masih uncommitted.
5. Jalankan test suite lengkap dengan environment project:
   PYTHONPATH=.venv/bin/python -m pytest -q
   dan juga:
   cd python && PYTHONPATH=. ../.venv/bin/python -m unittest discover -s tests
   Gunakan command yang benar sesuai struktur project jika path tersebut berbeda.
6. Pastikan perubahan bridge.py benar-benar memperbaiki partial-write handling, retry untuk sinyal yang belum terkirim, dan filesystem trace/malformed line handling tanpa merusak behavior yang sudah ada.
7. Jangan commit atau push dulu.
8. Setelah selesai, tampilkan:
   - file yang berubah
   - ringkasan perubahan
   - hasil seluruh test
   - apakah working tree clean atau masih ada perubahan
   - apa next step yang paling aman.
9. Jika ada masalah yang membutuhkan MT5/Windows atau dataset XAUUSD tambahan, jangan workaround dengan data sintetis. Berhenti pada blocker tersebut dan jelaskan persis apa yang dibutuhkan.

Kerjakan langsung, satu tahap yang aman, lalu laporkan hasilnya.
```
# 
```
Lanjutkan project /root/mt-info dari kondisi saat ini.

Fokus hanya memperbaiki bug pada python/xausr/bridge.py dan test yang berkaitan dengan bridge.

Kondisi terakhir:
- Ada perubahan: M python/xausr/bridge.py
- Ada file baru: ?? python/tests/test_bridge.py
- Sebelumnya ditemukan 3 failures dan 2 errors pada test suite.
- Bug yang sedang ditangani berkaitan dengan partial write / malformed lines dan signal yang bisa ter-drop.
- Jangan menyentuh dataset XAUUSD, benchmark, threshold, decision A/B/C/D/E, atau konfigurasi penelitian.
- Jangan melakukan perubahan yang tidak diperlukan di luar area bridge.
- Jangan menghapus test hanya agar suite menjadi hijau.
- Pertahankan behavior API yang sudah benar.

Tugas:
1. Baca implementasi bridge.py secara lengkap.
2. Baca python/tests/test_bridge.py dan test bridge lain yang relevan.
3. Jalankan test yang relevan terlebih dahulu untuk mendapatkan failure/error aktual.
4. Identifikasi akar masalah, bukan sekadar menyesuaikan test.
5. Perbaiki implementasi bridge agar aman terhadap partial write, malformed/incomplete lines, dan kondisi input yang sebelumnya menyebabkan signal hilang tanpa retry.
6. Pastikan error handling tidak membuat data valid ikut ter-drop.
7. Tambahkan/perbaiki regression test untuk setiap bug yang benar-benar ditemukan.
8. Setelah perubahan, jalankan test bridge terlebih dahulu, lalu full test suite:
   python3 -m pytest tests -q
9. Jangan commit atau push dulu.
10. Laporkan dengan jelas:
   - akar masalah
   - file yang berubah
   - test yang ditambahkan/diperbaiki
   - hasil test bridge
   - hasil full test
   - apakah working tree clean atau masih ada perubahan.

Berhenti setelah verifikasi selesai. Jangan mengerjakan dataset XAUUSD.
```
# 
```
Lanjutkan project mt-info dari kondisi saat ini.

Jangan mengubah baseline yang sudah terbukti stabil:
- commit/HEAD tetap 60fe529
- 375 tests harus tetap passed
- jangan membuat perubahan hanya untuk memaksakan commit
- jangan membuat dataset XAUUSD sintetis/palsu
- jangan menjalankan atau bergantung pada MetaTrader5 di VPS Linux
- jangan mengklaim hasil benchmark baru tanpa data nyata

Tugas tahap berikutnya:
1. Inspect seluruh repository dan dokumentasi yang ada.
2. Identifikasi bagian project yang saat ini sudah siap dikembangkan tanpa membutuhkan dataset XAUUSD tambahan.
3. Pilih SATU peningkatan paling bernilai yang bisa benar-benar dikerjakan dan diverifikasi di VPS ini.
4. Implementasikan peningkatan tersebut secara production-quality dengan perubahan seminimal mungkin.
5. Tambahkan/update test yang relevan.
6. Jalankan test suite yang sesuai dan pastikan baseline tidak rusak.
7. Tampilkan ringkasan:
   - file yang berubah
   - apa yang diimplementasikan
   - test yang dijalankan dan hasilnya
   - apakah perlu commit
   - keputusan/next step berikutnya

Penting:
Jangan langsung mengubah banyak hal atau membuat fitur spekulatif.
Sebelum coding, pahami arsitektur dan kondisi repository saat ini.
Jika tidak ada peningkatan yang aman untuk dikerjakan tanpa data XAUUSD, jangan memaksakan perubahan; cukup laporkan blocker dan rekomendasikan satu langkah paling tepat berikutnya.
```
# 
```
Kita lanjut project mt-info di VPS baru.

Tujuan tahap ini hanya memastikan environment VPS baru siap dan baseline project bisa direproduksi IDENTIK dengan VPS sebelumnya.

Kerjakan berurutan:

1. Pastikan berada di /root/mt-info.
2. Cek:
   - git status
   - git log -1 --oneline
   - git remote -v
   - python3 --version
   - pip/python environment yang tersedia
3. Baca struktur project dan requirements/dependency yang memang sudah ada.
4. Install hanya dependency yang diperlukan untuk menjalankan test existing. Jangan menambah library yang tidak diperlukan.
5. Jangan mengubah source code, strategi, indikator, threshold, dataset, konfigurasi keputusan, atau file benchmark.
6. Jalankan test suite existing dari direktori yang benar.
7. Jika test gagal karena dependency/environment, perbaiki environment saja tanpa mengubah logic project, lalu jalankan ulang.
8. Setelah test selesai, bandingkan hasil dengan baseline sebelumnya:
   - target: 375 passed, 0 failed, 0 error, 0 skipped
   - commit harus tetap 60fe529 (atau commit HEAD yang sedang terpasang jika hash ternyata berbeda tetapi isi identik)
9. Jangan commit/push apa pun karena tahap ini hanya validasi environment VPS baru.
10. Berikan laporan akhir:
   - environment
   - commit HEAD
   - hasil test
   - apakah baseline berhasil direproduksi
   - apakah VPS siap untuk tahap berikutnya.

PENTING: jangan membuat perubahan pada strategi atau indikator. Jika ada masalah yang membutuhkan data MT5/XAUUSD tambahan, berhenti dan laporkan masalahnya, jangan membuat data sintetis atau mengganti dataset.
```
# 
```
Lanjutkan setup project /root/mt-info di VPS baru.

Tujuan tahap ini hanya memastikan environment VPS baru siap menjalankan project secara reproducible. JANGAN menambah strategi, indikator, rule keputusan, threshold, atau mengubah source code yang sudah ada.

Kerjakan berurutan:

1. Periksa repository:
   - pwd
   - git status
   - git branch --show-current
   - git log -1 --oneline
   - git remote -v

2. Periksa environment:
   - python3 --version
   - python3 -m pip --version
   - pytest --version jika tersedia
   - periksa apakah ada requirements.txt, pyproject.toml, atau konfigurasi dependency lain.

3. Jika dependency Python belum tersedia, install dependency yang memang didefinisikan project secara minimal dan reproducible.
   Jangan install dependency yang tidak diperlukan.

4. Periksa struktur project dan pastikan file benchmark yang sudah ada tetap utuh, terutama:
   - python/xausr/
   - python/xausr/driftbench.py
   - python/xausr/benchmark.py
   - python/xausr/precompute.py
   - python/xausr/backtest.py
   - python/xausr/baseline.py
   - python/xausr/experiments.py
   - python/xausr/mql5/
   - docs/DATA.md
   - tests/

5. Jalankan baseline test yang sama seperti sebelumnya dari root repository:
   python3 -m pytest tests -q

6. Bandingkan hasil dengan checkpoint sebelumnya:
   375 passed, 0 failed, 0 error, 0 skipped.

7. Jika hasil berbeda, JANGAN memperbaiki kode secara spekulatif. Investigasi penyebab environment/dependency terlebih dahulu dan laporkan perbedaannya.

8. Jika hasil sama, buat laporan singkat bahwa VPS baru sudah reproducible dan siap untuk tahap berikutnya.

9. Jangan melakukan git commit/push pada tahap ini kecuali memang ada perubahan file yang benar-benar diperlukan untuk memperbaiki environment. Jika tidak ada perubahan, biarkan working tree clean.

PENTING:
- Jangan menjalankan atau mengubah strategi trading.
- Jangan membuat indikator baru.
- Jangan mengubah threshold.
- Jangan mengubah hasil benchmark.
- Jangan memakai data sintetis untuk menggantikan data MT5.
- Jangan mengklaim sinyal lebih akurat sebelum dataset XAUUSD tambahan benar-benar tersedia dan diuji.

Berhenti setelah verifikasi selesai dan tampilkan hasil lengkap:
environment, commit, test result, working tree, dan apakah VPS baru siap lanjut.

```
# 
```

```
# Tahap 1: export histori XAUUSD lebih panjang → verify → jalankan ulang drift benchmark.
```
Lanjutkan tahap berikutnya sesuai rekomendasi terakhir.

Tujuan tahap ini:
1. Periksa terlebih dahulu environment dan kondisi repo saat ini.
2. Jangan mengubah strategi, threshold, rule keputusan, atau menambah indikator baru.
3. Jangan mengarang data atau hasil eksperimen.
4. Verifikasi apakah tool `xausr.mt5_export` dan sumber data XAUUSD tersedia di environment VPS ini.
5. Jika tersedia, export histori XAUUSD yang lebih panjang dengan mode verifikasi (`--verify`) sesuai interface/tool yang benar-benar ada.
6. Setelah export berhasil, periksa integritas data, rentang tanggal, jumlah sample, timezone, missing/duplicate data, dan pastikan tidak ada leakage.
7. Jalankan ulang drift-neutral benchmark menggunakan dataset baru tersebut.
8. Bandingkan hasil baru dengan baseline commit yang sekarang. Jangan mengubah baseline secara diam-diam.
9. Fokus evaluasi khusus pada setup D Breakdown+Retest dan E Engine pooled karena keduanya sebelumnya `INSUFFICIENT EVIDENCE`.
10. Untuk A Resistance Rejection, tetap pertahankan status `WATCHLIST` sampai ada bukti independen untuk mengubahnya.
11. Jangan memasukkan setup baru dan jangan melakukan tuning hanya agar hasil terlihat lebih bagus.
12. Jalankan test suite yang relevan setelah perubahan.
13. Jika ada perubahan kode/data yang memang diperlukan, tampilkan file yang berubah dan alasan perubahan sebelum commit.
14. Jika environment VPS ini tidak memiliki akses MT5/data XAUUSD yang diperlukan, BERHENTI dan laporkan blocker secara jelas. Jangan membuat data sintetis sebagai pengganti.

Di akhir berikan laporan ringkas:
- status environment
- rentang histori XAUUSD
- jumlah sample
- hasil integrity/leakage check
- hasil benchmark terbaru
- keputusan A/B/C/D/E
- perbandingan dengan baseline
- test result
- apakah aman untuk lanjut ke tahap berikutnya

Jangan commit atau push sebelum saya instruksikan.
```

# 
```
Lanjutkan project mt-info dari checkpoint repository yang sekarang.

Konteks:
- Ini VPS baru hasil clone repository mt-info.
- Jangan membuat ulang atau mengubah desain project yang sudah ada.
- Checkpoint terakhir sudah tervalidasi: 375 passed, 0 failed, 0 error, 0 skipped.
- Commit terakhir yang menjadi baseline adalah 60fe529... ("feat: reproducible drift-neutral benchmark, plus its research scaffolding").
- Keputusan benchmark terakhir harus tetap dipertahankan:
  A Resistance Rejection = WATCHLIST
  B Breakout+Retest = DISABLED
  C Support Rejection = DISABLED
  D Breakdown+Retest = INSUFFICIENT EVIDENCE
  E Engine pooled = INSUFFICIENT EVIDENCE

Tugas tahap ini:
1. Verifikasi repository dan branch saat ini.
2. Verifikasi commit HEAD dan remote origin.
3. Periksa struktur project dan dependency yang dibutuhkan.
4. Siapkan environment VPS baru tanpa mengubah source code secara tidak perlu.
5. Jalankan test suite yang memang tersedia dari repository untuk memastikan baseline dapat direproduksi di VPS baru.
6. Bandingkan hasil dengan checkpoint terakhir.
7. Periksa git status dan pastikan tidak ada perubahan kode yang tidak disengaja.
8. Jangan mengubah keputusan benchmark.
9. Jangan menambah strategi/indikator baru pada tahap ini.
10. Jangan mengklaim PASS berdasarkan percakapan sebelumnya; gunakan hasil runner aktual dari VPS ini.
11. Jika ada dependency/environment issue, perbaiki hanya yang diperlukan untuk menjalankan project, lalu ulangi verifikasi.
12. Setelah selesai, tampilkan ringkasan:
   - commit HEAD
   - branch
   - hasil test aktual
   - perubahan file
   - apakah baseline identik dengan checkpoint sebelumnya
   - rekomendasi tepat untuk tahap berikutnya.

Kerjakan langsung di repository yang sedang aktif. Jangan hanya menjelaskan perintah; jalankan verifikasinya.
```
# 
```
Sekarang lakukan CHECKPOINT FINAL dan jangan mengubah desain/strategi/kode lagi.

Tujuan tahap ini hanya mengamankan seluruh pekerjaan yang sudah selesai ke Git.

1. Pastikan berada di repository /root/mt-info.
2. Jalankan:
   git status
   git diff
   git diff --stat
3. Pastikan seluruh perubahan hasil pekerjaan benchmark/drift-neutral yang memang merupakan bagian dari pekerjaan ini ikut terdeteksi.
4. Jangan membuat perubahan kode baru, jangan melakukan refactor, jangan menambah indikator, strategi, threshold, scoring, atau eksperimen baru.
5. Jalankan test suite yang relevan sekali lagi hanya untuk memastikan checkpoint bersih.
6. Jika semua test PASS, buat commit dengan pesan yang jelas, misalnya:
   "Add drift-neutral benchmark and validated setup decisions"
7. Push commit tersebut ke remote branch yang sedang digunakan.
8. Setelah push, verifikasi:
   git status
   git log -1 --oneline
   git remote -v
9. Pastikan working tree bersih dan commit yang baru benar-benar sudah berada di remote.
10. Laporkan secara ringkas:
   - jumlah test terakhir
   - commit hash
   - branch
   - apakah push berhasil
   - apakah working tree clean

PENTING:
- Jangan mengubah hasil keputusan yang sudah ada.
- Jangan menghapus test.
- Jangan skip test.
- Jangan membuat file eksperimen baru.
- Jangan melakukan pekerjaan lanjutan setelah checkpoint.
- Jika ada masalah autentikasi Git atau push gagal, BERHENTI dan jelaskan error-nya; jangan mengubah konfigurasi Git secara sembarangan.

Berhenti setelah checkpoint Git berhasil dan working tree clean.

```
# 
```
Lanjutkan dari state repository /root/mt-info saat ini.

TUGAS TAHAP INI: FINALIZE + INTEGRITY CHECK + COMMIT + PUSH.
Jangan menambah strategi baru, indikator baru, filter baru, threshold baru, atau mengubah hasil benchmark.

Konteks hasil terakhir:
- 375 passed pada kedua runner, 0 failed, 0 error, 0 skipped.
- drift-neutral benchmark sudah selesai.
- A Resistance Rejection = WATCHLIST.
- B Breakout+Retest = DISABLED.
- C Support Rejection = DISABLED.
- D Breakdown+Retest = INSUFFICIENT EVIDENCE.
- E Engine pooled = INSUFFICIENT EVIDENCE.
- Tidak boleh mengubah keputusan tersebut tanpa bukti baru.
- reports/ tetap git-ignored dan jangan dipaksa masuk commit.

Kerjakan secara berurutan:

1. Periksa git status dan git diff HEAD.
2. Pastikan perubahan yang ada hanya perubahan yang memang berasal dari tahap benchmark/drift-neutral dan tidak ada accidental change.
3. Jalankan test suite yang relevan sekali lagi sebagai final verification.
4. Verifikasi tidak ada test yang dihapus, di-skip, atau dilemahkan.
5. Verifikasi integritas CSV/report dan bahwa hasil benchmark konsisten dengan HEAD.
6. Periksa tidak ada secret, credential, atau file sementara yang akan ikut commit.
7. Tampilkan ringkasan file yang akan di-commit dan hasil test.
8. Jika semuanya bersih, buat satu commit yang jelas untuk menyimpan checkpoint tahap ini.
9. Push commit tersebut ke remote branch yang sedang digunakan.
10. Setelah push berhasil, tampilkan:
   - commit hash
   - branch
   - push status
   - test result
   - git status final

PENTING:
- Jangan melakukan refactor besar.
- Jangan melakukan tuning.
- Jangan menambah indikator/strategi.
- Jangan mengubah baseline hanya agar hasil terlihat lebih bagus.
- Jangan mengarang angka.
- Jangan commit reports/ yang memang di-ignore.
- Jika ada masalah sebelum commit/push, BERHENTI dan jelaskan masalahnya; jangan memperbaikinya dengan perubahan spekulatif.

Tujuan tahap ini hanya satu: membuat checkpoint Git yang bersih dan dapat direproduksi sebelum VPS dipindahkan.
```
# 
```
Lanjutkan pekerjaan dari state repository AKTUAL ini. Jangan mengandalkan klaim PASS/FAIL dari percakapan sebelumnya.

WAJIB:
1. Pastikan current directory benar-benar /root/mt-info dan merupakan Git repository.
2. Audit kondisi aktual:
   - git status
   - git diff
   - git log -5 --oneline
   - struktur python/ dan tests/
   - docs/DATA.md
   - data CSV yang menjadi baseline
3. Baca kode nyata sebelum mengambil keputusan, terutama:
   - python/xausr/backtest.py
   - python/xausr/config.py
   - python/xausr/continuation.py
   - python/xausr/stats.py
   - seluruh test yang relevan
4. Jalankan test suite dari root repository dan laporkan hasil aktualnya.
5. Lanjutkan Stage berikutnya sesuai arah pekerjaan sebelumnya: bangun benchmark drift-neutral yang benar-benar berbasis data dan kode aktual, bukan angka buatan atau asumsi.
6. Benchmark harus memisahkan dengan jelas:
   - descriptive/statistical evidence
   - continuation behavior
   - selection/survivor effects
   - dependency/overlap effects
   Jangan mengubah hasil menjadi klaim kausal hanya karena korelasi atau selection effect.
7. Untuk setiap metrik/threshold yang digunakan, cari sumbernya dari kode/data aktual. Jika belum ada dasar yang sah, tandai sebagai INSUFFICIENT EVIDENCE, jangan mengarang angka.
8. Pertahankan prinsip:
   - tidak menambah indikator trading baru
   - tidak tuning strategi berdasarkan hasil benchmark
   - tidak memasukkan data sintetis
   - tidak mengubah baseline tanpa alasan metodologis yang terdokumentasi
   - jangan menggunakan/menjalankan Gorouter.app
9. Tambahkan test untuk setiap perubahan yang memang diperlukan.
10. Jalankan ulang seluruh test setelah perubahan.
11. Periksa git diff secara menyeluruh untuk memastikan tidak ada perubahan yang tidak disengaja.
12. Jangan commit atau push.
13. Jika ada blocker, berhenti tepat pada blocker tersebut dan jelaskan file/baris/perintah yang dibutuhkan. Jangan membuat data atau hasil eksperimen palsu.

TARGET AKHIR:
hasilkan benchmark drift-neutral yang auditable dan reproducible dari repository ini, dengan output/report yang dapat ditelusuri kembali ke data dan kode aktual.

Setelah selesai, tampilkan:
- ringkasan perubahan
- hasil test aktual
- file yang berubah
- git diff summary
- keputusan setiap setup/engine beserta evidence-nya
- blocker jika masih ada

Kerjakan langsung di repository ini. Jangan hanya memberikan saran atau pseudocode.
```
# 
```
Lanjutkan project dari kondisi repository saat ini.

PENTING:
- Jangan membuat atau mengarang data hasil eksperimen.
- Jangan mengubah strategi, parameter, threshold, scoring, atau data historis yang sudah ada.
- Jangan lanjut ke confluence/research sebelum benchmark drift-neutral selesai.
- Semua angka/statistik harus berasal dari file/data dan runner yang benar-benar tersedia di filesystem.
- Gunakan repository sebagai source of truth, bukan asumsi dari percakapan sebelumnya.

Tugas sekarang:

1. Verifikasi akses filesystem dan lokasi repository:
   - pastikan /root/mt-info adalah repository yang benar
   - cek git status
   - identifikasi baseline/stage 1-4
   - baca struktur code dan test yang sudah ada

2. Audit benchmark yang baru dibuat:
   - baca python/benchmark.py dan test terkait
   - pastikan benchmark benar-benar drift-neutral
   - pastikan tidak ada leakage/look-ahead
   - pastikan benchmark tidak mengubah strategi trading
   - pastikan seluruh input berasal dari DATA historis yang tersedia

3. Implementasikan hanya framework benchmark yang memang dapat diverifikasi dari data.
   Jika data atau baseline yang diperlukan tidak tersedia, STOP dan laporkan file apa yang kurang.
   Jangan membuat placeholder yang seolah-olah merupakan hasil penelitian.

4. Jalankan seluruh test suite dari root repository.
   Target:
   - semua test existing tetap PASS
   - test benchmark PASS
   - tidak ada test yang dihapus, di-skip, atau dilemahkan hanya agar PASS

5. Setelah itu lakukan audit:
   - git diff
   - git status
   - daftar file yang berubah
   - checksum/data integrity jika relevan

6. Jangan commit atau push dulu.

Pada akhir pekerjaan berikan laporan singkat:
- apa yang benar-benar diperiksa
- apa yang benar-benar diubah
- jumlah test PASS/FAIL
- apakah benchmark valid dijalankan dari data nyata
- apakah ada blocker
- git status terakhir

Jika akses shell/filesystem tidak tersedia pada sesi ini, jangan mengarang hasil. Berhenti dan nyatakan bahwa pekerjaan harus dilanjutkan pada sesi dengan akses filesystem repository.
```
# 
```
Lanjutkan dari kondisi project TERAKHIR.

HASIL BENCHMARK TERAKHIR:
- 257 tests passed.
- 0 failed.
- 0 error.
- 0 skipped.
- Drift-neutral benchmark sudah selesai.
- Setup A Resistance Rejection = WATCHLIST.
- Setup B Breakout+Retest = DISABLED.
- Setup C Support Rejection = DISABLED.
- Setup D Breakdown+Retest = INSUFFICIENT EVIDENCE.
- Setup E Continuation Engine = WATCHLIST, belum diaktifkan.
- CSV real XAUUSD M5/M15 tetap cocok dengan HEAD.
- Belum commit.
- Belum push.

==================================================
TUJUAN TAHAP INI
==================================================

Sekarang lakukan CONFLUENCE RESEARCH secara ilmiah.

Tujuannya bukan membuat strategi lebih profitable.

Tujuannya:

> Menentukan apakah confirmation tambahan benar-benar memberikan informasi baru di atas baseline yang sudah ada.

Jangan menganggap indikator populer otomatis berguna.

Jangan tuning untuk mencari parameter terbaik.

Jangan membuat auto-trading.

Jangan mengaktifkan setup yang sebelumnya DISABLED.

==================================================
1. AUDIT BASELINE TERLEBIH DAHULU
==================================================

Audit implementasi baseline yang sekarang.

Baseline harus tetap:

M15:
- market structure
- Support/Resistance

M5:
- price reaction
- candle confirmation
- rejection/continuation sesuai setup

Pastikan:
- candle harus CLOSE,
- tidak ada look-ahead,
- tidak ada repaint,
- S/R tidak membaca masa depan,
- confirmation tidak membaca future candle.

Jangan mengubah baseline sebelum eksperimen.

==================================================
2. BATASI SETUP YANG DITELITI
==================================================

Gunakan status benchmark sebagai gate.

BOLEH diteliti:
- Setup A Resistance Rejection = WATCHLIST
- Setup E Continuation = WATCHLIST

JANGAN diaktifkan:
- Setup B = DISABLED
- Setup C = DISABLED

Untuk Setup D:
- status tetap INSUFFICIENT EVIDENCE.
- Jangan memaksanya menjadi signal.
- Jika datanya cukup untuk exploratory analysis, boleh dianalisis secara deskriptif.
- Jangan menaikkan status hanya karena hasil satu eksperimen.

==================================================
3. CANDIDATE CONFIRMATION
==================================================

Teliti satu per satu:

A. ADX
B. DMI (+DI/-DI)
C. EMA trend/regime
D. ATR
E. ATR relatif terhadap historical ATR
F. Candle range / ATR
G. Bullish/Bearish Engulfing
H. Pin Bar/Rejection
I. Strong Body
J. Breakout/Breakdown Candle
K. Retest Confirmation
L. VWAP jika data/timezone memungkinkan

Jangan langsung menggabungkan semuanya.

==================================================
4. EXPERIMENTAL DESIGN
==================================================

Gunakan baseline sebagai CONTROL.

Untuk setiap candidate:

CONTROL:
Baseline

EXPERIMENT:
Baseline + satu confirmation

Contoh:

Baseline
vs
Baseline + ADX

Baseline
vs
Baseline + ATR

Baseline
vs
Baseline + EMA

dan seterusnya.

Jangan melakukan parameter sweep besar.

Gunakan parameter yang sudah terdokumentasi atau parameter canonical yang wajar.

Jika parameter belum ada:
gunakan nilai standar yang masuk akal untuk exploratory research,
tetapi JANGAN memilih nilai berdasarkan hasil performa.

==================================================
5. INFORMATION GAIN
==================================================

Jangan hanya bertanya:

"Apakah win rate naik?"

Untuk setiap confirmation ukur:

- sample count
- signal count
- expectancy
- median R
- mean R
- win rate
- profit factor jika meaningful
- maximum drawdown
- consecutive losses
- distribution of R
- baseline vs experiment
- perubahan jumlah signal

Yang paling penting:

Apakah confirmation memberikan informasi tambahan?

Jika confirmation hanya:
- mengurangi jumlah trade,
- tetapi tidak meningkatkan kualitas secara konsisten,

maka jangan menganggapnya berguna.

==================================================
6. SAMPLE SIZE
==================================================

Jangan menarik kesimpulan kuat dari sample kecil.

Jika sample terlalu kecil:

INSUFFICIENT SAMPLE

Jika hasil tidak konsisten:

NO EVIDENCE

Jika hasil menunjukkan peningkatan tetapi belum cukup kuat:

WEAK EVIDENCE

Jika hasil konsisten:

CANDIDATE FOR VALIDATION

Jangan gunakan istilah:
"akurasi tinggi"
"pasti lebih bagus"
"indikator terbaik"

==================================================
7. IN-SAMPLE / OUT-OF-SAMPLE
==================================================

Semua confirmation yang terlihat menjanjikan harus diuji:

- In-sample
- Validation
- Out-of-sample

Jika memungkinkan:

- Walk-forward

Parameter tidak boleh dipilih menggunakan OOS.

Jangan melakukan repeated tuning terhadap OOS.

Jika confirmation bagus di IS tetapi gagal OOS:

OVERFIT / DISABLED

==================================================
8. REGIME ANALYSIS
==================================================

Pisahkan hasil berdasarkan:

- bullish
- bearish
- sideways

Dan untuk setup yang relevan:

- rejection
- continuation
- breakout
- retest

Tujuannya mengetahui apakah confirmation hanya berguna pada regime tertentu.

Jangan menggabungkan seluruh kondisi menjadi satu angka.

==================================================
9. INTERACTION / CONFLUENCE
==================================================

Setelah single confirmation selesai, hanya ambil candidate yang menunjukkan evidence.

Baru lakukan kombinasi terbatas:

Baseline
+
Confirmation A
+
Confirmation B

Contoh:

Baseline + ADX + ATR

Tetapi hanya jika:
- A dan B masing-masing memiliki evidence,
- kombinasi tidak dipilih hanya karena hasil tertinggi,
- hasil tetap diuji OOS.

Jangan melakukan exhaustive parameter optimization.

==================================================
10. NO SIGNAL RULE
==================================================

Tetap pertahankan:

CONFIRM OR NO SIGNAL

Jika:
- structure tidak jelas,
- S/R lemah,
- confirmation konflik,
- regime tidak sesuai,
- candle belum close,
- risk/reward tidak valid,

maka:

NO SIGNAL

Jangan membuat filter hanya agar statistik terlihat lebih bagus.

==================================================
11. REPORT
==================================================

Buat report:

# Confluence Research

## 1. Baseline Definition

## 2. Experimental Method

## 3. Candidate Confirmation Results

Tabel:

Confirmation | Setup | N | Signal Count | Expectancy | PF | Max DD | OOS Result | Classification

Classification hanya:

- USEFUL CANDIDATE
- WEAK EVIDENCE
- NO EVIDENCE
- INSUFFICIENT SAMPLE
- OVERFIT / DISABLED

## 4. Regime Analysis

## 5. OOS Analysis

## 6. Walk-Forward Analysis

jika memungkinkan.

## 7. Interaction Tests

Hanya kombinasi confirmation yang memiliki evidence.

## 8. Final Decision

Untuk setiap confirmation:

KEEP AS CANDIDATE
WATCHLIST
DISABLED

==================================================
12. STRICT ANTI-OVERFITTING
==================================================

DILARANG:

- memilih parameter berdasarkan OOS,
- mengulang tuning sampai menemukan hasil bagus,
- memilih periode terbaik,
- menghapus trade buruk,
- menghapus market regime buruk,
- mengubah entry agar hasil meningkat,
- mengubah SL/TP berdasarkan hasil eksperimen,
- menambah indikator yang tidak ada dalam eksperimen,
- menggunakan synthetic market data.

Jika ada ambiguity metodologis:
jelaskan dan jangan memaksakan kesimpulan.

==================================================
13. TESTING
==================================================

Tambahkan test hanya untuk kode/framework yang memang diperlukan.

Pastikan test memeriksa:

- deterministic calculation,
- no look-ahead,
- candle-close requirement,
- data immutability,
- regime classification,
- confirmation calculation,
- baseline tidak berubah,
- OOS tidak bocor ke training.

Jalankan kedua runner yang sudah digunakan project.

Target:

0 failed
0 error
0 skipped

==================================================
14. GIT
==================================================

Setelah selesai:

- git status
- git diff HEAD
- pastikan hanya perubahan yang berkaitan dengan tahap ini.
- jangan commit.
- jangan push.

==================================================
KEPUTUSAN AKHIR
==================================================

Saya ingin jawaban objektif:

1. Confirmation mana yang benar-benar menambah informasi?
2. Confirmation mana yang hanya mengurangi signal tanpa menambah kualitas?
3. Confirmation mana yang gagal OOS?
4. Confirmation mana yang cukup kuat menjadi candidate?
5. Apakah ADX/DMI membantu?
6. Apakah ATR membantu?
7. Apakah EMA membantu?
8. Apakah VWAP membantu?
9. Candle confirmation mana yang paling konsisten?
10. Apakah confluence meningkatkan kualitas Setup A?
11. Apakah confluence memberikan bukti tambahan untuk Setup E?
12. Apa yang tetap harus NO SIGNAL?

Jangan mengubah status setup hanya karena satu eksperimen.

Jangan mengaktifkan auto-trading.

Jangan lanjut ke production.

Setelah semua verifikasi selesai dan test PASS:

BERHENTI.

Tunggu instruksi berikutnya.
```
# 
```
Lanjutkan dari kondisi terakhir project.

STATUS TERAKHIR:
- 208 tests passed di kedua runner.
- Causal validation sudah ditambahkan.
- Data XAUUSD M5/M15 real sudah tervalidasi.
- Checksum CSV cocok dengan HEAD.
- Backtester causal dan integrity check sudah PASS.
- Stage robustness sudah selesai.
- Tidak ada setup yang boleh disebut ROBUST tanpa evidence.
- Continuation masih WATCHLIST.
- Belum ada confluence research.
- Belum ada tuning strategi.
- Belum ada auto-trading.
- Belum commit/push perubahan baru.

REKOMENDASI TAHAP TERAKHIR:
Sebelum confluence research, bangun benchmark drift-neutral.

TUJUAN UTAMA:
Menentukan apakah hasil setup saat ini benar-benar menunjukkan edge dibandingkan baseline yang netral terhadap arah/drift market.

Jangan mencoba membuat strategi lebih profitable.
Jangan menambah indikator.
Jangan mengubah threshold strategi.
Jangan melakukan tuning berdasarkan hasil benchmark.

==================================================
1. AUDIT IMPLEMENTASI SEBELUM CODING
==================================================

Periksa terlebih dahulu:

- struktur backtester
- data loader
- trade ledger
- outcome/R calculation
- existing statistical utilities
- existing reports
- existing tests

Jangan mengubah implementasi strategi jika tidak diperlukan.

Jika ada fungsi/utilitas statistik yang sudah tersedia, gunakan kembali.

==================================================
2. DRIFT-NEUTRAL BENCHMARK
==================================================

Bangun benchmark yang dapat menjawab:

"Apakah performa setup lebih baik daripada hasil yang dapat dijelaskan hanya oleh arah/drift harga?"

Benchmark harus mempertahankan karakteristik data/trade yang relevan sebisa mungkin, tetapi tidak boleh menggunakan informasi masa depan.

Minimal pertimbangkan benchmark berikut jika valid secara metodologis:

A. Direction-neutral baseline
- BUY/SELL direction tidak diberikan advantage berdasarkan future outcome.
- Tujuannya mendapatkan distribusi performa baseline netral.

B. Trade-timing-preserving benchmark
- Pertahankan timestamp/opportunity dari trade aktual.
- Jangan mengubah jumlah opportunity secara sembarangan.

C. Return/R permutation benchmark
- Gunakan permutation terhadap urutan outcome/R sesuai metodologi yang valid.
- Pastikan permutation tidak mengubah data market asli.

D. Drift-adjusted comparison
- Ukur return yang dapat dijelaskan oleh directional drift pada periode terkait.
- Jangan menggunakan future information untuk menentukan signal.

Jangan membuat benchmark yang terlihat netral tetapi sebenarnya memakai hasil masa depan.

Jika salah satu benchmark tidak metodologis valid untuk struktur backtester saat ini:
JANGAN memaksakannya.
Jelaskan alasannya dan gunakan benchmark yang valid saja.

==================================================
3. NULL HYPOTHESIS
==================================================

Definisikan secara eksplisit null hypothesis.

Contoh konsep:

H0:
Performa observed setup tidak berbeda secara material dari baseline drift-neutral.

H1:
Performa observed setup menunjukkan evidence yang konsisten lebih baik daripada baseline drift-neutral.

Jangan menganggap H1 benar.

==================================================
4. STATISTIK
==================================================

Untuk observed strategy dan benchmark hitung minimal:

- sample size
- mean R
- median R
- expectancy
- standard deviation
- profit factor jika meaningful
- maximum drawdown
- win rate jika meaningful
- distribution of R
- confidence interval untuk expectancy jika metodologinya valid
- perbedaan observed vs benchmark

Jika permutation/resampling digunakan:
laporkan distribusi benchmark, bukan hanya satu angka.

Jika memungkinkan hitung:

- empirical p-value
- percentile observed result terhadap benchmark distribution
- confidence interval

Jangan menggunakan p-value sebagai satu-satunya bukti edge.

==================================================
5. TRADE COUNT DAN DEPENDENCY
==================================================

Audit:

- apakah benchmark memiliki jumlah trade yang comparable,
- apakah trade saling overlap,
- apakah ada dependency antar trade,
- apakah multiple trade berasal dari event market yang sama.

Jika independence tidak dapat diasumsikan:
jangan menggunakan statistical test yang mensyaratkan independence tanpa penyesuaian.

Dokumentasikan keterbatasannya.

==================================================
6. TIME / REGIME ROBUSTNESS
==================================================

Benchmark harus dievaluasi pada:

- periode awal
- periode tengah
- periode akhir

Dan jika data memungkinkan:

- bullish
- bearish
- sideways

Tujuannya memastikan observed edge bukan hanya akibat market drift pada satu periode.

Jangan memilih periode terbaik.

==================================================
7. SETUP COMPARISON
==================================================

Bandingkan secara terpisah:

A. Resistance Rejection
B. Resistance Breakout + Retest
C. Support Rejection
D. Support Breakdown + Retest
E. Continuation WATCHLIST

Jangan menggabungkan semuanya menjadi satu angka sebelum masing-masing dianalisis.

Untuk setiap setup:

Observed
vs
Drift-neutral benchmark

Tentukan:

ROBUST EVIDENCE
WEAK EVIDENCE
INSUFFICIENT SAMPLE
NO EVIDENCE

Gunakan klasifikasi konservatif.

==================================================
8. IMPORTANT: NO STRATEGY TUNING
==================================================

Selama tahap ini:

- jangan mengubah entry
- jangan mengubah exit
- jangan mengubah SL
- jangan mengubah TP
- jangan mengubah S/R
- jangan mengubah confirmation
- jangan menambah filter
- jangan menambah indikator
- jangan mengubah scoring
- jangan memilih parameter terbaik

Benchmark hanya untuk VALIDASI.

==================================================
9. REPORT
==================================================

Buat report yang jelas:

# Drift-Neutral Benchmark

## 1. Objective

## 2. Null Hypothesis

## 3. Benchmark Method

## 4. Observed Strategy

## 5. Benchmark Distribution

## 6. Statistical Comparison

Tabel:

Setup | N | Observed Expectancy | Benchmark Expectancy | Difference | Percentile/P-value jika valid | Classification

## 7. Time Stability

## 8. Regime Stability

## 9. Limitations

## 10. Final Decision

Untuk setiap setup:

KEEP
WATCHLIST
DISABLED
INSUFFICIENT EVIDENCE

==================================================
10. TESTING
==================================================

Tambahkan unit tests untuk memastikan benchmark:

- deterministic jika seed diberikan,
- tidak memodifikasi CSV asli,
- tidak mengubah trade ledger asli,
- tidak menggunakan future market information,
- menghasilkan jumlah sample sesuai spesifikasi,
- permutation benar-benar berubah ketika seed berbeda,
- seed yang sama menghasilkan hasil yang sama,
- edge case sample kecil ditangani dengan benar.

Jalankan:

PYTHONPATH=. python3 -m pytest -q

dan runner test kedua yang sudah digunakan project.

Target:
0 failed
0 error
0 skipped karena perubahan ini.

==================================================
11. DATA SAFETY
==================================================

Jangan mengubah CSV asli.

Jangan membuat synthetic market data.

Permutation/resampling hanya boleh digunakan sebagai statistical null benchmark, bukan sebagai pengganti market data.

Jangan memasukkan file output besar ke Git.

Pastikan reports/ tetap sesuai aturan .gitignore yang sudah ada.

==================================================
12. GIT
==================================================

Setelah implementasi:

- tampilkan git diff
- tampilkan git status
- pastikan tidak ada perubahan tidak sengaja
- jangan commit
- jangan push

Berhenti setelah verifikasi selesai.

==================================================
HASIL AKHIR YANG SAYA INGINKAN
==================================================

Saya ingin jawaban objektif:

Apakah observed setup memberikan evidence yang cukup bahwa performanya tidak sekadar dijelaskan oleh drift market?

Jika YA:
jelaskan setup mana dan seberapa kuat evidence-nya.

Jika TIDAK:
jelaskan bahwa evidence belum cukup.

Jika sample terlalu kecil:
gunakan INSUFFICIENT SAMPLE.

Jangan membuat kesimpulan bullish hanya karena observed expectancy positif.

Setelah benchmark selesai dan seluruh test PASS, BERHENTI.

Jangan lanjut ke confluence research.

Jangan menambah indikator.

Jangan tuning.

Jangan auto-trading.

Jangan commit/push.
```
# 
```
Lanjutkan project dari kondisi terakhir saat ini.

STATUS TERAKHIR:
- 192 tests PASS di kedua runner.
- Repository bersih dari tracked changes selain perubahan yang memang sudah ada dari tahap sebelumnya.
- Data XAUUSD M5/M15 adalah data real broker dan checksum sudah diverifikasi.
- Backtester sudah diaudit untuk causal validation.
- Stage 4 robustness audit sudah selesai.
- WATCHLIST tetap dipertahankan.
- Belum ada setup yang boleh disebut ROBUST.
- Belum ada commit/push baru kecuali commit yang sudah ada.
- Jangan mengubah strategi hanya untuk memperbaiki statistik.

TAHAP SEKARANG:
Evidence & Edge Validation.

TUJUAN:
Cari tahu apakah kegagalan robustness berarti:
1. benar-benar tidak ada edge,
2. edge ada tetapi lemah,
3. sample belum cukup,
4. edge hanya muncul pada regime tertentu,
5. edge hilang setelah biaya/slippage,
6. hasil terlalu bergantung pada sedikit trade,
7. atau definisi setup masih belum cukup teridentifikasi.

JANGAN melakukan:
- auto-trading,
- optimasi parameter,
- tuning berdasarkan hasil OOS,
- menambah indikator baru,
- mengubah threshold hanya agar hasil terlihat bagus,
- synthetic data,
- menghapus trade/outlier hanya karena memperburuk hasil,
- look-ahead,
- penggunaan data masa depan,
- membuat klaim "akurasi tinggi".

PRINSIP UTAMA:
Jangan mencoba membuktikan bahwa strategi bagus.
Coba buktikan apakah EDGE benar-benar ada.

==================================================
1. AUDIT SETUP SAAT INI
==================================================

Identifikasi implementasi aktual dari:

A. Resistance Rejection
B. Resistance Breakout + Retest
C. Support Rejection
D. Support Breakdown + Retest
E. Continuation engine jika masih aktif/WATCHLIST

Untuk masing-masing jelaskan secara eksplisit:

- kondisi pembentukan setup,
- candle yang digunakan,
- timestamp informasi pertama yang tersedia,
- timestamp confirmation,
- timestamp entry,
- bagaimana SL ditentukan,
- bagaimana TP ditentukan,
- kapan trade dianggap WIN/LOSS,
- apakah ada kemungkinan future information masuk ke setup.

Jangan mengubah implementasi sebelum audit selesai.

==================================================
2. EVIDENCE LEDGER
==================================================

Buat ledger per setup.

Untuk setiap trade/signal catat minimal:

- timestamp setup
- setup type
- M15 regime
- S/R type
- S/R strength jika tersedia
- breakout/rejection/retest state
- confirmation type
- entry
- SL
- TP
- outcome
- R multiple
- MAE jika tersedia
- MFE jika tersedia
- holding duration
- biaya/slippage yang digunakan
- apakah trade valid secara causal

Pastikan satu trade dapat ditelusuri kembali ke candle yang membentuk keputusan.

Jangan mengubah data asli.

==================================================
3. SAMPLE SUFFICIENCY
==================================================

Untuk setiap setup hitung:

- total opportunities
- valid signals
- rejected/no-signal opportunities
- wins
- losses
- win rate
- average R
- median R
- expectancy
- profit factor
- maximum drawdown
- consecutive losses
- kontribusi top 5 winner
- kontribusi top 5 loser

Jangan hanya melihat win rate.

Tandai secara eksplisit jika sample terlalu kecil untuk kesimpulan.

Gunakan label:

ROBUST EVIDENCE
WEAK EVIDENCE
INSUFFICIENT SAMPLE
NO EVIDENCE

Jangan menggunakan satu angka threshold arbitrer sebagai bukti robustness.

==================================================
4. EDGE STABILITY
==================================================

Pecah hasil berdasarkan waktu.

Minimal:

- tahun/periode awal
- periode tengah
- periode akhir

Jika data memungkinkan gunakan beberapa blok waktu yang berurutan.

Tujuannya mengetahui apakah edge:

- konsisten,
- menurun,
- hanya muncul pada satu periode,
- atau berubah regime.

Jangan memilih periode yang paling bagus.

==================================================
5. MARKET REGIME
==================================================

Pisahkan hasil berdasarkan:

- bullish
- bearish
- sideways

Dan jika implementasi sudah menyediakan:

- breakout regime
- rejection regime
- continuation regime
- high volatility
- low volatility

Jangan menambah indikator baru.

Tujuannya hanya mengetahui DI MANA edge yang sudah ada mungkin bekerja.

==================================================
6. COST / EXECUTION SENSITIVITY
==================================================

Jika backtester sudah memiliki model spread/slippage/cost, audit penggunaannya.

Hitung jika memungkinkan:

- gross R
- net R
- perubahan expectancy
- perubahan profit factor

Jika biaya belum dapat dimodelkan dengan valid, jangan mengarang nilainya.

Laporkan keterbatasannya.

==================================================
7. TRADE CONCENTRATION
==================================================

Periksa apakah hasil strategi sebenarnya hanya berasal dari sedikit trade.

Bandingkan:

- seluruh trade
- tanpa top 1 winner
- tanpa top 3 winner
- tanpa top 5 winner

JANGAN menghapus trade dari hasil resmi.

Ini hanya sensitivity analysis untuk mengetahui apakah edge terdiversifikasi atau bergantung pada outlier.

==================================================
8. CONTINUATION WATCHLIST
==================================================

Continuation engine tetap WATCHLIST.

Jangan mengaktifkannya sebagai signal engine.

Audit apakah hasil continuation berbeda secara material antara:

- continuation setelah breakout
- continuation setelah retest
- continuation berdasarkan regime

Jika evidence tidak cukup:

WATCHLIST / INSUFFICIENT EVIDENCE

Jangan memaksa kesimpulan.

==================================================
9. BASELINE VS SETUP
==================================================

Jangan menambah indikator.

Bandingkan baseline dengan masing-masing setup yang sudah ada.

Tujuan:

Menentukan apakah struktur:

M15 Structure
+
S/R
+
M5 Reaction
+
Confirmation

memiliki evidence yang lebih baik daripada sekadar variasi setup tanpa confirmation.

Jika tidak ada baseline yang benar-benar comparable, jelaskan keterbatasannya daripada membuat pembanding palsu.

==================================================
10. OUT-OF-SAMPLE
==================================================

Pertahankan pembagian:

IN-SAMPLE
VALIDATION
OUT-OF-SAMPLE

Jangan melakukan tuning menggunakan OOS.

Jika sample OOS terlalu kecil:

tulis jelas:

OOS INSUFFICIENT

Jangan menyebut gagal hanya karena sample kecil.

Jika memungkinkan lakukan walk-forward evaluation tanpa mengubah parameter berdasarkan hasil masa depan.

==================================================
11. CAUSALITY TEST
==================================================

Tambahkan regression/unit tests jika diperlukan untuk memastikan:

- trade tidak dapat mengetahui candle masa depan,
- S/R tidak menggunakan future swing,
- confirmation hanya candle CLOSE,
- entry selalu setelah confirmation,
- retest tidak dinilai sebelum retest benar-benar terjadi,
- outcome tidak memengaruhi pembentukan signal sebelumnya.

Semua test baru harus tetap causal.

==================================================
12. OUTPUT WAJIB
==================================================

Buat laporan yang jelas dengan struktur:

A. DATA
- periode
- jumlah candle M5
- jumlah candle M15
- integrity status

B. SETUP EVIDENCE
Tabel:

Setup | Opportunities | Signals | Win Rate | Avg R | Expectancy | PF | Max DD | Evidence

C. REGIME ANALYSIS
Tabel hasil berdasarkan:
- bullish
- bearish
- sideways
- breakout
- rejection
- retest
- continuation

D. TIME STABILITY
Jelaskan apakah hasil konsisten antar periode.

E. COST SENSITIVITY
Jelaskan dampak biaya jika model tersedia.

F. TRADE CONCENTRATION
Jelaskan ketergantungan terhadap winner besar.

G. OOS
Pisahkan hasil IS / Validation / OOS.

H. CAUSALITY
Laporkan apakah ada potensi look-ahead/repainting.

I. FINAL CLASSIFICATION

Untuk setiap setup pilih hanya salah satu:

ROBUST EVIDENCE
WEAK EVIDENCE
INSUFFICIENT SAMPLE
NO EVIDENCE

J. REKOMENDASI

Berikan keputusan untuk setiap setup:

KEEP
WATCHLIST
DISABLED
NEED MORE DATA

==================================================
13. ATURAN KEPUTUSAN
==================================================

Jangan menyebut setup ROBUST hanya karena:

- win rate tinggi,
- profit besar,
- satu periode bagus,
- sample kecil,
- beberapa trade besar.

Evidence harus mempertimbangkan:

sample size
+
stability
+
OOS
+
drawdown
+
expectancy
+
trade concentration
+
regime stability
+
causal correctness.

Jika evidence belum cukup:

jangan dipaksa menjadi GOOD atau BAD.

Gunakan:

INSUFFICIENT SAMPLE

Jika tidak terlihat edge:

NO EVIDENCE

Jika edge ada tetapi tidak stabil:

WEAK EVIDENCE / WATCHLIST

Jika evidence konsisten lintas periode dan OOS:

ROBUST EVIDENCE

==================================================
14. FILE SAFETY
==================================================

Jangan menghapus data asli.

Jangan memodifikasi CSV original.

Jangan mengubah strategi inti hanya untuk tahap audit ini.

Jika perlu membuat file baru, gunakan nama yang jelas, misalnya:

reports/evidence_edge_validation.*
python/tests/test_evidence_edge_validation.py

Pastikan tidak memasukkan dataset besar ke Git secara tidak sengaja.

Sebelum selesai jalankan seluruh test suite.

TARGET:

Kita ingin menjawab pertanyaan:

"Apakah Support/Resistance + Breakout/Rejection + Retest + Candle Confirmation benar-benar menunjukkan edge yang dapat dibuktikan secara causal dan stabil, atau kita sebenarnya hanya melihat noise?"

Setelah laporan selesai:
- jangan lanjut ke confluence,
- jangan optimasi,
- jangan auto-trading,
- jangan push,
- berhenti dan laporkan hasil akhir beserta rekomendasi tahap berikutnya.
```
# 
```
Lanjutkan project dari kondisi terakhir. Jangan mengulang audit yang sudah selesai dan jangan mengubah strategi tanpa alasan.

KONDISI TERAKHIR:
- Test suite: 192 passed.
- Kedua runner test sudah PASS.
- Data XAUUSD M5/M15 adalah data real dan checksum/CSV sudah diverifikasi terhadap HEAD.
- Look-ahead/causal validation dan wiring audit sebelumnya sudah dilakukan.
- Continuation engine sudah diaudit.
- Belum perlu auto-trading.
- Jangan menggunakan synthetic data sebagai bukti performa.
- Jangan menambah indikator baru.
- Jangan melakukan tuning parameter hanya untuk memperbagus hasil.
- Jangan commit/push tanpa persetujuan.

TAHAP SEKARANG:
ROBUSTNESS AUDIT

Tujuan tahap ini adalah menjawab:

"Apakah edge/setup yang sudah ditemukan benar-benar robust, atau hasilnya hanya berasal dari periode tertentu, regime tertentu, outlier tertentu, atau kondisi data tertentu?"

JANGAN langsung mengubah strategi.

==================================================
1. AUDIT PERIODE WAKTU
==================================================

Gunakan data XAUUSD real yang sudah tersedia.

Pisahkan hasil berdasarkan periode waktu yang masuk akal, minimal:

- per tahun
- jika sample memungkinkan, per semester/kuartal
- full period

Untuk setiap periode laporkan:

- jumlah setup
- jumlah trade
- win rate
- average R
- expectancy
- profit factor
- maximum drawdown
- consecutive losses
- net R

Tujuannya bukan mencari periode terbaik, tetapi melihat apakah edge muncul secara konsisten.

Jika sebuah setup hanya bekerja pada satu periode dan gagal pada periode lain, tandai sebagai:

PERIOD-DEPENDENT

==================================================
2. REGIME AUDIT
==================================================

Pisahkan performa berdasarkan kondisi market yang SUDAH tersedia dari framework saat ini.

Minimal:

- bullish
- bearish
- sideways
- breakout regime
- rejection regime
- continuation regime

Jangan membuat indikator baru hanya untuk klasifikasi ini.

Jawab:

- Apakah edge hanya muncul pada satu regime?
- Apakah setup tertentu buruk ketika market sideways?
- Apakah continuation benar-benar berbeda dari rejection?
- Apakah hasil tetap konsisten ketika regime berubah?

==================================================
3. BULLISH VS BEARISH SYMMETRY
==================================================

Bandingkan:

BUY setup
vs
SELL setup

Untuk masing-masing:

- sample
- win rate
- average R
- expectancy
- profit factor
- maximum drawdown
- consecutive losses

Jangan mengasumsikan BUY dan SELL memiliki karakteristik yang sama.

Jika ada asymmetry yang kuat, laporkan.

Jangan memperbaikinya dengan tuning.

==================================================
4. OUTLIER / WINNER CONCENTRATION AUDIT
==================================================

Periksa apakah performa keseluruhan bergantung pada beberapa trade winner terbesar.

Hitung minimal:

A. Full result

B. Tanpa top 1 winner

C. Tanpa top 3 winner

D. Tanpa top 5 winner

Bandingkan:

- net R
- expectancy
- profit factor
- drawdown

Tujuan:

Mengetahui apakah edge benar-benar tersebar di banyak trade atau hanya terlihat bagus karena beberapa winner ekstrem.

Jika sebagian besar performa hilang setelah top winners dihapus, tandai:

OUTLIER DEPENDENT

Jangan menghapus trade tersebut dari dataset utama.

==================================================
5. LOSS CONCENTRATION AUDIT
==================================================

Periksa apakah kerugian terkonsentrasi pada:

- periode tertentu
- regime tertentu
- setup tertentu
- sesi/jam tertentu jika data mendukung

Hitung:

- consecutive losses
- maximum losing streak
- drawdown cluster
- distribusi loss

Tujuannya mengetahui kapan sistem paling rentan.

==================================================
6. TRADE DISTRIBUTION AUDIT
==================================================

Periksa distribusi seluruh trade.

Jangan hanya melihat average.

Laporkan jika memungkinkan:

- median R
- mean R
- percentile R
- jumlah winner besar
- jumlah loser besar
- distribusi holding time jika tersedia

Cari tahu apakah expectancy berasal dari distribusi yang sehat atau sangat skewed.

==================================================
7. TRANSACTION COST / SLIPPAGE SENSITIVITY
==================================================

Jangan mengubah strategi.

Uji sensitivity secara konservatif terhadap:

- spread
- slippage
- biaya transaksi jika model tersedia

Gunakan beberapa skenario biaya yang masuk akal.

Contoh:

BASE
CONSERVATIVE
HIGH COST

Tujuan:

Mengetahui apakah edge masih positif setelah biaya yang lebih realistis.

Jangan membuat asumsi broker-specific yang tidak didukung data.

Jika parameter biaya tidak dapat ditentukan secara valid, jangan mengarang angka. Jelaskan keterbatasannya.

==================================================
8. SERIAL / CLUSTER DEPENDENCY
==================================================

Pastikan hasil tidak terlihat bagus hanya karena banyak trade yang berasal dari event market yang sama.

Gunakan audit dependency yang sudah ada.

Periksa:

- trade yang overlap
- trade yang berasal dari breakout/event yang sama
- continuation yang berasal dari parent event yang sama
- cluster trade
- exposure simultan jika dapat dihitung

Laporkan:

- raw trade count
- independent/cluster-aware count jika framework sudah mendukung

Jangan menghapus data hanya untuk memperbagus statistik.

==================================================
9. SETUP-BY-SETUP ROBUSTNESS
==================================================

Evaluasi terpisah:

A. Resistance Rejection
B. Resistance Breakout + Retest + Bullish Confirmation
C. Support Rejection + Bullish Confirmation
D. Support Breakdown + Retest + Bearish Confirmation
E. Continuation

Untuk masing-masing jawab:

- Apakah edge stabil antarperiode?
- Apakah edge stabil antar-regime?
- Apakah bergantung pada outlier?
- Apakah sensitif terhadap biaya?
- Apakah sample cukup?
- Apakah layak dilanjutkan?

Gunakan status:

ROBUST
PROMISING
PERIOD-DEPENDENT
REGIME-DEPENDENT
OUTLIER-DEPENDENT
INSUFFICIENT SAMPLE
NOT ROBUST

Jangan menyebut "akurat" hanya berdasarkan win rate.

==================================================
10. SAMPLE SIZE CHECK
==================================================

Jangan menarik kesimpulan kuat dari sample kecil.

Jika sample tidak cukup untuk menyimpulkan sesuatu:

INSUFFICIENT SAMPLE

Jangan memaksakan ranking setup.

==================================================
11. OUT-OF-SAMPLE / WALK-FORWARD
==================================================

Gunakan pembagian data yang sudah tersedia.

Pisahkan:

- In-Sample
- Validation
- Out-of-Sample

Jika walk-forward framework sudah tersedia, gunakan.

Jangan melakukan tuning menggunakan OOS.

Jika hasil OOS tidak tersedia atau tidak valid, laporkan dengan jelas.

Jangan mengubah parameter agar OOS terlihat lebih bagus.

==================================================
12. JANGAN MENAMBAH INDIKATOR
==================================================

Pada tahap ini:

JANGAN menambahkan:

- ADX
- DMI
- EMA
- ATR
- VWAP
- indikator lain

Confluence research dilakukan SETELAH robustness baseline selesai.

Kita harus mengetahui apakah baseline yang sekarang sudah mempunyai edge yang cukup robust sebelum menambahkan confirmation baru.

==================================================
13. NO STRATEGY TUNING
==================================================

Jangan mengubah:

- threshold
- S/R logic
- breakout threshold
- retest logic
- candle confirmation
- SL/TP
- scoring

kecuali ditemukan bug nyata.

Jika ditemukan bug:

1. jelaskan bug
2. tunjukkan bukti
3. perbaiki secara minimal
4. jalankan seluruh test
5. jangan melakukan optimasi tambahan

==================================================
14. TEST REGRESSION
==================================================

Setelah audit:

jalankan seluruh test suite.

Target:

- 0 failed
- 0 error

Bandingkan dengan baseline sebelumnya:

192 passed

Jika jumlah test berubah, jelaskan kenapa.

Jangan menghapus test yang gagal hanya agar suite PASS.

==================================================
15. GIT
==================================================

Periksa:

git status
git diff
git log -1

Jangan commit.

Jangan push.

Jika ada perubahan yang dibuat karena bug/test baru, biarkan working tree sesuai kondisi aktual dan laporkan.

==================================================
OUTPUT WAJIB
==================================================

Berikan laporan ringkas tetapi lengkap:

1. Dataset yang digunakan
2. Periode data
3. Jumlah sample
4. Hasil full period
5. Hasil per periode
6. Hasil per regime
7. BUY vs SELL
8. Outlier sensitivity
9. Loss concentration
10. Transaction-cost sensitivity
11. Cluster/dependency audit
12. OOS / walk-forward
13. Setup mana yang ROBUST
14. Setup mana yang PERIOD-DEPENDENT
15. Setup mana yang REGIME-DEPENDENT
16. Setup mana yang OUTLIER-DEPENDENT
17. Setup mana yang INSUFFICIENT SAMPLE
18. Apakah baseline layak masuk ke tahap confluence research
19. Jumlah test terakhir
20. git status terakhir

==================================================
KEPUTUSAN AKHIR
==================================================

Jangan langsung melanjutkan ke optimasi.

Gunakan keputusan:

A. ROBUST ENOUGH
→ baseline boleh masuk ke tahap Confluence Research.

B. PROMISING BUT NOT ROBUST
→ tetap WATCHLIST dan jangan tuning untuk memaksakan hasil.

C. NOT ROBUST
→ tandai setup terkait sebagai DISABLED/WATCHLIST.

D. INSUFFICIENT SAMPLE
→ jangan mengambil kesimpulan.

Prinsip utama:

DATA > ASSUMPTION
ROBUSTNESS > WIN RATE
OOS > IN-SAMPLE
INDEPENDENT EVIDENCE > TRADE COUNT
CONFIRMATION > PREDICTION
NO SIGNAL > BAD SIGNAL

Berhenti setelah laporan selesai.

Jangan melakukan confluence research.
Jangan menambah indikator.
Jangan auto-trading.
Jangan commit.
Jangan push.

```
# 
```
Lanjutkan penelitian dari hasil audit terakhir.

Jangan menambah indikator.
Jangan tuning parameter.
Jangan mengubah strategi untuk memperbagus hasil.
Jangan auto-trading.
Jangan commit atau push.

Fokus tahap ini hanya pada masalah OVERLAP / TRADE DEPENDENCY yang ditemukan.

Temuan terakhir:
- maksimum 42 posisi terbuka bersamaan
- sekitar 16,9% entry berjarak <=15 menit dari entry sebelumnya
- hasil agregat continuation engine terlihat berbeda ketika dihitung secara serial
- median R sekitar -1,0029R
- winner terbesar sekitar +8,20R
- loser terbesar sekitar -5,95R
- test suite 177 passed

Tujuan:
Menentukan apakah apparent edge continuation engine benar-benar berasal dari setup yang independen, atau hanya akibat clustering/overlap posisi pada episode market yang sama.

Tugas:

1. Audit definisi "trade" dan "position".

2. Tentukan apakah beberapa entry yang berdekatan sebenarnya berasal dari:
   - breakout yang sama
   - retest yang sama
   - S/R zone yang sama
   - market episode yang sama
   - continuation leg yang sama

3. Buat analisis dengan tiga cara:

A. RAW
Gunakan seluruh trade sebagaimana backtester saat ini.

B. SERIAL
Hanya satu posisi aktif pada satu waktu.
Entry baru tidak boleh dihitung jika masih ada posisi aktif.

C. CLUSTERED
Kelompokkan trade yang berasal dari episode market/setup yang sama.
Jelaskan aturan clustering secara objektif dan tidak dibuat khusus agar hasil terlihat lebih buruk atau lebih baik.

4. Bandingkan ketiga hasil:

- total trade
- total R
- expectancy
- profit factor
- win rate
- median R
- average R
- maximum drawdown
- maximum losing streak
- largest winner
- largest loser
- drawdown duration

5. Pisahkan hasil:
- BUY
- SELL
- breakout
- breakdown
- retest
- continuation

6. Buat analisis time clustering:
- entry <=5 menit
- <=15 menit
- <=30 menit
- <=60 menit

Jangan menganggap entry yang dekat otomatis salah.
Tujuannya hanya mengukur dependency.

7. Audit apakah satu market move besar menghasilkan banyak trade yang semuanya dihitung sebagai bukti independen.

Jika iya, jelaskan seberapa besar pengaruhnya terhadap statistik.

8. Lakukan sensitivity analysis:
Bandingkan hasil RAW vs SERIAL vs CLUSTERED tanpa mengubah parameter strategi.

9. Sangat penting:
Jangan memilih metode yang menghasilkan angka terbaik.

Metode harus dipilih berdasarkan definisi metodologis yang paling benar untuk sistem ini.

10. Periksa juga apakah ada:
- duplicate signal
- repeated signal pada zone yang sama
- repeated retest
- re-entry tanpa reset setup
- breakout event yang menghasilkan beberapa trade
- trade yang overlap hanya karena implementation detail

Jika ditemukan bug, perbaiki bug tersebut.
Jika bukan bug dan memang bagian dari desain, jangan mengubahnya diam-diam; jelaskan terlebih dahulu.

11. Jalankan seluruh test suite setelah perubahan.

Target hasil:

Jawab dengan tegas:

1. Apakah continuation engine masih positif setelah dependency dikontrol?
2. Apakah PF sekitar 1,04 tetap bertahan?
3. Apakah expectancy positif masih ada pada SERIAL?
4. Apakah hasil positif hanya berasal dari beberapa market episode besar?
5. Apakah RAW backtest terlalu optimistis karena overlap?
6. Apakah ada bug duplicate/re-entry?
7. Apakah continuation engine masih layak WATCHLIST atau harus diturunkan?

Jika setelah audit ternyata edge hilang:
jangan mencoba memperbaikinya dengan indikator baru.

Jika edge tetap bertahan:
barulah kita lanjut ke penelitian robustness.

Jangan commit.
Jangan push.
Berhenti setelah laporan dan test selesai.
```
# 
```
Lanjutkan dari hasil baseline terakhir.

Jangan menambah indikator baru dulu.
Jangan melakukan auto-trading.
Jangan tuning untuk memperbagus hasil.
Jangan commit atau push.

Fokus tahap berikutnya adalah AUDIT CONTINUATION ENGINE.

Hasil baseline menunjukkan continuation engine lebih baik daripada baseline umum:
- sekitar 14.215 trade
- expectancy sekitar +0,029R
- PF sekitar 1,04
- net sekitar +414R
- maxDD sekitar 158,77R
- OOS sekitar +0,013R dan masih WATCHLIST

Jangan menganggap angka tersebut sebagai edge yang sudah terbukti.

Tugas:

1. Pecah continuation engine menjadi komponen:
   - resistance breakout
   - support breakdown
   - retest
   - candle confirmation
   - M15 trend alignment
   - market regime

2. Hitung kontribusi masing-masing komponen secara TERPISAH.

3. Bandingkan:
   A. breakout tanpa retest
   B. breakout + retest
   C. breakout + retest + candle confirmation
   D. breakdown tanpa retest
   E. breakdown + retest
   F. breakdown + retest + candle confirmation

4. Pisahkan hasil:
   - BUY continuation
   - SELL continuation
   - M15 bullish
   - M15 bearish
   - M15 sideways

5. Audit apakah expectancy positif hanya berasal dari salah satu arah/setup.

6. Periksa distribusi hasil trade:
   - median R
   - mean R
   - percentile
   - jumlah winner/loser
   - largest winner
   - largest loser
   - consecutive losses
   - drawdown duration

7. Lakukan analisis temporal:
   - per tahun
   - per bulan
   - per sesi jika data memungkinkan

8. Wajib pisahkan:
   - IN-SAMPLE
   - VALIDATION
   - OUT-OF-SAMPLE

9. Jika memungkinkan lakukan walk-forward validation.

10. Audit kembali:
   - look-ahead bias
   - future S/R leakage
   - entry sebelum candle close
   - retest menggunakan candle masa depan
   - SL/TP menggunakan informasi masa depan
   - overlap/double counting trade

11. Jangan mengubah parameter strategi selama audit.

12. Jika ditemukan komponen yang tidak memberikan kontribusi nyata, tandai:
   DISABLED / WATCHLIST

13. Jika continuation engine ternyata positif hanya karena satu periode, satu arah, atau beberapa trade ekstrem, nyatakan secara eksplisit dan jangan menyebutnya edge.

Output harus menjawab:

1. Komponen continuation mana yang benar-benar berkontribusi.
2. Apakah breakout membutuhkan retest.
3. Apakah candle confirmation menambah expectancy.
4. Apakah BUY dan SELL mempunyai performa berbeda.
5. Apakah M15 trend alignment membantu.
6. Apakah hasil positif konsisten antarperiode.
7. Apakah OOS mendukung hasil IS.
8. Apakah masih ada tanda overfitting.
9. Apakah continuation engine layak naik dari WATCHLIST menjadi kandidat edge.
10. Apa satu langkah penelitian berikutnya.

Tetap gunakan data XAUUSD real yang sudah tervalidasi.

Setelah selesai:
- jalankan seluruh test suite
- laporkan hasil test
- tampilkan git status
- jangan commit
- jangan push
- berhenti dan tunggu instruksi berikutnya.
```
# 
```
Lanjut ke tahap BASELINE BACKTEST.

Gunakan hanya data XAUUSD real M5 + M15 yang sudah tervalidasi.

Jangan:
- menambah indikator baru
- mengubah strategi
- tuning parameter
- menggunakan synthetic data
- menggunakan OOS untuk tuning
- membuat auto-trading
- membuat Telegram signal
- commit
- push

Tugas:

1. Audit ulang backtester yang sekarang.
2. Jalankan baseline sesuai roadmap:
   - M15 market structure
   - Support/Resistance
   - M5 rejection
   - M5 breakout/breakdown
   - retest
   - candle confirmation
   - CONFIRM OR NO SIGNAL

3. Uji 4 setup secara TERPISAH:
   A. Resistance Rejection → SELL
   B. Resistance Breakout + Retest → BUY
   C. Support Rejection + Confirmation → BUY
   D. Support Breakdown + Retest → SELL

4. Untuk setiap setup hitung:
   - total sample
   - signal count
   - win rate
   - loss rate
   - average R:R
   - expectancy
   - profit factor
   - maximum drawdown
   - consecutive wins
   - consecutive losses

5. Pisahkan hasil berdasarkan:
   - M15 bullish
   - M15 bearish
   - M15 sideways
   - rejection
   - breakout
   - retest
   - continuation

6. Wajib lakukan split:
   - in-sample
   - validation
   - out-of-sample

7. Jika memungkinkan lakukan walk-forward validation.

8. Audit secara eksplisit:
   - look-ahead bias
   - repaint
   - future S/R leakage
   - entry sebelum candle CLOSE
   - future candle digunakan untuk menentukan signal
   - SL/TP menggunakan informasi masa depan

9. Jangan mengubah parameter hanya karena hasil baseline kurang bagus.

10. Jangan menyimpulkan "akurat" atau "profitable" hanya dari win rate.

Buat laporan baseline lengkap dan simpan sebagai report.

Setelah selesai:
- jalankan seluruh test suite
- pastikan semua test PASS
- tampilkan git status
- jangan commit
- jangan push
- berhenti dan tunggu instruksi berikutnya.

Tujuan tahap ini hanya mengetahui performa BASELINE pada data XAUUSD real sebelum penelitian confluence dimulai.
```
# 
```
Ya, perbaiki tiga klaim dokumentasi yang keliru di docs/DATA.md:

1. timezone EET/EEST
2. penjelasan close-to-close derivation
3. command path yang benar

Perubahan ini hanya dokumentasi dan tidak boleh mengubah:
- strategi
- data CSV
- backtester
- signal logic
- parameter
- test logic

Setelah dokumentasi diperbaiki:

1. Jalankan seluruh test suite.
2. Pastikan semua test PASS.
3. Verifikasi git diff hanya berisi perubahan dokumentasi.
4. Pastikan CSV XAUUSD M5/M15 tidak berubah.
5. Jangan commit.
6. Jangan push.

Setelah selesai berhenti dan laporkan:
- hasil test
- file yang berubah
- apakah CSV tetap identik
- status git.

Jangan lanjut ke optimasi atau confluence dulu.
```
# DATA XAUUSD REAL
```
Lanjutkan ke tahap berikutnya berdasarkan roadmap.

Commit causal coverage sudah selesai dan 177 test PASS.
Jangan mengubah strategi yang sudah ada.

Sekarang fokus HANYA pada REAL XAUUSD DATA PIPELINE.

Tugas:

1. Audit project dan xausr.mt5_export serta docs/DATA.md.
2. Pastikan mekanisme export mengambil candle OHLC asli dari MT5/broker.
3. Jangan membuat synthetic market data.
4. Jangan melakukan tuning strategi.
5. Jangan menambah indikator.
6. Jangan melakukan auto-trading.

Kita membutuhkan:
- XAUUSD M5
- XAUUSD M15
- minimal 2 tahun
- ideal 3 tahun jika histori broker tersedia.

Jangan mengasumsikan symbol harus bernama XAUUSD.
Deteksi symbol yang tersedia di MT5, misalnya:
XAUUSD
XAUUSDm
XAUUSD.
GOLD
atau variasi broker lainnya.

Siapkan prosedur export ke:

data/XAUUSD_M5.csv
data/XAUUSD_M15.csv

Format:
timestamp,open,high,low,close,volume

Timezone harus eksplisit dan didokumentasikan.

Setelah data tersedia, lakukan VALIDASI DATA:

- jumlah candle
- earliest timestamp
- latest timestamp
- duplicate
- missing candle
- invalid OHLC
- timestamp ordering
- timezone
- gap
- M5 consistency
- M15 consistency

Jangan mengisi missing candle dengan data buatan.
Jangan menghapus candle hanya untuk memperbagus statistik.

Setelah itu audit bahwa pipeline backtest tidak mengalami:
- look-ahead bias
- future candle leakage
- repaint
- S/R menggunakan future data
- confirmation sebelum candle CLOSE
- breakout sebelum candle CLOSE
- retest menggunakan future information
- entry timestamp yang terlalu awal.

Jika data MT5/broker belum bisa diakses dari environment ini:

JANGAN mencari jalan pintas.

Berhenti pada tahap preparation dan jelaskan:
1. Apa yang sudah siap.
2. Apa yang belum tersedia.
3. Symbol MT5 yang dibutuhkan.
4. Cara export dari MT5.
5. Di mana CSV harus ditempatkan.
6. Command validasi yang harus dijalankan.

Jika data REAL berhasil tersedia dan lolos integrity:
berhenti setelah DATA INTEGRITY PASS.

Jangan langsung optimasi strategi.

Target:
REAL DATA
→ DATA INTEGRITY PASS
→ BACKTEST READY
→ STOP

Setelah selesai, jalankan seluruh test suite dan laporkan hasilnya.
Jangan commit atau push tanpa persetujuan saya.
```
# 
```
Saya setujui commit tersebut.

Lanjutkan sekarang:
1. Commit test_causal_gaps.py.
2. Jangan tambah fitur atau coverage baru.
3. Jangan ubah strategi.
4. Jangan push ke remote.
5. Setelah commit, jalankan:
   PYTHONPATH=python python3 -m pytest -q
6. Jalankan:
   git status --short --branch
   git log -1 --oneline
7. Pastikan seluruh test PASS.
8. Laporkan hasil akhir dan berhenti.

Target: repository bersih dan test suite tetap PASS.
```
# 
```
Lanjutkan project dari kondisi terakhir.

STATUS SAAT INI:
- Git sudah clean dan sinkron dengan origin/main.
- pytest = 149 passed, 0 failed, 0 skipped.
- Data XAUUSD M5 dan M15 real sudah tersedia.
- Data integrity sudah diverifikasi.
- Jangan membuat synthetic data.
- Jangan auto-trading.
- Jangan menambah indikator/confluence dulu.

FOKUS TAHAP INI:
Tutup causal coverage yang masih terbuka sebelum melakukan riset confluence.

1. Audit causal coverage secara menyeluruh pada:
   - is_resistance_breakout_close
   - is_support_breakdown_close
   - retest logic
   - breakout/rejection classification
   - pattern family wiring
   - continuation logic
   - M15 → M5 alignment

2. Pastikan fungsi close-based benar-benar causal:
   - hanya candle yang sudah CLOSE boleh digunakan;
   - tidak boleh membaca candle masa depan;
   - state machine tidak boleh mengetahui hasil candle berikutnya;
   - entry tidak boleh terjadi sebelum confirmation;
   - retest harus terjadi setelah breakout/breakdown;
   - confirmation harus terjadi setelah retest/reaction yang relevan.

3. Buat/sempurnakan regression test untuk setiap celah causal yang ditemukan.
   Jangan menghapus test lama.
   Jangan melemahkan assertion hanya supaya test pass.

4. Jalankan seluruh test suite:
   PYTHONPATH=python python3 -m pytest -q

5. Jika semua test PASS, jangan langsung tuning strategi.

6. Jalankan baseline pada DATA XAUUSD REAL yang sekarang sudah tersedia.

Gunakan dataset:
- data/XAUUSD_M5.csv
- data/XAUUSD_M15.csv

Gunakan logika baseline yang sudah ada:
- M15 market structure
- Support/Resistance
- M5 rejection
- M5 breakout/breakdown
- retest
- candle confirmation
- CONFIRM OR NO SIGNAL

Jangan menambah ADX, ATR, EMA, VWAP, atau indikator baru.

7. Pisahkan hasil:
- In-sample
- Validation
- Out-of-sample
- Walk-forward jika engine sudah mendukungnya

8. Laporkan minimal:
- jumlah sample
- signal/setup count
- win rate
- loss rate
- expectancy
- profit factor
- average R
- maximum drawdown
- consecutive wins/losses
- hasil A/B/C/D
- hasil berdasarkan bullish/bearish/sideways M15
- hasil rejection/breakout/retest/continuation

9. Sangat penting:
Jangan mengubah threshold hanya untuk memperbaiki statistik.
Jangan memilih parameter berdasarkan OOS.
Jangan mengklaim edge/akurasi jika statistik tidak mendukung.

10. Jika hasil baseline tetap marginal atau NO EVIDENCE:
nyatakan apa adanya dan jangan memaksakan strategi.

11. Setelah selesai, tampilkan:
- git status --short --branch
- git diff
- hasil pytest
- ringkasan baseline
- daftar masalah yang masih terbuka
- rekomendasi SATU langkah berikutnya.

Jangan commit/push pada tahap ini tanpa meminta persetujuan saya terlebih dahulu.
```
# 
```
Lanjutkan ke tahap Git.

Kondisi saat ini sudah diverifikasi:
- pytest: 149 passed, 0 failed, 0 skipped
- reports/ tidak boleh masuk commit
- CSV data jangan diubah
- perubahan kode dan test yang sudah dibuat harus dipertahankan

Tugas:
1. Jalankan git diff untuk review perubahan kode.
2. Jalankan git status --short.
3. Pastikan reports/ dan file CSV tidak akan di-commit.
4. Stage hanya perubahan project yang relevan:
   - .gitignore
   - python/xausr/backtest.py
   - python/tests/test_break_close_causality.py
   - python/tests/test_causal_audit.py
   - python/tests/test_pattern_wiring.py
5. Jalankan pytest sekali lagi:
   PYTHONPATH=python python3 -m pytest -q
6. Jika tetap 149 passed dan tidak ada error, buat commit dengan pesan:
   "fix causal validation and pattern wiring"
7. Setelah commit berhasil, push ke origin/main.
8. Terakhir tampilkan:
   git status --short --branch
   git log -1 --oneline

Jangan mengubah strategi.
Jangan mengubah CSV.
Jangan memasukkan reports/.
Jangan melakukan auto-trading.

```
# 
```
Sekarang rapikan status Git tanpa mengubah logika strategi.

1. Periksa .gitignore yang ada.
2. Tambahkan reports/ ke .gitignore jika belum ada.
3. Jangan menghapus reports/ dari filesystem.
4. Jangan menghapus atau mengubah data CSV.
5. Pastikan tiga file test baru tetap dipertahankan:
   - python/tests/test_causal_audit.py
   - python/tests/test_pattern_wiring.py
   - perubahan python/xausr/backtest.py
6. Jalankan kembali:
   PYTHONPATH=python python3 -m pytest -q

7. Tampilkan:
   git status --short --branch

Jangan commit dan jangan push dulu.
Berhenti setelah status Git dan hasil test ditampilkan.
```
# 
```
Lakukan FINAL VERIFICATION project ini.

Jangan mengubah kode, jangan menambah fitur, jangan tuning strategi, dan jangan commit/push.

1. Jalankan seluruh test suite:
PYTHONPATH=python python3 -m pytest -q

2. Periksa git status:
git status --short --branch

3. Pastikan:
- semua test PASS
- tidak ada failed/error
- causal coverage tetap tertutup
- tidak ada perubahan kode tambahan yang belum diperiksa
- data CSV asli tetap utuh
- reports/ jangan di-commit
- jangan commit atau push apa pun

4. Jika semua PASS, berikan laporan singkat:
- jumlah test
- failed/error/skipped
- file kode yang berubah
- status data CSV
- status causal audit
- apakah project siap masuk tahap berikutnya

Berhenti setelah final verification. Jangan melakukan perubahan apa pun.
```
# 
```
Lanjutkan dari review terakhir.

Perbaiki hanya dua hal kecil yang kamu temukan:

1. Tutup celah causal coverage pada:
   - is_resistance_breakout_close
   - is_support_breakdown_close

Buat body-level test yang benar-benar memastikan kedua fungsi tersebut tidak dapat melewatkan informasi masa depan.

2. Setelah perubahan selesai:
   - jalankan seluruh test suite
   - pastikan semua test PASS
   - lakukan git status
   - jangan commit
   - jangan push
   - jangan tuning strategi
   - jangan mengubah threshold strategi
   - jangan membuat data synthetic sebagai bukti

Untuk reports/, jangan commit dulu dan jangan hapus.
Cukup laporkan statusnya.

Di akhir berikan:
- perubahan yang dibuat
- hasil pytest lengkap
- jumlah passed/failed/skipped
- git status
- apakah causal coverage sekarang sudah tertutup

Berhenti setelah itu.

```
# 
```
Lakukan final review terhadap pekerjaan yang baru selesai.

Jangan mengubah kode, jangan membuat strategi baru, dan jangan commit/push.

Periksa:
1. Perubahan python/xausr/backtest.py
2. test_causal_audit.py
3. test_pattern_wiring.py
4. reports/
5. Pastikan 134 test yang sudah passed memang valid
6. Pastikan tidak ada look-ahead bias atau wiring pattern yang salah
7. Pastikan data XAUUSD M5/M15 asli digunakan
8. Berikan kesimpulan apakah project siap masuk tahap berikutnya.

Jangan melakukan tuning berdasarkan hasil OOS.
```
# 
```
Lanjutkan dari hasil baseline terakhir.

JANGAN mengubah strategi.
JANGAN menambah indikator.
JANGAN melakukan optimasi parameter.
JANGAN commit atau push.

Baseline real XAUUSD sudah selesai dan seluruh test:
134 passed
0 failed
0 skipped

Sekarang lakukan tahap berikutnya: STATISTICAL SIGNIFICANCE AUDIT.

Tujuan:
menentukan apakah hasil baseline yang sudah ada benar-benar berbeda dari noise/random expectation.

Gunakan HASIL BASELINE YANG SUDAH ADA.
Jangan membuat synthetic market data sebagai pengganti data real.

Lakukan:

1. Hitung expectancy R untuk setiap setup:
   - A Resistance Rejection
   - B Resistance Breakout + Retest
   - C Support Rejection
   - D Support Breakdown + Retest

2. Hitung uncertainty/confidence interval untuk expectancy jika metodologi yang digunakan valid.

3. Gunakan permutation/bootstrap test yang sesuai untuk menguji kestabilan hasil.

4. Evaluasi apakah:
   - expectancy berbeda secara berarti dari 0;
   - PF sekitar 1 benar-benar menunjukkan edge atau hanya noise;
   - hasil setup konsisten antara IN-SAMPLE, VALIDATION, dan OOS.

5. Analisis sample size.
   Jangan menyebut hasil signifikan jika sample tidak cukup.

6. Analisis pattern family:
   - engulfing
   - pin/rejection
   - strong_body
   - breakout
   - retest

7. Untuk setiap setup/pattern berikan:
   - sample
   - expectancy
   - confidence interval
   - PF
   - win rate
   - max drawdown
   - hasil IS
   - hasil validation
   - hasil OOS
   - verdict

Gunakan verdict:

STRONG EVIDENCE
WEAK EVIDENCE
NO EVIDENCE
INSUFFICIENT DATA

Jangan menggunakan kata "profitable", "akurat", atau "edge" jika hasil statistik belum mendukung.

Khusus OOS:
jangan melakukan tuning berdasarkan hasil OOS.

Jangan mengubah implementasi hanya karena statistik kurang bagus.

Setelah selesai:
1. tampilkan laporan statistik;
2. tampilkan setup mana yang memiliki evidence terbaik;
3. tampilkan setup mana yang tidak memiliki evidence;
4. jelaskan apakah baseline layak dilanjutkan ke penelitian confluence;
5. jalankan seluruh test lagi;
6. tampilkan git status.

Jangan commit/push.
Setelah laporan selesai, berhenti.
```
# 
```
Lanjutkan ke NEXT STEP.

Jalankan baseline penuh menggunakan DATA REAL XAUUSD yang sudah tersedia.

JANGAN:
- mengubah strategi
- mengubah threshold
- melakukan optimasi
- membuat synthetic data
- mengubah hasil agar terlihat lebih bagus
- commit
- push
- menghapus test

Gunakan dataset real yang sudah ada:

data/XAUUSD_m_M5.csv
data/XAUUSD_m_M15.csv

Jalankan baseline sesuai roadmap:

M15 market structure
+
M15 Support/Resistance
+
M5 rejection
+
M5 breakout/breakdown
+
M5 retest
+
M5 candle confirmation
+
CONFIRM OR NO SIGNAL

Sebelum baseline, pastikan input dan periode data yang digunakan benar.

Kemudian jalankan baseline penuh dan simpan report.

WAJIB pisahkan hasil:
- Setup A — Resistance Rejection
- Setup B — Resistance Breakout + Retest
- Setup C — Support Rejection
- Setup D — Support Breakdown + Retest

Dan pattern family:
- engulfing
- pin/rejection
- strong_body
- breakout
- breakdown
- retest jika tersedia

Untuk setiap hasil tampilkan:
- n/sample
- signal count
- win/loss
- win rate
- average R
- expectancy
- profit factor
- max drawdown
- consecutive loss
- verdict

Pisahkan:
- in-sample
- validation
- out-of-sample
- walk-forward jika implementasinya sudah tersedia

KHUSUS BREAKOUT n=0:

Jangan menyimpulkan breakout buruk hanya karena n=0.

Bandingkan dengan hasil trace sebelumnya dan pastikan:
1. apakah breakout candidate memang ada;
2. apakah candidate gugur di gate tertentu;
3. apakah pattern wiring sudah benar;
4. apakah n=0 merupakan karakteristik dataset atau bug.

Jangan memperbaiki apa pun kecuali ditemukan bug nyata pada implementasi.

Jika ditemukan bug:
- jelaskan akar masalah;
- lakukan perbaikan minimal;
- jangan mengubah definisi strategi;
- jalankan ulang test;
- jalankan ulang baseline.

Setelah selesai, berikan:

1. DATASET YANG DIGUNAKAN
2. BASELINE RESULT
3. SETUP A/B/C/D
4. PATTERN FAMILY
5. BREAKOUT n=0 ANALYSIS
6. IN-SAMPLE vs OOS
7. TEST RESULT
8. WORKING TREE STATUS
9. SATU NEXT STEP TERBAIK

Jangan klaim "akurasi tinggi" atau "strategi profitable" tanpa bukti statistik yang memadai.

Setelah laporan selesai, BERHENTI dan tunggu instruksi berikutnya.
```
# 
```
Lanjutkan dari hasil audit terakhir.

JANGAN optimasi strategi dan JANGAN mengubah threshold hanya untuk menghasilkan trade.

Temuan utama:
- Setup A: marginal / watchlist
- Setup B: disabled
- Setup C: marginal / watchlist
- Setup D: marginal / watchlist
- Pattern family breakout menghasilkan n=0 trade
- Dataset real XAUUSD sudah tersedia
- Working tree masih memiliki data CSV dan test causal yang untracked
- pytest belum tersedia pada environment VPS

FOKUS UTAMA SEKARANG:

TRACE MENGAPA BREAKOUT MENGHASILKAN 0 TRADE.

Jangan berasumsi ini bug dan jangan langsung memperbaiki threshold.

Telusuri pipeline breakout secara lengkap:

1. Di mana BREAKOUT_UP / BREAKOUT_DOWN pertama kali dideteksi.
2. Kondisi candle apa yang membuat breakout terdeteksi.
3. Apakah breakout detection benar-benar menemukan kandidat pada data real.
4. Berapa jumlah kandidat breakout sebelum filter.
5. Berapa yang gugur pada setiap filter.
6. Filter mana yang menyebabkan jumlah kandidat menjadi 0.
7. Apakah kandidat hilang pada:
   - S/R detection
   - breakout close
   - body/range requirement
   - retest
   - confirmation
   - scoring
   - R:R
   - trend/M15 gate
   - trade execution/backtest engine
8. Pastikan tidak ada bug wiring antara:
   BREAKOUT_UP / BREAKDOWN
   dengan
   PATTERN_FAMILY / setup classification.

BUAT DIAGNOSTIC COUNTER.

Contoh:

breakout_candidates = ...
breakout_close_pass = ...
breakout_strength_pass = ...
retest_candidates = ...
retest_pass = ...
confirmation_candidates = ...
confirmation_pass = ...
risk_reward_pass = ...
final_trades = ...

Lakukan hal yang sama untuk breakout UP dan breakout DOWN.

PENTING:

Jika ternyata:

A) Tidak ada breakout candidate sama sekali:
   periksa apakah breakout detector salah membaca data/SR.

B) Ada breakout candidate tetapi semuanya gugur pada gate tertentu:
   identifikasi gate tersebut dan jelaskan kenapa.

C) Breakout sebenarnya ditemukan tetapi tidak pernah masuk trade:
   audit wiring antara detector → pattern family → signal engine → backtester.

D) Memang secara natural tidak ada breakout valid pada dataset:
   jangan memaksakan trade. Laporkan bahwa n=0 adalah hasil valid dataset.

JANGAN:

- mengubah threshold hanya supaya muncul trade
- membuat synthetic data
- menghapus filter
- melemahkan causal test
- mengubah definisi strategi
- menambah indikator
- auto-trading
- Telegram
- commit
- push

CAUSAL SAFETY:

Pastikan diagnostic tidak mengubah hasil backtest.

Semua keputusan breakout harus tetap causal:
hanya menggunakan informasi yang tersedia sampai candle tersebut CLOSE.

PYTEST:

Setelah investigasi breakout selesai, periksa dependency test.

Jika pytest memang belum terinstall di VPS, install dependency minimal yang diperlukan atau gunakan environment project yang benar.

Kemudian jalankan:

PYTHONPATH=python python3 -m pytest -q

Jalankan full test suite.

Jangan menghapus test yang gagal.

OUTPUT:

Berikan laporan:

1. BREAKOUT TRACE
2. Jumlah kandidat pada setiap tahap
3. Filter yang paling banyak menggugurkan kandidat
4. Apakah 0 trade disebabkan BUG atau memang hasil dataset
5. Jika BUG, perbaiki secara minimal dan causal-safe
6. Jalankan ulang test setelah perbaikan
7. Hasil full pytest
8. Status working tree
9. NEXT STEP tunggal yang paling tepat

Jangan membuat kesimpulan bahwa breakout memiliki edge atau tidak memiliki edge hanya dari n=0.

Tujuan tahap ini hanya:

TRACE → IDENTIFY CAUSE → FIX BUG JIKA ADA → TEST ULANG

Setelah selesai berhenti dan tunggu instruksi berikutnya.

```
# 
```
Lanjutkan project /root/mt-info dari kondisi saat ini.

Jangan mengubah roadmap dan jangan membuat strategi baru.

TUJUAN:
Lakukan FULL TEST + AUDIT project secara menyeluruh menggunakan kondisi project yang sekarang.

PENTING:
- Python command saat ini `python` tidak tersedia.
- Gunakan `python3` jika tersedia.
- Jika dependency/testing environment belum siap, perbaiki environment terlebih dahulu secara minimal.
- Jangan membuat synthetic market data untuk menggantikan data XAUUSD asli.
- Synthetic data hanya boleh digunakan oleh unit test jika memang sudah menjadi bagian test.
- Jangan melakukan auto-trading.
- Jangan menghapus data CSV asli.
- Jangan menghapus test yang ada.
- Jangan commit atau push apa pun.
- Jangan mengubah kode hanya supaya test menjadi hijau tanpa memahami penyebabnya.

LANGKAH 1 — AUDIT ENVIRONMENT

Periksa:

python3 --version
python3 -m pip --version
git status --short --branch
find data -maxdepth 2 -type f -print
find python -maxdepth 3 -type f -print
find tests -maxdepth 3 -type f -print 2>/dev/null || true

Jika pytest/dependency belum tersedia, install dependency yang memang diperlukan untuk menjalankan test project.

Gunakan virtual environment jika struktur project sudah menggunakannya.

LANGKAH 2 — FULL TEST

Jalankan seluruh test suite.

Gunakan command yang sesuai dengan environment, misalnya:

PYTHONPATH=python python3 -m pytest -q

Jika gagal karena dependency/module/environment, diagnosis dan perbaiki masalah environment tersebut terlebih dahulu.

Jalankan kembali full test setelah perbaikan.

Jangan berhenti hanya karena satu test gagal.

LANGKAH 3 — AUDIT DATA

Pastikan data real yang sekarang tersedia:

data/XAUUSD_m_M5.csv
data/XAUUSD_m_M15.csv

Periksa:

- file dapat dibaca
- jumlah candle
- earliest timestamp
- latest timestamp
- duplicate
- ordering
- invalid OHLC
- missing candle
- gap
- timezone
- M5 integrity
- M15 integrity
- M5 ↔ M15 consistency

Data XAUUSD tersebut adalah data hasil export MT5/broker yang sudah tersedia.

Jangan mengganti data tersebut dengan synthetic/random data.

LANGKAH 4 — AUDIT BACKTEST

Audit kode backtester untuk:

- look-ahead bias
- future candle leakage
- repaint logic
- entry sebelum confirmation candle CLOSE
- S/R menggunakan future data
- market structure menggunakan future data
- breakout dinyatakan sebelum candle close
- retest dinilai sebelum terjadi
- SL/TP menggunakan informasi masa depan
- timestamp entry yang salah

Jika menemukan bug, jelaskan dahulu penyebabnya dan perbaiki secara minimal tanpa mengubah konsep strategi.

LANGKAH 5 — AUDIT TEST CAUSAL

Perhatikan file:

python/tests/test_causal_audit.py

File ini sebelumnya masih untracked.

Jalankan test tersebut.

Jangan menghapusnya hanya karena menyebabkan failure.

Jika test tersebut memang valid, pertahankan.

Jika ada masalah implementasi test, perbaiki test secara tepat tanpa melemahkan pemeriksaan causal/look-ahead.

LANGKAH 6 — JALANKAN BASELINE

Setelah full test dan data validation siap, jalankan baseline menggunakan DATA REAL:

M15:
- market structure
- Support/Resistance

M5:
- rejection
- breakout/breakdown
- retest
- candle confirmation

Gunakan prinsip:

CONFIRM OR NO SIGNAL

Jangan menambah indikator baru.

Jangan melakukan optimasi parameter hanya untuk meningkatkan win rate.

LANGKAH 7 — STATISTIK

Jika baseline dapat dijalankan dengan benar, laporkan:

- jumlah candle M5
- jumlah candle M15
- periode data
- jumlah setup
- jumlah signal
- jumlah NO SIGNAL
- win rate
- loss rate
- average R:R
- expectancy
- profit factor
- maximum drawdown
- consecutive wins
- consecutive losses

Pisahkan jika tersedia:

- bullish
- bearish
- sideways
- resistance rejection
- resistance breakout
- support rejection
- support breakdown
- retest
- continuation

Jangan membuat angka statistik jika backtest tidak benar-benar menggunakan data real.

LANGKAH 8 — JANGAN OPTIMASI

Pada tahap ini JANGAN:

- menambah indikator
- mengubah strategi
- mengubah threshold hanya untuk memperbagus hasil
- melakukan parameter hunting
- membuat auto-trading
- membuat Telegram signal baru
- melakukan commit
- melakukan push

Fokus hanya:

DATA → TEST → CAUSAL AUDIT → BASELINE → REPORT

LANGKAH 9 — LAPORAN AKHIR

Berikan laporan dengan format:

1. ENVIRONMENT
   - Python version
   - pytest status
   - dependency status

2. TEST RESULT
   - total passed
   - failed
   - skipped
   - error
   - penyebab failure jika ada

3. DATA
   - M5 file
   - M15 file
   - jumlah candle
   - periode
   - integrity result

4. CAUSAL / LOOK-AHEAD AUDIT
   - PASS/FAIL
   - masalah yang ditemukan
   - file dan lokasi kode terkait

5. BASELINE
   - apakah berhasil dijalankan
   - apakah menggunakan REAL XAUUSD data
   - statistik jika valid

6. PROBLEMS FOUND
   - daftar masalah yang masih ada

7. NEXT STEP
   - hanya satu langkah berikutnya yang paling tepat berdasarkan hasil aktual

ATURAN PALING PENTING:

Jangan mengarang hasil.

Jika test gagal, katakan gagal.
Jika data tidak valid, katakan tidak valid.
Jika baseline belum dapat dijalankan, katakan belum dapat dijalankan.
Jika hasil belum cukup untuk menyimpulkan edge, jangan menyimpulkan edge.

Setelah selesai, BERHENTI dan berikan laporan lengkap.
```
# 
```
KOREKSI ENVIRONMENT — JANGAN CLONE / JANGAN BUAT REPO KEDUA

Repo utama dan data real sudah ada di mesin Windows saya:

E:\mt5\mt-info

Struktur yang benar:

E:\mt5\mt-info\
├── data\
│   ├── XAUUSD_M5.csv
│   └── XAUUSD_M15.csv
├── python\
├── docs\
├── mq15\
└── ...

Repository tersebut sudah merupakan clone yang benar dari:

https://github.com/zenolambee/mt-info.git

JANGAN:
- clone repository lagi
- membuat repo kedua
- membuat folder mt-info baru
- membuat folder data kedua
- membuat synthetic data
- menganggap data real tidak tersedia
- meminta saya commit CSV hanya agar VM dapat melihatnya

Masalah saat ini hanya karena sesi Anda berjalan di Linux VM:

/root/mt-info

sedangkan CSV berada di mesin Windows saya:

E:\mt5\mt-info\data\

==================================================
TUJUAN
==================================================

Kita harus menjaga SATU struktur repo saja.

Repo utama:

E:\mt5\mt-info

Data:

E:\mt5\mt-info\data\XAUUSD_M5.csv
E:\mt5\mt-info\data\XAUUSD_M15.csv

==================================================
LANGKAH SEKARANG
==================================================

Jangan melakukan perubahan kode terlebih dahulu.

Berikan saya diagnosis:

1. Apakah session/environment Anda saat ini benar-benar Linux VM?
2. Apakah /root/mt-info merupakan checkout repo yang terpisah dari Windows?
3. Apakah environment ini memiliki mount/access ke E:\mt5\mt-info?
4. Apakah ada cara resmi untuk menjalankan command langsung pada Windows repo tanpa membuat clone kedua?

Jika tidak ada akses ke filesystem Windows, JANGAN menganggap data hilang.

Tulis:

REAL DATA STATUS:
AVAILABLE ON WINDOWS REPO

ENVIRONMENT STATUS:
LINUX VM CANNOT ACCESS WINDOWS CSV

==================================================
REKOMENDASI
==================================================

Karena data real sudah tersedia di Windows repo, baseline sebaiknya dijalankan langsung dari:

E:\mt5\mt-info

menggunakan Git Bash / Windows Python.

Command yang harus digunakan dari ROOT repo Windows:

cd /e/mt5/mt-info

git status --short --branch

ls data

Pastikan:

data/XAUUSD_M5.csv
data/XAUUSD_M15.csv

kemudian:

PYTHONPATH=python python -m pytest -q

Expected current result:

118 passed

Kemudian:

PYTHONPATH=python python -m xausr.baseline --help

Setelah interface diketahui, jalankan baseline menggunakan:

data/XAUUSD_M5.csv
data/XAUUSD_M15.csv

Jangan menggunakan:

/root/mt-info/data/

kecuali filesystem tersebut memang merupakan mount yang menunjuk langsung ke:

E:\mt5\mt-info\data\

==================================================
ATURAN REPO
==================================================

Hanya boleh ada SATU working repository utama.

Jangan membuat:

/root/mt-info-copy
/root/mt-info-new
/root/mt-info-clone
E:\mt5\mt-info\mt-info

atau struktur repo bertingkat lainnya.

Jangan memindahkan source code ke folder lain.

Jangan mengubah struktur repository hanya untuk menyesuaikan Linux VM.

==================================================
SETELAH DIAGNOSIS
==================================================

BERHENTI.

Jangan menjalankan baseline dari Linux VM jika CSV Windows tidak dapat diakses.

Jangan membuat data pengganti.

Jangan commit.

Jangan push.

Laporkan hanya:

ENVIRONMENT
REPO
DATA ACCESS
RECOMMENDED NEXT STEP

Kita akan menjalankan baseline dari repo Windows yang memang memiliki data real.
```
# 
```
STOP. Ada koreksi penting terhadap laporan sebelumnya.

DATA REAL XAUUSD SUDAH TERSEDIA DAN SUDAH BERHASIL DIEKSPOR.

Jangan lagi menyatakan "data real belum tersedia".

Kondisi yang sudah TERBUKTI dari tahap sebelumnya:

- Repository lokal: E:\mt5\mt-info
- Branch: main
- Remote: origin -> https://github.com/zenolambee/mt-info.git
- data/XAUUSD_M5.csv SUDAH ADA
- data/XAUUSD_M15.csv SUDAH ADA
- M5 = 212625 bars
- M15 = 70892 bars
- M5 range = 2023-08-28 01:00:00 sampai 2026-08-26 23:55:00
- M15 range = 2023-08-28 01:00:00 sampai 2026-08-26 23:45:00
- integrity verification:
  M5 ERROR=0
  M15 ERROR=0
- M5 -> M15 coverage = 100%
- Tidak ada ERROR-level integrity problem.
- Test suite sudah berhasil:
  PYTHONPATH=python python -m pytest -q
  -> 118 passed

Masalah pada percobaan sebelumnya adalah environment/path yang berbeda, bukan ketiadaan data.

==================================================
1. JANGAN EXPORT DATA LAGI
==================================================

Jangan menjalankan mt5_export lagi.

Jangan meminta CSV baru.

Jangan menggunakan synthetic/random data.

Gunakan CSV yang SUDAH ADA di:

data/XAUUSD_M5.csv
data/XAUUSD_M15.csv

==================================================
2. PASTIKAN CWD
==================================================

Semua command berikut harus dijalankan dari ROOT REPOSITORY:

E:\mt5\mt-info

Pastikan terlebih dahulu:

pwd
git branch --show-current
git status --short --branch

Kemudian:

ls data

Pastikan terlihat:

XAUUSD_M5.csv
XAUUSD_M15.csv

Jika menggunakan Windows CMD, gunakan command yang sesuai Windows.
Jika menggunakan Git Bash, gunakan command Unix/Git Bash.

Jangan menggunakan path Linux:

/root/mt-info

karena sekarang kita sedang menguji repository Windows lokal.

==================================================
3. PYTHONPATH
==================================================

Gunakan:

PYTHONPATH=python

Karena sebelumnya tanpa PYTHONPATH muncul:

ModuleNotFoundError: No module named 'xausr'

Sedangkan:

PYTHONPATH=python python -m pytest -q

sudah berhasil:

118 passed

Pertahankan mekanisme ini.

==================================================
4. JALANKAN BASELINE REAL DATA
==================================================

Sebelum mengubah kode, baca help:

PYTHONPATH=python python -m xausr.baseline --help

Kemudian jalankan baseline menggunakan:

data/XAUUSD_M5.csv
data/XAUUSD_M15.csv

Gunakan interface baseline yang SUDAH ADA.

Jangan membuat interface baru jika tidak diperlukan.

Jika command membutuhkan:

--m5
--m15
--symbol
--outdir

gunakan path relatif dari ROOT repository.

Contoh konsep:

PYTHONPATH=python python -m xausr.baseline ^
  --m5 data/XAUUSD_M5.csv ^
  --m15 data/XAUUSD_M15.csv ^
  --symbol XAUUSD ^
  --outdir reports

Sesuaikan dengan --help jika nama argumennya berbeda.

==================================================
5. AUDIT SEBELUM BACKTEST
==================================================

Jika baseline tetap mengatakan:

"tidak ada data"

JANGAN langsung mengubah strategi.

Cari penyebab path/data loader.

Periksa:

- bagaimana baseline membaca file
- default data directory
- relative path calculation
- current working directory
- argument parser
- data loader
- file existence check

Tambahkan diagnostic sementara jika diperlukan:

- current working directory
- resolved M5 path
- resolved M15 path
- exists()
- file size

Contoh informasi yang harus bisa dibuktikan:

CWD = E:\mt5\mt-info
M5 = E:\mt5\mt-info\data\XAUUSD_M5.csv
M5 exists = True
M15 = E:\mt5\mt-info\data\XAUUSD_M15.csv
M15 exists = True

Jangan menganggap data hilang hanya karena loader tidak menemukan path.

==================================================
6. JANGAN UBAH STRATEGI
==================================================

Jangan mengubah:

- definisi Setup A
- definisi Setup B
- definisi Setup C
- definisi Setup D
- threshold
- scoring
- S/R logic
- candle pattern
- SL/TP

Tujuan sekarang hanya memastikan baseline membaca DATA REAL yang benar.

==================================================
7. SETELAH DATA TERBACA
==================================================

Jalankan baseline terhadap seluruh dataset real.

Kemudian tampilkan:

DATA
----
M5 bars:
M15 bars:
M5 period:
M15 period:

BASELINE
--------
Setup A:
Setup B:
Setup C:
Setup D:

Jika setup menghasilkan 0 sample, laporkan 0.
Jangan memaksakan signal.

==================================================
8. LOOK-AHEAD
==================================================

Setelah baseline berhasil membaca data real, lanjutkan audit causal yang sudah dibuat.

Pastikan test:

- future candle tidak mengubah historical signal
- S/R tidak membaca future candle
- confirmation hanya setelah CLOSE
- breakout hanya setelah CLOSE
- retest hanya setelah terjadi
- entry setelah confirmation
- future data hanya digunakan untuk trade outcome

Jalankan:

PYTHONPATH=python python -m pytest -q

Target minimal tetap:

118 passed

Jika jumlah test bertambah, laporkan jumlah barunya.

==================================================
9. OOS
==================================================

Jangan optimasi parameter.

Jika framework temporal split/walk-forward sudah tersedia, jalankan.

Jika belum tersedia, jangan mengarang hasil OOS.

Tulis:

OOS = NOT YET RUN

bukan "data tidak tersedia".

==================================================
10. GIT
==================================================

Jangan commit atau push.

Setelah pemeriksaan:

git status --short --branch

Pastikan data CSV tidak sengaja diubah/dihapus.

Jangan menghapus data real.

==================================================
OUTPUT WAJIB
==================================================

Laporkan:

REPOSITORY
----------
CWD:
Branch:
Remote:
Working tree:

REAL DATA
---------
M5:
M15:
M5 bars:
M15 bars:
Period:
Integrity:

DATA LOADER
-----------
M5 path resolved:
M15 path resolved:
M5 exists:
M15 exists:

TEST
----
Before:
After:

LOOK-AHEAD
----------
Status:
Tests:

BASELINE
--------
A:
B:
C:
D:

OOS
---
Status:

PROBLEMS
--------
...

CHANGES
-------
...

NEXT STEP
---------
...

PENTING:

Jangan lagi menulis "REAL DATA belum tersedia".

Data real SUDAH TERSEDIA.

Jika ada masalah, cari masalahnya di PATH / DATA LOADER / ENVIRONMENT terlebih dahulu.

Target tahap sekarang:

ROOT REPO
   ↓
data/XAUUSD_M5.csv
data/XAUUSD_M15.csv
   ↓
DATA LOADER
   ↓
BASELINE
   ↓
CAUSAL / NO LOOK-AHEAD
   ↓
TEST PASS
   ↓
BARU ANALISIS HASIL
```
# audit backtester + look-ahead bias
```
Lanjutkan project XAUUSD berdasarkan roadmap yang sudah ada.

KONDISI SAAT INI:
- Repository sudah benar dan berada di branch main.
- Remote origin sudah terhubung ke GitHub.
- Working tree terakhir sudah clean.
- Data REAL XAUUSD sudah tersedia:
  - data/XAUUSD_M5.csv
  - data/XAUUSD_M15.csv
- Data berasal dari MT5/broker, bukan synthetic data.
- Export sudah berhasil.
- Integrity verification menunjukkan ERROR=0.
- M5 → M15 consistency = 100%.
- Data mencakup sekitar 2023-08 sampai 2026-08.
- Test suite saat ini: 118 passed.
- Python package harus dijalankan dengan PYTHONPATH=python pada Windows/Git Bash.

TUJUAN TAHAP INI:

Audit dan validasi BACKTESTER yang sudah ada.

JANGAN:
- membuat strategi baru
- menambah indikator
- mengoptimasi parameter
- mengubah threshold hanya agar hasil lebih bagus
- membuat synthetic market data
- mengklaim akurasi tinggi
- membuat auto-trading
- membuat signal Telegram baru
- menghapus test lama
- merusak API/module yang sudah ada

==================================================
1. AUDIT STRUKTUR BACKTESTER
==================================================

Periksa seluruh kode yang berhubungan dengan:

- python/xausr/backtest.py
- python/xausr/baseline.py
- python/xausr/models.py
- python/xausr/indicators.py
- python/xausr/continuation.py
- python/xausr/filters.py
- python/xausr/integrity.py
- python/tests/*

Cari entry point backtest yang sebenarnya digunakan project.

Jelaskan secara internal terlebih dahulu:
- data masuk dari mana
- candle diproses bagaimana
- bagaimana M15 digunakan
- bagaimana M5 digunakan
- bagaimana S/R dibentuk
- bagaimana setup A/B/C/D dikenali
- bagaimana confirmation dikenali
- kapan entry dibuat
- bagaimana SL/TP dibuat
- bagaimana trade outcome dihitung

Jangan langsung mengubah kode.

==================================================
2. LOOK-AHEAD BIAS AUDIT
==================================================

Ini adalah prioritas utama.

Periksa apakah ada penggunaan informasi masa depan pada saat sebuah signal dibuat.

Wajib audit:

A. Market Structure
- HH
- HL
- LH
- LL
- BOS
- CHOCH

Pastikan struktur pada timestamp T hanya menggunakan candle <= T yang memang sudah tersedia.

B. Support / Resistance

Pastikan S/R yang digunakan pada entry tidak dibangun menggunakan future candles.

Contoh yang DILARANG:

Jika signal terjadi pada 2024-01-10, sistem tidak boleh menggunakan swing high yang baru diketahui pada 2024-01-15 untuk menentukan resistance pada 2024-01-10.

C. Candle Confirmation

Pastikan candle confirmation harus sudah CLOSE.

Tidak boleh:

intrabar candle -> signal

Yang diperbolehkan:

candle close -> evaluate -> signal pada waktu berikutnya

D. Breakout

Breakout hanya valid setelah candle close melewati level.

Jangan menggunakan future high/low untuk mengetahui apakah breakout berhasil.

E. Retest

Retest hanya boleh diketahui setelah retest benar-benar terjadi.

Jangan mendeteksi retest menggunakan candle masa depan lalu membuat entry seolah-olah diketahui sebelumnya.

F. SL / TP

SL/TP pada saat entry tidak boleh dihitung menggunakan future price.

G. Outcome

Future candles hanya boleh digunakan SETELAH entry untuk menentukan apakah SL atau TP terkena.

Itu adalah outcome, bukan input signal.

==================================================
3. BUAT TEST ANTI LOOK-AHEAD
==================================================

Tambahkan test regression yang secara eksplisit mendeteksi look-ahead.

Gunakan prinsip causal data.

Contoh konsep:

Jika dataset sampai timestamp T dipotong, hasil signal sampai T harus sama dengan hasil ketika dataset lengkap tersedia.

Future candle setelah T tidak boleh mengubah signal historis yang sudah terjadi.

Buat test untuk minimal:

1. future candle tidak mengubah signal historis
2. future S/R tidak mempengaruhi signal sebelumnya
3. confirmation tidak terjadi sebelum candle close
4. entry tidak terjadi sebelum confirmation
5. outcome boleh menggunakan future data hanya setelah entry

Jangan membuat test palsu yang hanya memeriksa fungsi tanpa benar-benar menguji causal behavior.

==================================================
4. AUDIT TIMESTAMP
==================================================

Pastikan urutan event jelas:

M15 candle close
    ↓
M15 structure/SR tersedia
    ↓
M5 candle close
    ↓
M5 reaction/confirmation
    ↓
signal/entry
    ↓
future candles hanya untuk outcome

Periksa timezone dan timestamp comparison.

Jangan menggeser timestamp hanya agar test lolos.

==================================================
5. AUDIT EMPAT SETUP
==================================================

Jangan mengubah definisinya.

Setup A:
Resistance Rejection
→ bearish confirmation
→ SELL

Setup B:
Resistance Breakout
→ close above resistance
→ retest
→ bullish confirmation
→ BUY

Setup C:
Support Rejection
→ bullish confirmation
→ BUY

Setup D:
Support Breakdown
→ close below support
→ retest
→ bearish confirmation
→ SELL

Pastikan setiap setup hanya dievaluasi berdasarkan informasi yang sudah tersedia pada waktunya.

==================================================
6. JALANKAN TEST SUITE
==================================================

Pertama jalankan:

PYTHONPATH=python python -m pytest -q

Jika gagal, perbaiki hanya masalah environment/import/test infrastructure yang memang diperlukan.

Jangan mengubah logic strategi hanya untuk membuat test pass.

Setelah itu jalankan test yang relevan dengan backtester dan look-ahead.

==================================================
7. JALANKAN BACKTEST REAL DATA
==================================================

Setelah audit causal selesai dan test pass, jalankan baseline menggunakan:

data/XAUUSD_M15.csv
data/XAUUSD_M5.csv

Gunakan data REAL yang sudah diexport.

Jangan menggunakan synthetic/random data sebagai hasil penelitian.

Jika command backtest membutuhkan parameter tertentu, baca help/source code terlebih dahulu dan gunakan interface yang sudah tersedia.

Jangan membuat command baru yang mengubah definisi strategi.

==================================================
8. BASELINE SAJA
==================================================

Untuk tahap ini cukup baseline.

Pisahkan:

A_RESISTANCE_REJECTION
B_RESISTANCE_BREAKOUT
C_SUPPORT_REJECTION
D_SUPPORT_BREAKDOWN

Dan pattern:

- engulfing
- pin/rejection
- strong_body
- breakout
- retest

Jangan melakukan kombinasi indikator baru.

==================================================
9. STATISTIK
==================================================

Jika backtest berhasil, tampilkan minimal:

- total samples
- total signals
- wins
- losses
- win rate
- average R
- expectancy
- profit factor
- maximum drawdown
- consecutive wins
- consecutive losses

Pisahkan hasil berdasarkan:

- setup A
- setup B
- setup C
- setup D

Dan jika engine mendukung:

- bullish M15
- bearish M15
- sideways M15

Jangan menyebut "akurasi tinggi" atau "strategi terbaik".

Sample kecil harus diberi label sample kecil.

==================================================
10. OOS
==================================================

Jangan melakukan optimasi.

Tetapkan split data yang jelas untuk evaluasi awal.

Gunakan chronological split, bukan random split.

Contoh prinsip:

OLDER DATA
→ IN-SAMPLE

NEWER DATA
→ OUT-OF-SAMPLE

Jangan menggunakan OOS untuk tuning.

Jika implementasi OOS belum tersedia dengan aman, jangan memaksakan optimasi. Cukup laporkan bahwa baseline engine sudah diaudit dan OOS framework perlu tahap berikutnya.

==================================================
11. JIKA MENEMUKAN LOOK-AHEAD
==================================================

Jika ditemukan look-ahead:

- jangan menyembunyikannya
- jangan hanya menonaktifkan test
- identifikasi file dan fungsi
- jelaskan mekanismenya
- perbaiki dengan perubahan minimal
- tambahkan regression test
- jalankan seluruh test lagi

Prioritas:
VALIDITAS > HASIL BACKTEST

==================================================
12. GIT SAFETY
==================================================

Sebelum perubahan:

git status --short --branch

Setelah perubahan:

git diff --stat
git diff

Pastikan tidak ada file data besar atau file sementara yang tidak sengaja masuk Git.

Jangan commit atau push kecuali memang diperlukan oleh workflow project.

==================================================
13. OUTPUT AKHIR
==================================================

Laporkan dengan format:

AUDIT RESULT
--------------
Repository:
Branch:
Working tree:

TEST RESULT
-----------
Before:
After:

REAL DATA
---------
M5:
M15:
Period:

LOOK-AHEAD AUDIT
----------------
Market structure:
S/R:
Confirmation:
Breakout:
Retest:
Entry:
SL/TP:
Outcome:

STATUS:
PASS / FAIL / FIXED

BASELINE
--------
Setup A:
Setup B:
Setup C:
Setup D:

OOS:
PASS / NOT YET IMPLEMENTED

PROBLEMS FOUND
--------------
...

CHANGES MADE
------------
...

NEXT STEP
---------
...

PENTING:

Jangan lanjut ke ADX, ATR, EMA, VWAP atau confluence research pada tahap ini.

Kita harus memastikan terlebih dahulu bahwa backtester benar-benar causal dan tidak memiliki look-ahead bias.

Target tahap ini:

REAL DATA
    ↓
INTEGRITY ERROR=0
    ↓
CAUSAL BACKTEST
    ↓
NO LOOK-AHEAD
    ↓
REGRESSION TEST PASS
    ↓
BASELINE RESULT
    ↓
BARU LANJUT KE RESEARCH CONFLUENCE

```
# 
```
Lanjutkan dari kondisi project saat ini.

JANGAN mengubah strategi.
JANGAN menambah indikator.
JANGAN mengubah threshold.
JANGAN membuat synthetic data.
JANGAN membuat auto-trading.

Blocker saat ini sudah jelas:
- Test suite: 118 tests OK
- Compile: OK
- Backtester: siap
- Continuation engine: sudah aktif
- Tetapi backtest real masih BLOCKED karena dataset belum tersedia di /root/mt-info/data/

Sekarang fokus hanya pada IMPORT DATA REAL XAUUSD.

1. Periksa isi:

/root/mt-info/data/

Cari apakah tersedia:

XAUUSD_m_M5.csv
XAUUSD_m_M15.csv

Juga cari kemungkinan nama file lain seperti:

XAUUSD_M5.csv
XAUUSD_M15.csv

Jangan membuat file baru berisi data palsu.

2. Jika CSV belum ada di server, jangan melakukan backtest.

Tampilkan dengan jelas:

DATA M5: MISSING / FOUND
DATA M15: MISSING / FOUND

dan jelaskan file mana yang dibutuhkan.

3. Karena sebelumnya saya sudah berhasil export data XAUUSD dari MT5, siapkan project agar dapat menerima CSV tersebut tanpa mengubah isi data.

File yang akan digunakan:

XAUUSD_m_M5.csv
XAUUSD_m_M15.csv

4. Setelah kedua file tersedia, validasi terlebih dahulu:

- header
- jumlah bar
- earliest timestamp
- latest timestamp
- timezone
- duplicate
- timestamp ordering
- invalid OHLC
- zero/negative price
- missing/gap
- M5 interval
- M15 interval
- hubungan M5 → M15
- apakah ada candle yang tidak masuk akal

Jangan mengisi missing candle dengan data buatan.

5. Jika ada gap karena weekend atau jam trading broker, bedakan:

EXPECTED MARKET GAP

dengan:

UNEXPECTED DATA GAP

Jangan menghapus data hanya untuk menghilangkan warning.

6. Pastikan symbol tetap:

XAUUSD.m

jika itu memang symbol yang digunakan pada dataset.

Jangan mengganti menjadi XAUUSD tanpa memeriksa data.

7. Jika integrity check PASS, jalankan baseline yang SUDAH ADA:

cd /root/mt-info

python3 -m xausr.baseline \
  --m5 ./data/XAUUSD_m_M5.csv \
  --m15 ./data/XAUUSD_m_M15.csv \
  --symbol XAUUSD.m \
  --outdir ./reports

8. Setelah baseline selesai, tampilkan:

DATASET
- M5 bars
- M15 bars
- periode
- timezone
- integrity result

BACKTEST
- total setup
- CONFIRMED
- NO SIGNAL
- rejection
- breakout
- retest
- continuation

CONTINUATION STATE
- BREAKOUT_DETECTED
- BREAKOUT_CONFIRMED
- WAIT_RETEST
- RETEST_DETECTED
- WAIT_CONFIRMATION
- CONFIRMED_BUY
- CONFIRMED_SELL
- BREAKOUT_FAILED
- RETEST_FAILED

ANTI-BIAS
- look-ahead
- repaint
- closed-candle confirmation
- entry timing

STATISTICS
- win rate
- loss rate
- average R:R
- expectancy
- profit factor
- max drawdown
- consecutive wins
- consecutive losses

9. Jangan melakukan optimasi setelah baseline.

Kita ingin melihat performa baseline apa adanya terlebih dahulu.

10. Jika data belum tersedia, BERHENTI.

Jangan:
- membuat data pengganti
- membuat synthetic CSV
- mengklaim backtest berhasil
- mengklaim strategi akurat
- mengubah kode hanya agar backtest bisa jalan

Setelah selesai, berikan status akhir:

REAL DATA: READY / BLOCKED
DATA INTEGRITY: PASS / FAIL
BASELINE: RUN / BLOCKED
LOOK-AHEAD: PASS / FAIL
BACKTEST: READY / BLOCKED
TESTS: ...
GIT: ...

Fokus tahap ini hanya memastikan DATA REAL → VALIDATION → BASELINE berjalan dengan benar.
```

# 
```
Lanjutkan dari kondisi project saat ini.

Jangan membuat strategi baru.
Jangan menambah indikator.
Jangan melakukan auto-trading.
Jangan menggunakan synthetic data.

Sekarang fokus hanya pada menjalankan baseline dengan DATA XAUUSD REAL.

1. Periksa terlebih dahulu:

/root/mt-info/data/

Cari:

XAUUSD_m_M5.csv
XAUUSD_m_M15.csv

Jika kedua file ADA:
- jangan meminta saya melakukan hal lain
- langsung validasi format dan integrity data
- jalankan baseline backtest

Jika salah satu file TIDAK ADA:
- jangan membuat data pengganti
- jangan menggunakan synthetic data
- jangan mengklaim backtest berhasil
- tampilkan file apa yang tersedia dan berhenti.

2. Jika kedua CSV tersedia, jalankan:

cd /root/mt-info

python3 -m xausr.baseline \
  --m5 ./data/XAUUSD_m_M5.csv \
  --m15 ./data/XAUUSD_m_M15.csv \
  --symbol XAUUSD.m \
  --outdir ./reports

3. Pastikan baseline benar-benar menggunakan:

M15:
- market structure
- support/resistance
- trend/regime

M5:
- reaction
- breakout/breakdown
- retest
- candle confirmation
- continuation state

Gunakan prinsip:

CONFIRM OR NO SIGNAL

4. Setelah selesai, jangan langsung optimasi.

Tampilkan hasil audit:

- jumlah M5
- jumlah M15
- periode data
- duplicate
- missing/gap
- timezone
- alignment M5/M15
- look-ahead check
- repaint check
- jumlah setup
- jumlah CONFIRMED
- jumlah NO SIGNAL
- alasan signal ditolak
- hasil per setup
- hasil per regime M15
- hasil continuation

5. Khusus continuation, tampilkan:

BREAKOUT_DETECTED
BREAKOUT_CONFIRMED
WAIT_RETEST
RETEST_DETECTED
WAIT_CONFIRMATION
CONFIRMED_BUY
CONFIRMED_SELL
BREAKOUT_FAILED
RETEST_FAILED

dan jumlah masing-masing state.

6. Jangan mengubah threshold atau parameter untuk memperbagus hasil.

Kita ingin melihat baseline apa adanya terlebih dahulu.

7. Setelah baseline selesai:

- jalankan test suite
- pastikan tidak ada regression
- commit perubahan jika memang ada
- push ke origin main

Jika tidak ada perubahan kode, jangan membuat commit kosong.

Terakhir berikan laporan ringkas:

DATA STATUS
BASELINE STATUS
LOOK-AHEAD STATUS
CONTINUATION STATUS
BACKTEST STATUS
TEST STATUS
GIT STATUS

Jangan menyebut sistem akurat/paling akurat sebelum hasil out-of-sample diuji.

```
# audit real-data + validasi continuation end-to-end.
```
Lanjutkan project /root/mt-info berdasarkan roadmap dan implementasi terakhir.

PENTING:
- Jangan membuat strategi baru.
- Jangan menambah indikator baru.
- Jangan auto-trading.
- Jangan mengejar win rate dengan mengubah threshold.
- Gunakan data XAUUSD M5 + M15 asli yang sudah tersedia.
- Setelah perubahan selesai, WAJIB jalankan test yang relevan, commit, lalu push ke branch main.
- Jangan hanya melaporkan kode sudah benar; lakukan verifikasi nyata.

TASK UTAMA:
Validasi continuation engine yang baru di-wire ke backtester menggunakan dataset real XAUUSD M5 + M15.

1. AUDIT DATA REAL

Periksa file:

data/XAUUSD_m_M5.csv
data/XAUUSD_m_M15.csv

Validasi:
- jumlah candle
- timestamp ordering
- duplicate
- missing candle
- OHLC invalid
- timezone
- weekend gap
- abnormal gap
- konsistensi M5
- konsistensi M15
- alignment M5 -> M15

Jangan mengisi missing candle dengan data buatan.

2. AUDIT NO LOOK-AHEAD

Periksa seluruh jalur:

data
→ structure
→ S/R
→ breakout
→ retest
→ candle confirmation
→ continuation state
→ entry
→ backtester

Pastikan tidak ada informasi future yang masuk ke keputusan candle saat ini.

Aturan wajib:
- candle confirmation harus sudah CLOSE
- breakout harus confirmed setelah CLOSE
- retest hanya boleh diketahui setelah retest benar-benar terjadi
- continuation state tidak boleh mengetahui candle berikutnya
- entry timestamp harus setelah confirmation
- S/R tidak boleh menggunakan swing future
- SL/TP tidak boleh menggunakan future information

Jika menemukan potensi look-ahead, perbaiki implementasinya dan tambahkan regression test.

3. AUDIT CONTINUATION STATE MACHINE

Pastikan state continuation memiliki lifecycle yang jelas:

BREAKOUT_DETECTED
→ BREAKOUT_CONFIRMED
→ WAIT_RETEST
→ RETEST_DETECTED
→ WAIT_CONFIRMATION
→ CONFIRMED_BUY / CONFIRMED_SELL

Jika breakout gagal:
→ BREAKOUT_FAILED

Jika retest invalid:
→ RETEST_FAILED

Jika confirmation tidak muncul:
→ NO SIGNAL

Tidak boleh langsung menghasilkan BUY/SELL hanya karena harga menembus level.

4. RESISTANCE BREAKOUT

Untuk BUY continuation wajib:

M15 structure sesuai
+
Resistance valid
+
M5 breakout
+
candle M5 CLOSE di atas resistance
+
breakout valid
+
retest valid
+
retest hold
+
bullish confirmation candle CLOSE
=
CONFIRMED BUY CONTINUATION

Jika salah satu syarat penting gagal:

NO SIGNAL

5. SUPPORT BREAKDOWN

Untuk SELL continuation wajib:

M15 structure sesuai
+
Support valid
+
M5 breakdown
+
candle M5 CLOSE di bawah support
+
breakdown valid
+
retest valid
+
retest gagal reclaim level
+
bearish confirmation candle CLOSE
=
CONFIRMED SELL CONTINUATION

Jika salah satu syarat penting gagal:

NO SIGNAL

6. REJECTION JANGAN DISAMAKAN DENGAN CONTINUATION

Pastikan engine membedakan:

Resistance Rejection
Support Rejection
Resistance Breakout Continuation
Support Breakdown Continuation

Jangan menganggap setiap touch S/R sebagai signal.

7. ENTRY HARUS UNTUK TARGET PENDEK

Tujuan sistem kita bukan mencari pergerakan ribuan pips.

Kita ingin menemukan entry berkualitas untuk mengambil pergerakan pendek/intraday setelah confirmation.

Karena itu jangan membuat TP terlalu jauh hanya untuk memperbesar statistik.

Evaluasi apakah entry memiliki:
- invalidation yang jelas
- SL realistis
- target realistis
- R:R masuk akal
- ruang harga yang cukup sebelum S/R berikutnya

Jika ruang terlalu sempit:

NO SIGNAL

8. BACKTEST

Jalankan backtest menggunakan:

M15 = structure + S/R
M5  = confirmation + entry

Jangan optimasi parameter dulu.

Laporkan secara terpisah:

- rejection
- breakout continuation
- breakdown continuation
- retest
- candle confirmation

Pisahkan:
- bullish M15
- bearish M15
- sideways M15

9. EDGE CASE

Tambahkan regression test untuk kasus:

- breakout lalu langsung kembali ke zona
- wick menembus resistance tetapi close kembali di bawah
- wick menembus support tetapi close kembali di atas
- breakout tanpa retest
- retest terlalu dalam
- retest gagal
- confirmation candle belum close
- confirmation muncul setelah setup invalid
- breakout terjadi berkali-kali pada zona yang sama
- gap market
- weekend gap
- data M5 missing
- M15 tidak memiliki pasangan M5 lengkap

Semua harus menghasilkan state yang deterministik dan tidak menggunakan future data.

10. OUTPUT AUDIT

Buat laporan singkat yang menjawab:

- Apakah continuation engine benar-benar aktif di backtester?
- Apakah state transition benar?
- Apakah ada look-ahead?
- Apakah ada repaint?
- Apakah M5/M15 alignment benar?
- Berapa setup continuation yang ditemukan?
- Berapa yang CONFIRMED?
- Berapa yang NO SIGNAL?
- Apa alasan utama signal ditolak?
- Apakah ada bug yang ditemukan?

Jangan menyebut sistem "akurat" hanya berdasarkan hasil ini.

11. TEST

Jalankan seluruh test suite yang relevan.

Minimal:
- unit test
- continuation test
- backtester test
- data integrity test
- look-ahead regression test

Pastikan test lama tidak rusak.

12. GIT

Jika ada perubahan kode:

git status
git diff
jalankan test
commit dengan message yang jelas
push ke origin main

Setelah push, tampilkan:
- commit hash
- branch
- test result
- ringkasan perubahan

Jangan berhenti hanya setelah menulis kode.

TARGET TAHAP INI:

Bukan menambah fitur.

Targetnya adalah memastikan:

REAL XAUUSD DATA
→ M15 STRUCTURE
→ S/R
→ M5 BREAKOUT/REJECTION
→ RETEST
→ CLOSED CANDLE CONFIRMATION
→ CONTINUATION STATE
→ CONFIRMED / NO SIGNAL
→ BACKTEST

benar-benar berjalan end-to-end tanpa look-ahead dan tanpa memaksakan signal.
```
# 
```
Lanjutkan project dari kondisi TERAKHIR yang sudah ada.

Konteks penting:
- Project XAUUSD Support/Resistance Confirmation System.
- TF utama tetap M15 + M5.
- M15 = menentukan WHERE: market structure + Support/Resistance.
- M5 = menentukan WHEN: reaction + breakout/rejection + retest + candle confirmation.
- Continuation engine sudah dibuat pada commit sebelumnya:
  48d72e7 - feat: add S/R continuation confirmation engine
- Sebelumnya test suite berhasil:
  94 tests passed.
- Perubahan sebelumnya sudah di-push ke GitHub.
- Data XAUUSD real sudah berhasil diexport dari MT5/broker.
- Dataset yang tersedia sebelumnya:
  data/XAUUSD_m_M5.csv
  data/XAUUSD_m_M15.csv
- Jangan membuat synthetic market data.
- Jangan membuat strategi baru.
- Jangan menambah timeframe.
- Jangan menambah indikator.
- Jangan menggunakan AI di dalam signal engine pada tahap ini.
- Jangan membuat auto-trading.

==================================================
TUJUAN TAHAP INI
==================================================

Sekarang kita harus memastikan continuation engine yang sudah dibuat BENAR-BENAR terhubung ke backtester.

Jangan hanya melakukan static code review.

Lakukan audit → integrasi → test → backtest → evaluasi.

Arsitektur yang harus dipertahankan:

M15
  ↓
Market Structure
  ↓
Support / Resistance Zone
  ↓
M5 Reaction
  ↓
Breakout / Rejection
  ↓
Retest
  ↓
Candle CLOSE Confirmation
  ↓
Continuation Validation
  ↓
Risk/Reward
  ↓
CONFIRMED SIGNAL / NO SIGNAL

==================================================
1. AUDIT IMPLEMENTASI SEKARANG
==================================================

Periksa seluruh repository terlebih dahulu.

Cari dan pahami:

- continuation.py
- backtest.py
- baseline runner
- stats.py
- S/R detection
- market structure
- breakout/rejection logic
- retest logic
- candle confirmation
- signal generation
- dataset loader
- test suite

Jangan mengasumsikan nama file berdasarkan prompt.

Gunakan struktur repository yang benar-benar ada.

Pastikan continuation engine benar-benar dipanggil oleh backtester.

Jika continuation.py ada tetapi tidak pernah dipanggil oleh runner, perbaiki integrasinya.

Jangan membuat duplikasi engine.

==================================================
2. DATA REAL
==================================================

Gunakan data real yang sudah tersedia.

Prioritas:

M15:
data/XAUUSD_m_M15.csv

M5:
data/XAUUSD_m_M5.csv

Jika path berbeda, cari file dataset yang benar terlebih dahulu.

Jangan membuat data baru.

Jangan mengisi missing candle dengan candle sintetis.

Jangan mengubah harga historis.

Pastikan loader membaca timestamp, OHLC dan volume dengan benar.

==================================================
3. VALIDASI DATA SEBELUM BACKTEST
==================================================

Sebelum menjalankan strategi:

- validasi timestamp
- validasi ordering
- duplicate
- invalid OHLC
- timezone
- gap
- M5/M15 alignment
- coverage periode
- apakah M15 berasal dari data yang konsisten dengan M5

Jangan menghentikan backtest hanya karena weekend gap normal.

Bedakan:

NORMAL MARKET GAP
vs
DATA CORRUPTION

Jika ada gap broker normal, catat sebagai gap.

Jika ada gap abnormal/data corruption, laporkan.

==================================================
4. AUDIT NO LOOK-AHEAD
==================================================

Ini WAJIB.

Pastikan setiap keputusan pada candle T hanya menggunakan data yang tersedia sampai candle T.

Khusus:

S/R:
- tidak boleh memakai swing masa depan untuk keputusan entry masa lalu.

Market structure:
- tidak boleh mengetahui HH/HL/LH/LL yang baru terbentuk di masa depan.

Breakout:
- jangan valid hanya karena High menembus level.
- breakout harus dikonfirmasi setelah candle CLOSE.

Retest:
- retest harus terjadi setelah breakout.
- jangan mendeteksi retest menggunakan candle sebelum breakout.

Continuation:
- tidak boleh menganggap continuation valid sebelum confirmation selesai.

Entry:
- timestamp entry harus sesudah candle confirmation CLOSE.

SL/TP:
- jangan menggunakan future high/low untuk menentukan entry.

Jika ditemukan look-ahead bias:
STOP.
Perbaiki terlebih dahulu.
Kemudian jalankan test ulang.

==================================================
5. INTEGRASIKAN CONTINUATION ENGINE
==================================================

Continuation engine harus menangani dua setup:

A. Resistance Breakout Continuation

Harga:
naik
↓
mendekati resistance
↓
break resistance
↓
M5 candle CLOSE di atas resistance
↓
retest resistance
↓
resistance bertahan sebagai support
↓
bullish confirmation
↓
CONFIRMED BUY CONTINUATION

B. Support Breakdown Continuation

Harga:
turun
↓
mendekati support
↓
break support
↓
M5 candle CLOSE di bawah support
↓
retest support
↓
support gagal sebagai resistance
↓
bearish confirmation
↓
CONFIRMED SELL CONTINUATION

Jangan menganggap:

High > resistance

sebagai breakout valid.

Dan jangan menganggap:

Low < support

sebagai breakdown valid.

==================================================
6. CONFIRMATION HARUS CLOSE
==================================================

Signal tidak boleh muncul intrabar.

Gunakan candle yang sudah selesai/close.

Contoh BUY:

M5 breakout candle close
↓
retest terjadi
↓
retest confirmation close
↓
bullish confirmation close
↓
baru signal BUY

Jika candle masih berjalan:

NO SIGNAL.

==================================================
7. REJECTION TETAP DIPERTAHANKAN
==================================================

Jangan merusak setup rejection yang sudah ada.

Tetap pisahkan:

Resistance Rejection → SELL

Support Rejection → BUY

Resistance Breakout + Retest → BUY

Support Breakdown + Retest → SELL

Jangan mencampurkan rejection dengan continuation.

==================================================
8. STATE MACHINE
==================================================

Jika saat ini continuation menggunakan state machine, audit state transition-nya.

Contoh:

IDLE
↓
LEVEL_REACHED
↓
BREAKOUT_CONFIRMED
↓
WAIT_RETEST
↓
RETEST_CONFIRMED
↓
WAIT_CONFIRMATION
↓
CONFIRMED
↓
SIGNAL

Untuk failure:

BREAKOUT_CONFIRMED
↓
RETEST_FAILED
↓
BREAKOUT_FAILED / NO SIGNAL

atau:

WAIT_RETEST
↓
timeout
↓
NO SIGNAL

Jangan mempertahankan state continuation terlalu lama sehingga setup lama bisa menghasilkan signal jauh setelah kondisi awal sudah tidak relevan.

==================================================
9. TIMEOUT / EXPIRATION
==================================================

Periksa apakah continuation setup memiliki batas waktu/bar.

Retest tidak boleh dianggap valid tanpa batas.

Jika implementasi sekarang sudah memiliki timeout:

audit dan test.

Jika belum ada timeout dan penambahannya benar-benar diperlukan agar state machine tidak stale, implementasikan dengan parameter yang jelas dan konservatif.

Jangan melakukan optimasi parameter.

==================================================
10. BASELINE VS CONTINUATION
==================================================

Backtester harus bisa membedakan:

BASELINE
dan
BASELINE + CONTINUATION CONFIRMATION

Jangan mengubah baseline secara diam-diam.

Tujuannya melihat apakah continuation confirmation benar-benar memberikan nilai tambah.

Laporkan:

Baseline:
- total setup
- signal
- win/loss
- expectancy
- profit factor
- drawdown

Continuation enabled:
- total setup
- signal
- win/loss
- expectancy
- profit factor
- drawdown

==================================================
11. TEST CASE
==================================================

Tambahkan/ubah test hanya jika diperlukan.

Minimal test:

1. breakout tanpa CLOSE confirmation
   → NO SIGNAL

2. breakout close valid
   → state berubah

3. breakout tetapi tidak ada retest
   → NO SIGNAL

4. retest gagal
   → NO SIGNAL

5. retest valid + bullish confirmation
   → BUY continuation

6. breakdown valid + retest + bearish confirmation
   → SELL continuation

7. candle confirmation masih open
   → NO SIGNAL

8. breakout terjadi tetapi kemudian kembali ke dalam zone
   → breakout failed / NO SIGNAL

9. S/R menggunakan future data
   → test harus mendeteksi / mencegah

10. entry timestamp tidak boleh lebih awal dari confirmation close.

11. state continuation lama tidak boleh menghasilkan signal setelah expired.

12. M15 context tidak boleh memakai candle M15 yang belum close.

==================================================
12. JANGAN OPTIMASI DULU
==================================================

PENTING:

Jangan mengejar win rate.

Jangan mengubah threshold hanya supaya hasil backtest lebih bagus.

Jangan melakukan parameter sweep besar.

Jangan memilih parameter terbaik berdasarkan hasil historis.

Tahap ini hanya untuk:

VALIDASI LOGIKA
+
INTEGRASI
+
ANTI LOOK-AHEAD
+
BASELINE COMPARISON

==================================================
13. BACKTEST REAL DATA
==================================================

Setelah test lolos, jalankan backtest menggunakan dataset real yang tersedia.

Gunakan periode data yang memang tersedia.

Jangan mengarang periode.

Jika dataset dimulai pada 2024-08-26 dan berakhir 2026-08-25, gunakan periode aktual tersebut.

Pisahkan hasil jika runner mendukung:

- in-sample
- validation
- out-of-sample

Jika pembagian belum tersedia, jangan membuat pembagian yang mengubah strategi.

Laporkan kemampuan runner saat ini.

==================================================
14. STATISTIK
==================================================

Minimal tampilkan:

- total bars
- total setup
- total signal
- BUY
- SELL
- NO SIGNAL
- win
- loss
- win rate
- average R:R
- expectancy
- profit factor
- max drawdown
- consecutive wins
- consecutive losses

Pisahkan:

Resistance Rejection
Resistance Breakout Continuation
Support Rejection
Support Breakdown Continuation

Dan:

M15 bullish
M15 bearish
M15 sideways

==================================================
15. SAMPLE DETAIL
==================================================

Jangan hanya memberikan statistik agregat.

Tampilkan beberapa contoh signal nyata dari dataset.

Untuk setiap contoh:

timestamp
direction
M15 trend
S/R level
setup type
breakout/rejection
retest
confirmation candle
entry
SL
TP
result

Tujuannya agar kita bisa memeriksa apakah logika yang dihitung code memang sesuai dengan chart.

==================================================
16. IMPORTANT: ENTRY BUKAN RIBUAN PIPS
==================================================

Sistem ini bukan dibuat untuk menangkap pergerakan ratusan/ribuan pips.

Tujuan kita adalah menemukan:

ENTRY YANG TERKONFIRMASI
pada area yang jelas
dengan continuation/rejection yang valid.

Contoh konsep:

M15 menentukan area.

M5 menunggu reaksi.

Jika resistance:
break → retest → confirmation → entry.

Jika support:
break → retest → confirmation → entry.

Jika rejection:
touch zone → rejection → confirmation → entry.

Jangan memperbesar TP hanya untuk membuat hasil terlihat bagus.

Gunakan Risk/Reward yang realistis sesuai implementasi saat ini.

==================================================
17. JANGAN TAMBAH TIMEFRAME
==================================================

Tetap:

M15 = structure + S/R
M5 = confirmation + entry

Jangan menambahkan:

M1
M30
H1
H4

kecuali audit membuktikan secara teknis bahwa M15 + M5 tidak cukup dan ada alasan kuat yang dapat ditunjukkan dengan data.

Untuk tahap ini:

TIDAK BOLEH MENAMBAH TF.

==================================================
18. JANGAN TAMBAH AI
==================================================

Tidak perlu AI/ML di dalam signal engine sekarang.

Kita harus membuktikan dulu rule-based engine menggunakan data nyata.

AI baru boleh dipertimbangkan setelah baseline rule-based benar-benar tervalidasi dan kita mempunyai dataset serta alasan eksperimen yang jelas.

==================================================
19. TEST FINAL
==================================================

Jalankan:

- seluruh unit test
- integration test
- compile check
- backtest real data

Pastikan tidak ada regression.

Jika test gagal:

perbaiki penyebabnya.

Jangan menonaktifkan test hanya agar suite PASS.

==================================================
20. GIT
==================================================

Jika semua perubahan sudah benar:

git status
git diff
git log

Pastikan hanya perubahan yang berkaitan dengan tahap ini.

Buat commit dengan pesan yang jelas.

Kemudian PUSH ke branch/repository yang memang digunakan project.

Jangan force push.

==================================================
21. OUTPUT WAJIB
==================================================

Setelah selesai berikan laporan:

1. File yang diperiksa.
2. File yang diubah.
3. Integrasi continuation berhasil atau tidak.
4. Apakah ada look-ahead bias.
5. Apakah ada repaint logic.
6. Apakah confirmation benar-benar menunggu CLOSE.
7. Jumlah test sebelum/sesudah.
8. Hasil test.
9. Hasil baseline.
10. Hasil continuation.
11. Contoh signal nyata.
12. Masalah yang ditemukan.
13. Commit hash.
14. Status push.

Jika ada bagian yang belum bisa divalidasi, katakan terus terang.

Jangan mengatakan "akurat" hanya karena test PASS.

Target tahap ini:

Membuktikan bahwa:

M15 Structure
+
M15 S/R
+
M5 Reaction
+
Breakout/Rejection
+
Retest
+
Candle CLOSE Confirmation
+
Continuation Engine

benar-benar bekerja secara temporal dan dapat diuji pada data XAUUSD real.

Jika semua sudah PASS, BERHENTI.

Jangan lanjut ke indikator baru, AI, timeframe baru, Telegram baru, atau auto-trading sebelum saya memberikan instruksi berikutnya.
```
# S/R + rejection + breakout/breakdown + retest + candle confirmation
```
Lanjutkan project mt-info dari commit terakhir yang sudah berhasil di-push ke main.

Commit terakhir:
48d72e7 — feat: add S/R continuation confirmation engine

94 tests sudah PASS, compile semua module OK, dan push ke main berhasil.

TAHAP SEKARANG:
Real-data backtest validation untuk XAUUSD M5 + M15.

JANGAN membuat strategi baru.
JANGAN menambah indikator baru.
JANGAN melakukan auto-trading.
JANGAN menggunakan synthetic data sebagai bukti.
JANGAN mengubah threshold hanya untuk memperbagus hasil.

DATA REAL YANG SUDAH TERSEDIA:
data/XAUUSD_m_M5.csv
data/XAUUSD_m_M15.csv

Gunakan dataset tersebut sebagai sumber utama backtest.

==================================================
1. AUDIT BACKTESTER
==================================================

Audit terlebih dahulu seluruh pipeline backtest yang sudah ada.

Periksa:

- data loader
- timeframe handling
- M5/M15 alignment
- market structure
- Support/Resistance
- rejection
- breakout/breakdown
- retest
- candle confirmation
- continuation gate
- entry
- SL/TP
- scoring
- statistics

Jangan menghapus implementasi existing.

==================================================
2. ANTI LOOK-AHEAD
==================================================

Ini WAJIB.

Pastikan:

- S/R hanya menggunakan informasi yang sudah tersedia pada timestamp tersebut.
- M15 structure tidak membaca candle masa depan.
- Candle confirmation hanya menggunakan candle yang SUDAH CLOSE.
- Breakout baru valid setelah candle breakout CLOSE.
- Retest baru valid setelah retest benar-benar terjadi.
- Confirmation setelah retest tidak boleh memakai candle masa depan.
- Entry timestamp harus selalu setelah confirmation.
- SL/TP tidak boleh menentukan entry menggunakan future data.
- Tidak ada repaint logic.

Tambahkan/kuatkan regression test untuk memastikan tidak terjadi look-ahead bias.

==================================================
3. CONTINUATION ENGINE
==================================================

Uji continuation engine yang baru ditambahkan.

Resistance breakout:

RESISTANCE
↓
breakout
↓
M5 candle CLOSE di atas resistance
↓
valid breakout
↓
retest
↓
retest hold
↓
bullish confirmation CLOSE
↓
CONFIRMED BUY CONTINUATION

Support breakdown:

SUPPORT
↓
breakdown
↓
M5 candle CLOSE di bawah support
↓
valid breakdown
↓
retest
↓
retest gagal reclaim
↓
bearish confirmation CLOSE
↓
CONFIRMED SELL CONTINUATION

Jangan menganggap wick penetration sebagai breakout valid.

==================================================
4. REJECTION ENGINE
==================================================

Uji secara terpisah:

A. Resistance rejection → SELL

B. Support rejection → BUY

Rejection harus mempertimbangkan:

- zone
- wick
- body
- close position
- structure
- confirmation candle

Tidak boleh langsung signal hanya karena harga menyentuh level.

==================================================
5. EMPAT SETUP
==================================================

Backtest empat setup secara terpisah:

1. Resistance Rejection → SELL
2. Resistance Breakout + Retest + Bullish Confirmation → BUY
3. Support Rejection + Bullish Confirmation → BUY
4. Support Breakdown + Retest + Bearish Confirmation → SELL

Jangan mencampur hasilnya.

==================================================
6. CANDLE CONFIRMATION
==================================================

Pisahkan statistik untuk:

- Bullish Engulfing
- Bearish Engulfing
- Bullish Rejection / Pin Bar
- Bearish Rejection / Pin Bar
- Strong Bullish Body
- Strong Bearish Body
- Breakout Candle
- Breakdown Candle
- Retest Confirmation

Jangan menyimpulkan pattern terbaik hanya dari jumlah win rate.

==================================================
7. DATA SPLIT
==================================================

Gunakan pemisahan waktu yang benar.

Pisahkan:

- In-sample
- Validation
- Out-of-sample

Jangan tuning parameter berdasarkan OOS.

Jika implementasi walk-forward sudah tersedia dan aman digunakan, jalankan juga.

==================================================
8. STATISTIK
==================================================

Untuk setiap setup dan candle confirmation tampilkan:

- total samples
- signal count
- wins
- losses
- win rate
- average R:R
- expectancy
- profit factor
- maximum drawdown
- consecutive wins
- consecutive losses

Pisahkan juga berdasarkan:

- M15 bullish
- M15 bearish
- M15 sideways
- rejection
- breakout
- retest
- continuation

==================================================
9. CONFIRM OR NO SIGNAL
==================================================

Pastikan engine tetap mengikuti:

VALID STRUCTURE
+
VALID S/R
+
VALID PRICE REACTION
+
VALID BREAKOUT/REJECTION
+
VALID RETEST bila diperlukan
+
CANDLE CLOSE CONFIRMATION
+
VALID R:R
=
CONFIRMED SIGNAL

Jika salah satu syarat penting tidak terpenuhi:

NO SIGNAL

Jangan memaksa sistem menghasilkan BUY/SELL.

==================================================
10. OUTPUT REPORT
==================================================

Buat laporan hasil backtest yang jelas.

Minimal berisi:

DATA
- symbol
- timeframe
- earliest timestamp
- latest timestamp
- total candles

BACKTEST
- total setups
- total signals
- total NO SIGNAL
- statistik setiap setup
- statistik setiap candle confirmation

VALIDATION
- in-sample
- validation
- out-of-sample
- walk-forward jika tersedia

BIAS CHECK
- look-ahead
- repaint
- future candle leakage
- timestamp issue

==================================================
11. ATURAN KESIMPULAN
==================================================

Jangan mengatakan:

"akurasi tinggi"
"paling akurat"
"strategi terbaik"

kecuali benar-benar didukung sample yang memadai dan hasil OOS/walk-forward.

Jika pattern/setup tidak memberikan edge yang konsisten:

DISABLED / WATCHLIST

bukan dipaksa menjadi signal.

==================================================
12. TEST
==================================================

Setelah implementasi/perbaikan:

- jalankan seluruh test suite
- jalankan compile check
- jalankan real-data backtest
- pastikan tidak ada regression

Jangan skip test yang berkaitan langsung dengan engine.

==================================================
13. GIT
==================================================

Jika semua test PASS dan hasil implementasi valid:

1. git status
2. git diff
3. commit dengan message:

feat: validate XAUUSD real-data continuation backtest

4. push ke main

Jangan push jika test gagal.

==================================================
TARGET TAHAP INI
==================================================

Bukan membuat lebih banyak fitur.

Target hanya:

REAL XAUUSD DATA
↓
VALID BACKTEST
↓
NO LOOK-AHEAD
↓
SETUP STATISTICS
↓
OOS VALIDATION
↓
TENTUKAN SETUP YANG LAYAK DILANJUTKAN

Setelah selesai, tampilkan:

- hasil test
- hasil backtest
- statistik masing-masing setup
- hasil OOS
- masalah yang ditemukan
- commit hash
- status push

Jangan membuat auto-trading.
Jangan membuat Telegram signal baru pada tahap ini.
```
# Prompt berikutnya fokus implementasi langsung fitur candle continuation + Support/Resistance + rejection/breakout/retest
```
Lanjutkan implementasi project XAUUSD berdasarkan roadmap yang sudah ada.

Kali ini JANGAN hanya melakukan review atau membuat dokumentasi. IMPLEMENTASIKAN FITUR LANGSUNG ke codebase yang ada.

Setelah implementasi selesai:
1. Jalankan test yang relevan.
2. Perbaiki error yang ditemukan.
3. Pastikan tidak ada perubahan yang merusak fitur sebelumnya.
4. Commit semua perubahan.
5. Push langsung ke repository Git yang sedang digunakan.
6. Laporkan commit hash dan hasil test.

==================================================
FITUR UTAMA — CANDLE CONTINUATION + S/R
==================================================

Tujuan:

Sistem harus dapat memahami apakah candle setelah Support/Resistance, rejection, breakout, atau retest benar-benar melakukan CONTINUATION.

Jangan menganggap:

GREEN CANDLE = BUY
RED CANDLE = SELL

Sistem harus memahami konteks harga.

Alur utama:

M15 STRUCTURE
    ↓
SUPPORT / RESISTANCE ZONE
    ↓
PRICE REACHES ZONE
    ↓
REACTION
    ↓
REJECTION / BREAKOUT / BREAKDOWN
    ↓
RETEST
    ↓
CANDLE CONFIRMATION
    ↓
CONTINUATION
    ↓
CONFIRMED SETUP / NO SIGNAL


==================================================
1. SUPPORT / RESISTANCE SEBAGAI ZONA
==================================================

Pastikan Support dan Resistance tidak diperlakukan hanya sebagai satu harga.

Gunakan zona berdasarkan struktur yang sudah tersedia di project.

Zona dapat berasal dari:

- swing high
- swing low
- repeated rejection
- consolidation
- previous support
- previous resistance
- S/R flip

Simpan informasi minimal:

- zone type
- zone high
- zone low
- strength
- touch count
- source
- timeframe

Jangan menggunakan informasi candle masa depan untuk menentukan zona pada timestamp historis.


==================================================
2. RESISTANCE REJECTION
==================================================

Implementasikan deteksi:

Harga naik
↓
Masuk Resistance Zone
↓
Wick/rejection
↓
Close kembali di bawah resistance
↓
Bearish confirmation
↓
Candle berikutnya menunjukkan continuation turun

Jangan langsung menganggap candle pertama yang menyentuh resistance sebagai SELL.

Status harus dapat dibedakan:

- APPROACHING_RESISTANCE
- TESTING_RESISTANCE
- REJECTION_DETECTED
- BEARISH_CONFIRMATION
- BEARISH_CONTINUATION
- INVALIDATED


==================================================
3. SUPPORT REJECTION
==================================================

Kebalikan dari resistance:

Harga turun
↓
Masuk Support Zone
↓
Rejection
↓
Close kembali di atas support
↓
Bullish confirmation
↓
Candle berikutnya menunjukkan continuation naik

Status:

- APPROACHING_SUPPORT
- TESTING_SUPPORT
- REJECTION_DETECTED
- BULLISH_CONFIRMATION
- BULLISH_CONTINUATION
- INVALIDATED


==================================================
4. RESISTANCE BREAKOUT CONTINUATION
==================================================

Jangan menganggap:

HIGH > RESISTANCE = BREAKOUT

Breakout harus menggunakan candle CLOSE.

Minimal:

1. Harga menembus resistance.
2. Candle M5 close di atas resistance zone.
3. Breakout body/range cukup signifikan berdasarkan data yang tersedia.
4. Harga tidak langsung gagal kembali ke bawah zone.
5. Jika terjadi retest, retest harus dievaluasi.
6. Muncul bullish confirmation.
7. Candle berikutnya menunjukkan continuation.

Status:

RESISTANCE_BREAK_ATTEMPT
RESISTANCE_BREAK_CONFIRMED
BREAKOUT_RETEST
BREAKOUT_RETEST_HOLD
BULLISH_CONFIRMATION
BULLISH_CONTINUATION
BREAKOUT_FAILED


==================================================
5. SUPPORT BREAKDOWN CONTINUATION
==================================================

Kebalikan:

1. Harga menembus support.
2. Candle M5 close di bawah support zone.
3. Breakdown cukup signifikan.
4. Harga melakukan retest jika terjadi.
5. Retest gagal kembali di atas support.
6. Bearish confirmation.
7. Candle berikutnya menunjukkan continuation turun.

Status:

SUPPORT_BREAK_ATTEMPT
SUPPORT_BREAK_CONFIRMED
BREAKDOWN_RETEST
BREAKDOWN_RETEST_FAIL
BEARISH_CONFIRMATION
BEARISH_CONTINUATION
BREAKDOWN_FAILED


==================================================
6. CANDLE CONTINUATION ENGINE
==================================================

Buat logic khusus untuk menentukan CONTINUATION.

Continuation harus dievaluasi dari candle yang sudah CLOSE.

Contoh bullish continuation:

Confirmation candle:
    bullish

Candle berikutnya:
    close > confirmation close
    atau memenuhi aturan continuation yang sudah didefinisikan

Maka:

BULLISH_CONTINUATION

Contoh bearish:

Confirmation candle:
    bearish

Candle berikutnya:
    close < confirmation close
    atau memenuhi aturan continuation yang sudah didefinisikan

Maka:

BEARISH_CONTINUATION


Jangan menggunakan candle masa depan untuk menghasilkan signal pada candle sebelumnya.

Pastikan timestamp signal selalu berada setelah candle confirmation benar-benar CLOSE.


==================================================
7. BEDAKAN CONFIRMATION DAN CONTINUATION
==================================================

Jangan gabungkan kedua konsep.

Contoh:

Resistance
↓
Rejection candle
↓
CONFIRMATION
↓
Candle berikutnya
↓
CONTINUATION

Jika confirmation ada tetapi continuation belum terjadi:

status:

CONFIRMED_WAITING_CONTINUATION

Bukan langsung:

CONFIRMED BUY/SELL


Jika continuation gagal:

INVALIDATED / NO SIGNAL


==================================================
8. RETEST
==================================================

Retest harus menjadi event tersendiri.

Untuk resistance breakout:

Resistance
↓
Breakout
↓
Close above
↓
Return to resistance zone
↓
Zone bertahan sebagai support
↓
Bullish confirmation
↓
Continuation

Untuk support breakdown:

Support
↓
Breakdown
↓
Close below
↓
Return to support zone
↓
Zone gagal menjadi resistance
↓
Bearish confirmation
↓
Continuation


==================================================
9. FALSE BREAKOUT
==================================================

Deteksi false breakout.

Contoh:

Resistance
↓
Wick/high menembus
↓
Close kembali di bawah resistance
↓
Tidak ada continuation bullish

Jangan menghasilkan BUY.

Status:

FALSE_BREAKOUT
NO_SIGNAL

Hal yang sama untuk support.


==================================================
10. M15 → M5
==================================================

Tetap gunakan:

M15 = WHERE
M5  = WHEN

M15:

- structure
- trend
- major support
- major resistance

M5:

- reaction
- breakout
- breakdown
- retest
- confirmation
- continuation

Jangan membalik fungsi timeframe.


==================================================
11. SIGNAL STATE MACHINE
==================================================

Jika arsitektur project memungkinkan, gunakan state machine agar setup tidak langsung berubah menjadi BUY/SELL.

Contoh:

IDLE
 ↓
APPROACHING_ZONE
 ↓
TESTING_ZONE
 ↓
REJECTION / BREAKOUT / BREAKDOWN
 ↓
CONFIRMATION
 ↓
WAITING_CONTINUATION
 ↓
CONTINUATION
 ↓
CONFIRMED_SETUP

Jika gagal:

INVALIDATED
 ↓
NO_SIGNAL


==================================================
12. STRICT NO SIGNAL
==================================================

Jangan memaksa signal.

Jika:

- S/R tidak jelas
- candle belum close
- rejection belum confirmed
- breakout belum confirmed
- retest gagal
- continuation belum terjadi
- M15 structure konflik
- setup invalidated

maka:

NO SIGNAL


==================================================
13. CHART / OUTPUT
==================================================

Jika project memiliki output/chart annotation, tampilkan event secara jelas.

Contoh:

RESISTANCE
──────────────
      ↑
   TESTING
      ↑
   REJECTION
      ↓
 CONFIRMATION
      ↓
 CONTINUATION
      ↓
    SELL


Untuk breakout:

RESISTANCE
──────────────
      ↑
   BREAKOUT
      ↑
     RETEST
      ↑
 CONFIRMATION
      ↑
 CONTINUATION
      ↑
     BUY


Jangan hanya menampilkan BUY/SELL.

Simpan alasan setup.


==================================================
14. DATA DAN BACKTEST
==================================================

Gunakan data XAUUSD real yang sudah tersedia.

Jangan membuat synthetic market data.

Tambahkan unit/integration test untuk:

- resistance rejection
- support rejection
- resistance breakout
- support breakdown
- breakout retest
- breakdown retest
- bullish continuation
- bearish continuation
- false breakout
- incomplete confirmation
- invalidated setup
- candle belum close
- look-ahead protection

Jika data real belum tersedia untuk test tertentu, gunakan fixture/unit test yang jelas hanya untuk menguji logic, bukan untuk mengklaim performa strategi.


==================================================
15. ANTI LOOK-AHEAD
==================================================

Wajib audit.

Tidak boleh:

- membaca candle masa depan
- menggunakan future high/low untuk menentukan S/R historis
- menggunakan candle continuation untuk menentukan confirmation candle
- menghasilkan signal sebelum candle CLOSE
- melakukan repaint signal historis

Tambahkan test khusus jika belum tersedia.


==================================================
16. JANGAN MENAMBAH INDIKATOR
==================================================

Untuk tahap ini jangan menambahkan:

- RSI
- MACD
- Bollinger Bands
- stochastic
- indikator lain

Fokus hanya:

M15 Structure
+
Support/Resistance
+
Rejection
+
Breakout/Breakdown
+
Retest
+
Candle Confirmation
+
Continuation


==================================================
17. CODE QUALITY
==================================================

Jangan membuat satu file besar.

Pisahkan logic jika arsitektur project sudah modular.

Minimal pisahkan konsep:

- support/resistance detection
- reaction/rejection detection
- breakout/breakdown detection
- retest detection
- candle confirmation
- continuation detection
- signal state
- tests

Gunakan module yang sudah ada jika cocok. Jangan membuat duplikasi logic.


==================================================
18. VALIDASI SEBELUM PUSH
==================================================

Sebelum commit:

- jalankan test suite
- jalankan lint/type check jika project menggunakannya
- jalankan test khusus signal engine
- cek tidak ada regression
- cek git diff
- cek git status

Jika ada error, perbaiki terlebih dahulu.

Setelah semuanya PASS:

git add .
git commit -m "feat: add S/R continuation confirmation engine"
git push

Jika branch/repository memiliki aturan berbeda, ikuti konfigurasi repository yang sudah ada.

Jangan force push.

==================================================
HASIL AKHIR
==================================================

Setelah selesai laporkan:

1. File yang dibuat/diubah.
2. Logic continuation yang diimplementasikan.
3. Logic Support/Resistance yang diimplementasikan.
4. Logic rejection.
5. Logic breakout/breakdown.
6. Logic retest.
7. Anti-look-ahead protection.
8. Test yang dijalankan.
9. Hasil test.
10. Commit hash.
11. Push berhasil atau tidak.

Jangan hanya mengatakan "sudah dibuat".

Tunjukkan bukti dari test dan git status/commit.

Target tahap ini:

> Sistem mampu membedakan candle biasa dengan candle confirmation dan candle continuation, serta memahami apakah harga sedang ditolak Support/Resistance, melakukan breakout/breakdown, melakukan retest, atau benar-benar melanjutkan arah.

Jangan implementasikan auto-trading.
Jangan menambah indikator.
Jangan mengubah roadmap.
Langsung implementasikan, test, commit, dan push.
```
# 
```
Lanjutkan project XAUUSD berdasarkan roadmap yang sudah ada.

KONDISI SAAT INI:
- Data XAUUSD asli sudah berhasil diambil dari MetaTrader 5/broker.
- Symbol yang digunakan: XAUUSD.m
- File M5 sudah tersedia: data/XAUUSD_m_M5.csv
- File M15 sudah tersedia: data/XAUUSD_m_M15.csv
- Export M5 berhasil: 100835 bars
- Export M15 berhasil: 47265 bars
- Validasi M15 menunjukkan ERROR=0
- Validasi agregasi M5 → M15 menunjukkan ERROR=0
- Coverage overlap M5 → M15 = 100%
- Data memiliki gap/weekend gap yang harus tetap diperlakukan sebagai gap asli, bukan diisi candle sintetis.
- Jangan membuat synthetic market data.
- Jangan mengubah data asli hanya untuk memperbagus hasil.
- Jangan melakukan auto-trading.

==================================================
TAHAP SEKARANG: BASELINE BACKTEST
==================================================

Tujuan tahap ini adalah mengetahui performa dasar strategi roadmap menggunakan DATA XAUUSD ASLI sebelum menambahkan indikator/confluence apa pun.

Jangan menambahkan:
- ADX
- DMI
- ATR
- EMA
- VWAP
- RSI
- MACD
- machine learning
- indikator tambahan lainnya

Jangan melakukan optimasi parameter untuk mengejar win rate.

Gunakan strategi baseline yang sudah ditentukan roadmap:

M15:
    Market Structure
    +
    Support/Resistance

M5:
    Rejection
    +
    Breakout/Breakdown
    +
    Retest
    +
    Candle Confirmation

==================================================
1. AUDIT BACKTESTER TERLEBIH DAHULU
==================================================

Sebelum menjalankan backtest, audit kode backtester yang sudah ada.

Periksa:

- data loader
- timestamp handling
- timezone handling
- M5/M15 alignment
- market structure detection
- support/resistance detection
- breakout detection
- breakdown detection
- retest detection
- rejection detection
- candle confirmation
- entry calculation
- SL calculation
- TP calculation
- result calculation
- trade lifecycle
- equity curve
- drawdown calculation

Jangan menghapus implementasi yang sudah ada tanpa alasan.

Jika menemukan bug, perbaiki bug tersebut sebelum menjalankan baseline.

==================================================
2. WAJIB CEK LOOK-AHEAD BIAS
==================================================

Pastikan backtester tidak menggunakan informasi masa depan.

Aturan penting:

Candle yang belum CLOSE tidak boleh digunakan sebagai confirmation.

Untuk setiap entry:

    confirmation candle CLOSE
            ↓
    confirmation diketahui
            ↓
    entry pada candle/tick berikutnya

Jangan:

    future candle
        ↓
    mengetahui pattern
        ↓
    entry kembali ke masa lalu

Support/Resistance juga tidak boleh menggunakan swing future yang belum diketahui pada waktu entry.

Market structure hanya boleh menggunakan informasi yang sudah tersedia sampai timestamp tersebut.

Retest hanya boleh dianggap valid setelah retest benar-benar terjadi.

SL/TP tidak boleh menggunakan future price untuk menentukan apakah setup layak masuk.

Tambahkan test khusus untuk memastikan tidak ada look-ahead.

Jika terdapat look-ahead bias:
    STOP
    perbaiki terlebih dahulu
    jangan lanjutkan statistik

==================================================
3. PERIODE BACKTEST
==================================================

Karena M5 dan M15 mempunyai periode historis yang tidak identik, tentukan periode COMMON OVERLAP secara otomatis.

Jangan menggunakan periode sebelum data M5 tersedia.

Gunakan hanya periode yang benar-benar tersedia pada kedua timeframe.

Laporkan:

M5 earliest
M5 latest

M15 earliest
M15 latest

COMMON earliest
COMMON latest

Jangan menganggap data di luar common overlap tersedia.

==================================================
4. M15 MARKET STRUCTURE
==================================================

Gunakan roadmap yang sudah ada.

Identifikasi:

- HH
- HL
- LH
- LL
- BOS
- CHOCH

Klasifikasikan market:

    BULLISH
    BEARISH
    SIDEWAYS

Jangan menggunakan indikator tambahan.

Pastikan structure detection tidak melihat candle future.

==================================================
5. SUPPORT / RESISTANCE
==================================================

Gunakan Support/Resistance yang sudah ada dalam roadmap.

Level harus diperlakukan sebagai ZONE, bukan harga tunggal.

Gunakan informasi yang memang sudah tersedia pada saat setup terjadi.

Pertimbangkan:

- swing high
- swing low
- repeated rejection
- consolidation
- previous support/resistance
- flip level

Jangan membuat S/R menggunakan future data.

==================================================
6. SETUP A
==================================================

RESISTANCE REJECTION → SELL

Urutan:

Harga naik
↓
Harga masuk Resistance Zone
↓
Terjadi rejection
↓
Candle M5 CLOSE
↓
Bearish confirmation
↓
Entry SELL

Jangan entry sebelum confirmation candle CLOSE.

Catat setiap setup meskipun akhirnya tidak valid.

==================================================
7. SETUP B
==================================================

RESISTANCE BREAKOUT + RETEST → BUY

Urutan:

Harga mencapai resistance
↓
Breakout
↓
Candle M5 CLOSE di atas resistance
↓
Breakout valid
↓
Harga melakukan retest
↓
Retest bertahan
↓
Bullish confirmation candle CLOSE
↓
BUY

Jangan menganggap:

High > resistance

sebagai breakout valid.

Breakout harus dikonfirmasi menggunakan CLOSE.

==================================================
8. SETUP C
==================================================

SUPPORT REJECTION → BUY

Urutan:

Harga turun
↓
Masuk Support Zone
↓
Rejection
↓
Candle M5 CLOSE
↓
Bullish confirmation
↓
BUY

==================================================
9. SETUP D
==================================================

SUPPORT BREAKDOWN + RETEST → SELL

Urutan:

Harga mencapai support
↓
Breakdown
↓
Candle M5 CLOSE di bawah support
↓
Breakdown valid
↓
Retest
↓
Retest gagal reclaim support
↓
Bearish confirmation candle CLOSE
↓
SELL

==================================================
10. CANDLE CONFIRMATION
==================================================

Untuk baseline, gunakan candle confirmation yang SUDAH ADA di roadmap.

Uji secara terpisah:

1. Bullish/Bearish Engulfing
2. Rejection / Pin Bar
3. Strong Body
4. Breakout / Breakdown Candle
5. Retest Confirmation

Jangan langsung menggabungkan semuanya menjadi satu pattern.

Tujuannya mengetahui kontribusi masing-masing confirmation.

==================================================
11. RISK MANAGEMENT BACKTEST
==================================================

Gunakan mekanisme SL/TP yang sudah ada di project.

Jangan mengubah SL/TP hanya untuk meningkatkan statistik.

Jika mekanisme SL/TP belum jelas, audit dan dokumentasikan terlebih dahulu.

Pastikan:

- entry price jelas
- stop loss jelas
- take profit jelas
- R:R jelas
- spread/slippage handling jelas jika memang tersedia
- urutan candle setelah entry digunakan secara realistis

Jangan menggunakan harga future untuk memilih SL/TP setelah mengetahui hasil trade.

==================================================
12. TEST SETUP SECARA TERPISAH
==================================================

Jangan langsung membuat satu statistik gabungan.

Buat hasil terpisah untuk:

A:
Resistance Rejection SELL

B:
Resistance Breakout + Retest BUY

C:
Support Rejection BUY

D:
Support Breakdown + Retest SELL

Kemudian candle confirmation juga dipisahkan.

==================================================
13. STATISTIK BASELINE
==================================================

Untuk setiap setup tampilkan:

- Total setup
- Valid setup
- Invalid setup
- Total trades
- Wins
- Losses
- Win rate
- Loss rate
- Average R:R
- Expectancy
- Profit factor
- Net result
- Maximum drawdown
- Maximum consecutive wins
- Maximum consecutive losses

Jangan hanya menampilkan win rate.

==================================================
14. MARKET REGIME
==================================================

Pisahkan hasil berdasarkan M15:

BULLISH
BEARISH
SIDEWAYS

Untuk masing-masing kondisi tampilkan:

- sample
- trades
- win rate
- expectancy
- profit factor
- drawdown

Tujuannya mengetahui apakah setup tertentu hanya bekerja pada kondisi market tertentu.

==================================================
15. SETUP TYPE
==================================================

Pisahkan hasil berdasarkan:

- rejection
- breakout
- breakdown
- retest
- continuation

Jangan menggabungkan semuanya menjadi satu angka.

==================================================
16. IN-SAMPLE / OUT-OF-SAMPLE
==================================================

Jangan melakukan optimasi terhadap seluruh dataset.

Bagi data berdasarkan waktu.

Gunakan pembagian temporal yang jelas, misalnya:

IN-SAMPLE
    periode awal

VALIDATION
    periode berikutnya

OUT-OF-SAMPLE
    periode paling akhir

Gunakan tanggal aktual dataset yang tersedia.

Jangan random shuffle data time-series.

Jangan menggunakan OOS untuk tuning parameter.

Jika walk-forward framework sudah tersedia, gunakan.

Jika belum tersedia, cukup gunakan temporal split dan dokumentasikan.

==================================================
17. BASELINE TANPA OPTIMASI
==================================================

Ini sangat penting.

Jangan melakukan:

"ubah threshold → backtest → pilih hasil terbaik"

pada tahap ini.

Gunakan parameter baseline yang sudah ada.

Tujuan tahap ini bukan mendapatkan hasil terbaik.

Tujuannya adalah mendapatkan:

    BASELINE PERFORMANCE

yang jujur.

==================================================
18. NO SIGNAL
==================================================

Sistem wajib mendukung:

NO SIGNAL

Jika:

- structure tidak jelas
- S/R tidak jelas
- breakout tidak confirmed
- rejection tidak confirmed
- retest tidak valid
- candle confirmation tidak valid
- candle belum CLOSE
- R:R tidak memenuhi aturan
- terdapat konflik structure
- data tidak cukup

maka:

NO SIGNAL

Jangan memaksa BUY/SELL.

==================================================
19. AUDIT DATA
==================================================

Sebelum backtest, tampilkan:

DATASET
------------------------------
Symbol:
M5 bars:
M15 bars:
M5 earliest:
M5 latest:
M15 earliest:
M15 latest:
Common period:
Timezone:
Duplicate:
Invalid OHLC:
Ordering errors:
M5 integrity:
M15 integrity:
------------------------------

Jika ada masalah fatal:
    STOP

Jangan menghasilkan statistik strategi dari data yang rusak.

==================================================
20. OUTPUT FILE
==================================================

Jika memungkinkan, simpan hasil ke:

reports/
    baseline_summary.json
    baseline_trades.csv
    baseline_statistics.csv
    baseline_equity.csv

Dan dokumentasikan hasil di:

docs/BACKTEST_BASELINE.md

Jangan menimpa data mentah:

data/XAUUSD_m_M5.csv
data/XAUUSD_m_M15.csv

==================================================
21. HASIL YANG HARUS DILAPORKAN
==================================================

Setelah selesai, tampilkan ringkasan seperti:

BASELINE BACKTEST
==============================

Dataset:
Symbol:
Common period:

M5:
xxxxx bars

M15:
xxxxx bars

--------------------------------
SETUP A
Resistance Rejection
--------------------------------
Trades:
Win rate:
Avg R:R:
Expectancy:
Profit Factor:
Max Drawdown:

--------------------------------
SETUP B
Resistance Breakout + Retest
--------------------------------
Trades:
Win rate:
Avg R:R:
Expectancy:
Profit Factor:
Max Drawdown:

--------------------------------
SETUP C
Support Rejection
--------------------------------
Trades:
Win rate:
Avg R:R:
Expectancy:
Profit Factor:
Max Drawdown:

--------------------------------
SETUP D
Support Breakdown + Retest
--------------------------------
Trades:
Win rate:
Avg R:R:
Expectancy:
Profit Factor:
Max Drawdown:

--------------------------------
MARKET REGIME
--------------------------------
Bullish:
Bearish:
Sideways:

--------------------------------
CANDLE CONFIRMATION
--------------------------------
Engulfing:
Rejection:
Strong Body:
Breakout/Breakdown:
Retest:

--------------------------------
VALIDATION
--------------------------------
Look-ahead bias:
Repainting:
Data integrity:
OOS result:
Walk-forward:
================================

==================================================
22. INTERPRETASI
==================================================

Jangan mengatakan:

"strategi ini akurat"

hanya karena win rate terlihat tinggi.

Jangan mengatakan:

"pattern terbaik"

jika sample kecil.

Jangan memilih setup hanya berdasarkan win rate.

Jika sample terlalu kecil, tandai:

    INSUFFICIENT SAMPLE

Jika hasil in-sample bagus tetapi OOS buruk:

    OVERFITTING RISK

Jika setup konsisten tetapi jumlah sample masih kecil:

    WATCHLIST

Jika setup tidak menunjukkan edge:

    DISABLED

==================================================
23. JANGAN LANJUT KE INDIKATOR
==================================================

Setelah baseline selesai:

STOP.

Jangan langsung menambahkan:

ADX
DMI
ATR
EMA
VWAP
atau indikator lainnya.

Kita akan memakai hasil baseline sebagai pembanding pada eksperimen berikutnya.

Urutan project tetap:

REAL DATA
↓
DATA VALIDATION
↓
LOOK-AHEAD AUDIT
↓
BASELINE BACKTEST
↓
BASELINE STATISTICS
↓
OUT-OF-SAMPLE
↓
BARU RESEARCH CONFLUENCE

==================================================
TARGET TAHAP INI
==================================================

Target hanya satu:

> Mendapatkan baseline performance yang jujur dari strategi XAUUSD M15 + M5 menggunakan data MT5/broker asli, tanpa synthetic data, tanpa look-ahead bias, tanpa optimasi berlebihan, dan tanpa menambahkan indikator baru.

Jika semua sudah selesai, jangan membuat fitur baru.

Laporkan hasil baseline dan masalah yang ditemukan.

```
# 
```
# Prompt — Obtain Real XAUUSD M5/M15 Dataset

Lanjutkan project berdasarkan roadmap dan hasil validasi sebelumnya.

Saat ini blocker utama adalah **belum tersedianya data XAUUSD asli M5 dan M15**.

Jangan membuat synthetic data dan jangan mengklaim hasil strategi tanpa data market asli.

## Tugas

1. Audit `xausr.mt5_export` dan dokumentasi `docs/DATA.md`.
2. Pastikan exporter benar-benar mengambil OHLC candle dari **MetaTrader 5/broker**, bukan data sintetis.
3. Tentukan cara paling aman dan sederhana untuk mendapatkan:

   * XAUUSD M5
   * XAUUSD M15
   * minimal 2 tahun
   * ideal 3 tahun jika histori broker tersedia.
4. Jangan mengasumsikan nama symbol selalu `XAUUSD`.

Jika broker menggunakan nama seperti:

```text
XAUUSD
XAUUSDm
XAUUSD.
GOLD
```

jelaskan cara mendeteksi symbol yang tersedia dan gunakan symbol yang benar-benar tersedia di MT5.

## Export

Siapkan prosedur export yang menghasilkan:

```text
data/XAUUSD_M5.csv
data/XAUUSD_M15.csv
```

Format minimal:

```text
timestamp,open,high,low,close,volume
```

Pertahankan timezone secara eksplisit dan dokumentasikan timezone data.

## Data Integrity

Setelah export, otomatis lakukan pemeriksaan:

* jumlah candle
* earliest timestamp
* latest timestamp
* duplicate
* missing candle
* invalid OHLC
* timestamp ordering
* timezone
* gap data
* M5 consistency
* M15 consistency

Jangan menyatakan data valid jika pemeriksaan belum selesai.

## Broker Differences

Dokumentasikan bahwa:

* spread dapat berbeda antar broker,
* timezone server dapat berbeda,
* jam trading dapat berbeda,
* historical availability dapat berbeda,
* tick volume dan real volume dapat berbeda.

Jangan menyamakan data broker yang berbeda sebagai data identik.

## Backtest Readiness

Setelah dataset tersedia dan valid:

JANGAN langsung mengoptimasi strategi.

Cukup pastikan:

```text
REAL DATA
   ↓
DATA INTEGRITY PASS
   ↓
BACKTEST READY
```

Kemudian berhenti dan laporkan hasil pemeriksaan.

## Strict Rules

* Jangan membuat data market palsu.
* Jangan mengisi missing candle dengan harga buatan.
* Jangan menghapus data hanya agar statistik terlihat bagus.
* Jangan mengubah strategi untuk menyesuaikan dataset.
* Jangan menjalankan auto-trading.
* Jangan mengklaim akurasi.
* Jangan mengklaim indikator terbaik.
* Jangan menggunakan hasil synthetic sebagai bukti.

Jika MT5/broker tidak dapat diakses dari environment saat ini, jangan mencari jalan pintas dengan data sintetis.

Jelaskan dengan tepat:

1. Apa yang sudah tersedia.
2. Apa yang belum tersedia.
3. Dari mana data harus diexport.
4. Perintah yang harus dijalankan.
5. File CSV yang harus ditempatkan di project.
6. Command untuk memvalidasi data.

Target tahap ini hanya:

> **Mendapatkan dataset XAUUSD M5 + M15 asli yang bersih dan dapat dipercaya sehingga penelitian signal berikutnya bisa dilakukan secara valid.**

```
# 
```
# Prompt — Research Confluence & Signal Confirmation

Lanjutkan project berdasarkan roadmap yang sudah ada.

**Jangan melakukan auto-trading. Jangan mengklaim indikator tertentu paling akurat tanpa pengujian. Jangan menggunakan synthetic data sebagai bukti performa.**

Fokus tahap ini adalah merancang **framework penelitian confluence** untuk XAUUSD M15 + M5.

## Tujuan

Kita ingin mengetahui apakah kombinasi beberapa jenis confirmation dapat meningkatkan kualitas signal dibandingkan Support/Resistance + Price Action saja.

Prinsip:

> Setiap indikator harus membuktikan bahwa ia menambah informasi yang berguna. Jika tidak menambah edge, jangan digunakan.

## Kandidat Confirmation

Kelompokkan berdasarkan fungsi, jangan sekadar menumpuk indikator.

### 1. Market Structure

* HH
* HL
* LH
* LL
* BOS
* CHOCH

### 2. Support/Resistance

* Swing levels
* Repeated rejection
* Consolidation zones
* Previous S/R flip
* Strength of zone

### 3. Trend / Regime

Teliti secara objektif:

* ADX
* DMI (+DI/-DI)
* EMA trend filter

Gunakan indikator ini sebagai **filter kondisi market**, bukan tombol BUY/SELL.

### 4. Volatility

Teliti:

* ATR
* ATR relative to recent ATR
* Candle range relative to ATR

Tujuannya mengetahui apakah breakout/confirmation cukup signifikan dan apakah market terlalu tenang atau terlalu volatile.

### 5. Price Action

Teliti secara terpisah:

* Bullish/Bearish Engulfing
* Pin Bar/Rejection
* Strong Body
* Breakout Candle
* Breakdown Candle
* Retest Confirmation

Semua confirmation utama harus menggunakan candle yang sudah CLOSE.

### 6. Price Location

Teliti apakah setup lebih berkualitas ketika harga berada:

* dekat Support
* dekat Resistance
* setelah breakout
* setelah retest
* relatif terhadap VWAP jika data memungkinkan

VWAP hanya kandidat penelitian, bukan asumsi bahwa VWAP pasti meningkatkan akurasi.

## Eksperimen

Jika data XAUUSD asli sudah tersedia, bandingkan secara bertahap:

### Baseline

M15 Structure
+
S/R
+
M5 Price Action

### Experiment 1

Baseline + ADX/DMI

### Experiment 2

Baseline + ATR

### Experiment 3

Baseline + EMA trend filter

### Experiment 4

Baseline + VWAP

### Experiment 5

Baseline + ADX/DMI + ATR

### Experiment 6

Baseline + kombinasi confirmation terbaik yang terbukti dari eksperimen sebelumnya.

Jangan menggabungkan semua indikator secara otomatis.

## Evaluasi

Untuk setiap eksperimen ukur:

* Total sample
* Signal count
* Win rate
* Average R:R
* Expectancy
* Profit factor
* Maximum drawdown
* Consecutive losses
* Performance bullish market
* Performance bearish market
* Performance sideways market
* Performance breakout
* Performance rejection
* Performance retest
* Out-of-sample performance
* Walk-forward performance

Bandingkan dengan baseline.

## Strict Rule

Jika indikator:

* tidak meningkatkan hasil secara konsisten,
* hanya meningkatkan win rate pada sample kecil,
* meningkatkan hasil in-sample tetapi gagal out-of-sample,
* menyebabkan overfitting,
* atau tidak memberikan informasi tambahan yang jelas,

maka tandai:

```text
NOT USEFUL / DISABLED
```

Jangan memasukkannya ke signal engine.

## Signal Quality

Tujuan bukan mendapatkan signal sebanyak mungkin.

Signal hanya boleh dibuat jika:

```text
M15 Structure
+
Valid S/R
+
Valid Market Regime
+
M5 Reaction
+
Candle CLOSE Confirmation
+
Breakout/Rejection/Retest Valid
+
Risk/Reward Valid
+
Confluence Cukup
=
CONFIRMED SIGNAL
```

Jika terdapat konflik:

```text
NO SIGNAL
```

## Anti-Overfitting

Wajib:

* In-sample
* Validation
* Out-of-sample
* Walk-forward jika memungkinkan

Jangan memilih kombinasi indikator berdasarkan hasil terbaik pada satu periode saja.

Jangan melakukan tuning berulang terhadap OOS data.

## Output

Buat laporan yang menjawab:

1. Confirmation mana yang benar-benar menambah kualitas baseline.
2. Confirmation mana yang tidak memberikan manfaat.
3. Kondisi market mana yang paling cocok untuk setiap setup.
4. Apakah ADX/DMI membantu.
5. Apakah ATR membantu.
6. Apakah EMA membantu.
7. Apakah VWAP membantu.
8. Candle confirmation mana yang paling konsisten.
9. Kombinasi confirmation mana yang paling robust out-of-sample.
10. Kondisi apa yang menyebabkan sistem harus **NO SIGNAL**.

**Jangan menyebut suatu indikator atau kombinasi sebagai "paling akurat" sebelum memiliki sample yang memadai dan hasil out-of-sample/walk-forward yang konsisten.**

Jika data XAUUSD asli belum tersedia, jangan membuat hasil eksperimen. Siapkan framework pengujian saja dan laporkan bahwa pengujian real belum dapat dilakukan.

Belum perlu membuat auto-trading.

Target akhir tahap ini:

> Menemukan kombinasi confirmation yang benar-benar menambah kualitas signal XAUUSD M15 + M5 berdasarkan data nyata, bukan berdasarkan asumsi atau popularitas indikator.

```
# 
```
# Prompt — Real XAUUSD Data Pipeline & Validation

Lanjutkan project berdasarkan roadmap yang sudah ada.

**Jangan membuat strategi baru. Jangan menambah indikator baru. Jangan melakukan auto-trading.**

Fokus tahap ini hanya memastikan kita dapat menggunakan **data historis XAUUSD asli** untuk penelitian dan backtest yang valid.

## 1. Audit kondisi project

Periksa terlebih dahulu:

* Struktur project saat ini.
* Backtester Python.
* Modul data loader/import.
* Format CSV yang sudah didukung.
* Modul M5.
* Modul M15.
* Test yang sudah tersedia.
* Dokumentasi DATA.md/README.md.

Jangan menghapus atau merusak implementasi yang sudah ada.

## 2. Real Data Only

Synthetic data hanya boleh digunakan untuk unit test.

Untuk validasi strategi, gunakan:

* XAUUSD M5
* XAUUSD M15
* Data historis asli dari MT5/broker
* Idealnya minimal 2 tahun.
* Lebih baik 3 tahun jika tersedia.

Jangan membuat atau mengarang data market.

Jika data asli belum tersedia, **jangan menggantinya dengan synthetic data**.

Berhenti pada tahap preparation/import dan jelaskan dengan jelas data apa yang masih diperlukan.

## 3. Data Integrity

Validasi:

* timestamp
* timezone
* OHLC
* duplicate candle
* missing candle
* candle ordering
* invalid OHLC
* gap data
* consistency M5
* consistency M15

Pastikan candle M15 tidak menggunakan informasi M5 yang secara waktu belum tersedia.

## 4. No Look-Ahead Validation

Audit seluruh pipeline agar:

* S/R hanya menggunakan data yang sudah tersedia pada saat itu.
* Market structure tidak membaca candle masa depan.
* Confirmation hanya menggunakan candle yang sudah CLOSE.
* Breakout hanya dinyatakan valid setelah close.
* Retest hanya dinilai setelah kejadian retest.
* Entry timestamp selalu setelah confirmation.
* SL/TP tidak menggunakan informasi masa depan untuk menentukan entry.

Buat test khusus untuk mendeteksi look-ahead bias.

## 5. Backtest Dataset Split

Jika data real tersedia, siapkan:

* In-sample/training period
* Validation period
* Out-of-sample period

Jangan melakukan optimasi parameter menggunakan data out-of-sample.

Jika memungkinkan gunakan walk-forward validation.

## 6. Baseline Test

Sebelum menambah indikator atau optimasi apa pun, jalankan baseline menggunakan logika roadmap yang sudah ada:

* M15 market structure
* Support/Resistance zone
* M5 rejection
* M5 breakout/breakdown
* Retest
* Candle confirmation
* CONFIRM OR NO SIGNAL

Jangan mengubah threshold hanya untuk memperbagus statistik.

## 7. Statistik

Jika data real sudah tersedia, laporkan:

* jumlah candle
* periode data
* jumlah setup
* jumlah signal
* jumlah NO SIGNAL
* win rate
* loss rate
* average R:R
* expectancy
* profit factor
* maximum drawdown
* consecutive wins
* consecutive losses

Pisahkan hasil:

* M15 bullish
* M15 bearish
* M15 sideways
* resistance rejection
* resistance breakout
* support rejection
* support breakdown
* retest
* continuation

## 8. Strict Rule

Gunakan aturan:

CONFIRM OR NO SIGNAL

Jika data, structure, S/R, breakout/rejection, retest, candle confirmation, atau R:R tidak memenuhi syarat:

NO SIGNAL

Jangan memaksa menghasilkan BUY/SELL.

## 9. Output

Setelah selesai, laporkan:

1. Apakah data XAUUSD asli sudah tersedia.
2. Sumber/periode data.
3. Apakah data bersih.
4. Apakah ada look-ahead bias.
5. Apakah backtester siap menggunakan data real.
6. Hasil baseline jika data tersedia.
7. Masalah yang ditemukan.
8. Apa yang harus dilakukan berikutnya.

**Jangan mengklaim akurasi tinggi.**

Target tahap ini adalah memastikan fondasi data dan backtest benar sebelum kita melakukan penelitian indikator/confluence.

Jika data real belum tersedia, **jangan membuat hasil statistik palsu** dan jangan menggunakan synthetic data sebagai bukti performa.

```
# Prompt — Validasi Backtest XAUUSD Real Data
```
# Prompt — Validasi Backtest XAUUSD Real Data

Lanjutkan project berdasarkan roadmap yang sudah ada. Jangan membuat strategi baru di luar roadmap dan jangan langsung membuat auto-trading.

Fokus tahap ini adalah **memvalidasi apakah setup dan candle confirmation benar-benar memiliki edge pada data XAUUSD asli**.

### Tugas

1. Audit seluruh backtester Python yang sudah dibuat.
2. Pastikan tidak ada:

   * look-ahead bias
   * penggunaan candle masa depan
   * repaint logic
   * entry sebelum candle confirmation CLOSE
   * S/R yang menggunakan informasi masa depan
   * perhitungan SL/TP yang tidak realistis
3. Identifikasi dengan jelas bagaimana setiap setup A/B/C/D saat ini dihitung.
4. Jangan mengubah strategi hanya untuk mendapatkan win rate lebih tinggi.

### Data

Siapkan backtest untuk **data historis XAUUSD asli**, bukan synthetic data.

Prioritas:

* M15 untuk market structure dan S/R utama.
* M5 untuk breakout, retest, rejection, dan candle confirmation.

Jika data real belum tersedia di environment, jangan mengarang data. Buat dokumentasi format data yang dibutuhkan dan mekanisme import dari MT5/broker.

### Uji Setup Secara Terpisah

Uji dan laporkan secara terpisah:

1. Resistance Rejection → SELL
2. Resistance Breakout + Retest + Bullish Confirmation → BUY
3. Support Rejection + Bullish Confirmation → BUY
4. Support Breakdown + Retest + Bearish Confirmation → SELL

Kemudian uji candle confirmation secara terpisah:

* Engulfing
* Rejection/Pin Bar
* Strong Body
* Breakout/Breakdown Candle
* Retest Confirmation

Jangan langsung menggabungkan semua pattern. Kita harus mengetahui kontribusi masing-masing pattern.

### Statistik

Untuk setiap setup/pattern tampilkan minimal:

* Total sample
* Win rate
* Loss rate
* Average R:R
* Profit factor
* Expectancy
* Maximum drawdown
* Consecutive wins
* Consecutive losses
* Hasil berdasarkan kondisi M15:

  * bullish
  * bearish
  * sideways
* Hasil berdasarkan setup:

  * rejection
  * breakout
  * retest
  * continuation

### Validasi Anti-Overfitting

Gunakan pemisahan data yang benar:

* periode training/in-sample
* periode validation/out-of-sample

Jika memungkinkan, gunakan walk-forward validation.

Jangan memilih parameter hanya berdasarkan hasil terbaik pada satu periode.

### Strict Signal Rule

Implementasikan prinsip:

**CONFIRM OR NO SIGNAL**

Jika kondisi penting tidak terpenuhi:

text
NO SIGNAL


Jangan memaksa sistem menghasilkan BUY/SELL.

Jika sebuah candle pattern ternyata tidak memberikan edge yang cukup pada data asli, tandai sebagai:

text
DISABLED / WATCHLIST


bukan sebagai signal.

### Output

Setelah selesai:

1. Jelaskan struktur backtester saat ini.
2. Jelaskan apakah ada look-ahead/repainting/bias.
3. Jelaskan data apa yang sudah digunakan.
4. Berikan hasil statistik setiap setup dan pattern.
5. Pisahkan hasil in-sample dan out-of-sample.
6. Tentukan pattern/setup mana yang layak dilanjutkan ke tahap berikutnya.
7. Tentukan mana yang harus dinonaktifkan.
8. Jangan mengklaim "akurasi tinggi" hanya berdasarkan sample kecil.
9. Jangan mengubah roadmap tanpa alasan dan persetujuan.

**Jangan implementasikan Telegram signal baru atau auto-trading pada tahap ini.**

Target tahap ini hanya satu:

> Mengetahui berdasarkan data nyata apakah Support/Resistance + Breakout/Rejection + Retest + Candle Confirmation benar-benar cukup kuat untuk dijadikan dasar signal.

Jika data nyata belum tersedia, berhenti pada persiapan/import data dan laporkan apa yang dibutuhkan. Jangan menggunakan synthetic data sebagai bukti akurasi.

```
# 
```
# Prompt: BotSpace — Orphaned Running Job Recovery Contract + Reaper

Lanjutkan project BotSpace dari kondisi repository TERAKHIR.

KONDISI TERAKHIR

- B-030 Workspace API/Contract SUDAH selesai.
- B-070 Storage Adapter SUDAH selesai.
- B-071 File/Share contract SUDAH selesai.
- B-071 File/Share API SUDAH selesai.
- Production wiring B-071 SUDAH selesai.
- Redis OutboxPublisher/Consumer SUDAH selesai.
- Job State Machine SUDAH selesai.
- Worker Executor SUDAH selesai.
- Retry / exponential backoff / DLQ policy SUDAH selesai.
- Commit terakhir: 94e947a
- Push ke origin/backend-dev-recovery SUKSES.
- Local dan remote SHA sinkron.
- Working tree CLEAN.

REMAINING DEFERRED

1. Real Telegram integration — tetap deferred karena tidak ada API_ID/API_HASH/session nyata.
2. Concrete production JobHandler — deferred sampai ada workload nyata.
3. Orphaned running-job recovery / visibility timeout + reaper — TASK SEKARANG.
4. Automated dead-letter operator replay control — tetap deferred.
5. Optional correlationId pada JobEnvelope — tetap deferred.
6. Jangan membuat fitur speculative lainnya.

TUJUAN

Sekarang selesaikan dependency:

ORPHANED RUNNING-JOB RECOVERY

Masalah yang harus diselesaikan:

Jika worker mengambil job dan membuat state:

pending → running

lalu process mati sebelum job selesai, job tidak boleh selamanya tertinggal dalam state running.

Namun jangan langsung mengarang timeout/reaper behavior.

TAHAP 1 — AUDIT

Audit terlebih dahulu:

- jobs schema
- job repository
- JobEnvelope
- worker executor
- job state machine
- claim/atomic claim implementation
- outbox consumer
- retry/backoff/DLQ implementation TERAKHIR
- existing timestamps
- existing attempt fields
- existing `claimed_at` atau equivalent
- existing OPERATIONS_DESIGN
- ADR-007
- ADR-012
- migration history
- worker lifecycle/startup/shutdown

Cari apakah repository sudah memiliki contract untuk:

- visibility timeout,
- lease,
- claimed_at,
- heartbeat,
- stale running job,
- reaper,
- recovery transition.

Jangan mengarang contract jika belum ada.

TAHAP 2 — CONTRACT DECISION

Jika contract recovery belum ada:

Buat ADR/architecture decision yang mendefinisikan recovery semantics sebelum implementation.

Contract minimal harus menjawab:

1. Bagaimana job menjadi "orphaned"?
2. Field/timestamp apa yang menjadi dasar penentuan stale job?
3. Berapa visibility timeout?
4. Apakah timeout fixed atau configuration-driven?
5. Apakah worker membutuhkan heartbeat?
6. Bagaimana reaper menentukan job aman untuk direcover?
7. Bagaimana mencegah dua worker merecover job yang sama?
8. Bagaimana recovery berinteraksi dengan attempt counter?
9. Bagaimana recovery berinteraksi dengan retry/backoff/DLQ yang SUDAH ADA?
10. Apa yang terjadi jika attempt sudah exhausted?
11. Apa yang terjadi jika worker sebenarnya masih hidup tetapi lambat?
12. Apakah recovery langsung mengembalikan job ke pending atau menjalankan transition lain?
13. Apakah recovery harus atomic?
14. Bagaimana worker restart memengaruhi recovery?

Jangan memilih angka timeout secara arbitrary.

Gunakan evidence dari repository dan architecture yang sudah ada.

Jika belum ada evidence untuk angka timeout:
- jadikan configuration/operational decision,
- dokumentasikan dependency tersebut,
- jangan hardcode angka hanya agar implementation selesai.

TAHAP 3 — SCHEMA

Jika contract memang membutuhkan field baru seperti:

- claimed_at,
- lease/visibility deadline,
- worker ownership identifier,

tambahkan migration MINIMAL.

Sebelum migration:

- pastikan field benar-benar dibutuhkan,
- jangan membuat duplicate field,
- jangan mengubah schema jobs secara besar-besaran.

Jika existing schema sudah memiliki field yang cukup:
- gunakan field tersebut,
- jangan membuat migration baru.

TAHAP 4 — ATOMIC RECOVERY

Implementasikan recovery secara aman.

Requirements:

- hanya job `running` yang stale yang boleh direcover,
- recovery harus atomic,
- dua reaper/worker tidak boleh recover job yang sama,
- job yang masih aktif tidak boleh direcover,
- completed/failed/dead job tidak boleh direcover,
- attempt/retry policy harus tetap konsisten,
- jangan membuat infinite retry,
- jangan bypass DLQ policy.

Jika recovery membuat job kembali ke retry flow:
- gunakan retry/backoff policy yang SUDAH ADA,
- jangan membuat policy kedua.

TAHAP 5 — REAPER

Implementasikan reaper hanya jika repository sudah memiliki worker/runtime boundary yang tepat.

Jangan membuat daemon/process baru secara speculative.

Jika existing worker runtime merupakan tempat yang tepat:

- tambahkan recovery loop secara modular,
- jangan mencampur reaper dengan business handler,
- pastikan graceful shutdown,
- jangan membuat loop yang tidak dapat dihentikan.

Jika deployment/host process boundary belum ditentukan:

- implementasikan recovery primitive/repository operation,
- dokumentasikan runtime scheduler/reaper sebagai deployment dependency,
- jangan membuat process architecture baru.

TAHAP 6 — WORKER SAFETY

Pastikan normal worker execution tetap aman:

- claim tetap atomic,
- worker tidak mengambil job yang belum eligible,
- worker tidak kehilangan ownership secara diam-diam,
- recovery tidak membuat duplicate execution jika architecture belum menjamin exactly-once,
- failure tetap masuk retry/DLQ policy yang sudah ada.

Jangan mengklaim exactly-once execution jika repository hanya menyediakan at-least-once semantics.

TAHAP 7 — TEST

Tambahkan test nyata untuk:

- running job belum stale → tidak direcover,
- running job stale → dapat direcover,
- completed job → tidak direcover,
- failed job → tidak direcover,
- dead job → tidak direcover,
- concurrent reaper → hanya satu recovery berhasil,
- recovery mempertahankan attempt semantics,
- recovery menghormati retry/backoff/DLQ,
- worker restart,
- boundary timeout,
- timestamp handling,
- invalid/stale ownership jika contract mendukungnya.

Jangan membuat fake behavior hanya untuk PASS.

TAHAP 8 — TELEGRAM

Tetap DEFERRED.

Jangan:

- meminta API_ID,
- meminta API_HASH,
- meminta session,
- menjalankan real Telegram integration,
- membuat fake Telegram credentials.

TAHAP 9 — GOROUTER

Jangan menjalankan atau menambahkan test Gorouter.app.

NVIDIA dan TokenHarbor tidak perlu disentuh.

TAHAP 10 — VALIDATION

Jalankan:

pnpm test
pnpm build
pnpm typecheck
pnpm lint
pnpm format:check
node scripts/check-imports.mjs
node scripts/check-ownership.mjs
node scripts/check-doc-links.mjs
git diff --check

Jangan menjalankan atau membuat:

node scripts/check-symlinks.mjs

Jika tidak tersedia:

SKIPPED — scripts/check-symlinks.mjs unavailable

Jika PostgreSQL integration membutuhkan:

PERSISTENCE_TEST_DATABASE_URL

dan environment tidak tersedia:
- jangan membuat database palsu,
- laporkan skipped/unavailable.

TAHAP 11 — REVIEW

Sebelum commit:

git status
git diff --stat

Review seluruh diff.

Pastikan tidak ada:

- secret,
- credential,
- temporary files,
- generated junk,
- unrelated refactor,
- perubahan B-071,
- perubahan provider,
- Gorouter integration,
- Telegram runtime speculative,
- retry policy kedua.

TAHAP 12 — COMMIT + PUSH

Jika implementation valid dan validation selesai:

buat SATU commit dengan message yang sesuai, misalnya:

feat: add orphaned job recovery

Kemudian:

git push origin backend-dev-recovery

Verifikasi:

- local SHA,
- remote SHA,
- working tree clean.

Jika tidak ada perubahan valid:
- jangan membuat empty commit.

OUTPUT AKHIR

### Recovery Contract
- orphan detection:
- visibility timeout:
- ownership:
- recovery transition:
- concurrency safety:

### Schema
- migration:
- fields added/reused:

### Reaper
- primitive:
- runtime integration:
- graceful shutdown:

### Retry/DLQ Integration
- attempt handling:
- backoff:
- dead state:

### Tests
- test:
- build:
- typecheck:
- lint:
- format:
- imports:
- ownership:
- docs:
- diff:

### Git
- commit SHA:
- push:
- local/remote SHA:
- working tree:

### Remaining Deferred
Hanya dependency nyata.

### Next Roadmap
Tentukan SATU dependency berikutnya berdasarkan architecture repository.

Kerjakan langsung pada /root/botspace.
```
# 
```
# Roadmap — XAUUSD Support/Resistance Confirmation System

## Tujuan Utama

Membangun sistem analisis XAUUSD untuk MT5 yang dapat:

* Menganalisis trend pada M15.
* Menganalisis entry dan confirmation pada M5.
* Mendeteksi Support dan Resistance secara otomatis.
* Membedakan rejection dengan breakout/breakdown.
* Menunggu candle confirmation setelah harga mencapai level.
* Mendeteksi continuation trend.
* Memberikan skor kualitas setup.
* Menandai setup langsung pada chart MT5.
* Mengirim sinyal yang sudah terkonfirmasi ke Telegram.
* Melakukan backtest untuk mengetahui pola yang paling konsisten.
* Tidak mengklaim akurasi tertentu sebelum dibuktikan dengan data.

---

## PHASE 1 — Riset & Definisi Strategi

### 1.1 Pelajari Market Structure

Identifikasi:

* Higher High (HH)
* Higher Low (HL)
* Lower High (LH)
* Lower Low (LL)
* Break of Structure (BOS)
* Change of Character (CHOCH)

Tujuan:

Menentukan apakah market sedang bullish, bearish, atau sideways.

### 1.2 Pelajari Support & Resistance

Sistem harus mengenali:

* Swing High
* Swing Low
* Repeated rejection
* Area konsolidasi
* Previous Support → Resistance
* Previous Resistance → Support
* Strong Support
* Strong Resistance

Level harus diperlakukan sebagai **zona**, bukan angka tunggal.

### 1.3 Pelajari Candle Confirmation

Untuk bullish:

* Bullish Engulfing
* Bullish Rejection
* Hammer/Pin Bar
* Strong Bullish Body
* Breakout Candle
* Retest Confirmation

Untuk bearish:

* Bearish Engulfing
* Bearish Rejection
* Shooting Star/Pin Bar
* Strong Bearish Body
* Breakdown Candle
* Retest Confirmation

Semua confirmation utama harus menggunakan **candle yang sudah CLOSE**.

---

# PHASE 2 — Empat Setup Utama

Sistem hanya mencari empat kondisi utama.

## Setup A — Resistance Rejection

```text
Harga naik
↓
Masuk Resistance Zone
↓
Rejection
↓
Bearish Confirmation
↓
SELL
```

## Setup B — Resistance Breakout Continuation

```text
Harga naik
↓
Resistance
↓
Candle close di atas resistance
↓
Retest
↓
Bullish Confirmation
↓
BUY
```

## Setup C — Support Rejection

```text
Harga turun
↓
Masuk Support Zone
↓
Rejection
↓
Bullish Confirmation
↓
BUY
```

## Setup D — Support Breakdown Continuation

```text
Harga turun
↓
Support
↓
Candle close di bawah support
↓
Retest
↓
Bearish Confirmation
↓
SELL
```

---

# PHASE 3 — Multi-Timeframe Analysis

## M15 — Struktur Utama

M15 digunakan untuk:

* Menentukan trend.
* Menentukan Support/Resistance utama.
* Melihat market structure.
* Menentukan arah utama.
* Menentukan area penting.

## M5 — Confirmation & Entry

M5 digunakan untuk:

* Melihat reaksi harga pada level M15.
* Mendeteksi breakout/breakdown.
* Mendeteksi retest.
* Mendeteksi candle confirmation.
* Menentukan entry.

Prinsip:

```text
M15 = WHERE
M5  = WHEN
```

M15 menentukan **di mana** setup terjadi.

M5 menentukan **kapan** setup dianggap valid.

---

# PHASE 4 — Breakout & Retest Engine

Ini menjadi bagian inti sistem.

## Resistance Breakout

Tidak cukup hanya:

```text
High > Resistance
```

Sistem harus memeriksa:

1. Harga menembus resistance.
2. Candle M5 close di atas level/zona.
3. Breakout memiliki body yang cukup kuat.
4. Harga tidak langsung kembali ke bawah level.
5. Terjadi retest.
6. Retest berhasil bertahan.
7. Muncul bullish confirmation.

Baru:

```text
CONFIRMED BUY CONTINUATION
```

## Support Breakdown

Kebalikannya:

1. Harga menembus support.
2. Candle M5 close di bawah level/zona.
3. Breakdown cukup kuat.
4. Harga melakukan retest.
5. Retest gagal naik kembali.
6. Muncul bearish confirmation.

Baru:

```text
CONFIRMED SELL CONTINUATION
```

---

# PHASE 5 — Rejection Engine

Tidak semua sentuhan Support/Resistance adalah reversal.

Sistem harus memeriksa:

* Seberapa kuat level.
* Berapa kali level disentuh.
* Panjang wick.
* Ukuran body.
* Posisi close.
* Candle berikutnya.
* Market structure.
* Apakah rejection terjadi sesuai trend.

Contoh:

```text
Resistance
↓
Wick menembus sedikit
↓
Close kembali di bawah resistance
↓
Bearish confirmation
↓
SELL
```

---

# PHASE 6 — Confirmation Scoring

Setiap setup mendapatkan skor.

Contoh awal:

| Faktor                   |   Score |
| ------------------------ | ------: |
| M15 trend sesuai         |     +20 |
| Strong S/R               |     +20 |
| Market structure sesuai  |     +15 |
| Breakout/Breakdown valid |     +15 |
| Retest valid             |     +15 |
| Candle confirmation      |     +10 |
| Risk/Reward bagus        |      +5 |
| **Total**                | **100** |

Kategori:

* **80–100:** Strong Setup
* **70–79:** Valid Setup
* **60–69:** Watchlist
* **<60:** No Signal

Nilai ini masih **parameter awal** dan harus diuji melalui backtest.

---

# PHASE 7 — Anti-False-Signal Filter

Sistem harus belajar kapan **tidak boleh memberikan sinyal**.

Filter:

* Candle belum close.
* Breakout terlalu kecil.
* False breakout.
* Harga berada di tengah range.
* Support/Resistance tidak jelas.
* Tidak ada confirmation.
* Retest gagal.
* Risk/Reward terlalu buruk.
* Market terlalu sideways.
* Setup bertentangan dengan struktur M15.

Prinsip penting:

> **Tidak ada setup lebih baik daripada setup yang buruk.**

---

# PHASE 8 — Chart Visualization MT5

Jika setup ditemukan, MT5 menampilkan:

* Support zone.
* Resistance zone.
* Trend M15.
* BOS/CHOCH.
* Candle confirmation.
* Entry.
* Stop Loss.
* Take Profit.
* Retest.
* BUY/SELL marker.
* Score setup.
* Alasan sinyal.

Contoh:

```text
       RESISTANCE
━━━━━━━━━━━━━━━━━━━━
       ↓ Retest
       ↓
      🟥
      🟥  ← Bearish Confirmation
      🟥
       ↓
     SELL
```

---

# PHASE 9 — Telegram Notification

Telegram hanya menerima setup yang sudah memenuhi filter.

Contoh:

```text
🔴 XAUUSD SELL

TF Structure : M15
TF Entry     : M5

Trend        : Bearish
Level        : Resistance
Setup        : Rejection
Confirmation : Bearish Engulfing
Retest       : Valid
Score        : 87/100

Entry        : xxxx
SL           : xxxx
TP           : xxxx

Status       : CONFIRMED
```

Untuk continuation:

```text
🟢 XAUUSD BUY

M15 Trend    : Bullish
Resistance   : Broken
Breakout     : Confirmed
Retest       : Valid
Candle       : Bullish Confirmation

Score        : 91/100

Status       : BUY CONTINUATION
```

---

# PHASE 10 — Backtesting

Sebelum digunakan untuk trading nyata:

Uji data historis XAUUSD.

Prioritas:

* M15 + M5
* Berbagai kondisi market
* Trend bullish
* Trend bearish
* Sideways
* Breakout
* False breakout
* Rejection
* Retest

Catat:

* Jumlah setup.
* Win rate.
* Loss rate.
* Average R:R.
* Maximum drawdown.
* Setup terbaik.
* Candle confirmation terbaik.
* S/R terbaik.
* Jam trading terbaik.

Tujuan bukan mencari angka akurasi yang terlihat bagus, tetapi menemukan **kombinasi kondisi yang benar-benar konsisten**.

---

# PHASE 11 — Optimasi

Setelah backtest:

* Optimasi Support/Resistance detection.
* Optimasi candle confirmation.
* Optimasi breakout threshold.
* Optimasi retest.
* Optimasi scoring.
* Optimasi SL/TP.
* Optimasi filter market sideways.

Setiap perubahan harus diuji ulang agar tidak terjadi overfitting.

---

# PHASE 12 — Forward Test

Setelah backtest bagus:

* Jalankan sistem pada akun demo.
* Jangan langsung auto-trading.
* Telegram hanya mengirim sinyal.
* Semua sinyal dicatat.
* Bandingkan prediksi dengan hasil aktual.

Periksa apakah hasil real-time mendekati hasil backtest.

---

# PHASE 13 — MT5 Production Version

Setelah sistem lolos pengujian:

### MT5 Indicator

Untuk visualisasi dan analisis.

### MT5 EA

Untuk:

* Monitoring market.
* Menghitung setup.
* Mengirim Telegram.
* Optional auto-entry di masa depan.

### Telegram Bot

Untuk:

* Signal notification.
* Detail setup.
* Entry/SL/TP.
* Score.
* Status confirmation.

---

# PHASE 14 — Future Development

Setelah sistem utama stabil:

* Multi-symbol.
* XAUUSD sebagai prioritas pertama.
* NAS100.
* EURUSD.
* GBPUSD.
* Session filter.
* News filter.
* Advanced market structure.
* Liquidity analysis.
* Multiple confirmation levels.
* Signal history.
* Dashboard.
* Statistik performa.
* Machine-learning research jika memang diperlukan.

---

# Prinsip Utama Sistem

Sistem tidak boleh berpikir:

```text
Candle merah = SELL
Candle hijau = BUY
```

Sistem harus berpikir:

```text
M15 Structure
      ↓
Support / Resistance
      ↓
Harga mencapai zona
      ↓
Rejection atau Breakout?
      ↓
Break / Retest
      ↓
M5 Candle Confirmation
      ↓
Risk/Reward
      ↓
Scoring
      ↓
CONFIRMED SIGNAL
      ↓
MT5 Marker + Telegram
```

## Prioritas Pengembangan

**1. Market Structure**
**2. Support/Resistance**
**3. Breakout/Breakdown**
**4. Retest**
**5. Candle Confirmation**
**6. M15 → M5 Confirmation**
**7. Scoring**
**8. Backtest**
**9. Forward Test**
**10. Telegram + MT5 Production**

### Target awal

Kita **tidak mengejar "sinyal sebanyak mungkin"**.

Targetnya adalah:

> **Sedikit sinyal, tetapi setiap sinyal mempunyai alasan yang jelas dan dapat diuji secara statistik.**

```
