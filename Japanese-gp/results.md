# 🏎️ 2026 Japanese Grand Prix — Results

> **Circuit:** Suzuka International Racing Course, Japan
> **Date:** March 30, 2026
> **Round:** 3 of 24

---

## 📊 Model Prediction vs Actual Result

| | Predicted | Actual |
|--|-----------|--------|
| 🥇 Winner | Kimi Antonelli | ` ` |
| 🥈 2nd | George Russell | ` ` |
| 🥉 3rd | Max Verstappen | ` ` |
| 🎖️ Fastest Lap | — | ` ` |
| ✅ Model Correct? | — | ` yes / no ` |

---

## 🔢 Full Prediction Table

| Rank | Grid | Driver | XGB | Sim | Final |
|------|------|--------|-----|-----|-------|
| 1 | P1 | Kimi Antonelli | 6.0% | 88.1% | **38.8%** |
| 2 | P2 | George Russell | 33.4% | 8.3% | **23.4%** |
| 3 | P11 | Max Verstappen | 15.6% | 0.0% | **9.3%** |
| 4 | P3 | Oscar Piastri | 11.8% | 3.4% | **8.5%** |
| 5 | P5 | Lando Norris | 8.1% | 0.1% | **4.9%** |
| 6 | P6 | Lewis Hamilton | 6.6% | 0.0% | **4.0%** |
| 7 | P4 | Charles Leclerc | 4.2% | 0.1% | **2.5%** |
| 8 | P20 | Valtteri Bottas | 1.6% | 0.0% | **1.0%** ⚠️ |

> ⚠️ = suspected model artifact (rear-grid driver with inflated historical stats)

---

## 🌤️ Race Conditions

| Parameter | Value |
|-----------|-------|
| Condition | Dry |
| Rain probability | 8.5% |
| Expected rain | 0.0mm |
| Wind speed | 8.4 km/h |
| Weather impact score | 0.051 (essentially dry) |

---

## 🧠 Model Notes (Pre-Race)

### Key signals going in
- **Antonelli on pole** — Monte Carlo strongly favours pole at Suzuka (88.1%) due to very low overtaking probability (4% per lap vs 12% at Shanghai)
- **XGBoost favours Russell** (33.4%) — his recent form score + 2026 season points (43 pts) edges Antonelli slightly in the ML model
- **Verstappen P11** — model gives him 15.6% XGB due to exceptional Suzuka history (4 wins, 5 podiums in 6 races) despite starting from mid-grid. Monte Carlo gives him near-zero because overtaking is so hard
- **McLaren reliability flag** — Piastri & Norris both in top 5 of grid but both teams flagged HIGH risk after 4 DNS in 2 races
- **Tension between XGB & Monte Carlo** — Russell leads XGB (33.4%) but Antonelli dominates Monte Carlo (88.1%). Ensemble lands on Antonelli at 38.8%

### Known model limitations for this race
- **Monte Carlo too pole-dominant** — 88% for P1 at Suzuka is realistic historically but feels extreme. Low overtaking is real but not absolute
- **Verstappen severely split** — XGB says 15.6% (history), Monte Carlo says ~0% (grid pos). This tension is unresolved
- **Pit stop efficiency empty** — FastF1 pit data returned no results for 2024 Suzuka, feature set to 0.5 for all drivers

---

## 🏁 Actual Race Result

*Fill in after the race on March 30, 2026*

| Pos | Driver | Team | Time/Gap |
|-----|--------|------|----------|
| 1 | | | |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |
| 6 | | | |
| DNF | | | |
| DNF | | | |

**Fastest Lap:** &nbsp;
**Safety Cars:** &nbsp;
**Notable incidents:** &nbsp;

---

## 📈 Post-Race Analysis

### What the model got right
*Fill in after race*
-

### What the model got wrong
*Fill in after race*
-

### Ideas for next race
- [ ] Fix Monte Carlo pole dominance — increase lap time variance or add random pace shifts
- [ ] Resolve XGB vs Monte Carlo Verstappen split — add explicit overtaking ability feature
- [ ] Fix pit stop efficiency — debug why FastF1 returned empty DataFrame for Suzuka 2024
- [ ] Add grid position hard cap (P15+ win_prob × 0.15) to fix Bottas artifact
- [ ] Consider switching best model to Logistic Reg (0.9955 ROC-AUC vs XGBoost 0.8783)

---

## 📊 Model Performance Tracker

| Metric | Value |
|--------|-------|
| Predicted winner correct | ` - ` |
| Winner in top 2 predictions | ` - ` |
| Top 2 drivers correct | ` - ` |
| Biggest hit | ` - ` |
| Biggest miss | ` - ` |

---

## 🔧 Technical Notes

| Parameter | Value |
|-----------|-------|
| Training rows | 120 (6 Suzuka races × 20 drivers) |
| Season data rows | 1,838 (paginated, 2022–2025) |
| Features used | 12 (reduced from 20 to avoid overfitting) |
| XGBoost ROC-AUC | 0.878 ± 0.190 |
| Logistic Reg ROC-AUC | 0.996 ± 0.009 |
| Monte Carlo simulations | 20,000 |
| Laps simulated | 53 |
| Overtake probability/lap | 4.0% (Suzuka — very low) |
| Model confidence score | 0.366 (HIGH) |

---

*Data sources: Jolpica-F1 API (2018–2025) · FastF1 v3.8.1 · Open-Meteo (live forecast)*
*Notebook: [2026_JapaneseGP_Predictor.ipynb](./2026_JapaneseGP_Predictor.ipynb)*
