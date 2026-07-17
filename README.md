# VectorSplitK

An open-source, wireless, high-profile 42-key mechanical split keyboard. Built around the powerful Seeed Studio XIAO nRF52840, the VectorSplitK features an aggressive columnar stagger, custom-modeled flat profile keycaps, and a robust dual-case mechanical assembly. This project is my first split keyboard. The PCB was made entirely in KiCad and the CAD was done in Autodesk Fusion.

> Full day-by-day design log, decisions, and dead ends: [JOURNAL.md](./JOURNAL.md)

## Renders

### Standard Top View

<img width="21947" height="12333" alt="Render 1" src="https://github.com/user-attachments/assets/3efa0abc-780f-49f9-b0c4-ca2248520bc0" />

### Isometric Split Profile

<img width="21947" height="11113" alt="Render 2" src="https://github.com/user-attachments/assets/ce7feb83-7ecb-4b40-b707-0fcc76378252" />

### Rear Profile (USB-C & Alignment)

<img width="21947" height="11113" alt="Render 3" src="https://github.com/user-attachments/assets/501ce6b4-b045-4aa8-9bdb-96b5441b6191" />

## Hardware Architecture

### 1. Electrical Schematic

The electrical system uses hierarchical sheets in KiCad to define identical left and right sides. It resolves typical multi-sheet duplicate ground issues by utilizing sheet-specific power flags (${SHEETNAME}_GND).

Main Sheet

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/41074558-e1d6-47a8-8179-e87d7e236dc5" />

Left Half Matrix

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/ea8a6e65-f7e4-4908-bcbc-8609f5bb8108" />

Right Half Matrix

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/8aa38ea9-39c9-45ee-b7cd-703116fdfb38" />

### 2. Footprints

- **Switch Footprints:** High-profile `acheron_MXH:MX100H` (1.00u) and `acheron_MXH:MX150H` (1.50u) hotswap-ready switches (42 total, 21 per side).
- **Diodes:** `Diode_SMD:D_SOD-123` (42 total, 1 per key).
- **Mounting Holes:** `MountingHole:MountingHole_3.2mm_M3_DIN965_Pad` (8 total, 4 per side).
- **Resistors:** `Resistor_SMD:R_0805_2012Metric` (4 total, 2 per side).
- **Integrated Circuit:** `modified-XIAO-nRF52840-SMD:modified-XIAO-nRF52840-SMD` (2 total, 1 per side).
- **Testing Points:** `TestPoint:TestPoint_Pad_D2.0mm` (4 total, 2 per side).
- **Mousebites:** Clean PCB snapping using `PCM_marbastlib-various:mousebites_5p5mm_easysnap` (3 break-offs).

### 3. Printed Circuit Board Assembly

Designed for rugged reliability and high-profile ergonomics using the custom footprints above.

KiCad PCB Render

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/5277b5f5-4b47-4857-870f-0e312f831fd0" />

KiCad PCBA Render

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/fe0aa805-3a3f-471e-8dc4-206e7a3fa0e6" />

KiCad PCB Back Side

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/e0bf87ad-cf28-4e59-847d-2a7acd6446dd" />

KiCad PCBA Back Side

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/4d254682-7eae-46d1-854a-c2e21442ab51" />

- **Design files:** [`/PCBA`](./PCBA)

### 4. Enclosure & CAD Assembly

Designed from scratch in Autodesk Fusion, featuring integrated battery slots, precise USB-C ports, and secure brass threaded insert sockets.

file structure of fusion

<img width="300" height="510" alt="image" src="https://github.com/user-attachments/assets/994d035a-03be-4a72-b469-e2dc839ba279" />

top case and bottom case together in fusion

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/136446c6-3ab4-4730-a030-2a5b4a0eb14c" />

section analysis in fusion showing the screw assembly

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/e42ffea9-54a8-44b5-b0eb-9a250634d311" />

- **Tolerance Offset:** 0.2 mm case-on-case fit alignment.
- **Plates:** Structural upper case acts as a switch plate, anchoring switches securely.
- **Keycaps:** Custom-modeled 1.00u and 1.50u flat profile MX-stem keycaps tailored for 3D printing.
- **CAD files:** [`/CAD`](./CAD)

## Libraries & References

