# Dev board decision: Arty A7-100T

**Decision date:** 2026-04-17  
**Decision owner:** Mansoor  
**Revisit if:** Phase 3+ surfaces a capacity, Ethernet, or toolchain blocker that justifies switching boards; or the toolchain ecosystem meaningfully changes.

## Decision

The primary Fathom development board is the **Digilent Arty A7-100T** (AMD/Xilinx Artix-7 XC7A100T).

Accessory plan: Digilent Pmod HDMI added when Phase 4 arrives (~$25). No other accessories at initial purchase.

## Why this board

1. **Artix-7 matches FPGC.** Bart's project targets the same family. His reference design — memory map, timing closure approach, IP choices — can inspire ours directly, saving months across Phases 2-5. Inspiration stays inspiration; the port isn't a rewrite (CONSTITUTION §3 still applies).
2. **Capacity.** 101k logic cells and 4.8 Mb BRAM leave comfortable margin after CPU + GPU + MAC + glue logic.
3. **Mature toolchain.** Vivado WebPACK is free and the industry standard. Synthesis, simulation, and debug all have a decade of hobbyist-accessible documentation.
4. **Production-grade memory.** 256 MB DDR3L + Vivado's Memory Interface Generator give a solid foundation. Building understanding of DDR3 is deeper learning than inheriting an SDRAM controller, not shallower.
5. **On-board Ethernet** (10/100) covers Phase 5 without a daughter card.
6. **Longevity.** Digilent ships this board continuously; the community will still exist in 2030.

## Known deviations from FPGC

- **DDR3L instead of SDRAM.** Our controller will not be a port of Bart's SDRAM controller. This is extra learning, aligned with Fathom's depth principle (CONSTITUTION §1).
- **Different video path.** FPGC has a custom PCB with on-board HDMI. We use a Pmod HDMI expansion when Phase 4 arrives.
- **Artix-7 vs Bart's Cyclone.** Different vendor, different primitives (LUT6 vs LUT4), different IP catalog. Architectural ideas transfer; specific IP does not.

## Alternatives considered

See [`dev-board-research-2026-04-17.md`](dev-board-research-2026-04-17.md) for the full comparison. Tipping factors that would have flipped the decision:

- **ULX3S-85F (Lattice ECP5, ~$155)** — flips if fully-open toolchain (Yosys/nextpnr/Project Trellis) is a philosophical requirement. Tradeoff accepted against it: only 32 MB SDRAM limits Phase 3 OS ambitions, and no Ethernet adds a Phase 5 detour.
- **DE10-Nano (Intel Cyclone V SoC, ~$225)** — flips if gigabit Ethernet and 1 GB DDR3 from day one matter more than matching the FPGC reference. Tradeoff accepted against it: Cortex-A9 hard processor (HPS) on-die is a constant temptation to cheat the "from scratch" rule.
- **Tang Mega 138K Pro Dock (Gowin, ~$100-130)** — rejected. Cheap and capable on paper, but Gowin toolchain maturity is a real multi-year risk for a project where timing-closure debugging will be frequent.

## Ordering

**Primary source — Digilent direct:**
https://digilent.com/shop/arty-a7-100t-artix-7-fpga-development-board/

**Authorized distributors** (check for stock and shipping differences):
- DigiKey: https://www.digikey.com/en/products/detail/digilent-inc/410-319/5413892
- Mouser: search "Arty A7-100T"
- Newark (Element14): search "Arty A7-100T"
- Amazon: available intermittently, sometimes marked up — prefer direct.

**At-purchase accessory list:** none required. The board ships with a micro-USB cable for programming and bus power. A 12V barrel-jack wall supply is optional and only needed if peripherals draw beyond the USB power budget; defer until peripherals land.

## Phase 4 trigger

When Phase 4 begins, order **Digilent Pmod HDMI** (~$25):
https://digilent.com/shop/pmod-hdmi-high-definition-multimedia-interface/
