# CLAIMS: HLH homodimer reading E-boxes

Every scientific claim the demo shows, with its source. Numbers come only from `model.json`, which
`model/gen_model.py` generates, and are never typed in by hand.

**Status key**
- **MEASURED**: stated directly by the cited structure, assay or review.
- **INFERRED**: reasoned from measured facts. No direct measurement of this exact claim was found. The demo labels it as a model.
- **STYLISED**: chosen by the demo (an absolute number, a simplification or a drawing convention). The demo must show the
  word "stylised" next to it.

Sources are cited by PMID, with the DOI in `SOURCES.md`. Structures are cited by PDB id.

Prepared 2026-10-11 by the science intern. An Opus check against these sources is still required before Kyle sees the demo
(house rule 3).

---

## A. The E-box and its half-sites

| # | Claim shown | Status | Source |
|---|---|---|---|
| A1 | bHLH proteins bind the E-box, consensus **CANNTG**. | MEASURED | Massari & Murre 2000 (PMID 10611221); De Masi 2011 (PMID 21335608); Atchley & Fitch 1997 (PMID 9144210) |
| A2 | Each monomer reads one **C-A-N half-site**. The two monomers read opposite strands, so CANNTG = half-site CAN on the top strand + half-site CAN on the bottom strand. Example: CACGTG = CAC + CAC. | MEASURED | de Martin 2021 (PMID 34502060), "each monomer recognizing a CAN half site"; Wang 2017 (PMID 27903915), "each MAX monomer recognizes one half of the palindromic E-box" |
| A3 | CACGTG, CAGCTG and CATATG are palindromes: each reads the same on both strands (two identical half-sites). | MEASURED (sequence fact) | follows from base pairing |
| A4 | **CACCTG and CAGGTG are the same double-stranded site** read from opposite strands, so their Kd is identical. Its half-sites are CAC + CAG, so it is asymmetric. The dial keeps both labels, and the demo should say "same site, other strand". | MEASURED (sequence fact) | reverse complement; the E47 crystal used CACCTG (Ellenberger 1994, PMID 7926781) |
| A5 | Bases flanking the E-box also affect binding: the Max/Max consensus is RAN-CACGTG-NTY. The model ignores flanks. Every site uses the flanks GAC...GTC, which fit that consensus and create no extra CANNTG on either strand (the generator checks this). | MEASURED (the flank effect); STYLISED (flanks ignored) | Solomon, Amati & Land 1993 (PMID 8265351) |

## B. The dimer and its geometry

| # | Claim shown | Status | Source |
|---|---|---|---|
| B1 | bHLH proteins bind DNA **as dimers**. The HLH motif is the dimerisation motif. | MEASURED | Murre, McCaw & Baltimore 1989 (PMID 2493990); Ferré-D'Amaré 1993 (PMID 8479534) |
| B2 | Each **basic region lies in the major groove**. | MEASURED | Ferré-D'Amaré 1993 (PMID 8479534, PDB 1AN2); Ellenberger 1994 (PMID 7926781); Jones 2004 (PMID 15186484) |
| B3 | The HLH forms a **parallel four-helix bundle** at the dimer interface: helix 1 and helix 2 from each monomer. In Max the bundle is parallel and left-handed. Max also has a leucine zipper (a coiled coil) after helix 2; E47 has no zipper. | MEASURED | Ferré-D'Amaré 1993 (PMID 8479534); Ellenberger 1994 (PMID 7926781); Fairman 1997 (PMID 9007990) |
| B4 | In Max, **the basic region and helix 1 are one continuous alpha-helix**. So the reading head sits rigidly on the dimer interface, and the two reading heads are held a fixed distance and angle apart. | MEASURED (continuous helix); INFERRED ("rigid", "fixed") | Ferré-D'Amaré 1993 (PMID 8479534): "the basic region plus helix 1" form one helical segment |
| B5 | The basic region is largely unstructured without DNA and becomes helical when it binds. The demo may show this; it is optional. | MEASURED | Fairman 1997 (E47, PMID 9007990); de Martin 2021 (PMID 34502060) |
| B6 | The DNA is drawn straight. In fact, intact Max bends its DNA by about 25 degrees toward the protein; the other bHLH structures used straight DNA. | STYLISED (straight); MEASURED (the bend) | Brownlie 1997 (PMID 9115440, PDB 1HLO) |
| B7 | B-DNA has about **10.5 bp per turn**, so each inserted bp rotates the next base pair by **34.3 degrees** and moves it **3.4 Å** along the axis. Measured in solution: 10.4 ± 0.1 bp per turn (about 34.6 degrees per bp). 3.4 Å is the textbook B-form rise. | MEASURED (10.4 ± 0.1); textbook (10.5 and 3.4 Å) | Wang 1979 (PMID 284332); Watson & Crick 1953 (PMID 13054692) for the 3.4 Å rise |
| B8 | With +1, +2, +3 and +4 bp, the second half-site is rotated by 34.3, 68.6, 102.9 and 137.2 degrees and shifted by 3.4, 6.8, 10.2 and 13.6 Å. | arithmetic on B7 | `model.json` geometry |

