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
cd sky130RTLDesignAndSynthesisWorkshop
ls -l

```

![Screenshot from 2023-08-14 11-09-45](https://github.com/Vartika-iiitb/Vartika_ASIC/assets/140998716/5a1f3d7b-d181-407b-bd5f-e9eb96c1d077)
  
</details>
