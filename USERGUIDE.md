📖 LANA Dashboard User Guide (v1.4)
This guide provides the instructions necessary to implement, modify, and maintain a LANA Mortality Project. This project is a legally protected digital memorial designed to center the human cost of childhood homelessness while removing institutional and personal vanity.

1. Project Philosophy & Governance
The LANA Project operates under a "Memorial-First" framework. In a digital landscape often dominated by "social responsibility" branding, this methodology mandates a return to pure focus on the victims.

The LANA License (v1.4) Compliance
Any developer or organization using this code must adhere to these strict legal conditions:

Mandatory Memorial Naming: The project cannot be named after an organization or a generic city; it must be named after a specific child lost to homelessness.

The Identity Veil: You are prohibited from listing the names of individual researchers, authors, or financial donors in the project’s main content or promotion.

Neutral Attribution: Credits must be functional, not personal. You must use the phrase: "Derived from the LANA Methodology (https://www.beneaththesurface.au/lana-methodology)".

The Structural Exception: While content must be anonymized, you are permitted to place your organizational logo and business name within the site-wide header and footer only to allow for standard website integration.

2. The Research Framework: Methodology
The core of this project is a Multi-Pathway Mortality Model. Research suggests that official administrative data linkage only captures about 23% of child deaths attributable to homelessness.

The Six Pathways of Mortality
The model estimates the "True Toll" by calculating risk across these distinct areas:

Visible (Linkage-Adjusted): Specialist Homelessness Services (SHS) connected deaths, adjusted for a ~79% linkage success rate.

SUDI in Hidden Homelessness: Infant deaths (0-1) occurring in overcrowded or unstable housing environments.

Adolescent Suicide/Overdose: A 6.0× mortality multiplier for hidden homeless youth (12-17) without service contact.

Accident/Illness: Deaths of hidden homeless children (1-11) often resulting from reduced healthcare access.

FDV-Related: Deaths where a lack of housing options prevented escape from family and domestic violence.

Unlinked Post-Support: Deaths occurring more than 12 months after a child’s last service contact.

3. Technical Implementation: The Code
The project is delivered as a lightweight, reactive dashboard (dashboard.html) powered by vanilla JavaScript.

Core Logic: The MODEL_PARAMS Object
All statistical assumptions are contained within a single JSON-like object at the top of the script:

baseEstimate: The central annual death count (default: 169).

housingCrisisMultiplier: A year-by-year factor that adjusts mortality estimates based on the intensifying housing crisis.

childPopulation: ABS-based estimates used to calculate the mortality rate per 100,000 children.

The Live Counter Calculation
The "live" feel of the dashboard is achieved through a time-precision calculation within the calculateYearToDate function:

Seconds Elapsed: The script determines how many seconds have passed since January 1st of the current year.

Deaths Per Second: It calculates the deaths per second based on the annualized central estimate.

Real-Time Injection: The result is injected into the #liveCounter element every 1,000 milliseconds.

4. Customization & Localization
Developers are encouraged to adapt this model for specific states, regions, or updated datasets.

How to Modify the Data
To localize the dashboard for a specific region:

Update baseEstimate: Change the baseline annual death estimate in MODEL_PARAMS to reflect localized research.

Update childPopulation: Input the specific child population numbers for your target area.

Pathway Breakdown: Adjust the progress bar widths and values in the breakdown-section of the HTML to match local proportions.

Visual Customization
You may modify the CSS variables in the :root section to match your organizational theme, provided the Identity Exclusion rules of Section 3.B in the license are maintained.

5. Deployment Checklist
Before taking your implementation live, you must verify the following:

[ ] Project Title: Is the site/repository named after a specific child?

[ ] Branding Check: Are all logos and organizational names restricted only to the header or footer?

[ ] Attribution: Does the footer contain the neutral URL link to lana-methodology.au?

[ ] Anonymity: Have all researcher names, donor lists, and "Lead by" credits been removed?

[ ] Data Integrity: Is the "Important Note" regarding statistical estimates visible to prevent data misinterpretation?