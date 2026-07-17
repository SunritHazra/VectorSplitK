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

### 2. PCB & PCBA

Designed for rugged reliability and high-profile ergonomics using custom footprints.

kicad pcb

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/5277b5f5-4b47-4857-870f-0e312f831fd0" />

kicad pcba

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/fe0aa805-3a3f-471e-8dc4-206e7a3fa0e6" />

kicad pcb flip side

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/e0bf87ad-cf28-4e59-847d-2a7acd6446dd" />

kicad pcba flip side

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/4d254682-7eae-46d1-854a-c2e21442ab51" />

- **Switch Footprints:** High-profile `acheron_MXH:MX100H` (1.00u) and `acheron_MXH:MX150H` (1.50u) hotswap-ready switches.
- **Mousebites:** Clean PCB snapping using `PCM_marbastlib-various:mousebites_5p5mm_easysnap`.
- **Design files:** [`/PCBA`](./PCBA)

### 3. Enclosure & CAD Assembly

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

## Firmware

The board is designed around the **XIAO nRF52840**, so it's intended to run wireless **ZMK** firmware. Firmware configs and keymaps are not yet in this repository — coming soon.

## Gallery

More build photos and progress shots: [`/Gallery`](./Gallery)

## License

*(Add your license here, e.g. MIT / CERN-OHL-S — see LICENSE)*
