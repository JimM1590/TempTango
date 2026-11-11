# TempTango

TempTango is an Android HVAC control app for Jeep Cherokee KLs using compatible aftermarket Android head units.

It uses the head unit's existing CANBUS integration to send climate-control commands and read the vehicle's current HVAC state, allowing the on-screen controls and the Jeep's physical HVAC controls to stay synchronized.

## Current status

The current development release candidate is **TempTango 2.1 RC03 Mini** (`TempTango-2.1-RC03-Mini`, versionCode `704`).

RC03 adds **TempTango Mini**, a compact quick-control HVAC interface designed to be launched by DashHopper while another app remains visible.

RC03 remains a **prerelease / release candidate** while broader compatibility feedback is collected. TempTango Mini has now been successfully tested on the development Jeep, including launch through DashHopper and operation of the vehicle's HVAC controls.

The existing full TempTango interface has been vehicle-tested on:

- **2017 Jeep Cherokee KL**
- Dual-zone automatic HVAC
- Heated front seats
- Heated steering wheel
- Aftermarket Android head unit
- **Raise / RZC CANBUS decoder**
- XYAuto-style CANBUS software stack
- Stock / unmodified Cherokee P1 CANBUS plugin

No root, patched CANBUS APK, external OBD adapter, USB-CAN hardware, laptop, or ADB connection is required for normal use.

## What full TempTango currently supports

On the tested configuration, full TempTango can control and display:

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

## TempTango Mini

TempTango Mini is included in RC03 alongside the existing full TempTango interface.

Mini provides a compact set of quick HVAC controls:

- Driver temperature − / current temperature / +
- Passenger temperature − / current temperature / +
- Fan − / icon / + with no numerical speed display
- Vent-mode cycle: FACE → FACE + FEET → FEET → FEET + DEF → FACE
- Driver heated seat: OFF / LO / HI
- Passenger heated seat: OFF / LO / HI
- FRONT DEF
- REAR DEF
- OPEN TT
- Close X
- Android Back also closes Mini

The following controls are intentionally excluded from Mini and remain available in full TempTango:

- Heated steering wheel
- A/C
- AUTO
- MAX
- SYNC / DUAL control
- Fan-speed number

Mini uses the same shared TempTango/JIM backend as the full interface. It does **not** create a separate CANBUS connection, RXPD receiver, gate manager, or raw TX implementation.

The normal TempTango launcher icon still opens full TempTango directly.

### Mini window behavior

The RC03 Mini Activity can:

- Be dragged using its header
- Be resized using its corner resize grip
- Remember its position
- Remember its size
- Restore position and size after closing/reopening and process restart
- Launch full TempTango using **OPEN TT**

Mini moves and resizes its own Activity window only. It does not snap, move, or resize other applications.

## DashHopper integration

TempTango supports the public DashHopper HVAC quick-control contract.

Intent action:

```text
org.dashhop.intent.action.HVAC_QUICK_CONTROL
```

Category:

```text
android.intent.category.DEFAULT
```

TempTango exposes an exported, enabled, non-launcher Activity for this action.

DashHopper can discover the quick-control Activity inside the user's selected HVAC package and launch it explicitly. When TempTango is selected as the HVAC app, that contract opens TempTango Mini rather than the full interface.

Normal direct launch remains unchanged:

```text
TempTango launcher icon
→ full TempTango
```

DashHopper launch:

```text
DashHopper HVAC button
→ org.dashhop.intent.action.HVAC_QUICK_CONTROL
→ TempTango Mini
```

The contract is intentionally app-agnostic. DashHopper does not need a TempTango-specific package exception, and other HVAC applications can implement the same public action if desired.

## Compatibility requirements

For the best chance of matching the configuration already tested, you should have:

- A **Jeep Cherokee KL**
- An aftermarket **Android head unit**
- A **Raise / RZC CANBUS decoder**
- The radio's normal Cherokee CANBUS profile/plugin already installed and working
- Dual-zone HVAC if you want full dual-zone functionality

TempTango currently depends on the Android-side interfaces exposed by the Raise/XYAuto CANBUS stack.

Other CANBUS vendors such as Hiworld, SimpleSoft, and others may use different Android interfaces and are **not confirmed compatible yet**.

## RC03 vehicle validation

RC03 Mini has been successfully tested on the development vehicle:

- **2017 Jeep Cherokee KL**
- Dual-zone HVAC
- Heated front seats
- Heated steering wheel
- Aftermarket Android 11 head unit
- Raise / RZC CANBUS configuration
- XYAuto-style CANBUS software stack
- Stock / unmodified Cherokee P1 plugin

On this configuration, Mini launches through DashHopper and operates the Jeep's HVAC controls through the existing TempTango backend.

RC03 remains a prerelease because other Jeep model years, head units, Android/firmware builds, CANBUS decoders, and vehicle option combinations may behave differently. Please test while parked first and keep access to the radio's original HVAC interface until TempTango has been verified on your setup.

## RC03 build details

Version name:

```text
TempTango-2.1-RC03-Mini
```

versionCode:

```text
704
```

APK filename:

```text
TempTango_Mini_RC03.apk
```

Package ID:

```text
com.jmadsen.jishvac.versione
```

APK SHA-256:

```text
7872b31a0633053f03fa48d0695423d3413d2cfe5a71b1c6e36e414a7ec8414b
```

Signing certificate SHA-256:

```text
7e0cfd5e90a97b8335c00366661c76052dbc8c99392fbf32d676645d70477241
```

RC03 preserves the existing TempTango package and signing identity. Direct installation over RC02 was verified on an Android 11 emulator with application data preserved.

## Download

Published releases are available from the repository's **Releases** section:

https://github.com/JimM1590/TempTango/releases

The current published prerelease is **TempTango 2.1 RC03 Mini**:

https://github.com/JimM1590/TempTango/releases/tag/v2.1-RC03-Mini

Download `TempTango_Mini_RC03.apk` from the release assets and verify its SHA-256 against the value above.

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
- TempTango version tested
- Whether full TempTango works
- Whether TempTango Mini launches from DashHopper
- Whether Mini remains usable over your normal navigation/Android Auto setup
- Which Mini controls work
- Which physical controls are reflected correctly
- Any incorrect or missing status
- A TempTango diagnostics export if available

Compatibility reports from other **Raise/RZC-equipped Cherokee KLs** are especially useful right now.

## Known limitations

- Explicit Mini seat-level selection requires fresh verified RX state. Requests use the existing seat-cycle command and wait for RX confirmation between steps.
- Cached values may be displayed while awaiting fresh RX; stale seat/defrost states are not presented as verified active selections.
- Mini moves and resizes its own Activity window only.
- Outside temperature is not currently implemented.
- Cooled seats are not implemented.
- Other CANBUS vendors are not yet supported.
- The CANBUS mirror may not provide an unsolicited full HVAC state immediately after startup; TempTango keeps the last known state until a fresh full HVAC frame arrives.
- Android or vendor firmware can terminate background services or change the CANBUS mirror state.

## License

TempTango is released under the [MIT License](LICENSE).

---

TempTango is an independent community project and is not affiliated with or endorsed by Jeep, Stellantis, Raise, RZC, XYAuto, DashHopper, or any head-unit manufacturer.
