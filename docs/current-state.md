# Current State

## OS
- Gargoyle / LineageOS 20 boots.
- Boot image used: `magisk_patched-24000_Xkyu1_vbmeta.img`
- System image used: `gargoyle_bvN.img`

## Known fixes
- Disabled virtual keyboard with physical keyboard:
  `adb shell settings put secure show_ime_with_hard_keyboard 0`

## Known blockers
- Terminal usability is not proven.
- Special character access may be poor without soft keyboard.