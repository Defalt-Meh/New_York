# Manhattan Crime Visualization Dashboard

![Crime Visualization Dashboard](/data/project-thumbnail.png)

Look, **206 000 CSV rows** of NYPD complaints are about as digestible as kernel panic logs.  
So I did the sane thing: **chopped the scope down to Manhattan (≈ 11 000 records)** and built a dashboard that even a product manager could understand.

---

## Table of Contents
1. [Why Manhattan?](#why-manhattan)
2. [Features](#features)
3. [Tech Stack](#tech-stack)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Project Layout](#project-layout)
7. [Further Plans](#further-plans)
8. [Contributing](#contributing)
9. [License](#license)

---

## Why Manhattan?
Because:
- It’s **dense**—bad things happen in close proximity, which makes patterns pop.  
- My laptop fans shouldn’t have to audition for *Top Gun* just to render a map.  
- If we can tame Manhattan, the other boroughs are a `for`-loop away.

---

## Features
- **Interactive map** with crime hotspots (heatmaps, cluster layers, the whole fireworks display).  
- **Time-series lens**: scrub through months and watch the dots dance.  
- **Category filters**: felony, misdemeanor, violation—pick your poison.  
- **Deep-linking**: share a URL and coworkers land on the exact zoom/filter you’re ranting about.  
- **Zero JavaScript gymnastics** in your browser dev-tools console to get it running (Python + Dash handle the heavy lifting).

---

## Tech Stack
| Layer | Stuff Used | Why I Didn’t Choose Something Else |
|-------|------------|------------------------------------|
| Data wrangling | `Python 3.11`, `pandas`, `geopandas` | Excel is where data goes to die |
| Back-end | `Dash`, `Flask` | I like seeing what I type before I hit compile |
| Mapping | `Leaflet` (via `dash-leaflet`) | Plotting lat/long in Matplotlib? No thanks |
| Styling | Minimal CSS, zero frameworks | CSS frameworks are just bloat with prettier marketing |
| Testing | `pytest` | If you don’t test, you’re testing in prod—good luck |

---

## Installation
> If you can’t handle a virtual-env, I can’t help you.

```bash
git clone https://github.com/your-handle/Manhattan-Crime-Dashboard.git
cd Manhattan-Crime-Dashboard
python -m venv venv
source venv/bin/activate      # Windows users: venv\Scripts\activate
pip install -r requirements.txt


## Usage

# 1. Ingest & preprocess raw CSV (creates cleaned_parquet/)
python scripts/01_clean_dataset.py --input data/raw/NYPD_Complaint_Data.csv

# 2. Fire up the dashboard
python app.py

Then aim your browser at http://127.0.0.1:8050/ and marvel at the dots.

## Project Layout

.
├── app.py                  # Dash entry-point
├── data/
│   ├── raw/                # untouched CSV from NYC Open Data
│   └── cleaned_parquet/    # column-typed, de-duplicated, index-friendly data
├── scripts/
│   ├── 01_clean_dataset
│   └── 02_generate_tiles
├── dashboards/             # future multi-page layouts live here
└── tests/                  # pytest lives here; run them before PRs


# Further Plans

I jumped tracks to an AI & Data Science specialization, so the fun’s just starting:
1. Generative model on the full tri-borough dataset (yes, all 206 k rows).
2. Spatio-temporal transformer to spit out a probability heatmap for “where/when bad stuff will probably happen next.”
3. If the model says the entire city is doomed, at least we’ll have a cool GIF.
