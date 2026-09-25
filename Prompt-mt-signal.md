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
