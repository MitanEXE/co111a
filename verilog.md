# Verilog

##### 國立金門大學 資訊工程學系

##### 名字：陳彬彬  學號：111010544

# Chapter One: Install and Operation

#### Install the nand2tetris

> ![]()
> To start it, you'll need to use the Nand2Tetris app you can [Click here to redirect to the site](https://www.nand2tetris.org/software)，
> The Nand to tetris Software Suite features the following software tools:
>
> - Hardware Simulator
> - CPU Emulator
> - VM Emulator
> - Assembler
> - Compiler
> - Operating system
> - Text Comparer

#### How to execute the software

> Before you run the app, you'll need to prepare an text editor/code editor to edit or rewrite the data
>
> - Visual Studio Code
> - Sublime Text
> - Atom
> - Notepad++

#### Rewrite the file data

> How to rewrite it? back to the previous step you'll need to use text editor, and which file data we will rewrite? 
> it's .hdl file format


# Chapter two
> How to operate the nand2tetris software? 
> These are the demo that can help you to understand how to operate it. [Click here to redirect to the site]([https://www.nand2tetris.org/software](https://www.youtube.com/watch?v=FW6Z_Xp2v-c&list=PLYM3zllSC3SVdjWQUfedxssewHRS7EHuA&ab_channel=ShimonSchocken))

# Chapter Three

#### Logics

> To operate it, we will need to understand the basic of boolean logics and logic gates. [Click here to redirect to the site]([https://drive.google.com/file/d/1MY1buFHo_Wx5DPrKhCNSA2cm5ltwFJzM/view])
> To operate it, you'll need the data to start it. Here are the links may help you to obtain the files. [Click here to redirect to the site](https://www.nand2tetris.org/project01)

#### And
###### HDL
<pre><code>    Nand(a=a, b=b, out=AdB);
    Nand(a=AdB, b=AdB, out=out);
</code></pre>
###### The following is the truth table provided by Nand2Tetris.
<pre><code>|   a   |   b   |  out  |
|   0   |   0   |   0   |
|   0   |   1   |   0   |
|   1   |   0   |   0   |
|   1   |   1   |   1   |
</code></pre>
#### And16
###### HDL
<pre><code>     And(a=a[0],b=b[0],out=out[0]);
    And(a=a[1],b=b[1],out=out[1]);
    And(a=a[2],b=b[2],out=out[2]);
    And(a=a[3],b=b[3],out=out[3]);
    And(a=a[4],b=b[4],out=out[4]);
    And(a=a[5],b=b[5],out=out[5]);
    And(a=a[6],b=b[6],out=out[6]);
    And(a=a[7],b=b[7],out=out[7]);
    And(a=a[8],b=b[8],out=out[8]);
    And(a=a[9],b=b[9],out=out[9]);
    And(a=a[10],b=b[10],out=out[10]);
    And(a=a[11],b=b[11],out=out[11]);
    And(a=a[12],b=b[12],out=out[12]);
    And(a=a[13],b=b[13],out=out[13]);
    And(a=a[14],b=b[14],out=out[14]);
    And(a=a[15],b=b[15],out=out[15]);
</code></pre>
###### The output.
<pre><code>|        a         |        b         |       out        |
| 0000000000000000 | 0000000000000000 | 0000000000000000 |
| 0000000000000000 | 1111111111111111 | 0000000000000000 |
| 1111111111111111 | 1111111111111111 | 1111111111111111 |
| 1010101010101010 | 0101010101010101 | 0000000000000000 |
| 0011110011000011 | 0000111111110000 | 0000110011000000 |
| 0001001000110100 | 1001100001110110 | 0001000000110100 |
</code></pre>
#### DMux
###### HDL
<pre><code>    Not(in=sel,out=nsel);
    And(a=in,b=sel,out=b);
    And(a=in,b=nsel,out=a);
</code></pre>

###### output。
<pre><code>|  in   |  sel  |   a   |   b   |
|   0   |   0   |   0   |   0   |
|   0   |   1   |   0   |   0   |
|   1   |   0   |   1   |   0   |
|   1   |   1   |   0   |   1   |
</code></pre>

#### DMux4Way
###### HDL
<pre><code>    DMux(in=in,sel=sel[1],a=ab,b=cd);
    DMux(in=ab, sel=sel[0], a=a, b=b);
    DMux(in=cd, sel=sel[0], a=c, b=d);
</code></pre>
###### output
<pre><code>| in  | sel  |  a  |  b  |  c  |  d  |
|  0  |  00  |  0  |  0  |  0  |  0  |
|  0  |  01  |  0  |  0  |  0  |  0  |
|  0  |  10  |  0  |  0  |  0  |  0  |
|  0  |  11  |  0  |  0  |  0  |  0  |
|  1  |  00  |  1  |  0  |  0  |  0  |
|  1  |  01  |  0  |  1  |  0  |  0  |
|  1  |  10  |  0  |  0  |  1  |  0  |
|  1  |  11  |  0  |  0  |  0  |  1  |
</code></pre>

#### DMux8Way
###### HDL 
<pre><code>    DMux(in=in,sel=sel[2],a=in0,b=in1);
    DMux4Way(in=in0,sel=sel[0..1],a=a,b=b,c=c,d=d);
    DMux4Way(in=in1,sel=sel[0..1],a=e,b=f,c=g,d=h);
</code></pre>
###### output 
<pre><code>    | in  |  sel  |  a  |  b  |  c  |  d  |  e  |  f  |  g  |  h  |
|  0  |  000  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
|  0  |  001  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
|  0  |  010  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
|  0  |  011  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
|  0  |  100  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
|  0  |  101  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
|  0  |  110  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
|  0  |  111  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
|  1  |  000  |  1  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
|  1  |  001  |  0  |  1  |  0  |  0  |  0  |  0  |  0  |  0  |
|  1  |  010  |  0  |  0  |  1  |  0  |  0  |  0  |  0  |  0  |
|  1  |  011  |  0  |  0  |  0  |  1  |  0  |  0  |  0  |  0  |
|  1  |  100  |  0  |  0  |  0  |  0  |  1  |  0  |  0  |  0  |
|  1  |  101  |  0  |  0  |  0  |  0  |  0  |  1  |  0  |  0  |
|  1  |  110  |  0  |  0  |  0  |  0  |  0  |  0  |  1  |  0  |
|  1  |  111  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  1  |
</code></pre>

#### Mux
###### HDL
<pre><code>    Not(in=sel,out=x);
    And(a=a,b=x,out=y);
    And(a=sel,b=b,out=z);
    Or(a=y,b=z,out=out);
</code></pre>
###### output
<pre><code>    |   a   |   b   |  sel  |  out  |
|   0   |   0   |   0   |   0   |
|   0   |   0   |   1   |   0   |
|   0   |   1   |   0   |   0   |
|   0   |   1   |   1   |   1   |
|   1   |   0   |   0   |   1   |
|   1   |   0   |   1   |   0   |
|   1   |   1   |   0   |   1   |
|   1   |   1   |   1   |   1   |
</code></pre>

#### Mux4Way16
###### HDL
<pre><code>    Mux16(a=a, b=b, sel=sel[0], out=outab);
    Mux16(a=c, b=d, sel=sel[0], out=outcd);
    Mux16(a=outab, b=outcd, sel=sel[1], out=out);
</code></pre>

#### Mux8Way16
###### HDL
<pre><code>    Mux4Way16(a=a, b=b, c=c, d=d, sel=sel[0..1], out=outad);
    Mux4Way16(a=e, b=f, c=g, d=h, sel=sel[0..1], out=outeh);
    Mux16(a=outad, b=outeh, sel=sel[2], out=out);
</code></pre>

#### Mux16
###### HDL
<pre><code>    Mux(a=a[0],b=b[0],sel=sel,out=out[0]);
    Mux(a=a[1],b=b[1],sel=sel,out=out[1]);
    Mux(a=a[2],b=b[2],sel=sel,out=out[2]);
    Mux(a=a[3],b=b[3],sel=sel,out=out[3]);
    Mux(a=a[4],b=b[4],sel=sel,out=out[4]);
    Mux(a=a[5],b=b[5],sel=sel,out=out[5]);
    Mux(a=a[6],b=b[6],sel=sel,out=out[6]);
    Mux(a=a[7],b=b[7],sel=sel,out=out[7]);
    Mux(a=a[8],b=b[8],sel=sel,out=out[8]);
    Mux(a=a[9],b=b[9],sel=sel,out=out[9]);
    Mux(a=a[10],b=b[10],sel=sel,out=out[10]);
    Mux(a=a[11],b=b[11],sel=sel,out=out[11]);
    Mux(a=a[12],b=b[12],sel=sel,out=out[12]);
    Mux(a=a[13],b=b[13],sel=sel,out=out[13]);
    Mux(a=a[14],b=b[14],sel=sel,out=out[14]);
    Mux(a=a[15],b=b[15],sel=sel,out=out[15]);
</code></pre>

#### Not
###### HDL
<pre><code>    Nand(a=in, b=in, out=out);
</code></pre>

#### Not16
###### HDL
<pre><code>      Not(in=in[0],out=out[0]);
    Not(in=in[1],out=out[1]);
    Not(in=in[2],out=out[2]);
    Not(in=in[3],out=out[3]);
    Not(in=in[4],out=out[4]);
    Not(in=in[5],out=out[5]);
    Not(in=in[6],out=out[6]);
    Not(in=in[7],out=out[7]);
    Not(in=in[8],out=out[8]);
    Not(in=in[9],out=out[9]);
    Not(in=in[10],out=out[10]);
    Not(in=in[11],out=out[11]);
    Not(in=in[12],out=out[12]);
    Not(in=in[13],out=out[13]);
    Not(in=in[14],out=out[14]);
    Not(in=in[15],out=out[15]);
</code></pre>

#### Or
###### HDL 撰寫
<pre><code>   Not(in=a,out=x);
    Not(in=b,out=y);
    And(a=x,b=y,out=z);
    Not(in=z,out=out);
</code></pre>
#### Or8Way
###### HDL
<pre><code>    Or(a=in[7], b=in[6], out=or13);
    Or(a=in[5], b=in[4], out=or9);
    Or(a=in[3], b=in[2], out=or5);
    Or(a=in[1], b=in[0], out=or1);
    Or(a=or13, b=or9, out=or22);
    Or(a=or5, b=or1, out=or6);
    Or(a=or22, b=or6, out=out);
</code></pre>

#### Or16
###### HDL
<pre><code>    Or(a=a[15], b=b[15], out=out[15]);
    Or(a=a[14], b=b[14], out=out[14]);
    Or(a=a[13], b=b[13], out=out[13]);
    Or(a=a[12], b=b[12], out=out[12]);
    Or(a=a[11], b=b[11], out=out[11]);
    Or(a=a[10], b=b[10], out=out[10]);
    Or(a=a[9], b=b[9], out=out[9]);
    Or(a=a[8], b=b[8], out=out[8]);
    Or(a=a[7], b=b[7], out=out[7]);
    Or(a=a[6], b=b[6], out=out[6]);
    Or(a=a[5], b=b[5], out=out[5]);
    Or(a=a[4], b=b[4], out=out[4]);
    Or(a=a[3], b=b[3], out=out[3]);
    Or(a=a[2], b=b[2], out=out[2]);
    Or(a=a[1], b=b[1], out=out[1]);
    Or(a=a[0], b=b[0], out=out[0]);
</code></pre>

#### Xor
###### HDL 撰寫
<pre><code>    Nand (a=a, b=b, out= AnandB);
    Or   (a=a, b=b, out= AorB);
    And  (a=AnandB, b=AorB, out=out);
</code></pre>

# Chapter four, arithmetic

#### Add16
###### HDL
<pre><code>    FullAdder(a=a[0],b=b[0],c=false,sum=out[0],carry=c0);
    FullAdder(a=a[1],b=b[1],c=c0,sum=out[1],carry=c1);
    FullAdder(a=a[2],b=b[2],c=c1,sum=out[2],carry=c2);
    ...
    FullAdder(a=a[15],b=b[15],c=c14,sum=out[15],carry=c15);
</code></pre>

#### ALU-nostat
###### HDL
<pre><code>    Mux16(a=x,  b=false,  sel=zx, out=x1);   
    Not16(in=x1,out=notx1);
    Mux16(a=x1, b=notx1, sel=nx, out=x2);   
    Mux16(a=y,  b=false,  sel=zy, out=y1);   
    Not16(in=y1,out=noty1);
    Mux16(a=y1, b=noty1, sel=ny, out=y2);  
  
    Add16(a=x2, b=y2, out=addxy);         
    And16(a=x2, b=y2, out=andxy);        
    Mux16(a=andxy, b=addxy, sel=f, out=o1);   
    Not16(in=o1, out=noto1);           
    Mux16(a=o1, b=noto1, sel=no, out=out); 
</code></pre>

#### AlU
###### HDL
<pre><code>   Mux16(a=x,b=false,sel=zx,out=1x);
   Not16(in=1x,out=n1x);
   Mux16(a=1x,b=n1x,sel=nx,out=2x);

   Mux16(a=y,b=false,sel=zy,out=1y);
   Not16(in=1y,out=n1y);
   Mux16(a=1y,b=n1y,sel=ny,out=2y);

   Add16(a=2x, b=2y, out=addxy);     
   Mux16(a=andxy, b=addxy, sel=f, out=1o); 
   Not16(in=1o, out=not1o);
   Mux16(a=1o, b=not1o, sel=no, out=2o, out=out,out[0..7]=outLow,out[8..15]=outHigh,out[15]=ng); 
   Or8Way(in=outLow, out=orLow);  
   Or8Way(in=outHigh, out=orHigh);  
   Or(a=orLow, b=orHigh, out=notzr);  
   Not(in=notzr, out=zr); 
</code></pre>

#### FullAdder
###### HDL
<pre><code>    Xor(a=a,b=b,out=xab);
    Xor(a=xab,b=c,out=sum);
    And(a=a,b=c,out=ac);
    And(a=a,b=b,out=ab);
    And(a=b,b=c,out=bc);
    Or(a=ac,b=ab,out=acORab);
    Or(a=acORab,b=bc,out=carry);
</code></pre>

#### HalfAdder
###### HDL
<pre><code>    And(a=a,b=b,out=carry);
    Xor(a=a,b=b,out=sum);
</code></pre>

#### Inc16
###### HDL
<pre><code>   Add16(a=in,b[0]=true,b[1..15]=false,out=out);
</code></pre>

# Chapter five

#### Bit
###### HDL
<pre><code>    Mux(a=do,b=in,sel=load,out=mout);
    DFF(in=mout,out=do,out=out);
</code></pre>

#### PC
###### HDL
<pre><code>    Register(in=if3, load=true, out=o, out=out);
    Inc16(in=o, out=oInc);
  
    Mux16(a=o,   b=oInc,  sel=inc,   out=if1);
    Mux16(a=if1, b=in,    sel=load,  out=if2);
    Mux16(a=if2, b=false,  sel=reset, out=if3);
</code></pre>

#### RAM8
###### HDL
<pre><code>    DMux8Way(in=load,sel=address,a=a,b=b,c=c,d=d,e=e,f=f,g=g,h=h);
    Register(in=in,load=a,out=oa);
    Register(in=in,load=b,out=ob);
    Register(in=in,load=c,out=oc);
    Register(in=in,load=d,out=od);
    Register(in=in,load=e,out=oe);
    Register(in=in,load=f,out=of);
    Register(in=in,load=g,out=og);
    Register(in=in,load=h,out=oh);
    Mux8Way16(a=oa,b=ob,c=oc,d=od,e=oe,f=of,g=og,h=oh,sel=address,out=out);
</code></pre>

#### RAM64
###### HDL
<pre><code>    DMux8Way(in=load,sel=address[3..5],a=a,b=b,c=c,d=d,e=e,f=f,g=g,h=h);
    RAM8(in=in,load=a,address=address[0..2],out=oa);
    RAM8(in=in,load=b,address=address[0..2],out=ob);
    RAM8(in=in,load=c,address=address[0..2],out=oc);
    RAM8(in=in,load=d,address=address[0..2],out=od);
    RAM8(in=in,load=e,address=address[0..2],out=oe);
    RAM8(in=in,load=f,address=address[0..2],out=of);
    RAM8(in=in,load=g,address=address[0..2],out=og);
    RAM8(in=in,load=h,address=address[0..2],out=oh);
    Mux8Way16(a=oa,b=ob,c=oc,d=od,e=oe,f=of,g=og,h=oh,sel=address[3..5],out=out);
</code></pre>

#### Register
###### HDL
<pre><code>    Bit(in=in[0],load=load,out=out[0]);
    Bit(in=in[1],load=load,out=out[1]);
    Bit(in=in[2],load=load,out=out[2]);
    ...
    Bit(in=in[15],load=load,out=out[15]);
</code></pre>

#### RAM4K
###### HDL
<pre><code>    DMux8Way(in=load,sel=address[9..11],a=a,b=b,c=c,d=d,e=e,f=f,g=g,h=h);
    RAM512(in=in,load=a,address=address[0..8],out=oa);
    RAM512(in=in,load=b,address=address[0..8],out=ob);
    RAM512(in=in,load=c,address=address[0..8],out=oc);
    RAM512(in=in,load=d,address=address[0..8],out=od);
    RAM512(in=in,load=e,address=address[0..8],out=oe);
    RAM512(in=in,load=f,address=address[0..8],out=of);
    RAM512(in=in,load=g,address=address[0..8],out=og);
    RAM512(in=in,load=h,address=address[0..8],out=oh);
    Mux8Way16(a=oa,b=ob,c=oc,d=od,e=oe,f=of,g=og,h=oh,sel=address[9..11],out=out);
</code></pre>

#### RAM16K
###### HDL
<pre><code>    DMux4Way(in=load,sel=address[0..1],a=a,b=b,c=c,d=d);
    RAM4K(in=in,load=a,address=address[2..13],out=oa);
    RAM4K(in=in,load=b,address=address[2..13],out=ob);
    RAM4K(in=in,load=c,address=address[2..13],out=oc);
    RAM4K(in=in,load=d,address=address[2..13],out=od);
    Mux4Way16(a=oa,b=ob,c=oc,d=odsel=address[0..1],out=out);
</code></pre>

#### RAM512
###### HDL
<pre><code>     DMux8Way(in=load,sel=address[6..8],a=a,b=b,c=c,d=d,e=e,f=f,g=g,h=h);
     RAM64(in=in,load=a,address=address[0..5],out=oa);
     RAM64(in=in,load=b,address=address[0..5],out=ob);
     RAM64(in=in,load=c,address=address[0..5],out=oc);
     RAM64(in=in,load=d,address=address[0..5],out=od);
     RAM64(in=in,load=e,address=address[0..5],out=oe);
     RAM64(in=in,load=f,address=address[0..5],out=of);
     RAM64(in=in,load=g,address=address[0..5],out=og);
     RAM64(in=in,load=h,address=address[0..5],out=oh);
     Mux8Way16(a=oa,b=ob,c=oc,d=od,e=oe,f=of,g=og,h=oh,sel=address[6..8],out=out);
</code></pre>
