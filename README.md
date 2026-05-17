# ESP32 Soccer Robot

Hey! Welcome to the repository for the ESP32 Soccer Robot. Here you'll find all the hardware files needed to build the bot. 

As you probably noticed, the code isn't here yet (working on it, okay?), and the mobile app is definitely on the "someday" to-do list. But hey, the hardware layout is rock solid and ready to go!

---

## What’s in here?

We’ve got all the essential files lined up so you can check out the design or print the board straight away:

* **`Soccer Esp32.json`** ── The main schematic file. Just import this into EasyEDA and you're good to go. No need to wire things from scratch.
* **`PCB_Soccer Esp32.json`** ── The actual PCB layout file for EasyEDA. 

### Previews

#### Schematic Circuit
![Schematic Preview](Schematic_Soccer%20Esp32.png)

#### PCB Layers (Upper & Lower)
| Upper Layer | Lower Layer |
| :---: | :---: |
| ![Upper Layer](PCB_Soccer%20Esp32_upper_layer.png) | ![Lower Layer](PCB_Soccer%20Esp32_lower_layer.png) |

---

## How the Hardware is Setup

Here is a quick breakdown of how things are connected on the board:

### 1. The Brain (ESP32-WROOM-32D)
The master controller. It’s got plenty of power for the robot's logic, Wi-Fi, and Bluetooth (whenever we actually get around to writing the code).

### 2. Motor Driver (TB6612FNG)
Handles the heavy lifting for the motors instead of those old, bulky drivers.
* **Speed Control:** `PWMA` and `PWMB` are hooked up to `GPIO19` and `GPIO0`.
* **Direction:** Controlled via `AIN1/2` and `BIN1/2` pins linked directly to the ESP32.
* **Standby (`STBY`):** Connected to `GPIO17`. (Just remember to set this HIGH in your future code, or the robot won't budge!).

### 3. Power & Safety
* **VCC1:** Terminal block for the battery.
* **DIODO1 (1N4007):** Placed right after the switch to save the circuit just in case someone connects the battery backward.
* **U3 Regulator:** Steps down the battery voltage to a safe 5V (`VIN`) to keep the ESP32 and logic gates happy.

### 4. Starter Module (ARRANCADOR1)
A 4-pin header mapped to `GPIO2` (`GO`). Essential for tournament remote starters so the referee can start and stop the match without you diving onto the field.

---

## How to use this in EasyEDA

Don't overcomplicate it. To open and edit these files:

1. Head over to [EasyEDA](https://easyeda.com/).
2. Open a project workspace.
3. Go to **File > Open > EasyEDA** and select the `.json` files from this repo (or just drag and drop them into the editor).
4. Generate your Gerbers, order the PCB, and start soldering!

---

## Roadmap (Things actually happening later)
* [ ] **Firmware:** Code will be uploaded once it's tested and stops breaking.
* [ ] **Mobile App:** Coming soon...ish. For now, the hardware is ready for whatever control method you want to throw at it.