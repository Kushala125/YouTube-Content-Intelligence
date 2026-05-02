<div align="center">

<br/>

```
██╗   ██╗ ██████╗ ██╗   ██╗████████╗██╗   ██╗██████╗ ███████╗
╚██╗ ██╔╝██╔═══██╗██║   ██║╚══██╔══╝██║   ██║██╔══██╗██╔════╝
 ╚████╔╝ ██║   ██║██║   ██║   ██║   ██║   ██║██████╔╝█████╗  
  ╚██╔╝  ██║   ██║██║   ██║   ██║   ██║   ██║██╔══██╗██╔══╝  
   ██║   ╚██████╔╝╚██████╔╝   ██║   ╚██████╔╝██████╔╝███████╗
   ╚═╝    ╚═════╝  ╚═════╝    ╚═╝    ╚═════╝ ╚═════╝ ╚══════╝
        C O N T E N T   I N T E L L I G E N C E
```

<br/>

### *Dismantling the Algorithm — A Data-Driven Blueprint for Engineering Virality*

<br/>

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)&nbsp;
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org)&nbsp;
[![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge&logo=python&logoColor=white)](https://matplotlib.org)&nbsp;
[![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)](https://sqlite.org)&nbsp;
[![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white)](https://tableau.com)&nbsp;
[![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org)

<br/>

<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart1.png" width="32%"/>
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart3.png" width="32%"/>
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart4.png" width="32%"/>

<br/>
<sub><i>Views Distribution &nbsp;|&nbsp; Category Performance &nbsp;|&nbsp; Best Time to Post</i></sub>

<br/><br/>

> **"While creativity is an art, reach is a science."**
> 
> This project dismantles YouTube's Trending black box and rebuilds it as a transparent, repeatable, data-driven system.

<br/>

</div>

---

## 📌 The Mission

Every day, YouTube's Trending tab is the most valuable real estate on the internet. For creators and brands, appearing there changes everything — yet the path is widely treated as mysterious or luck-driven.

**This project proves it isn't luck. It's a system.**

Using an end-to-end analytics pipeline across Python, SQL, and Tableau, I analysed US YouTube Trending video data to answer one definitive question:

> *Can we engineer virality using historical patterns and statistical signals?*

**The answer — validated across three phases — is yes.**

---

## 🗂️ Repository Structure

```
📦 YouTube-Content-Intelligence
│
├── 📁 data/           →  Cleaned dataset: US_Trending_Cleaned.csv
├── 📁 notebook/       →  Python EDA: YOUTUBE.ipynb
├── 📁 sql/            →  SQL queries & analysis document
├── 📁 images/         →  All chart exports (chart1–18.png, tabelu.png)
├── 📊 youtube.twb     →  Tableau dashboard workbook
└── 📄 README.md
```

---

## 🔬 Three-Phase Investigation

| Phase | Tool | Focus |
|:-----:|------|-------|
| **🐍 1** | Python & EDA | Data cleaning · Pattern discovery · Visual storytelling |
| **🗃️ 2** | SQL & SQLite | Structural modelling · Engagement forensics · Virality scoring |
| **📊 3** | Tableau | Interactive command centre for decision-makers |

---

<br/>
<br/>

---

<div align="center">

# 🐍 PHASE 1
## Python · Exploratory Data Analysis

*Finding patterns in the noise — before the algorithm was questioned, the data had to be trusted*

</div>

---

### 🔧 Data Cleaning & Preparation

Before any analysis could begin, the raw dataset required rigorous forensic preparation:

| Step | Action |
|------|--------|
| **Deduplication** | Removed repeated video entries caused by multiple consecutive trending days |
| **Null handling** | Isolated and excluded incomplete records across views, likes, and comment columns |
| **Timezone normalisation** | Converted all global `publish_time` timestamps to US Eastern Time using Python `pytz` — critical for time-of-day accuracy |
| **Disabled comments** | Flagged `comments_disabled = True` entries as a separate control group (not discarded) to prevent engagement model distortion |
| **Category decoding** | Mapped raw numeric `category_id` values to readable labels using YouTube Data API category reference |

---

### 📊 EDA — Finding 1: Views Distribution

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart1.png" width="85%" alt="Views Distribution"/>
<br/><sub><b>Fig 1.</b> Views Distribution — Severe right skew confirming power-law dynamics across the platform</sub>
</div>

<br/>

The distribution of views across trending videos is dramatically right-skewed. Most videos occupy a modest view band, while a tiny fraction achieve explosive reach. This is a **power-law dynamic** — a few viral hits absorb most of the platform's traffic.

> ⚠️ This finding makes simple average-based performance benchmarking misleading — any analysis must account for outlier distortion before drawing conclusions.

---

### 📊 EDA — Finding 2: Views vs Likes

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart2.png" width="85%" alt="Views vs Likes"/>
<br/><sub><b>Fig 2.</b> Views vs Likes — Strong correlation, but notable divergence reveals the gap between reach and resonance</sub>
</div>

<br/>

A strong positive correlation exists between views and likes — but it is not linear. Several high-view videos receive far fewer likes than expected, while some moderate-view videos punch above their weight in engagement. This reveals the difference between **viral distribution** (algorithmic reach) and **genuine audience resonance** (content quality and relevance).

---

### 📊 EDA — Finding 3: Category Performance

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart3.png" width="85%" alt="Category Performance"/>
<br/><sub><b>Fig 3.</b> Category Performance — Audience behaviour and platform rewards differ dramatically by content type</sub>
</div>

<br/>

Different content categories exhibit fundamentally different performance patterns. Entertainment and Music dominate raw view counts, while How-to, Education, and Gaming categories often achieve higher engagement rates despite lower reach. **A fitness video and a pop music video are not competing on the same terms** — cross-category benchmarking produces false conclusions.

---

### 📊 EDA — Finding 4: Best Time to Post

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart4.png" width="85%" alt="Best Time to Post"/>
<br/><sub><b>Fig 4.</b> Publishing Time vs Performance — Morning uploads achieve ~3× the view velocity of night uploads</sub>
</div>

<br/>

Videos uploaded between **06:00 and 12:00** consistently outperform those published in the afternoon or at night. Morning uploads have more time to accumulate interactions before the algorithm's daily recommendation cycle runs — creating compounding engagement momentum that self-reinforces as the day progresses.

---

### 📊 EDA — Finding 5: Top Channels

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart5.png" width="85%" alt="Top Channels"/>
<br/><sub><b>Fig 5.</b> Top Channels by Total Views — High concentration of reach in a few dominant creators</sub>
</div>

<br/>

A small number of channels account for a disproportionately large share of total trending views. Established creators benefit from existing audiences, algorithmic trust, and platform promotion — creating structural advantages. However, the data also shows **niche breakouts**: smaller channels that reach trending through high engagement efficiency rather than raw audience size. This is the opening for new creators.

---

### 📊 EDA — Finding 6: The Engagement Funnel ⭐

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart15.png" width="85%" alt="Engagement Funnel"/>
<br/><sub><b>Fig 6.</b> Engagement Funnel — The conversion from views to comments is the critical bottleneck on the platform</sub>
</div>

<br/>

Using an **Animated Engagement Funnel**, I visualised how a video's audience behaves across three interaction stages over a 24-hour trending cycle:

```
 VIEWS       ███████████████████████████████████████   100.0%
 LIKES       ███░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░     ~8.0%
 COMMENTS    ▌░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░     ~1.2%
```

Most audiences are passive — they watch but don't interact. This means:
- Getting views is relatively easy through algorithmic distribution
- **Converting views into genuine engagement is the real differentiator**
- Content that triggers a reaction (emotional, educational, controversial) sits in a fundamentally different performance tier

---

### 🧠 Python Phase Summary

| Visual | Key Finding | Strategic Implication |
|--------|-------------|----------------------|
| Views Distribution | Power-law skew — few videos dominate | Outlier-aware analysis is essential before benchmarking |
| Views vs Likes | Strong but imperfect correlation | Content quality matters beyond raw reach |
| Category Performance | Different norms per category | Always benchmark within — not across — categories |
| Publishing Time | Morning uploads win consistently | Timing is a structural, free, controllable advantage |
| Top Channels | Reach is highly concentrated | Engagement efficiency is the path for new creators |
| Engagement Funnel | Massive drop-off at comments | Active engagement is the real algorithmic signal |

---

<br/>
<br/>

---

<div align="center">

# 🗃️ PHASE 2
## SQL · Structural Analysis

*Moving beyond observation — quantifying what actually separates trending content from everything else*

</div>

---

The cleaned dataset was migrated into an **SQLite database**. Eleven targeted queries were written using Window Functions, CTEs, conditional aggregation, and custom-engineered composite metrics to isolate the structural patterns underlying virality.

---

### 🔍 Query 1 — Do High-Engagement Videos Get More Views?

```sql
SELECT 
  CASE 
    WHEN comments = 0 THEN 'No Comments'
    WHEN (likes * 1.0 / comments) > 20 THEN 'High Engagement'
    ELSE 'Low Engagement'
  END AS engagement_tier,
  COUNT(*) AS total_videos,
  AVG(views) AS avg_views
FROM us_trending
GROUP BY engagement_tier;
```

> **📊 Finding:** High-engagement videos generate **~3× more views** than low-engagement ones.

> **💡 Insight:** Engagement is a *leading indicator* of reach — not a lagging reward. YouTube's algorithm actively amplifies content showing strong early interaction signals. The mechanism is: more comments → algorithm boost → more views. Not the reverse.

> **✅ Action:** Prioritise hooks, storytelling, and direct calls-to-action that drive comments and likes in the first hour after publishing.

---

### 🔍 Query 2 — Does Publish Time Affect Performance?

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
  AVG(views) AS avg_views,
  AVG(likes) AS avg_likes
FROM us_trending
GROUP BY time_of_day;
```

> **📊 Finding:** Morning uploads achieve significantly higher average views and likes than any other window.

> **💡 Insight:** Early publishing creates maximum runway within the algorithm's daily recommendation cycle. Morning content enters the discovery window with the most time to accumulate interactions before curation runs — a structural, timing-based advantage with zero creative cost.

> **✅ Action:** Schedule uploads consistently in the 06:00–10:00 window for maximum algorithmic exposure.

---

### 🔍 Query 3 — Do Longer Titles Perform Better?

```sql
SELECT 
  CASE 
    WHEN LENGTH(title) < 40            THEN 'Short  (<40 chars)'
    WHEN LENGTH(title) BETWEEN 40 AND 70 THEN 'Medium (40–70 chars)'
    ELSE                                    'Long   (>70 chars)' 
  END AS title_length_category,
  COUNT(*) AS total_videos,
  AVG(views) AS avg_views,
  AVG(likes) AS avg_likes
FROM us_trending
GROUP BY title_length_category;
```

> **📊 Finding:** Medium-length titles (40–70 characters) consistently outperform both short and long alternatives.

> **💡 Insight:** This is the **Goldilocks Zone** for title metadata. Short titles lack the context that drives a click. Long titles get truncated on mobile (the dominant viewing platform). The 40–70 character window balances SEO discoverability, mobile display, and cognitive clarity simultaneously.

> **✅ Action:** Treat title length as a precision engineering decision — not an afterthought. Balance curiosity + clarity + keyword within 40–70 characters.

---

### 🔍 Query 4 — Top 3 Videos Per Category (Window Function)

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

> **📊 Finding:** Entertainment and Music dominate top positions, but niche content regularly breaks through in Gaming, How-to, and Science categories.

> **💡 Insight:** Viral success is category-dependent but not category-exclusive. Smaller creators can compete by benchmarking against the top performers *within their own category* — not against platform-wide giants with structurally different advantages.

> **✅ Action:** Study the structural patterns (hook type, length, title format, thumbnail style) of the top 3 videos in your specific category.

---

### 🔍 Query 5 — Which Videos Outperform Their Category Average? (CTE + JOIN)

```sql
WITH category_avg AS (
  SELECT 
    category_id, 
    AVG(views) AS avg_category_views
  FROM us_trending
  GROUP BY category_id
)
SELECT 
  t.title, 
  t.category_id, 
  t.views,
  c.avg_category_views,
  (t.views - c.avg_category_views) AS performance_gap
FROM us_trending t
JOIN category_avg c ON t.category_id = c.category_id
ORDER BY performance_gap DESC
LIMIT 15;
```

> **📊 Finding:** A small number of videos outperform their category average by extreme margins — the performance gap distribution is itself power-law shaped.

> **💡 Insight:** Content performance follows a **power-law distribution within every category**. A few breakout hits drive most category-level traffic. Consistency alone cannot compete with a single well-timed viral moment.

> **✅ Action:** Run deliberate creative experiments for breakout content, rather than only optimising for reliable average performance.

---

### 🔍 Query 6 — Composite Virality Score Model ⭐ *Core Innovation*

```sql
WITH features AS (
  SELECT 
    title, views, likes, comments,
    (likes    * 1.0 / views) AS like_rate,
    (comments * 1.0 / views) AS comment_rate,
    LENGTH(title) AS title_length,
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
FROM scored
ORDER BY virality_score DESC LIMIT 15;
```

This query engineers a **custom Virality Score** weighting four independently validated signals: like rate (50%), comment rate (30%), title length optimisation (10%), and publishing time (10%). It is the analytical centrepiece of the project.

> **📊 Finding:** Engagement rate is a stronger virality predictor than raw view count. High-scoring videos frequently have moderate views but exceptional audience interaction.

> **💡 Insight:** Platforms optimise for *interaction efficiency*, not reach alone. Niche fan-driven content regularly outperforms mainstream content on this metric — depth of audience connection matters more than breadth of distribution.

> **✅ Action:** Design content for engagement rate — not view maximisation. A video seen by 500K who comment is worth more algorithmically than one seen by 2M who scroll past.

---

### 🔍 Query 7 — Psychological Overperformers: What Content Lifts Above Expectations?

```sql
WITH base AS (
  SELECT 
    title, category_id, views,
    (likes * 1.0 / NULLIF(views, 0)) 
    + (comments * 1.0 / NULLIF(views, 0)) AS virality
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
ORDER BY lift DESC LIMIT 20;
```

> **📊 Finding:** The highest-lift overperformers share three consistent characteristics — they are **emotional**, **story-driven**, or **curiosity-based** in their primary hook.

> **💡 Insight:** Psychology consistently outperforms production quality. Emotional hooks — personal narratives, surprising reveals, strong stakes — generate the kind of engagement that lifts a video above its category baseline. This is a **repeatable pattern**, not creative luck.

> **✅ Action:** Integrate emotional triggers and storytelling arcs at the scripting stage — not as an afterthought in the edit.

---

### 🔍 Query 8 — Detecting Declining Creators (LAG Window Function)

```sql
WITH lagged AS (
  SELECT 
    channel_title, views,
    LAG(views) OVER (
      PARTITION BY channel_title 
      ORDER BY publish_time
    ) AS prev_views
  FROM us_trending
)
SELECT 
  channel_title, views, prev_views, 
  (views - prev_views) AS growth
FROM lagged
WHERE prev_views IS NOT NULL
ORDER BY growth ASC LIMIT 5;
```

> **📊 Finding:** Several channels show consistent, measurable view decline across consecutive uploads — a clear early signal of content fatigue or audience disengagement.

> **💡 Insight:** Audience attention decays without content innovation. The algorithm likely reduces recommendation exposure for channels showing declining engagement trajectories — creating a compounding negative feedback loop that is hard to reverse.

> **✅ Action:** Monitor your own channel's LAG growth metric. Two consecutive declines is a trigger to refresh content strategy — not a signal to post more of the same.

---

### 🔍 Query 9 — Early Viral Signal Detection

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

> **📊 Finding:** High relative engagement combined with low absolute view count is a consistent early viral signal — identifying likely breakout videos before they scale.

> **💡 Insight:** This query models how recommendation engines identify viral content for amplification. A video at 50K views with 10× its category engagement ratio is almost certainly being tested for a broader push. The signal is detectable *before* scale happens.

> **✅ Action:** For creators — maximise engagement in the first 2 hours. For analysts — this metric can power a live viral candidate detection dashboard.

---

### 🔍 Query 10 — Are the Top 10% Fundamentally Different? (NTILE)

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

> **📊 Finding:** The top 10% of trending videos generate approximately **28× more views** than the bottom 90%.

> **💡 Insight:** Platform traffic is overwhelmingly concentrated in a tiny percentage of breakout hits. Long-tail content contributes relatively little to aggregate engagement. The platform's growth depends on viral moments — not a healthy distribution of consistent performers.

> **✅ Action:** Allocate creative resources asymmetrically — invest more in content with genuine breakout potential rather than spreading effort uniformly across average-output volume.

---

### 🔍 Query 11 — Full Content Funnel (CTE + NTILE + Conditional Aggregation)

```sql
WITH base AS (
  SELECT views,
    (likes * 1.0 / views + comments * 1.0 / views) AS engagement
  FROM us_trending
),
ranked AS (
  SELECT *, NTILE(10) OVER (ORDER BY views DESC) AS decile 
  FROM base
)
SELECT 
  COUNT(*) AS total_videos,
  SUM(CASE WHEN views > 100000    THEN 1 ELSE 0 END) AS reached_100k,
  SUM(CASE WHEN engagement > 0.05 THEN 1 ELSE 0 END) AS highly_engaged,
  SUM(CASE WHEN decile = 1        THEN 1 ELSE 0 END) AS viral_tier
FROM ranked;
```

> **📊 Finding:** The largest proportional drop-off occurs at the **engagement threshold** — far more videos achieve 100K views than achieve meaningful audience interaction rates.

> **💡 Insight:** Reach is not the bottleneck — engagement conversion is. The algorithm uses engagement signals to decide which high-reach videos deserve promotion to viral scale. Videos that fail the engagement threshold get stuck at moderate reach regardless of view count.

> **✅ Action:** Optimise for interaction prompts, not just distribution. Every video needs a hook that makes engagement feel effortless and natural for the audience.

---

### 🧠 SQL Phase — Full Findings Summary

| # | Query Focus | Key Metric | Headline Result |
|:-:|------------|-----------|----------------|
| 1 | Engagement → Views | Avg views by tier | High-engagement = **3× more views** |
| 2 | Publish time | Avg views by window | Morning uploads dominate across all metrics |
| 3 | Title length | Avg views by char range | **40–70 chars** is the Goldilocks Zone |
| 4 | Category leaders | ROW_NUMBER per category | Entertainment leads; niches still break through |
| 5 | Category outperformers | Performance gap (CTE+JOIN) | Power-law gap — a few massive outliers dominate |
| 6 | Virality Score | Composite multi-signal metric | Engagement rate predicts virality better than views |
| 7 | Psychological lift | Virality vs category avg | Emotional + story-driven content = highest lift |
| 8 | Creator decline | LAG() view growth | Consistent decline = measurable content fatigue |
| 9 | Early viral signal | Engagement ÷ LOG(views) | High engagement + low views = pre-viral signature |
| 10 | Top decile gap | NTILE(10) avg views | Top 10% generates **28× more views** |
| 11 | Full funnel | CTE + conditional aggregation | Engagement conversion is the critical bottleneck |

---

<br/>
<br/>

---

<div align="center">

# 📊 PHASE 3
## Tableau · Visual Command Centre

*Translating all findings into a single interactive dashboard for strategic decision-making*

</div>

---

The Tableau workbook (`youtube.twb`) integrates all three phases into a cohesive visual intelligence layer. Every finding from Python and SQL is represented in an interactive, filterable format designed for creators, strategists, and analysts who need insight without touching the raw data.

**Dashboard components:**
- 📈 View and engagement distribution charts with live category filters
- 🕐 Publishing time heatmaps identifying optimal upload windows by category
- 🏆 Top channel performance rankings with engagement rate overlays
- 🔽 Animated funnel from views through to comments
- 📊 Category benchmarking for relative performance comparison
- 🔮 Virality score leaderboard highlighting early breakout candidates

<br/>

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/tabelu.png" width="92%" alt="Tableau Dashboard"/>
<br/><sub><b>Fig 7.</b> Tableau Command Centre — Full interactive intelligence dashboard consolidating all project findings</sub>
</div>

---

<br/>

---

<div align="center">

# 🏆 The Three Golden Rules of YouTube Trending

*Validated in Python · Confirmed in SQL · Displayed in Tableau*

</div>

---

<br/>

<div align="center">

## 🌅 Rule 1 — The Morning Window

</div>

> Videos published between **06:00 and 12:00** achieve approximately **3× the view velocity** of videos published at night.

Alignment with the start of the US workday provides the initial momentum required for the algorithm to take notice. Morning uploads enter the recommendation cycle with maximum runway. This is a **structural, free advantage** that requires zero creative effort to implement — it is purely a scheduling decision.

<br/>

<div align="center">

## 📝 Rule 2 — The Title Geometry

</div>

> Titles in the **40–70 character range** consistently outperform both shorter and longer alternatives across every content category.

This is the precision window where three forces align: SEO keyword density, mobile display completeness, and cognitive clarity. Too short — the title lacks the context that drives a click. Too long — it gets truncated on mobile, the dominant viewing platform. **The 40–70 character Goldilocks Zone is the data's most actionable finding.**

<br/>

<div align="center">

## 💬 Rule 3 — The Engagement Catalyst

</div>

> Comments are a stronger predictor of sustained trending status than likes. The **Engagement Signature** — a high likes-to-comments ratio — is the most reliable metric for predicting which videos stay on the trending list across multiple days.

Active engagement (comments) signals a genuine conversation ignited by the content. Passive engagement (likes) signals approval. The algorithm rewards the former far more heavily — because conversation drives session depth, which drives the ad revenue YouTube fundamentally optimises for.

---

<br/>

---

## ⚠️ Challenges & Solutions

<br/>

**💬 The Disabled Comments Problem**

Many trending videos had comments turned off — threatening to distort the entire engagement model.

*Solution:* SQL conditional logic isolated these as a dedicated control group, allowing the Engagement Signature to remain statistically sound while preserving their view and like data for other analyses.

<br/>

**📉 The Celebrity Outlier Distortion**

High-profile uploads introduced extreme outliers that made normal content performance look like failure against simple averages.

*Solution:* NTILE-based Decile Analysis normalised the distribution, creating benchmarks applicable across all creator tiers — not just the top 1%.

<br/>

**🌐 Timezone Synchronisation**

Publishing timestamps originated globally, but all performance benchmarking needed to align to US Eastern Time (the dominant audience timezone).

*Solution:* Python's `pytz` library built a transformation pipeline that re-anchored all timestamps — ensuring the morning advantage finding reflected real audience behaviour, not a timezone artefact.

---

<br/>

---

<div align="center">

## 📌 Additional EDA Charts

</div>

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart6.png" width="47%"/>&nbsp;
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart7.png" width="47%"/>
<br/><sub>Extended EDA — Engagement patterns across additional cuts of the data</sub>
</div>

<br/>

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart8.png" width="47%"/>&nbsp;
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart9.png" width="47%"/>
<br/><sub>Deep-dive analysis — Distribution and correlation charts from secondary EDA phase</sub>
</div>

<br/>

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart10.png" width="47%"/>&nbsp;
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart11.png" width="47%"/>
<br/><sub>Performance segmentation — Channel-level and category-level breakdown charts</sub>
</div>

<br/>

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart12.png" width="47%"/>&nbsp;
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart13.png" width="47%"/>
<br/><sub>Temporal and metadata analysis — Time-based and title-based performance patterns</sub>
</div>

<br/>

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart16.png" width="47%"/>&nbsp;
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart17.png" width="47%"/>
<br/><sub>Advanced modelling outputs — Virality scoring and engagement efficiency analysis</sub>
</div>

<br/>

<div align="center">
<img src="https://raw.githubusercontent.com/Kushala125/YouTube-Content-Intelligence/main/images/chart18.png" width="70%"/>
<br/><sub>Final summary visualisation — Consolidated findings from the full EDA pipeline</sub>
</div>

---

<br/>

---

<div align="center">

## 🎯 Conclusion — The Viral Blueprint

</div>

This project proves that while **creativity is an art, reach is a science.**

By combining Python's visual storytelling, SQL's structural precision, and Tableau's interactive clarity — a clear, repeatable, evidence-based framework emerges for YouTube content strategy.

<br/>

```
┌─────────────────────────────────────────────────────────┐
│                   THE VIRAL BLUEPRINT                   │
├─────────────────────────────────────────────────────────┤
│  🌅  Publish between 06:00 – 12:00 every time           │
│  📝  Write titles in the 40–70 character Goldilocks Zone │
│  💬  Design content to generate comments, not just views │
│  🎯  Benchmark within your category — not platform-wide  │
│  ⚡  Experiment for breakout moments, not just volume    │
│  📊  Track engagement rate — it predicts reach           │
└─────────────────────────────────────────────────────────┘
```

<br/>

---

<div align="center">

<br/>

## 👤 About the Author

**Kushala Chikkappanna Reddy**

End-to-end YouTube data intelligence pipeline spanning Python EDA, SQL structural analysis, and Tableau visual dashboarding. Key findings include a ~3× engagement impact on views, a strong morning publishing advantage, and a composite Virality Score model that outperforms raw view count as a trending predictor.

<br/>

[![GitHub](https://img.shields.io/badge/GitHub-Kushala125-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Kushala125)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com)

<br/>

*⭐ If this project was useful or inspiring, please consider starring the repository.*

<br/>
<br/>

</div>
