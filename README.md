# Voron 2.4 Klipper Configuration - altruistically-minded

This repository contains my Klipper configuration for a Voron 2.4 3D printer. It includes several modifications, hardware additions, and quality-of-life improvements over a stock Klipper/Voron setup.

## Printer Specifications (Inferred from Config)

*   **Printer Model:** Voron 2.4 (R2)
*   **Main Control Board:** LDO Leviathan
*   **Toolhead Board:** LDO Nitehawk via `usb`
*   **Probe:** Beacon3d Beacon H
*   **Toolhead:** Stealthburner
*   **Extruder:** E3D Revo Obsidian HF

## Key Modifications & Customizations

This configuration deviates from or adds to a standard Voron Klipper setup in the following ways:

### 1. Hardware & Connectivity
    * **Toolhead Board:** LDO Nitehawk connected via `usb`.
    * **Probe:** Beacon3d Beacon H for Z-homing, quad gantry leving, and bed meshing. 

### 2. Toolhead & Extrusion Enhancements
    *   **Stealthburner LEDs:** [PENDING] Full support for Stealthburner's RGBW status LEDs, including macros for different states (`STATUS_READY`, `STATUS_PRINTING`, `STATUS_BUSY`, etc.) defined in `stealthburner_leds.cfg` and `macros/set_logo_led_color.cfg`, `macros/set_nozzle_led_color.cfg`.
    *   **Nozzle Scrubber/Cleaner:** [PENDING] Implemented a nozzle scrubber mechanism with associated settings and `CLEAN_NOZZLE` macro in `nozzle_scrub.cfg` and `macros/clean_nozzle.cfg`.
    *   **Voron Purge Line:** A custom `VORON_PURGE` macro (in `macros/voron_purge.cfg`) for a specific purge line routine.

### 3. Automation & Quality of Life Macros
    *   **Klipper Meshing** 
    *   **Custom `START_PRINT` & `END_PRINT`:**
        *   `START_PRINT` (in `macros/print_start.cfg`): Includes bed meshing (`BED_MESH_CALIBRATE`), custom homing, heating, nozzle cleaning, and purging sequences.
        *   `END_PRINT` (in `macros/print_end.cfg`): Includes bed cool down macros, nozzle parking, and disabling heaters/motors.

### 4. Lighting & Display
    *   **Case Lighting:** LDO LED light strips
    *   **BTT PI TFT43:** Configured with KlipperScreen
    
### 5. General Structure
    *   **Modular Macros:** Macros are well-organized into individual `.cfg` files within the `macros/` directory.
    *   **Includes:** Heavy use of `[include]` to keep the main `printer.cfg` cleaner and more organized.

## Standard Voron Features Preserved

While many customizations exist, the core setup still reflects a standard Voron 2.4 with Klipper:
*   CoreXY Kinematics
*   Quad Gantry Leveling (`QUAD_GANTRY_LEVEL`)
*   Bed Mesh (`BED_MESH_CALIBRATE`)
*   Standard stepper motor configurations (though pins are specific to SKR Mini E3 v3 + EBB36)
*   Input Shaping configuration
*   Mainsail integration (`mainsail.cfg`)


**Disclaimer:** Use this configuration at your own risk. Printer configurations are highly specific to individual builds. Thoroughly review and understand all settings before using them on your machine.