## C. Contacts (the network)

Max numbering is p22 MAX, as used for PDB 1AN2 and 5EYO. Max residue number = Atchley-Fitch basic-region site + 23, so
His28 = site 5, Asn29 = site 6, Glu32 = site 9, Arg35 = site 12 and Arg36 = site 13. The E47-like network uses
**generic site names** (b5, b6, Glu9, b12, b13), because E47's own residue numbers were not verified (the Genes Dev full text
was not reachable). No E47 PDB id is claimed.

Base-pair positions in each half-site are **outer** (the C:G of CA), **middle** (the A:T of CA) and **inner** (the third base N, half
of the central dinucleotide).

| # | Claim shown | Status | Source |
|---|---|---|---|
| C1 | **Glu32** (site 9, nearly invariant) reads the **CA**: an H-bond from N4 of the outer C, plus a contact to the A:T pair. In the classic description it contacts the adenine; in 5EYO it lies near the T methyl. It is the strongest base contact. | MEASURED | Wang 2017 (PMID 27903915, PDB 5EYO); Massari & Murre 2000 (PMID 10611221); De Masi 2011 (PMID 21335608); de Martin 2021 (PMID 34502060) |
| C2 | **His28** (site 5) donates an H-bond to O6 or N7 of the **G of the outer C:G pair**. | MEASURED | Wang 2017 (PMID 27903915); Chiu, Rao & Rohs 2023 (PMID 36656856) |
| C2-note | **Conflict for the checker.** A review says the His contacts "the central guanine" (Beaulieu 2020, PMID 32331235, citing older work). Both structure papers above put His28 on the outer G. The demo follows the structures. | — | — | **Resolved 2026-10-11 in favour of the structures:** the demo keeps His28 on the outer G, per Wang 2017 and Chiu 2023, pending the science check.
| C3 | **Asn29** (site 6) makes a van der Waals / C-H...O contact with the T methyl of the middle A:T pair. | MEASURED | Wang 2017 (PMID 27903915) |
| C4 | **Arg36** (site 13) H-bonds **N7 of the central G** (the bidentate O6 and N7 bond is the 5caC-specific form; on unmodified DNA it is one N7 bond) and packs on **C5 of the central C**. It spans both inner pairs. This is what makes class B choose **CAC** half-sites, and so CACGTG. | MEASURED | Wang 2017 (PMID 27903915); De Masi 2011 (PMID 21335608), "an arginine at position 13 prefer CAC"; de Martin 2021 (PMID 34502060) |
| C5 | A single residue at this position decides between CAC(A/G)TG and CAGCTG. Changing Met to Arg in the AP4 basic region switched a chimera to working on CAC(A/G)TG sites, and only Arg or Lys worked there. | MEASURED (in a yeast functional assay) | Dang et al. 1992 (PMID 1731330) |
| C6 | Arg36 on a **CAT** half-site gives a **partial** contact: the base opposite T is A, which has N7 but no O6, so at most one H-bond. On a **CAG** half-site the contact is **broken**: the base opposite G is C, with no O6 or N7. | INFERRED (from base chemistry); the "partial" weight is STYLISED | CAT is tolerated by Arg13 proteins: Dang 1992 (PMID 1731330), CAC(A/G)TG; De Masi 2011 (PMID 21335608) |
| C7 | **Arg35** (site 12) contacts the phosphate backbone and helps position Glu32. Mutating it (R35H/L) abolishes binding. | MEASURED (loss of binding); INFERRED (the contact) | Wang 2017 (PMID 27903915), measured and predicted; Massari & Murre 2000 (PMID 10611221), "an adjacent arginine stabilizes the position of the glutamate" |
| C8 | Mutations R36W and R35H/L abolish DNA binding; R36K weakens it more than 30-fold. These are context for the checker and are not shown. | MEASURED | Wang 2017 (PMID 27903915) |
| C9 | **Class A (E47-like)** has no Arg at site 13 (it has M, L, V or T) and does **not** H-bond the central bases. It prefers CAG (or CAT) half-sites. Its reading of the centre is drawn as an **indirect** link (backbone or DNA shape). | MEASURED (no Arg13, no central contact, CAG/CAT preference); STYLISED (the drawing and its weight) | de Martin 2021 (PMID 34502060); Atchley & Fitch 1997 (PMID 9144210); Ellenberger 1994 (PMID 7926781): discrimination "may result from interaction with both the DNA bases and the phosphodiester backbone" |
| C10 | The E47-like contacts b5→outer and b6→middle are drawn **by analogy** with the family-wide finding that sites 5, 6 and 12 contact the C or the A. | STYLISED by analogy | De Masi 2011 (PMID 21335608) |
| C11 | The "both strands" picture is simplified. In real dimers a monomer also reaches the partner's half-site, through site 13 and backbone contacts, so the centre is read jointly. The model splits the centre into one third base per half-site. | MEASURED (the joint reading); STYLISED (the split) | de Martin 2021 (PMID 34502060) |

