# QuackQuack Extension — Part B

## Our New Instructions

We added 4 new instructions to the computer. We picked these because they make the computer easier to program.

| Name | Number (Opcode) | What it does |
|---|---|---|
| INC  | 0x40 | ra = ra + 1 |
| DEC  | 0x41 | ra = ra - 1 |
| CLR  | 0x42 | ra = 0 |
| OUTC | 0x50 | Prints ra as a character |

---

## 1. INC ra (Opcode: 0x40)

**How it works:**
It adds 1 to whatever is in register `ra`. 

**Why we added it:**
In most programs, you need to count things (like loops). Instead of having to move the number 1 into a different register and then using `addw`, you can just use `inc`. It makes the program shorter and easier to read.

**Example:**
```
inc r0   ; Adds 1 to r0
```

---

## 2. DEC ra (Opcode: 0x41)

**How it works:**
It subtracts 1 from register `ra`.

**Why we added it:**
This is great for countdown loops. If you want to do something 5 times, you start at 5 and use `dec` until you hit 0. It also updates the Zero Flag, so you can jump back to the start of the loop easily.

**Example:**
```
dec r1   ; Subtracts 1 from r1
```

---

## 3. CLR ra (Opcode: 0x42)

**How it works:**
It sets register `ra` to 0.

**Why we added it:**
Usually, to reset a register to zero, you have to use a long instruction like `irmovw $0, ra`. Using `clr` is faster and it's very clear what the code is doing.

**Example:**
```
clr r2   ; Sets r2 to zero
```

---

## 4. OUTC ra (Opcode: 0x50)

**How it works:**
It takes the character code in register `ra` and prints it to the screen.

**Why we added it:**
Before this, printing a character was hard because you had to know the special memory address for the screen. Now, you just put the character you want in a register and use `outc`. It's much simpler for debugging.

**Example:**
```
irmovb $65, r0   ; 65 is 'A'
outc r0          ; Prints 'A'
```

---

## Implementation Details
We added these inside the main `switch` statement in `quack.c`. Each one takes up 4 bytes in memory, just like the other instructions. We didn't have to change anything else in the computer system to make them work.
