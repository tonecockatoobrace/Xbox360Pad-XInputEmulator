<p align="center">
  <img src="https://i.postimg.cc/mD2sym4s/banner.png" alt="XInputPad Bridge — Universal USB & DirectInput Gamepad to Xbox 360 XInput Mapper" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-DirectInput%20%E2%86%92%20XInput%20Bridge-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-xinput--bridge--v1.3-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# XInputPad Bridge — Universal USB & DirectInput Gamepad to Xbox 360 XInput Mapper

**Plugged in a generic USB controller, arcade fightstick, flight stick, or older Logitech/Thrustmaster gamepad only to find that modern PC games completely ignore it—or swap the right stick and triggers? Map any DirectInput HID controller to a native Xbox 360 XInput device.**

XInputPad Bridge reads raw DirectInput / Windows HID axes, buttons, and POV hats: **letting you click any Xbox 360 button on screen and press the corresponding physical button on your controller, fix inverted right-stick axes, tune stick deadzones, and output clean XInput**.

This project is aimed at **Windows 10 and Windows 11 (64-bit) PC gamers** using third-party USB gamepads, retro adapters, arcade sticks, and older DirectInput controllers in modern XInput-only games.

## Quick Use-Case & Troubleshooting Reference

| Scenario / Issue | Cause | Solution |
| --- | --- | --- |
| Modern PC game ignores third-party USB gamepad or arcade stick | Modern Windows games only query XInput (`xinput1_4.dll`), ignoring DirectInput | Translate raw DirectInput HID inputs into a virtual Xbox 360 XInput pad |
| Right analog stick moves camera up/down when pushed left/right | Generic USB controllers assign Z-Axis and Z-Rotation differently | Use **Click-to-Bind Axis Wizard** and toggle **Invert Axis** in 1 click |
| Old or worn analog sticks drift slightly at rest | Lack of hardware deadzone causes slow camera spin | Set custom **Inner Deadzone (`5%–20%`)** and **Anti-Deadzone** curves |
| Local 2-player co-op with one Xbox pad + one generic USB pad | Second player's generic controller is unrecognized in co-op menus | Assign generic pad to **Virtual XInput Player 2** cleanly |

## Download for Windows

[**Download XInputPadBridge.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/XInputPadBridge.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why use `XInputPadBridge.exe`? (Key features)

- Interactive **Click-to-Map Xbox 360 Diagram**—click `A`, `B`, `RT`, or `Right Stick` and press your physical control to bind.
- Fixes swapped right-stick axes, split vs. combined triggers, and inverted Y-axis in one click.
- Adjustable **Inner Deadzone**, **Outer Threshold**, and **Stick Sensitivity Curve** per profile.
- Supports saving multiple controller profiles (`Arcade_Stick`, `Generic_Pad`, `Retro_Adapter`) with auto-load.

### Sample Output

```text
[XInputPadBridge] Detected HID Device: Generic USB Twin-Stick Controller (VID_0079)
[OK]   Binding Profile  : Standard_X360_Map (All 14 buttons + 4 axes + D-Pad mapped)
[OK]   Deadzone Tuning  : Left Stick: 8% | Right Stick: 10% | Y-Axis Invert: OFF
[OK]   XInput Output    : Virtual Xbox 360 Controller [Player 1] Active
```

The release ZIP is named `XInputPadBridge.zip`; the Windows executable inside is named `XInputPadBridge.exe`.

1. Close XInputPad Bridge before updating or replacing executable files.
2. Click **Download XInputPadBridge.zip** above.
3. Right-click the downloaded archive and choose **Extract All**.
4. Open the extracted folder and run `XInputPadBridge.exe`.
5. Review the options and output paths before processing files.

**Requirements:** Windows 10 or 11 (64-bit) with ViGEmBus driver and any USB/Bluetooth DirectInput HID controller.

### Verification & Windows SmartScreen Note

- **Offline & standard user permissions:** `XInputPadBridge.exe` runs locally without uploading your personal files and does not require disabling Windows Defender.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Problems this project solves

### Making budget and retro USB controllers work in every modern game

Eliminates per-game DLL copying (`x360ce.ini` in every folder) by providing a system-wide virtual XInput pad.

### Fixing scrambled axis mappings on generic controllers

Visual live axis bars show exact raw HID input as you move sticks and triggers.

### Curing minor analog stick drift via custom deadzones

Prevents unwanted character walk or camera drift without buying a new controller.

### Per-device automatic profile switching

Remembers your exact mapping whenever you plug in that USB controller.

## Default folders and configuration paths

XInputPad Bridge saves controller mapping profiles in `%APPDATA%\XInputPadBridge`:

```text
%APPDATA%\XInputPadBridge\mappings\
```

Typical directory layout:

```text
Generic USB / DirectInput HID Device
        │
        ▼
[XInputPadBridge.exe] -> Button/Axis Remap + Deadzone Curve
        │
        ▼
System-Wide Virtual Xbox 360 XInput Controller
```

If a game reads both the raw DirectInput pad and the virtual XInput pad simultaneously, enable **Hide Physical Device (HidHide)** so the game sees only the clean Xbox 360 controller.

## Quick start guide

Follow these steps to get started:

1. **Plug in your USB controller and launch `XInputPadBridge.exe`.** Select your controller from the top HID device dropdown.
2. **Click **Auto-Map Wizard** and press each button/stick when prompted.** Verify all sticks and triggers move smoothly on the Xbox 360 preview.
3. **Adjust **Inner Deadzone** (`8%–12%`) if your sticks have minor center drift.** Click **Save Profile** and launch your game.

### Data safety note

XInputPad Bridge never modifies game installation directories or game DLLs.

## What the status summary shows

XInputPad Bridge displays **detected HID device VID/PID, active mapping profile, deadzone %, and virtual XInput slot status**.

## FAQ

**How is XInputPad Bridge better than copying x360ce DLLs into every game folder?**

Because it creates a virtual XInput controller at the Windows level, it works across all games (including 64-bit, DX12, and Game Pass titles) without placing DLLs inside game folders.

**Can I fix swapped right-stick X and Y axes?**

Yes—click 'Record Right Stick X' and push right, then 'Record Right Stick Y' and push up.

**Does it support multiple controllers for local co-op?**

Yes—you can map up to 4 separate USB controllers to XInput Slots 1–4.

## Useful reading

- [Microsoft Docs — Getting Started With XInput in Windows](https://learn.microsoft.com/en-us/windows/win32/xinput/getting-started-with-xinput)

## More Windows Gaming Utilities

- [SwitchProPC-BetterInputTray](../SwitchProPC-BetterInputTray) — Nintendo Switch Pro & Joy-Con XInput bridge + gyro aim
- [DualSensePC-ControllerGlyphBridge](../DualSensePC-ControllerGlyphBridge) — PlayStation DualSense tray battery %, lightbar RGB & trigger tool
- [PadDrift-ControllerPollingTest](../PadDrift-ControllerPollingTest) — Gamepad stick drift & mouse polling rate (1000-8000 Hz) tester
- [BorderlessForce-WindowScaler](../BorderlessForce-WindowScaler) — Force borderless windowed fullscreen & dual-monitor cursor lock

*Independent open-source desktop utility for Windows. Not affiliated with Microsoft Corporation.*
