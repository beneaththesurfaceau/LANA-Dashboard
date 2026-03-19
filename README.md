# LANA Dashboard

![License: LANA v2.0](https://img.shields.io/badge/License-LANA%20v2.0-blue)
![No Dependencies](https://img.shields.io/badge/Dependencies-None-green)

A real-time statistical implementation of the LANA Methodology, exposing the invisible mortality rate of childhood homelessness in Australia.

## Overview

This project addresses the systematic undercount of homeless child deaths in Australia, where official administrative data linkage captures only 23–30% of actual deaths.

The implementation consists of:

- **Mortality Tracker** - A reactive web interface (`dashboard.html`) for real-time visualization of estimated deaths
- **Research Framework** - A detailed multi-pathway mortality model (`methodology.md`)
- **Memorial License** - A legal framework (v2.0) ensuring all derivative works remain anonymized and memorial-focused

## Features

- Real-time death counter with per-second precision
- Multi-pathway mortality model (v2.0) aggregating eight risk pathways
- Year-by-year projections with housing crisis adjustments
- Fully client-side calculations (no backend required)
- Zero external dependencies

## Quick Start

```bash
# Clone the repository
git clone https://github.com/beneaththesurfaceau/LANA-Dashboard.git
cd LANA-Dashboard

# Open in browser (no build process required)
open dashboard.html
# or on Windows:
start dashboard.html
```

No installation, build tools, or dependencies required. Simply open `dashboard.html` in any modern browser.

## The LANA Methodology

The methodology addresses the systematic undercount of homeless child deaths, which often go unrecorded in mortality registries or coronial records.

### Multi-Pathway Model (v2.0)

Total deaths are calculated by aggregating eight specific risk pathways, with an inter-pathway overlap adjustment and temporal trend correction:

| Pathway | Deaths/Year | Description |
|---------|-------------|-------------|
| **Visible (Coverage-Adjusted)** | 50 | SHS-connected deaths adjusted for linkage and coverage gaps |
| **Adolescent Suicide/OD** | 22 | Hidden homeless youth (12–17) with 4.5× risk multiplier |
| **SUDI** | 20 | Housing-attributable infant deaths via population attributable fraction |
| **Accident/Illness** | 14 | Excess deaths in hidden homeless children (1–11) |
| **Neonatal/Perinatal** | 8 | Neonatal deaths attributable to maternal housing insecurity |
| **Temporally Unlinked** | 8 | Deaths occurring >12 months after last SHS contact |
| **FDV-Related** | 6 | Housing-preventable DFV-context filicides |
| **Child Protection Interface** | 4 | Deaths in OOHC where housing drove family separation |

## Modification Guide

The project is built using vanilla HTML5, CSS3, and JavaScript for maximum portability and ease of audit.

### Model Parameters

All mathematical logic is encapsulated in the `MODEL_PARAMS` object within `dashboard.html`. Modify these values to reflect localized or updated research:

```javascript
const MODEL_PARAMS = {
    baseEstimate: 155, // Central annualized death estimate (v2.0)
    lowerBound: 136,   // 95% Plausible Range (Lower)
    upperBound: 181,   // 95% Plausible Range (Upper)

    // Housing crisis multipliers adjust for worsening economic conditions
    housingCrisisMultiplier: {
        2024: 1.08,
        2025: 1.12,
        2026: 1.15
    }
};
```

### Live Counter Logic

The tracker calculates deaths-to-date with per-second precision:

1. **Pro-rating** - Determines seconds passed in the current year
2. **Frequency** - Calculates `deathsPerSecond` from the annualized estimate
3. **Injection** - `updateLiveCounter()` is called via `setInterval` every 1000ms

## Documentation

- [Methodology](methodology.md) - Detailed research framework and data sources
- [User Guide](USERGUIDE.md) - Implementation and customization guide
- [License](LICENSE.md) - LANA License v2.0 full terms

## License

This project is governed by the **LANA License v2.0** - a share-alike license with memorial-focused requirements.

See [LICENSE.md](LICENSE.md) for full terms.

### Branding Rules

| Permitted | Prohibited |
|-----------|------------|
| Organization logo/name in header and footer | Individual names or researcher bios in content |
| Neutral attribution link | Sponsor "shout-outs" in About section |

## Attribution

All projects must include:

> Derived from the LANA Methodology (https://www.beneaththesurface.au/lana-methodology)
