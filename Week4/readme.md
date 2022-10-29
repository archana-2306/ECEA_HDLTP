### Week 4
### Designing Combinatorial circuits using verilog
### DESIGN FILE

<pre>
module half_adder(a,b,s,c);
    input a,b;
    output s,c;

    xor x1(s,a,b);
    and a1(c,a,b);

endmodule: half_adder
</pre>

### TESTBENCH 

<pre>
module half_adder_tb;
    reg a,b;
    wire s,c;
    
    half_adder ha1(.a(a),.b(b),.s(s),.c(c));
    
    initial begin $dumpfile("half_adder.vcd"); $dumpvars(); end 
    initial begin a = 1; end
    initial begin b = 1; end
    initial begin $monitor("time = %0d a = %b b = %b sum=%b carry = %b",$time,a,b,s,c); end
    
endmodule : half_adder_tb
</pre>

### RTL Design

<img width="351" alt="image" src="https://user-images.githubusercontent.com/100028556/198827662-c317ade3-d67c-45b2-8a9b-dd2ca9b413d6.png">

### output 

<img width="631" alt="image" src="https://user-images.githubusercontent.com/100028556/198827811-a7d4c28a-cc97-45f6-bd7b-4219ae63bca2.png">

