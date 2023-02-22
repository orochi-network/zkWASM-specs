# Modules

## Indices 

All types of indices start with zero. Each class of definition has its own index space. These
classes are: **typeidx**, **funcidx**, **tableidx**, **memidx**, **globalidx**, **elemidx**,
**dataidx**, **localidx**, **labelidx**. They are all labeled in **u32**.



## Types

**Note** No explicit definition of type module is specified in Wasm spec.

## Functions

**func**: {**type** **typeidx**, **locals** **vec(valtype)**, **body** **expr**}

The **type** of the function 

The **locals** of the function is a vector of mutable local variables and their types.

The **body** of the function declares a sequence of instructions. Upon termination, it must
produce stack matching the function **type**’s result type.

**Note**: What does the stack contain? The value of the function's
result or the type of the function's result?

## Tables

The table component of a module defines a vector of tables described by their table type:

**table**: {**type** **tabletype**}

## Memory

A memory is a vector of raw uninterpreted bytes.

Memories can be initialized through data segments.

**mem**: {**type** **memtype**}

Memories are referenced through memory indices, starting with the smallest index not referencing a memory import.

**Note**: Memories can be managed through paging. The memtype here is actually the number of pages.

## Globals

The global component is a vector of global variables.

**global**: {**type** **globaltype**, **init** **expr**}

A global variable has a type. It also has an init value which is given by an expression.

## Start Function

The start component declares the function index that is automatically called when the module is instantiated. (For example, the constructor of a class?)

**start**: {**func** **funcidx**}