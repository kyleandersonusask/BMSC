# CLAIMS: two-d-page

| # | Claim | Status | Where |
|---|---|---|---|
| C1 | Below its pI a protein has a net + charge and moves toward the cathode (up the pH gradient); above its pI it is net - and moves toward the anode. At the pI its net charge is zero and it stops. | TEXTBOOK; KYLE (slide 29) | `q()`, `step()`; self-test (b) |
| C2 | Molecules that wander past their pI (by diffusion) change sign and are pulled back, which keeps the band focused. A kick by hand shows the same pull from either side. | TEXTBOOK (Kyle's ask, 10-28) | kick buttons; self-test (c) |
| C3 | Net charge is drawn as tanh(1.2 (pI - pH)): smooth, crossing zero at the pI. Real titration curves have steps from each ionisable group. | STYLISED (stated in footer) | `q()` |
| C4 | Strip pH 3 to 9, anode + at pH 3, as on slide 29. | KYLE | strip |
| C5 | Focused band width sqrt(D/(mu k)), about 0.08 pH units here. | DERIVED (drift-diffusion balance) | `MU`, `KQ`, `D`; self-test (a) |
| C6 | SDS coats every protein so it is negative whatever its pI; the second dimension then separates by size alone (12% gel, Rf = 2.177 - 1.02 log10 kDa). | TEXTBOOK; KYLE (slide 30) | second stage; self-test (d) |
| C7 | Six made-up proteins: A and D the same size (66 kDa) with different pIs; B and F the same pI (5.5) with different sizes. Each pair merges in one dimension and splits in two. | STYLISED | `P` |
| C8 | Real focusing takes 12-72 h; here it takes seconds. A kick runs the sim on while the stage clock holds. | KYLE (slide 29); STATED | footer |
