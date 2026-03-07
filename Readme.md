# 🏎️ pole-to-probability

> *Because watching 20 cars drive in circles shouldn't stop you from doing data science about it.*

---

```
P1  GEORGE RUSSELL     ████████████████████  32.4%  ← the model
P2  YOUR PREDICTION    ███                    4.1%  ← you, picking with your heart
P20 MAX VERSTAPPEN     █                      1.2%  ← started from the back (again)
```

---

## what is this

A collection of ML models that attempt to predict F1 Grand Prix race winners using **real historical data** — not vibes, not gut feeling, not "I just feel like Lando is due one."

Each race gets its own notebook. Each notebook pulls real data from the **Jolpica-F1 API** + **FastF1**, engineers features that actually matter (grid position, Melbourne podium history, recent form, constructor pace), trains an **XGBoost** model on real outcomes, and runs a **Monte Carlo simulation** with chaos factors baked in (safety cars, DNFs, first-race-of-new-regs madness).

Does it work? Somewhat. Is it more reliable than your fantasy F1 team? Almost certainly.

---

## races so far

| 🏁 Race | Season | Predicted Winner | Actual Winner | 😬 |
|---------|--------|-----------------|---------------|-----|
| [Australian GP](./australian-gp/) | 2026 | TBD | TBD | race is tomorrow lol |

*More races added throughout the 2026 season.*

---

## the stack

```python
fastf1          # lap times, telemetry, sector data — the good stuff
jolpica-f1-api  # every race result since 1950 (ergast's cooler successor)
xgboost         # does the heavy lifting
scikit-learn    # model comparison, cross-validation
pandas + numpy  # obviously
matplotlib      # pretty charts to show people at parties
```

---

## how it works

```
Real Qualifying Data          Historical Race Results (2018–2025)
        │                                   │
        ▼                                   ▼
  Feature Engineering  ◄──────────────────────────────┐
  - grid_advantage                                     │
  - quali_advantage              Jolpica F1 API        │
  - melb_win_rate                (all 20 drivers,      │
  - recent_form_score             not just the winner) │
  - constructor_pace             ─────────────────────►┘
        │
        ▼
   XGBoost Model
   (trained on real outcomes)
        │
        ▼
  Monte Carlo Sim (15,000 runs)
  + safety car lottery
  + DNF roulette
  + new-regs chaos factor
        │
        ▼
  🏆 Predicted Winner
     (probably Russell)
```

---

## repo structure

```
pole-to-probability/
│
├── australian-gp/
│   └── 2026_AustralianGP_FastF1_Predictor.ipynb
│
├── chinese-gp/           ← coming soon
├── japanese-gp/          ← coming soon
├── bahrain-gp/           ← coming soon
│
└── README.md             ← you are here
```

---

## quick start

```bash
git clone https://github.com/yourusername/pole-to-probability
cd pole-to-probability/australian-gp
```

Then open the `.ipynb` in **Google Colab** and run all cells.  
First run downloads ~50MB of FastF1 cache data. Grab a coffee. ☕

**Requirements** (auto-installed in Cell 1):
```
fastf1 xgboost scikit-learn pandas numpy matplotlib seaborn requests
```

---

## known limitations

- The model has never driven an F1 car *(neither have I, but still)*
- Safety cars are unpredictable by definition — we just accept this
- Max Verstappen's qualifying crash in 2026 Australia was not in the training data
- The 2026 constructor pace weights are educated guesses based on one qualifying session
- Weather is not modelled *(Melbourne weather is basically a random number generator anyway)*
- This will not make you money at a betting shop. Please do not try.

---

## results & accuracy

*Section to be updated after each race weekend.*

The goal isn't a perfect prediction — it's understanding **why** certain drivers and teams are favoured, and by how much. The feature importance charts are honestly more interesting than the final number.

---

## contributing

Found a bug? Have a better feature idea? Know why Stroll didn't even leave the garage?  
PRs welcome. Open an issue. Let's talk F1.

---

## disclaimer

```
This project is for educational and entertainment purposes only.
Do not use it to make financial decisions.
The author accepts no responsibility for fantasy F1 team failures.
Max Verstappen will probably still win the championship anyway.
```

---

<div align="center">

*Built with way too much interest in a sport where the winner is sometimes decided by who pits during a safety car*

⬛🟥⬛ &nbsp;&nbsp; 🏁 &nbsp;&nbsp; ⬛🟥⬛

</div>
