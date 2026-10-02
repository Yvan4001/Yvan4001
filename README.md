# Yvan Simon

### Software Architect & Systems Engineer | Language, Kernel & Cloud
**M.Sc. Computer Science — Epitech, Class of 2026** · Graduated

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/yvan-simon-448b11153/)
[![Email](https://img.shields.io/badge/Email-Contact-red?style=flat-square&logo=gmail)](mailto:y.simon@sivagames.com)
[![Portfolio](https://img.shields.io/badge/Portfolio-Interactive-black?style=flat-square&logo=vercel)](https://data.sivagames.com)
[![Status](https://img.shields.io/badge/Status-Open_to_opportunities_in_CH_🇨🇭_&_CA_🇨🇦-2ea44f?style=flat-square)](#)

---

## ⚡ Engineering Philosophy

I bridge the gap between **low-level hardware constraints** and **high-availability cloud architectures**. By deconstructing systems down to the compiler and kernel levels, I design software that is secure by design, highly predictable, and optimized for bare-metal performance. My focus centers on memory safety, distributed system resilience, and strict language engineering.

The clearest statement of that is a language I wrote and an operating system written in it: when the compiler is yours, a missing feature is a thing you add rather than a thing you work around.

---

## 🛠️ Technical Expertise

| Domain | Technologies & Tools |
| :--- | :--- |
| **Language & Compilers** | `Flux#` • `Rust` • Code generation • `NASM` • `x86-64 ABI` |
| **Systems & Low-Level** | Bare-metal kernels • `Rust (no_std)` • `C++` • SMP • `DRM/KMS` • `evdev` • `ALSA` • `QEMU` |
| **Cloud & Backend** | `.NET 8 (C#)` • `Node.js` • `REST` • `GraphQL` • `EF Core` |
| **Infrastructure & Security** | `Azure` • `Docker` • `Buildroot` • `CI/CD` • `SQL Server` • `MongoDB` |
| **Security Standards** | Cryptography (AES-256) • Blind Indexing • GDPR • OWASP Top 10 • Licence compliance (GPL/LGPL separation) |

---

## 📂 Architectural Showcases

### 1. FluxSharp | *Compiled Object-Oriented Systems Language* ⚖️ `MIT License` · `v1.0.8`
An open-source, compiled, type-safe language built to combine object-oriented expressiveness with predictable, secure execution — and used in production by the kernel below, which is the test that matters.
* **Compiler Architecture:** Written in Rust, a full pipeline from lexing and AST parsing to native x86-64 code generation. No VM, no garbage collector, no runtime beyond a `crt0`-sized static object.
* **A Real Object Model:** Instances with `this` passed in `rdi`, dual entry points so a method can be called with or without a receiver, and a heap allocator — added because writing drivers against static classes stopped scaling.
* **Systems Intrinsics:** MMIO and port I/O (`__load8..64`, `__in`/`__out`), atomics (`__xchg`, `__cmpxchg`), and Linux system calls (`__syscall0..5`, `__mmap`) — enough to write a device driver, or a userland program with no libc at all.
* **Tech Stack:** `Rust`, `Cargo`, `NASM`.

### 2. FluxGridOS (Research) | *Bare-Metal x86-64 Kernel, Written in Flux#*
A monolithic cloud-gaming kernel built from nothing: no standard library, no third-party module, no C. ~4.8k lines of Flux# over a hand-written assembly hardware layer. Rust appears only as the compiler's implementation language and never reaches the image.
* **Boot & Memory:** Custom Multiboot2 bootloader, long mode with 4-level paging and per-section permissions (NX, WP, SMEP/SMAP), GDT/IDT/PIC/PIT, physical page allocator and heap. 12 of 12 boot stages verified over a serial console.
* **Symmetric Multiprocessing:** Every application processor the firmware reports is released and parked, with spin locks on the page allocator and the heap — 7 of 7 at `-smp 8`. The bring-up failure was a single unset bit, `EFER.NXE`, which turned every NX page entry into a reserved-bit fault; found by reading the interrupt trace, not by guessing.
* **Networking & Streaming:** PCI enumeration, Intel e1000, ARP/IPv4/UDP/HTTP, and an RTP framebuffer streamer. **Measured: 82.2 fps at 1920×1080 raw RGBA, 5.45 Gb/s**, on one host over QEMU's e1000 and SLIRP.
* **GPU:** virtio-gpu 2D scanout verified against a host screendump; a Venus context returning `Vulkan 1.4.341`.
* **Tech Stack:** `Flux#`, `x86-64 Assembly`, `QEMU`, `GRUB2`.

### 3. FluxGridOS (Product) | *Cloud-Gaming Console on a Linux Base*
The shippable side of the same system: a Buildroot image whose entire session layer is Flux#, talking to Linux through raw system calls with no libc linked. Built so proprietary drivers can be carried where the research kernel cannot.
* **Display:** DRM/KMS brought up directly — dumb buffers, double buffering and `PAGE_FLIP` — with no libdrm. The seven-step bring-up reports which step refused, because "no display" and "another program owns the display" are different problems.
* **Input:** `/dev/input/event*` read directly, mapping a gamepad, a keyboard or a remote onto the same intentions, with non-blocking descriptors and a sleeping idle path rather than a spinning one.
* **Interface:** A Big Picture-style menu with glyph atlases rendered at build time — proportional text with no FreeType, no HarfBuzz and no font file on the image.
* **Licence Compliance:** GPL/LGPL separation audited and enforced: no static linking against LGPL libraries, GPL tools invoked as separate processes, and a third-party manifest generated from the build rather than written by hand.
* **Tech Stack:** `Flux#`, `Buildroot`, `Linux`, `DRM/KMS`, `ALSA`, `FFmpeg`.

### 4. SivaGames Ecosystem | *High-Availability Distributed Middleware*
Architected and deployed a resilient microservices ecosystem processing real-time data aggregation across 45+ production servers.
* **Resilience Patterns:** Designed and integrated Circuit Breakers, automated API Failover mechanics, and TTL multi-tier caching to absorb high traffic spikes.
* **Cloud Security:** Centralized secret management utilizing Azure Key Vault, enforced strict rate-limiting policies, and containerized services via Docker.
* **Tech Stack:** `Node.js`, `MongoDB`, `Azure Linux`, `PM2`, `Docker`.

### 5. Secure E-Commerce Core | *Banking-Grade .NET Backend*
A robust, secure-by-design API built with a strong focus on enterprise compliance, data privacy, and strict software patterns.
* **Domain-Driven Design (DDD):** Structured around Clean Architecture principles to isolate business logic from infrastructure frameworks.
* **Data Privacy & Compliance:** Implemented AES-256 encryption for PII, blind indexing for fast and secure GDPR-compliant database queries, and tokenized JWT rotation.
* **Tech Stack:** `C# .NET 8`, `Entity Framework Core`, `SQL Server`.

---

## 📈 Activity & Metrics

![GitHub Metrics](https://raw.githubusercontent.com/Yvan4001/Yvan4001/main/github-metrics.svg)

---

*"From bare-metal constraints to distributed cloud scale."*
