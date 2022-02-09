#  Design and Analysis of Half Adder using Transmission gates

### This repository presents the Design and implementation of Half Adder using transmission gates. Design of Half Adder circuit is done by using an Opensource EDA Tool called eSim, an Opensource Spice Simulator called ngspice and Sky130 PDK.

## Table of Contents
#### 1.[ABSTRACT](https://github.com/abhinandann/Half_Adder/blob/main/README.md#1abstract-1)
#### 2.[eSIM EDA TOOL](https://github.com/abhinandann/Half_Adder/blob/main/README.md#2esim-eda-tool-1) 
#### 3.[Sky130 PDK](https://github.com/abhinandann/Half_Adder/edit/main/README.md#3sky130-pdk)
#### 4.[CIRCUIT DESIGN](https://github.com/abhinandann/Half_Adder/edit/main/README.md#4circuit-design)
#### 5.[IMPLEMENTATION](https://github.com/abhinandann/Half_Adder/edit/main/README.md#5implementation-1)
#### 6.[REFERENCES](https://github.com/abhinandann/Half_Adder/edit/main/README.md#6references-1)
#### 7.[AKNOWLEDGEMENT](https://github.com/abhinandann/Half_Adder/edit/main/README.md#7-aknowledgement)
#### 8.[AUTHOR](https://github.com/abhinandann/Half_Adder/edit/main/README.md#8author-1)

## 1.ABSTRACT

An adder is a digital circuit that performs addition of two binary numbers. Basically, adders are the part of Arithmetic logic unit (ALU), which is the processing part of a CPU. Adders are used, not only in ALU, but also in other parts of processors to calculate addresses, increment, decrement operators and many other similar operations. The main concern is to build half adder which is power efficient, energy efficient and uses less number of transistors. The proposed work shows implementation of Half Adder using Transmission gates.

## 2.eSIM EDA TOOL

