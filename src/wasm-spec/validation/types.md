# Types

Most types are automatically valid. However, there are several restrictions to Limits, Block Type, Table Types, Memory Types.

## Limits


Trivially we must have \\(n \leq m\\). In addition, depend on different types (table, memory,...), we have a \\(k\\) such that:

1. \\(n \leq k\\).

1. If \\(m\\) is not empty, then \\(m \leq k\\).

We say that the limit is valid within range \\(k\\). 

## Block Types

## Table Types

The limit must be valid within range \\(2^{32}-1\\).

## Memory Types

The limit must be valid within range \\(2^{16}\\).