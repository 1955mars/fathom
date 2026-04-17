# Roadmap

*A rough sketch. Detailed milestones and content plan to be added after the CONSTITUTION is drafted.*

## Phase 0 — Foundations (4-6 months)

- nand2tetris (full course, both parts)
- Harris & Harris, *Digital Design and Computer Architecture* (RISC-V ed., 2nd)
- Patterson & Hennessy, *Computer Organization and Design* (RISC-V ed.)
- Verilog from scratch: HDLBits + local sim toolchain (Icarus + GTKWave + Verilator)
- Select hardware target and order dev board at end of phase

## Phase 1 — First CPU on real FPGA (6-12 months)

- Dev board bring-up: blink → UART
- Custom ISA running on BRAM
- SDRAM controller
- Assembler (written from scratch)

## Phase 2 — Toolchain and bare-metal C

- Port and modify QBE + cproc as C compiler
- Linker
- Minimal libc
- Bare-metal programs running from flash

## Phase 3 — Filesystem, OS, user programs

- Custom filesystem
- Operating system with syscalls
- Set of user programs

## Phase 4 — GPU, HDMI, framebuffer

- Custom GPU in Verilog
- HDMI output
- Graphics primitives

## Phase 5 — Networking

- Ethernet MAC
- Custom L2 protocol
- Networked applications

## Phase 6 — Custom PCB, case, standalone machine

- PCB design in KiCad
- Board bring-up
- 3D-printed case
- Standalone physical computer
