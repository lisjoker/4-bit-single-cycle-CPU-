 In-Order (DINO) CPU models


# Getting the code

To get the code, you can clone the repository that is in jlpteaching: `jlpteaching/dinocpu`.

```
git clone https://github.com/jlpteaching/dinocpu.git
```

## Overview of code

The `src/` directory:

- `main/scala/`
  - `components/`: This contains a number of components that are needed to implement a CPU. You will be filling in some missing pieces to these components in this lab. You can also find all of the interfaces between components defined in this file.
  - `pipelined/`: This is the code for the pipelined CPU. Right now, this is just an empty template. You will implement this in Lab 4.
  - `single-cycle/`: This is the code for the single cycle CPU. Right now, this is just an empty template. You will implement this in Lab 2.
  - `configuration.scala`: Contains a simple class to configure the CPU. **Do not modify.**
  - `elaborate.scala`: Contains a main function to output FIRRTL- and Verilog-based versions of the CPU design. You can use this file by executing `runMain dinocpu.elaborate` in `sbt`. More details below. **Do not modify.**
  - `simulate.scala`: Contains a main function to simulate your CPU design. This simulator is written in Scala using the [Treadle executing engine](https://github.com/freechipsproject/treadle). You can execute the simulator by using `runMain dinocpu.simulate` from sbt. This will allow you to run *real RISC-V binaries* on your CPU design. More detail about this will be given in Lab 2. **Do not modify.**
  - `top.scala`: A simple Chisel file that hooks up the memory to the CPU. **Do not modify.**
- `test/`
  - `java/`: This contains some Gradescope libraries for automated grading. **Feel free to ignore.**
  - `resources/riscv`: Test RISC-V applications that we will use to test your CPU design and that you can use to test your CPU design.
  - `scala/`
    - `components/`: Tests for the CPU components/modules. **You may want to add additional tests here. Feel free to modify, but do not submit!**
    - `cpu-tests/`: Tests the full CPU design. **You may want to add additional tests here in future labs. Feel free to modify, but do not submit!**
    - `grading/`: The tests that will be run on Gradescope. Note: these won't work unless you are running inside the Gradescope docker container. They should match the tests in `components` and `cpu-tests`. **Do not modify.** (You *can* modify, but it will be ignored when uploading to Gradescope.)

The `documentation` directory contains some documentation on [the design of the DINO CPU](documentation/overview.md) as well as an [introduction to the Chisel constructs required for the DINO CPU](documentation/chisel-notes/overview.md).

# How to run

First you should set up the [Singularity container](documentation/singularity.md) or follow the [documentation for installing Chisel](https://github.com/freechipsproject/chisel3#installation).

There are three primary ways to interact with the DINO CPU code.
1. [Running the DINO CPU tests.](documentation/testing.md)
2. [Running the DINO CPU simulator.](documentation/single-stepping.md)
3. Compiling the Chisel hardware description code into Verilog.

## Compiling into Verilog

To compile your Chisel design into Verilog, you can run the `elaborate` main function and pass a parameter for which design you want to compile.
As an example:

```
sbt:dinocpu> runMain dinocpu.elaborate single-cycle
```
The generated verilog will be available in the root folder as `Top.v` along with some meta-data. You may also get some generated verilog for auxillary devices like memory as `Top.<device_name>.v`

# Compiling code for DINO CPU

See [Compiling code to run on DINO CPU](documentation/compiling.md) for details on how to [compile baremetal RISC-V programs](documentation/compiling.md#Getting-baremetal-programs-working) and [compile full C applications](documentation/compiling.md#Compiling-C-programs).

# Documentation for Teachers

- [Creating the code templates](documentation/teaching/template.md)
- [Setting up grading on Gradescope](documentation/teaching/grading.md)
- [Updating the Singularity container](documentation/teaching/singularity.md)
