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
  
# Hierarchical Synthesis

A hierarchical design approach divides the ASIC into smaller and simpler modules or blocks, each with its own functionality and interface, and then connects them by a top-level structure that defines the overall behavior and performance of the ASIC. Since pins of submodules are accessible, it's easier to track paths for functional debugging and timing analysis. Pins can be forced or probed in post-synthesis simulations.

Multiple module

  ![Screenshot from 2023-08-15 16-34-42](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/63a8a571-e764-45eb-b799-4aa82820f168)

The internal connections of the above module is represented as:
![WhatsApp Image 2023-08-15 at 16 26 59](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/44e96bc9-c59d-45b4-b5ca-06078ffcf9d0)

The yosys synthesizer represented the following schematic in the following way:
![Screenshot from 2023-08-15 16-47-10](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/bcf594f7-33ca-4ca6-95a1-eb945fe299ec)


![Screenshot from 2023-08-15 16-49-31](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/83922884-6165-4a67-ad02-9605995e7fa6)

The hierarchical netlist code for the multiple_modules is shown below:
![Screenshot from 2023-08-15 17-23-07](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/5daa25f3-ad15-4a8a-8005-8149a3f477f3)

# Flattened Netlist

In a "flat" design, only primitives are instanced. Hierarchical designs can be recursively "exploded" ("flattened") by creating a new copy (with a new name) of each definition each time it is used. If the design is highly folded, expanding it like this will result in a much larger netlist database, but preserves the hierarchy dependencies. Given a hierarchical netlist, the list of instance names in a path from the root definition to a primitive instance specifies the single unique path to that primitive.
Command to flatten the netlist is given below:

```
flatten
write_verilog multiple_modules_flat.v
!gvim multiple_modules_flat.v

```
![Screenshot from 2023-08-15 18-42-30](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/ea265189-8746-4c80-b4d1-d51694595b33)

Command for getting the synthesized netlist is given below:
```
flatten
write_verilog -noattr multiple_modules_flat.v
!gvim multiple_modules_flat.v

```

This is the flattened Netlist which is being shown below:
![Screenshot from 2023-08-15 18-46-50](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/d83a3d95-095c-419d-91f0-a7dfa0c4871c)


</details>

<details>
<summary>
  Various flop coding styles and optimizations
</summary>

# Why Flops?

  Flip flops are the fundamental blocks of most sequential circuits. It is also known as a bistable multivibrator or a binary or one-bit memory. Flip-flops are used as memory elements in sequential circuit. The output is obtained in a sequential circuit from combinational circuit or flip-flop or both.
  In digital circuits every component has a propagation delay which can cause *Glitch* so to avoid that delay we use flops to store the value.
  
  # Glitch
  In electronics design, glitch refers to unnecessary signal transitions in a combinational circuit, while glitch power refers to the power consumed by glitches. The extra switching activity can lead to up to 40% of additional dynamic power consumption.

   ![WhatsApp Image 2023-08-15 at 19 13 14](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/9fadb789-c0fb-4dd7-804d-24675f9814a6)
  
1. Asynchronous reset
 ```  
module dff_asyncres ( input clk ,  input async_reset , input d , output reg q );
always @ (posedge clk , posedge async_reset)
begin
	if(async_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```

The Following fig. shows the Simulation of Asynchronous reset.
![Screenshot from 2023-08-15 20-07-37](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/7fa5d391-ba79-4b40-be98-8ee0b3465912)




2. Synchronous Reset

```
module dff_syncres ( input clk , input async_reset , input sync_reset , input d , output reg q );
always @ (posedge clk )
begin
	if (sync_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```

The Following fig. shows the Simulation of Synchronous reset:
![Screenshot from 2023-08-15 20-10-36](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/c7f3089c-eb9a-44ea-aae0-8e04ed929d42)


It's netlist is shown below:

![Screenshot from 2023-08-15 20-12-24](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/9c71d65f-70fc-4be7-beb8-eeca50dfa66c)

</details>

# Day 3 - Combinational and Sequential Optimizations


<details>
<summary>
  Combinational Logic Optimizations
</summary>
 Example 1:

 ```
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule
```
Synthesis

![Screenshot from 2023-08-15 21-27-49](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/e428fa58-b9c1-4cd2-8d59-1abdf908bdbe)

![WhatsApp Image 2023-08-15 at 21 31 23](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/7005b0d6-9aa3-49b9-9e26-e34d8968ce35)

Example 2:

```
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```
![Screenshot from 2023-08-15 21-33-46](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/42a8245a-99d8-4b08-96a6-b823aa6cc5c3)

Example 3:
```
module opt_check3 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```
![Screenshot from 2023-08-15 21-34-40](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/6578e09d-8bc3-4ced-8dec-5241bf4c71a1)

</details>

<details>
<summary>
   Sequential Logic Optimizations
</summary>
	
  Example 1:
  
  ```
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end
endmodule
```

![Screenshot from 2023-08-15 21-36-57](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/7e6234e6-3561-408d-a7b7-b47052298513)

Example 2:

```
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule
```
![Screenshot from 2023-08-15 21-40-53](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/1f84b728-b6e6-40da-94b3-f66e2de9256d)

Example 3:

```
module dff_const5(input clk, input reset, output reg q);
reg q1;
always @(posedge clk, posedge reset)
	begin
		if(reset)
		begin
			q <= 1'b0;
			q1 <= 1'b0;
		end
	else
		begin
			q1 <= 1'b1;
			q <= q1;
		end
	end
endmodule
```
![Screenshot from 2023-08-15 21-42-34](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/0431713f-6fff-4827-b574-4e797fdfd6d4)

Example 4:

```
	module dff_const4(input clk, input reset, output reg q);
	reg q1;

	always @(posedge clk, posedge reset)
	begin
		if(reset)
		begin
			q <= 1'b1;
			q1 <= 1'b1;
		end
	else
		begin
			q1 <= 1'b1;
			q <= q1;
		end
	end
	endmodule
```
![Screenshot from 2023-08-15 21-45-45](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/89126c61-0537-4ed2-a187-e99fc7e7b928)

</details>


# Day 4 - GLS, Blocking vs Non Blocking and synthesis simulation mismatch

<details>
  <summary>
    GLS, synthesis simulation mismatch and blocking/ nonblocking statements
  </summary>
What is GLS?
Gate Level Synthesis is used for running the test bench with netlist as design under test. It is logically same as HIL Code. It uses the same test bench that will align with the design.

 Why GLS?
 1. It verifies the Logical correctness of design after synthesis.
 2. It Ensures the timimng of the design is being met.
 3. GLS should be run with design annotation.

    Following figure shows the correct path of the GLS design:
![Screenshot from 2023-08-15 21-59-22](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/9901a307-d5f3-4ee9-a72b-ff00b1da4a7e)

    
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



