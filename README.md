# 🎬 YouTube Content Intelligence
### *Decoding the Algorithm — A Data-Driven Blueprint for Virality*

---

## 📌 Project Overview

Every day, YouTube's Trending tab is the most valuable real estate on the internet. For creators and brands, appearing there is the difference between obscurity and global reach. Yet the path to trending is often treated as guesswork.

**This project dismantles that black box.**

Using Python, SQL, and Tableau, I built an end-to-end analytics pipeline on US YouTube Trending data to answer one definitive question:

> *Can we engineer virality using historical patterns and statistical signals?*

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| Python (Pandas, Matplotlib, Seaborn) | Data cleaning, EDA, visualisation |
| SQL (SQLite) | Structural analysis, engagement modelling |
| Tableau | Interactive dashboard & visual storytelling |

---

## 📁 Repository Structure

```
YouTube-Content-Intelligence/
│
├── data/               # Cleaned dataset (US_Trending_Cleaned.csv)
├── notebook/           # Python Jupyter Notebook (YOUTUBE.ipynb)
├── sql/                # SQL queries and analysis document
├── images/             # All chart outputs (chart1.png – chart18.png, tabelu.png)
├── youtube.twb         # Tableau workbook
└── README.md
```

---

---

# 🐍 Phase 1 — Python & Exploratory Data Analysis (EDA)

> **Goal:** Understand the raw shape of the data, clean it, and surface visual patterns in YouTube's trending behaviour.

---

### 🔧 Data Cleaning & Preparation

Before any analysis, the raw dataset required significant preprocessing:

- Removed duplicate entries and null values across key columns (views, likes, comments)
- Parsed and standardised `publish_time` timestamps to a consistent US timezone — critical for accurate time-of-day analysis
- Handled videos with `comments_disabled = True` as a separate control group to avoid skewing engagement metrics
- Encoded `category_id` labels into readable category names for visual clarity

---

### 📊 EDA Findings

#### 1. Views Distribution — Winner Takes All

The distribution of views is heavily right-skewed. The vast majority of trending videos sit in a lower view band, while a tiny fraction achieve extreme reach. This confirms a **power-law dynamic**: a few viral videos absorb most of the platform's traffic.

📈 *Chart:* `images/chart1.png`

---

#### 2. Views vs Likes — Reach and Resonance

There is a strong positive correlation between views and likes. Higher reach generally drives higher engagement. However, the relationship is not perfectly linear — some high-view videos receive disproportionately few likes, pointing to the importance of **content quality and audience alignment**, not just reach.

📈 *Chart:* `images/chart2.png`

---

#### 3. Category Performance — Not All Content Is Equal

Different content categories show distinct performance patterns:

- **Entertainment and Music** dominate total view counts
- Some niche categories achieve **higher engagement rates** (likes + comments per view) despite lower overall reach
- This reveals that **audience behaviour differs by category** — a fitness video and a music video are not competing on the same terms

📈 *Chart:* `images/chart3.png`

---

#### 4. Best Time to Post — The Morning Advantage

Video performance varies significantly by publishing hour. Videos posted between **06:00 – 12:00** consistently outperform those published later in the day.

**Why it matters:** Morning uploads have more time to accumulate views and interactions before the algorithm's daily recommendation cycle runs — giving them a compounding engagement advantage.

📈 *Chart:* `images/chart4.png`

---

#### 5. Top Channels — Concentration of Power

A small number of channels account for a disproportionately large share of total trending views. Established creators benefit from existing audience bases, algorithmic trust, and platform promotion — making it harder (but not impossible) for new creators to break through.

📈 *Chart:* `images/chart5.png`

---

#### 6. Engagement Funnel — The Critical Drop-Off *(Most Important Finding)*

Using an **Animated Engagement Funnel**, I tracked how a video's audience behaves across three stages:

```
Views  →  Likes  →  Comments
  100%       ~8%        ~1.2%
```

The biggest drop-off occurs between **views and likes**. Only a tiny fraction of viewers actively engage. This means:

- Getting views is the easy part
- **Engagement is the gateway to sustained trending status**
- Content that triggers a reaction (emotional, educational, controversial) is fundamentally different from content that is merely watched

📈 *Chart:* `images/chart15.png`

---

### 🧠 Python Phase Summary

| Finding | Insight |
|--------|---------|
| Views are power-law distributed | A few videos dominate; outliers must be handled carefully |
| Views ↔ Likes correlation is strong but imperfect | Quality matters beyond raw reach |
| Morning publishing wins consistently | Timing is a controllable advantage |
| Engagement funnel drops sharply at comments | Active engagement is rare and highly valuable |
| Category behaviour is distinct | Benchmarks must be category-specific |

