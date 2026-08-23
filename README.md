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
