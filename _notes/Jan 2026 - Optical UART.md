---
title: Jan 2026 Project X
topics:
  - projects
---
# A Hands-On Optical Interconnect Demo

## What This Is
This project is a **minimal, working optical interconnect** that shows how digital information can be transmitted using **light instead of copper wires**. It’s a stripped-down, hardware-first demonstration of the same core idea powering modern photonic infrastructure from companies like **[Lightmatter](chatgpt://generic-entity?number=0)**.

This is not a visualization or simulation — it is a real system that sends real data.

## One-Line Pitch
**We built a simple optical data link that replaces a wire with light to show how future computers move information.**

## The Problem
Modern computing systems are increasingly bottlenecked by **data movement**, not compute. Moving bits between chips using electrical interconnects is:
- Power-hungry  
- Heat-limited  
- Hard to scale  

Optical interconnects solve this by moving data with photons instead of electrons.


## Our Approach
We recreated the core abstraction of an optical interconnect at a human-scale speed:

Microcontroller A

↓

Encode message → 8-bit binary

↓

Laser / LED (modulated light)

↓

Free space or optical fiber

↓

Photodiode + amplifier

↓

Microcontroller B

↓

Decode binary → original message

No electrical data wire connects the two devices. Information moves purely through light.

---

## What It Does
- Encodes text into **8-bit ASCII**
- Converts bits into **timed light pulses**
- Transmits data optically
- Detects and reconstructs the original message on the receiving side

In short: **digital data in → photons → digital data out**.

## Why This Matters
This project captures the exact data path used in large-scale optical systems:
- Electrical → optical conversion
- High-speed optical transport
- Optical → electrical conversion

The only differences from production systems are **speed, density, and integration scale**.

---

## What This Demonstrates
- Why optics scale better than copper  
- How data can move without physical electrical connections  
- The fundamentals behind photonic chip-to-chip communication  
- Real engineering constraints: timing, noise, alignment, and power  


## Industry Context
Modern AI and data-center architectures increasingly rely on optical links to:
- Reduce energy per bit  
- Increase bandwidth density  
- Enable larger, more connected systems  

This project is a first-principles look at that shift.

---

## Takeaway
**We didn’t build a faster chip — we built a better connection.**

This demo shows, in the simplest possible way, how the future of high-performance computing moves data.