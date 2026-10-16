# TempTango

TempTango is an Android HVAC control app for Jeep Cherokee KLs using compatible aftermarket Android head units.

It uses the head unit's existing CANBUS integration to send climate-control commands and read the vehicle's current HVAC state, allowing the on-screen controls and the Jeep's physical HVAC controls to stay synchronized.

## Current status

The current public test build is **TempTango 2.0 RC02**.

TempTango has been vehicle-tested on:

- **2017 Jeep Cherokee KL**
- Dual-zone automatic HVAC
- Heated front seats
- Heated steering wheel
- Aftermarket Android head unit
- **Raise / RZC CANBUS decoder**
- XYAuto-style CANBUS software stack
- Stock / unmodified Cherokee P1 CANBUS plugin

No root, patched CANBUS APK, external OBD adapter, USB-CAN hardware, laptop, or ADB connection is required for normal use.

## What TempTango currently supports

On the tested configuration, TempTango can control and display:

- Driver and passenger temperature
- Fan speed
- Airflow modes
- A/C
- AUTO
- Recirculation
- Front defrost
- Rear defrost
- DUAL / SYNC
- Driver heated seat
- Passenger heated seat
- Heated steering wheel

Physical HVAC controls are reflected back into TempTango, and controls pressed inside TempTango are sent through the head unit's existing CANBUS system.

## Compatibility requirements

For the best chance of matching the configuration already tested, you should have:

- A **Jeep Cherokee KL**
- An aftermarket **Android head unit**
- A **Raise / RZC CANBUS decoder**
- The radio's normal Cherokee CANBUS profile/plugin already installed and working
- Dual-zone HVAC if you want full dual-zone functionality

TempTango currently depends on the Android-side interfaces exposed by the Raise/XYAuto CANBUS stack.

Other CANBUS vendors such as Hiworld, SimpleSoft, and others may use different Android interfaces and are **not confirmed compatible yet**.

## Important testing note

This is still a community test release, not a claim of universal Jeep Cherokee compatibility.

Different head-unit firmware, Android builds, CANBUS boxes, vehicle years, trims, and factory option combinations may behave differently.

Please test while parked first and keep access to your radio's original HVAC interface until you know TempTango works correctly on your setup.

## Download

Download the latest APK from the repository's **Releases** section:

https://github.com/JimM1590/TempTango/releases

Current test build:

**TempTango 2.0 RC02**

APK SHA-256:

`149d119aacd509ece05e5d5a73de61a7fb420736d7c7b3d5de064ccd3faa173c`

## Feedback wanted

If you test TempTango, please include as much of the following as possible:

- Cherokee model year
- Trim
- Android head-unit make/model
- Android version
- CANBUS decoder brand/model
- CANBUS profile selected in factory settings
- Single-zone or dual-zone HVAC
- Heated seats: yes/no
- Heated steering wheel: yes/no
- Which TempTango controls work
- Which physical controls are reflected correctly
- Any incorrect or missing status
- A TempTango diagnostics export if available

Compatibility reports from other **Raise/RZC-equipped Cherokee KLs** are especially useful right now.

## Known limitations

- Outside temperature is not currently implemented.
- Cooled seats are not implemented.
- Other CANBUS vendors are not yet supported.
- The CANBUS mirror may not provide an unsolicited full HVAC state immediately after startup; TempTango keeps the last known state until a fresh full HVAC frame arrives.
- Android or vendor firmware can terminate background services or change the CANBUS mirror state.

## License

TempTango is released under the [MIT License](LICENSE).

---

TempTango is an independent community project and is not affiliated with or endorsed by Jeep, Stellantis, Raise, RZC, XYAuto, or any head-unit manufacturer.
