# 🏎️ pole-to-probability

> *Because watching 20 cars drive in circles shouldn't stop you from doing data science about it.*

---

```
P1  KIMI ANTONELLI     ████████████████████  38.8%  ← the model (JPN)
P2  YOUR PREDICTION    ███                    4.1%  ← you, picking with your heart
P11 MAX VERSTAPPEN     ██████                 9.3%  ← history says yes, grid says no
```

---

## what is this

A collection of ML models that attempt to predict F1 Grand Prix race winners using **real historical data** — not vibes, not gut feeling, not "I just feel like Lando is due one."

Each race gets its own notebook. Each notebook pulls real data from the **Jolpica-F1 API** + **FastF1**, engineers features that actually matter (grid position, track-specific podium history, recent form, constructor pace, tyre degradation, DNF probability, live weather), trains an **XGBoost** model on real outcomes, and runs a **per-lap Monte Carlo simulation** with chaos factors baked in.

Does it work? Getting better every race. Is it more reliable than your fantasy F1 team? Almost certainly.

---

## 🏁 races so far

| Race | Round | Predicted Winner | Actual Winner | Result |
|------|-------|-----------------|---------------|--------|
| [Australian GP](./australian-gp/) | R1 | Kimi Antonelli (36.8%) | George Russell | 🟡 Top 2 correct, order flipped |
| [Chinese GP](./chinese-gp/) | R2 | — | Kimi Antonelli | ⬜ No prediction made |
| [Japanese GP](./japanese-gp/) | R3 | Kimi Antonelli (38.8%) | — | 🕐 Race pending |

*Updated after each race weekend throughout the 2026 season.*

---

## 📈 season accuracy tracker

| Metric | Value |
|--------|-------|
| Races predicted | 2 of 3 |
| Winner correct | 0 / 2 |
| Winner in top 2 | 1 / 2 (AUS ✅) |
| Top 2 both correct | 1 / 2 (AUS ✅) |
| Biggest hit | Mercedes 1-2 at AUS |
| Biggest miss | Bottas P3 artifact (DNF'd) |

---

## how it works

```
Real Qualifying Data          Historical Race Results (2018–2025)
        │                                   │
        ▼                                   ▼
  Feature Engineering  ◄──────────────────────────────────────┐
  - grid_advantage (track-specific decay)                      │
  - gap_to_pole (real quali times in seconds)   Jolpica API   │
  - track_win_rate / podium_rate                (paginated,    │
  - recent_form_score (2024-2025)                all drivers)  │
  - constructor_pace_2026 (updated each race)  ──────────────►┘
  - tyre_deg_rate (FastF1 stint analysis)
  - pit_stop_efficiency (FastF1)
  - weather_impact (Open-Meteo live forecast)
  - dnf_probability (3-component module)
  - 2026_season_form (real race results)
        │
        ▼
   XGBoost Model
   (trained on real historical race outcomes)
        │
        ▼
  Per-Lap Monte Carlo (20,000 sims × 53 laps)
  + tyre degradation curve per compound
  + safety car events per lap
  + DNF probability per lap per driver
  + pit window open/close logic
  + track-specific overtaking probability
        │
        ▼
  Ensemble (60% XGBoost + 40% Monte Carlo)
  + Model confidence score (entropy-based)
        │
        ▼
  🏆 Predicted Winner
```

---

## the stack

```python
fastf1          # lap times, tyre stints, pit stop data, race pace
jolpica-f1-api  # every race result since 1950 (ergast's cooler successor)
open-meteo      # live race day weather forecast (free, no API key needed)
xgboost         # main prediction model
scikit-learn    # model comparison, cross-validation, logistic regression
pandas + numpy  # data wrangling
matplotlib      # dark mode dashboards
```

---

## repo structure

```
pole-to-probability/
│
├── australian-gp/
│   ├── 2026_AustralianGP_FastF1_Predictor.ipynb
│   └── results.md
│
├── chinese-gp/               ← no prediction made (missed qualifying)
│
├── japanese-gp/
│   ├── 2026_JapaneseGP_Predictor.ipynb
│   └── results.md
│
├── bahrain-gp/               ← coming soon
│
└── README.md                 ← you are here
```

---

## model evolution

The model gets meaningfully better each race as more 2026 data accumulates:

| Version | Race | Key upgrades |
|---------|------|-------------|
| v1 | Australian GP | Real Jolpica data, XGBoost, basic Monte Carlo |
| v2 | Japanese GP | FastF1 tyre deg + pit data, per-lap Monte Carlo (53 laps × 20k sims), DNF module (3-component), live weather, gap-to-pole feature, track normalisation, model confidence score |
| v3 | Bahrain GP | *coming — overtaking ability feature, grid position hard cap, Logistic Reg as primary model* |

---

## quick start

```bash
git clone https://github.com/yourusername/pole-to-probability
cd pole-to-probability/japanese-gp
```

Open the `.ipynb` in **Google Colab** and run all cells.
First run downloads ~80MB of FastF1 cache. Grab a coffee. ☕

**Requirements** (auto-installed in Cell 1):
```
fastf1 xgboost scikit-learn pandas numpy matplotlib seaborn requests
```

---

## known limitations

- The model has never driven an F1 car *(neither have I, but still)*
- Safety cars are unpredictable by definition — we just accept this
- McLaren's DNS streak is modelled but the root cause isn't (we just know it keeps happening)
- Verstappen's overtaking ability is severely underweighted by grid position penalty
- Pit stop efficiency data currently returns empty for some circuits via FastF1
- With only 6 years of Suzuka data, 120 training rows is tight for XGBoost
- This will not make you money at a betting shop. Please do not try.

---

## contributing

Found a bug? Have a better feature idea? Know why Stroll didn't even leave the garage in Australia?
PRs welcome. Open an issue. Let's talk F1.

---



<div align="center">

*Built with way too much interest in a sport where the winner is sometimes decided by who pits during a safety car*

⬛🟥⬛ &nbsp;&nbsp; 🏁 &nbsp;&nbsp; ⬛🟥⬛

</div>
