# SOURCES: Michaelis-Menten and Lineweaver-Burk generator, with inhibitors

## Parts

| Part | Version | Licence | Where | Use |
|---|---|---|---|---|
| uPlot | 1.6.32 | MIT | `lib/vendor/uplot-1.6.32/` (`uPlot.iife.min.js`, `uPlot.min.css`, `LICENSE`) | the Michaelis-Menten plot (left) and the Lineweaver-Burk plot (right) |
| Remix: Michaelis-Menten Bench | 2026-10-11 | the purchased set's terms (Kyle to check before any copy leaves the shelf) | `OneDrive - University of Saskatchewan\Claude\Style - Forever\_remix\molecular-04-michaelis-menten-bench.html` | **parts candidate only, if used**: the light/dark token pattern and the Vmax and Km guide lines on the saturation plot |

- uPlot is the **unmodified** npm browser build. The fetch and integrity record is in `lib/vendor/README.md`, and the SHA-256 of
  each file is in `lib/vendor/SHA256SUMS`. Inline it into `index.html` with
  `python tools/inline.py demos/enzyme-inhibition-mm-lb/src.html demos/enzyme-inhibition-mm-lb/index.html`. Each inlined block
  starts with a comment `/* inlined: lib/vendor/... */`. The MIT notice travels with the inlined code: keep the licence header,
  or add the `LICENSE` text as a comment beside it.
- **The remix.** It is a stylised particle bench (a 2-D chamber, a VU meter and a point trace), not a plotting tool. Its
  provenance comment lists four set components: `particles-physics/04-bouncing-balls.html`, `audio-visualizers/04-vu-meter.html`,
  `inputs-switches/03-spring-stepper.html` and `micro-dataviz/04-sparkline-dot.html`. If a builder lifts anything from the remix,
  add the set component behind it to this table by `theme/file`. Rewrite it for the demo; never paste it in whole (house rule 4).
  **Its fit is Hanes-Woolf ([S]/v against [S]).** That fit must not be carried over: this demo fits by unweighted LB for the LB
  panel and by nonlinear least squares for the table (CLAIMS.md G1-G2).
- No other set component or `lib/` part is used yet. Builders add any they use to this table.
- All numbers are invented (dial values). No published dataset and no student data are used.

## Textbooks

The books could not be opened here. Box and page numbers are left for the checker, as CLAIMS.md marks them.

