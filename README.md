# Manhattan Crime Visualization Dashboard

![Crime Visualization Dashboard](/data/project-thumbnail.png)

Look, **206 000 CSV rows** of NYPD complaints are about as digestible as kernel panic logs.  
So I did the sane thing: **chopped the scope down to Manhattan (≈ 11 000 records)** and built a dashboard that even a product manager could understand.

---

## Table of Contents
- [Why Manhattan?](#why-manhattan)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Usage](#usage)

---

## Why Manhattan?
Because:

- It’s **dense**—bad things happen in close proximity, which makes patterns pop.  
- My laptop fans shouldn’t audition for *Top Gun* just to render a map.  
- If we can tame Manhattan, the other boroughs are a three-line `for`-loop away.  

---

## Features
- **Interactive map** with crime hotspots (heat-maps, cluster layers, the whole fire-works display).  
- **Time-series scrubber**: drag through months and watch the dots jitter like nervous interns.  
- **Category filters**: felony, misdemeanor, violation—pick your flavor of human error.  
- **Deep-linking**: paste a URL and the viewer lands on the exact zoom/filter you’re ranting about.  
- **All-JavaScript stack**—no “install Python 3.11 but not 3.10” horror stories.  

---

## Tech Stack

| Layer          | Stuff Used                                 | Why I Didn’t Choose Something Else                    |
| -------------- | ------------------------------------------ | ----------------------------------------------------- |
| Data wrangling | `Node 20`, `d3-dsv`, `turf.js`             | CSV in Excel? Enjoy your corrupted encodings.         |
| Front-end      | `Vite`, `React`, `Leaflet`                 | Webpack is a nostalgia trip I don’t need.             |
| Back-end       | `Express` (optional - static works fine)   | Django? Wrong language. Flask? Same problem.          |
| Styling        | Hand-rolled CSS (no 2 MB frameworks)       | Tailwind is nice, but I’m not paying the bundle tax.  |
| Testing        | `jest` + `vitest`                          | If you don’t test, you’re testing in prod—good luck.  |

---

## Installation
> If cloning and `npm i` are foreign concepts, step away from the keyboard.

```bash
git clone https://github.com/your-handle/Manhattan-Crime-Dashboard.git
cd Manhattan-Crime-Dashboard
npm install          # or pnpm / yarn—pick your poison
