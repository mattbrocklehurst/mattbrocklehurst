# Matt Brocklehurst

R&D engineer. I end up wherever software meets hardware that won't cooperate — reverse-engineering protocols nobody documented, chasing kernel-level race conditions, keeping industrial hardware running long after the manufacturer stopped caring.

---

## OpenPnP

20+ feature branches and logic prototypes for the OpenPnP ecosystem — mostly G-code protocol work and vision-to-motion synchronization.

### Motion control & G-code
* **[Fiducial homing (PR-310/345)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-310-fiducial-homing-gcode)**: G-code sequences for high-precision homing via optical fiducial recognition.
* **[Error regex handling (PR-372)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-372-error-regex-handling)**: Serial response parsing for controllers that don't return standard feedback.
* **[Vacuum detection (PR-373)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-373-vacuum-detect-sense)**: Hardware-level sensor feedback wired into placement logic to catch dropped-part air-shots.

### Dispensing (paste/glue)
* **[G-code dispense core (PR-312/552)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-552-gcode-paste-dispenser-logic)**: Core logic for solder paste and glue dispensing — extrusion synchronized with XYZ motion.
* **[Alignment-aware dispensing (PR-464)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-464-alignment-dispense-logic-v2)**: V2 logic that keeps volumetric accuracy on skewed footprints.

### Vision & part alignment
* **[Multi-part aligner (PR-551)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-551-multi-part-aligner)**: Batch-processes part alignment, cut per-placement latency.
* **[Loose part feeder (PR-320/374)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-374-loose-part-feeder-v2)**: Vision-based recognition for non-strip-fed, loose-picked components.

### Legacy hardware
* **[Zevatech resurrection](https://github.com/mattbrocklehurst/openpnp/tree/zevatech)**: Reverse-engineering and modernizing a decommissioned Zevatech pick-and-place machine — see below.

---

## Real bugs, fixed

### [SDL2 (Simple DirectMedia Layer)](https://github.com/mattbrocklehurst/SDL/tree/feature/wasapi-deadlock-fix)
**Problem:** Windows WASAPI audio backend hung on device hot-plugging.
**Fix:** Race condition in kernel-level synchronization primitives — traced it with WinDbg, replaced `INFINITE` blocking with bounded 200ms defensive polling.
**Impact:** In mainline SDL now, quietly keeping a lot of downstream games and industrial UIs from hanging.

### Raspberry Pi kernel DMA debugging ([raspberrypi/linux #7136](https://github.com/raspberrypi/linux/issues/7136))
**Problem:** Bringing up BCM2836/BCM2837 (Pi 2/3) support in Armbian, the kernel panicked under QEMU — `VFS: Unable to mount root fs`, zero partitions ever detected.
**Root cause:** Built a gdb/QEMU kernel debugging setup from scratch (DWARF-enabled kernel, live source-level stepping against the running kernel) and traced it to a missing devicetree `dma-ranges` window — the SD host controller's MMIO address fell outside the declared RAM-only DMA bus alias. Dug further and found *why*: `raspberrypi/linux`'s own downstream driver patch (by the actual kernel maintainer) makes the MMC driver depend on DMA address translation the upstream-style devicetree doesn't provide — a real internal inconsistency between two devicetree variants shipped in the same repo, confirmed with the maintainer directly. Also found and fixed a separate, genuinely new bug this exposed: a NULL-pointer race in `bcm2835_finish_data()` between the DMA-completion workqueue and the interrupt/status-poll path, only reachable once DMA actually started completing.
**Outcome:** Confirmed on real hardware, not just QEMU. The devicetree gap itself turned out to already be fixed in Raspberry Pi's own downstream tree — not a novel fix, just an accurate diagnosis of a real divergence. Board-support PRs to `armbian/build` were rejected by a maintainer who argued kernel-level fixes belong upstream, not patched around in a build framework — fair, and I agreed once I saw it.

### Zevatech PM-560 resurrection
No schematics, no source, no vendor support, no one left at the company who remembered the protocol. Reverse-engineered the signal logic with a logic analyzer, then wrote a modern C++ firmware layer to drive the original 1990s motor controllers and solenoids directly under a PC-based control stack.

---

## Stack

* **Languages:** C/C++ (11+ years), Java, MCU firmware, Python
* **Environment:** Linux (Debian/i3wm), PCB design, logic analyzers, oscilloscopes
* **Notes:** Obsidian + git-crypt

---

## Contact

Manchester, UK. Available for R&D/systems roles. Currently active in the OpenPnP and SDL communities.