eSim is an open source EDA tool for circuit design, simulation and analysis , developed by FOSSEE Team at IIT Bombay. It is an integrated tool build using open source softwares such as KiCad, Ngspice and GHDL.
More details on eSIM tool can be found [here](https://esim.fossee.in/)

## 3.Sky130 PDK

The SkyWater Open Source PDK is a collaboration between Google and SkyWater Technology Foundry to provide a fully open source Process Design Kit and related resources, which can be used to create manufacturable designs at 130nm technology.
The SkyWater Open Source PDK documentation can be found [here](https://skywater-pdk.readthedocs.io/en/main/).Sky130 PDK foundary can be downloaded [here](https://static.fossee.in/esim/installation-files/sky130_fd_pr.zip)
 
 Steps to Sky130 PDK download and Implementaion:

1. Download sky130 PDK files from the above link.
2. Unzip the folder and save the sky130 files in a new folder.
3. Save the .cir.out file in the sky_fd_pr folder as .cir file.
4. Open with notepad and add the path .lib "models/sky130.lib.spice" tt at the top.
5. Replace with CMOSP, mos_p with sky130_fd_pr_pfet_01v8 and CMOSN, mos_n with  sky130_fd_pr_nfet_01v8.

Note: For more details go to the cells folder in sky_fd_pr and follow these steps:
1. Open the specific component folder which you want to use.
2. Open the test folder and check the SPICE file.
3. The SPICE file is an example of implementation of that component.
4. You will get to know how to use the component in your circuit.

Now Run the circuit with ngspice.
To Run the circuit using ngspice follow the below steps
1. Right click on .cir file.
2. Click on Open With.
3. Browse for the ngspice.
4. If ngspice not present scroll down click on More Apps. Go to the FOSSEE folder search for Ngspice and Run it

 ## 4.CIRCUIT DESIGN

Half adder accepts two binary inputs namely A and B and produces the output Sum and Carry. The four possible combinations of two binary digits A and B are ,when A is 0 and B is 0 the Sum and Carry output are 0 respectively. When A is 0 and B is 1 the Sum output is 1, as there is no Carry hence Carry output is 0. When A is 1 and B is 0 we get the same output as of case 2 i.e., Sum =1 and Carry =0. when A is 1 and B is 1, the Sum output is 0 whereas the Carry output is 1.
The 2-bit half adder truth table is as below:
| A | B | SUM | CARRY |
| :---         |     :---:      |          ---: | --: |
| 0   | 0    | 0   |0  |
| 0    | 1      | 1      |0  |
|1     | 0      |1       |0  |
|1      |1      |0       |1  |

Half adder can be easily implemented with the help of the XOR Gate for the output ‘SUM’ and an AND Gate for the ‘CARRY’.
                                                              -Sum= A XOR B
                                                            - Carry = A AND B
These XOR and AND gates are implemented using CMOS transmission gates. CMOS transmission gates consists of one NMOS and one PMOS transistor, connected in parallel. The gate voltages applied to these NMOS and PMOS transistors are set to be complementary signals. As such, CMOS Transmission Gates(TG) operates as a bidirectional switch between the nodes A and B which is controlled by signal C. 

In the reference circuit, half adder is implemented using transmission gate with two inverter circuits. Using CMOS TG logic, we can reduce the number transistors in the circuit implementation as compared to traditional CMOS half adder circuit. 

 ### REFERENCE CIRCUIT
![ref_ckt](https://user-images.githubusercontent.com/91964227/153210846-9f9957a5-493b-42b3-b5b0-225738734291.png)

 
 ### REFERENCE WAVEFORMS
![ref_wavform](https://user-images.githubusercontent.com/91964227/153210895-d5382792-e20f-4fa7-95c9-4dd56324698a.png)

 
## 5.IMPLEMENTATION
Half Adder is implemented using eSIM tool. 

### SCHEMATIC DESIGN
![halfadder_schematic](https://user-images.githubusercontent.com/91964227/153196241-693cbfe1-f21d-41bc-afc6-f9d522cbf6ea.JPG)

### Spice Netlist generated by eSim for the above schematic
[spice netlist_halfadder.txt](https://github.com/abhinandann/Half_Adder/files/8032486/spice.netlist_halfadder.txt)

### Modified Spice Netlist for Half Adder with Sky130 models, here sky130_fd_pr__pfet_01v8 represents P channel mosfet and sky130_fd_pr__nfet_01v8 represents N channel mosfets

[halfadder.txt](https://github.com/abhinandann/Half_Adder/files/8032474/halfadder.txt)

### Spice Simulation results
![spice_simulation](https://user-images.githubusercontent.com/91964227/153198451-07551ecb-bd12-4f2b-9677-6fb4192da79a.JPG)

### Ngspice Waveforms
![halfadder_waveform](https://user-images.githubusercontent.com/91964227/153198612-a202c925-3637-4c43-8954-6adf5f7c8fc0.JPG)

The above waveform can be verified using the truth table given [here](#CIRCUIT DESIGN)

## 6.REFERENCES

-[1]	R. K. (2015). Design of area and power efficient half adder using Transmission Gate. International Journal of Research in Engineering and Technology, 04(04), 122–127. https://doi.org/10.15623/ijret.2015.0404021 
-[2]	Balaji, G. N., V.A., & K.A. (2016). COMBINATIONAL CIRCUITS USING TRANSMISSION GATE LOGIC FOR POWER OPTIMIZATION. International Research Journal of Engineering and Technology (IRJET), 03(05). https://www.irjet.net

## 7. AKNOWLEDGEMENT

[Kunal Ghosh](https://github.com/kunalg123), Co-founder of VLSI System Design (VSD) Corp. Pvt. Ltd.

## 8.AUTHOR

ABHINANDAN R APPANNAVAR, 3rd year B.TECH, ECE, SDM COLLEGE OF ENGINEERING AND TECHNOLOGY,DHARWAD-580002 
-Contact:abhinandan7353@gmail.com