**Contact states shown per site and spacing** (from `model.json`, `contact_states_by_spacing`):
- **kept**: the outer, middle and backbone contacts are kept on any C-A-X half-site. Inner contacts: Max-like keeps Arg36 on CAC, partial on CAT, broken on CAG. E47-like keeps the indirect link on CAG, partial on CAT, broken on CAC.
- **broken**: every base contact of a monomer whose half-site lacks CA (half-site-only partner, control).
- **spacing ≥ 1**: the dimer sits on its better half-site. The other monomer is out of register, so all its base contacts are broken and its backbone contact becomes nonspecific. **INFERRED** from B4 and B7, and the drawing is **STYLISED**.
- **interface**: the dimer-interface links are always kept, because the dimer is treated as preformed (see E4).

## D. Binding: orderings (sourced) and numbers (stylised)

**Model (STYLISED).** Binding has three modes:
1. nonspecific;
2. one basic region on one CA half-site;
3. both basic regions in register on both half-sites (spacing 0 only, in practice).

Free energies add. h = g_core + g_inner(class, third base). Mode 3 adds a pair (avidity, or chelate) bonus and a penalty of
4 kcal/mol per inserted bp. Kd = Kd_ns / Z, where Z sums the mode weights at 25 °C. The formula and parameters are in
`model.json` → `energy_model`.

**Kd (nM), STYLISED absolute values, by spacing 0 / +1 / +2 / +3 / +4 bp:**

| Site | Max-like (class B) | E47-like (class A) |
|---|---|---|
| CACGTG | **20.1** / 2470 / 2880 / 2880 / 2880 | 405 / 9820 / 10100 / 10100 / 10100 |
| CAGCTG | 1470 / 15200 / 15400 / 15400 / 15400 | **20.1** / 2470 / 2880 / 2880 / 2880 |
| CATATG | 209 / 7550 / 7870 / 7870 / 7870 | 209 / 7550 / 7870 / 7870 / 7870 |
| CACCTG = CAGGTG | 175 / 4700 / 4850 / 4850 / 4850 | 90.6 / 4240 / 4480 / 4480 / 4480 |
| half-site only, CAC + nnn | 5310 (spacing does not apply) | 15600 |
| half-site only, CAG + nnn (optional) | 21200 | 5310 |
| non-E-box control (GGATCC) | 34000 | 34000 |