---

---

# 🗃️ Phase 2 — SQL Structural Analysis

> **Goal:** Move beyond observation into quantifiable models. Use SQL queries to isolate what separates top-performing videos from the rest — and build a measurable virality framework.

The cleaned data was migrated into an **SQLite database** and analysed using Window Functions, CTEs, and custom-engineered metrics.

---

### Query 1 — Do High-Engagement Videos Get More Views?

```sql
SELECT 
  CASE 
    WHEN comments = 0 THEN 0
    WHEN (likes * 1.0 / comments) > 20 THEN 1 
    ELSE 0 
  END AS high_engagement,
  COUNT(*) AS total_videos,
  AVG(views) AS avg_views
FROM us_trending
GROUP BY high_engagement;
```

**Finding:** High-engagement videos generate approximately **3× more views** than low-engagement ones.

**Insight:** Engagement is a *leading indicator* of reach, not just a lagging outcome. Platforms like YouTube actively boost content that shows strong early interaction signals. Prioritising content that drives comments and likes from the first hour is not optional — it is the mechanism by which the algorithm decides whether to push a video further.

---

### Query 2 — Does Publish Time Affect Performance?

```sql
SELECT 
  CASE 
    WHEN CAST(strftime('%H', publish_time) AS INTEGER) BETWEEN 6 AND 12 THEN 'Morning'
    WHEN CAST(strftime('%H', publish_time) AS INTEGER) BETWEEN 13 AND 18 THEN 'Afternoon'
    ELSE 'Night' 
  END AS time_of_day,
  COUNT(*) AS total_videos,
  AVG(views) AS avg_views,
  AVG(likes) AS avg_likes
FROM us_trending
GROUP BY time_of_day;
```

**Finding:** Morning uploads achieve significantly higher average views and likes than afternoon or night uploads.

**Insight:** Early publishing gives content more time to accumulate engagement within the algorithm's daily recommendation cycle. Morning uploads enter the discovery window with maximum runway — a structural advantage that has nothing to do with content quality and everything to do with timing.

---

### Query 3 — Do Longer Titles Perform Better?

```sql
SELECT 
  CASE 
    WHEN LENGTH(title) < 40 THEN 'Short'
    WHEN LENGTH(title) BETWEEN 40 AND 70 THEN 'Medium'
    ELSE 'Long' 
  END AS title_length_category,
  COUNT(*) AS total_videos,
  AVG(views) AS avg_views,
  AVG(likes) AS avg_likes
FROM us_trending
GROUP BY title_length_category;
```

**Finding:** Medium-length titles (40–70 characters) outperform both short and long titles.

**Insight:** This is the Goldilocks Zone for title metadata. Short titles lack enough context to drive clicks; long titles get truncated on mobile screens and lose impact. The 40–70 character window balances SEO discoverability with visual clarity — descriptive enough to communicate value, short enough to display in full.

---

### Query 4 — What Are the Top 3 Videos in Each Category?

```sql
WITH ranked_videos AS (
  SELECT 
    category_id, title, views,
    ROW_NUMBER() OVER (
      PARTITION BY category_id ORDER BY views DESC
    ) AS rank
  FROM us_trending
)
SELECT * FROM ranked_videos WHERE rank <= 3;
```

**Finding:** Entertainment and Music consistently dominate, but niche content does break through across categories.

**Insight:** Viral success is category-dependent but not category-exclusive. Smaller creators can compete by benchmarking against the top performers *within their own category* rather than against platform-wide giants. Category-specific benchmarking is a far more actionable strategy than chasing overall viral benchmarks.

---

### Query 5 — Which Videos Outperform Their Category Average?

```sql
WITH category_avg AS (
  SELECT category_id, AVG(views) AS avg_category_views
  FROM us_trending
  GROUP BY category_id
)
SELECT 
  t.title, t.category_id, t.views,
  c.avg_category_views,
  (t.views - c.avg_category_views) AS performance_gap
FROM us_trending t
JOIN category_avg c ON t.category_id = c.category_id
ORDER BY performance_gap DESC
LIMIT 15;
```

**Finding:** A small number of videos outperform their category average by extreme margins.

**Insight:** Content performance follows a **power-law distribution** — a handful of breakout videos drive the majority of category-level traffic. This means consistency alone is not a path to trend-level success. Creators must experiment for breakout moments, not just optimise for reliable mediocrity.

---

### Query 6 — What Drives Virality? (Composite Virality Score)

