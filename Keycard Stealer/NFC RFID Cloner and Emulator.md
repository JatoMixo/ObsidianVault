---
tags:
  - pentesting
  - hardware-hacking
  - rust
  - embedded
---
# Flipper Zero as a reference
- [Flipper Zero Docs](https://docs.flipper.net/)
- [Flipper Zero Source Code](https://github.com/flipperdevices/flipperzero-firmware/)
- [Flipper Zero Specs](https://docs.flipper.net/development/hardware/tech-specs)
# Types of electronic cards and functionality
## RFID
[Flipper Zero Docs](https://docs.flipper.net/rfid) | [Flipper Zero Source Code](https://github.com/flipperdevices/flipperzero-firmware/tree/dev/applications/main/lfrfid)
- Widely used in old systems
- Extremely vulnerable
- Stores and N-Byte ID without encryption or authentication that can be cloned easily.
- It's also important to notice that the fucking ID of the card is usually written on it and can be just read and copied without any fancy embedded stuff (People are truly genius).
- A small antenna is needed to clone and emulate the ID of the card. 
## NFC
[Flipper Zero Docs](https://docs.flipper.net/nfc) | [Flipper Zero Source Code](https://github.com/flipperdevices/flipperzero-firmware/tree/dev/applications/main/nfc)
## iButton?
[Flipper Zero Docs](https://docs.flipper.net/ibutton)
