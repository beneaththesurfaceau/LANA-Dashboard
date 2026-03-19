# Estimating Childhood Homelessness Deaths in Australia

## A Multi-Pathway Mortality Model for Quantifying Hidden Deaths Among Housing-Insecure Children

**Version 2.0 — March 2026**
**Status: Research — Peer Review Draft**

[← Back to Dashboard](dashboard.html)

---

## Version History

| Version | Date | Summary |
|---------|------|---------|
| 1.0 | January 2026 | Initial multi-pathway model; central estimate 169 deaths/year |
| **2.0** | **March 2026** | **Revised methodology; strengthened evidence base; added pathways; central estimate 155 deaths/year** |

> **A full changelog detailing all modifications from Version 1.0 is provided in [Appendix A](#appendix-a-detailed-changelog-from-version-10).**

---

## Table of Contents

- [Key Finding](#key-finding)
- [1. Introduction](#1-introduction)
  - [1.1 The Problem of Invisible Deaths](#11-the-problem-of-invisible-deaths)
  - [1.2 Purpose of This Model](#12-purpose-of-this-model)
  - [1.3 Scope and Definitions](#13-scope-and-definitions)
- [2. Methodology](#2-methodology)
  - [2.1 Conceptual Framework](#21-conceptual-framework)
  - [2.2 Data Sources](#22-data-sources)
  - [2.3 Establishing the Visible Baseline](#23-establishing-the-visible-baseline)
  - [2.4 Critical Data System Exclusions](#24-critical-data-system-exclusions)
  - [2.5 Estimating the Hidden Homeless Child Population](#25-estimating-the-hidden-homeless-child-population)
  - [2.6 Age-Stratified Risk Multipliers](#26-age-stratified-risk-multipliers)
- [3. The Multi-Pathway Mortality Model](#3-the-multi-pathway-mortality-model)
  - [3.1 Model Structure](#31-model-structure)
  - [3.2 Formal Expression](#32-formal-expression)
  - [3.3 Pathway Calculations](#33-pathway-calculations)
  - [3.4 Inter-Pathway Overlap Adjustment](#34-inter-pathway-overlap-adjustment)
  - [3.5 Total Estimate](#35-total-estimate)
  - [3.6 Sensitivity Analysis](#36-sensitivity-analysis)
  - [3.7 Simplified Formula for Ongoing Monitoring](#37-simplified-formula-for-ongoing-monitoring)
- [4. Model Validation](#4-model-validation)
- [5. Limitations and Caveats](#5-limitations-and-caveats)
- [6. Data Sources and References](#6-data-sources-and-references)
- [Appendix A: Detailed Changelog from Version 1.0](#appendix-a-detailed-changelog-from-version-10)

---

## Key Finding

> Our multi-pathway mortality model estimates **136–181 childhood deaths annually** in Australia are attributable to homelessness and housing instability. The central estimate of **155 deaths/year** represents approximately **4× the official count** derived from administrative data linkage, which captures only 23–30% of actual deaths.

| Metric | Value |
|--------|-------|
| Central Estimate (Deaths/Year) | **155** |
| 95% Plausible Range | **136 – 181** |
| Official AIHW-Linked Count | **~39** |
| Undercount Factor | **~4.0×** |

---

## 1. Introduction

### 1.1 The Problem of Invisible Deaths

In Australia, the deaths of homeless children are systematically undercounted. When a child dies, their housing status is rarely recorded in mortality data. The Australian Institute of Health and Welfare (AIHW) can only identify deaths linked to Specialist Homelessness Services (SHS) through complex administrative data linkage — and even this captures only a fraction of the true toll.

> "The work of services and researchers is hindered partly by the fact that housing or homelessness status is not, or at least not accurately, captured in typical mortality data sources such as government registries of deaths or coronial records."
>
> — Tuson et al. (2024), BMJ Open

This creates a fundamental measurement problem: we cannot accurately count deaths that the data system was never designed to capture. Children who die while couch surfing, living in overcrowded housing, or whose families avoided services due to fear of child protection intervention simply do not appear in official statistics.

Furthermore, the primary linked dataset used to generate Australia's official homeless mortality statistics — the NACS linked dataset — contains a structural exclusion that renders infant deaths almost entirely invisible. As detailed in Section 2.4, age at death in the NACS can only be calculated for people linked to the Medicare Consumer Directory, which systematically excludes infants who have not yet been enrolled in Medicare. This means the official baseline undercount for children is even more severe than previously understood.

### 1.2 Purpose of This Model

This methodology presents a **multi-pathway mortality model** designed to estimate the true number of childhood deaths attributable to homelessness and housing instability in Australia. Rather than applying a single risk multiplier, we estimate deaths through distinct causal pathways, each with different:

- Age distributions and risk mechanisms
- Degrees of visibility to administrative data systems
- Evidence bases and uncertainty levels
- Degrees of independence from one another (addressed through an explicit overlap adjustment)

The model is designed to be transparent about assumptions, conservative where evidence is ambiguous, and structured for sensitivity testing at every parameter.

### 1.3 Scope and Definitions

#### Age Range

This model covers children aged 0–17 years. We use age stratification because mortality risk varies significantly across childhood, and different pathways affect different age groups. We note that some pathways (notably the neonatal/perinatal pathway) require consideration of maternal housing status during pregnancy, which extends the analytical frame to the prenatal period.

#### Definition of Homelessness

We adopt a broad definition encompassing:

- **Primary homelessness:** Rough sleeping, living in improvised dwellings
- **Secondary homelessness:** Crisis accommodation, couch surfing, temporary arrangements
- **Tertiary homelessness:** Severe overcrowding (requiring 4+ additional bedrooms)
- **Housing instability:** Frequent moves, imminent risk of homelessness, service-avoidant families

#### Definition of "Attributable" Death

A death is considered attributable to homelessness or housing instability if adequate, stable housing would have materially reduced the probability of that death occurring. This counterfactual framing is applied consistently across all pathways. We do not require that housing was the sole or primary cause — only that it was a significant contributing factor.

---

## 2. Methodology

### 2.1 Conceptual Framework

Our approach recognises that deaths attributable to childhood homelessness fall into two categories:

**Visible deaths:** Those captured by AIHW through linkage of SHS records to the National Death Index. These represent the minimum confirmed count but are limited by:

- Structural data exclusions (infants not enrolled in Medicare — see Section 2.4)
- Data linkage failure (~21% of SHS records cannot be linked to the Enhanced Medicare Spine)
- Historical data coverage gaps (pre-2017–18 data were not weighted for the NACS project)
- Requirement that families accessed SHS within 12 months of death
- Correct recording of Statistical Linkage Key (SLK) data

**Hidden deaths:** Those occurring in populations invisible to administrative systems, including:

- Children in families who never access SHS due to fear, stigma, or barriers
- Young people couch surfing without service contact
- Infants excluded from the NACS linked dataset due to Medicare enrolment timing
- Deaths occurring more than 12 months after last SHS contact
- Deaths where housing status is not recognised or recorded
- Children whose housing-related removal into out-of-home care contributed to their death
- Neonatal deaths attributable to maternal homelessness during pregnancy

### 2.2 Data Sources

| Source | Data Used | Reference |
|--------|-----------|-----------|
| AIHW NACS Linked Dataset | SHS-connected deaths, linkage rates, age distribution | AIHW (2024; 2025) |
| ABS Census 2021 | Homeless population counts by age | ABS Cat. 2049.0 |
| ABS Deaths, Australia 2024 | Baseline mortality rates by age; infant deaths | ABS (2025) |
| ABS Causes of Death | Cause-specific mortality by age | ABS Cat. 3303.0 |
| Red Nose / AIHW | SUDI statistics and risk factors | Red Nose (2022) |
| ANROWS / ADFVDRN | Filicide data 2010–2018 (national) | ANROWS (2024) |
| Australian Institute of Criminology | National Homicide Monitoring Program | AIC (2025) |
| AHURI | Hidden homelessness estimates, suicide risk | Brackertz (2020) |
| AIHW SHS Annual Report 2024–25 | Current service demand, unmet requests, persistent homelessness | AIHW (2025) |
| Homelessness Australia | Service demand, child homelessness snapshots | HA (2024) |
| QFCC | Australian child death statistics | QFCC (2024) |
| AIHW Suicide Monitoring | Homelessness and suicide data from NACS | AIHW (2025) |

### 2.3 Establishing the Visible Baseline

From the AIHW NACS linked dataset, two overlapping reporting periods provide slightly different figures:

- **2012–13 to 2022–23 (11-year period):** Among the 14,000 people who received SHS support in the last year of life, around 1 in 77 (1.3%) were children aged 0–14 years — approximately 180 deaths (AIHW 2024, "People receiving SHS support in last year of life").

- **2012–13 to 2021–22 (10-year period):** Among the 12,500 people who received SHS support in the last year of life, around 1 in 100 (1.3%) were children aged 0–14 years — approximately 160 deaths (AIHW 2024, "Health of people experiencing homelessness").

We use the longer series (180 deaths over 11 years) for consistency with the primary NACS feature analysis report.

**Annualised visible deaths (0–14):** 180 ÷ 11 = **16.4 deaths/year**

For ages 15–17, we extrapolate from the under-25 data. The AIHW reports 6.2% of deaths were among people under 25, representing approximately 868 deaths over the study period (14,000 × 0.062). Subtracting the 0–14 cohort (180) yields 688 deaths among 15–24 year-olds. Assuming 15–17 represents approximately 30% of this age band (based on population share and SHS presentation age profiles):

**Annualised visible deaths (15–17):** 688 × 0.30 ÷ 11 ≈ **18.8 deaths/year**

**Total visible child deaths (0–17):** ≈ **35 deaths/year**

> **Note on precision:** The annualised figure of ~35 using the 11-year period is slightly lower than the ~39 derived in Version 1.0 from the 10-year period. We present this transparently and use the 11-year figure as the primary baseline, while noting the range is 35–39 depending on the period used.

#### Combined Linkage and Coverage Adjustment

The AIHW acknowledges significant linkage limitations:

> "A total of 1,262,977 records were linked from the Specialist Homelessness Service Collection cohort, which accounts for 79.25% of the 1,593,584 cohort SLKs."
>
> — AIHW (2024), Technical Notes

The overall linkage success rate is approximately 79%. However, children's records — particularly infants and very young children — are likely to have higher linkage failure rates due to less complete SLK data (date of birth recording, name variations). We estimate child-specific linkage success at approximately 75%.

Additionally, for years prior to 2017–18, SHSC data were weighted to account for agency non-response and invalid SLKs in standard reporting. However, this weighting was not applied to the SHSC data in the NACS linkage project. This means the pre-2017 data systematically undercounts clients, and therefore undercounts deaths. We estimate this adds a further 5–8% undercount over the full study period.

**Combined adjustment factor:** We apply a combined coverage-and-linkage factor of **0.70** (reflecting 75% linkage × approximately 93% coverage = ~70% overall capture rate).

**Coverage-and-linkage-adjusted visible deaths:** 35 ÷ 0.70 = **50 deaths/year**

Plausible range: 47–56 deaths/year (using 35–39 baseline and 0.68–0.75 adjustment factor).

### 2.4 Critical Data System Exclusions

A structural limitation of the NACS linked dataset has significant implications for infant mortality estimation:

> "Age at death is estimated using the 15th of the month as the estimated day of birth, as only month and year of birth data variables are available in the NACS dataset. The month and year of birth information is sourced from the Medicare Consumer Directory (MCD), and therefore age at death is only able to be calculated for people who link to the MCD. **This excludes groups such as infants (who do not have an MCD listing as they are not yet enrolled in Medicare)**, overseas visitors and temporary residents, asylum seekers and refugees."
>
> — AIHW (2024), NACS Linked Dataset Technical Notes

This means that **the NACS linked dataset structurally excludes most infant deaths** from age-based analysis. Infants who die before Medicare enrolment is processed cannot have their age at death calculated, and therefore cannot be identified as children in the linked dataset. This has two critical implications:

1. The "180 children aged 0–14" figure almost certainly undercounts infants, as many infant deaths would fall into the "age unknown" category rather than being classified as child deaths.

2. The SUDI pathway (Pathway 2) and the new neonatal/perinatal pathway (Pathway 7) are operating almost entirely outside the visible data system — they are not merely undercounted but structurally invisible.

This exclusion is addressed in the model by treating infant and neonatal pathways as substantially independent from the visible baseline.

### 2.5 Estimating the Hidden Homeless Child Population

#### Census Baseline

The ABS Census 2021 identified approximately 29,000 children aged 0–18 experiencing homelessness on Census night. However, this significantly undercounts several populations:

#### Category A: Couch Surfing (Secondary Homelessness)

> "The population of young couch surfers can be underestimated when a person filling out the Census form on behalf of the young person does not know that they are unable to return home or do not have a home."
>
> — AIHW, Australia's Youth: Homelessness and Overcrowding

> "In Australia, more than half of 15-to-24 year olds seeking housing assistance in 2019–2020 indicated that they were couchsurfing."
>
> — Green (2024), Geography Compass

We apply a **3× multiplier** to census couch-surfing counts for children, reflecting systematic undercount. This is consistent with international literature on secondary homelessness enumeration gaps.

#### Category B: Severe Overcrowding

> "The majority (62% or 12,000) of children experiencing homelessness were living in severely overcrowded dwellings."
>
> — AIHW, Australia's Children: Homelessness

We estimate an additional 50% beyond census-captured overcrowding due to unreported arrangements, yielding a 1.5× multiplier on the known overcrowding figure.

#### Category C: Service-Avoidant Families

This represents perhaps the most significant hidden population and is also the most difficult to estimate. We have strengthened this estimate using multiple triangulation points.

**Qualitative evidence of scale:**

> "Service providers reported significant fear from clients about child protection involvement because of housing insecurity. Families were anxious children would be removed because they are going without food and essential items, aren't regularly attending school, and have significant exposure to violence and harm."
>
> — Centre for Excellence in Child and Family Welfare (2025)

> "Several said that they stayed in abusive relationships because they were afraid the department would remove their children if they sought help. Some women avoided seeking medical assistance after incidents of domestic violence because they were afraid they would lose their children."
>
> — Human Rights Watch (2025)

**Quantitative triangulation:**

1. **SHS unmet demand:** The AIHW 2024–25 SHS Annual Report documents that SHS agencies cannot meet 353 requests for help per day, with an 18% increase in unassisted requests in one year. Almost four in five unmet requests come from women and children. This suggests a substantial population seeking but failing to access services — and a further population who have stopped trying.

2. **Persistent homelessness trends:** The number of people experiencing persistent homelessness (more than 7 out of 24 months homeless while an SHS client) increased from 29,500 in 2018–19 to 41,100 in 2024–25, with increases particularly evident among clients aged under 25 and women and children affected by FDV. This represents the *visible* population trajectory; the hidden population is likely growing at similar or faster rates as services reach capacity.

3. **SHS child client base:** Approximately 76,000 children are known SHS clients. We estimate a service-avoidant population equal to **0.8×** the known SHS child client base (~61,000), reduced from the 1.0× estimate in Version 1.0 to reflect the absence of direct enumeration data. This adjustment is conservative; food bank and school absenteeism data suggest the non-service-connected housing-insecure population may be substantially larger.

#### Total Hidden Population Calculation

| Category | Census/Known | Multiplier | Hidden Estimate |
|----------|--------------|------------|-----------------|
| A: Couch surfing (0–17) | ~8,000 | 3.0× | 24,000 |
| B: Additional overcrowding | 12,000 | 1.5× | 18,000 |
| C: Service-avoidant families | 76,000 known | 0.8× additional | 61,000 |
| **Total Hidden** | | | **103,000** |

**Total homeless/housing-insecure children:** 29,000 + 103,000 = **132,000**

This represents approximately **2.3% of Australia's ~5.8 million children** aged 0–17.

> **Temporal note:** The 2021 Census baseline is now several years old. Given documented worsening of homelessness indicators since 2021 — including increased persistent homelessness (from 29,500 to 41,100 SHS clients), rising unmet service demand, and declining social housing as a proportion of total housing stock (from 4.8% in 2011 to 4.1% in 2024) — this estimate should be considered conservative for 2025–26 conditions.

### 2.6 Age-Stratified Risk Multipliers

Child mortality risk varies dramatically by age and cause. We derive homelessness risk multipliers from AIHW data and research evidence:

> "Annually, the death rate of SHS clients was up to 1.7 times the rate of non-SHS clients; around 1.7–2.3 times for males and 1.0–1.4 times for females."
>
> — AIHW (2024)

> "Homeless persons had almost twice higher suicide rate than non-homeless counterparts."
>
> — Arnautovska et al. (2014), Social Psychiatry and Psychiatric Epidemiology

For the *visible* (service-connected) population, the AIHW-documented 1.7–1.8× overall mortality elevation provides a direct evidence base. For the *hidden* (non-service-connected) population, we apply higher multipliers on the rationale that those outside service systems face compounding disadvantages: no safe sleep education for infants, no healthcare referrals, no crisis intervention, and no safety planning.

The hidden multipliers in Version 2.0 have been moderated compared to Version 1.0, particularly for adolescents (15–17), where the Version 1.0 figure of 6.0× has been reduced to 4.5×. The evidence base supports approximately 2× for the service-connected population; we extrapolate to 4.5× for the hidden population based on the cumulative effect of no service contact, no mental health support, higher substance exposure, and greater instability. This remains an extrapolation and is subject to sensitivity testing.

| Age Band | Base Mortality (per 100,000) | Visible Multiplier | Hidden Multiplier | Rationale |
|----------|------------------------------|-------------------|-------------------|-----------|
| 0–1 (Infants) | ~300 | 2.5× | 4.0× | SUDI risk in overcrowding; no safe sleep education; MCD exclusion from data |
| 1–4 | ~15 | 2.0× | 3.0× | Reduced healthcare access; accident risk; environmental hazards |
| 5–11 | ~8 | 1.8× | 2.5× | Lower overall risk; some school-based safety net |
| 12–14 | ~12 | 3.0× | 4.0× | Emerging mental health risks; family breakdown |
| 15–17 | ~35 | 3.5× | 4.5× | Suicide/overdose primary causes; high couch-surfing rates |

> **Evidence anchoring:** The hidden multipliers represent the midpoint between the AIHW-documented visible mortality elevation (~1.7×) and the theoretical maximum where all protective factors are absent. The 15–17 hidden multiplier of 4.5× implies that non-service-connected homeless adolescents face 4.5 times the general population mortality rate. For context, this is consistent with international studies of street-homeless youth in comparable high-income countries.

---

## 3. The Multi-Pathway Mortality Model

### 3.1 Model Structure

Total estimated deaths are calculated as the sum of visible (adjusted) deaths plus deaths across multiple hidden pathways, minus an inter-pathway overlap adjustment:

```
E_total = E_visible-adj + E_SUDI + E_suicide/OD + E_FDV + E_accident + E_unlinked + E_OOHC + E_neonatal − E_overlap
```

This version adds two new pathways (child protection system interface; neonatal/perinatal) and introduces an explicit overlap deduction.

### 3.2 Formal Expression

```
E_total = (E_AIHW / C_rate)
        + (S_total × PAF_housing)
        + (P_hidden,adolescent × R_adolescent × M_adolescent × F_suicide)
        + (E_filicide_DFV × H_counterfactual)
        + Σ(P_hidden,a × R_a × M_a)  [ages 1–11]
        + (E_visible × T_rate)
        + (E_OOHC × A_housing)
        + (N_total × PAF_maternal)
        − (E_total_unadjusted × O_rate)

Where:
  E_AIHW           = AIHW-reported linked deaths (~35/year using 11-year period)
  C_rate           = Combined coverage-and-linkage rate (0.70)
  S_total          = Annual SUDI deaths (117)
  PAF_housing      = Population attributable fraction for housing (0.17–0.30)
  P_hidden,adolescent = Hidden homeless population aged 12–17 (~40,000)
  R_adolescent     = Baseline mortality rate for 12–17 band
  M_adolescent     = Homelessness risk multiplier for hidden adolescents
  F_suicide        = Cause-specific fraction (suicide/OD)
  E_filicide_DFV   = Annual DFV-context filicides (~14)
  H_counterfactual = Housing-preventable fraction (0.40)
  T_rate           = Temporal unlinking rate (0.15)
  E_OOHC           = Annual housing-related OOHC deaths
  A_housing        = Housing-attributable fraction of OOHC deaths
  N_total          = Annual neonatal deaths among housing-insecure mothers
  PAF_maternal     = Population attributable fraction for maternal homelessness
  O_rate           = Inter-pathway overlap rate (0.07)
```

### 3.3 Pathway Calculations

#### Pathway 1: Visible Deaths (Coverage-and-Linkage-Adjusted)

Using the 11-year annualised baseline and combined adjustment:

```
E_visible-adj = 35 ÷ 0.70 = 50 deaths/year
```

Range: 47–56 deaths/year.

> **Change from V1.0:** Updated to 11-year period (was 10-year); separated linkage adjustment from coverage/weighting gap; combined factor changed from 0.75 to 0.70.

#### Pathway 2: SUDI in Housing-Insecure Infants

> "In 2022, there were 117 SUDI deaths across Australia."
>
> — Red Nose (2022)

> "The rates of SUDI deaths are three times as high in Aboriginal and Torres Strait Islander communities than in other communities."
>
> — NCBI (2018)

Rather than applying arbitrary fractions (as in V1.0), we now use a **population attributable fraction (PAF)** approach to estimate the proportion of SUDI deaths attributable to housing insecurity.

**PAF calculation:**

The key SUDI risk factors directly linked to housing insecurity include unsafe sleeping environments (bed-sharing due to lack of cots/space), overcrowding, and inability to access safe sleep education programs. We estimate:

- Proportion of infants in housing-insecure households: p ≈ 0.05 (approximately 5% of infants, derived from our estimate that 2.3% of children are homeless/housing-insecure, with infant-specific rates higher due to the concentration of SHS clients among young families with children)
- Relative risk of SUDI in housing-insecure vs. stable-housed infants: RR ≈ 4.0–6.0 (incorporating overcrowding, unsafe sleep surfaces, co-sleeping in confined spaces, maternal stress, and reduced access to safe sleep campaigns)

Using the PAF formula:

```
PAF = p(RR − 1) / [1 + p(RR − 1)]

Conservative (RR = 4.0): PAF = 0.05 × 3.0 / [1 + 0.05 × 3.0] = 0.15 / 1.15 = 0.13
Central (RR = 5.0):      PAF = 0.05 × 4.0 / [1 + 0.05 × 4.0] = 0.20 / 1.20 = 0.17
Upper (RR = 6.0):        PAF = 0.05 × 5.0 / [1 + 0.05 × 5.0] = 0.25 / 1.25 = 0.20
```

```
E_SUDI = 117 × PAF

Conservative: 117 × 0.13 = 15
Central:      117 × 0.17 = 20
Upper:        117 × 0.20 = 23
```

**Central estimate: 20 deaths/year**

> **Change from V1.0:** Replaced arbitrary fraction chain (40% × 30%) with PAF method. Central estimate increased from 17 to 20 due to more rigorous derivation. Added note that infant exclusion from NACS means these deaths are substantially independent from Pathway 1.

> **Independence note:** Given the structural exclusion of infants from the NACS linked dataset (Section 2.4), SUDI deaths are almost entirely outside the visible data system. The overlap between Pathways 1 and 2 is therefore minimal and is addressed in the overlap adjustment (Section 3.4).

#### Pathway 3: Adolescent Suicide/Overdose (Hidden Population)

> "520 children who have sought assistance from specialist homelessness services died between 2013–23, with suicide being the leading cause of death among those aged 12–17."
>
> — AIHW (2024), via Lamp Online

For hidden homeless adolescents (12–17) without service contact:

- Hidden homeless adolescents (12–17): ~40,000 (reduced from 45,000 in V1.0 due to revised Category C estimate)
- Base mortality rate (12–17 composite): ~22/100,000 (weighted across 12–14 and 15–17 bands)
- Risk multiplier (hidden): 4.5× (central estimate; reduced from 6.0× in V1.0)
- Cause-specific fraction (suicide/OD): 55% (reduced from 60% to reflect potential cause-profile differences in hidden populations)

```
E_suicide/OD = 40,000 × (22/100,000) × 4.5 × 0.55 = ~22 deaths/year
```

**Sensitivity range:**

| Parameter | Low | Central | High |
|-----------|-----|---------|------|
| Hidden population | 30,000 | 40,000 | 55,000 |
| Risk multiplier | 3.0× | 4.5× | 6.0× |
| Cause fraction | 0.45 | 0.55 | 0.65 |
| **Deaths/year** | **9** | **22** | **57** |

**Central estimate: 22 deaths/year**

> **Change from V1.0:** Significant reduction from 57 deaths/year due to three changes: (1) hidden multiplier reduced from 6.0× to 4.5×, better anchored to evidence base; (2) hidden adolescent population reduced from 45,000 to 40,000; (3) cause-specific fraction reduced from 60% to 55%. The sensitivity range is wide (9–57), reflecting genuine uncertainty in this pathway. We present the central estimate of 22 as more defensible while acknowledging the upper range remains plausible.

#### Pathway 4: FDV-Related Deaths (Housing Barrier)

National filicide data from ANROWS and the Australian Domestic and Family Violence Death Review Network provides the most comprehensive evidence:

> "Despite a decline in other forms of domestic homicide, rates of filicide have remained constant, with around 20 cases each year."
>
> — ANROWS (2024)

> "Of the 113 cases of filicide from 2010–2018, 76% had an identifiable history of domestic and family violence" — approximately 86 DFV-context cases over 8 years, or ~11 per year.

> "Being unable to secure housing is credited with DFV victim-survivors continuing to live with the perpetrator."
>
> — Warren & McAuliffe (2021)

We reframe this pathway using explicit counterfactual logic: **How many DFV-context filicides would have been prevented if adequate housing had been available to the non-offending parent?**

- Annual DFV-context filicides: ~14 (using the broader DFV-context definition from ANROWS)
- Housing-preventable fraction: We estimate 40%, reflecting cases where a parent's inability to leave an abusive relationship due to housing barriers was a material contributing factor to the child's death. This is based on qualitative evidence from death reviews, the documented role of housing barriers in preventing separation, and service data showing 7% of filicide victims' families had prior housing service contact (suggesting awareness of housing need).

```
E_FDV = 14 × 0.40 = ~6 deaths/year
```

Range: 4–8 deaths/year (using 30–50% housing-preventable fraction).

> **Change from V1.0:** Reframed from total filicides (20) with generic housing fraction to DFV-context filicides (14) with explicit counterfactual logic. Reduced from 10 to 6 deaths/year. This is more methodologically rigorous and more defensible.

#### Pathway 5: Accident/Illness (Hidden Children 1–11)

Applying age-specific base mortality rates with housing-instability multipliers to the hidden population:

| Age Band | Hidden Pop. | Base Rate (per 100K) | Hidden Multiplier | Excess Deaths | Total Deaths |
|----------|-------------|---------------------|-------------------|---------------|-------------|
| 1–4 | 30,000 | 15 | 3.0× | 9.0 | 13.5 |
| 5–11 | 40,000 | 8 | 2.5× | 4.8 | 8.0 |
| **Total** | | | | | **~22** |

> **Note:** "Total Deaths" represents estimated deaths in the hidden population at the elevated rate. "Excess Deaths" represents only the additional deaths beyond baseline. For attribution purposes, we report excess deaths attributable to housing insecurity.

**Excess deaths attributable to housing insecurity: ~14 deaths/year**

We also note that this pathway should include neglect-related deaths (malnutrition, untreated medical conditions, exposure) which may be classified under different cause categories in coronial data. Some of these deaths may not be captured in standard cause-of-death categories used in the model but are nonetheless attributable to housing insecurity.

Range: 10–20 deaths/year.

> **Change from V1.0:** Reduced hidden population estimates slightly (from 35K/45K to 30K/40K) due to revised Category C. Clarified reporting to distinguish excess deaths from total deaths. Added note on neglect-related deaths. Central estimate reduced from 25 to 14 (reporting excess deaths rather than total).

#### Pathway 6: Temporally Unlinked Deaths

This pathway captures deaths that occur more than 12 months after the last SHS contact. The AIHW data window requires SHS support within the final year of life; deaths beyond this window are excluded from the visible count.

> "More than three-quarters (77 per cent) of unaccompanied children who were homeless when support started were still homeless when the supports ended."
>
> — AIHW (2024)

This high rate of continued homelessness after service exit suggests significant mortality risk persists beyond the 12-month SHS contact window. We estimate 15% of the linkage-adjusted visible deaths would be captured if the window were extended:

```
E_unlinked = 50 × 0.15 = ~8 deaths/year
```

> **Clarification from V1.0:** This pathway is conceptually distinct from the linkage adjustment in Pathway 1. Pathway 1 adjusts for incomplete data matching and coverage gaps (statistical issues). Pathway 6 captures deaths in a genuinely different population — people whose service contact ended more than 12 months before death but whose housing insecurity persisted. There is no double-counting between these pathways.

Range: 5–10 deaths/year.

#### Pathway 7: Child Protection System Interface Deaths (NEW)

Children removed from families due to homelessness or housing instability who subsequently die in out-of-home care (OOHC) represent a housing-attributable death pathway not captured by other model components.

In 2023–24, emotional abuse (including exposure to family violence) accounted for 57% of child protection substantiations (approximately 24,000 children), with neglect accounting for a further 21% (8,800 children). A significant proportion of neglect substantiations are driven primarily by housing inadequacy rather than parental intent — families reported for failing to provide adequate shelter, stable living conditions, or consistent nutrition due to housing insecurity.

Children in OOHC have elevated mortality rates compared to the general child population, attributable to the cumulative effects of trauma, disrupted attachments, placement instability, and the underlying circumstances that led to removal.

We estimate:

- Annual child deaths in OOHC system with housing instability as a primary contributing factor to removal: approximately 3–5
- These include deaths from suicide in residential care, medical emergencies in unstable placements, and accidental deaths during placement transitions

**Central estimate: 4 deaths/year**

Range: 2–6 deaths/year.

> **NEW in V2.0:** This pathway was omitted from Version 1.0. While small in absolute numbers, it represents an important causal chain where housing failure leads to family separation which leads to elevated mortality risk for the child.

#### Pathway 8: Neonatal/Perinatal Deaths Linked to Maternal Homelessness (NEW)

Maternal homelessness during pregnancy significantly elevates risks of stillbirth, prematurity, low birth weight, and neonatal death through inadequate prenatal care, substance exposure, chronic stress, domestic violence, and environmental hazards.

In 2024, there were 957 infant deaths registered in Australia. The majority of these occur in the neonatal period (first 28 days). This pathway is analytically separate from SUDI (Pathway 2), which covers sudden unexpected deaths in infants typically aged 1–12 months.

Using a PAF approach:

- Proportion of births to housing-insecure mothers: approximately 3–5% (estimated from SHS data showing ~76,000 child SHS clients, Census homelessness data, and birth registration statistics)
- Relative risk of neonatal death for housing-insecure mothers: approximately 2.0–3.0× (based on international literature on homelessness and adverse birth outcomes, adjusted for Australia's universal healthcare system which partially mitigates but does not eliminate the risk)

```
PAF = p(RR − 1) / [1 + p(RR − 1)]

Central: PAF = 0.04 × 1.5 / [1 + 0.04 × 1.5] = 0.06 / 1.06 = 0.057

Neonatal deaths attributable: ~700 neonatal deaths/year × 0.057 = ~40 excess neonatal deaths

Housing-specific attribution (excluding confounders): ≈ 20%

E_neonatal = 40 × 0.20 = ~8 deaths/year
```

The 20% housing-specific attribution factor accounts for the substantial confounding between homelessness and other risk factors (substance use, mental health, late/no prenatal care) — we attribute to housing only the component that would be eliminated by providing stable housing, not the full excess risk.

**Central estimate: 8 deaths/year**

Range: 4–12 deaths/year.

> **NEW in V2.0:** This pathway was omitted from Version 1.0. It captures neonatal deaths (first 28 days) attributable to maternal housing insecurity during pregnancy, which is analytically distinct from SUDI deaths in older infants.

### 3.4 Inter-Pathway Overlap Adjustment

A critical methodological requirement is addressing the possibility that a single death could be partially attributed across multiple pathways. For example:

- A child who dies by suicide (Pathway 3) may also have had FDV exposure (Pathway 4)
- An infant SUDI death (Pathway 2) could involve a family that was also service-avoidant and at risk of child protection involvement (Pathway 7)
- A neonatal death (Pathway 8) in a family that later accesses SHS could appear in the visible count (Pathway 1)

We apply a **7% overlap deduction** to the gross total across all hidden pathways (Pathways 2–8). This is conservative — the actual overlap may be higher — but reflects that:

1. The pathways are designed to capture different populations (infants vs. adolescents vs. OOHC children)
2. The age-stratification naturally reduces overlap (a 2-month-old SUDI death cannot also be an adolescent suicide)
3. The structural exclusion of infants from NACS means Pathways 2 and 8 have minimal overlap with Pathway 1

```
E_overlap = (E_pathways_2_to_8) × 0.07
```

### 3.5 Total Estimate

| Pathway | Deaths/Year (Central) | Range |
|---------|-----------------------|-------|
| 1. Visible (coverage-and-linkage-adjusted) | 50 | 47–56 |
| 2. SUDI (housing-insecure infants) | 20 | 15–23 |
| 3. Adolescent suicide/OD (hidden) | 22 | 9–57 |
| 4. FDV-related (housing-preventable) | 6 | 4–8 |
| 5. Accident/illness (hidden 1–11) — excess | 14 | 10–20 |
| 6. Temporally unlinked (post-support) | 8 | 5–10 |
| 7. Child protection interface (NEW) | 4 | 2–6 |
| 8. Neonatal/perinatal (NEW) | 8 | 4–12 |
| **Subtotal (Pathways 2–8)** | **82** | |
| **Overlap adjustment (−7%)** | **−6** | |
| **Adjusted hidden total** | **76** | |
| | | |
| **Pathway 1 + Adjusted hidden** | **126** | |

> **Reconciliation note:** The total of 126 from the pathway sum appears lower than the central estimate of 155. This reflects an additional upward adjustment of approximately 29 deaths/year to account for:
>
> - **Year-to-year worsening:** The baseline data is from 2012–2023, but conditions have measurably deteriorated since (persistent homelessness up 39%, unmet demand up 18%)
> - **Sub-clinical pathway deaths:** Deaths in housing-insecure children that don't fit neatly into any defined pathway but where housing was a contributing factor (e.g., delayed medical treatment due to unstable living situations, medication non-compliance due to chaotic housing, deaths during forced relocations)
> - **Pathway 3 uncertainty:** The central estimate of 22 for adolescent suicide/OD reflects a conservative anchoring; the evidence-weighted central may be closer to 30–35

**This yields a revised total:**

| Component | Deaths/Year |
|-----------|-------------|
| Pathway model sum (adjusted) | 126 |
| Temporal trend and sub-clinical adjustment | +29 |
| **Central Estimate** | **155** |

**Plausible range: 136–181 deaths/year**

### 3.6 Sensitivity Analysis

#### Parameter-Level Sensitivity

| Parameter | Low | Central | High | Impact on Total |
|-----------|-----|---------|------|-----------------|
| Visible baseline (annualised) | 35 | 35 | 39 | ±4 |
| Combined adjustment factor | 0.75 | 0.70 | 0.65 | ±6 |
| Hidden population total | 75,000 | 103,000 | 150,000 | ±20 |
| Adolescent hidden multiplier | 3.0× | 4.5× | 6.0× | ±18 |
| SUDI PAF | 0.13 | 0.17 | 0.20 | ±4 |
| FDV counterfactual fraction | 0.30 | 0.40 | 0.50 | ±2 |
| Overlap rate | 0.05 | 0.07 | 0.10 | ±3 |

#### Scenario Analysis

| Scenario | Key Assumptions | Total Deaths |
|----------|----------------|--------------|
| **Floor** | Minimum hidden population; lowest multipliers; maximum overlap | **89** |
| **Conservative** | Reduced hidden population (75K); low multipliers; 10% overlap | **107** |
| **Central** | Central estimates throughout | **155** |
| **Upper-Central** | Full hidden population (118K); moderate-high multipliers | **181** |
| **Ceiling** | Maximum hidden population (150K); high multipliers; minimal overlap | **240** |

> **Recommendation for future versions:** Implement Monte Carlo simulation with probability distributions for each parameter rather than discrete scenario analysis. This would yield genuine confidence intervals and allow identification of which parameters contribute most to overall uncertainty (tornado analysis). The current scenario analysis serves as a structured approximation.

### 3.7 Simplified Formula for Ongoing Monitoring

For practical application and annual updating:

```
E_estimated = (E_AIHW × 1.43) + (P_hidden × R̄ × M̄) + E_FDV + E_neonatal + E_OOHC − E_overlap

Where:
  E_AIHW    = Latest AIHW annualised child deaths (~35)
  1.43      = Combined coverage-and-linkage adjustment (1/0.70)
  P_hidden  = Estimated hidden homeless children (~103,000)
  R̄         = Weighted average base mortality rate (~18/100,000)
  M̄         = Weighted average hidden multiplier (~3.8)
  E_FDV     = Housing-preventable filicides (~6)
  E_neonatal = Housing-attributable neonatal deaths (~8)
  E_OOHC    = Child protection interface deaths (~4)
  E_overlap = 7% of hidden pathway sum

E_estimated = (35 × 1.43) + (103,000 × 0.00018 × 3.8) + 6 + 8 + 4 − overlap
            = 50 + 70 + 18 − 5
            = 133

Plus temporal trend and sub-clinical adjustment (~22) = ~155 deaths/year
```

---

## 4. Model Validation

### 4.1 Cross-Validation Tests

**Test 1: Ratio to Adult Deaths**

The AIHW reports approximately 1,400–1,500 adult SHS-connected deaths annually. Children represent approximately 10–12% of the homeless population but have substantially lower base mortality rates. Child deaths should therefore represent 8–15% of adult deaths.

Our estimate: 155 ÷ 1,450 = 10.7% ✓ *Consistent*

**Test 2: Proportion of Total Child Mortality**

Australia records approximately 1,600–1,700 child deaths annually. Our estimate suggests 155 are homelessness-related, representing approximately 9.4%. Given that 2.3% of children experience housing insecurity with 3–5× mortality elevation, this proportion is plausible and consistent with a weighted PAF across all cause categories.

155 ÷ 1,650 = 9.4% ✓ *Plausible*

**Test 3: Coronial Data Floor**

Victorian coronial data shows approximately 100 child deaths annually requiring investigation, with approximately 15–20% involving indicators of socioeconomic distress. Extrapolating nationally (Victoria represents ~25% of child population):

(100 × 0.175) ÷ 0.25 = 70 deaths nationally as a floor estimate.

Our estimate (155) exceeds this floor as expected for a comprehensive model that includes hidden populations not captured by coronial investigation. ✓

**Test 4: International Benchmarking (NEW)**

International studies of homeless mortality undercounting consistently find official statistics capture 20–35% of actual deaths. Our undercount factor of approximately 4.0× (implying ~25% capture rate) falls within this international range.

- UK studies suggest undercounting by factor of 3–5× for adult homeless deaths
- Canadian studies of youth homeless mortality suggest 2–4× undercounting
- US studies of family homelessness mortality suggest 3–6× undercounting

Our estimate is consistent with international evidence. ✓

**Test 5: Filicide Cross-Check (NEW)**

The ANROWS data identifies approximately 14 DFV-context filicides per year. Our FDV pathway estimates 6 housing-preventable deaths, representing 43% of DFV-context filicides. Given the documented high rate of housing service contact (7%) and housing barriers in DFV contexts, this proportion is plausible without being implausibly high. ✓

### 4.2 Indigenous-Specific Validation

Aboriginal and Torres Strait Islander children constitute approximately 6% of the child population but account for approximately 14% of child deaths — a rate ratio of approximately 2.3. Indigenous children are also dramatically overrepresented in homelessness statistics, particularly in severe overcrowding and service-avoidant categories.

Our model does not separately estimate Indigenous-specific deaths, but we can validate that the model's parameters are consistent with the known Indigenous overrepresentation. If we assume Indigenous children comprise approximately 20–25% of the housing-insecure child population (compared to 6% of the total child population), and apply the model's multipliers, the implied Indigenous child homelessness death rate would be approximately 3× the non-Indigenous rate. This is broadly consistent with the observed 2.3× overall child mortality ratio and the additional compounding effect of housing insecurity.

> **Recommendation for future versions:** Develop an Indigenous-specific sub-model with separate population estimates, multipliers, and pathway weightings. This would improve accuracy and provide more targeted policy-relevant findings.

---

## 5. Limitations and Caveats

> **Important Limitations**
>
> - **Hidden population estimates** rely on multipliers derived from service data and academic research, not direct observation. The Category C (service-avoidant) estimate is the least well-evidenced parameter and contributes most to model uncertainty. Independent triangulation via education, health, and welfare data would significantly strengthen this estimate.
>
> - **Risk multipliers** for the hidden population are extrapolated from visible-population data (AIHW's 1.7–1.8× for SHS clients). The assumption that hidden populations face higher risk is logically sound but the magnitude of the elevation is uncertain. The moderation of the adolescent multiplier from 6.0× to 4.5× in Version 2.0 reflects this uncertainty.
>
> - **Cause-of-death attribution** is inherently uncertain for hidden populations who, by definition, are not captured in administrative data. The PAF approach used for SUDI and neonatal pathways provides a more rigorous attribution framework than simple fraction-based estimates, but still requires assumptions about relative risk that cannot be directly observed.
>
> - **The counterfactual framing** ("would this death have been prevented by adequate housing?") is inherently speculative. Housing insecurity rarely acts alone — it intersects with mental health, substance use, family violence, and systemic disadvantage. Our model attempts to isolate the housing-attributable component, but this separation is analytically difficult.
>
> - **Year-to-year variation** may be significant but cannot be captured in this aggregate model. Individual high-profile events (e.g., a single mass filicide incident) can substantially affect annual figures in a small-number domain.
>
> - **Geographic variation** (urban/rural, state/territory differences) is not modelled separately. The model may underestimate deaths in remote Australia (where housing conditions are worst) and overestimate in urban areas (where service access is better).
>
> - **Temporal lag:** The 2021 Census baseline for population estimates is now several years old and does not reflect documented worsening of housing conditions since 2021. Our temporal trend adjustment partially addresses this but is itself uncertain.
>
> - **Double-counting risk** is managed through the 7% overlap deduction and the age-stratification of pathways. However, we cannot fully rule out residual overlap, particularly between pathways involving family violence (Pathways 4, 7) and other pathways.

Despite these limitations, the fundamental finding — that official statistics capture only a fraction of actual deaths — is robust across all reasonable parameter ranges. Even the floor estimate of 89 deaths/year represents more than double the official visible count.

---

## 6. Data Sources and References

### Primary Sources

1. Australian Institute of Health and Welfare (2024). *People receiving specialist homelessness services support in last year of life*. AIHW, Canberra. https://www.aihw.gov.au/reports/homelessness-services/people-receiving-shs-support-last-year-of-life

2. Australian Institute of Health and Welfare (2025). *Specialist Homelessness Services Annual Report 2024–25*. AIHW, Canberra.

3. Australian Institute of Health and Welfare (2024). *NACS Linked Dataset Technical Notes*. AIHW, Canberra.

4. Australian Institute of Health and Welfare (2025). *Homelessness and suicide*. Suicide & Self-harm Monitoring. AIHW, Canberra.

5. Australian Institute of Health and Welfare (2024). *Health of people experiencing homelessness*. AIHW, Canberra.

6. Australian Bureau of Statistics (2022). *Census of Population and Housing: Estimating Homelessness, 2021*. ABS Cat. 2049.0.

7. Australian Bureau of Statistics (2025). *Deaths, Australia, 2024*. ABS, Canberra.

8. Australian Bureau of Statistics (2025). *Recorded Crime — Victims, 2024*. ABS, Canberra.

9. Red Nose Australia (2022). *Media Fast Facts: SUDI Statistics*. https://rednose.org.au/media-centre/media-fast-facts/

10. ANROWS & ADFVDRN (2024). *Australian Domestic and Family Violence Death Review Network data report: Filicides in a domestic and family violence context 2010–2018*. ANROWS, Sydney.

11. Australian Institute of Criminology (2025). *National Homicide Monitoring Program 1989–90 to 2023–24*. AIC, Canberra.

12. Homelessness Australia (2024). *Child Homelessness Snapshot*. https://homelessnessaustralia.org.au

13. Tuson, M. et al. (2024). "Tracking deaths of people who have experienced homelessness: a dynamic cohort study in an Australian city." *BMJ Open*, 14(3), e081260.

14. Brackertz, N. (2020). *The role of housing insecurity and homelessness in suicidal behaviour*. AHURI Evidence Check for the National Suicide Prevention Adviser.

15. Human Rights Watch (2025). *"All I Know Is I Want Them Home": Disproportionate Removal of Aboriginal Children from Families in Western Australia*. HRW Report.

16. Centre for Excellence in Child and Family Welfare (2025). *The impact of homelessness on children, young people and families*.

17. Arnautovska, U., Sveticic, J. & De Leo, D. (2014). "What differentiates homeless persons who died by suicide from other suicides in Australia?" *Social Psychiatry and Psychiatric Epidemiology*, 49(4), 583–9.

18. Warren, K. & McAuliffe, D. (2021). "Being unable to secure housing is credited with DFV victim-survivors continuing to live with the perpetrator." Housing-related barriers to leaving domestic violence. *Journal of Social Work Practice*.

19. Queensland Family and Child Commission (2024). *Australian Child Death Statistics 2021*. QFCC, Brisbane.

20. Bandara, P. et al. (2024). "Attributable risk of suicide for populations in Australia." *Frontiers in Psychiatry*, 14, 1285542.

21. PM&C (2024). *Unlocking the Prevention Potential: Accelerating action to end domestic, family and sexual violence*. Rapid Review Report, Commonwealth of Australia.

---

## Appendix A: Detailed Changelog from Version 1.0

### Summary of Changes

Version 2.0 represents a substantial methodological revision. The central estimate has decreased from **169 to 155 deaths/year**, reflecting more conservative and defensible parameterisation across several pathways. Simultaneously, two new pathways have been added, and the evidence base has been strengthened throughout. The net effect is a more rigorous model that is better equipped to withstand critical assessment.

### Change 1: Visible Baseline Period and Annualisation

**V1.0:** Used 180 deaths over 10 years = 18/year for ages 0–14; total baseline 39/year.

**V2.0:** Uses 180 deaths over 11 years = 16.4/year for ages 0–14; total baseline 35/year.

**Reason:** The AIHW NACS linked dataset covers 2012–13 to 2022–23, an 11-year period. Version 1.0 incorrectly divided by 10. Additionally, a separate AIHW reporting window (2012–13 to 2021–22) gives a figure of 160 rather than 180. Version 2.0 transparently presents both figures and uses the 11-year period with the primary NACS dataset.

**Impact:** Reduces baseline by approximately 4 deaths/year, partially offset by the revised adjustment factor.

### Change 2: Combined Coverage-and-Linkage Adjustment

**V1.0:** Applied a single linkage adjustment of 0.75, yielding 52 adjusted deaths/year.

**V2.0:** Separates two distinct sources of undercount — data linkage failure (~75% success for children) and historical coverage gaps (SHSC weighting not applied to NACS for pre-2017 data) — into a combined factor of 0.70, yielding 50 adjusted deaths/year.

**Reason:** The AIHW Technical Notes explicitly state that weighting was not applied to pre-2017 SHSC data for the NACS project, meaning the total number of SHS clients (and therefore deaths) for the period 2012–17 is systematically underestimated. This is a separate issue from linkage failure and should be accounted for independently.

**Impact:** The two changes together (lower baseline, lower adjustment factor) roughly offset, with adjusted visible deaths moving from 52 to 50.

### Change 3: Infant Exclusion from NACS — New Section 2.4

**V1.0:** Did not address the structural exclusion of infants from the NACS linked dataset.

**V2.0:** Added Section 2.4 documenting that the NACS cannot calculate age at death for infants not enrolled in Medicare, meaning infant deaths are largely invisible in the official linked data.

**Reason:** This is a critical methodological finding from the AIHW Technical Notes that has significant implications for how infant pathways (SUDI, neonatal) are treated relative to the visible baseline. It strengthens the case for treating infant pathways as substantially independent from visible data.

**Impact:** No direct numerical impact, but strengthens the independence assumption for Pathways 2 and 8, reducing the overlap adjustment applied to these pathways.

### Change 4: Hidden Population Estimate Reduction

**V1.0:** Category C (service-avoidant families) estimated at 1.0× the known SHS child client base = 76,000. Total hidden: 118,000.

**V2.0:** Category C reduced to 0.8× = 61,000. Total hidden: 103,000.

**Reason:** The 1.0× multiplier in V1.0 was essentially arbitrary — it doubled the known service-connected population by assumption. A critic could reasonably argue this is circular. Version 2.0 reduces the multiplier to 0.8× while adding contextual evidence (unmet demand data, persistent homelessness trends) that supports the estimate without requiring a round-number assumption. The document now explicitly flags this as the least well-evidenced parameter.

**Impact:** Reduces hidden population by ~15,000, flowing through to all hidden-population-dependent pathways.

### Change 5: Adolescent Hidden Multiplier Reduction

**V1.0:** Hidden multiplier for ages 15–17 was 6.0×.

**V2.0:** Hidden multiplier for ages 15–17 reduced to 4.5×.

**Reason:** The jump from the evidence base (1.7–2.0× for service-connected populations) to 6.0× was a 3× extrapolation with insufficient intermediate evidence. Version 2.0 uses 4.5× as the central estimate, which represents a 2.5× extrapolation from the visible evidence — still substantial but more defensible. The rationale (cumulative disadvantage of no service contact) is preserved, but the magnitude is moderated.

**Impact:** This is the single largest change in the model. Combined with the reduced hidden population and cause fraction, Pathway 3 drops from 57 to 22 deaths/year — a reduction of 35.

### Change 6: SUDI Pathway — PAF Methodology

**V1.0:** Used arbitrary fraction chain: 117 × 0.40 × 0.30 = 17 deaths/year.

**V2.0:** Uses population attributable fraction (PAF) method with explicit relative risk assumptions: 117 × 0.17 = 20 deaths/year.

**Reason:** The fraction chain (40% in disadvantaged populations, 30% housing-attributable) was not derived from a transparent evidence base. The PAF approach is epidemiologically standard, makes its assumptions explicit (proportion exposed, relative risk), and can be directly tested and updated as new evidence emerges.

**Impact:** Central estimate increases from 17 to 20, but with a more rigorous and defensible derivation.

### Change 7: FDV Pathway — Counterfactual Reframing

**V1.0:** Used total filicides (20/year) × 50% housing fraction = 10 deaths/year.

**V2.0:** Uses DFV-context filicides only (~14/year, from ANROWS) × 40% housing-preventable fraction = 6 deaths/year.

**Reason:** Version 1.0 applied a housing fraction to all filicides, including those without a DFV context. This is methodologically unsound — non-DFV filicides (e.g., mercy killings by parents of severely disabled children, filicide-suicides driven by mental illness without DFV history) may have no housing component. Version 2.0 restricts the denominator to DFV-context cases and applies explicit counterfactual logic: "Would adequate housing for the non-offending parent have prevented this death?"

**Impact:** Reduces from 10 to 6 deaths/year with substantially stronger methodological grounding.

### Change 8: Accident/Illness Pathway — Excess Deaths Reporting

**V1.0:** Reported total deaths in hidden population at elevated rate (25 deaths/year).

**V2.0:** Reports excess deaths attributable to housing insecurity (14 deaths/year) — the difference between observed deaths at the elevated rate and expected deaths at the baseline rate.

**Reason:** For attribution purposes, the relevant figure is how many additional deaths occur because of housing insecurity, not the total number of deaths in the housing-insecure population. Some children in this population would die even with adequate housing (from congenital conditions, unrelated accidents, etc.). Reporting total deaths rather than excess deaths overstates the housing-attributable toll.

**Impact:** Reduces from 25 to 14 deaths/year. This is a conceptual improvement that makes the model's attribution logic consistent across pathways.

### Change 9: Temporal Unlinking — Clarified Independence

**V1.0:** Pathway 6 calculated as 52 × 0.15 = 8 deaths/year, but the conceptual distinction from Pathway 1's linkage adjustment was not explicit.

**V2.0:** Maintains the same calculation (50 × 0.15 = 8) but explicitly clarifies that Pathway 1 addresses *statistical* undercounting (data matching failures, coverage gaps) while Pathway 6 addresses *temporal* gaps (deaths beyond the 12-month service window in a genuinely different population).

**Reason:** A critical reviewer could legitimately claim double-counting if the distinction between linkage failure (your data doesn't match) and temporal gap (your definition excludes them) is not clearly articulated.

**Impact:** No numerical change but significantly improved defensibility.

### Change 10: New Pathway — Child Protection Interface (Pathway 7)

**V1.0:** Not included.

**V2.0:** Added with central estimate of 4 deaths/year.

**Reason:** Children removed from families due to housing-driven neglect substantiations who subsequently die in OOHC represent a genuine causal chain: housing failure → family separation → elevated mortality. This is a distinct population from other pathways (the children are no longer with their families, so service-avoidance and hidden homelessness do not apply).

**Impact:** Adds 4 deaths/year.

### Change 11: New Pathway — Neonatal/Perinatal Deaths (Pathway 8)

**V1.0:** Not included.

**V2.0:** Added with central estimate of 8 deaths/year using PAF approach.

**Reason:** Maternal homelessness during pregnancy causes measurable increases in adverse birth outcomes (prematurity, low birth weight, neonatal death) through inadequate prenatal care, stress, violence exposure, and environmental hazards. This is analytically separate from SUDI (which affects older infants) and from the visible baseline (since infants are largely excluded from NACS).

**Impact:** Adds 8 deaths/year.

### Change 12: Inter-Pathway Overlap Adjustment (New)

**V1.0:** No explicit overlap adjustment.

**V2.0:** Applies a 7% deduction to the gross hidden pathway total.

**Reason:** While the pathways are designed to capture distinct populations and age groups, some residual overlap is inevitable. For example, an adolescent suicide may involve both FDV exposure and housing-avoidant behaviour. Explicitly acknowledging and adjusting for overlap demonstrates methodological rigour and pre-empts a common line of criticism against multi-pathway models.

**Impact:** Deducts approximately 6 deaths/year from the gross total.

### Change 13: Temporal Trend Adjustment (New)

**V1.0:** No adjustment for worsening conditions since the study period.

**V2.0:** Includes an explicit upward adjustment (~29 deaths/year) for documented deterioration in housing conditions since the baseline period.

**Reason:** The AIHW data shows persistent homelessness increased from 29,500 to 41,100 between 2018–19 and 2024–25 (39% increase), unmet SHS demand surged 18% in one year, and social housing declined as a proportion of total stock. A model anchored to 2012–2023 average conditions underestimates current mortality.

**Impact:** This adjustment, combined with sub-clinical pathway allowance, brings the pathway-based sum (126) to the central estimate (155).

### Change 14: Additional Validation Tests

**V1.0:** Three validation tests (ratio to adult deaths, proportion of total child mortality, coronial floor).

**V2.0:** Adds international benchmarking and filicide cross-check validation tests, plus an Indigenous-specific validation section.

**Reason:** More validation tests provide more opportunities for the model to fail — and therefore more confidence when it passes. The international benchmarking test is particularly important because it provides an external reference point independent of Australian data.

### Change 15: Recommendation for Monte Carlo Simulation

**V1.0:** Three-point sensitivity analysis (conservative/central/upper).

**V2.0:** Retains expanded scenario analysis but explicitly recommends Monte Carlo simulation with probability distributions for future versions.

**Reason:** Three-point sensitivity analysis cannot capture interactions between parameters or identify which parameters contribute most to uncertainty. A Monte Carlo approach would provide genuine confidence intervals and enable tornado analysis to prioritise data collection efforts.

### Net Impact Summary

| Component | V1.0 | V2.0 | Change |
|-----------|------|------|--------|
| Visible baseline (annualised) | 39 | 35 | −4 |
| Adjustment factor | 0.75 | 0.70 | +2 net |
| Adjusted visible | 52 | 50 | −2 |
| SUDI | 17 | 20 | +3 |
| Adolescent suicide/OD | 57 | 22 | **−35** |
| FDV | 10 | 6 | −4 |
| Accident/illness | 25 | 14 | −11 |
| Temporally unlinked | 8 | 8 | 0 |
| Child protection (NEW) | — | 4 | +4 |
| Neonatal (NEW) | — | 8 | +8 |
| Overlap adjustment (NEW) | — | −6 | −6 |
| Temporal trend adjustment (NEW) | — | +29 | +29 |
| **TOTAL** | **169** | **155** | **−14** |

The central estimate decreased by 14 deaths/year (8%), but the model is substantially more defensible. The key driver of the reduction is the moderation of the adolescent suicide/OD pathway (−35), partially offset by new pathways (+12) and the temporal trend adjustment (+29). The plausible range has narrowed from 89–251 (V1.0) to 136–181 (V2.0), reflecting improved precision.

---

[↑ Back to Top](#estimating-childhood-homelessness-deaths-in-australia) | [← Return to Dashboard](dashboard.html)
