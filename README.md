# 📊 Customer Journey Performance Analysis (SQL | BigQuery)

## 🔍 Overview  
This project performs a **funnel analysis** to analyse end-to-end customer journeys using event-level user interaction data to identify where users drop off in a typical e-commerce journey between `page_view` and `purchase`.

The aim is to understand **how customers move through the journey**, which steps lose the most users and how performance differs by **country and device**. It leverages **advanced SQL techniques** to analyse how users from the top 3 countries, 🇺🇸 United States, 🇮🇳 India and 🇨🇦 Canada, behave across various funnel stages.

---

## 🎯 Objectives

- Clean and deduplicate raw event data (1 event per user per funnel step)
- Focus on key funnel events that represent meaningful journey stages
- Measure drop-offs and conversion at each step
- Compare performance across top countries and devices
- Produce clear outputs that support performance decisions

---

## 🛠️ Tech Stack

- **Language:** SQL (Google BigQuery syntax)
- **Data Source:** Funnel_analysis_raw events
- **Visualisation:** Python (Matplotlib)
- **Techniques Used:**
  - Common Table Expressions (CTEs)
  - Window functions (`ROW_NUMBER()`, `RANK()`)
  - Deduplication and filtering
  - Country & event-level grouping
  - Funnel and conversion calculations
  - Ranking by engagement

---

## 🗂️ Funnel Events Considered

1. `page_view`
2. `view_item`
3. `add_to_cart`
4. `add_shipping_info`
5. `add_payment_info`
6. `purchase`

These events represent typical customer journey in an e-commerce platform.

---

## 🔄 Step-by-Step Process

| Step | Description |
|------|-------------|
| **1. Deduplicate Events** | Used `ROW_NUMBER()` to keep the first occurrence of each event per user |
| **2. Filter Events & Countries** | Focus only on the top 3 active countries and relevant funnel events |
| **3. Group & Rank Events** | Count how often each event occurs, globally and per country |
| **4. Build Final Funnel Table** | Join country-wise breakdowns to get a comparative analysis of each funnel step |
| **5. Visualise Results** | Created charts to clearly show drop-offs and differences |

---

## 📈 Outputs & How Conclusions Were Reached

## 📈 Sample Output

| Category | Event Name       | 🇺🇸 US Events | 🇮🇳 India Events | 🇨🇦 Canada Events |
|----------|------------------|--------------|------------------|-------------------|
| Shopping | page_view        | 45,312       | 39,142           | 12,430            |
| Shopping | view_item        | 30,102       | 22,510           | 7,120             |
| Shopping | add_to_cart      | 18,545       | 12,843           | 4,870             |
| Shopping | add_payment_info | 10,012       | 5,205            | 1,911             |
| Shopping | purchase         | 7,145        | 2,103            | 905               |

✅ *Shows clear drop-off trend and allows business to take region-specific action.*

### 1️⃣ Overall Conversion by Funnel Stage
This chart shows how users progress through each step of the funnel, expressed as a proportion of `page_view` users.

![Overall Conversion by Stage](overall_conversion_by_stage.png)

**How this was calculated:**
- Counted unique users at each funnel stage
- Divided each stage by total `page_view` users

**What this shows:**
- The biggest drop occurs between `view_item` and `add_to_cart`
- Conversion continues to decline through checkout stages
- Later-stage friction has a large impact on final outcomes

---

### 2️⃣ Purchase Conversion by Device
This chart compares purchase conversion across device types.

![Conversion Rate by Device](conversion_rate_by_device.png)

**How this was calculated:**
- Purchase users ÷ page_view users for each device

**What this shows:**
- Mobile has the highest conversion
- Desktop performs slightly lower
- Tablet shows the weakest performance, indicating potential usability issues

---

## 🔍 Key Insights

- - **United States** had the highest engagement at every stage of the funnel.
- **India** showed major drop-offs post `add_to_cart`, hinting at friction during checkout.
- **Canada** had the lowest absolute engagement, but a more consistent funnel progression.
- Strong early engagement does not translate into completed purchases
- Checkout stages contribute most to overall drop-off
- Device type has a measurable impact on conversion
- Improving later funnel stages would deliver the biggest performance gains

---

## 💡 Business / Service Impact

This analysis helps teams:
- Identify where users struggle in a digital journey
- Prioritise improvements based on evidence
- Monitor whether changes improve outcomes
- Support data-driven discussions with product and service teams

---

## 🧠 What I Learned

- How to clean and structure real-world event data for analysis
- Practical use of window functions like `ROW_NUMBER()` and `RANK()` in SQL
- Funnel analysis logic from scratch
- How to derive **actionable insights** from data, not just numbers

---

## 🚀 Future Improvements

- Add time-to-conversion analysis
- Segment funnels by new vs returning users
- Build a Power BI dashboard for ongoing monitoring
- Compare performance before and after service changes
- - Run A/B test comparisons between countries or time periods

---

## 🧠 What This Project Demonstrates

- Strong SQL fundamentals for performance analysis.
- Ability to translate raw data into clear insights.
- Understanding of customer journeys and outcomes.
- Clear communication of results using simple visuals.

---

## Why This Matters  

Understanding how users move through digital services and where they struggle. It is critical for improving efficiency, reducing avoidable contact and supporting scalable digital transformation.

This project demonstrates a **structured, evidence-led approach** to learning from customer journeys using a single, consistent dataset.
