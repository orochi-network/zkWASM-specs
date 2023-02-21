# Handling Memory Accesses
In this section, we assume that the execution of the program that we are trying to intertwine a proof has accesses to a single memory, represented as an array of fixed-size words. Let \\(M = (m_i)_{i\in \\{0,\dots,\ell-1\\}}\\) be such an array such that each \\(m_i\\) is a word at the \\(i\\)-th location.

We employ the technique from [Constant-Overhead Zero-Knowledge for RAM Programs](https://eprint.iacr.org/2021/979) to argue the correct accesses to the memory, by either reading or writing words. In particular, we enforce the following rule for each location \\(i\\) as follows.
- First access to \\(i\\)-th location must be a WRITE access.
- Any READ access to \\(i\\)-th location must have value equal to the value of previous access, either READ or WRITE.

## Logging Accesses
We now transform the above constraints to more detailed ones that we can apply proof systems on. To this end, for each access to the memory, we log the time tag in some sufficiently small unit of time so that any different accesses have different time tags logged. Hence, we can form the following tuple for each access:
$$
    (\textsf{location}, \textsf{time}, \textsf{value}, \textsf{type})
$$
where \\(\textsf{location}\\) is the location in the memory, \\(\textsf{time}\\) is the time tag, \\(\textsf{value}\\) is the value and \\(\textsf{type}\\) is either READ or WRITE.

## Sorting Accesses
After logging all accesses to the memory, we denote the record of all accesses by the sequence 
$$
    \textsf{AcRec} = \left((\textsf{location} _i, \textsf{time} _i, \textsf{value} _i, \textsf{type} _i)\right) _{i \in \\{0, \dots, t - 1\\}}
$$ for some positive integer \\(t\\).

Then, we sort the above sequence \\(\textsf{AcRec}\\) into the form that, for all accesses having the same location, the time tags are arranged in an increasing order.

## Transforming to Constraints
We now make the constraints regarding the above sorted ordering of sequence of accesses. These constraints guarantee that the sequence is sorted correctly. We describe the constraints as follows:
1. The locations are non-decreasing.
$$
    (i = 0) \vee \left((i > 0) \wedge \left(\textsf{location} _{i - 1} \leq \textsf{location} _i\right)\right).
$$
1. For a specific location, time tags must be increasingly ordered.
$$
    (i = 0) \vee \left((i > 0) \wedge \left(\overline{(\textsf{location} _{i - 1} = \textsf{location} _i) \wedge (\textsf{time} _{i - 1} \geq \textsf{time} _i)}\right)\right).
$$
2. For a specific location, the first access must be WRITE. 
$$
    \left((i = 0) \wedge (\textsf{type}_i = \text{WRITE})\right) \vee \left((i > 0) \wedge \left(\overline{(\textsf{location} _{i - 1}\neq \textsf{location} _i) \wedge (\textsf{type} _i = \text{READ})}\right)\right).
$$
3. For a specific location, any READ access must have value equal to the previous access.
$$
    (i = 0) \vee \left((i > 0) \wedge \left(\overline{(\textsf{location} _{i - 1} = \textsf{location} _i) \wedge (\textsf{type}_i = \text{READ}) \wedge (\textsf{value}_i \neq \textsf{value} _{i - 1})}\right)\right).
$$