# Handling Memory Accesses
In this section, we assume that the execution of the program that we are trying to interwine a proof has accesses to a single memory, represented as an array of fixed-size words. Let \\(M = (m_i)_{i\in \\{0,\dots,\ell-1\\}}\\) be such an array such that each \\(m_i\\) is a word at the \\(i\\)-th location.

We employ the technique from [Constant-Overhead Zero-Knowledge for RAM Programs](https://eprint.iacr.org/2021/979) to argue the correct accesses to the memory, by either reading or writing words. In particular, we enforce the following rule for each location \\(i\\) as follows.
- First access to \\(i\\)-th location must be a WRITE access.
- Any READ access to \\(i\\)-th location must have value equal to the value of previous access, either READ or WRITE.