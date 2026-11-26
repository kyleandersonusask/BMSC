# CLAIMS: Michaelis-Menten and Lineweaver-Burk generator, with inhibitors

Every scientific claim the demo shows, with its source. The request is
`docs/requests/2026-10-11-enzyme-inhibition-mm-lb.md`.

**Status key**
- **TEXTBOOK**: standard result, stated in the cited textbooks and primary papers.
- **DERIVED**: algebra on a TEXTBOOK result. The derivation is given here, and it was checked numerically (section H).
- **STYLISED**: chosen by the demo (an idealisation, a noise model, a dial range). The demo must show the word
  "stylised" (or "idealised") next to it.

Sources are cited by short name or PMID. Full references and DOIs are in `SOURCES.md`. Textbooks are cited by edition
and chapter. Box and page numbers are marked "checker to confirm", because the books could not be opened here.

Prepared 2026-10-11 by the science intern. An Opus check against these sources is still required before Kyle sees the
demo (house rule 3).

**Symbols and units used by the demo**

| Symbol | Meaning | Unit |
|---|---|---|
| [S] | substrate concentration (free is taken to equal total, A2) | µM |
| [I] | inhibitor concentration (free is taken to equal total, A6) | µM |
| v | initial rate | µM/min |
| Vmax | maximum rate, = kcat [E]T | µM/min |
| Km | Michaelis constant | µM |
| Ki | dissociation constant of EI (inhibitor binding to free enzyme) | µM |
| Ki' | dissociation constant of ESI (inhibitor binding to the ES complex) | µM |
| α, α' | α = 1 + [I]/Ki, α' = 1 + [I]/Ki' (dimensionless) | - |
| 1/[S] | LB x-axis | µM⁻¹ |
| 1/v | LB y-axis | min/µM |

**Naming conventions differ between texts.** This demo uses Lehninger's names. A checker reading another source should map
them as follows.

| This demo (Lehninger) | Cleland 1963 (PMID 14021668) | Cornish-Bowden (*Fundamentals*; PMID 4206907) | Copeland (*Evaluation of Enzyme Inhibitors*) |
|---|---|---|---|
| Ki (EI) | Kis ("slope" constant) | Kic (competitive constant) | Ki |
| Ki' (ESI) | Kii ("intercept" constant) | Kiu (uncompetitive constant) | αKi |
| α = 1 + [I]/Ki | - | - | (Copeland's α is the *ratio* Ki'/Ki, a different quantity) |

Warning: Copeland's α is not Lehninger's α. The two are easy to confuse in a check.

---

## A. The Michaelis-Menten equation and its assumptions

