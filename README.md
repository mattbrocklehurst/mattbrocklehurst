# Matt Brocklehurst | R&D Systems Architect & Fixer

I take mechanical intent and turn it into reliable, high-performance control logic. 

My specialty is navigating undocumented, broken, or obsolete hardware and bending it to modern standards. Whether it's a 20-year-old SMT machine or a kernel-level audio deadlock, I thrive where the documentation ends and the logic begins.

---

## 🛠️ The "Fixer" Proof-of-Work

### [SDL (Simple DirectMedia Layer)](https://github.com/mattbrocklehurst/SDL/tree/feature/wasapi-deadlock-fix)
**The Problem:** A permanent system hang in the Windows WASAPI audio backend during device hot-plugging.
**The Fix:** Identified a race condition in the kernel-level synchronization primitives. Replaced infinite blocking with bounded, defensive polling, enabling graceful hardware recovery.
**Impact:** My code is etched into the mainline SDL source, stabilizing audio for thousands of applications.

### [OpenPnP](https://github.com/openpnp/openpnp)
**Role:** Core Contributor & Systems Navigator.
I work on the high-performance control logic that drives global-scale robotics. I focus on making hardware abstraction layers actually abstract, ensuring that complex mechanical movement is predictable and repeatable at the firmware/software boundary.

### Zevatech Resurrection & Jaguar Jigs
I have a track record of "Logic Breaching"—reverse-engineering proprietary protocols on obsolete industrial hardware (Zevatech SMT) and industrial integration (Jaguar) to keep multi-million dollar systems relevant in a modern R&D stack.

---

## 🧠 Logic & Infrastructure

I don't just "write code." I build reliable systems using a structured, ADHD-friendly R&D protocol:
- **Language:** C/C++ (11+ years professional experience), Firmware, Python.
- **Tools:** Linux (Debian/i3wm), PCB Design, Logic Analyzers, Oscilloscopes.
- **Philosophy:** Scannability over prose. Intellectual honesty over "yes-man" engineering.

---

## 🏗️ What I'm Looking For
I’m at my best when I can touch the hardware, talk logic with an Architect, and be left alone to "lash it up" until it works. If you have a system that's "impossible" to fix or a protocol that refuses to be breached, that's where I belong.



---

**Current Status:** Based in Burnley | Operating from "Homer" & "Flanders" | Solving the hard problems.
