# MeshCore 102 Presenter Guide

## Build The People's Repeater

**Class length:** 2 hours  
**Recommended level:** MeshCore 102  
**Primary activity:** Convert a Harbor Breeze solar light into a solar-powered MeshCore repeater  
**Hands-on build time:** 70 minutes, including open-unit inspection and testing

This guide keeps the class moving while students use the separate Student Guide and Build Instructions. Before class, flash, configure, test, and label every board. During class, demonstrate the firmware process without asking participants to repeat it. Keep the soldering and assembly work as the hands-on core of the class. The finished repeater uses the ALFA outdoor antenna and does not retain the original light.

## Project Repository and Build Sources

- [Class repository](https://github.com/commputethis/TheMaker-sSpace_MeshCore102) — <https://github.com/commputethis/TheMaker-sSpace_MeshCore102>
- [Build reference video 1](https://www.youtube.com/watch?v=yAmINEghCOc) — <https://www.youtube.com/watch?v=yAmINEghCOc>
- [Build reference video 2](https://www.youtube.com/watch?v=eXMlvGiI7Hs) — <https://www.youtube.com/watch?v=eXMlvGiI7Hs>

This class build combines ideas from both reference videos with the specific parts, printed components, wiring, and procedures documented in these guides.

## Class Goals

By the end of the class, participants should be able to:

- Distinguish companions, repeaters, and Room Servers.
- Explain what a dedicated MeshCore repeater does.
- Identify the qualities of a useful repeater location.
- Assemble The People's Repeater using the supplied components.
- Configure, inspect, and perform basic radio and charging tests.
- Describe how to weatherproof, mount, and maintain the finished unit.

## Before the Class

### Prepare Reference Materials

- Assemble and test one finished repeater as a demonstration unit.
- Prepare one partially assembled unit that shows the internal component arrangement.
- Have the Student Guide and Build Instructions available in print or electronically.
- Project the repeater configuration, naming, county-code, MeshMapper, and solar-angle pages.
- Display a photograph of the completed repeater in its intended outdoor orientation.

### Prepare Boards, Demonstration Computer, and Firmware

- Update the OTAFIX bootloader and flash the current compatible MeshCore repeater firmware onto every class board.
- Configure every board with the class radio, command-line, and region settings.
- Give each board a temporary standard-form name, such as `IN.ALL.FWA.Class01`, `IN.ALL.FWA.Class02`, and so on.
- Put a matching removable label on each board or kit. Record its temporary name, firmware version, and configuration status on the instructor's preparation sheet.
- Do not put the administrator password on an outward-facing label. Record it securely where the student can receive it with the completed repeater.
- Confirm normal startup on every board before placing it in a kit.
- Leave the supplied small Wio antenna attached. Students will remove it only when they are ready to connect the external pigtail during the build.
- Prepare one separate demonstration board, a known-good USB data cable, and a computer that can show the bootloader, firmware, and configuration workflow.
- Decide which legal regional preset and repeater class settings the class will use.
- Confirm that the NEIMesh radio, CLI, and region recommendations in this guide are still current before class.

### Prepare Each Kit

#### Electronics and Power

- Harbor Breeze solar light with included 1500 mAh 18650 battery
- Seeed Studio XIAO nRF52840 with Wio-SX1262 LoRa radio
- ACEIRMC CN3065 mini solar LiPo charger
- Three 100 mm female-socket JST PH 2.0 silicone-wire leads

The class JST leads have already been corrected by swapping the red and black positions where needed. Students must still verify actual polarity before making connections.

#### Antenna System

- ALFA Network AOA-915-5ACM 5 dBi outdoor 915 MHz antenna
- 6 in / 15 cm U.FL1-to-N-female RG178 pigtail
- Waterproof self-fusing silicone tape

The small antenna supplied attached to the Wio remains connected while the prepared board is handled. It is removed once during the build, immediately before the external pigtail is connected, and is not used in the finished repeater.

#### Enclosure and Mounting

- 3D-printed TPU gasket
- 3D-printed PETG component mount
- 3D-printed PETG [antenna connector clamp](https://www.printables.com/model/1761740-xiao-nrf52840-wio-sx1262-antenna-clamp) — <https://www.printables.com/model/1761740-xiao-nrf52840-wio-sx1262-antenna-clamp>
- Zip ties or hose clamps for attaching the mount to a pole

The [Harbor Breeze solar mesh-node models](https://www.printables.com/model/1748950-26-harbor-breeze-solar-mesh-node-mounts-meshtastic) page contains the component mount, alternate mounts, and TPU gasket: <https://www.printables.com/model/1748950-26-harbor-breeze-solar-mesh-node-mounts-meshtastic>

### Prepare Tools and Supplies

- Soldering irons, stands, solder, and tip-cleaning supplies
- Flush cutters or wire cutters
- Nonconductive tools for battery removal
- Small screwdrivers and tools for tightening the N-connector hardware
- Parts trays for retained screws and the separate mount nut
- Painter's tape
- Goo Gone, isopropyl alcohol, and cleaning cloths
- Demonstration computer and USB data cable
- Completed reference repeater

### Perform Pre-Class Checks

- Confirm visually that the corrected JST leads match the labeled connections and illustrated wiring.
- Check that the printed parts fit the enclosure and pigtail used in class.
- Confirm that every kit has the correct washers and N-connector nut.
- Confirm that every board has been flashed, configured, tested, and matched to its temporary-name label.
- Arrange tables so the presenter or helpers can inspect solder joints and wiring.
- Set aside a troubleshooting area for units that need more time.

## Class Schedule

| Time | Presenter focus |
| ---: | --- |
| 0:00-0:15 | MeshCore refresher, Room Servers, and project overview |
| 0:15-0:30 | Placement and solar guidance |
| 0:30-0:40 | Firmware and repeater configuration demonstration |
| 0:40-1:50 | Guided construction and open-unit testing |
| 1:50-2:00 | Installation, maintenance, and wrap-up |

Protect the 70-minute build period. Move optional discussion to the end or to a follow-up session.

## 0:00-0:15 MeshCore Refresher and Project Overview

### Suggested Introduction

"Welcome back to The Maker's Space. Today we are building The People's Repeater, a solar-powered MeshCore repeater housed in a repurposed Harbor Breeze solar-light enclosure. Your board has already been flashed, configured, tested, and labeled. We will review that process, discuss placement, and then reserve the rest of the class for construction and testing. The finished unit has an outdoor antenna and no light."

### MeshCore Roles and Room Servers

- A **companion** gives a person access to the mesh.
- A **repeater** extends useful coverage by forwarding packets toward their destinations.
- A **Room Server** is a shared message board. It stores posts and can deliver unseen history when a user returns, unlike an ordinary channel where a message can be missed while the user is out of range.

A Room Server and repeater solve different problems. MeshCore recommends separate devices for the best experience; enabling repeat behavior on a Room Server does not provide the full repeater feature set. This class builds a dedicated repeater. See the [MeshCore FAQ](https://github.com/meshcore-dev/MeshCore/blob/main/docs/faq.md): <https://github.com/meshcore-dev/MeshCore/blob/main/docs/faq.md>

Show the completed reference unit. Identify the enclosure, panel, battery, XIAO and Wio boards, CN3065, printed parts, pigtail, ALFA antenna, TPU gasket, switch, weatherproofing, and pole-mounting points.

Mention that a larger-capacity compatible 18650 may provide more reserve during cold or low-sun months. Any replacement must match the required chemistry, voltage, size, polarity, terminal style, protection, and charger requirements.

## 0:15-0:30 Placement and Solar Guidance

### Key Message

**Height helps, but a useful location is more than simply the highest available point.** The goal is reliable radio coverage, adequate sunlight, safe access, and long-term survivability.

### 1. Start with the coverage objective

Ask:

- What area are we trying to serve?
- Are we filling a known dead zone?
- Are we connecting two groups or neighborhoods?
- Is there already good repeater coverage nearby?
- Who will benefit from this location?

Emphasize intentional placement. A repeater should solve a coverage problem or strengthen an important route through the mesh.

Use [MeshMapper](https://fwa.meshmapper.net/) to demonstrate the purpose and radio-path tools: <https://fwa.meshmapper.net/>

### 2. Favor clear radio paths

Discuss the advantages of:

- Greater elevation
- Open surroundings
- Fewer nearby walls, roofs, trees, and metal structures
- A position with a clear view toward the intended coverage area
- Keeping the antenna away from large metal objects

Explain that terrain and structures can block or weaken signals. A location that looks close on a map may still perform poorly when a hill, building, or dense obstruction lies between stations.

### 3. Protect antenna performance

Point out that the antenna should:

- Remain in the orientation intended by the design.
- Not be buried inside or pressed directly against metal.
- Be kept clear of wiring and other objects when possible.
- Have secure, weather-resistant connections.
- Not be bent, cut, substituted, or modified casually.

Use the demonstration unit to show the desired antenna position.

### 4. Plan for solar exposure

A solar repeater needs enough light to replace the energy it uses.

Look for:

- Reliable sunlight across the day
- Minimal seasonal shading
- A panel orientation that receives useful light
- A location that will not quickly become covered by leaves, vegetation, snow, or debris

In Indiana, a generally southerly exposure at approximately a 40° angle is a useful starting point, adjusted for site-specific shade. Demonstrate the [solar tilt-angle calculator](https://www.baess.app/tools/solar-tilt-angle-calculator): <https://www.baess.app/tools/solar-tilt-angle-calculator>

Remind participants that a sunny location in November may be shaded differently during another season.

### 5. Consider weather and drainage

Choose a position that:

- Does not collect standing water
- Allows water to drain away from openings
- Keeps cable entries and seals in their intended orientation
- Avoids direct runoff from roofs or gutters
- Is not likely to be struck by lawn equipment, vehicles, or falling debris

Weather resistance depends on both sealing and orientation. An enclosure that survives ordinary rain may fail if installed upside down or where water continually pools against a seam.

### 6. Maintain safe, legal access

A suitable location should:

- Be installed with the property owner’s permission.
- Be safely reachable for inspection and repair.
- Not interfere with utilities or normal property use.
- Avoid creating a climbing, tripping, or falling-object hazard.
- Comply with any applicable property, mounting, and radio requirements.

### 7. Make maintenance possible

Every repeater will eventually need inspection.

Ask participants to consider:

- Can the unit be retrieved safely?
- Can the solar panel be cleaned?
- Can the battery be serviced?
- Can water intrusion or physical damage be noticed?
- Is there a way to identify the unit and its owner?
- Can its operation be checked without removing it?

### Placement checklist

Before installing a repeater, confirm:

- It serves a clear coverage purpose.
- The radio path is reasonably open.
- The antenna has adequate clearance.
- The solar panel receives useful sunlight.
- The enclosure can drain and resist weather.
- The mounting point is secure.
- Installation and maintenance are safe.
- The property owner has approved the installation.
- The repeater can be retrieved and inspected.

## 0:30-0:40 Firmware and Configuration Demonstration

Class boards are already flashed, configured, tested, and labeled. Use the separate demonstration board to walk through the process. Participants should observe rather than connect or reflash their class boards.

Keep the demonstration focused on the bootloader purpose, repeater firmware, required settings, naming, and the preparation label. Leave the supplied Wio antenna attached to each class board until the external pigtail is ready during the build.

Naming standard: `StateCode.CountyCode.descriptiveName`.

- Allen County: `IN.ALL.descriptiveName`
- Local Fort Wayne convention: `IN.ALL.FWA.descriptiveName`
- [Repeater naming](https://docs.okimesh.org/books/meshcore-I9o/page/repeater-naming) — <https://docs.okimesh.org/books/meshcore-I9o/page/repeater-naming>
- [County abbreviations](https://docs.okimesh.org/books/meshcore-I9o/page/county-abbreviations) — <https://docs.okimesh.org/books/meshcore-I9o/page/county-abbreviations>

### Recommended NEIMesh Node Settings

MeshCore devices must use matching radio settings to communicate. NEIMesh currently recommends the following local baseline. These recommendations may change as the mesh grows, so verify them before presenting the class.

#### Radio Settings

- Preset: `USA`
- Frequency: `910.525 MHz`
- Bandwidth: `62.5 kHz`
- Spreading factor: `7`
- Coding rate: `5`
- Path hash size: **2-byte**

#### Repeater Command-Line Settings

Enter these commands in the repeater command-line interface:

```text
set agc.reset.interval 500
set multi.acks 1
set loop.detect minimal
```

#### Repeater Region Settings

Regions are not currently enforced, but NEIMesh recommends defining the local region hierarchy in preparation for future growth. A weather-alert node already scopes messages to the `fwa` region. Repeaters that do not define that region will not receive those scoped messages.

```text
region put us-in
region put nei us-in
region put fwa nei
region allowf *
```

Explain the hierarchy as `us-in` for Indiana, `nei` for northeast Indiana, and `fwa` for the Fort Wayne area.

### Demonstrate Flashing the Firmware

1. Connect the demonstration board to the computer.
2. Flash the current compatible MeshCore **repeater** firmware.
   1. Go to [https://flasher.meshcore.io/](https://flasher.meshcore.io/)
   2. Type `xiao` into the search/filter bar
       ![MeshCoreFlasher](images/MeshCoreFlasher1.png)
   3. Select the Seeed Studio Xiao nRF52 WIO option
      1. _Likely the middle option_
       ![MeshCoreFlasher](images/MeshCoreFlasher2.png)
   4. Select the Repeater role
       ![MeshCoreFlasher](images/MeshCoreFlasher3.png)
   5. Explain that selecting the OTAFIX link in the flasher downloads a ZIP file, which is not the file needed for this procedure.
   6. Open the [OTAFIX bootloader releases page](https://github.com/oltaco/Adafruit_nRF52_Bootloader_OTAFIX/releases) directly: <https://github.com/oltaco/Adafruit_nRF52_Bootloader_OTAFIX/releases>
      1. OTAFIX permits future firmware updates over Bluetooth without reopening the finished enclosure and reconnecting it to a computer.
   7. Scroll down to `Assets` and click the `"Show all assets"` link.
      1. If you do not see that link, you have likely scrolled down too far.
       ![MeshCoreFlasher](images/UF2ShowAllAssets.png)
   8. Scroll down until you see a file named `update-xiao_nrf52840_ble_sense_bootloader-0.9.2-OTAFIX2.3-BP1.4_nosd.uf2`
      1. **Make sure to get the one with `sense` in the middle of the name**
      2. Show where to find the correct file (the INFO_UF2.TXT file)
       ![MeshCoreFlasher](images/uf2File.png)
   9. Double press the `RST` button on the XIAO to put it into UF2 mode.
      1. Within 0.5 seconds
      2. A drive named XIAO-SENSE or XIAO-BOOT should appear.
       ![MeshCoreFlasher](images/XIAO_RST.jpg)
   10. Go to your Downloads and copy the downloaded bootloader UF2 file.
       ![MeshCoreFlasher](images/bootloader.png)
   11. Click on the drive and paste the bootloader UF2 file.
       ![MeshCoreFlasher](images/XIAO_Sense.png)
       1. The drive will disappear and your device will reboot with the updated bootloader.
   12. Go back to the [MeshCore Flasher](https://flasher.meshcore.io/): <https://flasher.meshcore.io/>
   13. Click the `DFU mode active` button
       ![MeshCoreFlasher](images/DFUmodeActive.png)
   14. Select the proper USB connection and click `Connect`.
       1. It will look something like this:
       ![MeshCoreFlasher](images/USBDevice.png)
       2. If it does not work for you, you may need to refresh your browser page.
   15. Click the `Flash!` button
       ![MeshCoreFlasher](images/Flash.png)
   16. Select the proper USB connection and click `Connect`.
       1. It will look something like this:
       ![MeshCoreFlasher](images/USBDevice.png)
   17. Wait for the flashing process to complete.
       ![MeshCoreFlasher](images/Flashing.png)
   18. Once you see this, you are ready to go onto the Configuration.
       ![MeshCoreFlasher](images/FlashingCompleted.png)

### Demonstrate Configuring the Repeater

1. Click the `Configure via USB` button
   ![ConfigureRepeater](images/ConfigureUSB.png)
2. Click the `Connect` button
   ![ConfigureRepeater](images/ConnectButton.png)
3. Select proper USB connection and click `Connect`.
   1. It will look something like this:
   ![ConfigureRepeater](images/USBDevice.png)
4. You should now see a window like this
   ![ConfigureRepeater](images/SetupScreen.png)
5. We are going to follow the [OKI Mesh repeater configuration guide](https://docs.okimesh.org/books/meshcore-I9o/page/repeater-configuration) for the repeater name and settings: <https://docs.okimesh.org/books/meshcore-I9o/page/repeater-configuration>
6. Show the temporary class naming pattern, such as `IN.ALL.FWA.Class01`. Explain that the owner may choose a permanent standard-form name later.
7. Enter a good Admin password
   1. Make sure to keep a note of what you make this.
8. Configure Radio Settings
   1. Preset: `USA`
      1. It will change to `Canada`, but you can change it to `USA` again, but doesn't matter as they are the same settings.
   2. Scroll down and enter `Owner info`
      1. You want to give some description of where the device is and your name on Discord, Mesh, HAM Radio call sign, etc. so one has an idea of who to contact about that repeater.
    ![ConfigureRepeater](images/OwnerInfo.png)
   3. Under `Advanced settings` change `Path hash mode` to either `2-byte (1)` or `3-byte (2)`
    ![ConfigureRepeater](images/byteHash.png)
   4. Click the `Save settings` button
    ![ConfigureRepeater](images/SaveSettings.png)
   5. Click the `OK` button to Reboot the device to apply the updated settings.
9. Disconnect the demonstration board from the computer.

**Preparation checkpoint:** Show participants where the removable board or kit label identifies the temporary repeater name. Confirm that their supplied board was prepared before class. Do not remove the supplied antenna yet.

## 0:40-1:50 Guided Build

Use the numbered steps in the Student Guide and Build Instructions. Demonstrate each operation before releasing the group to perform it. Stop the room at each checkpoint rather than allowing faster participants to enter a safety-critical step alone.

### Build Safety Briefing

- Verify that the solar-light switch is **OFF** before cutting the wire to the light.
- Remove the battery immediately after opening the enclosure. Use fingers or a nonconductive tool, never a metal tool.
- Keep the battery out during cutting, desoldering, soldering, and rewiring.
- Never short, puncture, crush, overheat, or reverse an 18650.
- Visually verify every connection against the hardware labels and illustrated build instructions.
- Never transmit without an antenna connected.
- Stop for unexpected heat, odor, smoke, uncertain wiring, or abnormal behavior.
- Ask for help before forcing a connector or printed part.
- Do not close the enclosure until the open-unit inspection and tests pass.

There is no drilling or cutting of the enclosure in this build.

### 0:40-0:50 Steps 2 Through 5

1. Identify and retain the original mount screw and separate nut.
2. Put all removed hardware in a parts tray.
3. Confirm that the solar-light switch is **OFF**.
4. Cut the wire joining the enclosure to the light. The entire wire will be removed.
5. Remove and retain the enclosure screws, then open the cover.
6. Remove the 18650 using fingers or a nonconductive tool.
7. Pull the cut wire through its feed-through.
8. Remove and retain the two screws holding the switch PCB.
9. Clip the cut light wire at both PCB connections, both solar-panel leads at the PCB, and the negative battery lead at the PCB.

The original PCB is retained only so its switch can be placed inline with CN3065 `SYS OUT`.

**Checkpoint 1:** The battery is out, the original hardware is retained, and the switch PCB and required wires are accessible.

### 0:50-1:00 Steps 6 and 7

1. Identify the two marked copper paths while the battery and panel are disconnected.
2. Demonstrate how the paths are opened and checked.
3. Remove the factory foam gasket.
4. Clean the channel and seat the TPU gasket evenly.

**The instructor will provide additional instruction for completing and checking the PCB modification.**

**Checkpoint 2:** The PCB modification has been checked and the TPU gasket is seated evenly.

### 1:00-1:20 Steps 8 Through 11

#### Rewire the Battery Holder

Desolder the original negative wire, install the negative JST conductor, then desolder the original positive wire and install the positive JST conductor. The old negative wire is not reused.

#### Add the Solar-Panel JST Lead

The panel terminals are not labeled. Change only **one conductor at a time**: remove one original wire and immediately solder its matching JST conductor before touching the other terminal.

#### Wire the XIAO and Retained Switch PCB

- Original battery-holder positive wire to XIAO `BAT+`
- JST negative conductor to XIAO `BAT-`
- Positive conductor from that JST lead to the retained PCB, placing the switch inline with CN3065 `SYS OUT`

#### Connect the CN3065

**JST wiring:** The class cables have already been corrected by swapping the red and black positions where needed. Students must visually verify that each conductor goes to the labeled connection shown in the build guide.

Connect the verified JST plugs for solar input, battery, and system output. Do not install the battery.

**Checkpoint 3:** A presenter or helper verifies polarity, solder joints, XIAO battery connections, the switch path, and all three CN3065 connections.

### 1:20-1:40 Steps 12 Through 15

1. Feed the pigtail through the PETG mount.
2. Push the N connector upward through the antenna opening from the bottom.
3. Align the connector's flat sides.
4. Install the tooth lock washer, flat washer, and nut in that order.
5. Tighten without crushing the PETG mount.
6. Feed the U.FL end through the enclosure opening.
7. Attach the mount with the retained screw and nut.
8. Attach and hand-tighten the ALFA antenna.
9. Seat the rubber switch boot.
10. Reinstall the switch PCB with its two original screws.
11. Cover the PCB with painter's tape.
12. Remove the supplied small antenna from the Wio, then immediately press the pigtail's U.FL plug straight down onto the Wio socket without twisting or pulling the coax.
13. Support the boards and pigtail while installing the antenna connector clamp.

The ALFA antenna is attached before the radio is powered. Keep the coax bend gentle.

**Checkpoint 4:** The antenna is attached, the switch boot and PCB are reinstalled, the U.FL connection is seated, and the clamp supports the assembly without flexing the boards.

### 1:40-1:50 Steps 16 Through 18

#### Clean the Panel Before Testing

Remove the solar-panel sticker. Use Goo Gone to remove the residue, then clean the panel with isopropyl alcohol (aka IPA).

#### Inspect and Test the Open Unit

Before installing the battery, visually verify the labeled battery orientation, solder joints, PCB modifications, JST positions, switch insulation, rubber-boot seating, U.FL seating, clamp support, antenna connection, and wire routing.

Install the 18650 with correct polarity and test:

- Normal startup
- Saved regional setting, class settings, and repeater name
- LoRa relay through the ALFA antenna
- Solar charging response

Disconnect the battery immediately for heat, odor, smoke, or abnormal behavior.

#### Close and Weatherproof

After the tests pass:

1. Arrange components and wires clear of the screw posts.
2. Close the enclosure without forcing it.
3. Reinstall the original enclosure screws gradually.
4. Confirm that the ALFA antenna joint is clean, dry, and hand-tight.
5. Stretch and overlap self-fusing silicone tape across the complete antenna joint without covering the radiating body.

**Checkpoint 5:** The unit is closed, the original hardware is installed, the antenna joint is weatherproofed, and the finished repeater has no light.

If a unit is not ready to close at 1:50, bag and label its parts and record the specific next step. Do not bypass an inspection or safety check to finish on time.

## 1:50-2:00 Installation Maintenance and Wrap Up

### Explain Pole Mounting

- Use zip ties or hose clamps to attach the PETG mount to a pole.
- These fasteners are for pole mounting, not internal cable management or strain relief.
- Keep the ALFA antenna vertical.
- Set the panel for seasonal sun.
- Confirm permission, stability, safe access, and a water-shedding orientation.

### Review Maintenance

Inspect after severe weather and periodically. Clean the panel; inspect the pole fasteners, PETG mount, enclosure, TPU gasket, silicone tape, and antenna connection; look for corrosion or moisture; review battery performance before winter; and retest after moving the unit or changing its antenna system.

### Closing Message

"The repeater's value depends on where it is installed and whether it remains powered, dry, and serviceable. Test the proposed location, obtain permission, document the repeater name and location, and inspect it periodically."

## Troubleshooting Strategy

- Move problem units to the troubleshooting area.
- Compare them with the completed reference unit.
- Test one variable at a time.
- Keep a known-good battery, USB cable, CN3065, and radio available.
- Pair participants who finish early with those who want assistance.
- Label unfinished units and record a clear next step.

| Symptom | Check first |
| --- | --- |
| No power | Battery orientation, labeled JST connections, switch wiring, solder joints, and CN3065 path |
| No charging | Solar illumination, labeled panel connection, CN3065 connections, and PCB trace modifications |
| Poor LoRa range | Regional preset, ALFA antenna, U.FL seating, height, and obstructions |
| Intermittent operation | Loose connection, weak battery, pinched wire, solder joint, water, or shade |

Never bypass an uncertain connection, battery concern, damaged enclosure, or questionable electrical connection simply to finish on time.

## Presenter Time Checks

- At **0:15**, begin placement and solar guidance.
- At **0:30**, begin the firmware and repeater configuration demonstration.
- At **0:40**, confirm that switches are off and begin the build.
- At **1:00**, the PCB modification and TPU gasket should be complete.
- At **1:20**, electrical rewiring should be ready for inspection.
- At **1:40**, begin panel cleaning, final inspection, and open-unit testing.
- At **1:50**, stop construction and begin installation and maintenance guidance.
- At **2:00**, end with a documented follow-up step for any unfinished unit.

---
