# Runtime

## Values

Values can be integers, floating-points data of 32 or 64 bit width each, vectors of 128 bit width or reference types.

**value**:   **num** | **vec** | **ref**

**num**:  **i32**.**const** **i32** | **i64**.**const** **i64** |

          **f32**.**const** **f32** | **f64**.**const** **f64**

**vec**:  **v128**.**const** **i128**

**ref**:  **ref**.**null** **t** | **ref** **funcaddr** | **ref**.**extern** **externaddr**

## Result

A result is the outcome of a computation. It can be a sequence of values or a trap.

**result**: **(val*)** | **trap**

## Address
Function instances, table instances, memory instances, and global instances, element instances, and data instances in the store are **referenced** with abstract addresses. 

**addr**: 0 | 1 | | 2 | ...

**Note** Currently, the address space is **u32**. There is a proposal to extend the address space to **u64**. 

**Note** Addresses are dynamic, while indices are static.

## Memories

It record its type and holds a vector of bytes.

**memoryinst** {**type** **memtype**, **data** **vec(byte)**}

**Note** The length of the vector is a multiple of a page size. The default page size is 65536.
This means the limit can be view as |len(**vec**)|/65536, right?

## Globals

A global instance  represents a global variable. It has a type and value of the variable.

**globalinst**: {type **globaltype**, value **val**}

## Data Instances

Data instance represents a data segment. It has a vector of bytes.

**datainst**: {**data** **vec(byte)**}

## External Values

It is an address of a function instance, memory instance, table instance or global instance in the store.

**externval**: **func** **funcadrr** |
                **mem** **memadrr** |
                **table** **tableadrr** |
                **global** **globaladrr**

## Stack

Most instructions interacts with a stack. The stack store the following:

**Values**: Operand of instructions.

**Labels**: The label of structured control instructions. Each label has a an index n and a list of instructions when we reaches this label.

**labels**: **label_n{instr*}**

**Call Frame**: The call frames of active function calls. It contains all the local values and a reference to the function's module instance.

**frame**: {**local** **(val*)**, **module** **moduleinst**}

**Note**: Should we add a depth attribute to the call frame?