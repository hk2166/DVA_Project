# Data Dictionary

## Overview
This document describes all variables in the Teen Mental Health dataset after processing.

---

## Original Features

### Demographics

| Variable | Type | Range/Values | Description |
|----------|------|--------------|-------------|
| `age` | Integer | 13-19 | Age of the teenager in years |
| `gender` | Categorical | male, female | Self-reported gender |

### Social Media Usage

| Variable | Type | Range/Values | Description |
|----------|------|--------------|-------------|
| `daily_social_media_hours` | Float | 1.0-8.0 | Average hours spent on social media per day |
| `platform_usage` | Categorical | Instagram, TikTok, Both | Primary social media platform(s) used |

### Sleep & Screen Time

| Variable | Type | Range/Values | Description |
|----------|------|--------------|-------------|
| `sleep_hours` | Float | 4.0-9.0 | Average hours of sleep per night |
| `screen_time_before_sleep` | Float | 0.5-3.0 | Hours of screen time in the hour before bed |

### Lifestyle Factors

| Variable | Type | Range/Values | Description |
|----------|------|--------------|-------------|
| `academic_performance` | Float | 2.0-4.0 | GPA or academic performance score |
| `physical_activity` | Float | 0.0-2.0 | Hours of physical activity per day |
| `social_interaction_level` | Categorical | low, medium, high | Level of in-person social interaction |

### Mental Health Indicators

| Variable | Type | Range/Values | Description |
|----------|------|--------------|-------------|
| `stress_level` | Integer | 1-10 | Self-reported stress level (1=low, 10=high) |
| `anxiety_level` | Integer | 1-10 | Self-reported anxiety level (1=low, 10=high) |
| `addiction_level` | Integer | 1-10 | Social media addiction assessment (1=low, 10=high) |

---

## Derived Features

### Derived Metrics :-

| Variable | Type | Range/Values | Description |
|----------|------|--------------|-------------|
| `social_interaction_score` | Integer | 1-3 | Ordinal encoding: low=1, medium=2, high=3 |
| `mental_health_score` | Integer | 2-20 | Combined score: stress_level + anxiety_level |

### Risk Flags:-

| Variable | Type | Values | Description |
|----------|------|--------|-------------|
| `high_social_media_usage` | Binary | 0, 1 | 1 if daily_social_media_hours > 4, else 0 |
| `low_sleep` | Binary | 0, 1 | 1 if sleep_hours < 6, else 0 |
| `late_night_screen` | Binary | 0, 1 | 1 if screen_time_before_sleep > 2, else 0 |

---

## Statistical Summary

### Continuous Variables

| Variable | Mean | Std Dev | Min | 25% | Median | 75% | Max |
|----------|------|---------|-----|-----|--------|-----|-----|
| age | 15.93 | 2.02 | 13 | 14 | 16 | 18 | 19 |
| daily_social_media_hours | 4.54 | 2.03 | 1.0 | 2.8 | 4.5 | 6.3 | 8.0 |
| sleep_hours | 6.45 | 1.44 | 4.0 | 5.2 | 6.5 | 7.6 | 9.0 |
| screen_time_before_sleep | 1.74 | 0.72 | 0.5 | 1.1 | 1.8 | 2.4 | 3.0 |
| academic_performance | 2.99 | 0.58 | 2.0 | 2.5 | 2.99 | 3.48 | 4.0 |
| physical_activity | 1.01 | 0.58 | 0.0 | 0.5 | 1.0 | 1.5 | 2.0 |
| stress_level | 5.45 | 2.90 | 1 | 3 | 5 | 8 | 10 |
| anxiety_level | 5.64 | 2.86 | 1 | 3 | 6 | 8 | 10 |
| addiction_level | 5.57 | 2.83 | 1 | 3 | 6 | 8 | 10 |
| mental_health_score | 11.08 | 4.11 | 2 | 8 | 11 | 14 | 20 |

### Categorical Variables

#### Gender Distribution
- Male: ~50%
- Female: ~50%

#### Platform Usage Distribution
- Instagram: ~33%
- TikTok: ~33%
- Both: ~33%

#### Social Interaction Level Distribution
- Low: ~33%
- Medium: ~33%
- High: ~33%

### Binary Flags

| Flag | Percentage with Flag=1 |
|------|------------------------|
| high_social_media_usage | 56.0% |
| low_sleep | 40.0% |
| late_night_screen | 36.8% |

---

## Data Quality Notes

1. **Missing Values**: All missing values were imputed
   - Numeric: Filled with median
   - Categorical: Filled with mode

2. **Outliers**: Capped to reasonable ranges
   - `daily_social_media_hours`: 0-12 hours
   - `sleep_hours`: 0-12 hours

3. **Duplicates**: Removed (9 duplicate records)

4. **Final Dataset**: 1,200 clean records

---

## Usage Notes

- **Mental Health Score**: Higher values indicate poorer mental health
- **Risk Flags**: Binary indicators for at-risk behaviors
- **Social Interaction Score**: Ordinal scale for easier correlation analysis
- All continuous variables are on their natural scales (hours, scores)

---

## Target Variable (Removed)

**Note**: The original dataset contained a `depression_label` binary variable (0/1) which was removed during processing. This analysis focuses on continuous mental health indicators rather than binary classification.
