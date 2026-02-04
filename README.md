# LANA Dashboard

![License: LANA v1.4](https://img.shields.io/badge/License-LANA%20v1.4-blue)
![No Dependencies](https://img.shields.io/badge/Dependencies-None-green)

A real-time statistical implementation of the LANA Methodology, exposing the invisible mortality rate of childhood homelessness in Australia.

## Overview

This project addresses the systematic undercount of homeless child deaths in Australia, where official administrative data linkage captures only 23–30% of actual deaths.

The implementation consists of:

- **Mortality Tracker** - A reactive web interface (`dashboard.html`) for real-time visualization of estimated deaths
- **Research Framework** - A detailed multi-pathway mortality model (`methodology.md`)
- **Memorial License** - A legal framework (v1.4) ensuring all derivative works remain anonymized and memorial-focused

## Features

- Real-time death counter with per-second precision
- Multi-pathway mortality model aggregating six risk pathways
- Year-by-year projections with housing crisis adjustments
- Fully client-side calculations (no backend required)
- Zero external dependencies

## Quick Start

```bash
# Clone the repository
git clone <repository-url>
cd LANA-Dashboard

# Open in browser (no build process required)
open dashboard.html
# or on Windows:
start dashboard.html
```

No installation, build tools, or dependencies required. Simply open `dashboard.html` in any modern browser.

## The LANA Methodology

The methodology addresses the systematic undercount of homeless child deaths, which often go unrecorded in mortality registries or coronial records.

### Multi-Pathway Model

Total deaths are calculated by aggregating six specific risk pathways:

| Pathway | Description |
|---------|-------------|
| **Visible Deaths** | SHS-connected deaths adjusted for ~79% data linkage success rate |
| **SUDI** | Sudden Unexpected Death in Infancy attributable to severe overcrowding |
| **Adolescent Suicide/OD** | Hidden homeless youth (12–17) with 6.0× risk multiplier |
| **FDV-Related** | Deaths where housing barriers prevented escape from domestic violence |
| **Accident/Illness** | Children (1–11) in hidden homelessness with reduced healthcare access |
| **Unlinked Deaths** | Mortality occurring >12 months after last service contact |

## Modification Guide

The project is built using vanilla HTML5, CSS3, and JavaScript for maximum portability and ease of audit.

### Model Parameters

All mathematical logic is encapsulated in the `MODEL_PARAMS` object within `dashboard.html`. Modify these values to reflect localized or updated research:

```javascript
const MODEL_PARAMS = {
    baseEstimate: 169, // Central annualized death estimate
    lowerBound: 89,    // 95% Confidence Interval (Lower)
    upperBound: 251,   // 95% Confidence Interval (Upper)

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
- [License](LICENSE.md) - LANA License v1.4 full terms

## License

This project is governed by the **LANA License v1.4** - a share-alike license with memorial-focused requirements.

See [LICENSE.md](LICENSE.md) for full terms.

### Branding Rules

| Permitted | Prohibited |
|-----------|------------|
| Organization logo/name in header and footer | Individual names or researcher bios in content |
| Neutral attribution link | Sponsor "shout-outs" in About section |

## Attribution

All projects must include:

> Derived from the LANA Methodology (https://www.beneaththesurface.au/lana-methodology)
