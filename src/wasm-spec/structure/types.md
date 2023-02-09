# Types

## Number types

Number types are numeric values.

**numtype**: **i32** | **i64** | **f32** | **f64**

**Questions**: Wasm numeric values also consists of **i8**, **i16**. Why don't we have **i8** and **i16** in number types? 

## Vector types

Vector types are vector of numeric values processed by vector instructions.

**vectype**: **v128**

The type **v128** is a 128 bit vector of packed integer or floating-point data.

**Questions**: What does bit means here? Is it the size of a vector or something?

## Reference types

Reference types are first-class (**what does this mean?**) references to objects in the runtime store.

**reftype**: **funcref** | **externref**

As in the wasm spec, **funref** is the union all references to functions, regardless of their function types.

Similarly, **externref** is the infinite union of all references to objects owned by the embedder (**what does embedder mean?**) and that can be passed into WebAssembly under this type.

## Value types:

Value types are  that Wasm code can with and the values that a variable accepts. 

**valtype**: **numtype** | **vectype** | **reftype**

## Result types: 

Result types is the result of executing instructions or functions which is a sequence of values, written with brackets.

**resulttype** : **[vec(valtype)]**

## Global Types: 

**globaltype**: **mut** **valtype**
**mut**: const | var

