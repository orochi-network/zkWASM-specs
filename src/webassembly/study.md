## Study from manuscript

Reading this [manuscript](https://jhc.sjtu.edu.cn/~hongfeifu/manuscriptb.pdf) give us a starting point to design our own zkWASM.

We consider Wasm run-time as a state machine:

### Input data of Wasm run-time

- Wasm run-time will be init with a input tuple: \\((I(C, H), E, IO)\\)
  - \\(I\\): Wasm executable image
    - \\(C\\): Code image (code image is a read only memory section)
    - \\(H\\): Initial memory (what's kind of the initial memory? is it a stack and can be popped by `local.get`?)
  - \\(E\\): Entrypoint of the program (the initial state will has `iaddr = E`)
  - \\(IO\\): Represent as `stdin` and `stdout`

In the manuscript they supposed that, zk-SNARK circuit will take the whole input tuple and prove the result of `stdout`.

**Note**:

- In the manuscript they don't mention about block devices
- Do we need data encoding for `stdin`?
- `stdout` can be simulate as a write only memory, where the `data_ptr` increase 1 for every byte of data
- Could we use [WASI](https://wasi.dev/) to replace `stdin` and `stdout`?
- Wasm spec still updating we should aware of version diff

### Internal state of Wasm run-time

Denote \\(S\\) is state of Wasm run-time, it's a tuple: \\((𝑖𝑎𝑑𝑑𝑟, F,M, G, SP, I, IO)\\)

- \\(𝑖𝑎𝑑𝑑𝑟\\): current address of instruction in memory (\\(𝑖𝑎𝑑𝑑𝑟 = E\\) at the beginning, 𝑖𝑎𝑑𝑑𝑟 is not program count `PC`)
- \\(F\\): Calling frame with a `depth` field (is it a stack?)
- \\(M\\): Memory state
- \\(G\\): Global variables
- \\(SP\\): Stack
- \\(I\\): Wasm executable image
  - \\(C\\): Code image (𝑖𝑎𝑑𝑑𝑟 can't point to a address outside the code image)
  - \\(H\\): Initial memory
- \\(IO\\): Represent as `stdin` and `stdout`

Here are steps of the execution:

- **Step 1**: Take the internal state \\(S_i\\) as the input (At the initial state, \\(S_i\.\text{𝑖𝑎𝑑𝑑𝑟} = E\\)).
- **Step 2**: Execute the opcode at current 𝑖𝑎𝑑𝑑𝑟 over \\(S\_{i}\\)
  to compute the next state \\(S\_{i+1}\\).
  We called this is a execution trace \\(t_i\\)
- **Step 3**: If calling frame's depth isn't zero then repeat `Step 1`, otherwise stop.

After we complete the computation, we have:

- \\([t_0, t_1,..t_n]\\): Execution trace of the program
- \\(O\\): The result of program in `stdout`

**Note**:

- We need to implement execution trace computation for every WebAssembly opcode
