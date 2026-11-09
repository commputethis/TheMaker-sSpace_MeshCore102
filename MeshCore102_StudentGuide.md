<!-- Use guide-print.css when exporting this Markdown to PDF. -->

<div class="cover">

![MeshCore 102: Build The People's Repeater](images/event-banner.png)

# MeshCore 102

## Build The People's Repeater

### Student Guide and Build Instructions

**The Maker's Space · November 2026**

Build a solar-powered MeshCore repeater from a Harbor Breeze solar-light enclosure, a Seeed Studio XIAO nRF52840, and a Wio-SX1262 LoRa radio.

</div>

<div class="page-break" style="page-break-after: always; break-after: page;"></div>

## What You Will Build

The People's Repeater is a compact, solar-powered MeshCore relay for the 915 MHz band. The original light is removed; the finished repeater has an outdoor antenna and **does not have a light**.

<figure class="keep-together"><img src="images/installed-reference.png" alt="Completed repeater mounted outdoors"><figcaption>Example finished repeater. The exact PETG mount used in class may differ.</figcaption></figure>

## MeshCore Roles and Room Servers

- A **companion** gives a person access to the mesh.
- A **repeater** extends useful coverage by forwarding packets toward their destinations.
- A **Room Server** is a shared message board. It stores posts and can deliver unseen history when a user returns, unlike an ordinary channel where a message can be missed while the user is out of range.

A Room Server and repeater solve different problems. MeshCore recommends separate devices for the best experience; enabling repeat behavior on a Room Server does not provide the full repeater feature set. This class builds a dedicated repeater. See the [MeshCore FAQ](https://github.com/meshcore-dev/MeshCore/blob/main/docs/faq.md).

<div class="page-break" style="page-break-after: always; break-after: page;"></div>

## Parts

<figure class="keep-together"><img src="images/parts-core.jpg" alt="Core electronic parts"><figcaption>Core electronics and power components. The Wio is the lower board beneath the XIAO.</figcaption></figure>

### Electronics and power

- Harbor Breeze solar light with included **1500 mAh 18650 battery**
- Seeed Studio **XIAO nRF52840** and **Wio-SX1262** LoRa radio
- **ACEIRMC CN3065** mini solar LiPo charger
- 100 mm female-socket **JST PH 2.0** silicone-wire cables

### Antenna system

- **ALFA Network AOA-915-5ACM**, 5 dBi outdoor 915 MHz antenna
- 6 in / 15 cm **U.FL1-to-N-female** RG178 pigtail
- Waterproof self-fusing silicone tape

> The small antenna supplied attached to the Wio is used only during pre-build setup, then disconnected once and set aside. It is not used in the finished repeater.

<figure class="keep-together"><img src="images/parts-hardware.jpg" alt="Enclosure, gasket, mounts, antenna, and hardware"><figcaption>Antenna and enclosure hardware, including the PETG component mount and connector clamp.</figcaption></figure>

### Enclosure and mounting

- 3D-printed **TPU gasket** and **PETG component mount**
- 3D-printed [**antenna connector clamp**](https://www.printables.com/model/1761740-xiao-nrf52840-wio-sx1262-antenna-clamp)
- Zip ties **or** hose clamps for attaching the mount to a pole
- Original enclosure screws and original mount screw and nut

The [Harbor Breeze solar mesh-node models](https://www.printables.com/model/1748950-26-harbor-breeze-solar-mesh-node-mounts-meshtastic) page contains the component mount shown here, alternate mounts, and the TPU gasket.

> Put all removed screws and the separate mount nut in a parts tray. They are reused; they are not extra hardware.

### Battery note

The class uses the included 1500 mAh 18650. A larger-capacity compatible 18650 may provide more winter reserve, but verify chemistry, voltage, size, polarity, terminals, protection, and charger compatibility.

## Safety Rules

- Remove the battery immediately after opening the enclosure. Use fingers or a nonconductive tool—never a metal tool.
- Keep the battery out during cutting, desoldering, soldering, and rewiring.
- Never short, puncture, crush, overheat, or reverse an 18650.
- Verify polarity with a meter; connector shape and wire color alone are not proof.
- Never transmit without an antenna connected.
- Stop for unexpected heat, odor, smoke, uncertain polarity, or an unexpected measurement.

## Placement Before the Build

- Favor useful height, open surroundings, and a clear path toward the area served.
- Keep the vertical antenna clear of nearby metal where practical.
- Give the solar panel several hours of direct sun, including during winter.
- In Indiana, a generally southerly exposure is a useful starting point, adjusted for shade.
- Choose a safe, permitted, stable, serviceable location and orient seams to shed water.

Planning tools:

- [MeshMapper](https://fwa.meshmapper.net/) for purpose and radio-path planning
- [Solar tilt-angle calculator](https://www.baess.app/tools/solar-tilt-angle-calculator) for panel-angle planning

<div class="page-break" style="page-break-after: always; break-after: page;"></div>

# Build Guide

## 1. Flash and Configure Before Disassembly

Leave the supplied Wio antenna attached during computer setup.

1. Flash the current compatible MeshCore **repeater** firmware.
2. Select the correct legal regional radio preset.
3. Follow the [OKI Mesh repeater configuration guide](https://docs.okimesh.org/books/meshcore-I9o/page/repeater-configuration) to set the repeater name and class settings.
4. Confirm normal startup.
5. Power down, disconnect the supplied antenna once, and set it aside.

Naming standard: `StateCode.CountyCode.descriptiveName`.

- Allen County: `IN.ALL.descriptiveName`
- Local Fort Wayne convention: `IN.ALL.FWA.descriptiveName`
- [Repeater naming reference](https://docs.okimesh.org/books/meshcore-I9o/page/repeater-naming)
- [County abbreviations](https://docs.okimesh.org/books/meshcore-I9o/page/county-abbreviations)

## 2. Retain the Mount Hardware

<figure class="keep-together"><img src="images/build-01.jpg" alt="Mounting screw and nut"><figcaption>Retain the mounting screw and separate matching nut. Both are reused.</figcaption></figure>

## 3. Switch Off and Cut Away the Light

Verify the solar-light switch is **OFF**, then cut the wire joining the enclosure to the light. The exact cut location is not important because the entire wire will eventually be removed.

<figure class="keep-together"><img src="images/step-03-cut-wire.jpg" alt="Cutting the light wire"><figcaption>Switch the light off before cutting the wire.</figcaption></figure>

## 4. Open the Enclosure and Remove the Battery

Remove and retain the enclosure screws. Open the cover carefully, then remove the 18650 with fingers or a nonconductive tool—never a metal tool. Keep it out until the wiring inspection is complete and the open-unit test is ready. After removing the battery, pull the cut wire through its feed-through and remove and retain the two screws holding the switch/PCB.

<figure class="keep-together"><img src="images/step-04-switch-pcb.jpg" alt="Pulling the wire through and retaining the PCB screws"><figcaption>Pull the wire through only after opening the enclosure and removing the battery.</figcaption></figure>

## 5. Remove the Unused Original Wiring

Clip the cut light wire at both PCB connections, both solar-panel leads at the PCB, and the negative battery lead at the PCB. Retain the PCB and switch; they will be used only as a switch inline with CN3065 SYS OUT.

<figure class="keep-together"><img src="images/build-03.jpg" alt="Removing old PCB wiring"><figcaption>Clip the old light and solar-panel wires at the PCB.</figcaption></figure>
<figure class="keep-together"><img src="images/build-04.jpg" alt="Battery negative and gasket removal"><figcaption>Disconnect battery negative.</figcaption></figure>

## 6. Open the Two Marked PCB Traces

With the battery and panel disconnected, identify the two marked copper paths.

**The instructor will provide additional instructions for completing and checking this modification.**

<figure class="keep-together full-width"><img src="images/pcb-trace-modification.jpg" alt="PCB traces to open"><figcaption>The instructor will demonstrate the two marked PCB modifications.</figcaption></figure>

## 7. Install the TPU Gasket

Remove the foam gasket, clean the channel, and seat the TPU gasket evenly.

<figure class="keep-together"><img src="images/build-05.jpg" alt="Gaskets"><figcaption>Factory gasket removed; TPU replacement ready.</figcaption></figure>
<figure class="keep-together"><img src="images/build-06.jpg" alt="Installed TPU gasket and corrected JST leads"><figcaption>TPU gasket installed.</figcaption></figure>

## 8. Rewire the Battery Holder

Desolder the original negative wire; it is not reused. Install the negative JST conductor. Then desolder the original positive wire and install the positive JST conductor.

<figure class="keep-together"><img src="images/build-07.jpg" alt="Battery negative rewiring"><figcaption>Remove the old negative wire and install the JST negative.</figcaption></figure>
<figure class="keep-together"><img src="images/step-08-battery-positive.jpg" alt="Battery positive rewiring"><figcaption>Complete the positive battery-holder connection.</figcaption></figure>

## 9. Add the Solar-Panel JST Lead

The panel terminals are unlabeled. Change only **one conductor at a time**: remove one original wire and immediately install its matching JST conductor before touching the other terminal.

<figure class="keep-together"><img src="images/step-09-panel-wiring.jpg" alt="Solar-panel JST wiring"><figcaption>Change the panel wires one at a time, then inspect the completed JST lead.</figcaption></figure>

## 10. Wire the XIAO and Retained Switch

- Original battery-holder positive wire to XIAO `BAT+`
- JST negative conductor to XIAO `BAT−`
- That JST lead's positive conductor to the retained PCB, placing the switch inline with CN3065 `SYS OUT`

<figure class="keep-together"><img src="images/step-10-xiao-switch.jpg" alt="XIAO and retained switch wiring"><figcaption>Wire the XIAO battery terminals and retained switch PCB.</figcaption></figure>

## 11. Connect the CN3065

> **JST polarity:** The class cables have already been corrected by swapping the red and black positions where needed. Still verify actual positive and negative polarity before connecting them.

Connect the three verified JST plugs for solar input, battery, and system output. Do not install the battery yet.

<figure class="keep-together"><img src="images/step-11-cn3065.jpg" alt="Three JST plugs connected to CN3065"><figcaption>Connect all three verified JST plugs to the appropriate CN3065 positions.</figcaption></figure>

## 12. Install the N Connector in the PETG Mount

Feed the pigtail through the mount, then push the connector upward from the bottom. Align its flat sides before applying gentle force. Install the tooth lock washer, then flat washer, then nut.

<figure class="keep-together"><img src="images/step-12-pigtail-mount.jpg" alt="Feeding the pigtail through the mount"><figcaption>Feed the pigtail through the PETG mount before seating the N connector.</figcaption></figure>
<figure class="keep-together"><img src="images/build-11.jpg" alt="N connector and washer order"><figcaption>Align the flats and use the illustrated washer order.</figcaption></figure>
<figure class="keep-together"><img src="images/build-12.jpg" alt="Tightened connector and pigtail"><figcaption>Tighten without crushing PETG, then feed the U.FL end inside.</figcaption></figure>

## 13. Attach the Mount, Antenna, and Route the Pigtail

Attach the mount with the retained screw and nut. Keep the coax bend gentle. Attach and hand-tighten the ALFA antenna on the exterior N connector.

<figure class="keep-together"><img src="images/build-13.jpg" alt="Pigtail and mount"><figcaption>Pigtail routed and mount attached.</figcaption></figure>

## 14. Reinstall the Switch and Connect the Radio

Before reinstalling the switch/PCB, make sure the rubber switch boot is seated correctly to keep moisture out. Reinstall the switch/PCB with its two original screws, then cover it with painter's tape. Press the U.FL plug straight down onto the Wio socket; do not twist or pull on the coax.

<figure class="keep-together"><img src="images/build-14.jpg" alt="Switch insulation and Wio connection"><figcaption>Seat the rubber boot, reinstall the screws, apply tape, and connect the pigtail.</figcaption></figure>

## 15. Install the Antenna Connector Clamp

Support the boards and pigtail while installing the clamp. Do not flex the boards or lever against U.FL.

<figure class="keep-together"><img src="images/build-15.jpg" alt="Connector clamp"><figcaption>Position and secure the connector clamp.</figcaption></figure>

## 16. Clean the Panel, Inspect, Install the Battery, and Test

Remove the solar-panel sticker. Use Goo Gone to remove adhesive residue, then clean the panel with isopropyl alcohol. Arrange components and inspect polarity, solder joints, trace cuts, JST positions, switch insulation, and pigtail seating. Install the 18650 with correct polarity and test startup, the saved settings and name, LoRa relay through the ALFA antenna, and charging response. Disconnect immediately for heat, odor, smoke, or abnormal behavior.

<figure class="keep-together"><img src="images/step-16-sticker.jpg" alt="Removing the solar-panel sticker"><figcaption>Remove the sticker and clean the panel before testing.</figcaption></figure>

## 17. Close and Finish

After tests pass, arrange wires clear of screw posts, close the enclosure, and reinstall original screws gradually.

<figure class="keep-together"><img src="images/step-17-finished.jpg" alt="Finished repeater"><figcaption>Inspect the finished repeater. The finished unit has no light.</figcaption></figure>

## 18. Weatherproof and Mount

Confirm that the hand-tightened ALFA antenna connection is clean and dry. Stretch and overlap self-fusing silicone tape across the complete joint without covering the radiating body.

Use zip ties or hose clamps to attach the PETG mount to a pole. They are for pole mounting, not internal cable management or strain relief. Keep the antenna vertical, set the panel for seasonal sun, and confirm permission, stability, safe access, and water-shedding orientation.

<div class="page-break" style="page-break-after: always; break-after: page;"></div>

## Final Acceptance Checklist

- [ ] Correct repeater firmware, regional preset, and standard-form name saved
- [ ] Both PCB trace cuts test open
- [ ] Corrected JST polarity and solder joints verified
- [ ] ALFA antenna and U.FL pigtail secure
- [ ] Battery installed with correct polarity only after inspection
- [ ] LoRa relay and charging tests pass
- [ ] TPU gasket and all original hardware installed
- [ ] Antenna joint sealed with self-fusing silicone tape

## Troubleshooting

| Symptom | Check first |
|---|---|
| No power | Battery polarity/voltage, JST polarity, switch wiring, solder joints, and CN3065 path |
| No charging | Solar illumination, panel polarity, CN3065 connections, and trace cuts |
| Poor LoRa range | Regional preset, ALFA antenna, U.FL seating, height, and obstructions |
| Intermittent operation | Loose connection, weak battery, pinched wire, solder joint, water, or shade |

## Maintenance

Inspect after severe weather and periodically. Clean the panel; inspect the mount, fasteners, gasket, enclosure, and silicone tape; look for corrosion or moisture; review battery performance before winter; and retest after moving the unit or changing its antenna system.

## Build Record

| Item | Record |
|---|---|
| Builder |  |
| Build date |  |
| Repeater name |  |
| Firmware/version |  |
| Installation location |  |
| Battery installed | Included 1500 mAh 18650 / Other: __________ |
| Final radio test | Pass / Needs follow-up |
| Final charging test | Pass / Needs follow-up |
| Notes |  |

---
