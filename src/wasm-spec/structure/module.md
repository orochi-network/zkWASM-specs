# Modules

## Indices 

All types of indices start with zero.

## Types

## Memory

A memory is a vector of raw uninterpreted bytes.

Memories can be initialized through data segments.

Memories can be managed through paging.

Memories are referenced through memory indices, starting with the smallest index not referencing a memory import.

## Opcode

## Globals

The global component is a vector of global variables.

global: {type globaltype, init expr}

A global variable has a type. It also has an init value which is given by an expression.