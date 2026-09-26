# 
```
https://github.com/zenolambee/mt-signal.git
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
PHASE BERIKUTNYA — CLEANUP REPO HASIL + VALIDASI SIGNAL XAUUSD DENGAN CANDLE AKTUAL

Lanjutkan dari kondisi repository saat ini.

PENTING:
- Jangan membuat strategy baru.
- Jangan menambah indikator baru.
- Jangan mengubah logic utama EMA20/50 + RSI14 + ATR14 + Market Structure + Fibonacci yang sudah dibuat.
- Jangan menghapus hasil coding yang sudah dibuat sebelum memastikan source code aman di repository utama.
- Repository `hasil-prompt-mt-signal` adalah REPO HASIL/DOKUMENTASI PROMPT, bukan repository source code utama.
- Source code utama tetap berada di repository utama `zenolambee/mt-signal`.
- Semua perubahan harus diverifikasi sebelum commit/push.

==================================================
BAGIAN 1 — CLEANUP REPOSITORY HASIL
==================================================

Repository hasil:

https://github.com/zenolambee/hasil-prompt-mt-signal.git

Tujuan repository ini:
MENYIMPAN HASIL DARI PROMPT/PHASE, BUKAN MENJADI SOURCE CODE UTAMA.

1. Inspect terlebih dahulu:
- branch
- commit history
- seluruh file
- isi README.md
- source code yang saat ini terlanjur berada di repository hasil.

2. Pastikan source code strategy tetap aman di repository utama:

https://github.com/zenolambee/mt-signal

Jika source code yang sekarang hanya ada di repository hasil dan belum ada di repository utama:
- jangan hapus dulu.
- pastikan source code sudah tersedia/tersimpan di repository utama.
- setelah aman, baru rapikan repository hasil.

3. Repository `hasil-prompt-mt-signal` setelah cleanup harus berisi DOKUMENTASI HASIL, bukan source code utama.

Gunakan struktur sederhana:

hasil-prompt-mt-signal/
├── README.md
└── phase/
    └── phase-01-xauusd-ema-rsi-atr-fibonacci.md

Jika sudah ada format folder/hasil yang lebih baik di repository, pertahankan dan sesuaikan tanpa membuat struktur berlebihan.

4. File hasil phase harus menjelaskan:

- Nama strategy:
  XAUUSD_EMA_RSI_ATR_STRUCTURE_FIB

- Indikator:
  EMA20
  EMA50
  RSI14
  ATR14
  Fibonacci
  Market Structure

- Timeframe:
  M15 confirmation
  M5 entry

- Logic BUY secara ringkas.
- Logic SELL secara ringkas.
- Logic NO SIGNAL.
- Fibonacci 0.382 / 0.500 / 0.618 / 0.786.
- Fibonacci extension 1.272 / 1.618.
- ATR SL.
- RR TP.
- Confidence.
- Test yang sudah dilakukan.
- Jumlah test PASS/FAIL.
- Status validasi candle aktual.

5. Jangan masukkan:
- API key
- password
- token
- `.env`
- credential
- secret
- data sensitif.

6. Setelah cleanup:
- git status
- git diff
- pastikan source code strategy tidak hilang.
- commit dengan message yang jelas.
- push ke repository hasil.

JANGAN menghapus source code dari repository hasil sebelum memastikan source code aman di repository utama.

==================================================
BAGIAN 2 — VALIDASI DENGAN CANDLE XAUUSD AKTUAL
==================================================

Setelah cleanup repository selesai, lanjutkan validasi strategy.

Tujuan:
Memastikan strategy bukan hanya lulus unit test, tetapi benar-benar dapat memproses candle XAUUSD dan menghasilkan:

BUY
SELL
atau
NO SIGNAL

berdasarkan data candle.

==================================================
A. INSPECT SOURCE CODE
==================================================

Inspect strategy yang sekarang.

Pastikan fungsi/komponen yang digunakan untuk signal dapat menerima data candle secara nyata/deterministik.

Jangan membuat mock BUY/SELL hanya supaya test PASS.

Jika architecture belum memiliki candle input yang jelas, buat adapter/input layer minimal tanpa mengubah logic strategy.

==================================================
B. DATA CANDLE
==================================================

Gunakan data candle XAUUSD aktual jika repository/project sudah memiliki data provider atau feed.

Jika belum ada live feed:
- gunakan historical candle XAUUSD yang nyata untuk validation.
- jangan menggunakan candle random.
- jangan mengarang OHLC.

Data minimal:

timestamp
open
high
low
close

Jika diperlukan:

volume
spread

Gunakan:
M15 untuk confirmation.
M5 untuk entry.

==================================================
C. PIPELINE VALIDASI
==================================================

Test pipeline:

XAUUSD candle
↓
M15 EMA20/EMA50
↓
M15 trend
↓
M5 EMA20/EMA50
↓
Market Structure
↓
Fibonacci swing
↓
Fibonacci retracement
↓
RSI14
↓
Candle confirmation
↓
Structure break
↓
ATR14
↓
SL
↓
TP
↓
BUY / SELL / NO SIGNAL

Pastikan setiap tahap menggunakan candle yang tersedia pada saat itu.

Jangan menggunakan candle masa depan untuk menentukan signal.

==================================================
D. AVOID LOOK-AHEAD BIAS
==================================================

Ini WAJIB.

Signal pada candle N hanya boleh menggunakan data candle sampai candle N.

Tidak boleh:
- menggunakan future candle.
- menggunakan future swing.
- menggunakan future Fibonacci anchor.
- menggunakan candle setelah entry untuk menentukan signal entry.

Jika swing membutuhkan confirmation candle, gunakan hanya setelah swing tersebut benar-benar confirmed.

Dokumentasikan aturan ini.

==================================================
E. END-TO-END VALIDATION
==================================================

Buat minimal:

1. Satu scenario BUY yang berasal dari candle nyata.
2. Satu scenario SELL yang berasal dari candle nyata.
3. Satu scenario NO SIGNAL.

Untuk setiap scenario tampilkan:

timestamp
symbol
timeframe
M15 trend
M5 trend
EMA20
EMA50
RSI
ATR
swing high
swing low
Fib 0.382
Fib 0.500
Fib 0.618
Fib 0.786
current price
market structure
candle confirmation
structure break
entry
SL
TP
RR
confidence
final signal
reason

==================================================
F. SIGNAL TIDAK BOLEH DIPAKSA
==================================================

Jika data candle tidak menghasilkan BUY/SELL:

→ tampilkan NO SIGNAL.

Jangan mengubah parameter hanya untuk memaksa muncul BUY/SELL.

Jika historical dataset tidak menemukan setup yang valid, laporkan:

"Dataset tidak menghasilkan setup valid."

Jangan membuat hasil palsu.

==================================================
G. VALIDASI OUTPUT
==================================================

Pastikan output seperti:

XAUUSD
Strategy: XAUUSD_EMA_RSI_ATR_STRUCTURE_FIB

M15 Trend: Bullish
M5 Structure: Higher High / Higher Low

Fibonacci:
0.382 = ...
0.500 = ...
0.618 = ...
0.786 = ...

RSI: ...
ATR: ...

Signal: BUY

Entry: ...
SL: ...
TP: ...
RR: 1:2

Confidence: .../100

Reason:
M15 bullish + M5 pullback + Fib 0.500-0.618 + RSI confirmation + bullish structure break.

Untuk SELL gunakan informasi yang sesuai.

Jika NO SIGNAL:

Signal: NO SIGNAL

Reason:
jelaskan kondisi yang gagal.

==================================================
H. TEST
==================================================

Jalankan seluruh test existing.

Kemudian tambahkan test untuk:

- candle input aktual/deterministik.
- BUY end-to-end.
- SELL end-to-end.
- NO SIGNAL.
- M15/M5 alignment.
- Fibonacci calculation.
- Fibonacci anchor.
- RSI.
- ATR.
- SL.
- TP.
- structure break.
- candle confirmation.
- duplicate signal.
- no look-ahead bias.

Jalankan:

python -m unittest -v

Jika project memiliki pytest, gunakan pytest juga.

Jalankan compile/typecheck/lint yang tersedia.

==================================================
I. JANGAN MERUSAK STRATEGI EXISTING
==================================================

Sebelum selesai lakukan:

git diff

Pastikan:
- strategy lama tidak rusak.
- logic Fibonacci tidak hilang.
- test lama tetap PASS.
- tidak ada credential.
- tidak ada file `.env`.
- tidak ada file temporary/cache.

==================================================
J. REPOSITORY HASIL
==================================================

Setelah validasi selesai, update repository:

https://github.com/zenolambee/hasil-prompt-mt-signal.git

Tambahkan hasil validation ke dokumentasi phase.

Contoh:

phase/
└── phase-02-candle-validation.md

Isi:
- tujuan
- data yang digunakan
- periode data
- jumlah candle
- BUY scenario
- SELL scenario
- NO SIGNAL scenario
- hasil test
- hasil validation
- limitation
- status

Repository hasil tetap hanya untuk dokumentasi hasil.

Jangan memasukkan source code utama ke repository hasil lagi.

==================================================
K. GIT COMMIT
==================================================

Repository utama:
https://github.com/zenolambee/mt-signal

Repository hasil:
https://github.com/zenolambee/hasil-prompt-mt-signal.git

Pastikan perubahan source code hanya masuk repository utama.

Pastikan dokumentasi hasil masuk repository hasil.

Commit message yang jelas.

Contoh source repository:

feat: validate xauusd fib strategy with candle data

Contoh repository hasil:

docs: add xauusd candle validation result

Push kedua repository sesuai fungsinya.

==================================================
L. FINAL REPORT
==================================================

Setelah selesai tampilkan singkat:

1. Repository utama:
   - source code aman atau tidak
   - commit
   - push status

2. Repository hasil:
   - cleanup berhasil atau tidak
   - struktur file
   - commit
   - push status

3. Validation:
   - dataset yang digunakan
   - jumlah candle
   - BUY scenario
   - SELL scenario
   - NO SIGNAL scenario

4. Test:
   - total PASS
   - total FAIL

5. Look-ahead bias:
   - PASS/FAIL

6. Masalah yang ditemukan.

7. Jangan mengatakan berhasil jika push atau test sebenarnya gagal.

PENTING:
Jangan lanjut membuat indikator atau strategi baru.
Fokus menyelesaikan CLEANUP REPO + VALIDASI CANDLE AKTUAL terlebih dahulu.

```
# 
```
LANJUTKAN IMPLEMENTASI STRATEGI SIGNAL XAUUSD YANG SUDAH ADA.

PENTING:
- Jangan membuat project baru.
- Jangan menghapus strategi/logic yang sudah dibuat.
- Inspect hasil coding saat ini terlebih dahulu.
- Pertahankan EMA20/50 + RSI14 + ATR14 + Market Structure.
- SEKARANG TAMBAHKAN FIBONACCI RETRACEMENT sebagai filter tambahan.
- Setelah implementasi selesai dan semua test berhasil, COMMIT DAN PUSH seluruh hasil ke repository:
https://github.com/zenolambee/hasil-prompt-mt-signal.git

==================================================
1. STRATEGI EXISTING
==================================================

Strategi:
XAUUSD_EMA_RSI_ATR_STRUCTURE

Timeframe:
- M15 = trend confirmation
- M5 = entry

Indikator existing:
- EMA 20
- EMA 50
- RSI 14
- ATR 14
- Market Structure

Jangan mengubah logic existing kecuali memang diperlukan agar Fibonacci dapat terintegrasi dengan benar.

==================================================
2. TAMBAHKAN FIBONACCI RETRACEMENT
==================================================

Tambahkan Fibonacci Retracement berdasarkan swing structure yang SUDAH CONFIRMED.

Level utama:

0.382
0.500
0.618
0.786

Level utama entry/pullback:
- 0.500
- 0.618

Level 0.382 dapat digunakan sebagai shallow pullback.

Level 0.786 digunakan sebagai deep retracement/invalidation filter.

JANGAN menghitung Fibonacci dari candle random.

Anchor Fibonacci harus berasal dari swing High dan swing Low yang sudah terdeteksi oleh Market Structure.

==================================================
3. FIBONACCI BUY
==================================================

Untuk BUY:

1. M15 bullish:
   EMA20 > EMA50

2. Market structure bullish:
   Higher High + Higher Low

3. Tentukan swing Low → swing High yang valid.

4. Tunggu harga melakukan retracement.

5. Area retracement yang diprioritaskan:
   Fibonacci 0.500–0.618

6. Harga berada/masuk area Fibonacci tersebut.

7. RSI M5 kembali > 50.

8. M5 menunjukkan bullish confirmation.

9. Harga melakukan break terhadap swing high/structure confirmation.

Jika kondisi utama terpenuhi:
→ BUY

Fibonacci TIDAK boleh menghasilkan BUY sendirian.

==================================================
4. FIBONACCI SELL
==================================================

Untuk SELL:

1. M15 bearish:
   EMA20 < EMA50

2. Market structure bearish:
   Lower High + Lower Low

3. Tentukan swing High → swing Low yang valid.

4. Tunggu harga melakukan retracement.

5. Area retracement yang diprioritaskan:
   Fibonacci 0.500–0.618

6. Harga berada/masuk area Fibonacci tersebut.

7. RSI M5 kembali < 50.

8. M5 menunjukkan bearish confirmation.

9. Harga melakukan break terhadap swing low/structure confirmation.

Jika kondisi utama terpenuhi:
→ SELL

Fibonacci TIDAK boleh menghasilkan SELL sendirian.

==================================================
5. FIBONACCI 0.786
==================================================

Gunakan 0.786 sebagai filter.

Jika harga melakukan retracement terlalu dalam melewati 0.786:

BUY:
→ setup bullish dianggap invalid atau confidence dikurangi sesuai konfigurasi.

SELL:
→ setup bearish dianggap invalid atau confidence dikurangi sesuai konfigurasi.

Jangan langsung menghasilkan signal hanya karena harga menyentuh 0.786.

==================================================
6. FIBONACCI + EXISTING CONFIRMATION
==================================================

Signal harus menggunakan kombinasi:

M15 Trend
+
M5 Alignment
+
Market Structure
+
Fibonacci Pullback
+
RSI Confirmation
+
Candle Confirmation
+
Break Structure
+
ATR Risk Management

Contoh BUY:

M15 bullish
↓
Higher High + Higher Low
↓
Fibonacci ditarik dari swing valid
↓
harga retrace ke 0.500–0.618
↓
RSI > 50
↓
bullish candle confirmation
↓
break swing high
↓
BUY

Contoh SELL:

M15 bearish
↓
Lower High + Lower Low
↓
Fibonacci swing valid
↓
harga retrace ke 0.500–0.618
↓
RSI < 50
↓
bearish candle confirmation
↓
break swing low
↓
SELL

==================================================
7. CONFIDENCE SCORE
==================================================

Pertahankan confidence system existing, tetapi tambahkan Fibonacci.

Contoh:

M15 trend              +20
M5 alignment           +15
Pullback               +10
Fibonacci 0.500–0.618  +15
RSI confirmation       +10
Market structure       +15
Candle confirmation    +10
Break structure        +5

Total:
100

Jangan membuat score menjadi BUY/SELL jika mandatory condition gagal.

Jika Fibonacci tidak valid:
→ jangan memaksakan signal.

==================================================
8. ATR SL
==================================================

Tetap gunakan ATR14 M5.

Default:

atrSLMultiplier = 1.5

SL harus mempertimbangkan:
- swing structure
- ATR
- invalidation Fibonacci

BUY:
SL di bawah swing low/area invalidation.

SELL:
SL di atas swing high/area invalidation.

Jangan menggunakan fixed SL yang sama untuk semua kondisi.

==================================================
9. TAKE PROFIT + FIBONACCI EXTENSION
==================================================

Pertahankan RR configurable:

riskReward = 2.0

Selain TP berdasarkan RR, siapkan Fibonacci Extension sebagai informasi/target tambahan:

1.272
1.618

Gunakan extension sebagai candidate TP/reference.

Jangan memaksa TP ke extension jika hasilnya lebih buruk dari risk management.

Output dapat menampilkan:

TP RR
Fib Extension 1.272
Fib Extension 1.618

==================================================
10. NO SIGNAL
==================================================

NO SIGNAL jika:

- M15 ranging
- M5 tidak searah
- Market structure belum confirmed
- Fibonacci anchor tidak valid
- Harga tidak berada pada area retracement yang valid
- Retracement melewati 0.786
- RSI tidak memberikan confirmation
- Candle confirmation belum ada
- Break structure belum terjadi
- Spread terlalu tinggi
- Kondisi market tidak jelas

Lebih baik NO SIGNAL daripada memaksakan signal.

==================================================
11. SIGNAL OUTPUT
==================================================

Tambahkan informasi Fibonacci:

XAUUSD
Signal: BUY / SELL / NO SIGNAL

Strategy:
XAUUSD_EMA_RSI_ATR_STRUCTURE_FIB

Timeframe:
M5

Confirmation:
M15

Entry:
xxxx.xx

SL:
xxxx.xx

TP:
xxxx.xx

RR:
1:2

EMA20:
xxxx

EMA50:
xxxx

RSI:
xx.xx

ATR:
xx.xx

Trend:
Bullish / Bearish / Ranging

Market Structure:
Higher High / Higher Low
atau
Lower High / Lower Low

Fibonacci:
0.382 = xxxx
0.500 = xxxx
0.618 = xxxx
0.786 = xxxx

Active Fib Zone:
0.500–0.618

Fib Extension:
1.272 = xxxx
1.618 = xxxx

Confidence:
xx/100

==================================================
12. CONFIGURATION
==================================================

Semua parameter harus configurable:

emaFast = 20
emaSlow = 50

rsiPeriod = 14

atrPeriod = 14
atrSLMultiplier = 1.5

riskReward = 2.0

fibRetracementShallow = 0.382
fibRetracementEntry1 = 0.500
fibRetracementEntry2 = 0.618
fibRetracementInvalidation = 0.786

fibExtension1 = 1.272
fibExtension2 = 1.618

swingLookback = configurable
minimumStructureDistance = configurable

enableSpreadFilter = true
maxSpread = configurable

minimumConfidence = configurable

Jangan hard-code parameter di banyak tempat.

==================================================
13. TEST
==================================================

Tambahkan/update unit test untuk:

1. Fibonacci calculation.
2. Bullish Fibonacci setup.
3. Bearish Fibonacci setup.
4. Harga berada di 0.500.
5. Harga berada di 0.618.
6. Harga berada di 0.382.
7. Harga melewati 0.786.
8. Invalid Fibonacci swing.
9. BUY dengan semua confirmation.
10. SELL dengan semua confirmation.
11. M15 bullish tetapi M5 bearish.
12. M15 bearish tetapi M5 bullish.
13. RSI gagal confirmation.
14. Candle confirmation gagal.
15. Structure gagal.
16. Duplicate signal.
17. ATR SL.
18. RR TP.
19. Fibonacci extension.
20. NO SIGNAL.

Jika tersedia backtesting engine, gunakan candle/data aktual untuk validasi.

Jangan menggunakan random/mock signal untuk menyatakan strategy berhasil.

==================================================
14. AUDIT HASIL EXISTING
==================================================

Sebelum coding:
- baca file yang sudah dibuat.
- cek test_xauusd_strategy.py.
- cek xauusd_strategy.py.
- cek README.md.
- cek konfigurasi yang sudah ada.

Dari hasil pada implementasi sebelumnya, test sudah ada tetapi belum membuktikan end-to-end signal BUY/SELL dengan candle/feed aktual.

Sekarang perbaiki bagian tersebut jika memang masih belum lengkap.

Pastikan ada minimal test end-to-end yang menggunakan candle input nyata/deterministik dan menghasilkan:
- valid BUY scenario
- valid SELL scenario
- valid NO SIGNAL scenario

==================================================
15. GIT
==================================================

SETELAH CODING SELESAI:

1. Jalankan test.
2. Jalankan lint/typecheck jika tersedia.
3. Jalankan compile check jika tersedia.
4. Audit git diff.
5. Pastikan tidak ada file rahasia seperti .env, API key, password, token, credential, atau secret yang ikut commit.
6. Jangan commit credential.
7. Pastikan README diperbarui dengan cara menjalankan strategy baru.
8. Commit perubahan dengan message yang jelas, contoh:

feat: add fibonacci xauusd signal strategy

9. Push ke:

https://github.com/zenolambee/hasil-prompt-mt-signal.git

10. Setelah push, verifikasi bahwa commit benar-benar berhasil masuk ke remote repository.

==================================================
16. FINAL REPORT
==================================================

Setelah selesai, tampilkan singkat:

- File yang dibuat/diubah.
- Fibonacci berhasil diimplementasikan atau tidak.
- Logic BUY.
- Logic SELL.
- Logic NO SIGNAL.
- Test yang dijalankan.
- Jumlah test PASS/FAIL.
- Commit hash.
- Status push ke repository.
- Jika ada masalah yang belum selesai, jelaskan apa adanya.

JANGAN mengatakan berhasil push jika push sebenarnya gagal.

PENTING:
Fokus hanya menyelesaikan strategi ini.
Jangan membuat strategi baru lagi.
Jangan mengubah strategi lama yang tidak berkaitan.
Jangan melakukan refactor besar tanpa kebutuhan.
Gunakan data candle aktual/deterministik untuk validasi.

```
# 
```
Buat STRATEGI SIGNAL XAUUSD BARU sebagai modul terpisah. Jangan mengubah, menghapus, atau merusak strategi signal lama. Strategi ini menggunakan EMA 20/50 + RSI 14 + ATR 14 + Market Structure. Timeframe M15 untuk konfirmasi trend dan M5 untuk entry.

ATURAN UTAMA:

1. M15 TREND

* Bullish: EMA20 > EMA50.
* Bearish: EMA20 < EMA50.
* Jika EMA20 dan EMA50 terlalu dekat/datar atau sering crossover → NO SIGNAL.
* Buat threshold ranging sebagai konfigurasi.

2. MARKET STRUCTURE

* Bullish: Higher High + Higher Low.
* Bearish: Lower High + Lower Low.
* Gunakan swing candle yang sudah terbentuk.
* Buat parameter swingLookback dan minimumStructureDistance.
* Jangan menggunakan prediksi.

3. BUY M5
   Semua kondisi utama harus terpenuhi:

* M15 EMA20 > EMA50.
* M5 searah bullish atau baru kembali bullish setelah pullback.
* Harga melakukan pullback ke area EMA20/EMA50.
* RSI14 M5 kembali > 50.
* Terbentuk Higher Low.
* Harga break swing high terdekat.
* Ada candle bullish confirmation, seperti bullish engulfing, bullish rejection, atau strong bullish close.
* Jika semua terpenuhi → BUY.

4. SELL M5
   Semua kondisi utama harus terpenuhi:

* M15 EMA20 < EMA50.
* M5 searah bearish atau baru kembali bearish setelah pullback.
* Harga melakukan pullback ke area EMA20/EMA50.
* RSI14 M5 kembali < 50.
* Terbentuk Lower High.
* Harga break swing low terdekat.
* Ada candle bearish confirmation, seperti bearish engulfing, bearish rejection, atau strong bearish close.
* Jika semua terpenuhi → SELL.

5. NO SIGNAL
   Jangan menghasilkan signal jika:

* Trend M15 ranging.
* EMA M5 terlalu sering crossover.
* RSI berada di sekitar 50 tanpa momentum.
* Market structure belum jelas.
* Belum ada candle confirmation.
* Harga terlalu jauh dari EMA setelah breakout.
* Spread terlalu tinggi.
* M15 dan M5 berlawanan arah.
  Lebih baik NO SIGNAL daripada memaksakan BUY/SELL.

6. ATR STOP LOSS
   Gunakan ATR14 M5.
   Default atrSLMultiplier = 1.5.
   SL harus mempertimbangkan swing structure:

* BUY: di bawah swing low/ATR protection.
* SELL: di atas swing high/ATR protection.
  Jadikan multiplier configurable, jangan hard-code.

7. TAKE PROFIT
   Gunakan Risk/Reward configurable.
   Default riskReward = 2.0 atau RR 1:2.
   TP harus dihitung berdasarkan jarak SL, bukan fixed point.

8. CONFIDENCE SCORE
   Buat score berdasarkan kondisi nyata:

* M15 trend +20
* M5 alignment +15
* Pullback +15
* RSI confirmation +15
* Market structure +20
* Candle confirmation +15
  Total maksimum 100.
  Confidence tidak boleh mengabaikan mandatory condition.
  Contoh: score tinggi tetapi structure gagal → tetap NO SIGNAL.

9. SIGNAL OUTPUT
   Tampilkan:
   XAUUSD
   Signal: BUY/SELL/NO SIGNAL
   Strategy: XAUUSD_EMA_RSI_ATR_STRUCTURE
   Timeframe: M5
   Confirmation: M15
   Entry
   SL
   TP
   RR
   EMA20
   EMA50
   RSI
   ATR
   Trend
   Market Structure
   Confidence
   Timestamp
   signalId

10. DUPLICATE SIGNAL
    Jangan mengirim signal berulang pada candle yang sama.
    Simpan signalId, symbol, timeframe, timestamp, direction, entry, SL, TP, dan strategyName.

11. CONFIG
    Buat parameter configurable:
    emaFast = 20
    emaSlow = 50
    rsiPeriod = 14
    atrPeriod = 14
    atrSLMultiplier = 1.5
    riskReward = 2.0
    swingLookback = configurable
    minimumStructureDistance = configurable
    enableSpreadFilter = true
    maxSpread = configurable
    minimumConfidence = configurable

12. UI/LOG
    Jika project memiliki UI signal, tampilkan:
    Strategy
    M15 Trend
    M5 status
    Pullback
    RSI
    ATR
    Market Structure
    Signal
    Confidence

Jika NO SIGNAL, tampilkan alasan spesifik, contoh:
"NO SIGNAL — M15 bullish tetapi M5 belum confirmation."
"NO SIGNAL — Market structure belum confirmed."
"NO SIGNAL — Kondisi ranging."

13. VALIDATION
    Setelah implementasi:

* Jalankan lint/typecheck.
* Jalankan unit test.
* Test BUY.
* Test SELL.
* Test ranging.
* Test false breakout.
* Test duplicate candle.
* Test M15 bullish + M5 bearish.
* Test M15 bearish + M5 bullish.
* Test ATR SL.
* Test RR TP.
* Test NO SIGNAL.

Jika tersedia backtesting engine, tambahkan strategy ini tanpa mengubah strategy lama.

PENTING:

* Inspect repository terlebih dahulu sebelum coding.
* Jangan membuat mock/random signal.
* Gunakan data candle aktual.
* Jangan menghapus fitur existing.
* Jangan melakukan refactor besar yang tidak diperlukan.
* Strategy harus modular sehingga bisa diaktifkan/dinonaktifkan tanpa memengaruhi strategy lain.
* Setelah selesai, tampilkan file yang dibuat/diubah, logic yang diimplementasikan, hasil test, contoh signal, dan masalah yang masih ditemukan.
* Jangan lanjut ke strategi lain sebelum strategi ini selesai dan tervalidasi.

```
