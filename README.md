EXP-2

date:

                      SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM:
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA

PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

LOGIC DIAGRAM

ENCODER

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-2/assets/161432255/efe2b90d-7a2e-48b0-9dea-021660cbb2e0)

verilog code
```
module encoder(a,y);
input [7:0]a;
output[2:0]y;
or(y[2],a[6],a[5],a[4],a[3]);
or(y[1],a[6],a[5],a[2],a[1]);
or(y[0],a[6],a[4],a[2],a[0]);
endmodule
```
output

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-2/assets/161432255/0a7dae4d-195d-4478-ab95-7fa72bff1cb0)

LOGIC DIAGRAM DECODER

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-2/assets/161432255/379dfab4-6571-4e74-b3f0-7fad4010dcb4)

verilog code
```
module decoder1(a,y);
input [2:0]a;
output[7:0]y;
and(y[0],~a[2],~a[1],~a[0]);
and(y[1],~a[2],~a[1],a[0]);
and(y[2],~a[2],a[1],~a[0]);
and(y[3],~a[2],a[1],a[0]);
and(y[4],a[2],~a[1],~a[0]);
and(y[5],a[2],~a[1],a[0]);
and(y[6],a[2],a[1],~a[0]);
and(y[7],a[2],a[1],a[0]);
endmodule
```
output

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-2/assets/161432255/21cc150c-9fc2-4b5a-b779-b3a6b1e57e98)

LOGIC DIAGRAM MULTIPLEXER

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-2/assets/161432255/cd7ef931-2f82-44dc-8110-321214476a4f)

VERILOG CODE
```
module mux(s,c,a);
input [2:0]s;
input [7:0]a;
wire [7:0]w;
output c;
and(w[0],a[0],~s[2],~s[1],~s[0]);
and(w[1],a[1],~s[2],~s[1],s[0]);
and(w[2],a[2],~s[2],s[1],~s[0]);
and(w[3],a[3],~s[2],s[1],s[0]);
and(w[4],a[4],s[2],~s[1],~s[0]);
and(w[5],a[5],s[2],~s[1],s[0]);
and(w[6],a[6],s[2],s[1],~s[0]);
and(w[7],a[7],s[2],s[1],s[0]);
or (c,w[0],w[1],w[2],w[3],w[4],w[5],w[6],w[7]);
endmodule
```
output

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-2/assets/161432255/8dd1c71b-e233-4725-96d7-70477fa1babd)

VERILOG CODE DEMULTIPLEXER

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-2/assets/161432255/7499dabf-d2bd-48b0-88ec-fd33fc3bf323)

VERILOG CODE
```
module demux_8(s,a,y);
input [2:0]s;
input a;
output [7:0]y;
and(y[0],a,~s[2],~s[1],~s[0]);
and(y[1],a,~s[2],~s[1],s[0]);
and(y[2],a,~s[2],s[1],~s[0]);
and(y[3],a,~s[2],s[1],s[0]);
and(y[4],a,s[2],~s[1],~s[0]);
and(y[5],a,s[2],~s[1],s[0]);
and(y[6],a,s[2],s[1],~s[0]);
and(y[7],a,s[2],s[1],s[0]);
endmodule
```

output

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-2/assets/161432255/31b3314b-b860-40ff-9334-b0ee03ed5a5f)

MAGNITUDE COMPARATOR

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-2/assets/161432255/438bf227-3184-4629-9e37-92c0ee354a9b)

VERILOG CODE
```
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 if (a==b)
 begin
  eq = 1'b1;
  lt = 1'b0;
  gt = 1'b0;
 end
 else if (a>b)
 begin
  eq = 1'b0;
  lt = 1'b0;
  gt = 1'b1;
 end
 else
 begin
  eq = 1'b0;
  lt = 1'b1;
  gt = 1'b0;
 end
end 
endmodule
```
OUTPUT

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-2/assets/161432255/08d2e7c6-2608-4faf-8d17-a85311763ce5)

RESULT

Thus the simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, 2bit MAGNITUDE COMPARATOR using vivado is successfully completed and executed.

























