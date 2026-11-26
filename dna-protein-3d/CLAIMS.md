# CLAIMS: dna-protein-3d

Every scientific claim the page shows, its status, and its source. Status tags:
**MEASURED** (computed from the 1AN2 coordinates or a stated formula, and checked in the page's self-test where
marked), **INFERRED** (standard theory or chemistry applied by us), **STYLISED** (a teaching choice or a drawn
shape, labelled on screen), **BORROWED** (a number from another demo or paper, labelled on screen).
Status is for the science check: nothing here is marked "verified" until the house-rule check (CLAIMS rows read
against their sources, including the full texts of Kühner 2004 and Wang 2017) has been done. That check is pending.

Source key: **1AN2** = RCSB PDB 1AN2 (Ferré-D'Amaré et al. 1993, *Nature* 363:38), see SOURCES.md. **HLH** =
`demos/hlh-dimer-ebox/model.json`. **Design** = `docs/design/dna-protein-3d.md`.

## A. Crystal-derived facts (1AN2 is the source)

| # | claim as shown | status | source and check |
|---|---|---|---|
| A1 | The duplex is 22 base pairs; the Max dimer (chains A1 and A2) sits on it. Strand I is chain B residues 1 to 22; strand II is the crystal two-fold copy. | MEASURED | 1AN2 assembly 1; `model/build_model.py` |
| A2 | The starting pose is the crystal's own duplex: its bend is kept, not removed. The bend angle is not measured here. | MEASURED (pose), not claimed (bend) | 1AN2 coordinates; Design §2 says the DNA is "straight" in the first draft: that wording is withdrawn, the crystal is not straight in the data |
| A3 | Per base pair, the groove each base atom is on is set by its chemistry: major = N7, O6, N4, C7; minor = N3, O2, N2. The page colours the bands by pattern, not by width. | MEASURED (atom names) / INFERRED (chemistry) | `model.json` groove labels; self-test "arrow vs atoms" uses the same face labels (`M.dna[].groove`) |
| A4 | Face code per pair (major edge, minor edge), from the table in CLAUDE.md. Example for pair 1, G:C: major `H A A D H H`, minor `A D A`. | INFERRED (chemistry); table from the shop's CLAUDE.md, consistent with the DNA project's 336/336 sites (BORROWED) | `model.json` face_code; self-test "face code table" compares all 22 pairs |
| A5 | Each pair's own +x arrow points to its major-groove edge; the arrow is drawn from that pair's own frame. Checked against the major-face and minor-face atoms (by their face labels): all 22 pairs within 30° in 3-D; largest angle 19.1°. | MEASURED | self-test `arrow` (tolerance 30°); the flipped-arrow and Y-axis red tests each fail every pair |
| A6 | Contacts at 4.0 Å from the 1AN2 heavy atoms: 128 in total, of which 28 are H-bond (N/O to N/O ≤ 3.5 Å), 8 methyl (any heavy protein atom to thymine C7 ≤ 4.0 Å), 92 van der Waals (other heavy pairs ≤ 4.0 Å). | MEASURED (distances); types INFERRED | self-test `counts` (28/8/92 asserted); the list is from coordinates, there are no hydrogens or angles in a crystal |
| A7 | The model's own 3.5 Å list (54 items, `model.json` contacts) is reproduced: 54 of 54 matched, the largest distance difference 0.004 Å. A 1 Å shift of the protein breaks the match (red test). | MEASURED | self-test `model` (asserted, with a red test); `model.json` contacts vs recomputed distances |
| A8 | The local statement on screen (scenes 3 to 6): "helix 26 to 47 (1AN2) sits in the major groove at pairs 11 to 15 (chain A1) and 8 to 12 (chain A2)". Computed from the 4.0 Å contacts, counting only residues inside the HELIX record. | MEASURED | `computeStatement`; HELIX record from `model.json` `protein.helices_from_HELIX_records` |
| A9 | The basic-region helix is residues 26 to 47 (chain A, HELIX record 1). The page's pairs are the contacts of that helix at 4.0 Å. The Ferré-D'Amaré 1993 abstract describes the basic region plus helix 1 as one helical segment that contacts the major groove; the full text was not re-read here. | MEASURED (HELIX record and contacts); literature wording from the abstract only | `model.json`; Ferré-D'Amaré 1993 (DOI 10.1038/363038a0), abstract |
| A10 | Base pairs are rigid slabs with the crystal atoms. Neighbouring pairs are joined by six step springs centred on the crystal's own step values. At zero deviation the chain reproduces the embedded rest pose: the largest atom error is 0.057 Å (tolerance 0.1 Å). The rest pose matches the crystal to 1e-15 Å before 3-decimal rounding (build_model CHECK 2). | MEASURED | self-test `pose`; the 0.1 Å tolerance is set by the 3-decimal embedded data, see SOURCES.md |
| A11 | Step values in `model.json` (shift, slide, rise, tilt, roll, twist per step) are the crystal's own, in the model's own convention, and are not directly comparable with 3DNA tables. | MEASURED, with the convention stated | `model.json` `step_convention` |
| A12 | The frame is model.json's own: origin at the midpoint of the two C1′ atoms; z along strand I 5′→3′; x = y × z. This is **not** the standard Olson reference frame, and the DNA project's frame F is not used: it is a lead decision. | STYLISED convention | `model.json` `frame`; SOURCES.md |

## B. Stiffness and motion (STYLISED)

| # | claim as shown | status | source |
|---|---|---|---|
| B1 | Translation stiffness of the step springs: 1.0 kBT/Å² for shift, slide and rise. | STYLISED | `model.json` `steps[].stiffness_STYLISED` (the file says so) |
| B2 | Rotation stiffness: 0.047 kBT/deg² for tilt, roll and twist, the coarse-grained twisting constant in Olson et al. 1998 (PNAS 95:11163). The 6×6 dimer-step table was not retrieved, and the PMC text of the value could not be re-read, so the value is BORROWED but unconfirmed. The same value is used for all three rotations. | BORROWED (one constant, text unconfirmed) / STYLISED (applied to all three) | Olson 1998 (text), `model.json` `stiffness`. If the source cannot be confirmed, downgrade to STYLISED. |
| B3 | The motion is a seeded slow sway (Kyle 2026-10-12: 'like a sea anemone'): each step parameter is a sum of 3 travelling sine waves with periods 5 to 16 s and wavelengths 9 to 20 steps, so the helix bends as a whole. Its spread is the Olson 1998 equipartition sd sqrt(kT/f) times 0.2 (about 0.2 Å and 0.92° per step). Real thermal motion is ps to ns and much faster; the sway is a slowed picture of the shapes, not the dynamics. | STYLISED | `jiggleStep`; labelled on screen |
| B4 | The backbone is a swivelling scaffold. Each sugar rides its base pair. Each phosphate sits at the average of the two positions predicted from the frames of the pairs it joins. | MEASURED (construction) / STYLISED (the averaging rule) | `model.json` phosphate frames in both pairs |
| B5 | "Base pairs stacked close hold the helix together; the sugar-phosphate backbone is a swivelling scaffold." (Kyle's wording.) | STYLISED (a statement about the model) | Design §0 ruling 1 |

## C. Protein, contacts and the pull

| # | claim as shown | status | source |
|---|---|---|---|
| C1 | The well (scene 4) is narrow: its contact term is a 2 Å Gaussian (a drawn width). That width is NOT the 5.4 Å x‡ used for rupture. The electrostatic term is -1.5 kcal/mol at contact and decays with the Debye length at the dial's salt (7.85 Å at 150 mM). The shape is for teaching. | STYLISED | `energyAt`; labelled "stylised" on screen |
| C2 | The well's bottom, at contact (x = 0), is ΔG° = RT ln(Kd/1 M), with Kd 20.1 nM for CACGTG: **-10.50 kcal/mol** at 25 °C (RT = 0.5925 kcal/mol; RT ln(20.1e-9) = -10.50). The electrostatic term is included in that bottom, so the total at x = 0 equals ΔG° exactly at any salt. The value is printed by the self-test `dg` (red test: the /1e6 slip gives -6.4 and fails). The -10.3 figure in the old design is for Kd about 28 to 30 nM and is not used. | BORROWED (Kd) / MEASURED (arithmetic) | Wang 2017 (PMID 27903915) via HLH; HLH `model.json`; self-test `dg` |
| C3 | Debye screening length λD = 0.304/√I nm (I in M), so 0.785 nm at 150 mM. The salt dial changes λD, and the scene-4 well's electrostatic decay follows it. No salt effect on force is modelled. | INFERRED (Debye theory) | standard theory; readout line and `energyAt` |
| C4 | Binding releases counterions and more salt weakens binding (direction only). | literature direction; **not** shown as a force effect | Record, Lohman & de Haseth 1976 (DOI 10.1016/s0022-2836(76)80023-x) |
| C5 | Contact types are classified by distance, not by hydrogens or angles. Breaking contacts fade by type as the protein moves: H-bond at 1.5 Å, methyl at 2.5 Å, van der Waals at 3.5 Å of displacement. | INFERRED (classification) / STYLISED (fade distances) | `fadeOf`; `CONST.contactFadeA` |
| C6 | Before rupture the protein leans up to 2 Å toward the trap. After rupture it drifts 25 Å in the drawing. The trap spring is drawn, not to scale. | STYLISED | `pullNow`; labelled |
| C7 | Rupture force is sampled by inverse CDF of the Bell-Evans survival function, with the seed shown (20261011). The rupture force is the seeded draw; the visible motion is only an illustration. | MEASURED (sampler) | `bellSample`; self-test `bell` |
| C8 | The most probable rupture force: F* = (kT/x‡) ln(r·x‡/(k_off·kT)), with kT = 4.12 pN·nm at 25 °C and x‡ = 0.54 nm. Below r_c = k_off·kT/x‡ the formula is blind, and the panel says so ("blind below r_c"; no line drawn). | MEASURED theory (Bell 1978; Evans & Ritchie 1997, DOI 10.1016/S0006-3495(97)78802-7) | self-test `bell`: 500 seeded draws at 1e3, 1e4 and 1e5 pN/s; worst measured mode error 3.0% (tolerance 5%; smoothed density, bandwidth 2 pN) |
| C9 | The slope of F* against log₁₀(rate) is 2.303·kT/x‡ (17.6 pN per decade at x‡ = 0.54 nm). Simulated 18.1 (2.9% off). Doubling x‡ halves it (ratio 0.48). | MEASURED | self-test `slope` (red test: the broken estimator gives ratio 1 and fails) |
| C10 | x‡ = 0.54 nm, from LexA on recA (Kühner 2004, DOI 10.1529/biophysj.104.048868, 5.4 Å). No bHLH force landscape was found. The screen says: "x‡ 0.54 nm, BORROWED from LexA-DNA (Kühner 2004); Max not measured. k_off = k_on × Kd (BORROWED). Landscape constructed from both." | BORROWED | Kühner 2004 (abstract only, per the design §3.1) |
| C11 | k_off for each site = kon × Kd, with kon = 0.01 nM⁻¹ s⁻¹ (= 10⁷ M⁻¹ s⁻¹). CACGTG 0.201 s⁻¹; CAGCTG 14.7; CATATG 2.09; ruler 340. Only CACGTG is anchored to a literature Kd; the other sites and the ruler are outputs of HLH's stylised energy model (HLH `classes.max_like.stylised` = true), so they are BORROWED from a STYLISED model. The readout tag says so for every site except CACGTG. | BORROWED from a STYLISED model (CACGTG literature-anchored, Wang 2017) | HLH `model.json` kinetics (its own science check pending) |
| C12 | Kd values (class max-like, spacing 0): CACGTG 20.1 nM (literature, Wang 2017); CAGCTG 1470 nM; CATATG 209 nM; non-specific 34,000 nM. The last three are BORROWED from HLH's stylised energy model, not literature values. | BORROWED (CACGTG literature; others from a STYLISED model) | HLH `model.json` `classes.max_like` and `energy_model.kd_nonspecific_nM` |
| C13 | Site scan: each register's barrier uses the kept fraction f = kept base contacts / 50 base contacts (identity match on the same strand), on a log scale between the cognate and ruler Kd. Backbone contacts are not counted (f = 0 gives the ruler Kd). | BORROWED anchors / STYLISED mapping | `scanRegs`, `siteKdFor`. **The cognate register tops the plot by construction**: f = 1 at d = 0. The self-test checks the pipeline (a forced change moves the top), not the biology. |
| C14 | Water drag is 6πηRv, with η = 0.89 mPa·s at 25 °C and R = 2.5 nm. At 1 m/s it is 41.9 pN; at 10 µm/s it is 4.2 × 10⁻⁴ pN. Drag at lab speeds is far below any force on the trace. | MEASURED formula; R STYLISED (assumed Stokes radius); η textbook | Evans & Ritchie 1997 (MD regime); self-test `drag` |
| C15 | The optional drag arrow is drawn MAGNIFIED at 2.4 × 10⁵ px per pN (x240,000), capped at 200 px, and it points against the motion (along -uPull as it lands on screen). True drag at 10 µm/s is 4 × 10⁻⁴ pN, so the magnified arrow is not drag at true scale. The factor is printed beside the checkbox. | STYLISED | `DRAG_SCALE_PX_PER_PN`, `DRAG_MAX_PX`; label on screen |
| C16 | Time dilation: 1 s on screen is (rupture time in simulated seconds) / 8 s. The readout prints it. | computed | `startPull` |
| C17 | Repeat pulls: the histogram is drawn from the same seeded sampler at 10, 1e2, 1e3, 1e4 and 1e5 pN/s. The dots are draws; the marker is the smoothed mode. | MEASURED (sampler) | `computeRepeats` |
| C18 | Bartels 2003: TF-DNA rupture forces about 50 to 165 pN over 70 to 79,000 pN/s (ExpG). Context only; not plotted. | BORROWED | Bartels 2003 (DOI 10.1016/s1047-8477(03)00127-8), abstract only |
| C19 | Desolvation and counterion re-condensation contribute to the well. No number is shown. | STYLISED (named, not computed) | Design §3.3 (literature to find) |

## D. Not claimed (the screen says so)

- The DNA is a crystal-derived duplex with rigid slabs and springs. It is not a molecular-dynamics trajectory.
- No explicit water. No counterion model. No chromatin, nucleosome or crowding. Hydrogens are not drawn (crystal heavy atoms only).
- The protein is the 1AN2 construct (bHLHZ region), not full-length Max. Its helix range is the HELIX record (A8, A9).
- **Not implemented in this slice:** the design asks for the protein as cartoon helices with the contact residues as sticks. The page draws every protein atom as a sphere (solid, ghost shell or hidden); contact atoms are tinted, not drawn as sticks. This was not met and is not claimed.
- Potential colouring (electrostatics) is not in this version: the charge self-test belongs to the DNA project's
  all-atom tier and has not been ported.
- The methyl dial at the central CpG and the half-site dial are not implemented (no borrowed Kd for the half-site).
- Frame F of the DNA project is not used. The lead decides whether to adopt it (see SOURCES.md).
