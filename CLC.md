---
tags:
  - debugging
---

## Keys of interest (Write to `Erd_CooktopCurrentKeyStatusWord`, then write 0):
 - Initiate precision cook:  CooktopKey_BurnerSizeBurner1, 0x0000000000200000
 - Press on/off: CooktopKey_PowerOnOffBurner1, 0x0000000000040000
 - Increment power level: CooktopKey_IncLevelBurner1, 0x0000000000100000
