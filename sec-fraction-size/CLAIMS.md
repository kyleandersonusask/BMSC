# CLAIMS: sec-fraction-size

| # | Claim | Status | Where |
|---|---|---|---|
| C1 | A collected fraction holds the mean concentration of everything that eluted while it filled, so its reading is the average over its volume. | PHYSICAL (mixing in the tube) | `tube()`; self-test conserves total protein |
| C2 | Wider fractions average neighbouring peaks together, so peaks merge and vanish. Narrower fractions resolve them. | DERIVED from C1 | panels for 2, 5, 10 and 20 fractions; self-test checks peaks never drop as fractions get finer |
| C3 | K = (Ve - Vo)/(Vt - Vo), with Vt = 30 mL and Vo = 5 mL, as on Kyle's slide. | TEXTBOOK | footer |
| C4 | Peak positions, heights and widths are stylised Gaussians placed like Kyle's 1 mL run (about 8, 15, 20 and 27 mL). | STYLISED | `PEAKS` |
| C5 | Column packing is ideal. Poor packing broadens peaks as well, which Kyle's slide mentions but the model leaves out. | STYLISED (omission stated) | footer |
