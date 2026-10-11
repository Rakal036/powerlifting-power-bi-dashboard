# 🏋️ Powerlifting Analytics — Power BI

An interactive Power BI report analysing **386,000+ competition results** from **8,400+ powerlifting meets** (OpenPowerlifting dataset, data through 2017).

![Report preview](images/overview.png)

## Questions this report answers
- How has the sport grown over time, by number of meets and competitors?
- Which countries and federations host the most competitions?
- How do squat, bench, deadlift and Wilks scores differ by sex, equipment and weight class?
- How do bodyweight and age relate to strength?
- Who are the top athletes by Wilks score?

## Report pages
| Page | What it shows |
|---|---|
| Global Overview | Map of competitors by country with a year slider |
| Powerlifting Evolution | Growth over time, strength by age group, bodyweight vs total |
| Competition Landscape | Biggest federations and countries, equipment share |
| Performance Analysis | Average lifts and Wilks by sex, with equipment, weight class and year filters |
| Athlete Explorer | Top 15 leaderboard (dynamic rank), athlete profile and Wilks history |

## Data model
- Two tables, `meets` (one row per meet) and `openpowerlifting` (one row per result), joined one-to-many on MeetID.
- Cleaned in Power Query: types set, duplicates removed, unused columns dropped.
- Calculated columns: Full Meet flag, Age Group (IPF categories) and rounded bodyweight.

## DAX highlights
- **Full-meet logic:** Average Total and Wilks only count lifters who completed all three lifts, so single-lift events don't distort the results.
- **Dynamic ranking:** RANKX over ALLSELECTED, so the leaderboard re-ranks with every slicer.
- **Athlete profile card:** TREATAS and CONCATENATEX list each athlete's countries and federations.
- **Share of total:** DIVIDE with ALLSELECTED for equipment percentages.

## Tools
Power BI Desktop · Power Query · DAX

## Data source
[powerlifting-database]([https://www.openpowerlifting.org/](https://www.kaggle.com/datasets/dansbecker/powerlifting-database?select=meets.csv)) via Kaggle (meets.csv, openpowerlifting.csv).
