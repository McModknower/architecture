# Instructions & Instruction Layout

## Layout

In this architecture all instructions are four bytes long:

```
 1 2 3 4 5 6 7 8
+-+-+-+-+-+-+-+-+
|a|b|  opcode   |
+-+-+-+-+-+-+-+-+
|   source 1    |
+-+-+-+-+-+-+-+-+
|   source 2    |
+-+-+-+-+-+-+-+-+
|  destination  |
+-+-+-+-+-+-+-+-+
```

**a: 1 bit**
Is set if source 1 is an immediate value.

**b: 1 bit**
Is set if source 2 is an immediate value.

**opcode: 6 bits**
Is the opcode, further details are written below in its section.

**source 1: 8 bits**
Is the source for the first argument.
If a is set, this value is taken directly.
Otherwise this is the register that holds the value.

**source 2: 8 bits**
Is the source for the second argument.
Works like source 1, but uses b.

**destination: 8 bits**
The place where the result will be saved, if applicable.
If the result should be ignored, set this to 0 (see [Registers](registers.md) for more info).

## Opcodes

Opcodes are split into 4 categories based on their 2-bit prefix:
- `00` are special instructions, currently only halt. Here the other 4 bits are ignored, but they should be set to zero regardless for future expansion.
- `01` are conditional save instructions.
- `10` are storage instructions, like RAM and level IO.
- `11` are ALU instructions.

All unspecified opcodes are reserved for future use and using them is undefined behaviour, as their behaviour may change in the future.

### Conditional save instructions

Conditional save instructions test the first argument and if the test is successful, the second argument is stored in the destination.

Conditional save instructions treat the 4 bits as a bitfield: `abcd`.
The highest bit (a) is zero.
b and c determine if =0 and >127 are tested. The results of these tests are combined by OR.
If the lowest bit (d) is set, the result of the previous tests is inverted.

Together these can express a multitude of conditions. Below is a table with the most useful combinations:
| Test    | Bitfield | when using the result of signed `a-b` |
|---------|----------|---------------------------------------|
| zero    | 0100     | a==b                                  |
| nonzero | 0101     | a/=b                                  |
| >127    | 0010     | a<b                                   |
| >=127   | 0110     | a<=b                                  |
| <127    | 0111     | a>b                                   |
| <=127   | 0011     | a>=b                                  |

### Storage
TODO

### ALU
TODO