| # | Claim shown | Status | Source |
|---|---|---|---|
| D1 | **Max-like order:** CACGTG ≫ CACCTG ≈ CATATG > CAGCTG > lone half-site > control. CACGTG is best because Arg36 reads both central G's. The CAC·CAG and CAT·CAT sites keep one or two partial central reads. The order between CACCTG and CATATG is **not established**: the demo puts them within 1.2-fold of each other. | MEASURED (CACGTG best for class B; Arg discriminates against CAGCTG); INFERRED (the middle of the order) | Ferré-D'Amaré 1993 (PMID 8479534); Atchley & Fitch 1997 (PMID 9144210); Dang 1992 (PMID 1731330); de Martin 2021 (PMID 34502060) |
| D2 | **E47-like order:** CAGCTG ≳ CACCTG > CATATG ≳ CACGTG > control. Sources support "class A prefers CAG half-sites; binds CAGCTG or CACCTG". The E47 crystal is on CACCTG. The kappa-E2 site that E47 was cloned on (Murre 1989) is usually given as CAGGTG, the same
site, but that sequence is not in the abstract: **verify it**. **The ranking CAGCTG over CACCTG is not established.** The model puts CAGCTG 4.5-fold ahead; say "about equal" in the demo if asked. | MEASURED (CAG preference; CACCTG is bound); STYLISED (the gap) | Jones 2004 (PMID 15186484), Table 1; Atchley & Fitch 1997 (PMID 9144210); Ellenberger 1994 (PMID 7926781); Murre 1989 (PMID 2493990); Blackwell & Weintraub 1990 (PMID 2174572) |
| D3 | **The class switch:** swapping the class swaps the best site (Max-like: CAGCTG is 73-fold weaker than CACGTG; E47-like: CACGTG is 20-fold weaker than CAGCTG). | MEASURED (the direction); STYLISED (the fold values) | Dang 1992 (PMID 1731330); de Martin 2021 (PMID 34502060) |
| D4 | The Max-like Kd on CACGTG is set to **20 nM**. That is inside the measured range for full-length MAX homodimer on CACGTG at 150 mM NaCl: Kd about 30 nM by fluorescence polarisation, and 16 to 32 nM by EMSA. The E47-like cognate Kd is set equal by symmetry; no E47 value is sourced. | MEASURED (the anchor); STYLISED (the choice of 20) | Wang 2017 (PMID 27903915) |
| D5 | **Nonspecific Kd = 34 µM** (1700-fold weaker than cognate). One measured value for a Max construct is only about 100-fold cognate over nonspecific. The model **widens** this on purpose. With a 100-fold window, a ≥100-fold drop for +1 bp would land straight on the nonspecific floor, and the single-half-site step would be invisible. | STYLISED; the measured 100-fold is reported in a review | Beaulieu, Castillo & Soucek 2020 (PMID 32331235) |
| D6 | **A lone half-site binds weakly**, at about the level of a dimer with one basic region engaged: Max-like CAC + nnn is 264-fold weaker than CACGTG. Half-site binding is real but weak, and is usually seen only in special contexts: MYC on degenerate E-boxes through a partly folded basic helix, and TCF3-TAL1 in an LMO2 complex. | MEASURED (half-site binding occurs in context); STYLISED (the 264-fold) | de Martin 2021 (PMID 34502060), reviewing those cases; El Omari 2013 (PMID 23831025) |
| D7 | **+1 bp breaks binding.** Kd(+1)/Kd(0) = **123-fold** for each class's cognate site (≥100, checked by the generator). Binding falls to the level of a dimer engaged on one half-site, and +2 to +4 bp sit on that floor. A spaced site stays slightly stronger than a lone half-site (2880 vs 5310 nM) because it offers two half-sites to choose from. Poor sites change little with spacing, because they are already near their floor; that is physically expected. | INFERRED (the direction: from B4 rigidity, B7 geometry and B1 dimer reading); STYLISED (the 4 kcal/mol per bp penalty and the fold values) | No direct measurement of base-pair insertion between bHLH half-sites was found. The closest analogy is another dimer family: changing nuclear-receptor half-site spacing by **1 nucleotide** switches which receptor binds (Umesono 1991, PMID 1648450). |
| D7-note | **For the checker.** Not every dimer is this strict. Some bZIP dimers bind sites of two lengths, which is common textbook knowledge but not sourced here. The demo's claim is limited to "this rigid bHLH model"; see B4. | — | — |
| D8 | The penalty does not reverse within 0 to 4 bp: the rotation reaches 137 degrees at +4. A full turn (about 10.5 bp) would restore the angle but leave a shift of about 36 Å. | arithmetic on B7 | — |

