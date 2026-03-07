# 🏎️ 2026 Australian Grand Prix — Results

> **Circuit:** Albert Park, Melbourne, Australia
> **Date:** March 9, 2026
> **Round:** 1 of 24

---

## 📊 Model Prediction vs Actual Result

| | Predicted | Actual |
|--|-----------|--------|
| 🥇 Winner | Kimi Antonelli | ` ` |
| 🥈 2nd | George Russell | ` ` |
| 🥉 3rd | Valtteri Bottas* | ` ` |
| 🎖️ Fastest Lap | — | ` ` |
| ✅ Model Correct? | — | ` yes / no ` |

*\*Bottas P3 prediction is likely a model artifact — see notes below*

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

| Pos | Driver | Team | Notes |
|-----|--------|------|-------|
| 1 | | | |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |
| DNF | | | |
| DNF | | | |

**Fastest Lap:** &nbsp;
**Safety Cars:** &nbsp;
**Notable incidents:** &nbsp;

---

## 🧠 Model Notes & Post-Race Analysis

### What the model got right
*Fill in after race*
- 

### What the model got wrong
*Fill in after race*
- 

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
| Predicted winner correct | ` - ` |
| Winner in top 3 predictions | ` - ` |
| Average position error (top 5) | ` - ` |
| Biggest miss | ` - ` |

---

*Data sources: Jolpica-F1 API (2018–2025) · FastF1 v3.8.1 · XGBoost · Monte Carlo (15,000 simulations)*
*Notebook: [2026_AustralianGP_FastF1_Predictor.ipynb](./2026_AustralianGP_FastF1_Predictor.ipynb)*
