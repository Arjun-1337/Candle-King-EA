# 👑 Candle King – Stop Order Algo (Fixed)

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/6/64/Metatrader_logo.png" width="100" alt="MetaTrader 5 Logo"/>
</p>

<p align="center">
  <b>Candle King EA</b>  
  ⚡ Breakout logic with dual pending stops | 🎯 Per-trade TP & SL | 🔄 Automatic order cleanup | 📊 Trailing stop engine | 🛡️ Retry-safe execution
</p>

---

## 🔥 Overview

`Candle_King_StopOrder_Fixed.mq5` is a **breakout trading Expert Advisor** designed for MetaTrader 5.  
It automatically places **dual pending stop orders** above/below the previous candle and manages positions with built-in **risk controls and trailing stop logic**.

- 📌 **Dual stop entry strategy** (Buy Stop above high, Sell Stop below low)  
- 🛠️ **Automatic pending order cleanup** (no stale orders)  
- 🎯 **Take Profit in pips**  
- 🛡️ **Trailing Stop Engine** with breakeven logic  
- 🔄 **Opposite pending order removal after fill**  
- ⚖️ **Lot normalization** (respects broker limits & step sizes)  
- 🔁 **Safe order retries** with backoff  
- 📊 **New bar only mode** or **continuous pending mode**  

---

## 🛠️ Features

✅ Dual pending stop placement (previous candle breakout)  
✅ Per-trade TP/SL in pips  
✅ Smart SL validation (never too close to market)  
✅ Opposite pending orders auto-cancelled on fill  
✅ Normalized lot sizing (min/max/step aware)  
✅ Trailing stop with breakeven shift  
✅ Safe order retries (`MaxOrderSendRetries`)  
✅ Optional **Only on New Bar** execution  

---

## ⚙️ Input Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| `InpLot` | 0.10 | Lot size (auto-normalized to broker requirements) |
| `InpMagic` | 20250826 | Magic number (EA identifier) |
| `InpSlippage` | 5 | Max slippage (points) |
| `TrailingStartPoints` | 10 | Start trailing when profit >= this many points |
| `TrailingDistance` | 10 | Distance to keep from price when trailing (points) |
| `InpTP_Pips` | 30 | Take Profit (pips) |
| `OnlyOnNewBar` | true | Place orders only once per new bar |
| `Timeframe` | PERIOD_CURRENT | Timeframe for candle reference |
| `MaxOrderSendRetries` | 2 | Retry attempts for order placement |

---

## 📊 Strategy Logic

1. **Candle Breakout Entry**  
   - Place **Buy Stop** above previous candle’s high  
   - Place **Sell Stop** below previous candle’s low  

2. **Order Management**  
   - If trade executes, opposite pending is cancelled  
   - Pending orders auto-cleaned each bar to avoid duplicates  
   - No new orders while a position is active  

3. **Risk Management**  
   - **SL** placed at opposite side of previous candle  
   - **TP** based on user-defined pip offset  
   - Lot size adjusted to broker constraints  

4. **Trailing Stop Engine**  
   - Activates once trade moves `TrailingStartPoints` into profit  
   - SL trails price while respecting breakeven level  
   - Updates dynamically until TP/SL hit  

---

## 🚀 Installation

1. Copy `Candle_King_StopOrder_Fixed.mq5` into: MQL5/Experts/
2. Restart MetaTrader 5.  
3. Attach EA to desired chart (`M15` or `H1` recommended).  
4. Configure **Inputs** based on strategy & risk profile.  

---

## 📷 Screenshots (Optional)

*(Insert chart examples of pending orders, trade execution, and trailing stop behavior)*

---

## 🏆 Best Practices

- Works best on **volatile pairs** with clean candle breaks (e.g., XAUUSD, GBPJPY).  
- Use **higher TF (H1, H4)** to reduce noise in ranging markets.  
- Always **enable trailing stops** to secure profits in trending moves.  
- Test different **OnlyOnNewBar** vs. continuous modes in backtests.  
- Run on **low-latency VPS** for optimal pending order execution.  

---

## 📜 License

This EA is for **personal & educational use only**.  
Author: **Arjun1337 (patched & fixed)**  

---

<p align="center">
<img src="https://img.shields.io/badge/Platform-MetaTrader%205-blue?logo=metatrader&logoColor=white"/>
<img src="https://img.shields.io/badge/Language-MQL5-orange?logo=c&logoColor=white"/>
<img src="https://img.shields.io/badge/Status-Stable-success"/>
</p>
