# HSEAE Photonic Memory
### Holographic Seeding and Electro-Acid Etching for Transparent Ceramic Computing

> **Document Version:** 2.3 — Final Submission Draft  
> **Status:** Pre-submission / Under review  
> **Proposed Duration:** 42 months  
> **Budget Estimate:** $5.2M – $7.3M  
> **Target Agencies:** DARPA · IARPA · NSF · ERC · AFOSR/ONR

---

## Overview

This repository contains the full research proposal for a **volumetric monolithic memory architecture** fabricated within a pre-formed porous Aluminum Oxynitride (AlON) ceramic scaffold using the HSEAE process.

The core idea: abandon planar lithography entirely. Instead of stacking layers of silicon, we grow a complete 3D memory system — conductive paths, memristive junctions, and optical readout geometry — inside a transparent ceramic block, using holographic light patterns to define where chemistry happens.

**Write electronically. Read optically. No sneak paths. No selector devices.**

---

## The Problem

Data movement between processor and memory consumes **>60% of system energy** in large-scale AI workloads. Existing solutions are hitting walls:

| Technology | Bottleneck |
|---|---|
| DRAM | Capacitor scaling limits; 10–50 ns latency |
| 3D NAND | Lithography-limited density; sneak path currents |
| HBM | TSV density; inter-layer thermal resistance |
| ReRAM (2D/3D) | Sneak paths require selectors, doubling cell area |

HSEAE proposes a fundamentally different path: **volumetric density defined by diffraction limits, not lithography limits**, with optical readout that physically cannot suffer sneak path currents.

---

## The HSEAE Process

```
Pre-fabricated          Two-photon           Electrochemical
porous AlON      →      holographic    →      processing      →   Functional
scaffold               seeding (PAGs)         (2V bias)           memory cube
```

### Step 1 — Scaffold
Porous AlON (20–50 nm pores, >50% porosity) is fabricated via sacrificial templating or combustion synthesis at 1600–1900 °C. This decouples ceramic densification from all subsequent low-temperature steps. Optionally coated with 1–2 nm Al₂O₃ by ALD to eliminate reactive nitride surface sites before acid exposure.

### Step 2 — Infiltration
Two-stage vacuum infiltration:
- **Stage 1:** PAG (photoacid generator) + AgNO₃ + PEO-LiClO₄ electrolyte
- **Stage 2** (post-rinse): Zn(NO₃)₂ + PEO-LiClO₄ only  
Sequential stages avoid Ag⁺/Zn²⁺ galvanic interference (ΔE° = 1.56 V).

### Step 3 — Holographic Writing
A spatial light modulator (SLM) generates pre-computed wavefronts that, after propagating through the characterised scattering medium (the scaffold itself), focus two-photon excitation precisely at target voxels. The porous AlON is not just a passive host — it is an **active scattering element** whose transmission matrix, once characterised, enables depth-resolved focusing beyond what conventional optics alone could achieve.

Two writing modalities:
- **Modality A:** Full-volume parallel holographic exposure (fast; fixed pattern)
- **Modality B:** Sequential CNC-like voxel scanning (adaptive; layer-by-layer correction)

At each activated voxel, the two-photon PAG generates localised Brønsted acid (H₀ ≈ −12). The acid is confined by four layered mechanisms (see below).

### Step 4 — Electrochemical Processing
A 2V bias drives:
1. Silver filament formation at acid-seeded lattice nodes (Stage 1)
2. ZnO electrodeposition at silver filament tips (Stage 2, after Ag⁺ rinse)
3. Al(OH)₃ → Al₂O₃ consolidation (300–500 °C, after electrolyte removal)

### Step 5 — Optical Readout
A NIR laser (850–1300 nm) probes the cube. ZnO LRS/HRS states alter the local refractive index (Δn ≈ 0.01–0.1), modulating transmitted light. A 2D SPAD array reads an entire memory plane simultaneously — no beam steering, no sneak paths.

---

## Key Technical Parameters (Version 2.3)

| Parameter | Realistic Target | Aspirational (Long-term) |
|---|---|---|
| Lattice pitch | 200 nm (diffraction-limited at 800 nm, NA 1.4) | <100 nm (STED / synthetic aperture) |
| Volumetric density | **125 Gb/cm³** | 1 Tb/cm³ |
| Read latency | <10 ns | <1 ns |
| Write voltage | 2V | 1–2V |
| Writing depth | >500 µm (T-matrix compensated) | >1 mm |
| Optical window | 800–1300 nm (AlON transparency) | 800–1300 nm |
| Scaffold porosity | >50% (20–50 nm pores) | >60% |
| Infiltration efficiency | >95% (Phase 1 gate criterion) | >99% |
| Write endurance | >10⁶ cycles (Phase 2 target) | >10⁹ cycles |
| Data retention | >10 years at 85°C (accelerated) | >10 years at 125°C |

