## This the first week of our HDL Program. We have installed the vivado software and learned the basic syntax.
### The first program on verilog is to design a full adder. 
### Design file using verilog
<pre>
// Code your design : Full Adder
module full_add(a,b,cin,sum,cout);
  input a,b,cin;
  output sum,cout;
  wire x,y,z;
 
// instantiate building blocks of full adder 
  half_add h1(.a(a),.b(b),.s(x),.c(y));
  half_add h2(.a(x),.b(cin),.s(sum),.c(z));
  or o1(cout,y,z);
endmodule : full_add

// code your half adder design             
module half_add(a,b,s,c); 
  input a,b;
  output s,c;
 
// gate level design of half adder  
  xor x1(s,a,b);
  and a1(c,a,b);
endmodule :half_add
</pre>
### Simulation file or test bench using verilog
<pre>
// Code your testbench here
module full_add_tb;
  reg a,b,cin;
  wire sum,cout;
 
// instantiate the DUT block  
  full_add f1(.a(a),.b(b),.cin(cin),.sum(sum),.cout(cout));
 
// this particular line is added to dump the file on online simulator
  initial begin $dumpfile("full_tb.vcd");$dumpvars(); end

// insert all the inputs 
  initial begin a=1'b1;  #4; a=1'b0;#10 $stop();end
  initial begin b=1'b1; forever #2 b=~b;end
  initial begin cin=1'b1;forever #1 cin=~cin; #10 $stop();end

// monitor all the input and output ports at times 
// when any of the input changes its state

 initial begin $monitor(" time=%0d A=%b B=%b Cin=%b Sum=%b Cout=%b",$time,a,b,cin,sum,cout);end
endmodule : full_add_tb
</pre>
### TCL Console output

![image](https://user-images.githubusercontent.com/100028556/197371735-bb2a8265-5a20-4142-8f19-d0a724f15297.png)

### RTL Design


