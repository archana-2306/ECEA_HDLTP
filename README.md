# ECEA_HDLTP
## Week 1
#### Vivado installed & Full adder

![Screenshot (109)](https://user-images.githubusercontent.com/100028556/195990023-3f0eb63c-9846-42ed-9e5b-2c05e1c3014e.png)

#### Input and Output

![HDL week1](https://user-images.githubusercontent.com/100028556/195991108-f5493a5f-0c7a-4e63-8468-dbcf75f05865.jpeg)

#### RTL Design

![HDL week1 (2)](https://user-images.githubusercontent.com/100028556/195991071-2757292c-bf7a-4a9f-aa92-531f1ac982f2.jpeg)

## Week 2
#### Learned the syntax and done program for 2-bit full adder
##### Syntax is basically like C program. It is case sensitive and we can use only small letters for variable declaration. Starting of the variable holder should not be numbers are special characters.
##### To pass the arguments we use . operator here. Like C it has its own precedence in the usage of operators where braces and parenthesis are at top priority followed by logical negotion and negotion and resuction operators.

#### Design file of two bit full adder

![Screenshot (113)](https://user-images.githubusercontent.com/100028556/195990214-144f3b76-f03d-4f95-831c-e272310698ad.png)

#### Simulation file or Testbench file

![Screenshot (114)](https://user-images.githubusercontent.com/100028556/195990223-57182687-2338-40bf-8f92-b6d1766d9b07.png)

#### RTL Design

![Screenshot (111)](https://user-images.githubusercontent.com/100028556/195990249-96a605ed-9159-4076-b8ce-34d3c6b447e6.png)

#### Input and Output values

<img width="307" alt="image" src="https://user-images.githubusercontent.com/100028556/195990297-99f31fe8-34b6-4cb3-a098-abd45a8def1d.png">

## WEEK 3

### Modelling types 

<pre>
Gatelevel Modelling                    |           Dataflow Modelling                   |          Behavioural Modelling 
------------------------------------------------------------------------------------------------------------------------------------------------
Verilog contains primitive gate        |    Dataflow modelling means a continuous       |   Behavioural modelling uses different
types. So we can use gate level        |    assignment of outputs through operators.    |   statements like initial, always, case etc.
modelling for basic combinatorial      |    It is also used in designing combinatorial  |   It is used to design complex circuits such as 
cicuits.                               |   circuits.                                    |   Sequential circuits and pure Combinatorial circuits.
</pre>

### 2- bit Full Adder with Carry contains 5 inputs and 3 outputs. C0 , A0, B0 and A1, B1 are inputs whereas Cout, S1, S0 are outputs. 
### Gatelevel Modelling of 2-bit full Adder

### Design file

<img width="305" alt="image" src="https://user-images.githubusercontent.com/100028556/197327628-e398dea2-8b29-4c02-82fd-bad43a240ced.png">

### Simulation file

<img width="716" alt="image" src="https://user-images.githubusercontent.com/100028556/197327662-5f6f9d21-4639-4f11-b5d1-261124ef320a.png">

### Schematic

<img width="748" alt="image" src="https://user-images.githubusercontent.com/100028556/197327697-cbe4a4b0-e322-4b1c-89c9-b35bf9ea8a54.png">

### Output

<img width="740" alt="image" src="https://user-images.githubusercontent.com/100028556/197327736-adab1ebe-b15d-4b6a-9b77-71e04dcde060.png">


