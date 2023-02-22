# Types

Most types are automatically valid. However, there are several restrictions to Limits, Block Type, Table Types, Memory Types.

## Limits

Trivially we must have \\(**limits**.**min** \leq **limits**.**max**\\). In addition, depend on different types (table, memory,...), we have a \\(k\\) such that:

1. \\(**limits**.**min** \leq k\\).

1. If \\(**limits**.**max**\\) is not empty, then \\(**limits**.**max** \leq k\\).

We say that the limit is valid within range \\(k\\). As in, the limit condition is formally expressed as follow:

\\(**limits**.**min** \leq k\\).   \\((**limits**.**max** \leq k)^{?}\\).    \\((**limits**.**min** \leq **limits**.**max**)^{?}\\). 

**limits**:k


## Block Types

## Function Types

The function types are always valid.

## Table Types

The limit of table type must be valid within range \\(2^{32}-1\\).

**tabletype**.**limits**:2^{32}


## Memory Types

The limit of memory type must be valid within range \\(2^{16}\\).

**memtype**.**limits**:2^{16}


## Global Types

The global type is always valid.

## External Types

**table** **tabletype**: The table type **tabletype** must be valid.

**mem**  **memtype**: The memory type **memtype** must be valid.

**func** **functype**: The function type **functype** must be valid.
