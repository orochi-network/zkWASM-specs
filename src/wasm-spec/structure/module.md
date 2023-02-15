# Modules

## Indices 

All types of indices start with zero. Each class of definition has its own index space

## Types

## Functions

**func**: {**type** **typeidx**, **locals** **vec(valtype)**, **body** **expr**}

The **type** of the function 

The **locals** of the function is a vector of mutable local variables and their types.

The **body** of the function declares a sequence of instructions. Upon termination, it must
produce stack matching the function **type**’s result type.

**Question**: What does the stack contain? The value of the function's
result or the type of the function's result?

## Tables

The table component of a module defines a vector of tables described by their table type:

**table**: {**type** **tabletype**}

## Memory

A memory is a vector of raw uninterpreted bytes.

Memories can be initialized through data segments.

Memories can be managed through paging.

**mem**: {**type** **memtype**}

Memories are referenced through memory indices, starting with the smallest index not referencing a memory import.


## Globals

The global component is a vector of global variables.

**global**: {**type** **globaltype**, **init** **expr**}

A global variable has a type. It also has an init value which is given by an expression.