| Reference | Used for |
|---|---|
| Nelson DL, Cox MM. *Lehninger Principles of Biochemistry*, 8th ed. New York: Macmillan Learning (W.H. Freeman), 2021. Ch. 6, "Enzymes": the section on enzyme kinetics, the box on the double-reciprocal plot (Box 6-1 in the 7th ed., 2017) and the box on kinetic tests for inhibition mechanisms (Box 6-2 in the 7th ed.). Checker to confirm the 8th-edition box numbers. | the MM equation; the steady state; Km and Vmax; LB; α and α'; competitive, uncompetitive, mixed and non-competitive as a special case (A, B, C) |
| Berg JM, Tymoczko JL, Gatto GJ Jr, Stryer L. *Biochemistry*, 9th ed. New York: W.H. Freeman, 2019. Ch. 8, "Enzymes: Basic Concepts and Kinetics". | the MM equation; the double-reciprocal plot; competitive, uncompetitive and non-competitive inhibition and their LB patterns (A, B, C) |
| Segel IH. *Enzyme Kinetics: Behavior and Analysis of Rapid Equilibrium and Steady-State Enzyme Systems*. New York: Wiley, 1975 (Wiley Classics Library reissue, 1993). Ch. 3, simple inhibition systems. | the general mixed-type equation; where the LB lines meet in each case (C, D) |
| Cornish-Bowden A. *Fundamentals of Enzyme Kinetics*, 4th ed. Weinheim: Wiley-Blackwell, 2012. The chapters on inhibition and on the statistics of fitting. Checker to confirm the chapter numbers. | the Kic/Kiu names; "non-competitive" used loosely; the meaning of Km; [S] bracketing Km; least squares (A5, C5, F, G) |
| Copeland RA. *Evaluation of Enzyme Inhibitors in Drug Discovery: A Guide for Medicinal Chemists and Pharmacologists*, 2nd ed. Hoboken: Wiley, 2013. Ch. 3, reversible modes of inhibitor interactions with enzymes; the chapter on tight-binding inhibitors. Checker to confirm the chapter numbers. | mixed inhibition with Copeland's α = Ki'/Ki; the LB meeting point; initial-rate conditions; tight binding (A2, A7, C4, D) |
| Lineweaver H, Burk D. The determination of enzyme dissociation constants. *J Am Chem Soc* 1934;56:658-66. [10.1021/ja01318a036](https://doi.org/10.1021/ja01318a036) (not in PubMed; checker to confirm the DOI) | the double-reciprocal transform (B) |

## Literature

Retrieved through PubMed on 2026-10-11. DOIs are from the PubMed records.

| PMID | Reference | DOI | Used for |
|---|---|---|---|
| 21888353 | Johnson KA, Goody RS. The original Michaelis constant: translation of the 1913 Michaelis-Menten paper. *Biochemistry* 2011;50:8264-9 (translating Michaelis L, Menten ML, *Biochem Z* 1913;49:333-69) | [10.1021/bi201284u](https://doi.org/10.1021/bi201284u) | the MM equation; rapid equilibrium as the original assumption (A1, A4) |
| 16743508 | Briggs GE, Haldane JB. A note on the kinetics of enzyme action. *Biochem J* 1925;19:338-9 | [10.1042/bj0190338](https://doi.org/10.1042/bj0190338) | the steady state; Km = (k₋₁ + k₂)/k₁; [S] much greater than [E] (A3, A4) |
| 14021668 | Cleland WW. The kinetics of enzyme-catalyzed reactions with two or more substrates or products. II. Inhibition: nomenclature and theory. *Biochim Biophys Acta* 1963;67:173-87 | [10.1016/0006-3002(63)91815-8](https://doi.org/10.1016/0006-3002(63)91815-8) | slope and intercept inhibition (Kis, Kii); the naming map (C) |
| 4206907 | Cornish-Bowden A. A simple graphical method for determining the inhibition constants of mixed, uncompetitive and non-competitive inhibitors. *Biochem J* 1974;137:143-4 | [10.1042/bj1370143](https://doi.org/10.1042/bj1370143) | Ki' for uncompetitive, mixed and non-competitive inhibitors (C3, C6) |
| 24523108 | Ring B, Wrighton SA, Mohutsky M. Reversible mechanisms of enzyme inhibition and resulting clinical significance. *Methods Mol Biol* 2014;1113:37-56 | [10.1007/978-1-62703-758-7_4](https://doi.org/10.1007/978-1-62703-758-7_4) | the four reversible mechanisms, including mixed (C4, D5-D6) |
| 4980133 | Morrison JF. Kinetics of the reversible inhibition of enzyme-catalysed reactions by tight-binding inhibitors. *Biochim Biophys Acta* 1969;185:269-86 | [10.1016/0005-2744(69)90420-3](https://doi.org/10.1016/0005-2744(69)90420-3) | what the free-[I] assumption excludes (A7) |
| 22553875 | Brooks HB, et al. Basics of enzymatic assays for HTS. In: *Assay Guidance Manual*. Bethesda: Eli Lilly & Company and the National Center for Advancing Translational Sciences; 2012 (NCBI Bookshelf). The PubMed search returned this PMID, but the metadata tool returned no record; checker to confirm. | - | initial-rate conditions (A2) |
| 13785321 | Wilkinson GN. Statistical estimations in enzyme kinetics. *Biochem J* 1961;80:324-32 | [10.1042/bj0800324](https://doi.org/10.1042/bj0800324) | the error distortion of linear transforms; weighting; least squares (F1, F3, G1) |
| 14275146 | Dowd JE, Riggs DS. A comparison of estimates of Michaelis-Menten kinetic constants from various linear transformations. *J Biol Chem* 1965;240:863-9 | [10.1016/S0021-9258(17)45254-9](https://doi.org/10.1016/S0021-9258(17)45254-9) (from the PII; checker to confirm) | LB the least reliable transform (F1, F2) |
| 4881884 | Cleland WW. The statistical analysis of enzyme kinetic data. *Adv Enzymol Relat Areas Mol Biol* 1967;29:1-32 | [10.1002/9780470122747.ch1](https://doi.org/10.1002/9780470122747.ch1) | weighted and nonlinear fitting (F1, F3, G1, G2) |
| 3986669 | Tommasini R, Endrenyi L, Taylor PA, Mahuran DJ, Lowden JA. A statistical comparison of parameter estimation for the Michaelis-Menten kinetics of human placental hexosaminidase. *Can J Biochem Cell Biol* 1985;63:225-30 | [10.1139/o85-032](https://doi.org/10.1139/o85-032) | LB "very imprecise and inaccurate"; unweighted nonlinear least squares preferred (F2, F5) |
| 2246896 | Tseng SJ, Hsu JP. A comparison of the parameter estimating procedures for the Michaelis-Menten model. *J Theor Biol* 1990;145:457-64 | [10.1016/s0022-5193(05)80481-3](https://doi.org/10.1016/s0022-5193(05)80481-3) | LB had the largest sum of squared errors (F2) |
| 23850893 | Johnson KA. A century of enzyme kinetic analysis, 1913 to 2013. *FEBS Lett* 2013;587:2753-66 | [10.1016/j.febslet.2013.07.012](https://doi.org/10.1016/j.febslet.2013.07.012) | modern practice: fit the equation directly (F3, G2) |
| 27177048 | Schlosser PM. Revision of the affinity constant for perchlorate binding to the sodium-iodide symporter based on in vitro and human in vivo data. *J Appl Toxicol* 2016;36:1531-5 | [10.1002/jat.3337](https://doi.org/10.1002/jat.3337) | a real case: an LB Ki of 1.5 µM, re-fitted nonlinearly, became 0.59 µM (F4, optional) |
