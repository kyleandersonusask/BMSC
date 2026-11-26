# SOURCES: dna-protein-3d

Where each input and each borrowed number comes from. Read-only inputs are named by path and SHA-256 where a
hash was taken. Nothing in `dna-viewer` was written, run or copied into this demo: the only code read from there
was a set of documents (below), and no code was copied, so no per-file copy hash is required.

## Structure data

- **1AN2**, RCSB PDB, biological assembly 1: Max bHLHZ dimer on a 22-bp duplex. Ferré-D'Amaré, Prendergast &
  Burley, 1993, *Nature* 363:38. Licence: PDB data, CC0. Vendored by the Library lane at
  `lib/data/pdb/1AN2/1AN2.pdb1`. Source SHA-256 (from `model/model.json` provenance):
  `8c7bd9ff545fd879c04f2746a06dbaca30383b159cb63092dac8a984950390cb`, which matches `lib/data/pdb/1AN2/SHA256SUMS`.
- `model/model.json`, built by `model/build_model.py` (stdlib only, `python -I -B`). Its frame is model.json's own
  (see CLAIMS A12). Frame F (`model/build_model_frameF.py`, `model_frameF.json`) is a second file in another
  schema and is **not** used by this page. Frame-F adapter: a lead decision.
- The page embeds a trimmed copy of `model/model.json` (3-decimal rounding, unused fields dropped, phosphate frames
  A and B both kept). The embedded copy is written by `build_index.py`, which stamps the source SHA-256 into the page
  (`model.json` sha256 `1d965665045494d2e1f428925bbb078d54b1b2f21a645d9298fb9224e93036c7`).

## Parameters and literature (BORROWED or STYLISED; labelled on screen)

| source | used for | status |
|---|---|---|
| Olson, Gorin, Lu, Hock & Zhurkin 1998, *PNAS* 95:11163 (PMID 9736707). Full text not re-read (PMC returned empty); 6×6 table not. | rotational step stiffness, 0.047 kBT/deg², convention E = ½ f dq² | BORROWED but unconfirmed; applied to tilt, roll and twist alike (STYLISED). Downgrade to STYLISED if the text cannot be confirmed. |
| Bell 1978, *Science* (DOI 10.1126/science.347575) | Bell-Evans rupture law | MEASURED theory |
| Evans & Ritchie 1997, *Biophys J* (DOI 10.1016/S0006-3495(97)78802-7), abstract | dynamic-strength model; the MD regime for drag | MEASURED theory |
| Kühner, Bartels et al. 2004, *Biophys J* (DOI 10.1529/biophysj.104.048868), abstract | LexA-DNA x‡ 5.4 Å and k_off; the landscape used for the pull (x‡ only; k_off comes from the site Kd) | BORROWED |
| Bartels et al. 2003 (DOI 10.1016/s1047-8477(03)00127-8), abstract | range check only (not plotted) | BORROWED |
| Record, Lohman & de Haseth 1976 (DOI 10.1016/s0022-2836(76)80023-x); Lohman, deHaseth & Record 1978 (DOI 10.1016/0301-4622(78)80011-8) | counterion release direction | literature (direction only) |
| Wang et al. 2017 (PMID 27903915), via the HLH demo | Max Kd on CACGTG, about 20 to 30 nM at 150 mM | BORROWED (through HLH) |
| HLH demo `demos/hlh-dimer-ebox/model.json` (read only) | Kd by site and class (`classes.max_like`, spacing 0); non-specific Kd 34,000 nM; kon 0.01 nM⁻¹ s⁻¹; RT = 0.5925 kcal/mol | BORROWED (the HLH science check is still pending) |
| Fairman 1997 (PMID 9007990), de Martin 2021: basic region disorder off DNA | context in CLAIMS (the fold is not animated) | literature |
| Okabe & Ito colour-blind-safe palette | base colours A #2E9B57, T #D55E00, G #0072B2, C #E69F00 | convention (from CLAUDE.md) |

