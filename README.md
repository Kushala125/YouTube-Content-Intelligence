<div align="center">

<br/>

<h1>
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=30&pause=1000&color=FF0000&center=true&vCenter=true&width=700&lines=🎬+YouTube+Content+Intelligence;Decoding+the+Algorithm;Engineering+Virality+with+Data" alt="Typing SVG" />
</h1>

<br/>

<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart1.png" width="30%" style="border-radius:8px"/>
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart3.png" width="30%" style="border-radius:8px"/>
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart15.png" width="30%" style="border-radius:8px"/>

<br/><br/>

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org)
[![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)](https://sqlite.org)
[![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white)](https://tableau.com)
[![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org)

<br/>

[![Stars](https://img.shields.io/github/stars/Kushala125/YouTube-Content-Intelligence?style=social)](https://github.com/Kushala125/YouTube-Content-Intelligence)
[![Forks](https://img.shields.io/github/forks/Kushala125/YouTube-Content-Intelligence?style=social)](https://github.com/Kushala125/YouTube-Content-Intelligence)

<br/>

> ### *"While creativity is an art — reach is a science."*
>
> This project dismantles YouTube's Trending algorithm black box and rebuilds it as a **transparent, repeatable, data-proven blueprint for virality**.

<br/>

</div>

---

<div align="center">

## ⚡ Three Key Discoveries at a Glance

</div>

<br/>

<div align="center">

|  🌅 Morning Uploads  |  📝 Title Length  |  💬 Comments Win  |
|:-------------------:|:-----------------:|:------------------:|
| **3× more views** than night uploads | **40–70 chars** is the Goldilocks Zone | Active engagement predicts trending far better than likes |

</div>

---

## 📌 The Mission

Every day, YouTube's Trending tab is the internet's most valuable real estate. For a creator or brand, appearing there changes everything — yet the path is widely treated as mysterious, random, or luck-driven.

**This project proves it is none of those things. It is a system.**

Using an end-to-end analytics pipeline across **Python EDA → SQL structural analysis → Tableau dashboarding**, I investigated US YouTube Trending data to answer one definitive question:

> *Can we engineer virality using historical patterns and statistical signals?*

**The answer — validated across three rigorous phases — is yes.**

---

## 🗂️ Repository Structure

```
📦 YouTube-Content-Intelligence
 ┃
 ┣ 📁 data/          →  US_Trending_Cleaned.csv
 ┣ 📁 notebook/      →  YOUTUBE.ipynb  (full Python EDA)
 ┣ 📁 sql/           →  SQL queries & business analysis document
 ┣ 📁 images/        →  chart1.png – chart18.png  +  tabelu.png
 ┣ 📊 youtube.twb    →  Tableau workbook
 ┗ 📄 README.md
```

---

## 🔬 Three-Phase Investigation

```
Phase 1 ──────────────────────────────────────────────── Phase 2 ──────────────────── Phase 3
   🐍                                                       🗃️                            📊
Python EDA                                              SQL Analysis                  Tableau
   │                                                        │                            │
Clean data                                            Migrate to DB               Visual dashboard
Visualise patterns                                    Write 11 queries            Interactive filters
Build funnel                                          Engineer virality score     Command centre
```

---

<br/>
<br/>

---

<div align="center">

# 🐍 PHASE 1 — Python & Exploratory Data Analysis

<img src="https://img.shields.io/badge/Tool-Python%20%7C%20Pandas%20%7C%20Matplotlib%20%7C%20Seaborn-3776AB?style=for-the-badge&logo=python&logoColor=white"/>

</div>

<br/>

> **Objective:** Scrub the raw data clean, then visualise the statistical patterns buried inside YouTube's trending behaviour — six findings that change how you think about the platform.

---

### 🔧 Data Cleaning Pipeline

| Step | What Was Done | Why It Mattered |
|------|--------------|-----------------|
| **Deduplication** | Removed repeated video entries (videos trend for multiple days) | Prevented double-counting from skewing averages |
| **Null handling** | Excluded incomplete records across views, likes, comments | Ensured statistical integrity across all metrics |
| **Timezone normalisation** | Converted all `publish_time` to US Eastern via `pytz` | Made time-of-day analysis accurate — not timezone-distorted |
| **Disabled comments flag** | Tagged `comments_disabled=True` as a control group | Prevented engagement model distortion without losing the data |
| **Category decoding** | Mapped `category_id` integers to readable labels | Enabled meaningful category-level comparison |

---

### 📊 EDA Chart 1 — Views Distribution: Winner Takes All

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart1.png" width="88%" alt="Views Distribution"/>
  <br/>
  <sub><b>Fig 1 · Views Distribution</b> — Heavy right skew confirms power-law dynamics. A tiny fraction of videos absorb most of the platform's traffic.</sub>
</div>

<br/>

**What the chart shows:** The distribution of views across trending videos is dramatically right-skewed. Most videos occupy a modest view band, while a tiny fraction achieve explosive reach.

**Why it matters:** This is a **power-law dynamic** — a few viral hits absorb most platform traffic. Average-based benchmarking is misleading when the data is this skewed. Any performance analysis must account for this before drawing conclusions.

---

### 📊 EDA Chart 2 — Views vs Likes: Reach vs Resonance

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart2.png" width="88%" alt="Views vs Likes"/>
  <br/>
  <sub><b>Fig 2 · Views vs Likes</b> — Strong positive correlation, but notable divergence reveals the gap between algorithmic reach and genuine audience resonance.</sub>
</div>

<br/>

**What the chart shows:** A strong positive correlation between views and likes — but it's not linear. Several high-view videos receive disproportionately few likes, and some moderate-view videos punch far above their weight in engagement.

**Why it matters:** The gap reveals the difference between **viral distribution** (algorithmic reach) and **genuine resonance** (content quality). A video can be seen by millions and still fail to move them.

---

### 📊 EDA Chart 3 — Category Performance: Audience Behaviour by Content Type

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart3.png" width="88%" alt="Category Performance"/>
  <br/>
  <sub><b>Fig 3 · Category Performance</b> — Entertainment and Music dominate views; niche categories often outperform on engagement rate despite lower reach.</sub>
</div>

<br/>

**What the chart shows:** Different categories exhibit fundamentally different performance patterns. Entertainment and Music dominate raw views; How-to, Education, and Gaming categories achieve higher engagement rates per view.

**Why it matters:** **A fitness video and a pop music video are not competing on the same terms.** Cross-category benchmarking produces false conclusions. Every creator must benchmark within their own category.

---

### 📊 EDA Chart 4 — Best Time to Post: The Morning Advantage

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart4.png" width="88%" alt="Best Time to Post"/>
  <br/>
  <sub><b>Fig 4 · Publishing Time vs Performance</b> — Videos published between 06:00–12:00 consistently achieve ~3× the view velocity of night uploads.</sub>
</div>

<br/>

**What the chart shows:** Videos uploaded between **06:00 and 12:00** consistently outperform those published in the afternoon or at night across views, likes, and engagement metrics.

**Why it matters:** Morning uploads have more time to accumulate interactions before the algorithm's daily recommendation cycle runs — creating compounding engagement momentum that self-reinforces through the day. This is a **free, structural advantage** that requires only a scheduling decision.

---

### 📊 EDA Chart 5 — Top Channels: The Concentration of Influence

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart5.png" width="88%" alt="Top Channels"/>
  <br/>
  <sub><b>Fig 5 · Top Channels by Total Views</b> — A small number of channels dominate overall reach, but niche breakouts still appear throughout the data.</sub>
</div>

<br/>

**What the chart shows:** A small number of channels account for a disproportionately large share of total trending views. Established creators benefit from existing audiences, algorithmic trust, and platform promotion.

**Why it matters:** The data also reveals **niche breakouts** — smaller channels that reach trending through high engagement efficiency rather than raw audience size. This is the opening that the data-driven creator can exploit.

---

### 📊 EDA Chart 6 — The Engagement Funnel ⭐ *Most Important Finding*

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart15.png" width="88%" alt="Engagement Funnel"/>
  <br/>
  <sub><b>Fig 6 · Engagement Funnel</b> — The conversion from views to comments is the critical bottleneck that separates trending content from everything else.</sub>
</div>

<br/>

**What the chart shows:** Using an Animated Engagement Funnel, I tracked how a video's audience behaves across three interaction stages over a 24-hour trending cycle:

```
 VIEWS     ████████████████████████████████████████  100.0%
 LIKES     ████░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░    ~8.0%
 COMMENTS  ▌░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░    ~1.2%
```

**Why it matters:** Most audiences are passive — they watch but don't interact. Getting views is relatively easy through algorithmic distribution. **Converting views into genuine engagement is the real differentiator.** Content that triggers a reaction sits in a fundamentally different performance tier.

---

<br/>

---

<div align="center">

# 🗃️ PHASE 2 — SQL Structural Analysis

<img src="https://img.shields.io/badge/Tool-SQLite%20%7C%20Window%20Functions%20%7C%20CTEs%20%7C%20Composite%20Metrics-003B57?style=for-the-badge&logo=sqlite&logoColor=white"/>

</div>

<br/>

> **Objective:** Move beyond observation into quantifiable models. Eleven SQL queries — using Window Functions, CTEs, NTILE, LAG, and custom-engineered metrics — to isolate the structural patterns underlying virality.

---

### 🔍 SQL Query 1 — Do High-Engagement Videos Get More Views?

```sql
SELECT
  CASE
    WHEN comments = 0 THEN 'No Comments'
    WHEN (likes * 1.0 / comments) > 20 THEN 'High Engagement'
    ELSE 'Low Engagement'
  END AS engagement_tier,
  COUNT(*) AS total_videos,
  AVG(views)  AS avg_views
FROM us_trending
GROUP BY engagement_tier;
```

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart6.png" width="88%" alt="High Engagement vs Views"/>
  <br/>
  <sub><b>SQL Fig 1 · Engagement Tier vs Average Views</b> — High-engagement videos generate approximately 3× more views than low-engagement ones.</sub>
</div>

<br/>

> **📊 Finding:** High-engagement videos generate **~3× more views** than low-engagement ones.

> **💡 Insight:** Engagement is a *leading indicator* of reach — not a lagging reward. YouTube's algorithm actively amplifies content showing strong early interaction signals. More comments → algorithm boost → more views. Not the reverse.

> **✅ Action:** Prioritise hooks, storytelling, and calls-to-action that drive comments and likes in the **first hour** after publishing.

---

### 🔍 SQL Query 2 — Does Publish Time Affect Performance?

```sql
SELECT
  CASE
    WHEN CAST(strftime('%H', publish_time) AS INTEGER) BETWEEN 6 AND 12
      THEN 'Morning (6AM–12PM)'
    WHEN CAST(strftime('%H', publish_time) AS INTEGER) BETWEEN 13 AND 18
      THEN 'Afternoon (1PM–6PM)'
    ELSE 'Night (7PM–5AM)'
  END AS time_of_day,
  COUNT(*) AS total_videos,
  AVG(views)  AS avg_views,
  AVG(likes)  AS avg_likes
FROM us_trending
GROUP BY time_of_day;
```

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart7.png" width="88%" alt="Publish Time Performance"/>
  <br/>
  <sub><b>SQL Fig 2 · Publish Time vs Average Views & Likes</b> — Morning uploads consistently outperform across every engagement metric.</sub>
</div>

<br/>

> **📊 Finding:** Morning uploads achieve significantly higher average views and likes than any other publishing window.

> **💡 Insight:** Early publishing creates maximum runway within the algorithm's daily recommendation cycle. Morning content enters the discovery window with the most time to accumulate interactions before curation runs.

> **✅ Action:** Schedule uploads consistently in the **06:00–10:00 window** for maximum algorithmic exposure.

---

### 🔍 SQL Query 3 — Do Longer Titles Perform Better?

```sql
SELECT
  CASE
    WHEN LENGTH(title) < 40              THEN 'Short  (<40 chars)'
    WHEN LENGTH(title) BETWEEN 40 AND 70 THEN 'Medium (40–70 chars)'
    ELSE                                     'Long   (>70 chars)'
  END AS title_length_category,
  COUNT(*) AS total_videos,
  AVG(views)  AS avg_views,
  AVG(likes)  AS avg_likes
FROM us_trending
GROUP BY title_length_category;
```

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart8.png" width="88%" alt="Title Length Performance"/>
  <br/>
  <sub><b>SQL Fig 3 · Title Length vs Average Views</b> — Medium-length titles (40–70 chars) are the clear winner across all categories.</sub>
</div>

<br/>

> **📊 Finding:** Medium-length titles (40–70 characters) consistently outperform both short and long alternatives.

> **💡 Insight:** The **Goldilocks Zone**. Short titles lack the context to drive clicks. Long titles get truncated on mobile — the dominant platform. 40–70 characters balances SEO, mobile display, and cognitive clarity simultaneously.

> **✅ Action:** Treat title engineering as a precision decision. Balance curiosity + clarity + keyword within **40–70 characters**.

---

### 🔍 SQL Query 4 — Top 3 Videos Per Category (ROW_NUMBER Window Function)

```sql
WITH ranked_videos AS (
  SELECT
    category_id, title, views,
    ROW_NUMBER() OVER (
      PARTITION BY category_id
      ORDER BY views DESC
    ) AS rank
  FROM us_trending
)
SELECT * FROM ranked_videos WHERE rank <= 3;
```

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart9.png" width="88%" alt="Top Videos Per Category"/>
  <br/>
  <sub><b>SQL Fig 4 · Top 3 Videos Per Category</b> — Entertainment and Music lead, but niche categories consistently produce breakout content.</sub>
</div>

<br/>

> **📊 Finding:** Entertainment and Music dominate top positions, but niche content regularly breaks through in Gaming, How-to, and Science.

> **💡 Insight:** Viral success is category-dependent but not category-exclusive. Smaller creators compete by benchmarking within their own category — not against platform-wide giants with structurally different advantages.

> **✅ Action:** Study the structural patterns (hook type, length, title format) of the **top 3 in your specific category** — not the platform's overall top 10.

---

### 🔍 SQL Query 5 — Which Videos Outperform Their Category? (CTE + JOIN)

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

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart10.png" width="88%" alt="Category Outperformers"/>
  <br/>
  <sub><b>SQL Fig 5 · Performance Gap vs Category Average</b> — A small number of videos outperform their category average by enormous margins.</sub>
</div>

<br/>

> **📊 Finding:** A small number of videos outperform their category average by extreme margins — the performance gap distribution is itself power-law shaped.

> **💡 Insight:** Content performance follows a **power-law distribution within every category**. A few breakout hits drive most traffic. Consistency alone cannot compete with a single well-timed viral moment.

> **✅ Action:** Run deliberate creative experiments for **breakout content** — don't only optimise for reliable average performance.

---

### 🔍 SQL Query 6 — Composite Virality Score ⭐ *Core Innovation*

```sql
WITH features AS (
  SELECT title, views, likes, comments,
    (likes    * 1.0 / views) AS like_rate,
    (comments * 1.0 / views) AS comment_rate,
    LENGTH(title)             AS title_length,
    CAST(strftime('%H', publish_time) AS INTEGER) AS publish_hour
  FROM us_trending
),
scored AS (
  SELECT *,
    (  like_rate    * 0.5
     + comment_rate * 0.3
     + CASE WHEN title_length BETWEEN 40 AND 70 THEN 0.1 ELSE 0 END
     + CASE WHEN publish_hour BETWEEN 6  AND 12  THEN 0.1 ELSE 0 END
    ) AS virality_score
  FROM features
)
SELECT title, views, virality_score
FROM scored ORDER BY virality_score DESC LIMIT 15;
```

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart11.png" width="88%" alt="Virality Score Model"/>
  <br/>
  <sub><b>SQL Fig 6 · Composite Virality Score Rankings</b> — Multi-signal score outperforms raw view count as a virality predictor.</sub>
</div>

<br/>

This query engineers a **custom Virality Score** weighting four independently validated signals:

| Signal | Weight | Rationale |
|--------|:------:|-----------|
| Like Rate | **50%** | Primary passive engagement signal |
| Comment Rate | **30%** | Active engagement — strongest algorithmic signal |
| Title Length (40–70 chars) | **10%** | Metadata optimisation bonus |
| Morning Publish (6AM–12PM) | **10%** | Timing advantage bonus |

> **📊 Finding:** Engagement rate predicts virality more reliably than raw view count. High-scoring videos frequently have moderate views but exceptional audience interaction.

> **💡 Insight:** Platforms optimise for *interaction efficiency*, not reach alone. Niche fan-driven content regularly outperforms mainstream content on this metric.

> **✅ Action:** Design content for **engagement rate** — not view maximisation. A video seen by 500K who comment is worth more algorithmically than one seen by 2M who scroll past.

---

### 🔍 SQL Query 7 — Psychological Overperformers: What Lifts Above Expectations?

```sql
WITH base AS (
  SELECT title, category_id, views,
    (likes * 1.0 / NULLIF(views,0))
    + (comments * 1.0 / NULLIF(views,0)) AS virality
  FROM us_trending
),
category_avg AS (
  SELECT category_id, AVG(virality) AS avg_cat_virality
  FROM base GROUP BY category_id
)
SELECT b.title, b.category_id,
  (b.virality - c.avg_cat_virality) AS lift
FROM base b
JOIN category_avg c ON b.category_id = c.category_id
ORDER BY lift DESC LIMIT 20;
```

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart12.png" width="88%" alt="Psychological Overperformers"/>
  <br/>
  <sub><b>SQL Fig 7 · Engagement Lift Above Category Average</b> — Emotional, story-driven, and curiosity-based content consistently overperforms.</sub>
</div>

<br/>

> **📊 Finding:** The highest-lift overperformers share three consistent characteristics — they are **emotional**, **story-driven**, or **curiosity-based** in their primary hook.

> **💡 Insight:** Psychology consistently outperforms production quality. Emotional hooks — personal narratives, surprising reveals, strong stakes — generate the kind of engagement that lifts a video above its category baseline. This is a repeatable pattern.

> **✅ Action:** Integrate emotional triggers and storytelling arcs at the **scripting stage** — not as an afterthought in the edit.

---

### 🔍 SQL Query 8 — Detecting Declining Creators (LAG Window Function)

```sql
WITH lagged AS (
  SELECT channel_title, views,
    LAG(views) OVER (
      PARTITION BY channel_title
      ORDER BY publish_time
    ) AS prev_views
  FROM us_trending
)
SELECT channel_title, views, prev_views,
  (views - prev_views) AS growth
FROM lagged
WHERE prev_views IS NOT NULL
ORDER BY growth ASC LIMIT 5;
```

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart13.png" width="88%" alt="Declining Creators"/>
  <br/>
  <sub><b>SQL Fig 8 · Creator View Growth via LAG Function</b> — Some channels show consistent, measurable decline — a clear early warning signal of content fatigue.</sub>
</div>

<br/>

> **📊 Finding:** Several channels show consistent, measurable view decline across consecutive uploads — a clear early signal of content fatigue or audience disengagement.

> **💡 Insight:** Audience attention decays without content innovation. The algorithm likely progressively reduces recommendation exposure for declining channels — creating a compounding negative feedback loop.

> **✅ Action:** Monitor your channel's LAG growth metric. Two consecutive declines = **trigger to refresh strategy**, not publish more of the same.

---

### 🔍 SQL Query 9 — Early Viral Signal Detection

```sql
WITH base AS (
  SELECT title, category_id, views,
    (likes * 1.0 / views + comments * 1.0 / views) AS engagement
  FROM us_trending
),
category_avg AS (
  SELECT category_id, AVG(engagement) AS avg_engagement
  FROM base GROUP BY category_id
),
scored AS (
  SELECT b.title, b.views,
    (b.engagement / c.avg_engagement)
    * (1.0 / LOG(b.views + 1)) AS early_viral_score
  FROM base b
  JOIN category_avg c ON b.category_id = c.category_id
)
SELECT * FROM scored
WHERE views < 500000
ORDER BY early_viral_score DESC LIMIT 10;
```

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart14%20.png" width="88%" alt="Early Viral Signal"/>
  <br/>
  <sub><b>SQL Fig 9 · Early Viral Score — Low Views + High Engagement</b> — Pre-scale viral candidates identified by relative engagement efficiency.</sub>
</div>

<br/>

> **📊 Finding:** High relative engagement combined with low absolute view count is a consistent and reliable early viral signal.

> **💡 Insight:** This query models how recommendation engines identify viral content *before it scales*. A video at 50K views with 10× its category engagement ratio is almost certainly being tested for a broader push.

> **✅ Action:** Maximise engagement in the **first 2 hours**. For platform analysts — this metric can power a live viral candidate detection dashboard.

---

### 🔍 SQL Query 10 — Are Top 10% Videos Fundamentally Different? (NTILE)

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

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart16.png" width="88%" alt="Top 10% vs Rest"/>
  <br/>
  <sub><b>SQL Fig 10 · Top 10% vs Bottom 90% Average Views</b> — The top decile generates approximately 28× more views than the remaining 90%.</sub>
</div>

<br/>

> **📊 Finding:** The top 10% of trending videos generate approximately **28× more views** than the bottom 90%.

> **💡 Insight:** Platform traffic is overwhelmingly concentrated in a tiny percentage of breakout hits. Long-tail content contributes relatively little. The platform's growth depends on viral moments — not a healthy distribution of consistent performers.

> **✅ Action:** Allocate creative resources **asymmetrically** — invest more in content with genuine breakout potential rather than spreading effort across high-volume average output.

---

### 🔍 SQL Query 11 — Full Content Funnel Validation

```sql
WITH base AS (
  SELECT views,
    (likes * 1.0 / views + comments * 1.0 / views) AS engagement
  FROM us_trending
),
ranked AS (
  SELECT *, NTILE(10) OVER (ORDER BY views DESC) AS decile FROM base
)
SELECT
  COUNT(*) AS total_videos,
  SUM(CASE WHEN views > 100000    THEN 1 ELSE 0 END) AS reached_100k,
  SUM(CASE WHEN engagement > 0.05 THEN 1 ELSE 0 END) AS highly_engaged,
  SUM(CASE WHEN decile = 1        THEN 1 ELSE 0 END) AS viral_tier
FROM ranked;
```

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart17.png" width="88%" alt="Content Funnel SQL"/>
  <br/>
  <sub><b>SQL Fig 11 · Content Funnel Validation</b> — The engagement conversion threshold is the biggest drop-off point in the entire funnel.</sub>
</div>

<br/>

> **📊 Finding:** The largest proportional drop-off occurs at the **engagement threshold** — far more videos achieve 100K views than achieve meaningful audience interaction rates.

> **💡 Insight:** Reach is not the bottleneck — engagement conversion is. The algorithm uses engagement signals to decide which high-reach videos get promoted to viral scale.

> **✅ Action:** Optimise for interaction prompts, not just distribution. Every video needs a hook that makes engagement feel **effortless and natural** for the audience.

---

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart18.png" width="88%" alt="SQL Summary Chart"/>
  <br/>
  <sub><b>SQL Fig 12 · Consolidated SQL Analysis Summary</b> — All structural findings unified into a single comparative view.</sub>
</div>

---

### 🧠 SQL Phase — Complete Findings Summary

| # | Query | Key Metric | Headline Result |
|:-:|-------|-----------|----------------|
| 1 | Engagement → Views | Avg views by tier | High-engagement = **3× more views** |
| 2 | Publish time | Avg views by window | Morning uploads dominate all metrics |
| 3 | Title length | Avg views by char range | **40–70 chars** = the Goldilocks Zone |
| 4 | Category leaders | ROW_NUMBER per category | Entertainment leads; niches break through |
| 5 | Category outperformers | Performance gap (CTE+JOIN) | Power-law gap — a few massive outliers |
| 6 | Virality Score ⭐ | Composite 4-signal metric | Engagement rate predicts virality > views |
| 7 | Psychological lift | Virality vs category avg | Emotional + story-driven = highest lift |
| 8 | Creator decline | LAG() view growth | 2 consecutive declines = fatigue signal |
| 9 | Early viral signal | Engagement ÷ LOG(views) | High engagement + low views = pre-viral |
| 10 | Top decile gap | NTILE(10) avg views | Top 10% generates **28× more views** |
| 11 | Full funnel | CTE + conditional aggregation | Engagement conversion = critical bottleneck |

---

<br/>
<br/>

---

<div align="center">

# 📊 PHASE 3 — Tableau Visual Command Centre

<img src="https://img.shields.io/badge/Tool-Tableau%20Desktop-E97627?style=for-the-badge&logo=tableau&logoColor=white"/>

</div>

<br/>

> **Objective:** Translate all Python and SQL findings into a single interactive dashboard — a decision-making command centre for creators, strategists, and analysts who need insight without touching raw data.

**Dashboard components:**

| Panel | What It Shows |
|-------|--------------|
| 📈 Distribution Charts | View and engagement distributions with live category filters |
| 🕐 Time Heatmap | Publishing time performance by category and day |
| 🏆 Channel Rankings | Top channels with engagement rate overlays |
| 🔽 Funnel Visual | Animated funnel from views → likes → comments |
| 📊 Category Benchmarks | Relative performance comparison across categories |
| 🔮 Virality Leaderboard | Early breakout candidates ranked by virality score |

<br/>

<div align="center">
  <img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/tabelu.png" width="92%" alt="Tableau Dashboard"/>
  <br/>
  <sub><b>Fig · Tableau Command Centre</b> — Full interactive intelligence dashboard consolidating all findings from Phase 1 and Phase 2.</sub>
</div>

---

<br/>

---

<div align="center">

# 🏆 The Three Golden Rules of YouTube Trending

*Independently validated in Python · Confirmed in SQL · Displayed in Tableau*

<br/>

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│   🌅  Rule 1 — THE MORNING WINDOW                               │
│       Publish between 06:00 – 12:00                             │
│       → ~3× the view velocity of night uploads                  │
│                                                                  │
│   📝  Rule 2 — THE TITLE GEOMETRY                               │
│       40–70 characters: the Goldilocks Zone                     │
│       → Outperforms short AND long titles across every category │
│                                                                  │
│   💬  Rule 3 — THE ENGAGEMENT CATALYST                          │
│       Comments predict sustained trending better than likes     │
│       → The Engagement Signature is the North Star metric       │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

</div>

---

<br/>

---

## ⚠️ Challenges & How They Were Solved

<br/>

**💬 The Disabled Comments Problem**

Many trending videos had comments turned off — threatening to distort the engagement model.

**Solution →** SQL conditional logic isolated these as a dedicated control group, keeping the Engagement Signature statistically sound while preserving their view and like data for other analyses.

<br/>

**📉 The Celebrity Outlier Distortion**

High-profile uploads introduced extreme outliers that made normal content performance appear to be failure against simple averages.

**Solution →** NTILE-based Decile Analysis normalised the distribution, creating benchmarks applicable across all creator tiers — not just the top 1%.

<br/>

**🌐 Timezone Synchronisation**

Publishing timestamps came from creators globally, but all performance benchmarking needed to align to US Eastern Time.

**Solution →** Python's `pytz` library built a transformation pipeline re-anchoring all timestamps — ensuring the morning publishing finding reflected real audience behaviour, not a timezone artefact.

---

<br/>

---

<div align="center">

## 🎯 The Viral Blueprint — Final Summary

```
╔══════════════════════════════════════════════════════════════╗
║                                                              ║
║   1.  🌅  Publish between 06:00–12:00 every time            ║
║   2.  📝  Titles in the 40–70 character Goldilocks Zone      ║
║   3.  💬  Design content to generate COMMENTS not just views ║
║   4.  🎯  Benchmark within your category — not platform-wide ║
║   5.  ⚡  Experiment for breakout moments, not just volume   ║
║   6.  📊  Engagement Rate predicts reach — track it always   ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

<br/>

---

<br/>

## 👤 About the Author

**Kushala Chikkappanna Reddy**

End-to-end YouTube data intelligence pipeline spanning Python EDA, SQL structural analysis, and Tableau visual dashboarding. Key findings include a ~3× engagement impact on views, a strong morning publishing advantage, and a composite Virality Score model that outperforms raw view count as a virality predictor.

<br/>

[![GitHub](https://img.shields.io/badge/GitHub-Kushala125-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Kushala125)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com)
[![Tableau](https://img.shields.io/badge/Tableau-Public-E97627?style=for-the-badge&logo=tableau&logoColor=white)](https://public.tableau.com)

<br/><br/>

*⭐ If this project was useful or inspiring, please consider starring the repository.*

<br/>

</div>
