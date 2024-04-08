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

**LOGIC DIAGRAM**

ENCODER![301734849-3cd1f95e-7531-4cad-9154-fdd397ac439e](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/106177371/4e20af07-c6ac-472d-93ef-2af3312a0553)





DECODER
![301735010-45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/106177371/a71fb811-87b0-49f5-96ae-c2e93ec77290)





MULTIPLEXER
![301735287-427f75b2-8e67-44b9-ac45-a66651787436](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/106177371/c287fadb-cc44-4b62-b76c-962c5168955a)





DEMULTIPLEXER
![301735386-1c45a7fc-08ac-4f76-87f2-c084e7150557](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/106177371/0e4cc37b-ba3a-4929-bfad-6c235c45e389)



MAGNITUDE COMPARATOR
![301735522-b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/106177371/5297f187-c67b-4d72-baf7-fc1776d9768e)




  


VERILOG CODE
# ENCODER
```
module encoder(a,y);
input [7:0]a;
output[2:0]y;
or(y[2],a[6],a[5],a[4],a[3]);
or(y[1],a[6],a[5],a[2],a[1]);
or(y[0],a[6],a[4],a[2],a[0]);
endmodule
```
# DECODER
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
# MULTIPLEXER
```
verilog code 
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
# DEMULTIPLEXER
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
# MAGNITUDE COMPARATOR
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

OUTPUT WAVEFORM
# ENCODER
![318353110-a7497d75-f686-43b8-9357-69e59e14eea1](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/106177371/59d041e7-3431-4431-855a-284b8914c427)

# DECODER
![318353325-5f78d343-fc3a-4c1e-bfcf-f85bcc58a6e9](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/106177371/6429bb62-adcb-4868-aa03-76482ea1d9ce)


# MULTIPLEXER
![318358035-5768add5-fee5-4c52-91c3-e3e3e72aa3ed](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/106177371/a6235842-8df6-4595-88fa-01e6a456d25f)


# DEMULTIPLEXER
![318358386-559774ba-65c5-4eeb-9d5f-452ea3b27c29](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/106177371/2e89d256-649a-4827-b45a-505908e34ae9)


# MAGNITUDE COMPARATOR
![318358593-4a9e2670-3a8d-42fd-a755-f728c5a36b45](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/106177371/7fe02453-8dbf-48b2-9be5-7c97818497e7)

RESULT
simulation and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE is verified.