| # | Claim shown | Status | Source |
|---|---|---|---|
| A1 | **v = Vmax[S] / (Km + [S])**. The curve is a rectangular hyperbola: it rises linearly at low [S] (v ≈ (Vmax/Km)[S]), reaches Vmax/2 at [S] = Km, and approaches Vmax as [S] grows. | TEXTBOOK | Lehninger 8e Ch. 6; Berg 9e Ch. 8; Michaelis & Menten 1913, translated by Johnson & Goody 2011 (PMID 21888353); Briggs & Haldane 1925 (PMID 16743508) |
| A2 | **Initial rates.** v is measured before significant product forms (a common working rule is less than about 10% of substrate converted), so the reverse reaction and product inhibition can be ignored, and [S] stays at its starting value. | TEXTBOOK | Lehninger 8e Ch. 6; Berg 9e Ch. 8; Assay Guidance Manual, Brooks et al. 2012 (PMID 22553875, checker to confirm); Copeland 2013 (chapter checker to confirm) |
| A3 | **[S] much greater than [E]T**, so the substrate bound in ES is negligible and free [S] ≈ total [S]. | TEXTBOOK | Lehninger 8e Ch. 6; Berg 9e Ch. 8; Briggs & Haldane 1925 (PMID 16743508) |
| A4 | **Steady state:** d[ES]/dt ≈ 0 during the measurement (Briggs & Haldane). Then **Km = (k₋₁ + k₂)/k₁**. Michaelis and Menten's original derivation assumed rapid equilibrium (k₂ much less than k₋₁), where Km reduces to the dissociation constant of ES, Ks = k₋₁/k₁. | TEXTBOOK | Briggs & Haldane 1925 (PMID 16743508); Johnson & Goody 2011 (PMID 21888353); Lehninger 8e Ch. 6 |
| A5 | **What Km means.** Always true: Km is the [S] at which v = Vmax/2. Only under rapid equilibrium is Km also the ES dissociation constant. **The demo must not say "Km measures affinity"** without this qualifier. | TEXTBOOK | Lehninger 8e Ch. 6; Berg 9e Ch. 8; Cornish-Bowden 4e |
| A6 | **Vmax = kcat[E]T.** The demo holds [E]T fixed, so Vmax is set directly by its dial. | TEXTBOOK | Lehninger 8e Ch. 6; Berg 9e Ch. 8 |
| A7 | **Reversible inhibitors at equilibrium, free [I] ≈ total [I].** The inhibitor binds and leaves fast compared with the measurement, and [E]T is much less than Ki, so inhibitor bound to enzyme does not deplete it. When [E]T is close to Ki ("tight binding"), these equations fail and the Morrison equation is needed. The demo's lowest Ki is 0.5 µM, so it assumes [E]T is in the low nM range (STYLISED: the enzyme concentration is not shown). | TEXTBOOK; STYLISED ([E]T not shown) | Morrison 1969 (PMID 4980133); Copeland 2013 Ch. 3 and the tight-binding chapter |
| A8 | **Single substrate, one active site, no cooperativity.** One hyperbola per assay. | STYLISED (model choice) | Lehninger 8e Ch. 6 |

## B. The Lineweaver-Burk (double-reciprocal) transform

| # | Claim shown | Status | Source |
|---|---|---|---|
| B1 | Taking reciprocals of A1 gives **1/v = (Km/Vmax)(1/[S]) + 1/Vmax**, a straight line in 1/v against 1/[S]. | TEXTBOOK | Lineweaver & Burk 1934 (JACS 56:658); Lehninger 8e Ch. 6, box on the double-reciprocal plot (box number checker to confirm; Box 6-1 in the 7th edition) |
| B2 | **Slope = Km/Vmax** (unit: min, since µM ÷ µM/min = min). | TEXTBOOK | as B1 |
| B3 | **y-intercept = 1/Vmax** (min/µM). | TEXTBOOK | as B1 |
| B4 | **x-intercept = −1/Km** (µM⁻¹). It lies to the left of the origin, outside the range of any real measurement, so it is reached by extrapolation. The demo draws the extrapolated part of each line faded (same dash as its series). | TEXTBOOK; STYLISED (faded extrapolation) | as B1 |
| B5 | The highest [S] gives the point nearest the y-axis, and the lowest [S] gives the point farthest to the right. | TEXTBOOK (reciprocal) | arithmetic |

## C. Inhibition types: what moves

