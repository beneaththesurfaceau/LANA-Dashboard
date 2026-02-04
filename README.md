1. Project Overview
This project provides a real-time statistical implementation of the LANA Methodology. It is designed to expose the "invisible" mortality rate of childhood homelessness in Australia, where official administrative data linkage is estimated to capture only 23–30% of actual deaths.

The implementation consists of:

A Mortality Tracker: A reactive web interface (dashboard.html) for real-time visualization of estimated deaths.

The Research Framework: A detailed multi-pathway mortality model (methodology.md).

The Memorial License: A legal framework (v1.4) ensuring all derivative works remain anonymized and memorial-focused.

2. The LANA Methodology
The methodology addresses the systematic undercount of homeless child deaths, which often go unrecorded in mortality registries or coronial records.

The Multi-Pathway Model
Total deaths are calculated by aggregating six specific risk pathways:

Visible Deaths: SHS-connected deaths adjusted for a ~79% data linkage success rate.

SUDI: Sudden Unexpected Death in Infancy attributable to severe overcrowding.

Adolescent Suicide/OD: Hidden homeless youth (12–17) experiencing a 6.0× risk multiplier compared to housed peers.

FDV-Related: Deaths where housing barriers prevented escape from domestic violence.

Accident/Illness: Children (1–11) in hidden homelessness with reduced healthcare access.

Unlinked Deaths: Mortality occurring more than 12 months after the last service contact.

3. Developer Guide: Modification & Code Logic
The project is built using vanilla HTML5, CSS3, and JavaScript to ensure maximum portability and ease of audit.

Modifying the Mortality Logic
All mathematical logic is encapsulated in the MODEL_PARAMS object within dashboard.html. Developers should modify these values to reflect localized or updated research:

JavaScript
const MODEL_PARAMS = {
    baseEstimate: 169, // The central annualized death estimate
    lowerBound: 89,    // 95% Confidence Interval (Lower)
    upperBound: 251,   // 95% Confidence Interval (Upper)
    
    // Housing crisis multipliers adjust for worsening economic conditions
    housingCrisisMultiplier: {
        2024: 1.08,
        2025: 1.12,
        2026: 1.15 
    }
};
The Live Counter (updateLiveCounter)
The tracker calculates deaths-to-date with per-second precision using the following logic:

Pro-rating: It determines the number of seconds passed in the current year.

Frequency: It calculates a deathsPerSecond value based on the annualized central estimate.

Injection: The updateLiveCounter() function is called via setInterval every 1000ms to update the DOM without page refreshes.

4. Branding & Compliance (LANA License v1.4)
This project is governed by a Share-Alike reciprocity clause; any modifications must be re-released under the same LANA License.

The Structural Exception for Developers
To allow for easier integration into existing organizational websites, version 1.4 permits limited branding:

Permitted Branding: You may place your organization’s logo and name in the site-wide header and footer only.

Prohibited Branding: No individual names, researcher bios, or sponsor "shout-outs" may appear in the "About" section, page content, or promotional graphics.

Neutral Attribution: All projects must include the credit: "Derived from the LANA Methodology (https://www.beneaththesurface.au/lana-methodology)". No mention of "Beneath the Surface AU" is permitted in the public-facing attribution.