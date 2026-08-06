# Matt Brocklehurst | R&D C++ Programmer & Systems Architect

I build high-performance control logic for hardware that refuses to cooperate. 

I specialize in the **Hardware-Software Boundary**: reverse-engineering proprietary protocols, stabilizing kernel-level synchronization, and modernizing industrial hardware. I thrive in the space where the documentation ends and the logic begins—translating noisy physical inputs into stable, production-grade systems.

---

## 🛠️ OpenPnP | Systems Architecture & Logic
I have authored over 20+ feature branches and logic prototypes for the OpenPnP ecosystem, specializing in the intersection of G-code protocol breaching and high-speed vision-to-motion synchronization.

### 🎯 Motion Control & G-Code Protocols
* **[Fiducial Homing (PR-310/345)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-310-fiducial-homing-gcode)**: Custom G-code sequences for high-precision machine homing via optical fiducial recognition.
* **[Error Regex Handling (PR-372)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-372-error-regex-handling)**: Robust serial response parsing to handle non-standard controller feedback during protocol breaching.
* **[Vacuum Detection (PR-373)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-373-vacuum-detect-sense)**: Integrated hardware-level sensor feedback into placement logic to prevent "dropped-part" air-shots.

### 🧪 Material Dispensing (Paste/Glue)
* **[G-Code Dispense Core (PR-312/552)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-552-gcode-paste-dispenser-logic)**: Architected core logic for solder paste and glue dispensing, managing synchronized extrusion with XYZ motion.
* **[Alignment Dispense Logic (PR-464)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-464-alignment-dispense-logic-v2)**: V2 logic for part-alignment-aware dispensing, ensuring volumetric accuracy on skewed footprints.

### 👁️ Vision & Part Alignment
* **[Multi-Part Aligner (PR-551)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-551-multi-part-aligner)**: Optimized vision pipelines for batch-processing part alignment, reducing per-placement latency.
* **[Loose Part Feeder (PR-320/374)](https://github.com/mattbrocklehurst/openpnp/tree/legacy/pr-374-loose-part-feeder-v2)**: Advanced vision-based part recognition for non-strip-fed components (loose-part picking).

### 📟 Legacy Hardware Modernization
* **[Zevatech Resurrection](https://github.com/mattbrocklehurst/openpnp/tree/zevatech)**: Primary R&D branch for reverse-engineering and modernizing legacy Zevatech SMT hardware.

---

## 🛡️ The "Fixer" Proof-of-Work

### [SDL (Simple DirectMedia Layer)](https://github.com/mattbrocklehurst/SDL/tree/feature/wasapi-deadlock-fix)
**The Problem:** Catastrophic system hang in the Windows WASAPI audio backend during device hot-plugging.
**The Fix:** Identified a race condition in kernel-level synchronization primitives. Replaced `INFINITE` blocking with bounded, 200ms defensive polling.
**Impact:** My fix is part of the mainline SDL source, stabilizing audio for thousands of applications globally.

### [Armbian / Raspberry Pi 2 Kernel DMA Fix](https://github.com/armbian/build/pull/10355)
**The Problem:** Bringing up Raspberry Pi 2 (BCM2836) support in the Armbian build framework, the kernel panicked under QEMU — `VFS: Unable to mount root fs`, zero partitions ever detected on the SD card.
**The Fix:** Built a full gdb/QEMU kernel debugging environment from scratch (DWARF-enabled kernel rebuild, live source-level stepping against the running kernel) to root-cause it down to a missing devicetree `dma-ranges` window: the SD host controller's own MMIO register address fell outside the declared RAM-only DMA bus alias, so the kernel's address-translation lookup silently failed and the driver never completed a transfer.
**Impact:** Verified end-to-end — kernel boots, root filesystem mounts, init launches. Testing also showed the *existing* upstream kernel fix for this exact driver ([raspberrypi/linux #7136](https://github.com/raspberrypi/linux/issues/7136#issuecomment-5207917045)) was incomplete for this SoC; posted the analysis directly to the upstream maintainers and opened a PR against `armbian/build`.

### Zevatech Resurrection & Jaguar Jigs
Reverse-engineered proprietary protocols on obsolete industrial hardware to integrate into modern R&D stacks. I specialize in "Logic Breaching" where manufacturers have long since abandoned support.

---

## 🏗️ Technical Infrastructure
- **Languages:** C/C++ (11+ years), Java, Firmware (MCUs), Python.
- **Environment:** Linux (Debian/i3wm), PCB Design, Logic Analyzers, Oscilloscopes.
- **Workflow:** Structured technical logging and documentation via Obsidian/Git-Crypt.

---

## 🏗️ Deployment & Contact
I’m at my best when I can work directly with hardware, collaborate with lead architects on system design, and iterate until the solution is robust.

**Location:** Manchester, UK (Available for R&D/Systems roles)
**Current Status:** Active in the OpenPnP and SDL communities.
