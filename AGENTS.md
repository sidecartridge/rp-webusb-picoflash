# AGENTS.md

## Project scope
This project is the `rp-webusb-picoflash` utility page. It provides a WebUSB UF2 flasher for RP2040/RP2350 BOOTSEL ROM in a single `index.html`.

## Coding style
- Prefer minimal dependencies; keep everything in a single HTML file when possible.
- Use plain JavaScript (no build step).
- Keep UI simple; inline CSS is acceptable.
- Favor ASCII text in edits.

## WebUSB flasher notes
- Use the Pico ROM vendor protocol (picotool-style), not raw UF2 to MSC bulk endpoints.
- Required flow: request device, open, claim vendor interface, reset, exclusive access, exit XIP, erase, write, reboot.
- Progress feedback is expected for: load (blue), erase (red), write (green).
- Keep timeouts on USB transfers to prevent hangs.
- The erase step should be optional (user-controlled).

## Files of interest
- `index.html`

## Testing
- Manual test only: use Chromium, BOOTSEL mode device, verify load/erase/write/reboot logs.
