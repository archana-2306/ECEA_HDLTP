### Week 5 Contents
#### This week we have started to try out sequential circuits 
#### Sequential Circuits are the one which depends upon the clock 
#### This week we have tried out D FF, JK FF, 4-bit counter and SISO SR
### D FF
#### Verilog Code
#### Synchronous reset rising edge clock 
#### Design File
<pre>
module RisingEdge_DFlipFlop_SyncReset(D,clk,sync_reset,Q);
input D; // Data input 
input clk; // clock input 
input sync_reset; // synchronous reset 
output reg Q; // output Q 
always @(posedge clk) 
begin
 if(sync_reset==1'b1)
  Q <= 1'b0; 
 else 
  Q <= D; 
end 
endmodule 
</pre>
#### Testbench File
<pre>
`timescale 1ns/1ps;
module tb_DFF();
reg D;
reg clk;
reg reset;
wire Q;

RisingEdge_DFlipFlop_SyncReset dut(D,clk,reset,Q);

initial begin
  clk=0;
     forever #10 clk = ~clk;  
end 
initial begin 
 reset=1;
 D <= 0;
 #100;
 reset=0;
 D <= 1;
 #100;
 D <= 0;
 #100;
 D <= 1;
end 
endmodule 
</pre>
#### Simulated Output