## E. Kinetics and concentration

| # | Claim shown | Status | Source |
|---|---|---|---|
| E1 | Association rate constant **kon = 1×10^7 M^-1 s^-1** (0.01 nM^-1 s^-1), the **same for every site**. Sequence changes the **off-rate**: koff = kon·Kd. For example, Max-like on CACGTG has koff = 0.20 s^-1 and a half-life of 3.5 s; at +1 bp, koff = 24.7 s^-1. | STYLISED. The order of magnitude is typical of protein-DNA association, and the value was chosen so the occupancy chart settles in seconds. | Halford & Marko 2004 (PMID 15178741), on association rates and the facilitated-diffusion range |
| E2 | Occupancy over time follows dθ/dt = kon·[D]·(1 − θ) − koff·θ. At equilibrium θ = [D]/([D] + Kd). The protein is in excess, with no depletion. | STYLISED (the textbook single-site model) | — |
| E3 | The concentration dial runs 0.1 to 1000 nM. At 1000 nM, a +1 bp CACGTG site is still about 29% occupied. **Concentration can partly rescue a poor site**, which is a teaching point and not a bug. | follows from the model | — |
| E4 | **The dimer is treated as preformed.** Real p21 Max homodimerises with a micromolar Kd, so at 0.1 to 1000 nM most real Max would be monomeric. The dial means "nM of dimer". | STYLISED; MEASURED (the micromolar figure, as reported in a review) | Beaulieu 2020 (PMID 32331235) |
| E5 | Temperature is 25 °C (RT = 0.5925 kcal/mol). | STYLISED | — |

## F. What the demo must label "stylised" on screen

- every Kd, koff, half-life and kcal/mol value;
- the half-site and nonspecific floors, and the 1700-fold window (D5);
- the spacing penalty and the 123-fold drop (D7);
- straight DNA (B6), the preformed dimer (E4), the four-link drawing of the four-helix bundle, and the E47-like generic residue names
  and indirect centre link (C9, C10).

## Pick fixes applied 2026-10-11 (for the Opus science check)

The build now shows, and this file claims, the following. The science check still has to re-derive each one against its source.

- **B1 (interface):** the HLH dimer interface is a four-helix bundle drawn as four links (stylised). The leucine zipper (Max only) is a separate solid link. The legend says so and the on-canvas label reads "HLH dimer interface".
- **B2 (groove):** each basic region sits in the major groove of one half-site. The DNA is drawn straight (stylised).
- **B4 (one helix, Max):** the basic region and helix 1 are one continuous helix. The node is labelled "basic+H1" and the caption says so.
- **B7 (turn, stylised):** the 34.3 degree turn per bp is about the helix axis. It is drawn **in the plane of the page** (stylised), so the rotation is schematic. The spacing readout gives the model's 34.3 degrees and 3.4 Angstrom per bp, with B-DNA at 10.5 bp per turn.
- **C2, C3, C4 (contacts):** each contact's tooltip gives its residue, its base and the model description. C4 is rewritten above; `model.json` edge text is regenerated from `model/gen_model.py` to match.
- **C9 (indirect centre, class A):** the class A centre contact (site 13 to the inner pair) is drawn as an indirect, dash-dot link, labelled "indirect: DNA shape (stylised)". It is not a base contact.
- **C10 (generic names):** the E47-like residue names are generic Atchley-Fitch site numbers (b5, b6, Glu9, b12, b13). Their contacts are drawn by analogy (stylised). The class note says so.
- **C11 (joint centre):** the centre is read jointly by the two monomers; the drawing splits it to one inner base per monomer (stylised).
- **D7 (binding loss):** the 123-fold loss at +1 bp is a **model inference** (stylised), not a measured spacing effect. The spacing readout says so.
- **E4 (preformed dimer):** the concentration dial reads "preformed dimer, stylised; log scale".
- **F (stylised labels):** the footer lists Kd, rates, shares and weights; dimer preformed; DNA straight; turn drawn in plane; centre split per monomer; E47-like names generic.
- **Not yet covered on screen:** C6 (the partial weight on CAT half-sites) has no fix text in the pick, so it is not changed here. Its claim still needs the on-screen label check.
