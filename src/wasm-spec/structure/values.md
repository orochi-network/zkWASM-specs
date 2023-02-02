# Values

## Bytes
Bytes are represented as hexadecimal literals.

byte: \\(0x00\\) | \\(0x01\\) | \\(0x02\\) |... | \\(0xff\\)

## Integers
Integers are demermined by their bit length \\(b\\) and whether they are signed or unsigned.

ub: \\(0\\) | \\(1\\) |...| \\(2^b-1\\)
sb: \\(-2^{b-1}\\) |...| \\(-1\\) | \\(0\\) | \\(1\\) |...| \\(2^{b-1}-1\\) 

In Wasm, the main types of integers are: u32, u64, s32, s64, i8, i16, i32, i64. 

## Floating-Points

Floating-point represents 32 or 64 bit values that correspond to the respective binary formats of the IEEE 754-2019 standard.

fb: +fbmag | -fbmag
fbmag: \\((1+uM2^{-M}2^e)\\) if \\(-2^{E-1}+2 \leq e \leq 2^{E-1}-1\\)
       \\((0+uM2^{-M}2^e)\\) if \\(e=-2^{E-1}+2\\)

## Vectors

## Names

Names are sequences of characters.

name: char* if |utf8(char*)| \\(<2^32\\)
char: 