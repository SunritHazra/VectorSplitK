---
**Title:** VectorSplitK
**Author:** Sunrit Hazra  
**Description:** A wireless high-profile 42 key mechanical split keyboard based on Seeed Studio XIAO nRF52840.  
**Created on:** 30-06-2026  
**Designing Progress (%): 100%**
**Building Progress (%): 0%**
---

# Day 1 — 30.06.2026: Drawing the Schematic & Assigning Footprints

For the split keyboard I have followed the Starter Project Guide from Hack Club Stasis. For the first few minutes, before I started drawing the schmatic, I was asking AI what could I name
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
* Then I placed the XIAO-nRF52840-SMD symbol by copying it from [here](https://github.com/Seeed-Studio/OPL_Kicad_Library/blob/master/XIAO%20Family/XIAO.kicad_sch).
* Followed by that I made the connections with the XIAO-nRF52840-SMD
* Then it was the break offs (mousebites) which I placed in the main sheet.

Here's how the main Schematic looks:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/41074558-e1d6-47a8-8179-e87d7e236dc5" />

Here's how the left schematic looks:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/ea8a6e65-f7e4-4908-bcbc-8609f5bb8108" />

Here's how the right schematic looks:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/8aa38ea9-39c9-45ee-b7cd-703116fdfb38" />

Next were the footprints which were not just simple selections but a whole thought process and understanding. I initially was just trying to copy the footprints without understanding. Turned out that most of the footprints I chose, were replaced by other footprints, and even modified, when I finally understood what I was doing.

Here's how each of them went by: 

1. **Break-offs:** There are 3 of them. I didn't actually chose anything but **panelization:mouse-bite-2mm-slot** came by default since I copied the break-offs from mito-keyboard. But later I switched to **PCM_marbastlib-various:mousebites_5p5mm_easysnap**.
2. **Diodes:** There is a diode for every key, so there are 42 diodes. I had chosen **Diode_SMD:D_SOD-123** since it was suggested in the split keyboard guide.
3. **Mounting Holes:** There are 4 on each side of PCB, so 8 in total. I had selected **MountingHole:MountingHole_3.2mm_M3_DIN965_Pad** for this.
4. **Resistors:** 2 Resistors in each side of PCB. 4 in total. I had selected **Resistor_SMD:R_0805_2012Metric**.
5. **Switches:** 42 of them, 21 on each side of PCB. I initially chose **KEYS: SW_Hotswap Kailh MX** then switched to **Button_Switch_Keyboard:SW_Cherry_MX_1.00u_PCB**.
6. **Testing Points:** 2 on each side of PCB. 4 of them in total. I selected **TestPoint:TestPoint_Pad_D2.0mm** as the footprint.
7. **Integrated Circuit:** 1 XIAO on each side of PCB. 2 in total. I chose **modified-XIAO-nRF52840-SMD:modified-XIAO-nRF52840-SMD** as told in the guide.

Here's the glimpse of the Footprint Assigning Table:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/8a61f3d2-fec3-4f36-808e-dd65e889bda1" />

I ran the ERC. Then it was time for the PCB. I didn't know how to design the edges of the board, place the switches in a grid or what to do. So it seemed like I need some inspiration. So, I opened some repositories of people I know who have built a hackpad, to see how to do what I didn't know. I opened these repositories:

1. [mito-keyboard](https://github.com/mito-keyboard/mito-simplified/tree/main)
2. [TaoTeChing](https://github.com/sudo-apt-install-tap/TaoTeChing)
3. [OVERRIDE-X3D-Split-Keeb](https://github.com/DevX-Dragon/OVERRIDE-X3D-Split-Keeb)

I copied the edge cuts from different sources and found a way of awwanging the switches. My idea was to lay the swtiches in a grid (exactly as in the schematic) and then I move the second and second last rows **"X"** mm up and the middle row **"2X"** mm up. Here **"X"** can be 5 mm or 10 mm depending on the spacing.

Here're the lapses of today's session: [VectorSplitK-LPS-1-D1-1](https://lapse.hackclub.com/timelapse/eYyMFjQSes5m) and [VectorSplitK-LPS-1-D1-2](https://lapse.hackclub.com/timelapse/YLruufpElHKS)

**Total time spent: 3h 50m**

---

# Day 2 — 01.07.2026: Placing Components

It was not time for me to execute the idea that I got the day before. I executed it succesfully in two attempts:

* First, I laid out the grid using the positioning tools initially with 15 mm distance between the switches. Then moved the second and fourth row 5 mm up and the third row 10 mm up. I then drew the edges as well.

* But in the first attempt the switches were too close together. Then after correcting the spacing to 20 mm distance between the switches, moved the second and fourth row 10 mm up and the third row 20 mm up. I then drew the edges again at 5 mm distance from the keys.

This is how the pattern looks like:

<img width="1069" height="564" alt="image" src="https://github.com/user-attachments/assets/5cef9142-aef2-4d24-beaa-60553c8dbd60" />

With the switches placed and the edges drawn, I moved the left side of the PCB to the right and the right to the left.

I was then left with the mousebites, resistors, diodes and the integrated circuits. Here's where and what I placed next:

1. Mousebites between the flat sides of the PCB.
2. XIAO-nRF52840-SMD above the 41st and 42nd key.
3. Each diode above thier respective switches (for SW_41 and SW_42 it was below them)
4. Resistors beside the 41st and 42nd key.

Then I started routing the PCB, but I thought of doing some research using Gemini on the keys I was using and it turned out that I had to change the footprint of my switches as the one I chose were low profile. I wanted high profile mechanical switches.

With that, I changed the footprint for the switches from **Button_Switch_Keyboard:SW_Cherry_MX_1.00u_PCB** to **acheron_MXH.pretty-master:MX100H** for hotswap high profile keys. And I updated the PCB and added models for all the switches and the XIAO-nRF52840-SMD

But then I noticed a connection between the grounds of the two different parts of the PCB. I was confused as I didn't expect this from hierarcheal sheets. I kept it as a problem for the next day.

But, anyways, here's how the PCB looks with the components placed nd edges defined:

<img width="1072" height="565" alt="image" src="https://github.com/user-attachments/assets/e0490416-5e3d-4748-a686-6793f372d27d" />

Here's the lapse of today's session: [VectorSplitK-LPS-2-D2](https://lapse.hackclub.com/timelapse/7gLMdGcFhW8j)

**Total time spent: 5h 05m**

---

# Day 3 — 02.07.2026: PCB Routing

Today's day was about routing the PCB, but before that I had to solve yesterday;s problem first.

I realised that there are power flags for GND and since the names are same, the only way to change them was to make them sheet specific, which seemed impossible as hierarcheal streets are just duplicates. So whatever change I make also applies to the other one as well. Thanks to Gemini that suggested to use **"${SHEETNAME}_GND"** for the GND power flag. This meant that there will be one **Right_GND** and **Left_GND**. Problem solved!

With the problem solved, I routed all the components of the PCB and and editd the edge cuts so it matches the mousebites footprint template.

Next I edited the Front and Back Silkscreen like this:

1. I converted both the Front Fab (after flipping) and Back Fab to Back Silkcreen.
2. Manually named the testing points.
3. Positioned the text centered to the switches.
4. I converted User.Drawings to Front Silkscreen.
5. I converted User.Eco1 to Back Silkscreen.

Then I ran DRC and fixed the last remaining errors and then also exported the gerbers for a little test. I uploaded it on JLCMC and saw if things were okay.

I had also exported the STEP files. So, I imported them into Fusion for making the case. But looking at the model, it seemed like it would be best if I used 1.50u keys for the 41st and 42nd key. So, I made some adjustments to the position of the two key and rotated them 180 degrees.

I needed 3d model to see how it would look but things didn't go as expected. I saw many people have posted whole collections and sets of keycaps ranging from 1.00u all they way to 7.00u. But there was the same problem with every single one of them: They are not symmetrical and fat, but angled. After a lot of searching and several attempts, I decided to add keycaps later becuase I had a lot other thing to focus on at the moment. Like the case and the battery.

For the battery, I searched in google, took guidance from AI and chose [WLY394058 3.7V 1000mAh 1S LiPo Battery](https://robu.in/product/wly394058-1000mah-3-7v-single-cell-rechargeable-lipo-battery/) from Robu.in for each side of my keyboard. I chose it becuase it is just 3.9 mm thick, so I can easily place it under the PCBA without making the lower case much thick.

For the case, I had to make a sketch. Here's what I did:

1. Imported the PCB into the Fusion workspace.
2. Deleted the shapes except the outermost layer (edge cuts)
3. Deleted the extra faces in the rounded corners.
4. Redrew the sketch with no rounded corners.

I decided to work on this for the next day where I will use offsets and fillets to form the lower case.

But here's the full routed PCB:

<img width="1067" height="567" alt="image" src="https://github.com/user-attachments/assets/21ae7e6a-41a7-459e-be00-d6eb4a80c987" />

Here're the lapse of today's session: [VectorSplitK-LPS-3-D3-1](https://lapse.hackclub.com/timelapse/wJ1pVrpDzbS-), [VectorSplitK-LPS-3-D3-2](https://lapse.hackclub.com/timelapse/x-hgnSQhrMK1) and [VectorSplitK-LPS-3-D3-3](https://lapse.hackclub.com/timelapse/ZtfF6PPONsYK)

**Total time spent: 6h 40m**

---

# Day 4 — 03.07.2026: Trying My Best

I started working with this straight sketch which I firstly mirrored to make it symmetric. I added offset of 2 mm to it which represented the outer edges of the lower case.

The PCB was placed directly above the sketch, so I had to move apart the two sides of the PCB which was really hard since the way the components were arranged required manual selection to first organize them in the browser and them move them. Trying to move the two sides of the PCB apart as bodies just doesen't work.

I had to take a drastically different approach to this. 

Take this imge for example. Every single diode, switch and resistor is a differnet component. This means that either I have to mannually select or take a drastically different approach to this.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/7a340392-f9d8-4634-b1e6-d0ec855a9429" />

It seemed like using simpler STEP file was the way to go since the previous one had tracks, vias and all the little detials. So, I exported the file again with the minimal details. But it still was far from practical. I tried manually selecting the switches, resistors, diodes, one by one to seperate them into different components. Fusion has got to give a way for people to select multiple components from the workspace selection alone, like we do with meshes in Blender.

I have an idea. Let's explore it the next day.

Here's the lapse of today's session: [VectorSplitK-LPS-4-D4](https://lapse.hackclub.com/timelapse/2fYtNShAUCum)

**Total time spent: 1h 10m**

---

# Day 5 — 04.07.2026: Modelling the Lower Case

For the simple version of the model, both sides are supposed to exactly symmetrical and mirrored. Here's how I executed yesterday's idea:

1. Went into KiCad and deleted the right side of the PCB including the mousebites.
2. Redrew the board's left edge in Edge Cuts.
3. Exported it with minimal settings without saving.
4. Imported into Fusion and moved it a little to the left.
5. Mirrored the whole component on the other side.

Simultaneously, I also added fillets and offsets to the sketch and placed them to the left. Then I placed my PCB exactly over it.

Then it was time for the lower casing. Here's what I did:

1. Extended the existing hubs for the screws required to mount the PCB to the lower body of the casing, from the pcb itself.
2. Added a body sized exactly in the dimentions of [WLY394058 3.7V 1000mAh 1S LiPo Battery](https://robu.in/product/wly394058-1000mah-3-7v-single-cell-rechargeable-lipo-battery/) as I chose it before.
3. Positioned the battery in the centre of the PCB based on the rectangle formed due to the four points from the screw position.
4. In KiCad, moved the position of the testing points to the bottom part of the PCB, and routed them.
5. Used the Battery's position as reference to extrude a sketch that will surround the battery pack.

With that, the lower case was completed, and it looks like this:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/249c9f63-322f-4050-8047-b0a26c1e658d" />

Here's the lapse of today's session: [VectorSplitK-LPS-5-D5](https://lapse.hackclub.com/timelapse/6bBPs-QqJmJs)

**Total time spent: 2h 05m**

---

# Day 6 — 05.07.2026: Modeling the Keycaps

The very first thing I did was this: I imported the updated STEP file with the correct position of the testing points into Fusion and placed it properly and mirrored it to correct position.

Next were the keycaps. Due to the struggle I was went through to search for the keycaps, it seemed like the best way was to model the keycaps. This meant that I had to 3D print my keys, most likely. Well, that is not a problem since I have a 3D printer thanks to Construct. I thus fimalised the idea of self-modelling the keys.

I needed some source for the model, so I started searching in Printables. For reference I imported the 1u model from [Printables](https://www.printables.com/model/467351-flat-mx-keycaps).

I first modeled the 1.00u keycap and then the 1.50u keycap.

Here's how I did the 1.00u keycap:

* I projected the upper and lower face of the imported keycap.
* Used extrusions to form a flat shape representing the lower face.
* Used loft to join the lower and upper face, forming the shape.
* Used extrusion to cut out the inner part of keycap body.
* Used projected sketch to extrude out the stem and +-like hub.

The 1.00u keycap:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/c063af4f-78ea-456d-a1e7-c4b87b28e8bc" />

Here's how I did the 1.50u keycap:

* I deleted the keycap stem and +-like hub.
* Split the 1.00u keycap in half.
* Moved both the parts apart by 4.5 mm apart, making the distance 9 mm between them.
* Used extrude to bridge the gap.
* Used the old sketch to form the +-like hub.

The 1.50u keycap:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/b5eb427d-dd2c-4336-9424-ced0e5985541" />

But I was not totally confident with the internal dimensions of the +-like section. So, I did this:

1. Deleted the like part.
2. Copied the moving part of the switch.
3. Used joint to position it over the stem section.
4. Used combine cut to carve out the geometry.
5. Rotated it and repated the action.

I also made sure that the same geometry exists at the stem section of both the 1.00u and 1.50u keycaps.

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/1d415397-c43c-4553-b555-7b1499a1ef53" />

With the 1.00u and 1.50u keycaps modeled, it was finally the time to integrate them into the PCBA. Thus, I went into kiCad and then I updated both the **MX100H** and **MX150H** footprints by adding the models.

Then I went into KiCad, deleted one side of the PCB and then exported the STEP file (again) with the simplest possible settings, imported it into fusion, positioned the PCB, mirrored the PCB and finally arranged the components in the browser.

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/db8059a2-9102-4b3e-8784-6feb1774e44e" />

I then made some clearence adjustments in the model and made sure nothing overlaps, and everything fits gracefully.

Then I noticed there was no hole for the USB-C cable to get in. So, I made an extrusion to cut through the lower case wall:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/4d4704b3-1298-42bb-8e61-fbe1d199c7f5" />

After that I deleted the inner part and then used offset to make the hole a little bigger:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/8bf3363d-8858-42fd-8ff0-da7921443aad" />

Next thing which I had to model was the upper case, which I will do tommorow.

Here's how the Split keyboard looks:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/5eff51ac-2099-4242-aff3-b4fc18a26942" />

Here's the lapse of today's session: [VectorSplitK-LPS-6-D6](https://lapse.hackclub.com/timelapse/r0XjsalRWVzc)

**Total time spent: 3h 10m**

---

# Day 7 — 06.07.2026: Modelling the Upper Case

For modelling the upper case, I had a design in mind where the switches will be firmly attached to the upper case and the PCB, so that they act as one single part of the same system. I wanted the screw hoes to extend to the upper face of the upper case.

I needed to figure out a way using which I could know the exact shape needed for properly attaching the switches to the upper case. For this, I visited my hackpad's model to study the dimensions of the uppercase.

I found out that the square was 14.70 mm by 14.70 mm, with rounded corners having length of 0.705 mm. Good thing that I came to know the dimensions but it proved futile.

Here's what I did next:

1. Made a sketch and projected every switch body on the sketch.
   <img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/35ad7ad6-6285-4fd1-8a96-6f028b36646b" />
2. Extruded the sketch and moved it up, as the sketch was on the floor.
   <img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/731b3b73-5c4f-43b0-b90d-62bea4fc97ed" />
3. Mirrored the body, arranged both of the bodies in the Browser and added appearence.
   <img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/dc109f5f-f171-44db-9b85-7cc302fec086" />
4. Made a new sketch and made 1 mm offset for switches and 1.5 mm offset for the walls.
   <img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/0e49fec5-ec81-476c-8a48-a95972b9e611" />
5. Extruded the switch offsets by 1 mm and the wall offsets by 4.05 mm, to make it thicker.
   <img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/06252676-01e1-40ca-990d-384f1b534b5f" />
6. Extended the screw hole pads to the uppercase, and then extruded in till the PCB.
   <img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/57c3c739-da9a-4853-a536-de2c18fa46f1" />
7. Made the outer wall thinner by using facial offsets on the curved faces by -0.8 mm.
   <img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/6504d556-e3e6-4401-901a-5bb9a53c7d5e" />
8. Combined the parts of the screw hubs and mirrored the combined body.
   <img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/18a5f651-48cd-4790-b75a-b9a7b193f031" />

With this, the upper case was completed, leaving almost nothing to model.

Here's how the Split Keyboard looks:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/66cbb42b-4fb9-4d8a-a126-4891d20101de" />

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/7fa85380-3b1d-42a2-866a-e7a369bbc0db" />

Here's the lapse of today's session: [VectorSplitK-LPS-7-D7](https://lapse.hackclub.com/timelapse/vuXKPHH6yCxN)

**Total time spent: 1h 05m**

---

# Day 8 — 07.07.2026: Journaling

Journaled the day #1 (partly)

Day #1

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/9c148fe5-4e82-41d5-a49e-d1a01fc9735f" />

Here's the lapse of today's session: [VectorSplitK-LPS-8-D8](https://lapse.hackclub.com/timelapse/1Yx_xMfhucab)

**Total time spent: 1h 05m**

---

# Day 9 — 08.07.2026: Journaling

When I was about to continue journaling day #1, I saw I lost all the changes made yesterday as I had forgotten to save my work. So, I played yesterday's sketch and using the screenshots, copied the text and retrived my writing from yesterday.

<img width="1271" height="713" alt="image" src="https://github.com/user-attachments/assets/2aeb20a0-7d00-441e-864b-0604fa802c56" />

Here's the lapse of today's session: [VectorSplitK-LPS-9-D9](https://lapse.hackclub.com/timelapse/5DwjW-JZZNnw)

**Total time spent: 0h 30m**

---

# Day 10 — 10.07.2026: Journaling

Journaled the days #1 (full), #2, #3, #4, #5, #6 (partly) and #9.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/0c8b5a8a-5b19-4e2e-b3ce-754df5d546b2" />

Here're the lapses of today's session: [VectorSplitK-LPS-10-D10-1](https://lapse.hackclub.com/timelapse/rkP9sRGi9QtF) and [VectorSplitK-LPS-10-D10-2](https://lapse.hackclub.com/timelapse/IaWoMt11Kqi8)

**Total time spent: 4h 35m**

---

# Day 11 — 11.07.2026: Journaling & Modelling

For the first one hour and thirty minutes, I spent time on journaling days #7 and #8 and adding more details to days #1, #4, #5, #6 and #7.

I had actually not completed journaling but I was bored out of my mind, so it felt like it is better to spend time on something else like modelling. So, I needed something to work on. To be specific, a problem to work on.

So, I started to investigate the problems with the system, so that I can work on them and I found these three in my investigation:

1. **SoC Type C Hole:** The current position of the Seeed Studio XIAO nRF52840 was such that it would be very tight for the Type C cable, as it might rub against the lower case. Or even worse, it could not even fit. Thus I had to shift the position of the SoC a little so that it is both symmetrical and also ensures proper fit for the cable. 

2. **PCB Mounting Holes:** The positions of the mounting holes was not very good resulting in the problem of adding knurled inserts. Thus I have to position them exactly in the centre of the nearby switches.

3. **Upper Case Mounting Holes:** The position of the holes on the Upper Case depended on the sketch of projection of the PCB itself. This meant that I had to update the PCB.

I then opened KiCad and one by one solved each problem like this:

* For the first one I first made sure what the position of the Seeed Studio XIAO nRF52840 was on the board relative to its closest corner on the Edge. Then updated that position and copied it to the other side as well with mirrored position. Then imported the PCB after routing.

* For the mounting holes, I also made a similar approach and positioned them at a certain location where the centre of the hole is quidistant from the 3 switches surrounding it. Then imported the PCB after routing.

* For the uppercase, I used the updated PCB to project sketch and use it, after routing the PCB and exporting it. The imported PCB had the correct positions that gave more room for the knurled inserts.

After having the position of the mounting holes fixed, I also centered the battery space by making an offset of 0.13 mm.

Here's how the keyboard looks at last:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/d035b426-b603-4154-b5b9-608c26c7af1f" />

Here's the lapse of today's session: [VectorSplitK-LPS-11-D11](https://lapse.hackclub.com/timelapse/CPPEX1s_R7dv)

**Total time spent: 5h 15m**

---

# Day 12 — 13.07.2026: Making the BOM

I started with a minor change I forgot to make the day before, which was adding offsets for the Upper Case so it actually fits with the Lower Case. Previously, there was zero offset, but today I added 0.2 mm offset.

Then I exported my PCB into VectorSplitK_Gerber.zip with all the nescessary files.

With the PCB exported, I simultaneously opened Excel and copied my BOM format from one of my other project and started adding placeholders. I opened JLCPCB and uploaded the ZIP and wasn't quite happy with the numbers. Actually, I don't mind paying $16.40 for the PCB but the shipping is literally $16.73 with E-POST and there are additional customs that Forge ain't gonna pay.

Next I obviously went for the keys, which took a lot of time. I had planned to print my Keycaps, so that was nonw of my concerns. Initially I thought of searching in Amazon or Flipkart, but the deals were pathetic. So, I settled on Cosmic Bite for the keys and later changed to Meckeys, as for the Kalih socket, I was buying from Meckeys.

Next, one by one I went through the Footprint table and chose component for the diodes, resistors, SoC and battery. I chose all of these from Robu.in.

For the screws and the knurled inserts, I had chosen them from OnlyScrews.

Finally, this is the complete BOM:
	
<img width="1776" height="460" alt="image" src="https://github.com/user-attachments/assets/3aff129f-a53d-4340-9f2d-5316817ebed3" />

Here's the lapse of today's session: [VectorSplitK-LPS-12-D12](https://lapse.hackclub.com/timelapse/eZuC9CHMVYUR)

**Total time spent: 3h 50m**

---

# Day 13 — 16.07.2026: Journaling & Adding Slikscreen Text

I mostly spent time journaling days #8, #9, #10, #11, #12 and #13 and added pictures to days #1, #2, #3, #4, #5, #7, and the new ones.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/a0e7bfc8-192e-4d89-b2de-51805e5d2e85" />

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/e1f521f3-f59a-4a09-a7b9-771da3f76d7f" />

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/f8144d9f-15b9-4e73-be9c-f6ae7dad5bed" />

I also added text for my name, name of the projet and month and year on which I made it, in the PCB F.Slikscreen like my previous PCBs. Then I re-exported the Fabrication outputs.

Here's what I did to the PCB:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/b3e1e8ef-e9e1-44f7-a322-619f9ca8c23f" />

Here're the lapses of today's session: [VectorSplitK-LPS-13-D13-1](https://lapse.hackclub.com/timelapse/p4w9sKsDkTIn) and [VectorSplitK-LPS-13-D13](https://lapse.hackclub.com/timelapse/TeylD5ZsRaPr)

**Total time spent: 2h 20m**

---

# Day 14 — 17.07.2026: Completing the Repository

Today was all about compiling the fruits of the last two weeks of hard work and making the project public-ready. I focused entirely on documentation, visual assets, and setting up the GitHub repository.

Here is exactly what went down today:

* **Visual Assets:** Captured high-quality, clean renders of the completed 3D model from Fusion Teams, Autodesk Fusion, and the PCB layouts from KiCad. These visuals showcase the final assembly, including the custom 1.00u and 1.50u keycaps, the lower case battery compartments, and the physical alignment of the USB-C ports.

* **Documentation (README.md):** Wrote the comprehensive project README.md to serve as the landing page for the repository. I used AI solely as a second set of eyes to polish up my grammar, spelling, and punctuation, ensuring the write-up accurately represents the technical details of the design process.

* **Repository Setup & Licensing:** Cloned my local desktop development files into the remote GitHub repository, organized the folders for Gerbers, CAD files, and logs, and added an open-source license to protect and share the work.

I also added a section in the [README](./README.md) where I wrote how I have used AI in this project, in the section **"AI as a Design Collaborator"**.

With the repository fully structured and the design phase sitting at a proud 100%, the VectorSplitK is officially ready to transition from a digital design to a physical build.

Here's a screenshot of the repository itself:

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/4fbfc491-a1af-4442-8d49-efa5ef5c6214" />

Here's the lapse of today's session: [VectorSplitK-LPS-14-D14]()

**Total time spent: 3h 20m**

---

# Day 15 — 18.07.2026: The Firmware

Today was the final thing that I had to do before submission: the code.

<img width="1366" height="733" alt="image" src="https://github.com/user-attachments/assets/e51dc886-6f63-46a2-bb43-cc9554e524dc" />

I added the code to the Firmware.

**Total time spent: 6h 00m**

---
