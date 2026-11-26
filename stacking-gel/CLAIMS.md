# CLAIMS: stacking-gel

| # | Claim | Status | Where |
|---|---|---|---|
| C1 | Stacking gel 5% acrylamide, Tris-HCl pH 6.8; running gel ~12%, Tris-HCl pH 8.8; upper buffer Tris-glycine pH 8.3; glycine pI about 6. | KYLE (slide 17; captions 1136-1164) | gel labels |
| C2 | Cl- is small and always charged, so it leads in both gels. | KYLE (captions 1200-1212, 1344-1348) | readout; green dots below the boundary |
| C3 | At pH 6.8 glycine is charged only a small fraction of the time, so it trails and leaves a zone poor in charge carriers where the voltage is high (the "gap"). | KYLE (captions 1224-1292); TEXTBOOK | lit vs dim orange dots; voltage strip |
| C4 | Glycinate (net -1) fraction from Henderson-Hasselbalch with pKa2 9.6: about 0.16% at pH 6.8, 5% at 8.3, 14% at 8.8. That is roughly 80 times more often charged at 8.8 than at 6.8. | DERIVED | footer; `GLY_FRAC` |
| C5 | Dots are lit (charged) far more often than C4 (10%, 35%, 60%) so the change can be seen. Only the order 6.8 < 8.3 < 8.8 is meant. | STYLISED | `LIT` |
| C6 | SDS-proteins move faster than the boundary in the high-field glycine zone and slower than it in the low-field Cl- zone, so they collect at the boundary as a thin stack (isotachophoresis). The 5% gel barely sieves, so size does not matter there. | TEXTBOOK; KYLE (captions 1296-1336) | `molY`; self-test (a)-(c) |
| C7 | Below the wells the boundary is one sheet across the gel, so a full and a nearly empty well reach the running gel at the same time as equally thin bands. | KYLE (captions 1390-1400); TEXTBOOK | self-test (a), (b) |
| C8 | At pH 8.8 glycine speeds up, passes the proteins and runs just behind the Cl-; the proteins, now in a uniform field and a 12% gel, separate by size. Dye (Rf 1) rides the front. | KYLE (slide 19; captions 1356-1380) | self-test (d), (e) |
| C9 | Mobility in the running gel is linear in log(MW): Rf = 2.177 - 1.02 log10(kDa), so 97 kDa is about 0.15 and 21 kDa about 0.83. | STYLISED (typical 12% gel) | `rf()` |
| C10 | Without a stacking gel each band starts as tall as the sample column. It is squeezed only by the gel's own slowing (thickness = height x Rf), so big loads overlap neighbours (45 and 40 kDa). | STYLISED (no stacking at all); KYLE (slide 15) | comparison gel; self-test (f), (g) |
| C11 | The well phase is stylised: every lane's boundary reaches the bottom of its well at the same moment. The one-gel clock starts when the stack enters the running gel, so both races run side by side. | STYLISED (stated on screen) | `T0`; comparison caption |
| C12 | Proteins are drawn as if visible; in a real run only the dye shows until the gel is stained. | STATED | footer |
