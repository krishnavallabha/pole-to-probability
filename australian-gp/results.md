# 🏎️ 2026 Australian Grand Prix — Results

> **Circuit:** Albert Park, Melbourne, Australia
> **Date:** March 9, 2026
> **Round:** 1 of 24

---

## 📊 Model Prediction vs Actual Result

| | Predicted | Actual |
|--|-----------|--------|
| 🥇 Winner | Kimi Antonelli | **George Russell** |
| 🥈 2nd | George Russell | **Kimi Antonelli** |
| 🥉 3rd | Valtteri Bottas* | **Charles Leclerc** |
| 🎖️ Fastest Lap | — | — |
| ✅ Model Correct? | Almost 😅 | **Top 2 correct, wrong order** |

*\*Bottas P3 prediction was a model artifact — DNF'd in actual race*

---

## 🔢 Full Prediction Table

| Rank | Grid | Driver | XGB | Sim | Final |
|------|------|--------|-----|-----|-------|
| 1 | P2 | Kimi Antonelli | 35.8% | 38.3% | **36.8%** |
| 2 | P1 | George Russell | 37.1% | 33.4% | **35.6%** |
| 3 | P19 | Valtteri Bottas | 6.7% | 5.7% | **6.3%** ⚠️ |
| 4 | P3 | Isack Hadjar | 6.3% | 5.7% | **6.1%** |
| 5 | P4 | Charles Leclerc | 2.9% | 4.1% | **3.4%** |
| 6 | P6 | Lando Norris | 2.7% | 3.9% | **3.2%** |
| 7 | P21 | Carlos Sainz | 2.2% | 1.8% | **2.0%** ⚠️ |
| 8 | P5 | Oscar Piastri | 0.5% | 0.9% | **0.7%** |

> ⚠️ = suspected model artifact (see notes)

---

## 🏁 Actual Race Result

*Fill this in after the race on March 9, 2026*

| Pos | Driver | Team | Time/Gap |
|-----|--------|------|-------|
| 1 | George Russell | Mercedes | 1:23:06.801 |
| 2 | Kimi Antonelli | Mercedes | +2.974s |
| 3 | Charles Leclerc | Ferrari | +15.519s |
| 4 | Lewis Hamilton | Ferrari | +16.143s |
| 5 | Lando Norris | McLaren | +51.741s |
| 6 | Max Verstappen | Red Bull | +54.617s |
| 7 | Oliver Bearman | Haas | +1 Lap |
| 8 | Arvid Lindblad | RB | +1 Lap |
| 9 | Gabriel Bortoleto | Audi | +1 Lap |
| 10 | Pierre Gasly | Alpine | +1 Lap |
| 15 | Carlos Sainz | Williams | +2 Laps |
| DNF | Fernando Alonso | Aston Martin | — |
| DNF | Valtteri Bottas | Cadillac | — |
| DNF | Isack Hadjar | Red Bull | — |
| DNS | Oscar Piastri | McLaren | — |
| DNS | Nico Hulkenberg | Audi | — |

**Fastest Lap:** —
**Safety Cars:** —
**Notable incidents:** Piastri & Hulkenberg DNS, Hadjar DNF, Alonso DNF, Bottas DNF

---

## 🧠 Model Notes & Post-Race Analysis

### What the model got right
- ✅ **Mercedes 1-2** — nailed it, both Russell & Antonelli in top 2
- ✅ **Leclerc top 5** — predicted P5, finished P3 (close!)
- ✅ **Norris top 6** — predicted P6, finished P5
- ✅ **Verstappen recovery** — model underweighted him (P20 start) but he charged to P6
- ✅ **Bottas & Sainz NOT winning** — despite model artifacts, both were non-factors

### What the model got wrong
- ❌ **Winner order flipped** — Russell won, not Antonelli (35.6% vs 36.8% was basically a coin flip anyway)
- ❌ **Bottas P3 artifact** — DNF'd in reality, confirming this was a bad prediction
- ❌ **Hadjar DNF** — predicted P4 contender, retired from the race
- ❌ **Piastri & Hulkenberg DNS** — not modelled at all (impossible to predict pre-race)
- ❌ **Bearman P7** — not on the model's radar at all, good result for Haas

### Known issues with this prediction

- **Bottas at 6.3% from P19** — his strong 2024/2025 form score inflated his win probability despite starting near the back. Melbourne is historically very hard to overtake at, making a P19 win essentially impossible. Fix for next race: add a hard grid position cap (e.g. P15+ gets win_prob multiplied by 0.1)

- **Sainz at 2% from P21** — same issue. Historical Melbourne stats are bleeding through too strongly relative to grid position penalty.

- **2026 constructor pace** is still estimated from one qualifying session. Will improve as season data accumulates.

- **Verstappen severely underweighted** — starting P20 tanks his ML score but he's a 4x champion with the pace to recover. Monte Carlo doesn't fully model his overtaking ability.

### Ideas for next race
- [ ] Add hard grid position penalty cap for P15+
- [ ] Weight 2026 quali gap to pole as a feature (not just grid position)
- [ ] Add tyre strategy uncertainty layer to Monte Carlo
- [ ] Pull 2026 FP1/FP2 lap time data via FastF1 for pace context

---

## 📈 Model Performance Tracker

| Metric | Value |
|--------|-------|
| Predicted winner correct |  (got P2 right, wrong order) |
| Winner in top 2 predictions | Yes — Russell was our P2 pick |
| Top 2 drivers correct |  Yes — Russell & Antonelli |
| Biggest hit | Mercedes 1-2 prediction |
| Biggest miss | Bottas P3 (DNF), Hadjar DNF, Piastri DNS |

---

*Data sources: Jolpica-F1 API (2018–2025) · FastF1 v3.8.1 · XGBoost · Monte Carlo (15,000 simulations)*
*Notebook: [2026_AustralianGP_FastF1_Predictor.ipynb](./2026_AustralianGP_FastF1_Predictor.ipynb)*
