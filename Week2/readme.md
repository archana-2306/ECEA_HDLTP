## This is the second week of HDL program where we have ourselves deigned a 2-bit full adder
### Design File of 2-bit full adder

<pre>
module bit2_full_adder(a0,a1,b0,b1,sum0,sum1,cout);
    input a0,a1,b0,b1;
    output sum0,sum1,cout;
  
    wire x,y,z,u;
 
    half_adder h1(.a(a0),.b(b0),.s(sum0),.c(x));
    half_adder h2(.a(a1),.b(b1),.s(y),.c(z));
    half_adder h3(.a(y),.b(x),.s(sum1),.c(u));
    or o1(cout,u,z);

endmodule: bit2_full_adder

module half_adder(a,b,s,c);
    input a,b;
    output s,c;

    xor x1(s,a,b);
    and a1(c,a,b);

endmodule: half_adder
</pre>

### Test Bench for 2-bit full adder

<pre>
module bit_full_adder_tb;
    reg a0,a1,b0,b1;
    wire sum0,sum1,cout;
    
    bit2_full_adder fa1(.a0(a0),.b0(b0),.a1(a1),.b1(b1));
    
    initial begin $dumpfile("bit2_full_adder.vcd"); $dumpvars(); end 
    initial begin a0 = 1'b1; #4; a0 = 1'b0; #10 $stop(); end
    initial begin a1 = 1'b1; forever #2 a1 = ~a1; end
    initial begin b0 = 1'b1; forever #2 b0 = ~b0; end
    initial begin b1 = 1'b1; forever #2 b1 = ~b1; $stop; end
    initial begin $monitor("time = %0d A0 = %b A1 = %b B0 = %b B1 = %b Sum0 = %b Sum1 = %b Cout = %b",$time,a0,a1,b0,b1,sum0,sum1,cout); end
    
endmodule : bit_full_adder_tb
</pre>



