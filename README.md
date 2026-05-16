# Analysis for Release of New Puzzle Mobile Game - Case Study

> A CEO-facing analytics case study on a new 2-player mobile puzzle game's 4-market soft launch.

## At a glance

I evaluated whether the newly launched 2-player puzzle game was ready for global rollout, using activity, match, and in-app-purchase data from the soft-launch markets (US, UK, India, Brazil). Defined stickiness, longevity, and loyalty metrics from scratch; ran cohort, conversion, and platform-mix analyses; and translated the findings into six concrete recommendations a CEO could act on — spanning marketing reallocation, trial promotions, server quality, and tiered difficulty.


| | |
|---|---|
| **Stack** | R · Tableau|
| **Datasets** | User Daily Activity · Match Data · User activity · Pusrchase History|
| **Deliverable** | Stakeholder ready slide deck with high level analysis points and 6 point recomendation plan|
| **Timebox** | 7 days, solo |

## Why this project

Consumer data can tell us so much and this example illustrates how usage/purchase data can tell a story of how a product fairs. Using these trends we can see how to tailor marketing approaches and truly reach the consumer meeting them at their interests. 

Diagnostic analysis (where is the game underperforming?) 
Prescriptive thinking (what's the smallest set of changes that would meaningfully move those metrics?)

The questions that drove the analysis:

- Is the game acquiring users at a healthy rate, and is acquisition translating to retention?
- Are some markets / platforms working noticeably better than others?
- Are players actually spending? If not, what's the gap between acquisition and the first purchase?
- What does a "loyal" player look like, and are we keeping enough of them around to monetize?

## Datasets

```
Data/
├── daily_daily_activity.csv   	# daily joins by individual users
├── data_in_app_purchases.csv   # match data for all players during roll out period
├── data_matches.csv            # in-app purchases per user
├── user_activity.csv 		    # Tableau Exports of Cleaned Data 
├── user_matches.csv		    # Tableau Exports of Cleaned Data
└── user_purchases.csv 		    # Tableau Exports of Cleaned Data
```

## The workflow

1. **Ingest & clean in R** — read the three CSVs, fix the match-count anomalies, impute the missing activity rows, label the outliers.
2. **Compute metrics** — daily / weekly active users, DAU/WAU, longevity, consistency, loyalty tiers, conversion rate, days-to-first-purchase.
3. **Explore in Tableau** — interactive cuts by country, platform, acquisition type, loyalty tier, and product group.
4. **Frame the story** — five analysis sections: Active Users & Retention → Country & Platform → Stickiness → Conversion & Purchasing → Recommendation Summary.
5. **Deliver** — a 12-slide deck with one CEO-readable insight per slide and a two-slide closing recommendation set.

## What the project demonstrates

- Data Cleaning (Imputation etc) and Statistical Analysis in R.
- Making decisions to show reason and transparency in analysis where it could have been easy to remove entirely (e.g. flag and label outliers).
- Visualizing user based data to create insights that drive decisions.
- Preparing a detailed but not overly technical presentation detailing reccomendations.

## Custom metrics

The dataset doesn't ship with off-the-shelf engagement metrics, so I built three from the daily activity table:

| Metric | Definition |
|---|---|
| **Longevity** | `Latest Day Active / Days Since Download` |
| **Consistency** | `# of Days Active / Days Since Download` |
| **Loyalty** | A player exceeding the 75th percentile on both Longevity *and* Consistency |

## What the analysis surfaced

- **Acquisition is healthy; retention/conversion is the real question.** DAU/WAU ratio improved week-over-week from ~29% to ~39%, which is encouraging — but a lot of that growth came from India, where players don't monetize at the same rate.
- **The US and UK grow more slowly but drive most of the purchasing.** Excluding India flips the per-user revenue picture entirely.
- **iOS uptake is weak — and it's worst in the markets that matter most.** When user-mix is benchmarked against actual platform market share in the US and UK, the game is materially under-indexed on iOS.
- **Conversion is low everywhere (<2%), and slow.** Players who do convert take ~7.69 days from download to first purchase. Less-committed players churn before they reach that threshold.
- **Loyal players are worth nearly 2x.** Profit per loyal player is roughly double that of less-committed players, especially on promotions and season passes.
- **High win rates may be masking a difficulty problem.** Loyal users are disproportionately playing the "quick" and "bot" modes, which I read as a search for harder challenge.

## What the recommendations were

Six concrete actions, paired to the findings:

1. & 2. **Marketing reallocation** — invest in iOS-targeted acquisition in the US and UK, with a social-media-first creative strategy.
3. & 4. **Bridge the 7.69-day gap** — run a 1–2 week trial promotion or free season pass with daily rewards to push less-committed players past the first-purchase threshold.
5. & 6. **Product changes for committed players** — invest in server-quality (the disconnection rate spikes among unsatisfied users) and ship a tiered difficulty system (Easy / Medium / Hard) or alternate-time modes to retain players seeking more challenge.

**Overall:** extend the soft-launch trial window and collect another cycle of data before global rollout.

## Repository layout

```
Puzzle-Game-Analysis/
├── README.md
├── Data Presentation.pptx	# Stakeholder ready presentation
├── puzzle_assesment.RMD	# Markdown Code file with plots and statistical analysis
├── Analaysis.pdf 		# The data dictionary and task outline
└── Data/         		# raw + generated CSVs (see above)
    └── images    		# exported visualizations
```

## What I'd do next

- **Push the trial timeline.** Seven days of analysis on a few weeks of soft-launch data only goes so far — a second cohort window would let me run a real cohort-retention curve rather than infer it.
- **Build a churn model** on top of the longevity/consistency features and use it as an early-warning signal for which acquisition channels are buying low-retention users.
- **Simulate the promo impact.** Now that the levers are identified (trial pass, difficulty tiers, iOS-targeted marketing), run the trial and see how the adjustments fair.

---

Built by **Vincenzo Coppola** — aspiring data analyst in the sports industry.
[GitHub](https://github.com/VinCoppola) · [LinkedIn](https://www.linkedin.com/in/vincenzo-coppola12/)