> **Note on the 1 Tb/cm³ figure:** Achieving this requires either STED-like beam shaping, shorter excitation wavelength (with explicit scattering penalties), or synthetic aperture super-resolution. It is a Phase 4+ research goal, not a Phase 1–3 deliverable. The 125 Gb/cm³ figure at 200 nm pitch is the physically validated near-term target.

---

## Acid Diffusion Confinement: Four Layers

The core fabrication challenge is keeping photogenerated acid at the intended voxel. Unconfined H⁺ in bulk solution diffuses ~105 µm in 10 minutes. The solution is layered confinement:

```
Layer 1: Polymer-bound PAGs     → Tethered counterion; ~20–80 nm in liquid-phase pores
Layer 2: Nanopore tortuosity    → D_eff = D/τ ≈ 3–5×10⁻¹⁰ m²/s; ~80–90 nm at 10 ms
Layer 3: Double-layer overlap   → <50 nm pores alter ion mobility; 2–5× additional reduction
Layer 4: Al(OH)₃ passivation   → Insoluble, volume-expanding; self-seals reacted voxel
─────────────────────────────────────────────────────────────────────────────────────────
Combined target: <50 nm net acid spread at 200 nm pitch (Phase 0 empirical validation)
```

> ⚠️ The <10 nm diffusion claim common in solid-film lithography PAG literature **does not transfer directly** to liquid-infiltrated pore networks. The 20–80 nm range is a corrected estimate for this geometry. Phase 0 measures this empirically — it is not assumed.

---

## T-Matrix Writing Stability

Scattering-assisted holography requires the transmission matrix (T-matrix) to remain stable during writing. Each write event modifies the medium:

| Voxel type | Δn per voxel | Relative T-matrix impact |
|---|---|---|
| Al(OH)₃ / Al₂O₃ | ~0.05–0.1 | 1× baseline |
| ZnO junction | ~0.05–0.1 | ~2–5× |
| **Silver filament** | **~1.5–2.0 + large imaginary** | **~100–500×** |

Silver voxels dominate drift. A zone-based writing protocol (50 µm zones, independent T-matrix per zone) bounds the maximum writes under any single characterisation to ~10⁶ voxels — within stability limits. Interleaved guide-star re-characterisation every 10,000 writes provides a secondary safeguard.

---

## ALD Coating: Why Al₂O₃ over HfO₂

Both HfO₂ and Al₂O₃ ALD protect AlON pore walls from photoacid attack. Al₂O₃ is preferred:

| Property | HfO₂ ALD | Al₂O₃ ALD |
|---|---|---|
| Acid resistance | High | High |
| Surface -OH density | ~5×10¹⁴ cm⁻² (quenches ~10–16% of acid in 50 nm pores) | Similar, but reaction product is Al(OH)₃ — **consistent with intended chemistry** |
| Nitride elimination | Partial | **Complete** — converts reactive AlON surface to pure oxide |
| Passivation needed? | PFOTS fluorinated silane (HMDS is acid-labile — not suitable) | Generally not required |
| Deposition complexity | Standard | Simpler |

Al₂O₃ ALD converts the reactive N³⁻-bearing surface to a pure oxide surface, eliminating the nitride protonation pathway entirely. Its acid interaction (forming Al(OH)₃) is chemically consistent with the intended self-passivation mechanism rather than a competing side reaction.

---

## Programme Structure

```
Phase 0 (Months 1–6)     Simulation, screening, chemical compatibility
  Gate 0A (Month 4)  ──► AlON etch <10 nm/pulse AND acid yield >70%
  Gate 0B (Month 6)  ──► MFP >200 µm · T-matrix drift <5% · PAG diffusion <100 nm

Phase 1 (Months 6–21)    Single-layer proof-of-concept
  Gate 1  (Month 21) ──► Single-layer switch · Δn >0.02 · >90% device yield

Phase 2 (Months 21–33)   Multi-layer integration + CNC-mode writing
  Gate 2  (Month 33) ──► 3-layer cube · electronic write / optical read · <10% cross-talk

Phase 3 (Months 33–42)   Prototype demonstrator
  Gate 3  (Month 42) ──► 10+ layer cube · <10 ns read · ≥2 peer-reviewed publications
```

All gates are **mandatory and binary**. Programme funding does not advance without gate passage.

---

## Risk Summary

