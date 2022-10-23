# ECEA_HDLTP 
### HDL - Hardware Definition Language. This is a training course on Verilog. We do learn things and do assignments based on those. 

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
Gatelevel Modelling               |           Dataflow Modelling               |          Behavioural Modelling 
---------------------------------------------------------------------------------------------------------------------------------
Verilog contains primitive gate   | Dataflow modelling means a continuous      | Behavioural modelling uses different statements
types. So we can use gate level   | assignment of outputs through operators.   | like initial, always, case etc.It is used
modelling for basic combinatorial | It is also used in designing combinatorial | to design complex circuits such as Sequential
cicuits.                          | circuits.                                  | circuits and pure Combinatorial circuits.
</pre>

### 2- bit Full Adder with Carry contains 5 inputs and 3 outputs. C0 , A0, B0 and A1, B1 are inputs whereas Cout, S1, S0 are outputs. 
### Gatelevel Modelling of 2-bit full Adder

#### Design file

<img width="305" alt="image" src="https://user-images.githubusercontent.com/100028556/197327628-e398dea2-8b29-4c02-82fd-bad43a240ced.png">

#### Simulation file

<img width="716" alt="image" src="https://user-images.githubusercontent.com/100028556/197327662-5f6f9d21-4639-4f11-b5d1-261124ef320a.png">

#### Schematic

<img width="748" alt="image" src="https://user-images.githubusercontent.com/100028556/197327697-cbe4a4b0-e322-4b1c-89c9-b35bf9ea8a54.png">

#### Output

<img width="740" alt="image" src="https://user-images.githubusercontent.com/100028556/197327736-adab1ebe-b15d-4b6a-9b77-71e04dcde060.png">

### Dataflow Modelling

#### Design File

<img width="238" alt="image" src="https://user-images.githubusercontent.com/100028556/197329977-3472a8e0-09d3-445d-a2ff-4fb723565b3f.png">

#### Simulation File

<img width="698" alt="image" src="https://user-images.githubusercontent.com/100028556/197330055-102724ac-f90e-4db5-90b6-4ac674438bbb.png">

#### Schematic

<img width="745" alt="image" src="https://user-images.githubusercontent.com/100028556/197330093-ffdf6985-5c85-419e-b186-4b63c7d5f6e1.png">

#### Output

<img width="275" alt="image" src="https://user-images.githubusercontent.com/100028556/197330144-a8590a99-d35b-499e-8022-43a332c3c890.png">

### Behavioural Modelling

#### Design File

<img width="353" alt="image" src="https://user-images.githubusercontent.com/100028556/197332536-e28e3d04-7ad9-4e6b-a8a0-1bb9b8e49aed.png">

#### Simulation file

<img width="691" alt="image" src="https://user-images.githubusercontent.com/100028556/197332590-7f409bc2-07dd-4d9e-86e8-d1369d2136ac.png">

#### Schematic

<img width="749" alt="image" src="https://user-images.githubusercontent.com/100028556/197332636-7ee09b06-f168-4045-ac73-5163602c9420.png">

#### Output

<img width="620" alt="image" src="https://user-images.githubusercontent.com/100028556/197332517-e6e46e86-0373-4f7b-ae8d-c81eaed19363.png">

#### End of week 3 assignments

