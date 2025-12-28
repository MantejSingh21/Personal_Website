---
title: Jan 2026 Optical UART
topics:
  - projects
---
# A Minimal Optical Interconnect: Technical Concept and Implementation

As modern computing systems scale, overall performance is increasingly limited by **data movement rather than computation**. In large AI and high-performance computing systems, chips must continuously exchange massive volumes of data. Traditional electrical interconnects (copper traces and cables) suffer from fundamental limitations: resistive losses, heat generation, signal attenuation, and crosstalk all worsen as bandwidth and distance increase. Optical interconnects address these constraints by transmitting information using photons instead of electrons.

This project is a **technical, first-principles demonstration of an optical interconnect**. It recreates—at a greatly reduced speed and scale—the same signal path used in modern photonic systems deployed by companies such as **[Lightmatter](chatgpt://generic-entity?number=0)**. While simplified, the architecture is physically accurate and preserves the essential electrical-to-optical and optical-to-electrical conversions that define real photonic links.

## System Concept

The system consists of two independent microcontrollers that communicate without a shared electrical data wire. All information transfer between them occurs optically. On the transmit side, digital data is encoded into a binary bitstream (8-bit ASCII), which modulates a light source (LED or laser diode). The resulting intensity-modulated optical signal propagates through free space or an optical fiber and is detected on the receive side by a photodiode. The photodiode converts incident photons into an electrical current, which is amplified, thresholded, and decoded to recover the original digital data.

At an abstract level, the signal chain is:
Electrical Data → Optical Modulation → Optical Transport → Photodetection → Electrical Data

This abstraction is identical to that used in high-speed fiber-optic communication and chip-to-chip photonic interconnects.

## Data Encoding and Modulation

Digital messages are first converted into binary form using standard ASCII encoding, where each character is represented by 8 bits. Each bit is mapped to a fixed time interval (the bit period). During each interval, the optical transmitter outputs either a high optical power level (logical ‘1’) or a low/no optical power level (logical ‘0’). This scheme corresponds to **on–off keying (OOK)**, the simplest form of intensity modulation.

Although industrial systems use far more advanced modulation formats (e.g., PAM-4, phase modulation, wavelength-division multiplexing), OOK captures the essential idea: **information is encoded in controlled variations of light**.

## Optical Channel

The optical channel can be implemented either as a free-space path or using plastic optical fiber. From a systems perspective, this channel replaces a copper wire. Unlike electrical conductors, the optical channel is immune to electromagnetic interference and does not suffer resistive heating. The primary constraints become optical alignment, coupling efficiency, and detector sensitivity—mirroring challenges encountered in real photonic packaging.

## Photodetection and Decoding

On the receive side, a photodiode converts incident optical power into a proportional electrical current via the photoelectric effect. This current is converted into a voltage using either a load resistor or, more robustly, a transimpedance amplifier. The resulting analog signal is sampled by the receiving microcontroller and compared against a threshold to recover digital logic levels. With appropriate timing (e.g., start/stop bits or fixed-rate sampling), the original binary sequence and corresponding characters are reconstructed.

This process directly parallels the receiver front-end in high-speed optical links, where photodetectors, amplifiers, clock recovery, and digital logic convert optical waveforms back into bits.

## What This Demonstrates

Although the system operates at kilohertz or low-megahertz data rates, it demonstrates several key technical concepts:

- Electrical-to-optical and optical-to-electrical conversion  
- Intensity modulation and direct detection  
- Timing, synchronization, and noise sensitivity  
- The decoupling of data transport from electrical conduction  

These are the same foundational mechanisms used in state-of-the-art photonic interconnects. The primary differences between this prototype and production systems are speed (GHz vs. kHz), channel count (thousands vs. one), and integration (on-chip silicon photonics vs. discrete components).

## Broader Context

In advanced computing architectures, optical interconnects enable higher bandwidth density, lower energy per bit, and improved scalability compared to electrical links. Rather than accelerating computation itself, they remove the communication bottleneck that increasingly dominates system performance.

## Takeaway

This project does not attempt to build a faster processor or a novel compute architecture. Instead, it provides a concrete, technical demonstration of how **improving data movement through optical interconnects** can fundamentally change system-level performance. By building a minimal optical link, the underlying principles of modern photonic computing infrastructure become tangible and intuitive.