```sql
WITH features AS (
  SELECT 
    title, views, likes, comments,
    (likes * 1.0 / views) AS like_rate,
    (comments * 1.0 / views) AS comment_rate,
    LENGTH(title) AS title_length,
    CAST(strftime('%H', publish_time) AS INTEGER) AS publish_hour
  FROM us_trending
),
scored AS (
  SELECT *,
    (like_rate * 0.5 
     + comment_rate * 0.3 
     + CASE WHEN title_length BETWEEN 40 AND 70 THEN 0.1 ELSE 0 END
     + CASE WHEN publish_hour BETWEEN 6 AND 12 THEN 0.1 ELSE 0 END
    ) AS virality_score
  FROM features
)
SELECT title, views, virality_score
FROM scored
ORDER BY virality_score DESC
LIMIT 15;
```

**Finding:** Engagement rate is a stronger predictor of virality than raw view count.

**Insight:** This composite score — weighting like rate, comment rate, title length, and publish time — reveals that niche, fan-driven content frequently outperforms mainstream uploads in virality terms. Platforms optimise for *interaction efficiency*, not just absolute reach. Designing content for engagement rate rather than raw views is a fundamentally different and more sustainable strategy.

---

### Query 7 — Which Videos Overperform Relative Expectations?

```sql
WITH base AS (
  SELECT 
    title, category_id, views,
    (likes * 1.0 / NULLIF(views, 0)) + (comments * 1.0 / NULLIF(views, 0)) AS virality
  FROM us_trending
),
category_avg AS (
  SELECT category_id, AVG(virality) AS avg_cat_virality
  FROM base GROUP BY category_id
)
SELECT 
  b.title, b.category_id,
  (b.virality - c.avg_cat_virality) AS lift
FROM base b
JOIN category_avg c ON b.category_id = c.category_id
ORDER BY lift DESC
LIMIT 20;
```

**Finding:** Top overperformers are consistently emotional, story-driven, or curiosity-based in nature.

**Insight:** Psychology outperforms production quality. Emotional hooks — storytelling arcs, surprising reveals, strong personal narratives — generate the kind of engagement that pushes a video above its category baseline. This is not an accident; it is a repeatable pattern that content strategy can deliberately target.

---

### Query 8 — Detecting Declining Creators

```sql
WITH lagged AS (
  SELECT 
    channel_title, views,
    LAG(views) OVER (
      PARTITION BY channel_title ORDER BY publish_time
    ) AS prev_views
  FROM us_trending
)
SELECT channel_title, views, prev_views, (views - prev_views) AS growth
FROM lagged
WHERE prev_views IS NOT NULL
ORDER BY growth ASC
LIMIT 5;
```

**Finding:** Some channels show a consistent, measurable decline in views across consecutive uploads.

**Insight:** Audience attention decays without content innovation. The algorithm likely reduces recommendation exposure for creators whose videos are showing declining engagement trajectories. This query provides an **early warning system** — identifying creator fatigue before it becomes irreversible.

---

### Query 9 — Early Viral Signal Detection

```sql
WITH base AS (
  SELECT 
    title, category_id, views,
    (likes * 1.0 / views + comments * 1.0 / views) AS engagement
  FROM us_trending
),
category_avg AS (
  SELECT category_id, AVG(engagement) AS avg_engagement
  FROM base GROUP BY category_id
),
scored AS (
  SELECT 
    b.title, b.views,
    (b.engagement / c.avg_engagement) * (1.0 / LOG(b.views + 1)) AS early_viral_score
  FROM base b
  JOIN category_avg c ON b.category_id = c.category_id
)
SELECT * FROM scored
WHERE views < 500000
ORDER BY early_viral_score DESC
LIMIT 10;
```

**Finding:** High relative engagement combined with low absolute views is a reliable early viral signal.

**Insight:** Videos with strong engagement-to-view ratios *before* they scale are likely candidates for algorithmic amplification. This query effectively models how recommendation engines identify breakout content early. Platforms can use patterns like this to decide which low-view videos deserve a wider push — making it a valuable signal for both creators and platform engineers.

---

### Query 10 — Are Top 10% Videos Fundamentally Different?

```sql
WITH ranked AS (
  SELECT views,
    NTILE(10) OVER (ORDER BY views DESC) AS decile
  FROM us_trending
)
SELECT 
  CASE WHEN decile = 1 THEN 'Top 10%' ELSE 'Bottom 90%' END AS group_type,
  AVG(views) AS avg_views
FROM ranked
GROUP BY group_type;
```

**Finding:** The top 10% of videos generate approximately **28× more views** than the bottom 90%.

**Insight:** Platform growth is driven by a tiny number of outsized hits. The long tail of content contributes relatively little to aggregate traffic. This reinforces the case for a **breakout content strategy** — focusing creative and promotional energy on content with genuine viral potential rather than spreading effort uniformly across consistent but average uploads.

