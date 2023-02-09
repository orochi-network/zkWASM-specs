# Runtime

## Values

Values can be integers, floating-points data of 32 or 64 bit width each, vectors of 128 bit width or reference types

**value**:   **num** | **vec** | **ref**

**num**:  **i32**.const i32 | **i64**.const i64 |

           **f32**.const f32 | **f64**.const f64

**vec**:  **v128**.const i128

**ref**:  **ref**.null t | **ref** funcaddr | **ref**.extern externaddr

## Result

A result is the outcome of a computation. It can be a sequence of values or a trap.

**result**: **val*** | **trap**

## Address
Function instances, table instances, memory instances, and global instances, element instances, and data instances in the store are referenced with abstract addresses. 

**addr**: 0 | 1 | | 2 | ...

## Memories

**memoryinst** { data **vec(byte)**}

## Globals

A global instance  represents a global variable. It has a type and value of the variable.

**globalinst**: {type **globaltype**, value **val**}