# Vartika_Tapeout_Process

This Github Repository demonstrates the procedures and steps which is being followed during the Tapeout Process.


# Tapeout Process
# WEEK 1
# Day 0
<details>
  <summary>
    Yosys
  </summary>
  I installed Yosys using the following commands:

```
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys-master 
$ sudo apt install make (If make is not installed please install it) 
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ make 
$ sudo make install

```
Below is the screenshot showing successful installation:
![Screenshot from 2023-07-31 10-50-46](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/5ab5283b-be3e-4487-b8ac-01fb86b8d2b5)


Below is the Screenshot showing successful Launch:
![Screenshot from 2023-07-31 10-50-55](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/e48b05c6-c712-4b20-b8ca-6b21b25bf48c)


</details>

<details>
  <summary>
  iverilog
  </summary>
  I installed iverilog using the following comment

  
  ```

sudo apt-get install iverilog

  ```
![Screenshot from 2023-08-02 08-28-38](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/85790984-eac7-47e0-81a3-46f3e56ca363)

</details>

<details>
  <summary>
    gtkwave
  </summary>
    I installed gtkwave using the following command:
    

    ```
    
    sudo apt-get install gtkwave
    

    
    ```
    
  ![Screenshot from 2023-08-02 08-29-09](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/13b0a958-feba-4a17-90f9-45343e05da84)

    
  
</details>

# WEEK 2

# Day 1: Introduction to Icarus Verilog and Yosys
<details>
  <summary>
    Introduction to iverilog
  </summary>

  
  Icarus Verilog is an implementation of the Verilog hardware description language compiler that generates netlists in the desired format (EDIF). It supports the 1995, 2001 and 2005 versions of the standard, portions of SystemVerilog, and some extensions.Verilog Test benches are used to simulate and analyze designs without the need for any physical hardware or any hardware device. The most significant advantage of this is that you can inspect every signal /variable (reg, wire in Verilog) in the design.
  
  Following Screenshot shows the correct Mapping of simulation flow in iverilog:
![Screenshot from 2023-08-11 16-07-16](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/3a9cf4f3-e46a-4fa8-b539-74ae266af316)


Command to view the total number of folders present inside the directory.

```
cd verilog_files
ls -l

```

![Screenshot from 2023-08-14 11-09-45](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/5a1f3d7b-d181-407b-bd5f-e9eb96c1d077)

  # Demonstration of Icarus verilog and Gtkwave

  To run the iverilog command and for simulationg the RTL design and the Test Bench we use the following command.
  
```
  iverilog good_mux.v tb_good_mux.v
  ls -l

```
For getting the output, the following command is used:
```
./a.out

```
Command for viewing and analyzing the waveform:

```
gtkwave tb_good_mux.vcd

```
![Screenshot from 2023-08-14 11-30-52](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/18802ea8-70f2-4212-89f8-f12b192a9286)

</details>

<details>
<summary>
  Introduction to Yosys
</summary>

# Synthesizer
RTL synthesizer primary responsibility is to convert the code into the gate-level netlist. This is a automated process; a tool has all the standard libraries definitions that can manipulate the respective gate-level netlist, which is an equivalent of your design in RTL. Synthesize tools can also do circuit optimization, power estimation, as well as timing analysis. Here we will use YOSYS as a synthesizer.

The following Screenshot shows the flow of the synthesizer.

![Screenshot from 2023-08-14 12-15-06](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/07165fb6-9a00-4deb-828c-aa63bdbd17c6)
![Screenshot from 2023-08-14 12-15-17](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/f09a9174-8f89-4ff7-8cf3-89f7274fa90a)

# .lib
It is a collection of logical modules which includes basic logic gates like AND, OR, NOT etc. It may contain different flavours of the same gate such as 2 input, 3 input and gate with different speed i.e., ranging from slow to fast.
So based on our requirement we use different flavours of cell.

