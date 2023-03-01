# Instructions

## Numeric instructions

Numeric instructions provide basic operations over numeric values of specific type. 
The list of numeric instructions can be found in {{#cite Wasm}}. 

**Note**: For integer types, some instructions (those with _**sx** in the tail) distinguish
whether the operands are interprted as signed or unsigned integers. 

## Vector instructions

Vector instructions (also known as SIMD instructions, single instruction multiple data) provide basic operations over values of vector type. The list of vector instructions can be found in {{#cite Wasm}}. 

## Variable instructions

Variable instructions are used to access variables

**instr**: **local**.**get** **localidx**|
            **local**.**set** **localidx**|
            **local**.**tee** **localidx**|
            **global**.**get** **localidx**|
            **global**.**set** **localidx**

**Note**: **local**.**tee** is similar to **local**.**set** but it also returns the argument.

## Parametric Instructuion

## Expression

Expressions are sequences or instructions, then terminated be an **end** marker.

**expr**: **(instr*)** **end**

