# Workout Strength Trend Analysis + Forecasting

This project analyzes my workout log data to identify training trends and forecast future strength performance. Using exported session data from the app **Hevy**, the notebook cleans and restructures the dataset into daily and weekly summaries, compares intensity vs volume patterns, and generates predictive estimates for future progress. The main exercises I chose to look at were the front squat, dumbbell shoulder press, barbell bench press, lat pull down, clean, and squat.  

---

## What This Project Does

- Loads and cleans exported workout history data
- Creates daily and weekly training summaries by exercise
- Compares **low volume vs high volume** sessions to understand intensity trends
- Computes key training metrics:
  - daily max weight
  - weekly max weight
  - total sets and total reps
  - training volume (weight × reps)
  - estimated 1RM (e1RM)
- Visualizes long-term training patterns across major lifts
- Builds forecasting models to estimate strength progression over the next several weeks

---

## Methods Used

### 1) Data Processing
- Converts timestamps into usable `day` and `week` bins
- Groups by exercise title and time period to summarize performance
- Creates volume and intensity metrics for each lift

### 2) Volume Classification
Sessions are classified into **low volume vs high volume** days using a combination of:
- number of sets performed
- rep range constraints (to avoid misclassifying high-rep work)

This helps compare whether heavier lifts tend to happen on lower-volume days.

### 3) Correlation Analysis
The project calculates correlations between:
- volume vs weekly max weight
- volume vs next-week max weight (lag correlation)

This helps measure whether workload relates to future performance changes.

### 4) Forecasting
Two forecasting approaches are used:
- **Linear regression baseline** to project weekly max weight trends
- **Iterative e1RM forecasting model**, using lag/rolling features such as:
  - previous week e1RM values
  - 3-week rolling e1RM averages
  - previous volume / sets / reps trends

Predictions are generated week-by-week for the next 6–8 weeks.

---

## Files

- `stats.ipynb` — main notebook for cleaning, analysis, visualization, and forecasting
- `data/` *(optional)* — folder for exported workout logs (not included if private)

---

## Challenges 
I ran into common debugging pandas/sklearn errors, as well as not having enough data for certain exercises. Resolving these issues improved the reliability of the analysis and helped reinforce best practices around reproducibility and clean data pipelines.

---
# Future Improvements 
I think I can change my exercise selection and do more low volume training for a longer time. 
