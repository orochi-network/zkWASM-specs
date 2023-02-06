# Types

## Number types

Number types are numeric values.

numtype: i32 | i64 | f32 | f64

**Questions**: Wasm numeric values also consists of i8, i16. Why don't we have i8 and i16 in number types? 

## Vector types

Vector types are vector of numeric values processed by vector instructions.

vectype: v128

The type v128 is a 128 bit vector of packed integer or floating-point data.

**Questions**: What does bit means here? Is it the size of a vector or something?