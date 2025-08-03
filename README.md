# EZee Rotation - Effortless Zero Engagement Engine
Current Version: 0.2.2  
Release Date: 08/03/2025  

## Welcome!
Welcome to `EZee Rotation`. This document will serve as both an advanced user guide as well as a reference tool for ongoing development.  

## What is this Sorcery? 
`EZee Rotation` is a rotation bot for World of Warcraft. It is a standalone desktop application that relies on WoW AddOns for supplemental support. `EZee Rotation` has no rotation model/logic of its own, it is entirely driven by the suggested abilities that come from either Blizzard's built-in `Combat Assisted Highlight` or the `Hekili` AddOn. `EZee Rotation` can either cast abilities automatically using virtual keypresses or prepare your next manual keystroke to cast the suggested ability. 

## Why is it Better? 
`EZee Rotation` is superior to Blizzard's built-in `One-Button Rotation Tool` as `EZee Rotation` suffers no `GCD` penalty. This alone will account for a substantial `DPS` increase.  
`EZee Rotation` works flawlessly with the `Hekili` rotation AddOn. The rotation models used in `Hekili` come directly from `SimulationCraft`, which is what `Raidbots` and nearly all rotation/priority theorycrafting are primarily built from. This means that `EZee Rotation` is immediately making use of the most up-to-date theorycrafted `APLs` any time `Hekili` updates come through. 

## How does it Work?
1) WoW suggests an ability to the player.
2) EZee Rotation detects the suggested ability.
3) EZee Rotation presses the matching key for the ability.
4) Loop back to Step 1.

## Installation
1) Install `EZee Rotation` with the `setup.exe` auto-installer.
2) Launch `EZee Rotation` from where you installed it.
3) Enter your `License Key`.
4) In the `Installation` tab, configure the path to your `World of Warcraft` root directory. `NOTE:` not `_retail_`, it needs to be the base `World of Warcraft` folder where `Wow.exe` is located. 
5) Select your account from the dropdown. This is important for WoW keybind detection. 
6) Select which rotation `AddOn` you are using, either Blizzard's built-in `Combat Assisted Highlight` or `Hekili`. `Hekili` is strongly recommended. 
7) Click the `Install EZee Rotation` button to install the `EZee AddOn` and `EZee Helper` is using `Hekili`.

## Configuration
1) In the `Configuration` tab, assign a `Toggle Key` to activate / deactivate the bot.
2) Select the `Action Mode`. See `Action Modes` section below for details.
3) If using `One-Button` mode, assign a `Trigger Key` that will cast suggested abilities. The assigned hotkey `CANNOT` be a key you use as a keybind in WoW!
4) If using `QMK-VIA` mode, assign the `layer`, `row`, and `column` of the physical `Trigger Key` that will cast suggested abilities. You will also need to set the `Reset Key Value`, which will be the value the physical key returns to when the bot is deactivated. 
5) If you are not using `QMK-VIA`, go to the `Configuration - Anti-Ban` section.
6) If you are using `QMK-VIA`, go to the `Configuration - QMK-VIA` section. 

### Configuration - Anti-Ban
1) In the `Anti-Ban` tab, adjust the sliders to tweak `EZee Rotation` behavior. Faster key presses means more `DPS` but higher risk. Greater variance between the min/max delays is lower risk. 
2) Click the `Save & Apply` button. 
3) You are done and ready to parse! 

### Configuration - QMK-VIA
1) If you are using `QMK-VIA` mode, go to the the `Keybinds` tab.
2) Verify that the detected WoW Keybinds match your in-game keybinds. If there are errors, see `Valid Keys` section below. 
3) This is `EXTREMELY` important. In WoW, every keybind for an ability in your rotation needs to have a `single-key` keybind mapped to it. Do not freak out - in WoW, every ability action button can have a `primary` and a `secondary` keybind set. If you want to maintain your multi-button keybind combos for normal play, make use of the `secondary` keybinds for each ability action button as needed. After you set a `single-key` (`primary` or `secondary`) keybind for all abilities in your rotation, `/reload` in WoW and refresh the `Keybinds` tab. You should see any multi-key `Keybind Combos` pair with a `Single-Key Override`. Not every single `Keybind Combo` needs to have a `Single-Key Override` paired with it, only those in your actual rotation. Verify the pairings and click the `Save Key Overrides` button. 

## Action Modes
### One-Button
`One-Button` mode functions similar to Blizzard's built-in `One-Button Rotation Tool` but without the `GCD` penalty. The chosen `Trigger Key` will cast the suggested ability. It is important to make sure the configured `Trigger Key` is not a keybind used in WoW. Only the `Auto Press Duration` and `Modifier Delay` settings in the `Anti-Ban` tab apply to `One-Button` mode. The `Auto Press Delay` setting is null because you are the one that is manually initiating the spell being cast. 

### Full-Auto
`Auto` mode will automatically cast abilities when detected at random intervals based on the sliders in the `Anti-Ban` tab. Adjust according to your risk tolerance. 

### Non-QMK-VIA (default)
At `Step 9` in `Detailed Steps`, all automation is done through a virtual/simulated keyboard. `Enigo` cross-platform input simulation in `Rust` is used to press and release keys. If `EZee Rotation` is set to `One-Button` mode, the `Trigger Key` set by the user will initiate the virtual key press instead of it being automatic.  

### QMK-VIA
At `Step 9` in `Detailed Steps`, the player's `VIA`-compatible `QMK` keyboard is reprogrammed in real-time. A physical `Trigger-Key`, whose layer, row and column are configured by the user, is modified to send the keycode that matches the corresponding ability keybind. This is no different than opening `VIA` and changing the physical `2` key to instead send the keycode for `3`.  

## Valid Keys
Below are the list of valid keys for `QMK-VIA` mode. Certain keycodes are restricted due to technical limitations.  
### Keys
```
"a",
"b",
"c",
"d",
"e",
"f",
"g",
"h",
"i",
"j",
"k",
"l",
"m",
"n",
"o",
"p",
"q",
"r",
"s",
"t",
"u",
"v",
"w",
"x",
"y",
"z",

"1",
"2",
"3",
"4",
"5",
"6",
"7",
"8",
"9",
"0",

"-",
"=",
"[",
"]",
";",
"'",
",",
".",
"/",
"\\",
"`",

"f1",
"f2",
"f3",
"f4",
"f5",
"f6",
"f7",
"f8",
"f9",
"f10",
"f11",
"f12",

"mousebutton3",
"mousebutton4",
"mousebutton5"
```
### Modifiers
```
"alt",
"ctrl",
"shift"
```

## How does it Work? - Detailed
1) WoW: `Combat Assisted Highlight` or `Hekili` process the game state
2) WoW: `Combat Assisted Highlight` or `Hekili` suggest an ability to the player
3) WoW: `EZee AddOn` captures the suggested ability
4) WoW: `EZee AddOn` translates the suggested ability into a unique color
5) WoW: `EZee AddOn` discretely displays the color as a single pixel on the screen
6) Desktop App: `EZee Rotation` is constantly watching for color changes at a 10 millisecond interval
7) Desktop App: `EZee Rotation` detects when the color matches a recognized ability
8) Desktop App: `EZee Rotation` determines which key or keybind is mapped to the ability
9) Desktop App: `EZee Rotation` either presses the key automatically or reconfigures the player's keyboard to the matching key
10) Loop back to Step 1

## Changelog
### 0.2.3 - ?
* License-based features  
### 0.2.2 - 08/03/2025
* Auto updates  
### 0.2.1 - 07/30/2025
* Licensing  

---  
\- G