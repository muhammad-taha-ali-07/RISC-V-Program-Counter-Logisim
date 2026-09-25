# RISC-V Program Counter in Logisim

A simple **32-bit RISC-V Program Counter (PC)** implemented using **Logisim Evolution**.

The circuit updates the Program Counter on every rising clock edge according to:

```text
PC_next = PC + 4
```

This represents the normal sequential execution of 32-bit RISC-V instructions.

## Circuit Components

The Program Counter circuit consists of:

- 32-bit Register
- 32-bit Adder
- 32-bit Constant `4`
- Clock
- Write Enable
- Reset
- Carry-In constant `0`

## Working Principle

The current value of the Program Counter is stored inside a 32-bit register.

The register output is connected to one input of a 32-bit adder.

A constant value of `4` is connected to the second input.

```text
PC ----+
       |
       v
   +---------+
   |  Adder  |----> PC + 4
   +---------+
       ^
       |
       4
```

The result of the addition is fed back into the input of the PC register.

```text
        +-----------------------+
        |                       |
        |                       v
   +---------+              +---------+
   |   PC    |------------->|  Adder  |
   |Register |              |  PC + 4 |
   +---------+              +---------+
        ^                       |
        |                       |
        +-----------------------+
```

On every **rising clock edge**, the new value is stored in the PC register.

## PC Sequence

Starting from:

```text
PC = 0
```

The Program Counter produces:

```text
0
4
8
12
16
20
24
28
...
```

In hexadecimal:

```text
00000000
00000004
00000008
0000000C
00000010
00000014
00000018
0000001C
...
```

## Control Signals

### Write Enable

The register's **WE (Write Enable)** input is connected to:

```text
1
```

This allows the PC register to update on every clock edge.

### Reset

The register's **Reset** input is normally connected to:

```text
0
```

When reset is activated, the Program Counter can be cleared back to zero.

### Carry-In

The adder's carry input is connected to:

```text
0
```

Therefore:

```text
PC_next = PC + 4 + 0
```

## Testing

The circuit was tested using manual clock ticks in Logisim Evolution.

Expected sequence:

```text
00000000
00000004
00000008
0000000C
00000010
```

The circuit successfully increments the Program Counter by **4 on each rising clock edge**.

## Software

Built using:

**Logisim Evolution 4.1.0**

## Project File

```text
RV32I_Program_Counter.circ
```

## Status

- [x] 32-bit Program Counter
- [x] PC + 4 Adder
- [x] Clock Input
- [x] Write Enable
- [x] Reset
- [x] Manual Clock Testing
- [x] Sequential PC Increment Verified

## Author

**Muhammad Taha Ali**

Computer Systems Engineering