Textbook formulas: Stokes drag 6πηRv (η = 0.89 mPa·s at 25 °C; R = 2.5 nm STYLISED); Debye length 0.304/√I nm;
the Bondi (1964) radii, which are a PLACEHOLDER for AMBER Rmin/2 (the DNA project's tier not ported).

## The DNA project's documents (read only; no code copied)

Read on 2026-10-11 and 2026-10-12 from `OneDrive\Claude\dna-viewer\` (SHA-256 at reading):

- `HANDOFF_DNA_PRESENTATION.md`, `f0e472910c5608fcf3606b21454bcbfbf3baeb1a2de4ebb3d6bca34d26256f1f` (matches
  the hash recorded in `model.json` provenance). Used for: the groove rule (edge chemistry, not width; per-pair
  measurement against the ring centroid); the face code table; the rule that nobody faces one groove.
- `allatom/DNA_PRESENTATION_HANDOFF.md`, `33d83769b07882e5962aa94088c4c107fea2c5715572623d8aa3453e4b174109`.
  Used for: the rule to include hydrogens and name the force field; the rule to say what fragment is shown.
- `allatom/DNA_PRESENTATION_VERIFICATION.md`, `0a4d126bcda48edb0c8b321e8f00c3b7470afda269f46650cb01e8d2da13b1b8`.
  Used for: the checklist (frames stated beside every signed number; anchor signs in chemistry; a reference check
  that can fail). The B to Z rules are not used (B-form only).

## The shop's own files

- Groove and face rules, Okabe-Ito colours, the machine-safety rule and the presenter standard: `CLAUDE.md`
  (`universal-visuals`, repo root).
- `docs/design/dna-protein-3d.md`: design, Kyle's rulings in §0, the claims table in §3.5, the build plan §6.
- `demos/dna-protein-3d/takes/webgl/index.html`: the renderer this page is built from (sphere impostors, groove
  bands, contact quads, ghost shell, arrow check). Written in this shop; no code from the purchased set.
- `demos/dna-protein-3d/takes/canvas/`: the painter (not embedded; the fallback is the labelled still frame, a
  packaging decision for the lead). Its presenter-row and self-test ideas are re-written here.
- `demos/dna-protein-3d/takes/webgl/measure_headless.py`: the PID discipline was copied into
  `demos/dna-protein-3d/measure_headless.py` (Python `tempfile.mkdtemp()`, list arguments, child-path check, stop by
  PID only). The measurement script is written for this page.
- `tools/publish.py`: the house-rule checks (`--check`).

## Code copied from dna-viewer

**None.** If any is added later, copy it into `lib/vendor/dna-viewer-allatom-2026-10-11/` with its SHA-256, and
name the path and hash in this section. (Design §1 applies.)

## Open items for the lead

- Frame F adapter, or retire `build_model.py` (design §6, data follow-up).
- `build_model.py` CHECK 1 is only half red: the groove side test is unchanged by the strand swap. Port
  `build_model_frameF.py` RED 1b, or retire it.
- `build_model_frameF.py` RED 1a (strand swap) does not go red (its author reported this).
- `build_model.py` CHECK 5 (presence) counts a backbone contact and a carbon contact as reading the base; its His28
  absence is checked only on pairs 9 to 11. CHECK 5b now checks the six exact E-box contacts per chain (A1 Glu32 to
  strand II pair 14, Arg36 to strand I pair 12; A2 Glu32 to strand I pair 9, Arg36 to strand II pair 11), with a
  one-pair shift as the red test. These pairs come from the model's own contact list, not from the design text.
- The HLH Kd values and the Wang 2017 claim still await their own science check (HLH CLAIMS D4).
- The helix range (residues 26 to 47) comes from the 1AN2 HELIX record. The Ferré-D'Amaré 1993 claim that the basic
  region and helix 1 form one helical segment touching the major groove is from its abstract only (DOI 10.1038/363038a0);
  the full text still needs the science check.
