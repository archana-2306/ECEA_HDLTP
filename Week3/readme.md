###  This is the third week of HDL trainig program
### Types of Modelling

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

<pre>
module gate_level_2bitfa1(
    input A0, input A1, input B0, input B1, input C0,
    output S0, output S1, output Cout
    );
    wire x1,x2,x3,x4,x5,x6,x7;
    //least significant bit
    xor (x1,A0,B0);
    and (x2,x1,C0);
    and (x3,A0,B0);
    xor (S0,x1,C0);
    or (x4,x2,x3);
    //upcoming bit
    xor (x5,A1,B1);
    and (x6,x4,x5);
    and (x7,A1,B1);
    xor (S1,x5,x4);
    or (Cout,x6,x7);
endmodule
</pre>

#### TestBench file

<pre>
module gate_level_2bitfa_tb;
    reg A0,A1,B0,B1,C0;
    wire S0,S1,Cout;
    
    gate_level_2bitfa1 inst0(.A0(A0),.A1(A1),.B0(B0),.B1(B1),.C0(C0),.S0(S0),.S1(S1),.Cout(Cout));
    initial begin $dumpfile("gate_level_2bitfa1.vcd"); $dumpvars(); end
    initial begin 
      A0 = 1; B0 = 1; C0 = 1; A1 = 1; B1 = 1;
      #1  A0 = 0; B0 = 1; C0 = 0; A1 = 1; B1 = 1;
    end
    initial begin 
       $monitor("T = %0d | A0 = %b | B0 = %b | C0 = %b | A1 = %b | B1 = %b | S0 = %b | S1 = %b | Cout =%b",$time,A0,B0,C0,A1,B1,S0,S1,Cout);
    end 
    
endmodule: gate_level_2bitfa_tb
</pre>

#### Schematic

<img width="748" alt="image" src="https://user-images.githubusercontent.com/100028556/197327697-cbe4a4b0-e322-4b1c-89c9-b35bf9ea8a54.png">

#### Output

<img width="740" alt="image" src="https://user-images.githubusercontent.com/100028556/197327736-adab1ebe-b15d-4b6a-9b77-71e04dcde060.png">

### Dataflow Modelling

#### Design File

<pre>
module dataflow_fa(
    input a0, input a1,input b0, 
    input b1,input c0, output s0, 
    output s1, output cout
    );
    assign s0 = a0^b0^c0;
    assign c1 = (a0&b0)|(c0&(a0^b0));
    assign s1 = a1^b1^c1;
    assign cout = (a1&b1)|(c1&(a1^b1));
endmodule
</pre>

#### TestBench File

<pre>
module dataflow_fa_tb;
    reg a0,a1,b0,b1,c0;
    wire s0,s1,cout;
    
    dataflow_fa fa1(.a0(a0),.a1(a1),.b0(b0),.b1(b1),.c0(c0),.s0(s0),.s1(s0),.cout(cout));
    
    initial begin $dumpfile("dataflow_fa.vcd"); $dumpvars(); end
    initial begin 
      a0 = 1; b0 = 1; c0 = 1; a1 = 1; b1 = 1;
    end
    initial begin 
       $monitor("T = %0d | a0 = %b | b0 = %b | c0 = %b | a1 = %b | b1 = %b | s0 = %b | s1 = %b | cout = %b",$time,a0,b0,c0,a1,b1,s0,s1,cout);
    end 

endmodule: dataflow_fa_tb
</pre>

#### Schematic

<img width="745" alt="image" src="https://user-images.githubusercontent.com/100028556/197330093-ffdf6985-5c85-419e-b186-4b63c7d5f6e1.png">

#### Output

<img width="275" alt="image" src="https://user-images.githubusercontent.com/100028556/197330144-a8590a99-d35b-499e-8022-43a332c3c890.png">

### Behavioural Modelling

#### Design File

<pre>
`timescale 1ns / 1ps 
module behavioural_fa( A0, A1, B0 , B1, C0, S0,S1, Cout);

 input wire A0,A1, B0,B1,C0;
 output reg S0,S1, Cout;

  always @(A0 or A1 or B0 or B1 or C0)
  begin 
   S0 = A0^B0 ^C0;
   S1 = A1^B1^((A0&B0)|(C0&(A0^B0)));
   Cout =  (A1&B1)|(((A0&B0)|(C0&(A0^B0)))&(A1^B1));
  end
endmodule
</pre>

#### TestBench file

<pre>
`timescale 1ns / 1ps
module top;
  reg  A0_input, A1_input,B0_input,B1_input, C0_input;
  wire Sum0,Sum1,C_output;  
  behavioural_fa instantiation(.A0(A0_input), .A1(A1_input), .B0(B0_input), .B1(B1_input), .C0(C0_input),.S0(Sum0),.S1(Sum1),.Cout(C_output));

  initial
    begin
      $dumpfile("xyz.vcd");
      $dumpvars;
      A0_input =0;A1_input = 0;B0_input = 0;B1_input = 0;C0_input = 0;#100 $finish;
    end
always #160 A0_input=~A0_input;
always #80 B0_input=~B0_input;
always #40 C0_input=~C0_input;
always #20 A1_input = ~A1_input;
always #10 B1_input = ~B1_input;
//display output if there's a change in the input event
  always @(A0_input or B0_input or C0_input,A1_input,B1_input)
      $monitor("At TIME(in ns)=%t, A0=%d B0=%d C0=%d A1 = %d B1 = %d Sum0 = %d Sum1 = %d Carry = %d", $time, A0_input, B0_input, C0_input,A1_input,B1_input, Sum0,Sum1, C_output);

endmodule
</pre>

#### Schematic

<img width="749" alt="image" src="https://user-images.githubusercontent.com/100028556/197332636-7ee09b06-f168-4045-ac73-5163602c9420.png">

#### Output

<img width="620" alt="image" src="https://user-images.githubusercontent.com/100028556/197332517-e6e46e86-0373-4f7b-ae8d-c81eaed19363.png">

#### End of week 3 assignments
