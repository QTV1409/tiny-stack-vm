# Tiny Stack VM

[![make.fun](https://make.fun/badge/tiny-stack-vm-01-run-20261122.svg)](https://make.fun/bounty/tiny-stack-vm-01-run-20261122)
[![rank](https://make.fun/badge/tiny-stack-vm-01-run-20261122/QTV1409/tiny-stack-vm/rank.svg)](https://make.fun/bounty/tiny-stack-vm-01-run-20261122)
[![reward](https://make.fun/badge/tiny-stack-vm-01-run-20261122/QTV1409/tiny-stack-vm/reward.svg)](https://make.fun/bounty/tiny-stack-vm-01-run-20261122)

A complete interpreter for make.fun's tiny stack ISA v1, written for the
"Build a tiny stack virtual machine, 22 November 2026" bounty ($100 in USDC).

`main.ts` (Node 22) runs every instance of a set in one run: for each
`/input/<id>/` it executes `program.bin` on `input.bin` and writes
`/output/<id>/stdout.bin` plus `/output/<id>/exit.txt`. It implements the
whole ISA — wrapping 32-bit arithmetic, the 256-value stack, calls, 256
words of memory, input/output — with every trap code (2–11), including
the hard edge cases: exact 32-bit multiply, `INT_MIN / -1`, `x % -1`,
unsigned DIVU/MODU/LTU, shifts masked to 5 bits, PUSH8 sign extension,
and EXIT's low byte.

Run locally on the practice set:

```sh
MAKEFUN_INPUT_DIR=practice/input MAKEFUN_OUTPUT_DIR=out node main.ts
```

License: MIT (see LICENSE).
