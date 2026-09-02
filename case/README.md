# katibOS Deck Mk1 — enclosure

A 3D-printed clamshell for the **Waveshare ESP32-S3-RLCD-4.2** (the `waveshare` env)
and a **NuPhy Air60 V2**. Concept stage: dimensioned sheet set, no CAD yet.

**[DECK_MK1.html](DECK_MK1.html)** is the deliverable — open it in a browser.
Sheets A0–A9: inputs, drivers, shut/open sections, plans, centring, hinge, parts,
the one number that decides everything, the rev.8 benchmark, and the
measure-before-CAD list. Also published as an Artifact at
`claude.ai/code/artifact/886a0107-0f1b-4bf8-9fc0-8cc6abd3e340`.

## The design in five lines

Clamshell, like Micro Journal rev.8 — but **structurally inverted**. rev.8 puts a
bare display module in the lid and its MCU, charger and cell in the base, so the
display ribbon crosses the hinge. One Waveshare board *is* all of that, so it goes
in the lid entire; the Air60 is BLE; **nothing crosses the hinge at all**. The base
holds no electronics, which is why it is 28 mm tall where rev.8's is 47.

The lid does not house the board — it **docks the assembled snap-fit case**
([printables 1780357](https://www.printables.com/model/1780357-slim-snap-fit-case-for-waveshare-esp32-s3-rlcd-42/files))
through a cut-out window. So both halves stay removable: the keyboard lifts out
and goes back to the desk, the display pops out and is a standalone reader.

## Numbers

| | |
|---|---|
| Shut | 308 × 130 × **28 + _T_** |
| Open height | 146 (lid at 105°) |
| Screen centre | 84 above the desk, 15° rake |
| Printed parts | 8 (+3 spare hinge stops) |
| Largest part | 200 × 130 — rev.8's bed cap, adopted |
| Filament | ~265 cm³ modelled solid, ~300 g |
| Crosses the hinge | nothing |

**_T_ is the display case's outer thickness over the cell.** It is the only
unmeasured number left and it sets the shut height directly: _T_=20 → 48,
_T_=28 → 56, _T_=32 → 60 (at which point the margin over rev.8 is gone and
sheet A7's two escapes apply — merge the case into `lid_centre`, or fold the
screen backwards into a rear well for a ~34 mm slab at the cost of 70 mm of depth).

## Parts

`base_centre` 200×130×28 · `base_cap_L/_R` 54×130×28 · `lid_centre` 200×122×4
(cradle window, sprung tabs, inner lip) · `lid_cap_L/_R` 54×122×4 ·
`hinge_stop` ×2 · `nameplate` 90×15×2.

Hardware: 8× M3×16 + inserts, 2× mini torque hinges 3–4 kgf·cm, 4× Ø6×3 magnets,
4× Ø12 feet. No M2.5 screws, no connector, no glue — the display brick is never opened.

## Traps already walked into

- **The board is not centred on its own picture.** Waveshare's active area sits
  1.50 from the PCB's left edge and 6.20 from the right, where the ribbon folds.
  Centre the *window*, not the board. Since the snap case is now in between, the
  fix moves up a level: cradle offset = (R − L) / 2 from its measured bezel
  borders. Skip it and the image is silently off-centre.
- **Print knuckles with layers running along the pin axis**, or the first one
  shears on layer lines — which is why the base's knuckles belong to
  `base_centre` and the caps rather than being bonded on.
- **The 20 mm island has to bulge outward.** There is nowhere inside a full
  keyboard pocket for a boss to nest, so the lid's inner face stays flat and
  shuts onto the rear keycaps with 2.1 mm over the lip. rev.8 has the same hump.
- **Buy the torque hinges.** Brick + plate ≈ 315 g ≈ 2 kgf·cm at the pin.
  Printed friction would creep.
- **PETG or ASA, not PLA.** A 300 mm span that has softened in a car is scrap.

## Before CAD

Four measurements, all on hardware that is already on the desk: _T_; the case's
outer footprint; its bezel borders left and right of the glass; and the keyboard's
real length, depth and rear height with keycaps on. Sheet A9 says what each one
changes.

## ref/

- `waveshare-rlcd-4.2-outline.jpg` — Waveshare's own outline drawing. 92.50 × 70.10
  PCB, 84.80 × 63.60 active, 4× M2.5 on 85.50 × 62.10, 13.50 thick without the cell.
  Source: waveshare.com/esp32-s3-rlcd-4.2.htm
- `microjournal-rev8-stl-measurements.txt` — bounding boxes and closed volumes of
  all 20 rev.8 STLs, computed from the meshes, plus the derived assembly figures
  and the notes that shaped this design.
- `microjournal-rev8-open.jpg`, `-shut.jpg` — rev.8 for form reference.
  Source: github.com/unkyulee/micro-journal

Nothing in this folder has been printed. The hinge in particular is drawn, not proven.
