# Types

## Number types

Number types are numeric values.

**numtype**: **i32** | **i64** | **f32** | **f64**


## Vector types

Vector types are vector of numeric values processed by vector instructions.

**vectype**: **v128**

The type **v128** is a 128 bit vector of packed integer or floating-point data.


## Reference types

Reference types are first-class references to objects in the runtime store.

**reftype**: **funcref** | **externref**

As in the wasm spec, **funref** is the union all references to functions, regardless of their function types.

Similarly, **externref** is the infinite union of all references to objects owned by the embedder  and that can be passed into WebAssembly under this type.

## Value types:

Value types are  that Wasm code can with and the values that a variable accepts. 

**valtype**: **numtype** | **vectype** | **reftype**

## Result types: 

Result types is the result of executing instructions or functions which is a sequence of values, written with brackets.

**resulttype** : **[vec(valtype)]**

## Limit Types:

Limit types are the range of storage of memory types and table types

**limit**: \\(\{\\)**min** **u32**, **max** **u32** \\(\}\\)

The value **max** is optional. If there is no **max**, the storage can grow to any size.

## Memory Types:

**memtype**: **limits**

**Note**: The limits here is the optimal number of page size?. 

## Table Types:

Table types classify tables over elements of reference types within a size range. 

**tabletype**: **limits** **reftype**

Like memories, tables are constrained by limits for their minimum and optionally maximum size.

**Note**: It means that the table contains the reference types.

## Global Types: 

Global types classify global variables, which hold a value and can either be mutable or immutable.

**globaltype**: **mut** **valtype**

**mut**: **const** | **var**

## Extrenal Types:

External types classify external or imported values (from libraries of other files). They can be function types, table types, memory types and global types.

**extrentype**: **functype** | **tabletype** | **memtype** | **globaltype**