General form for all four types (Lehninger's notation):
**v = Vmax[S] / (α Km + α'[S])**, so **Vmax,app = Vmax/α'** and **Km,app = Km α/α'**.
In LB form: **1/v = (α Km/Vmax)(1/[S]) + α'/Vmax**. The slope is multiplied by α and the intercept by α'.

| # | Type | Inhibitor binds | α, α' | Km,app | Vmax,app | Vmax/Km (initial slope of the MM curve) | MM picture | LB picture | Status | Source |
|---|---|---|---|---|---|---|---|---|---|---|
| C1 | **Competitive** | E only (Ki' → ∞) | α = 1 + [I]/Ki; α' = 1 | **Km(1 + [I]/Ki)**, rises | **Vmax**, unchanged | falls by α | curves reach the same plateau, but more slowly | slopes rise; **all lines meet on the y-axis at 1/Vmax** | TEXTBOOK | Lehninger 8e Ch. 6 (box on kinetic tests for inhibition mechanisms; Box 6-2 in the 7th edition, checker to confirm); Berg 9e Ch. 8; Segel 1975 Ch. 3; Cleland 1963 (PMID 14021668) |
| C2 | **Pure non-competitive** | E and ES equally (Ki = Ki') | α = α' = 1 + [I]/Ki | **Km**, unchanged | **Vmax/(1 + [I]/Ki)**, falls | falls by α | lower plateaus; the half-maximum is at the same [S] | slopes and intercepts both rise by α; **all lines meet on the x-axis at −1/Km** | TEXTBOOK | Lehninger 8e Ch. 6; Berg 9e Ch. 8; Segel 1975 Ch. 3 |
| C3 | **Uncompetitive** | ES only (Ki → ∞) | α = 1; α' = 1 + [I]/Ki' | **Km/(1 + [I]/Ki')**, falls | **Vmax/(1 + [I]/Ki')**, falls by the **same factor** | **unchanged** | lower plateaus; the curves overlap at low [S] | slope unchanged; **lines are parallel** | TEXTBOOK | Lehninger 8e Ch. 6; Berg 9e Ch. 8; Segel 1975 Ch. 3; Cornish-Bowden 1974 (PMID 4206907) |
| C4 | **Mixed** | E (Ki) and ES (Ki'), Ki ≠ Ki' | α = 1 + [I]/Ki; α' = 1 + [I]/Ki' | **Km α/α'**: rises if Ki < Ki', falls if Ki > Ki' | **Vmax/α'**, falls | falls by α | lower plateaus, and the half-maximum shifts | **lines meet at one point off both axes**: second quadrant if Ki < Ki', third quadrant if Ki > Ki' (section D) | TEXTBOOK; DERIVED (the point, D1) | Lehninger 8e Ch. 6; Segel 1975 Ch. 3; Cleland 1963 (PMID 14021668); Ring et al. 2014 (PMID 24523108); Copeland 2013 Ch. 3 |
| C5 | **"Non-competitive" is used loosely.** Many papers call any mixed inhibitor "non-competitive". The demo says "pure non-competitive" for Ki = Ki', and Lehninger treats it as a special case of mixed inhibition. | TEXTBOOK | Lehninger 8e Ch. 6; Cornish-Bowden 4e (inhibition chapter) |
| C6 | **The uncompetitive dial is Ki'.** For an uncompetitive inhibitor, the one constant is the ESI dissociation constant. The demo should label that dial **Ki'** (or "Ki' (binds ES)"), not Ki. For pure non-competitive, one dial sets Ki = Ki'. For mixed, two dials. | TEXTBOOK | as C3 |
| C7 | **Fold change** (shown in the table): Km,app/Km = α/α' and Vmax,app/Vmax = 1/α'. Uncompetitive: both equal 1/α'. Competitive: the Km fold is α and the Vmax fold is 1. Pure non-competitive: the Km fold is 1 and the Vmax fold is 1/α. | DERIVED (ratio of C1-C4) | algebra |

## D. Where the LB lines meet

| # | Claim shown | Status | Source |
|---|---|---|---|
| D1 | For two inhibitor concentrations (or one and zero), the LB lines from C (slope α Km/Vmax, intercept α'/Vmax) intersect at **x\* = −Ki/(Ki'·Km)** and **y\* = (1/Vmax)(1 − Ki/Ki')**. Derivation: setting the two lines equal gives x\* = −Δα'/(Δα·Km), where Δα = Δ[I]/Ki and Δα' = Δ[I]/Ki'. **The [I] cancels**, so the 0, low and medium lines all pass through **one common point**. This is the checkable claim. | DERIVED (numerically verified, H1) | Segel 1975 Ch. 3; Copeland 2013 Ch. 3 (as x = −1/(αKm), y = (1/Vmax)(1 − 1/α) in Copeland's α = Ki'/Ki) |
| D2 | **Competitive** (Ki' → ∞): x\* → 0, y\* → 1/Vmax: **on the y-axis.** | DERIVED from D1; TEXTBOOK | as C1 |
| D3 | **Pure non-competitive** (Ki = Ki'): x\* = −1/Km, y\* = 0: **on the x-axis.** | DERIVED from D1; TEXTBOOK | as C2 |
| D4 | **Uncompetitive** (Ki → ∞): the slopes are all equal, so the lines are **parallel** and never meet. | TEXTBOOK | as C3 |
| D5 | **Mixed, Ki < Ki'** (prefers free E, "competitive-leaning"): y\* > 0 and −1/Km < x\* < 0: the point is **in the second quadrant** (left of the y-axis, above the x-axis), and closer to the y-axis than −1/Km. | DERIVED from D1; TEXTBOOK | Segel 1975 Ch. 3; Copeland 2013 Ch. 3; Ring et al. 2014 (PMID 24523108) |
| D6 | **Mixed, Ki > Ki'** (prefers ES, "uncompetitive-leaning"): y\* < 0 and x\* < −1/Km: the point is **in the third quadrant** (below the x-axis). | DERIVED from D1; TEXTBOOK | as D5 |
| D7 | Because the meeting point is outside the measured range (x < 0), it is found by **extrapolating** the fitted lines. With noise on, the three fitted lines will not meet at one exact point. The demo should mark the *true* meeting point (from the dials) and let the fitted lines fall where they fall, and say which is which. | STYLISED (display rule) | follows from B4 |

## E. The table of apparent constants

| # | Claim shown | Status | Source |
|---|---|---|---|
| E1 | For each assay (0, low and medium [I]) the table shows the **true** Km,app and Vmax,app (from C1-C4 and the dials), the values **fitted** from the simulated points (by nonlinear least squares, G2), the values from the **LB line** (G1), and the fold change against the 0-[I] row. | DERIVED; method in G | C1-C7 |
| E2 | Each assay is fitted **on its own** to the plain MM equation, giving an apparent Km and Vmax per [I]. The demo does not fit Ki globally (that is a later lesson). | STYLISED (scope) | - |
| E3 | At Noise = 0, the fitted and LB columns must equal the true column to rounding (an acceptance test, G4). | DERIVED (exact data) | H2 |

## F. Statistics: why LB misleads, and what to show

| # | Claim shown | Status | Source |
|---|---|---|---|
| F1 | **LB distorts the error structure.** If v has error σ_v, then 1/v has error about σ_v/v². So the low-[S] points (small v) carry the largest error in 1/v, and they also sit farthest out on the 1/[S] axis, so they have the most leverage on the slope. An unweighted straight-line fit to LB is therefore dominated by the least reliable points. | TEXTBOOK | Wilkinson 1961 (PMID 13785321); Dowd & Riggs 1965 (PMID 14275146); Cleland 1967 (PMID 4881884); Lehninger 8e Ch. 6 (box on the double-reciprocal plot); Cornish-Bowden 4e |
| F2 | **Simulation studies found LB estimates the least reliable** of the common linear transforms. Tommasini et al. found LB "very imprecise and inaccurate" under constant absolute and constant relative error, with unweighted nonlinear least squares the most precise. Tseng & Hsu ranked LB last by sum of squared errors. Dowd & Riggs is the classic comparison (abstract not in PubMed; checker to confirm its conclusion from the full text). **Caveat:** this file's own simulation (H3) did *not* reproduce a large LB penalty under relative error for the demo's design (8 points, 0.2-10 Km, geometric spacing); see F5. The demo should cite the absolute-error case. | TEXTBOOK (primary studies); conflict noted | Dowd & Riggs 1965 (PMID 14275146); Tommasini et al. 1985 (PMID 3986669); Tseng & Hsu 1990 (PMID 2246896) |
| F3 | **Nonlinear least squares on v against [S] is preferred.** Weighted LB (weights proportional to v⁴ under constant absolute error) recovers the correct answer, but it is equivalent to fitting the hyperbola directly. | TEXTBOOK | Wilkinson 1961 (PMID 13785321); Cleland 1967 (PMID 4881884); Johnson 2013 (PMID 23850893) |
| F4 | **A real case:** a published Ki, re-fitted by nonlinear regression instead of LB, fell from 1.5 to 0.59 µM. (Optional caption material.) | TEXTBOOK (primary) | Schlosser 2016 (PMID 27177048) |
| F5 | **The noise model decides how strongly lesson 5 shows. Decided by Kyle 2026-10-15 (board q-uv-noise): "Absolute, % of each assay's Vmax,app" is the default; relative stays in the dropdown.** The request's noise dial is "% of v" (constant *relative* error). The simulation for this file (H3, true Km 10 µM) found that lesson 5 **shows only weakly under relative noise and strongly under absolute noise**. At 10% relative noise, the 5-95% range of fitted Km was 7.4-14.3 µM for unweighted LB, against 7.4-14.0 for an unweighted nonlinear fit and 8.0-12.6 for a relative-weighted nonlinear fit: LB was about 1.5 times wider than the correctly weighted fit, and no worse than an unweighted one. At an absolute SD of 5% of Vmax, the ranges were 4.7-39 µM for LB against 7.7-13.1 µM for the nonlinear fit, about 5 times wider for LB. Under relative noise, the visual claim in F1 still holds (the low-[S] points scatter most on the LB plot, because σ(1/v) = CV/v is largest where v is smallest), but the demo must not caption the LB *fit* as badly misleading unless the numbers on screen show it. The recommendation is in J1. | STYLISED (noise model); DERIVED (simulation, H3) | H3; Tommasini et al. 1985 (PMID 3986669) |
| F6 | **Non-positive simulated rates.** With absolute noise, a low-[S] point can come out at v ≤ 0, and then 1/v is undefined or negative. For the uninhibited assay at an absolute SD of 10% of Vmax, this happened for 171 of 24,000 simulated points (H3). For a strongly inhibited assay with the SD tied to the *uninhibited* Vmax, it happened for 1,186 of 24,000 points at only 2% (H4). The demo must handle it: redraw that point's noise (a truncated normal, labelled "stylised") or drop the point from the LB fit and say so. It must not silently clamp to a tiny v, because that makes a huge 1/v spike. | DERIVED (H3, H4); STYLISED (the handling) | H3, H4 |

## G. How the demo fits (the method the builders implement)

| # | Method | Status | Source |
|---|---|---|---|
| G1 | **LB panel: unweighted ordinary least squares of 1/v on 1/[S]**, one line per assay. Slope m and intercept b; Km,LB = m/b and Vmax,LB = 1/b. This is deliberately the textbook student method, *unweighted*, because that is what lesson 5 is about. A weighted LB fit (weights v⁴, or v² under relative error) would reproduce the nonlinear fit and erase the lesson. If b ≤ 0 (possible with noise), report "LB fit fails (intercept ≤ 0)" rather than a negative Vmax. | TEXTBOOK (method); STYLISED (choice of unweighted) | Lineweaver & Burk 1934; Wilkinson 1961 (PMID 13785321); Cleland 1967 (PMID 4881884) |
| G2 | **Table: nonlinear least squares of v against [S], by variable projection.** For a trial Km, let fᵢ = [S]ᵢ/(Km + [S]ᵢ). The best Vmax for that Km is closed-form: **Vmax(Km) = Σ vᵢ fᵢ / Σ fᵢ²**. The residual sum of squares is then a function of Km alone, and is minimised in one dimension: a coarse grid of about 200 steps in log Km, over [min[S]/100, 100·max[S]], then a golden-section refine of about 60 iterations around the best grid cell. This method cannot diverge, needs no starting guess and no library, and fits in about 30 lines of JavaScript. (Gauss-Newton or Levenberg-Marquardt would also work, but each needs a starting guess and can fail to converge.) Unweighted under absolute noise; under relative noise, the correct weights are 1/v_model², done by iterating. | TEXTBOOK (least squares); STYLISED (algorithm choice) | Cleland 1967 (PMID 4881884); Johnson 2013 (PMID 23850893); Cornish-Bowden 4e (statistics chapter) |
| G3 | **When the fit is not determined:** if the best Km lands on the edge of the search range, if the highest [S] in the series is below Km,app, or if the assay's rates are near the noise floor (J1, H4), show the fitted values with a flag ("not determined: [S] does not reach Km,app" or "rates too close to the noise") rather than a confident number. | STYLISED (display rule) | Cornish-Bowden 4e (experimental design: [S] should bracket Km); H4 |
| G4 | **Acceptance tests for the builders.** (a) Noise = 0: the fitted Km and Vmax and the LB Km and Vmax equal the true values to 4 significant figures, for every type and dial setting. (b) The three true LB lines pass through the D1 point to floating-point tolerance (D2-D6 cases). (c) Uncompetitive: the three true slopes are equal. (d) Same seed, same dials, same points. | DERIVED | H1, H2 |

## H. Checks run for this file (not part of the demo)

Script: `demos/enzyme-inhibition-mm-lb/checks/mm_checks.py`. Run it with `python -I demos/enzyme-inhibition-mm-lb/checks/mm_checks.py`
(about 7 minutes). It uses Python's `random.Random(7)` (Mersenne Twister) with Gaussian noise, 8 points at [S] = 0.2 to 10 Km
(geometric spacing), Km = 10 µM, Vmax = 100 µM/min and 3000 runs per row. A non-positive v is clamped to 0.001 and counted (the
demo must not do this; see F6). Run on 2026-10-11.

- **H1, intersection.** [I] = 0, 3 and 12. Every pair of lines met at the D1 point:
  (Ki, Ki') = (2, 8) at (−0.025, 0.0075) (second quadrant); (8, 2) at (−0.4, −0.03) (third quadrant, beyond −1/Km = −0.1);
  (5, 5) at (−0.1, 0) (x-axis); (5, ∞) at (0, 0.01) (y-axis, 1/Vmax). Uncompetitive slopes all 0.1 (parallel).
- **H2, exact data.** The variable-projection fit returned Km = 10.000 and Vmax = 100.000; the LB fit returned the same.
- **H3, noise, uninhibited assay.** Fitted Km (true 10), median [5%, 95%]. The weighted column uses weights 1/v_obs², an
  approximation to the correct 1/v_model². It is the right benchmark under relative noise, and the wrong one under absolute noise.

| Noise model | Nonlinear, unweighted | Nonlinear, weighted 1/v_obs² | LB, unweighted | v ≤ 0 (of 24,000) |
|---|---|---|---|---|
| relative, 5% of v | 10.05 [8.60, 11.81] | 10.03 [8.98, 11.16] | 9.98 [8.57, 11.83] | 0 |
| relative, 10% of v | 10.11 [7.43, 14.02] | 10.07 [7.96, 12.58] | 9.89 [7.41, 14.29] | 0 |
| absolute, SD 5% of Vmax | 10.04 [7.72, 13.14] | 10.78 [7.26, 20.96] | 9.72 [4.68, 38.97] | 2 |
| absolute, SD 10% of Vmax | 10.06 [5.92, 17.16] | 13.29 [5.49, 10000] | 7.04 [−43.5, 52.6] | 171 |

- **H4, noise, inhibited assay, SD tied to the uninhibited Vmax.** Pure non-competitive, Ki = Ki' = 5 µM, [I] = 50 µM, so
  Vmax,app = Vmax/11 and Km,app = 10 µM. Fitted Km (true 10):

| Absolute SD | Nonlinear, unweighted | LB, unweighted | v ≤ 0 (of 24,000) |
|---|---|---|---|
| 2% of uninhibited Vmax | 9.74 [2.91, 33.30] | 2.64 [−25.9, 31.0] | 1,186 |
| 5% of uninhibited Vmax | 6.47 [0.02, 489.75] | 0.55 [−24.3, 36.0] | 4,316 |

- **Scale note (derived, not simulated).** If the absolute SD is instead set as p% of *each assay's own* Vmax,app, every assay is a
  rescaled copy of the uninhibited case. Both the rates and the SD scale by Vmax,app/Vmax, and the fitted Km does not change under
  that scaling, so each assay behaves like the H3 absolute rows.

The skeptic should re-run this script before F5 and J1 drive a design change.

## I. Idealised or stylised, and what the demo must label

1. **Idealised kinetics:** initial rates only; [S] much greater than [E]T; steady state; one substrate; no cooperativity (A2-A4, A8).
2. **No substrate inhibition.** v never falls at high [S].
3. **No product inhibition** and no reverse reaction (initial rates).
4. **Rapid, reversible inhibitor binding with free [I] = total [I]** (no tight binding, A7). Irreversible and slow-binding
   inhibitors are out of scope.
5. **Noise model:** normal and seeded, with one stated model (F5, J1): "SD = p% of each assay's Vmax,app", "SD = p% of the
   uninhibited Vmax" or "p% of v". Real assays often have a mixture of error types, and the label must name the one used.
6. **Non-positive rates** are redrawn or dropped, and the demo says so (F6).
7. **Units:** concentrations in µM, rates in µM/min. The numbers are invented, not from a real enzyme.
8. **The LB line beyond the data is an extrapolation** (faded, B4).

## J. Design flags for the lead (not claims; decisions)

1. **Noise model (F5).** Kyle's request says "% of v" (relative), and under that lesson 5 shows only weakly (H3). Absolute
   noise shows it strongly. But tying the absolute SD to the *uninhibited* Vmax, the realistic instrument floor, wrecks the
   medium-[I] assay. At only 2% the inhibited points sit near the noise, 5% of them come out at v ≤ 0, and even the nonlinear
   fit's Km spans 2.9 to 33 µM (H4). So the table would mostly show noise, not inhibition. **Recommendation:** absolute noise
   within each assay, with SD = p% of that assay's own Vmax,app. It is labelled "stylised: noise scaled to each assay", it keeps
   lesson 5 strong in every row (scale note in H), and it keeps the inhibited rows fittable. A second option, "instrument floor",
   with the SD tied to the uninhibited Vmax, could teach why strongly inhibited assays need more enzyme or a more sensitive
   readout. Either way, this needs Kyle's call, because it changes his dial's meaning.
2. **Ill-conditioned extremes.** With Ki = 0.5 µM and [I] = 50 µM, α = 101. A competitive Km,app is then about 100 Km, while
   the [S] series reaches only 10 Km, so the medium-[I] assay never gets near saturation. Its fitted Vmax and Km are
   unreliable as soon as there is any noise (at zero noise the fit is still exact, H2). Options: let the [S] series follow the largest Km,app (stated on screen), or
   keep it fixed and show the G3 flag. Both are honest; the fixed series plus the flag also teaches assay design.
3. **The [S] series** should be geometrically spaced (equal steps in log [S]), and the demo should say so. Equal spacing in
   [S] crowds the LB plot near the y-axis; equal spacing in 1/[S] crowds the MM plot near zero.
4. **Dial labels:** Ki' for uncompetitive (C6); a single shared constant for pure non-competitive; both for mixed.
5. **The remix** (`_remix/molecular-04-michaelis-menten-bench.html`) fits by Hanes-Woolf ([S]/v against [S]). If any part of it
   is lifted, its fit must be replaced by G1 and G2. Hanes-Woolf is not what this demo claims to show.