a) Faster the cells lesser is the delay, but for that we need wider transistors so the power dissipation will be more too.So faster cells donot come free,they come at penalty of area and power.More use of faster cell will result in bad circuit with large area and power dissipation.

b) slower cells are used at non-critical path where we donot require high performance where delay is not an issue so our power dissipation and area will also be minimum. But more use of slower cells will make our circuit sluggish.

# Synthesis
synthesis is used for converting the RTL level design to gate level design. The design are converted into gates and the connections are made between the gates and hence this file is gaiven out as a file called Netlist.

Following flow graph shows the path of converting RTL design into its respective netlist:

![Screenshot from 2023-08-14 23-05-40](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/01226908-488c-4b7d-927a-437e3a21f283)


Command
change the working directory in which we have all the verilog files and invoke yosys using the following command

```

cd /vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files
vartika@vartika:~/vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files$ yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> read_verilog good_mux.v
yosys> synth -top good_mux

```
After executing this, we will get the following output:

![Screenshot from 2023-08-14 22-53-35](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/2d8ea14a-5838-4789-86e9-3f0034b0b070)

For generating the Netlist we use the following command:

Command

```

yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show

```
Following command is used for writing the netlist and viewing it:
```

yosys> write_verilog -noattr good_mux_netlist.v
yosys> !gvim good_mux_netlist.v

```
![Screenshot from 2023-08-14 22-57-41](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/31da9143-8e89-4876-ae61-bf15773c7352)

</details>

# Day 2 - Timing Labs, hierarchical vs Flat synthesis and efficient flop coding styles

<details>
  <summary>
    Introduction to Timing.libs
  </summary>
  This lab teaches us how does .lib looks like and the information that it contains within it.
  
![WhatsApp Image 2023-08-15 at 01 33 17](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/fbfd4a95-0536-409d-8957-c2d1961c42af)

In the following example, inside the Lib file there are 2^5 (32) possible combinations are present which shows all the respective values of voltage, Temperature etc.


  ![Screenshot from 2023-08-15 01-50-24](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/e6da3594-87c3-4e51-9e22-12505bf85ec5)
  

  Here as we can see from the screenshot given below that as we move from left towards right the Area is increasing. This means that we need much wider transistors to use over there. Although wider cells are going to be faster when compared to the small cell but it's power consumption is going to be more but on the contrary it's delay is going to be less.

  ![Screenshot from 2023-08-15 01-56-57](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/32736181-e631-4c10-b811-7365e16c673e)


</details>

<details>
<summary>
  Hierarchical vs Flat synthesis
</summary>
  
</details>

<details>
<summary>
  Various flop coding styles and optimizations
</summary>
  
</details>

# Day 3 - Combinational and Sequential Optimizations

<details>
  <summary>
    Introduction to Optimizations
  </summary>
</details>

<details>
<summary>
  Combinational Logic Optimizations
</summary>
  
</details>

<details>
<summary>
   Sequential Logic Optimizations
</summary>
  
</details>

<details>
<summary>
  Sequential Optimizations for unused Outputs
</summary>
  
</details>

# Day 4 - GLS, Blocking vs Non Blocking and synthesis simulation mismatch

<details>
  <summary>
    GLS, synthesis simulation mismatch and blocking/ nonblocking statements
  </summary>
</details>

<details>
<summary>
  Labs on GLS, synthesis simulation mismatch
</summary>
  
</details>

<details>
<summary>
   Labs on Synthesis mismatch for blocking statement
</summary>
  
</details>

# Day 5 - If, case, for loop and for generate

<details>
  <summary>
    If case constructs
  </summary>
</details>

<details>
<summary>
  Labs on Incomplete overlapping case
</summary>
  
</details>

<details>
<summary>
   Labs on "for loop and ""for generate"
</summary>
  
</details>

# References

<summary>
https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop
  
https://github.com/YosysHQ/yosys.git

https://www.vsdiat.com/
</summary>



