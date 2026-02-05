# LANA Dashboard User Guide

**Version 1.4**

![Type](https://img.shields.io/badge/Type-User%20Guide-green)
![License](https://img.shields.io/badge/License-LANA%20v1.4-blue)

[← Back to README](README.md) | [View Dashboard](dashboard.html) | [Methodology](methodology.md)

---

## Table of Contents

- [1. Project Philosophy & Governance](#1-project-philosophy--governance)
- [2. The Research Framework](#2-the-research-framework-methodology)
- [3. Technical Implementation](#3-technical-implementation-the-code)
- [4. Customization & Localization](#4-customization--localization)
- [5. Deployment Checklist](#5-deployment-checklist)

---

## Overview

This guide provides the instructions necessary to implement, modify, and maintain a LANA Mortality Project. This project is a legally protected digital memorial designed to center the human cost of childhood homelessness while removing institutional and personal vanity.

---

## 1. Project Philosophy & Governance

The LANA Project operates under a "Memorial-First" framework. In a digital landscape often dominated by "social responsibility" branding, this methodology mandates a return to pure focus on the victims.

### LANA License (v1.4) Compliance

Any developer or organization using this code must adhere to these strict legal conditions:

| Requirement | Description |
|-------------|-------------|
| **Mandatory Memorial Naming** | The project cannot be named after an organization or a generic city; it must be named after a specific child lost to homelessness |
| **The Identity Veil** | You are prohibited from listing the names of individual researchers, authors, or financial donors in the project's main content or promotion |
| **Neutral Attribution** | Credits must be functional, not personal. Use: "Derived from the LANA Methodology (https://www.beneaththesurface.au/lana-methodology)" |
| **The Structural Exception** | You may place your organizational logo and business name within the site-wide header and footer only |

See [LICENSE.md](LICENSE.md) for full legal terms.

---

## 2. The Research Framework: Methodology

The core of this project is a **Multi-Pathway Mortality Model**. Research suggests that official administrative data linkage only captures about 23% of child deaths attributable to homelessness.

### The Six Pathways of Mortality

The model estimates the "True Toll" by calculating risk across these distinct areas:

| Pathway | Description |
|---------|-------------|
| **Visible (Linkage-Adjusted)** | SHS-connected deaths, adjusted for ~79% linkage success rate |
| **SUDI in Hidden Homelessness** | Infant deaths (0-1) in overcrowded or unstable housing |
| **Adolescent Suicide/Overdose** | 6.0× mortality multiplier for hidden homeless youth (12-17) |
| **Accident/Illness** | Deaths of hidden homeless children (1-11) from reduced healthcare access |
| **FDV-Related** | Deaths where lack of housing prevented escape from domestic violence |
| **Unlinked Post-Support** | Deaths occurring >12 months after last service contact |

See [methodology.md](methodology.md) for detailed calculations and data sources.

---

## 3. Technical Implementation: The Code

The project is delivered as a lightweight, reactive dashboard (`dashboard.html`) powered by vanilla JavaScript.

### Core Logic: The `MODEL_PARAMS` Object

All statistical assumptions are contained within a single JSON-like object at the top of the script:

| Parameter | Description |
|-----------|-------------|
| `baseEstimate` | The central annual death count (default: 169) |
| `housingCrisisMultiplier` | Year-by-year factor adjusting for the intensifying housing crisis |
| `childPopulation` | ABS-based estimates for calculating mortality rate per 100,000 children |

### The Live Counter Calculation

The "live" feel of the dashboard is achieved through time-precision calculation within the `calculateYearToDate` function:

1. **Seconds Elapsed** — Determines seconds passed since January 1st of the current year
2. **Deaths Per Second** — Calculates deaths per second from the annualized central estimate
3. **Real-Time Injection** — Result is injected into `#liveCounter` every 1,000 milliseconds

---

## 4. Customization & Localization

Developers are encouraged to adapt this model for specific states, regions, or updated datasets.

### How to Modify the Data

To localize the dashboard for a specific region:

1. **Update `baseEstimate`** — Change the baseline annual death estimate in `MODEL_PARAMS` to reflect localized research
2. **Update `childPopulation`** — Input the specific child population numbers for your target area
3. **Pathway Breakdown** — Adjust the progress bar widths and values in the `breakdown-section` of the HTML to match local proportions

### Visual Customization

You may modify the CSS variables in the `:root` section to match your organizational theme, provided the Identity Exclusion rules of Section 3.B in the license are maintained.

---

## 5. Deployment Checklist

Before taking your implementation live, verify the following:

- [ ] **Project Title** — Is the site/repository named after a specific child?
- [ ] **Branding Check** — Are all logos and organizational names restricted only to the header or footer?
- [ ] **Attribution** — Does the footer contain the neutral URL link to lana-methodology?
- [ ] **Anonymity** — Have all researcher names, donor lists, and "Lead by" credits been removed?
- [ ] **Data Integrity** — Is the "Important Note" regarding statistical estimates visible to prevent data misinterpretation?

---

[↑ Back to Top](#lana-dashboard-user-guide) | [← Back to README](README.md)
