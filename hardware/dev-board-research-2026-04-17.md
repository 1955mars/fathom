# Dev board research — 2026-04-17

Point-in-time snapshot of the FPGA board comparison that led to the [Arty A7-100T decision](dev-board-decision.md). Pricing and availability reflect the date stamped above; re-check before any future re-evaluation.

## Candidates

| Feature | **Arty A7-100T** | **ULX3S-85F** | **DE10-Nano** | **Tang Mega 138K Pro Dock** |
|---|---|---|---|---|
| Price (2026) | $299 | ~$155 | ~$225 ($190 edu) | ~$100-130 |
| FPGA | Artix-7 XC7A100T | Lattice ECP5 LFE5U-85F | Cyclone V SoC (5CSEBA6) | Gowin GW5AST-138K |
| Logic | 101k LCs / ~63k LUT6, 4.8 Mb BRAM | 84k LUT4, ~3.7 Mb BRAM | 110k LEs, 5.5 Mb BRAM + HPS | 138k LUT4, large BRAM |
| On-board RAM | 256 MB DDR3L | 32 MB SDRAM (166 MHz) | 1 GB DDR3 (shared w/ HPS) | 1 GB DDR3 |
| Video | Pmod HDMI (add-on) | Built-in GPDI/HDMI | Built-in HDMI (Full HD) | HDMI onboard (Pro Dock) |
| Ethernet | 10/100 onboard | None (USB/WiFi via ESP32) | Gigabit onboard | Gigabit + SFP+ |
| Toolchain | Vivado WebPACK (free, vendor) | Yosys + nextpnr (fully open) or Diamond | Quartus Prime Lite (free) | Gowin EDA (free, closed, less polished) |
| Community | Very large; hobbyist reference designs everywhere | Strong open-source / Hackaday following | Huge (MiSTer retro-gaming) | Growing, still thin |

## Tipping factors

- **ULX3S-85F** would flip the decision if a fully-open toolchain (Yosys / nextpnr / Project Trellis) were a philosophical requirement. Tradeoff: only 32 MB SDRAM limits Phase 3 OS ambitions; no Ethernet adds a Phase 5 detour.
- **DE10-Nano** would flip if gigabit Ethernet and 1 GB DDR3 from day one mattered more than matching the FPGC reference. Tradeoff: Cortex-A9 HPS is a constant temptation to cheat "from scratch."
- **Tang Mega 138K** was rejected despite cheap and capable hardware because Gowin's toolchain maturity is a real risk over a multi-year project with frequent timing and synthesis debugging.

## Sources (retrieved 2026-04-17)

- [Arty A7-100T product page — Digilent](https://digilent.com/shop/arty-a7-100t-artix-7-fpga-development-board/)
- [Arty A7 reference — Digilent](https://digilent.com/reference/programmable-logic/arty-a7/start)
- [ULX3S — Crowd Supply](https://www.crowdsupply.com/radiona/ulx3s) / [radiona.org](https://radiona.org/ulx3s/)
- [DE10-Nano — Terasic](https://de10-nano.terasic.com/)
- [Tang Mega 138K wiki — Sipeed](https://wiki.sipeed.com/hardware/en/tang/tang-mega-138k/mega-138k.html)
- [Tang Console coverage — CNX Software](https://www.cnx-software.com/2025/05/27/sipeed-tang-console-a-gowin-gw5ast-gw5at-board-with-60k-or-138k-lut-for-fpga-development-and-retro-gaming/)
