# ◆ Arm Cortex-A Presentation Series

Interactive slide decks covering the Arm **Cortex-A** application-profile family end-to-end — from the ARM1176 and Cortex-A8 that powered the first smartphones, through the pivot to **AArch64** in Cortex-A57, up to the current Armv9-A "Blackhawk / Chaberton" generations used in flagship phones and SoCs.

Designed for SoC, CPU microarchitecture, and kernel engineers building or working on Arm application processors (phones, tablets, laptops, automotive SoCs, embedded Linux platforms).

## ▶ [Open the Series Landing Page](https://brendanjameslynskey.github.io/Cortex_A/)

> **Setup:** Enable GitHub Pages (Settings → Pages → Deploy from `main` branch, `/ (root)` directory).
>
> Alternatively, open `index.html` locally in any browser — all presentations work offline after first load.

---

## Presentations

| # | Topic | Slides | Status |
|---|-------|--------|--------|
| 01 | History &amp; the Cortex-A Family | 18 | ✅ Complete |
| 02 | Armv8-A / Armv9-A Architecture &amp; Exception Levels | 18 | ✅ Complete |
| 03 | Memory System — VMSA, Caches &amp; Ordering | 18 | ✅ Complete |
| 04 | Vector Extensions — NEON, SVE, SVE2, SME | 16 | ✅ Complete |
| 05 | Security &amp; Virtualization — TrustZone-A, PAC/BTI, MTE, RME/CCA | 17 | ✅ Complete |
| 06 | Microarchitecture — OoO, big.LITTLE, DynamIQ, PMU | 17 | ✅ Complete |

---

## Presentation 01: History &amp; the Cortex-A Family

18 slides from ARM11 (the last of the "classic" cores) through every Cortex-A generation: **A8** (first Armv7-A in the iPhone 3GS, 2009), **A9** (first multi-core Arm SoC — Tegra 2, OMAP4), **A15** (big.LITTLE foundation with **A7**), **A53 / A57** (the AArch64 switch-over, 2014), **A72 / A73 / A75 / A76 / A77 / A78** (annual Austin/Cambridge cadence), **X1 / X2 / X3 / X4** (Cortex-X "Custom Cores"), **A510 / A520** (Armv9 little), **A715 / A720 / A725** (Armv9 middle), and the 2024 **Cortex-X925 (Blackhawk)** + **Cortex-A925**. Also covers the **big.LITTLE → DynamIQ** transition, the 2011 acquisition of the Texas Instruments OMAP team into Arm Austin, and why Arm killed the 32-bit-only Cortex-A32.

## Presentation 02: Armv8-A / v9-A Architecture

18 slides on the A-profile architecture — **Exception Levels EL0 → EL3**, AArch64 vs AArch32 execution states, **SPSR / ELR / VBAR** exception-handling registers, the 64-bit A64 ISA (31 × 64-bit GPRs + XZR, fixed 32-bit encoding, PC-relative addressing), synchronous vs asynchronous exceptions, the **WFI / WFE / SEV** low-power instructions at A-profile, and the Armv9-A additions (**SVE2 mandatory**, Confidential Compute Architecture, MPAM v1, BRBE, TRBE).

## Presentation 03: Memory System — VMSA, Caches &amp; Ordering

18 slides on the A-profile memory system — **VMSAv8-64** (4 KB / 16 KB / 64 KB translation granules, up to 5 levels for 52-bit VAs), **Stage 1** (OS) and **Stage 2** (hypervisor) translation, **TCR_EL1 / TTBR0 / TTBR1**, **ASID / VMID** tagged TLBs, **VAE1 / VAE2 / VAE3 IS** maintenance instructions, L1 / L2 / L3 / SLC hierarchies, **Point-of-Unification (PoU)** vs **Point-of-Coherency (PoC)**, the weakly-ordered Arm memory model, **DMB / DSB / ISB** barriers, **LDAR / STLR** release-consistency loads/stores, **LSE atomics** (Armv8.1-A, CAS / SWP / LDADD families), and **RCpc** (Armv8.3-A) for relaxed consistency loads.

