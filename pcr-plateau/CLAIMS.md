# CLAIMS: pcr-plateau

| # | Claim | Status | Where |
|---|---|---|---|
| C1 | 1 pg of a 5 kb plasmid is about 2 x 10^5 copies (1e-12 g / (5000 bp x 650 g/mol/bp) x 6.02e23 = 1.85e5). | KYLE (slide); DERIVED | default start |
| C2 | A tube holds ~10^12 of each primer, ~10^15 of each dNTP, ~10^10 Taq; Taq adds ~50 nt/s. | KYLE (slide) | defaults, `V`, `NTP0` |
| C3 | Primers set the hard ceiling: each new strand uses one primer, so double-stranded copies cannot pass the primer count. | KYLE (slide: primers "mostly determine maximum amplification") | `sim()`; self-test (f) |
| C4 | Taq limit: at most Taq x 50 nt/s x extension time / amplicon length new strands per cycle; with the defaults (200 bp, 60 s) that is 1.5 x 10^11 and is reached at cycle 21 from 2 x 10^5 copies, matching the slide's "~20 cycles". Drawn as a soft minimum (power 4) so the slowdown is gradual. | KYLE (slide); STYLISED (length, time, soft minimum) | `cap()`, `SK`; self-test (a), (e) |
| C5 | Re-pairing: product strands are long and pair with their partners near 85 C on cooling, before primers (Tm ~60 C) can land; the share of strands that get a primer is P/(P + r D). r = 3 is fixed in the code and not shown (Kyle, 11-26: he will not teach the head start); it is chosen, not measured. | TEXTBOOK (mechanism); STYLISED (form and r) | `sim()`; self-test (d) |
| C6 | Each cycle a template strand is copied, primed but not finished (Taq busy; at very long amplicons dNTPs too), or re-paired. These shares sum to 1. | DERIVED | fate bars; self-test (f) |
| C7 | A 100-fold dilution shifts Ct by log2(100) = 6.6 cycles and every tube reaches the same plateau; Kyle's qPCR figure shows ~7-cycle steps and one plateau height. | KYLE (figure); DERIVED | Dilution series; self-test (b), (c) |
| C8 | dNTPs are not what stops it: a 200 bp product uses ~10% of the pool by cycle 40. A 2 kb product would run them out, so the model caps synthesis at the pool. | KYLE (slide); DERIVED | dNTP meter; self-test (g) |
| C9 | Other plateau causes are left out: Taq heat loss, Taq bound by product DNA, pyrophosphate. Stated in the footer. | STATED | footer |
| C10 | The dilution series is labelled in copies (2 x 10^8 to 2 x 10^2), not ng: the figure's 2 ng = 2.39 x 10^8 copies is a different (~7.8 kb) plasmid from the slide's 5 kb one. | DERIVED | series labels |
