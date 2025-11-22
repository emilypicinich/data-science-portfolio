⚾ Dodgers 2022 Attendance Analysis

A data-driven exploration of what drives fan turnout at Los Angeles Dodgers home games

📌 Overview

This project analyzes attendance data from all 81 Los Angeles Dodgers home games in the 2022 MLB season to identify the factors that most strongly influence turnout. Using exploratory data analysis, statistical testing, and a full OLS regression model, the study evaluates how day of week, opponent, promotions, weather, and game context shape attendance patterns.

The analysis shows that bobblehead giveaways are by far the most powerful attendance driver, consistently producing near-capacity crowds, while factors like temperature, caps/shirts, and fireworks had little or no measurable effect once other variables were controlled for.

📁 Dataset

The dataset contains:
- 81 rows (one per home game)
- 12 columns, including:
  - attend — attendance (target variable)
  - day_of_week
  - opponent
  - temp
  - skies (Clear/Cloudy)
  - day_night
  - Promotions: cap, shirt, fireworks, bobblehead
- No missing values
- No duplicate rows
- 
🧹 Data Cleaning & Preparation

✓ Validated Missingness
- All columns had 0 nulls.

✓ Encoded Categorical Variables
- Converted YES/NO promotions → 1/0
- Converted day_night → Day=0, Night=1
- Mapped day_of_week → Monday=1 through Sunday=7

✓ Prepared Data for Correlation & Regression
- Created a copy (df_corr and df_reg) to perform:
  - Correlation heatmaps
  - OLS regression with categorical encodings

📊 Exploratory Data Analysis

Attendance Distribution
- The histogram shows a bimodal distribution:
  - A large cluster around 35,000–40,000
  - A second strong peak around 50,000–55,000
- This suggests that certain games consistently reached near-capacity crowds.

Attendance by Day of Week
- The boxplot illustrates:
  - Tuesdays draw the highest crowds (~47,700 average)
  - Saturdays and Sundays also perform strongly
  - Mondays produce the lowest attendance
- A one-way ANOVA confirms the differences are statistically significant (p = 0.003).

Promotions — Fireworks
- The fireworks boxplot shows:
  - Medians for YES/NO are nearly identical
  - Fireworks create more stable attendance but do not increase average turnout
- A t-test shows no significant difference (p = 0.981).

Promotions — Bobbleheads
- The bobblehead boxplot shows a dramatic effect:
  - Bobblehead games almost always drew 50,000–56,000
  - Non-bobblehead games ranged anywhere from 24,000–56,000
- A t-test shows a massively significant difference (p ≈ 3e-13).

Temperature Effects
- The scatterplot shows no clear relationship.
- Attendance stayed high regardless of whether the temperature was 55°F or 95°F.
- Temperature had a correlation of only 0.10.

Correlation Heatmap
- Bobblehead → r = 0.58 (strongest correlation)
- Fireworks, caps, shirts → near zero
- Day of week (numeric) → slight positive effect
- Day/night, temperature → near zero

dodgers_attendance
- Average attendance by opponent:
  - Highest: Angels, Mets, Nationals (~49–50k)
  - Lowest: Braves, Brewers, Astros (~32–36k)
- A full boxplot shows big variation by opponent, with some teams producing highly consistent sellouts and others drawing weak crowds.

📈 Regression Modeling (OLS)
The full OLS regression includes:
- Dependent variable: attend
- Predictors:
  - Temperature
  - All promotions
  - Day/night
  - Day of week (categorical)
  - Opponent (categorical)
  - Skies (Clear/Cloudy)
  - Model Fit
- R² = 0.689
- Adjusted R² = 0.511
- This means ~69% of attendance variation is explained by the included factors.

Significant Predictors
- Bobblehead: +11,700 fans (p < 0.001)
- Fireworks: +1,900 fans (p = 0.019)
- Day of Week: Tuesday, Saturday, Sunday significant
- Certain Opponents: Braves, Brewers, Diamondbacks strongly negative

Non-Significant Predictors
- Caps
- Shirts
- Temperature
- Day/night
- Skies (Clear/Cloudy)

This supports the EDA findings that promotions and game context matter far more than weather-related factors.

🧠 Key Insights
- Bobblehead giveaways are the strongest driver of attendance, consistently producing near-sellout games.
- Fireworks do not raise average attendance, though they stabilize turnout.
- Caps and shirts do not meaningfully influence attendance.
- Day of the week matters — Tuesdays and weekends are strongest; Mondays weakest.
- Opponent matters — Angels, Mets, Nationals produce strong crowds; Brewers, Braves, Diamondbacks do not.
- Weather factors are negligible — neither temperature nor skies significantly predict attendance.

💼 Recommendations
- Increase bobblehead nights, and strategically schedule them on weak-demand days (Mondays, low-interest opponents).
- Use fireworks as a secondary promotional tool for midweek games.
- Allocate premium pricing to high-demand opponents (Angels, Mets).
- Use discounts, group deals, and marketing pushes for weak opponents (Brewers, Braves, Diamondbacks).
- De-prioritize cap/shirt giveaways, as they do not shift attendance.

🚀 Future Extensions
- Build a predictive attendance model (Random Forest / Gradient Boosting).
- Include ticket pricing, giveaway quantities, and special event nights if data becomes available.
- Build a dashboard for stadium management showing high- and low-demand games.
- Combine this with multi-year data to model trend patterns.
