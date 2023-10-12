# TST / TEQ
## Test / Test Equivalence

TST{cond} Rn, Op2
TEQ{cond} Rn, Op2

These instructions test the value in a register against Op2.
They update the condition flags on the result but do not place the result in any register.
The _TST_ instruction performs a *bitwise AND* operation on the value in *Rn* and the value of *Op2*.
This is the same as the ANDS instruction, except that the result is discarded.

The _TEQ_ instruction performs a *bitwise Exclusive OR* operation on the value in *Rn* and the value of *Op2*.
This is the same as the EORS instruction, except that the result is discarded.


## Example
Assume:
    r0  -> 0x1000
    r9  -> 0x31
    r10 -> 0x38

`TST r0, #0x3F8` -> `Bitwise AND (0x1000, 0x3F8)` -> `0x0` -> `Z = 1` & `N = 0`

`TEQEQ r10, r9` -> `If Z == 1` -> `Bitwise XOR (0x31, 0x38)` -> `0x09` -> `Z = 1` & `N = 0`
