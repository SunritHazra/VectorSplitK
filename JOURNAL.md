---
**Title:** VectorSplitK
**Author:** Sunrit Hazra  
**Description:** A 42 key split keyboard powered by Seeed Studio XIAO nRF52840.  
**Created on:** 2026-06-30  
**Progress (%): 60%**
---

# Day 1 — 30.06.2026: Drawing the Schematic and Assigning Footprints

For the split keyboard I have followed the Started Project Guide from Hack Club Stasis. For the first few minutes, before I started drawing the schmatic, I was asking AI what could I name
my project. And I chose "VectorSplitk" as the name of my project, which follows the same naming format as my previous starter electronics projects like hackpad and devboard.

In this naming system, there are three parts:

* The first phrase is a either a random word or "Hackro".
* The second phrase is a short phrase taken out of the thing's real name like "Dev", "Pad", or "Split".
* The third part is just a letter like "X" or "D"

Thus giving the name "VectorSplitk".

With that done, I opened KiCad and started reading the guide at the same time.

The first step for me was to install the libraries. To be specific, the following libraries:

1. [mito-keyboard](https://github.com/mito-keyboard/sito-simplified/tree/sain)
2. [marbastlib](https://github.com/ebastler/marbastlib)
3. [Panelization](https://github.com/madworm/Panelization.pretty)

Then I started drawing the schematic with the hierierchy determined for left and right sides as stated in the guide. This was my first time working with hierarcheal sheets.

Here's how I did the schematic:

* First I made the matrix using labels, exactly as shown in the tutorial.
* Then I placed the XIAO-nRF52840-SMD symbol by copying it from [https://github.com/Seeed-Studio/OPL Kicad Library/blob/master/XTA0%20Family/XTAO.kicad sch] (here).
* Followed by that I made the connections with the XIAO-nRF52840-SMD
* Then it was the break offs (mousebites) which I placed in the main sheet.

Next were the footprints which were not just simple selections but a whole thought process and understanding. I initially was just trying to copy the footprints without understanding. Turned out that most of the footprints I chose, were replaced by other footprints, and even modified, when I finally understood what I was doing.

Here's how each of them went by: 

1. **Break-offs:** There are 3 of them. I didn't actually chose anything but **panelization:mouse-bite-2mm-slot** came by default since I copied the break-offs from mito-keyboard.
2. **Diodes:** There is a diode for every key, so there are 42 diodes. I had chosen **Diode_SMD:D_SOD-123**.
3. **Mounting Holes:** There are 4 on each side of PCB, so 8 in total. I had selected **MountingHole:MountingHole_3.2mm_M3_DIN965_Pad** for this.
4. **Resistors:** 2 Resistors in each side of PCB. 4 in total. I had selected **Resistor_SMD:R_0805_2012Metric**.
5. **Switches:** 42 of them, 21 on each side of PCB. I initially chose **KEYS: SW_Hotswap Kailh MX** then switched to **Button_Switch_Keyboard:SW_Cherry_MX_1.00u_PCB**.
6. **Testing Points:** 2 on each side of PCB. 4 of them in total. I selected **TestPoint:TestPoint_Pad_D2.0mm** as the footprint.
7. **Integrated Circuit:** 1 XIAO on each side of PCB. 2 in total. I chose **modified-XIAO-nRF52840-SMD:modified-XIAO-nRF52840-SMD** as told in the guide.

I ran the ERC. Then it was time for the PCB. 

Here're the lapse of today's session: [VectorSplitK-LPS-1-D1-1](https://lapse.hackclub.com/timelapse/eYyMFjQSes5m) and [VectorSplitK-LPS-1-D1-2](https://lapse.hackclub.com/timelapse/YLruufpElHKS)

**Total time spent: 3h 50m**

---

# Day 2 — 01.07.2026: Placing Components and Routing

Here's the lapse of today's session: [VectorSplitK-LPS-2-D2](https://lapse.hackclub.com/timelapse/7gLMdGcFhW8j)

**Total time spent: 5h 05m**

---

# Day 3 — 02.07.2026: idk go see urself

Here're the lapse of today's session: [VectorSplitK-LPS-3-D3-1](https://lapse.hackclub.com/timelapse/wJ1pVrpDzbS-), [VectorSplitK-LPS-3-D3-2](https://lapse.hackclub.com/timelapse/x-hgnSQhrMK1) and [VectorSplitK-LPS-3-D3-3](https://lapse.hackclub.com/timelapse/ZtfF6PPONsYK)

**Total time spent: 6h 40m**

---

# Day 4 — 03.07.2026: 

Here's the lapse of today's session: [VectorSplitK-LPS-4-D4](https://lapse.hackclub.com/timelapse/2fYtNShAUCum)

**Total time spent: 1h 10m**

---

# Day 5 — 04.07.2026: 

Here's the lapse of today's session: [VectorSplitK-LPS-5-D5](https://lapse.hackclub.com/timelapse/6bBPs-QqJmJs)

**Total time spent: 2h 05m**

---

# Day 6 — 05.07.2026: 

Here's the lapse of today's session: [VectorSplitK-LPS-6-D6](https://lapse.hackclub.com/timelapse/r0XjsalRWVzc)

**Total time spent: 3h 10m**

---

# Day 7 — 06.07.2026: 

Here's the lapse of today's session: [VectorSplitK-LPS-7-D7](https://lapse.hackclub.com/timelapse/vuXKPHH6yCxN)

**Total time spent: 1h 05m**

---

# Day 8 — 07.07.2026: Journaling

Here's the lapse of today's session: [VectorSplitK-LPS-8-D8](https://lapse.hackclub.com/timelapse/1Yx_xMfhucab)

**Total time spent: 1h 05m**

---

# Day 9 — 08.07.2026: Journaling

Here's the lapse of today's session: [VectorSplitK-LPS-9-D9](https://lapse.hackclub.com/timelapse/5DwjW-JZZNnw)

**Total time spent: 0h 30m**

---

# Day 10 — 10.07.2026: Journaling

Here's the lapse of today's session: []()

**Total time spent: 0h 00m**

---