| Risk | Prob. | Impact | Primary Mitigation |
|---|---|---|---|
| AlON scaffold etching by photoacid | High | High | Phase 0 gate; Al₂O₃ ALD preferred |
| ALD coating quenches generated acid | High | High | Al₂O₃ ALD (compatible chemistry); PFOTS if HfO₂ used |
| Acid diffusion exceeds 200 nm pitch | High | High | Four-layer confinement (see above) |
| Infiltration incomplete (<95%) | High | High | Vacuum optimisation; SAXS gate |
| T-matrix drift (silver-dominated) | Medium | High | Zone-based writing; 10,000-write re-characterisation cadence |
| Polymer-bound PAG diffusion in liquid pores | Medium | High | Phase 0 empirical measurement (not assumed from solid-film data) |
| Galvanic Ag/Zn incompatibility | Medium | High | Two-step infiltration; ICP-OES rinse gate |
| Optical contrast insufficient | Medium | Medium | Empirical Δn measurement; plasmonic enhancement |

Full risk register with 13 items and mitigations is in the proposal document.

---

## Budget Overview (42 months)

| Category | Cost (USD) |
|---|---|
| Personnel (PI + 2 postdocs + 3 PhD students) | $1,800,000 |
| Equipment (SLM, lasers, SPAD, ALD, probes) | $1,550,000 |
| Materials (AlON, PAGs, substrates) | $400,000 |
| Characterisation (TEM, XRD, ICP-OES) | $500,000 |
| Cleanroom / fabrication access | $450,000 |
| Computing (GPU cluster, T-matrix) | $150,000 |
| Travel and dissemination | $100,000 |
| **Subtotal Direct** | **$4,550,000** |
| Indirect / overhead (50%) | $2,275,000 |
| Contingency (10%) | $455,000 |
| **TOTAL** | **~$7.3M** |

Modular phasing enables a reduced $5.2M scope (36 months, Phases 0–2 only) if preferred by the funding agency.

---

## Competitive Position

| Feature | 3D NAND | ReRAM | HSEAE (V2.3) |
|---|---|---|---|
| Density ceiling | Lithography-limited | Selector-limited | Diffraction-limited (200 nm → 125 Gb/cm³) |
| Read mechanism | Electrical | Electrical (sneak paths) | **Optical (parallel, no sneak paths)** |
| Thermal management | Poor (Si insulator) | Moderate | **Excellent (AlON 12 W/m·K)** |
| Radiation hardness | Vulnerable | Moderate | **High (AlON + ZnO)** |
| Manufacturing | Multi-step litho | Litho-based | Volumetric scaffold synthesis |
| Read latency | 10–50 ns | 10–50 ns | **<10 ns target** |

---

## Target Funding Agencies

**United States**
- DARPA — Electronics Resurgence Initiative (ERI) / 3DSoS
- IARPA — Ultra-low power computing
- NSF DMREF — Materials discovery (Thrust 1)
- NSF CISE/CCF — Computer architecture implications
- AFOSR / ONR — Radiation-hardened electronics
- DOE ASCR — Exascale memory architectures

**Europe**
- ERC Pathfinder / FET-Open (Horizon Europe EIC)
- Horizon Europe Cluster 4

**Industry / Partnership**
- imec — Core partner programme
- Samsung / SK Hynix — University R&D collaboration

---

## Document History

| Version | Key Changes |
|---|---|
| 1.0 | Initial proposal. Fatal flaws: in-situ AlON densification (thermodynamically impossible), UV holography in scattering medium, no risk register. |
| 2.0 | Porous AlON scaffold; two-photon NIR PAGs; formal risk register introduced. Remaining issues: pitch/density mismatch, acid diffusion unquantified, PEO thermal conflict. |
| 2.1 | Density corrected to 125 Gb/cm³ (200 nm pitch); acid diffusion model; electroforming sequence reordered; galvanic incompatibility resolved; photon budget with background noise. |
| 2.2 | Scaffold chemical stability under photoacid (new Section 3.4); angular multiplexed "holographic CNC" writing; T-matrix stability as explicit risk; Al³⁺ electrolyte contamination risk. |
| **2.3** | **Four-layer acid confinement model; Al₂O₃ ALD preferred over HfO₂; HMDS replaced by PFOTS; T-matrix drift corrected for silver-voxel dominance; zone-based writing protocol; polymer-bound PAG liquid-phase diffusion as new measured (not assumed) parameter.** |

---

## Repository Contents

```
├── README.md                        ← This file
└── HSEAE_Proposal_v2.3.docx         ← Full research proposal (42 months, $7.3M)
```

---

## Acknowledgements

This proposal builds upon foundational research in:
- Two-photon photoacid generators (AFOSR, NSF, ONR supported)
- Porous AlON development (U.S. Department of Energy / Battelle Energy Alliance)
- Wavefront shaping through scattering media (Vellekoop & Mosk 2007; Popoff et al. 2010)
- Droplet-scale anodisation (Ateneo de Manila University / Nara Institute of Science and Technology)
- Scattering-assisted holography (USTC and related groups)
- ALD in nanoporous ceramics (extensive literature)
- ZnO ReRAM switching (broad community)

---

*Unclassified — For official review and funding consideration.*