---

### Query 11 — Content Funnel Analysis (SQL Validation)

```sql
WITH base AS (
  SELECT 
    views,
    (likes * 1.0 / views + comments * 1.0 / views) AS engagement
  FROM us_trending
),
ranked AS (
  SELECT *, NTILE(10) OVER (ORDER BY views DESC) AS decile FROM base
)
SELECT 
  COUNT(*) AS total_videos,
  SUM(CASE WHEN views > 100000 THEN 1 ELSE 0 END) AS reached_100k,
  SUM(CASE WHEN engagement > 0.05 THEN 1 ELSE 0 END) AS highly_engaged,
  SUM(CASE WHEN decile = 1 THEN 1 ELSE 0 END) AS viral
FROM ranked;
```

**Finding:** The largest drop-off in the content funnel occurs at the engagement stage — far more videos achieve reach than achieve genuine engagement.

**Insight:** Getting views is the easier challenge. Converting those views into meaningful interaction is the bottleneck that separates trending content from ordinary content. Content hooks, storytelling structure, and direct calls to action are the levers that move audiences from passive viewers to active participants.

---

### 🧠 SQL Phase Summary

| Query | Key Finding |
|-------|------------|
| High engagement → more views | Engagement drives reach, not the other way around |
| Morning publishing wins | Timing is a structural, not creative, advantage |
| Medium titles (40–70 chars) dominate | Metadata is a precision tool |
| Power-law performance within categories | Breakout content, not consistency, drives results |
| Virality score model | Engagement rate predicts virality better than view count |
| Emotional content overperforms | Psychology beats production quality |
| Declining creator detection | LAG() functions reveal content fatigue early |
| Early viral signal (low views, high engagement) | Algorithm amplification is predictable |
| Top 10% generate 28× more views | Platform traffic concentrates in breakout hits |
| Funnel analysis confirms engagement bottleneck | Converting views to engagement is the critical challenge |

---

---

# 📊 Phase 3 — Tableau Dashboard

> **Goal:** Translate all Python and SQL findings into a single interactive visual command centre for decision-makers.

The Tableau dashboard (`youtube.twb`) consolidates the key insights into interactive charts covering:

- View and engagement distributions by category
- Publishing time heatmaps showing optimal upload windows
- Top channel performance rankings
- Funnel visualisation showing view → like → comment drop-off rates
- Category benchmarking for performance comparison

📸 *Dashboard preview:* `images/tabelu.png`

---

---

# 🏆 The Three Golden Rules of YouTube Trending

These findings emerged consistently across all three phases of the analysis:

### 1. 🌅 The Morning Window
Videos published between **06:00 – 12:00** achieve approximately **3× the view velocity** of night uploads. Alignment with the start of the US workday gives content maximum runway before the algorithm's recommendation cycle runs.

### 2. 📝 The Title Geometry
Titles in the **40–70 character range** consistently outperform shorter and longer alternatives. This is the precise window where SEO value, click-through clarity, and mobile display align — descriptive enough to rank, concise enough to display in full.

### 3. 💬 The Engagement Catalyst
**Comments are a stronger predictor of sustained trending than likes.** A high likes-to-comments ratio — the "Engagement Signature" — is the single most reliable metric for predicting which videos will remain on the trending list across multiple days.

---

# ⚠️ Challenges Overcome

**The Disabled Comments Problem**
Many videos had comments disabled, threatening to break engagement ratio calculations. SQL logic was used to isolate these as a separate control group, keeping the Engagement Signature metric statistically sound.

**The Celebrity Outlier Effect**
High-profile uploads skewed category averages, making normal performance appear like failure. Decile Analysis (NTILE) normalised the distribution and created actionable benchmarks for all creator tiers.

**Timezone Synchronisation**
Global timestamps required a complex transformation in Python to align all publish times into a consistent US timezone — ensuring the morning publishing effect was a real signal, not a timezone artefact.

---

# 📌 Conclusion

This project demonstrates that while **creativity is an art, reach is a science**.

By combining Python EDA, structured SQL modelling, and Tableau visualisation, a clear and repeatable framework emerges for content strategy:

- Publish in the morning
- Write medium-length, curiosity-driven titles
- Design for comments, not just views
- Benchmark within your category, not against platform-wide averages
- Experiment for breakout moments, not just consistency

---

## 👤 About

**Built by Kushala Chikkappanna Reddy**

End-to-end data pipeline and interactive dashboard analysing YouTube trending video performance using Python, SQL, and Tableau. Key findings include a ~3× engagement impact on views, a strong influence of publishing time, and the superiority of engagement rate over raw views as a virality predictor.