## Presentation 04: Vector Extensions — NEON, SVE, SVE2, SME

16 slides on A-profile SIMD — **NEON** (Advanced SIMD, 128-bit fixed), instruction layout (Q / D register file sharing with the FPU), common kernels (memcpy / string search / 4×4 matmul). **SVE** (Scalable Vector Extension, 128–2048 bit, vector-length agnostic) — predicate registers, vector-length-agnostic loops, gather/scatter, Fujitsu A64FX context. **SVE2** (mandatory in Armv9-A) — brings SVE to mobile, adds integer helpers, string ops, crypto. **SME** (Scalable Matrix Extension, Armv9.2-A) — ZA tile storage, outer-product instructions, streaming mode, and how SME relates to the Apple AMX / matrix co-processors.

## Presentation 05: Security &amp; Virtualization

17 slides on A-profile security and virt — **EL2 hypervisor mode**, **Stage 2 translation**, **VHE** (Virtualization Host Extensions) that let a host Linux kernel run in EL2 directly, **EL3 secure monitor** and the SMC calling convention. **TrustZone-A** — secure / non-secure worlds, banked SCR registers, secure memory tagging in the bus. **Pointer Authentication (PAC)** — PACIA / PACIB / AUTIA / RETAA, the QARMA cipher, how PAC defeats ROP. **BTI** (Branch Target Identification) — JOP defeat in Armv8.5-A. **MTE** (Memory Tagging Extension) — 4-bit colour tags in the top of the pointer, asynchronous vs synchronous modes, why Pixel 8 was the first to ship it. **RME / CCA** — the Armv9-A Realm Management Extension, four worlds (NS / Secure / Root / Realm), GPT (Granule Protection Table), and how CCA lets cloud tenants get confidential compute on Arm.

## Presentation 06: Microarchitecture

17 slides on A-class microarchitecture — deep **OoO pipelines** (Cortex-A76 onwards: 13-stage, 4-wide fetch, 8-wide issue), branch prediction (TAGE-style predictors, BTB, RSB), instruction prefetching, **big.LITTLE** dual-cluster origins (2011, A15 + A7), the 2017 pivot to **DynamIQ Shared Unit (DSU)** where heterogeneous cores share a single L3, the DSU-110 / DSU-120 cache-coherent hub, the **1 + 3 + 4** triple-cluster layout seen in modern phones (1 × X-core + 3 × A-core + 4 × A5xx), **PMU** (up to 6 programmable counters per PE, SPE for statistical profiling), **ETE / TRBE** for embedded trace buffers, and the microarchitectural security features (**STIBP / SSBS** for speculative side-channels).

---

## Technical details

- **Framework:** [Reveal.js 4.6.1](https://revealjs.com) from CDN
- **Fonts:** Playfair Display (headings), DM Sans (body), JetBrains Mono (code)
- **Offline:** works after first load (fonts &amp; Reveal.js cached by the browser)
- **Navigation:** `→` / `←` for slides, `Esc` for overview, `F` for fullscreen, `S` for speaker notes

## Related repositories

- [Hardware](https://github.com/BrendanJamesLynskey/Hardware) — parent hub
- [Arm Cortex-M Presentation Series](https://github.com/BrendanJamesLynskey/Cortex_M) — sibling deck set on the M-profile CPU
- [Arm Neoverse Presentation Series](https://github.com/BrendanJamesLynskey/Neoverse) — sibling deck set on infrastructure / server A-profile cores
- [Arm System IP Presentation Series](https://github.com/BrendanJamesLynskey/Arm_System_IP) — GIC, SMMU, DynamIQ, MPAM
- [Arm AMBA Presentation Series](https://github.com/BrendanJamesLynskey/AMBA) — interconnect protocols used by every Cortex-A system
- [Modern SoC Design](https://github.com/BrendanJamesLynskey/SoC) — same visual style, complementary topics

## License

Educational use. Content © Brendan Lynskey. Fonts and Reveal.js retain their own licenses.
