# ECE 281 ICE 3: Ripple-Carry Adder with Top Level Design

## Documentation
C3C Keelie O'Hollaren helped me understand how to draw a proper entity design. She explained in details how to put all of my work from my computer onto an entity design without showing me her design at all.

This is a **template** repository.

[ICE 3 instructions](https://usafa-ece.github.io/ece281-book/ICE/ICE3.html)

Targeted toward Digilent Basys3. Make sure to install the [board files](https://github.com/Xilinx/XilinxBoardStore/tree/2018.2/boards/Digilent/basys3).

Tested on Vivado 2024.2

##Waveform
<img width="750" alt="{163522D9-1979-4567-8592-56CE99BF86B5}" src="https://github.com/user-attachments/assets/8ffa0d46-8621-45e6-bb71-8b3c8a7aed20" />

##Design
<img width="627" alt="{5A3FE007-8DEC-47A2-8148-3ED47E4317C0}" src="https://github.com/user-attachments/assets/da2ea6a3-4a76-4d04-8589-0a49740ec7a9" />



---

## GitHub Actions Testbench

The workflow uses the [setup-ghdl-ci](https://github.com/ghdl/setup-ghdl-ci) GitHub action
to run a *nightly* build of [GHDL](https://ghdl.github.io/ghdl/).

First, the workflow uses GHDL to **analyze** all `.vhd` files in `src/`.

Then it **elaborates** the entity defined by `$TB_ENTITY`

Finally, the workflow **runs** the simulation. If successful then it will quietly exit with a `0` code.
If any of the `assert` statements fail then GHDL will cease the simulation and exit with non-zero code; this will also cause the workflow to fail.
Assert statements of other severity levels will be reported, but not fail the workflow.
