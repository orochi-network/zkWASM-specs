# Values

## Bytes
Bytes are represented as hexadecimal literals less than 256.

**byte**: \\(0x00\\) | \\(0x01\\) | \\(0x02\\) |... | \\(0xff\\)

**Questions**: Don't we have the **Bit** type?

## Integers
Types of integers are demermined by their bit length \\(b\\) and whether they are signed or unsigned.

**ub**: \\(0\\) | \\(1\\) |...| \\(2^b-1\\)

**sb**: \\(-2^{b-1}\\) |...| \\(-1\\) | \\(0\\) | \\(1\\) |...| \\(2^{b-1}-1\\) 

**ib**: **ub**

The signedness of **ib** depends on context. They are automatically interpreted as unsigned integer. However, some operations convert them into signed integer.

In Wasm, the main types of integers are: **u32**, **u64**, **s32**, **s64**, **i8**, **i16**, **i32**, **i64**. 

## Floating-Points

Floating-point represents 32 or 64 bit values that correspond to the respective binary formats of the IEEE 754-2019 standard.

**fb**: +**fbmag** | -**fbmag**

**fbmag**: \\((1+uM2^{-M}2^e)\\) if \\(-2^{E-1}+2 \leq e \leq 2^{E-1}-1\\)

       \\((0+uM2^{-M}2^e)\\) if \\(e=-2^{E-1}+2\\)

       \\(\inf \\)

       \\(nan(n)\\) if \\(1\leq n \leq 2^M\\)

where \\(M=signif(N)\\) and \\(E=expon(N)\\) with

\\(signif(32)= 23\\)                        \\(expon(32)=8\\)

\\(signif(64)= 52\\)                       \\(expon(64)=11\\)

**Questions**: What is n here? Does it has any relationship to N?

## Vectors

Numeric vectors are 128-bit values that are processed by vector instructions. They are represented in the abstract syntax using i128.

**Question**: The description of vectors are unclear. Does it means that a vector is simply i128, or an array with 128 elements, each elements are integer or float?

## Names

Names are sequences of characters.

**name**: **(char*)** if |utf8(char*)| \\(<2^32\\)

**char**: \\(U+00 |...| U+D7FF | U+E00 |...| U+10FFF\\)

The length of the name is bounded by the length of utf8 encoding.