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

# Synthesizer
RTL synthesizer primary responsibility is to convert the code into the gate-level netlist. This is a automated process; a tool has all the standard libraries definitions that can manipulate the respective gate-level netlist, which is an equivalent of your design in RTL. Synthesize tools can also do circuit optimization, power estimation, as well as timing analysis. Here we will use YOSYS as a synthesizer.

The following Screenshot shows the flow of the synthesizer.

![Screenshot from 2023-08-14 12-15-06](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/07165fb6-9a00-4deb-828c-aa63bdbd17c6)
![Screenshot from 2023-08-14 12-15-17](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/f09a9174-8f89-4ff7-8cf3-89f7274fa90a)

# .lib
It is a collection of logical modules which includes basic logic gates like AND, OR, NOT etc. It may contain different flavours of the same gate such as 2 input, 3 input and gate with different speed i.e., ranging from slow to fast.
So based on our requirement we use different flavours of cell.

a) Faster the cells lesser is the delay, but for that we need wider transistors so the power dissipation will be more too.So faster cells donot come free,they come at penalty of area and power.More use of faster cell will result in bad circuit with large area and power dissipation.

b) slower cells are used at non-critical path where we donot require high performance where delay is not an issue so our power dissipation and area will also be minimum. But more use of slower cells will make our circuit sluggish

# Synthesis
synthesis is used for converting the RTL level design to gate level design. The design are converted into gates and the connections are made between the gates and hence this file is gaiven out as a file called Netlist.

Following flow graph shows the path of converting RTL design into its respective netlist:

![Screenshot from 2023-08-14 23-05-40](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/01226908-488c-4b7d-927a-437e3a21f283)

</details>