**KiCad libraries used:**
- [mito-keyboard](https://github.com/mito-keyboard/sito-simplified/tree/sain) — base keyboard library
- [marbastlib](https://github.com/ebastler/marbastlib) — mousebite & hardware footprints
- [Panelization](https://github.com/madworm/Panelization.pretty) — panelization footprints
- [Seeed XIAO KiCad Library](https://github.com/Seeed-Studio/OPL_Kicad_Library/blob/master/XIAO%20Family/XIAO.kicad_sch) — XIAO nRF52840 schematic symbol

**Layout & edge-cut inspiration** (referenced for switch arrangement and board outline conventions):
- [mito-keyboard](https://github.com/mito-keyboard/mito-simplified/tree/main)
- [TaoTeChing](https://github.com/sudo-apt-install-tap/TaoTeChing)
- [OVERRIDE-X3D-Split-Keeb](https://github.com/DevX-Dragon/OVERRIDE-X3D-Split-Keeb)

**Keycap reference model:** [Flat MX Keycaps — Printables](https://www.printables.com/model/467351-flat-mx-keycaps), used as a base to project and re-model custom 1.00u/1.50u profiles.

## Design Notes

**Columnar stagger layout:** Switches placed on a 20 mm grid; second and fourth rows shifted 10 mm up, the middle row shifted 20 mm up, with board edges drawn 5 mm out from the outermost keys.

**Hierarchical sheet grounding:** KiCad hierarchical sheets duplicate net names by default, which merged the left/right ground nets into one. Fixed using sheet-specific power flags (`${SHEETNAME}_GND`), producing distinct `Left_GND` and `Right_GND` nets per half.

**Case construction (Fusion 360):** Built symmetrically — one side of the PCB modeled, then mirrored — with:
- Screw hubs extruded directly from the PCB's mounting hole positions
- A battery cavity sized to the WLY394058 LiPo and centered relative to the four mounting screws
- A USB-C cutout on the lower case wall, offset slightly oversized for clearance

**Keycap modeling:** 1.00u caps built by lofting projected upper/lower faces of a reference keycap, then hollowing and adding a stem + cross-hub. 1.50u caps were derived by splitting the 1.00u shape, spacing the halves 9 mm apart, and bridging the gap. Stem geometry was verified by cutting the actual switch stem shape directly into the keycap model to guarantee fit.

**Upper case (switch plate):** Modeled by projecting all switch bodies into a sketch, offsetting 1 mm around each switch and 1.5 mm along the walls, then extruding to the wall thickness (4.05 mm) with screw-hole pillars extended up from the PCB. Outer walls were thinned via a −0.8 mm facial offset on the curved edges for a lighter profile. Corner/cutout dimensions (14.70 × 14.70 mm switch openings, 0.705 mm corner radius) were carried over from the author's earlier hackpad build.

**Design refinements:** The SoC position, PCB mounting holes, and upper-case mounting holes were all iterated to (1) clear the USB-C cable path symmetrically on both halves, (2) keep mounting holes equidistant from the three nearest switches for insert clearance, and (3) keep the upper-case screw geometry in sync with the final PCB layout.

## Bill of Materials (BOM)

Full sourcing sheet with vendors and pricing: [`/Bill of Materials`](<./Bill of Materials>)

### Electronics & PCBs

- **2x** PCBs (Left & Right snap-apart panels)
- **2x** Seeed Studio XIAO nRF52840 MCU boards
- **2x** WLY394058 3.7V 1000mAh 1S LiPo Batteries (3.9 mm thickness for slim fit)
- **42x** Mechanical switches (MX compatible)
- **42x** Kailh MX Hotswap Sockets
- **42x** SOD-123 SMD Diodes (`1N4148`)
- **4x** `0805` Metric SMD Resistors (2 per side)

### Hardware & Case Assembly

- **M3** Screws (Specific lengths to clamp top and bottom cases)
- **M3** Brass Knurled Heat-Staking Inserts (Pressed into bottom case pillars)
- **1x Set** Custom-printed 1.00u & 1.50u flat keycaps (STEP files included)

### Sourcing

| Component | Vendor |
|---|---|
| PCB Fabrication | JLCPCB |
| Switches & Kailh Hotswap Sockets | Meckeys |
| Diodes, Resistors, SoC, Battery | Robu.in |
| Screws & Knurled Inserts | OnlyScrews |

## Firmware

The board is designed around the **XIAO nRF52840**, so it's intended to run wireless **ZMK** firmware. Firmware configs and keymaps are not yet in this repository — coming soon.
