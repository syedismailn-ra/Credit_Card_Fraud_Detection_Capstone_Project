# Video Script — Credit Card Fraud Detection Project
### Target runtime: ~7:45–8:00 | Pace assumption: ~140 words/minute | Speak naturally, don't rush

---

## [0:00–0:30] Slide 1–2: Title & Agenda

Hi, I'm Syed Ismail N, and in this video I'll walk you through my project on **Credit Card Fraud Detection using Machine Learning** — from the business problem, through the data and modeling approach, to the financial impact and recommendations for the bank.

Here's the agenda: I'll cover the problem statement and goals, walk through the key insights from the data, explain the modeling approach and results, and then spend most of our time on the part that matters most to the business — the **cost-benefit analysis and recommendations**.

*(0:30 elapsed)*

---

## [0:30–1:15] Slide 3–5: Introduction, Problem Statement & Goals

Credit card fraud covers any unauthorized use of a payment card to obtain goods, services, or funds. It's a growing problem for banks — not just because of direct financial loss, but because it threatens customer trust and retention, which is one of the most valuable assets a bank has.

The core problem: manual fraud review is slow, expensive, and inconsistent. Fraudulent transactions have detectable patterns, so machine learning can catch them faster and more reliably than manual processes — reducing chargebacks, false denials of legitimate transactions, and operational cost.

My goals were twofold: first, build a machine learning model that can accurately flag fraudulent transactions from historical transaction data; and second — just as important — quantify the **business impact** of that model through a cost-benefit analysis, so the bank has a clear number to act on.

*(1:15 elapsed)*

---

## [1:15–2:00] Slide 6–7: Data Overview

The dataset is highly imbalanced, which is typical for fraud detection: about 9,650 fraudulent transactions versus roughly 1.84 million legitimate ones — fraud makes up just **0.52%** of all transactions. That imbalance shaped a lot of my modeling decisions later on.

Looking at fraud over time, I found clear seasonal spikes — fraud activity increases around **New Year's Eve and December**, with secondary spikes in **May, August, and October**. That's a useful signal for the bank's monitoring teams to increase vigilance during those windows.

*(2:00 elapsed)*

---

## [2:00–3:15] Slide 8–16: Key Insights

I ran a detailed exploratory analysis across several dimensions to understand *when* and *where* fraud happens. A few of the most actionable patterns:

- **Timing:** fraud counts are highest on **Sundays, Saturdays, and Mondays**, and transactions cluster in **odd overnight hours — between 10 PM and 3 AM**.
- **Customer age:** fraud is more frequent among customers aged **30–60**, though the *highest dollar amounts* per fraud skew toward the **very young and older age bins**.
- **Spending category:** fraud concentrates in **grocery, online shopping, and gas/transport categories** — the categories where genuine high-volume spending also happens, which is exactly why fraudsters target them.
- **Geography:** the **South and Midwest** regions see the highest fraud counts, with the **Northeast** showing slightly higher average fraud amounts.

Taken together, these patterns told me which features would carry the most predictive signal — time of day, day of week, spending category, and recent spending behavior.

*(3:15 elapsed)*

---

## [3:15–4:45] Slide 17–21: Modeling Approach & Results

For modeling, I followed a standard pipeline: clean and merge the data, engineer features from the patterns I just described, encode categorical variables, and drop highly correlated features. Because fraud is only 0.5% of the data, I addressed the class imbalance using **SMOTE and ADASYN** oversampling before training.

I tested three algorithms — **Decision Tree, Random Forest, and XGBoost** — each with default and hyperparameter-tuned versions on both SMOTE and ADASYN data.

**XGBoost was the clear winner.** The hyperparameter-tuned XGBoost model on SMOTE data achieved:
- **99.9% accuracy**
- **89.6% recall**
- **99.8% ROC-AUC**

Recall was the metric I optimized for, not accuracy — because in fraud detection, missing an actual fraud case is far more costly to the business than a false alarm. An 89.6% recall means the model correctly catches nearly 9 out of every 10 fraudulent transactions, which is the highest among all models I tested.

*(4:45 elapsed)*

---

## [4:45–6:45] Slide 22–23: Cost-Benefit Analysis & Business Impact — *the core result*

This is the part I want to spend the most time on, because it translates the model's performance into a number the business actually cares about.

Before deploying any model, the bank's estimated cost from fraud — based on the losses in this dataset — was approximately **$213,392 per month**.

After deploying the XGBoost model, I calculated two components of ongoing cost: the cost of fraud that still slips through undetected, and the operational cost of customer support handling the fraud cases the model *does* catch — around **$608 per month**. Combined, the total monthly cost after deployment drops to approximately **$9,231**.

That's a monthly savings of **$204,161** — a **95.67% reduction** in the cost the bank incurs from fraud. To be clear: this isn't just a modeling exercise — this is the financial argument for why the bank should deploy this system. A model with strong recall directly converts into avoided losses at a scale that easily justifies the cost of building and maintaining it.

*(6:45 elapsed)*

---

## [6:45–7:40] Slide 24: Business Recommendations

Based on what the model learned, I have four concrete recommendations for the bank:

1. **Real-time SMS alerts** when a customer's spending in the last 24 hours significantly exceeds their historical average — this was one of the strongest fraud predictors.
2. **Heightened monitoring on Thursdays, Saturdays, and Mondays**, and during overnight hours between 10 PM and 3 AM, when fraud activity peaks.
3. **Threshold-based alerts** whenever a transaction amount is unusually high relative to a customer's normal spending pattern.
4. **Category-specific monitoring** for grocery, online/in-store shopping, health & fitness, and gas — sending detailed transaction alerts when spend in these categories spikes.

These recommendations are designed to work *alongside* the model — combining automated detection with proactive customer alerts to catch fraud earlier and reduce losses even further.

*(7:40 elapsed)*

---

## [7:40–7:55] Slide 25: Closing

To summarize: fraud is rare but costly, and a well-tuned XGBoost model — optimized for recall — can reduce the bank's fraud-related costs by over 95%, saving roughly **$204,000 a month** in this dataset. Combined with targeted alerting based on timing, amount, and category, this gives the bank both an automated safety net and clear operational guardrails.

Thank you for watching.

*(~7:55 total)*

---

## Notes for recording
- **Pacing:** ~140 wpm is a comfortable, clear speaking pace — don't rush the cost-benefit section (Slide 22–23); it's the section a business audience will care about most.
- **Screen recording:** advance slides at the bracketed timestamps as a guide — they're approximate, not exact cue points.
- **If you're over 8 minutes:** trim the insights section (Slides 9–16) first — summarize 2–3 patterns instead of 4, since the cost-benefit and recommendations sections are the ones to protect.
- **If you're under time:** add 1–2 sentences on *why* recall was prioritized over accuracy/precision in the modeling section — it's a common question from evaluators.
