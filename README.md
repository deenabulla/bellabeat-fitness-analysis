# Bellabeat Fitness Tracker — Consumer Behavior Analysis

## Business problem
Bellabeat makes health-focused smart products. To sharpen its marketing strategy, the company needs to understand how consumers actually use smart fitness devices day to day: when they move, how much they sleep, and which usage patterns predict engagement.

## Data source
**FitBit Fitness Tracker Data** (CC0 Public Domain, originally shared via Kaggle by Mobius): 33 consenting Fitbit users, April–May 2016. Files analyzed:
- `dailyActivity_merged.csv` — 940 rows, 33 users (steps, distance, active minutes, calories)
- `sleepDay_merged.csv` — 413 rows, 24 users (minutes asleep, time in bed)
- `hourlySteps_merged.csv` / `hourlyIntensities_merged.csv` — 22,099 hourly records

## Cleaning steps
1. Parsed all date columns to datetime types; dropped duplicate rows (none found).
2. Removed **73 non-wear days** across 15 users — rows with 0 steps plus a (near-)full day of sedentary minutes, i.e. the tracker wasn't worn rather than a true zero-activity day.
3. Built `TotalActiveMinutes` (lightly + fairly + very active minutes) and `SleepEfficiency` (minutes asleep ÷ time in bed).
4. Clean dataset: **867 daily rows, 33 users**; sleep analysis on **410 matched user-days from 24 users**.

## Key findings (from the actual data)
1. **Users are highly sedentary.** Average day: **953.5 sedentary minutes (66.2% of the day)** vs only **246.7 active minutes (17.1%)**. Average daily steps: **8,281** (median 7,990); **46.3% of days fall below 7,500 steps**.
2. **Sleep is healthy but disconnected from daytime activity.** Sleep trackers averaged **419.2 minutes (6.99 hours)** per night at **91.6% sleep efficiency** — yet daily step counts show essentially **no correlation with minutes asleep (r = -0.19)**, and active minutes vs sleep is flat (r = -0.07).
3. **Strong weekly and daily rhythms.** **Tuesday (8,885 avg steps)** and **Saturday (8,868)** are the most active days; **Sunday (7,627)** the least. Activity peaks at **6 PM (~599 steps/hour)** and collapses overnight (~20 steps/hour, 12–4 AM).
4. **A split user base.** By average daily steps: **7 sedentary (<5k)**, **9 lightly active**, **10 fairly active**, **7 very active (10k+)**. Device engagement is high overall — **25 of 33 users** logged 21–31 days of data (avg 26.3 days).
5. **Steps drive calories, moderately.** Daily steps vs calories correlation **r = 0.57** — active days burn more, but the relationship leaves room for intensity/diet factors.

## Recommendations
1. **Sedentary-break coaching as the flagship feature.** With two-thirds of the day sedentary, push smart "stand up and move" nudges timed to each user's personal low-activity hours (visible in the hourly data) rather than generic reminders.
2. **Segment messaging by activity level.** The 7 sedentary users need starter goals (e.g., +1,000 steps/day streaks); the 7 very-active users need advanced challenges. One-size-fits-all goals will bore one group and intimidate the other.
3. **Time engagement to the weekly rhythm.** Launch challenges and notifications for Tuesday/Saturday peaks, and run gentle "Sunday reset" content (sleep/recovery tips — sleep efficiency is already a strength at 91.6%) on the lowest-activity day.

## Limitations
Small sample (33 users), short window (April–May 2016), no demographics, and only 24 of 33 users tracked sleep — findings describe these users, not the whole market.

---
*Portfolio rebuild of the 2024 Google Data Analytics capstone analysis; original coursework files were lost.*
