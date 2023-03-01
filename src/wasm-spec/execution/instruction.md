# Instructions

## Numeric instructions

t.**const**\\(c\\)

1. Push \\(c\\) to the stack

t.**unop** ()

1. Check if the stack is not empty (?)

1. Pop the top value \\(c_1\\) from the stack

1. If **unop**(\\(c_1\\)) is defined, then push the result \\(c\\) to the stack.

1. Otherwise, trap.

t.**binop** (add | sub | mul | div | min | max)

1. Check if there are at least two elements in the stack (?)

1. Pop the two top values \\(c_1\\) and \\(c2\\) from the stack

1. If **unop**(\\(c_1,c_2\\)) is defined, then push the result \\(c\\) to the stack.

1. Otherwise, trap.

t.**testop** (eqz)

This can be done exactly as t.**unop**

t.**relop** (eq, le, ge, lt, gt, ne)

This can be done exactly as t.**binop**

## Vector instructions

**ref.null** \\(t\\)

1. Push \\(t\\) to the stack.

**ref.is_null**

1. Check if a reference value is at the top of the stack.

1. Pop the reference value **val** from the stack.

1. If **val**==**null**, push **i32.const** 1 to the stack,
otherwise push **i32.const** 0 to the stack.

**ref.func** \\(x\\)

1. Let F be the current calling frame. Remember that F contains the function's module instance **module**.

1. Let \\(a\\) be the address of F.**module**.**funcadrr**[x].

1. Push \\(a\\) to the stack.

## Vector instructions

**v128.const** \\(c\\)

1. Push \\(c\\) to the stack.

**v128.vvunop**  (not)

This can be done exactly as t.**unop**

**v128.vvbinop** (and, andnot, xor, or)

This can be done exactly as t.**binop**

**v128.any_true**

1. Pop the value \\(c_1\\) from the stack.

1.  Let \\(i= **bool** (c_1==0)\\). Push \\(i\\) to the stack.

**Note**: What exacly does **any_true** do? 

## Parametric Instructions

**drop**

1. Check if the stack is not empty (?)

1. Pop the top element from the stack

**select**(\\(t*\\))

**Note** This instruction "grabs" two values **val_1** and **val_2** from the stack and choose
one of them.

1. Pop the value **i32** \\(c\\) from the stack.

1. Pop the value **val_1** from the stack.

1. Pop the value **val_2** from the stack.

1. If \\(c=0\\), push **val_1** to the stack, otherwise pop **val_2** to the stack.

**Note**: Wasm may allow to select more than one values in the future.

## Variable Instructions

**local.get** \\(x\\)

1. Let F be the current frame.

1. Let **val** be the value of F.**locals**[x]

1. Push **val** to the stack.

**local.set** \\(x\\)

1. Let F be the current frame.

1. Pop the value **val** from the stack.

1. Replace the value F.**locals**[x] with **val**.

**local.tee** \\(x\\)

1. Pop the value **val** from the stack.

1. Push the value **val** from the stack. Do this two times.

1. Execute **local.set** \\(x\\). **Note**: After this, the value **val** is on the top
of the stack and is ready to be returned.


## Memory instructions

t.**load memarg** and t.**loadN_sxmemarg**

1. Let F be the current frame.

1. Let \\(a\\) be the memory address of F.**module**.**memaddrs**[0]

1. Let **mem** be the memory instance S.**mems**[a]

1. Pop the value **i32.const** \\(i\\) from the stack.

1. Let e be the integer \\(i+\\)**memarg.offset**.    (I don't quite get this.)

1. If \\(e+N/8\\) is larger than the length of mem.**data**, then trap. (What does this mean?)