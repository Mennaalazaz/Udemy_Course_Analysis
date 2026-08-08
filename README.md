#  Udemy Finance & Accounting Courses — Business Intelligence Analysis

A data analytics project examining **13,608 Finance & Accounting courses** on Udemy to uncover what drives course popularity, pricing performance, and learner satisfaction — and to turn those findings into concrete business recommendations.

---

## 🎯 Overview

This project analyzes course-level data from Udemy's Finance & Accounting catalog to answer a core business question:

> **What factors influence the popularity and financial success of Finance & Accounting courses on Udemy — and how should pricing and content strategy respond?**

The analysis covers data cleaning, exploratory data analysis (EDA), BI dashboarding, and a stakeholder-facing report with prioritized recommendations.

---

## 🗂️ Dataset

| | |
|---|---|
| **Source** | Udemy (Finance & Accounting course catalog) |
| **Rows** | 13,608 courses |
| **Columns** | 20 variables |
| **Types** | Numerical, categorical, text, datetime |

**Key fields:** `num_subscribers`, `avg_rating`, `avg_rating_recent`, `num_reviews`, `num_published_lectures`, `num_published_practice_tests`, `discount_price__amount`, `price_detail__amount`, `created`, `published_time`, and more.

📄 See [`udemy_data_description.pdf`](./udemy_data_description.pdf) for the full variable dictionary.

---

## 🧹 Data Preparation

- **Missing values (~5%)** in discount-price fields were confirmed to reflect free/non-discounted courses (not data errors) and were retained without imputation.
- **Redundant columns** (text-formatted price strings, constant currency field) were excluded from quantitative analysis.
- **No duplicate records** were found.
- **Derived fields**: `created_year`, `created_month`, `published_year`, `published_month`, and a course **category hierarchy**.
- **Custom measures**:
  - `Estimated_Revenue` = `num_subscribers × COALESCE(discount_price, price_detail)`
  - `percentage_discount` = `(price_detail − discount_price) / price_detail`
  - Supporting totals for total courses, total revenue, and total paid courses.

---

## 📈 Key Insights

- **Portfolio scale:** 13,608 courses, 96.4% paid, average rating **3.92/5**, total revenue **₹2.37bn** (+18.6% vs. target).
- **Category mismatch:** *Business* leads in course volume, but **Big Data** and **Automation** drive disproportionately higher revenue and subscribers per course.
- **Discounting:** Subscriber acquisition is flat across moderate discounts (40–70%) and spikes only at extreme discounts (95–100%).
- **Pricing:** Revenue and enrollment both spike sharply near the **₹10K** price point — a premium sweet spot.
- **Course design:** Enrollment favors shorter courses (<200 lectures); practice test count has little effect on ratings.
- **Quality risk:** A small number of critically low-rated courses were flagged for content review or removal.
- **Seasonality:** Subscriber acquisition peaks consistently in **October**.

Full narrative and supporting dashboards are in [`Udemy_Business_Report.pdf`](./Udemy_Business_Report.pdf).

---

## 💡 Recommendations

| Priority | Recommendation |
|---|---|
| 🔴 High | Prioritize instructor acquisition & marketing in Big Data, Automation, and Data Analytics |
| 🔴 High | Establish a quarterly quality-review process for critically low-rated courses |
| 🟠 Medium | Re-evaluate blanket steep discounting; test long-term subscriber impact |
| 🟠 Medium | Replicate the pricing/content profile of high-performing ~₹10K courses |
| 🟠 Medium | Guide instructors toward concise, tightly scoped courses |
| ⚪ Low | Time major launches and campaigns around September–October |
| ⚪ Low | Maintain current pricing strategy; monitor post-2015 per-course revenue trend |

---

## 🛠️ Tech Stack

- **Data cleaning & modeling:** Power BI / Power Query, DAX
- **Dashboards:** Power BI

---
