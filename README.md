# decomp
A Python 3.9 bytecode decompiler, currently in the making...

# What's a decompiler?
First of all, we should establish what bytecode and OPCODEs are. 
To put it simply, bytecode is just a series of instructions, since Python is interpreted, these instructions are executed within CPythons VM. When you run a Python program, you may sometimes find a \_\_pycache\_\_ folder, in this folder the compiled bytecode is stored as '{filename}.pyc'.

__An example of bytecode instructions:__

By importing the `dis` module and calling `dis.dis("a = 10")`, we get the following output:
```
     (1)     (2)                  (3)  (4)
      0   LOAD_CONST               0   (10)
      2   STORE_NAME               0   (some_var)
```
1. Byte address index within the bytecode, Python 3.6+ uses 2 bytes for each instruction, as such multiples of 2.
2. The instruction __OPCODE__, this tells the internal CPython interpreter what instruction should be carried out.
3. Instruction argument, used to fetch or manage data from the stack along other uses.
4. Human-friendly interpretation of the argument.

The `LOAD_CONST` OPCODE pushes a piece of data onto the stack. In this instance `10`.

The `STORE_NAME` OPCODE stores the data on top-of-the-stack into a variable. In this instance `some_var`.

Resulting in: `some_var = 10`.

However, bytecode is meant for machines, and not humans. As such it is not as readable as the original source code.
This is where a decompiler steps in, a decompiler tries to decompile given Python bytecode into it's original human-readable Python source code.

# Why?
Other python bytecode decompilers such as Pycdc or decompyle3 do not currently support Python 3.9 (alteast not fully).

- [Pycdc](https://github.com/zrax/pycdc) - A decompiler written in C++, it works fine but some OPCODEs are not yet fully implemeneted, I would implement them myself but C++ isn't my thing.
- [decompyle3](https://github.com/rocky/python-decompile3) - A decompiler written in Python, fully supports versions 3.7-3.8, the developer (rocky) is not planning on adding Python 3.9 support.
