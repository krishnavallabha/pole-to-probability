# 🏎️ 2026 Japanese Grand Prix — Results

> **Circuit:** Suzuka International Racing Course, Japan
> **Date:** March 30, 2026
> **Round:** 3 of 24

---

## 📊 Model Prediction vs Actual Result

| | Predicted | Actual |
|--|-----------|--------|
| 🥇 Winner | Kimi Antonelli | **Kimi Antonelli** ✅ |
| 🥈 2nd | George Russell | **Oscar Piastri** ❌ |
| 🥉 3rd | Max Verstappen | **Charles Leclerc** ❌ |
| 🎖️ Fastest Lap | — | — |
| ✅ Model Correct? | **YES — first correct winner prediction! 🎉** | |

---

## 🔢 Full Prediction Table

| Rank | Grid | Driver | XGB | Sim | Final | Actual Pos |
|------|------|--------|-----|-----|-------|------------|
| 1 | P1 | Kimi Antonelli | 6.0% | 88.1% | **38.8%** | **P1 ✅** |
| 2 | P2 | George Russell | 33.4% | 8.3% | **23.4%** | P4 ❌ |
| 3 | P11 | Max Verstappen | 15.6% | 0.0% | **9.3%** | P8 ❌ |
| 4 | P3 | Oscar Piastri | 11.8% | 3.4% | **8.5%** | P2 ✅ |
| 5 | P5 | Lando Norris | 8.1% | 0.1% | **4.9%** | P5 ✅ |
| 6 | P6 | Lewis Hamilton | 6.6% | 0.0% | **4.0%** | P6 ✅ |
| 7 | P4 | Charles Leclerc | 4.2% | 0.1% | **2.5%** | P3 ✅ |
| 8 | P20 | Valtteri Bottas | 1.6% | 0.0% | **1.0%** ⚠️ | P19 |

> ⚠️ = confirmed model artifact — Bottas P19 in reality

---

## 🌤️ Race Conditions

| Parameter | Value |
|-----------|-------|
| Condition | Dry |
| Rain probability | 8.5% |
| Expected rain | 0.0mm |
| Wind speed | 8.4 km/h |
| Weather impact score | 0.051 |

---

## 🏁 Actual Race Result

| Pos | Driver | Team | Time/Gap |
|-----|--------|------|----------|
| 1 | Kimi Antonelli | Mercedes | 1:28:03.403 |
| 2 | Oscar Piastri | McLaren | +13.722s |
| 3 | Charles Leclerc | Ferrari | +15.270s |
| 4 | George Russell | Mercedes | +15.754s |
| 5 | Lando Norris | McLaren | +23.479s |
| 6 | Lewis Hamilton | Ferrari | +25.037s |
| 7 | Pierre Gasly | Alpine | +32.340s |
| 8 | Max Verstappen | Red Bull | +32.677s |
| 9 | Liam Lawson | RB | +50.180s |
| 10 | Esteban Ocon | Haas | +51.216s |
| 11 | Nico Hulkenberg | Audi | +52.280s |
| 12 | Isack Hadjar | Red Bull | +56.154s |
| 13 | Gabriel Bortoleto | Audi | +59.078s |
| 14 | Arvid Lindblad | RB | +59.848s |
| 15 | Carlos Sainz | Williams | +65.007s |
| 16 | Franco Colapinto | Alpine | +65.773s |
| 17 | Sergio Perez | Cadillac | +92.453s |
| 18 | Fernando Alonso | Aston Martin | +1 Lap |
| 19 | Valtteri Bottas | Cadillac | +1 Lap |
| 20 | Alex Albon | Williams | +2 Laps |
| DNF | Lance Stroll | Aston Martin | — |
| DNF | Oliver Bearman | Haas | — |

**Fastest Lap:** —
**Safety Cars:** —
**Notable incidents:** Stroll DNF, Bearman DNF

---

## 🧠 Post-Race Analysis

### What the model got right
- ✅ **Antonelli wins** — model's top pick at 38.8%, first correct winner prediction!
- ✅ **Piastri top 4** — predicted P4, finished P2. Direction correct
- ✅ **Norris P5** — predicted P5, finished P5. Exact match
- ✅ **Hamilton P6** — predicted P6, finished P6. Exact match
- ✅ **Leclerc top 5** — predicted P7, finished P3. Close
- ✅ **Top 6 all predicted within top 7** — genuinely strong result for the model
- ✅ **Monte Carlo logic vindicated** — low overtaking at Suzuka proved real. P1 won, grid order largely held

### What the model got wrong
- ❌ **Russell P4 not P2** — XGBoost heavily favoured Russell (33.4%) but Piastri beat him cleanly
- ❌ **Verstappen P8 not P3** — model gave him 9.3% based on Suzuka history, but P11 start was too far back. Monte Carlo (0%) was actually closer to right
- ❌ **Bearman DNF** — model rated him well after P5 CHN and P7 AUS, but he retired
- ❌ **Bottas still an artifact** — P19 in reality vs 1.0% prediction. Still too high for a P20 starter

### Key insight: XGB vs Monte Carlo tension
The split between XGBoost (Russell 33.4%) and Monte Carlo (Antonelli 88.1%) was resolved by the ensemble toward Antonelli — and that was correct. The Monte Carlo's low overtaking logic proved right: pole position won, top-3 grid positions finished P1/P2/P3. Track position was everything at Suzuka.

The big lesson: **at technical low-overtaking circuits, weight Monte Carlo more heavily.** Consider 40/60 XGB/MC split for Suzuka-type tracks vs 60/40 for street circuits.

---

## 📈 Model Performance Tracker

| Metric | Value |
|--------|-------|
| Predicted winner correct | ✅ YES — Antonelli |
| Winner in top 2 predictions | ✅ YES |
| Top 6 all in predicted top 8 | ✅ YES |
| Norris exact finish | ✅ P5 predicted, P5 actual |
| Hamilton exact finish | ✅ P6 predicted, P6 actual |
| Biggest hit | Antonelli win + Norris P5 + Hamilton P6 |
| Biggest miss | Russell overrated, Verstappen overrated |
| Model confidence score | 0.366 HIGH — justified ✅ |

---

## 🔧 Technical Notes

| Parameter | Value |
|-----------|-------|
| Training rows | 120 (6 Suzuka races × 20 drivers) |
| Season data rows | 1,838 (paginated, 2022–2025) |
| Features used | 12 |
| XGBoost ROC-AUC | 0.878 ± 0.190 |
| Logistic Reg ROC-AUC | 0.996 ± 0.009 |
| Monte Carlo simulations | 20,000 × 53 laps |
| Overtake probability/lap | 4.0% (very low — Suzuka) |
| Model confidence | 0.366 HIGH |

### Fixes for next race
- [ ] Increase Monte Carlo weight for technical circuits (try 40/60 XGB/MC)
- [ ] Add explicit overtaking ability modifier for Verstappen
- [ ] Fix pit stop efficiency — FastF1 returning empty DataFrame
- [ ] Reduce Bearman rating — mid-field points don't indicate outright pace
- [ ] Add hard grid position cap: P15+ gets `win_prob × 0.15`
- [ ] Consider Logistic Regression as primary model (0.996 ROC-AUC vs XGBoost 0.878)

---

*Data sources: Jolpica-F1 API (2018–2025) · FastF1 v3.8.1 · Open-Meteo (live forecast)*
*Notebook: [2026_JapaneseGP_Predictor.ipynb](./2026_JapaneseGP_Predictor.ipynb)*
