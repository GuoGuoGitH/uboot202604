# U-Boot Driver Model — Annotated Source Study

A source-level research workspace focused on **U-Boot internals, Device Tree, and the Driver Model lifecycle**.

This repository uses upstream U-Boot source as a baseline. My study commits trace how the firmware discovers a device tree, creates device-model objects, binds drivers, and probes devices during boot.

## What I'm studying

| Topic | Entry points |
| --- | --- |
| FDT discovery and setup | `lib/fdtdec.c`, `fdtdec_setup()` |
| Driver Model initialization | `drivers/core/root.c`, `dm_init()` |
| Device creation and binding | `drivers/core/device.c`, `device_bind_common()` |
| Device Tree scanning and driver matching | `drivers/core/lists.c`, `lists_bind_fdt()` |
| Device activation | `drivers/core/device.c`, `device_probe()` |
| Device Tree properties | `device_of_to_plat()`, `ofnode` helpers |

## Approach

1. Follow the call chain from early firmware initialization into DM setup.
2. Read the relevant C code and annotate control flow and data structures.
3. Separate source observations from changes that affect runtime behavior.
4. Validate any functional changes before treating them as fixes.

## Important status note

**Research in progress — not a production-ready U-Boot fork.**

Most personal commits add explanatory notes to upstream code. At least one study commit also contains non-comment source changes, which have **not** been presented here as build-tested or hardware-validated fixes. Do not use this branch as a drop-in production baseline without review.

## Credit

U-Boot and its imported history are the work of the [upstream U-Boot community](https://source.denx.de/u-boot/u-boot). Upstream commits are not my original contributions.

My additions in this repository are primarily personal research annotations.
