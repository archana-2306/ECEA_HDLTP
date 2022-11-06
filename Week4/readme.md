### Week 4
### Designing Combinatorial circuits using verilog
### HALF ADDER
#### DESIGN FILE

<pre>
module half_adder(a,b,s,c);
    input a,b;
    output s,c;

    xor x1(s,a,b);
    and a1(c,a,b);

endmodule: half_adder
</pre>

#### TESTBENCH 

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

### FULL ADDER

#### DESIGN FILE

<pre>
module full_adder(A,B,Cin,Sum,Cout);
     input A,B,Cin;
     output Sum,Cout;
     
     wire y1,y2,y3;
     half_adder ha1(.a(A),.b(B),.s(y2),.c(y1));
     half_adder ha2(.a(y2),.b(Cin),.s(Sum),.c(y3));
     or o1(Cout,y3,y1);
endmodule: full_adder

module half_adder(a,b,s,c);
    input a,b;
    output s,c;

    xor x1(s,a,b);
    and a1(c,a,b);

endmodule: half_adder
</pre>

#### TESTBENCH

<pre>
module full_adder_tb;

    reg A,B,Cin;
    wire Sum,Cout;
    full_adder fa1(.A(A),.B(B),.Cin(Cin),.Sum(Sum),.Cout(Cout));
   
   initial begin $dumpfile("full_adder.vcd"); $dumpvars(); end 

   initial begin A = 1; B = 1; Cin = 1; end
    initial begin $monitor("time = %0d A = %b B = %b Cin = %b Sum = %b Cout = %b",$time,A,B,Cin,Sum,Cout);end

endmodule: full_adder_tb
</pre>

#### RTL

<img width="706" alt="image" src="https://user-images.githubusercontent.com/100028556/198840628-ed6810be-89be-41a2-9d24-98bc5f92b05a.png">

#### output

<img width="594" alt="image" src="https://user-images.githubusercontent.com/100028556/198840645-33f7d895-fac5-4c94-897f-e36a238dcc59.png">

### MULTIPLEXER

#### Multiplexer is a combinatorial circuit where it selects information from one of many inputs and directs it to a single output line

#### Design file

<pre>

module mux(I0,I1,S,Out);
      input I0,I1,S;
      output Out;
      // DATALEVEL Model
      assign Out = S ? I0:I1;
endmodule : mux
</pre>

#### TestBench

<pre>
module mux_tb;
    reg I0,I1,S;
    wire Out;
    
    mux mux1(.I0(I0),.I1(I1),.S(S),.Out(Out));
    integer i; 
    initial begin
        $dumpfile("mux.vcd");
        $dumpvars(0,mux_tb);
        $monitor($time,"I0 = %b, I1 = %b, S = %b, Out = %b",I0,I1,S,Out);
        
        for (i=0; i<7; i = i+1) 
        begin
            #5 {I0,I1,S} = i;
        end
        #100 $finish;
    end
endmodule : mux_tb
</pre>


