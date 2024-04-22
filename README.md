# SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

# AIM: 
  To simulate ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using VIVADO 2023.1.

# APPARATUS REQUIRED:
              VIVADO 2023.1

# PROCEDURE:
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

# LOGIC DIAGRAM

# ENCODER
![301734849-3cd1f95e-7531-4cad-9154-fdd397ac439e](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/e0686f04-ab98-4b23-b0f7-7bfd04004b32)

# verilog code
```
module encoder_8_to_3(a0,a1,a2,d7,d6,d5,d4,d3,d2,d1,d0);
input d7,d6,d5,d4,d3,d2,d1,d0;
output a0,a1,a2;
or g1(a0,d1,d3,d5,d7);
or g2(a1,d2,d3,d6,d7);
or g3(a2,d4,d5,d6,d7);
endmodule
```
# output

![318353110-a7497d75-f686-43b8-9357-69e59e14eea1](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/b2cb2f7d-c92a-47ec-a900-19bd3b3b0da3)

# RTL DESIGN

<img width="764" alt="324393129-54ddc383-ee27-4cfb-b4e4-bcc3e2720b04" src="https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/8105fc33-fd84-4d77-a7fa-7ccadf2a6964">

# DECODER
![301735010-45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/4a43503a-8dd4-4968-a06c-359e67030439)

# verilog code
```
module decoder(input [2:0] a,output [7:0] d );
assign d[0]=(~a[2])&(~a[1])&(~a[0]);
assign d[1]=(~a[2])&(~a[1])&(a[0]);
assign d[2]=(~a[2])&(a[1])&(~a[0]);
assign d[3]=(~a[2])&(a[1])&(a[0]);
assign d[4]=(a[2])&(~a[1])&(~a[0]);
assign d[5]=(a[2])&(~a[1])&(a[0]);
assign d[6]=(a[2])&(a[1])&(~a[0]);
assign d[7]=(a[2])&(a[1])&(a[0]);
endmodule
```

# output

![318353325-5f78d343-fc3a-4c1e-bfcf-f85bcc58a6e9](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/6e158ab1-eca6-450b-b59e-a212e33a3e43)

# RTL DESIGN

<img width="766" alt="324393344-2e4fd12c-b731-49f8-ad9d-370a70d33e8f" src="https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/11b97cf8-ef31-4812-85c7-5aace6ba14d0">

# MULTIPLEXER

![301735287-427f75b2-8e67-44b9-ac45-a66651787436](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/f2b7c963-4b8a-4ae6-918e-81248613eec5)

# verilog code
```
module mux(a,s,y);
input [7:0]a;
input [2:0]s;
output y;
reg y;
always@({s ,a})
   begin
      case(s)
         3'b000: y=a[0];
         3'b001: y=a[1];
         3'b010: y=a[2];
         3'b011: y=a[3];
         3'b100: y=a[4];
         3'b101: y=a[5];
         3'b110: y=a[6];
         3'b111: y=a[7];
      endcase
   end
endmodule
```

# output

![318358035-5768add5-fee5-4c52-91c3-e3e3e72aa3ed](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/766970e9-975e-478f-8ab1-8c5df2c24ad9)

# RTL DESIGN

<img width="761" alt="324393560-d1c0f5dc-bfb6-4f7a-9eea-ad050207e06c" src="https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/2537a600-f8be-48cf-8998-f3fe0b1d6f11">

# DEMULTIPLEXER

![301735386-1c45a7fc-08ac-4f76-87f2-c084e7150557](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/6dcb6ced-2602-4d6d-951e-3a8c22a279f7)

# verilog code
```
module demux(din,s,d);
input din;
input[2:0]s;
output [7:0]d;
assign d[0]=(din&~s [2]&~s[1]&~s[0]);
assign d[1]=(din&~s[2]&~s[1]&s[0]);
assign d[2]=(din&~s[2]&s[1]&~s[0]);
assign d[3]=(din&~s[2]&s[1]&s[0]);
assign d[4]=(din&s[2]&~s[1]&~s[0]);
assign d[5]=(din&s[2]&~s[1]&s[0]);
assign d[6]=(din&s[2]&s[1]&~s[0]);
assign d[7]=(din&s[2]&s[1]&s[0]);
endmodule
```

# output

![318358386-559774ba-65c5-4eeb-9d5f-452ea3b27c29](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/be30677f-15b5-4fc7-b9ec-3ec305974ccc)

# RTL DESIGN

<img width="767" alt="324393740-38db4464-72f1-4155-ae71-93c6773a9a00" src="https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/529c0ec3-d323-4b32-9bec-40d369cbae5c">

# MAGNITUDE COMPARATOR

![301735522-b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/ca9b5ed3-9b51-480a-889e-9474be9e35a1)

**verilog code**
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

# output

![318358593-4a9e2670-3a8d-42fd-a755-f728c5a36b45](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/3b0a314f-3c1d-4e68-8284-020d02ebb8ef)

# RTL DESIGN

<img width="761" alt="324393962-4b937b7a-c5ec-43b3-8f7a-27ca463738b3" src="https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/7e9455c7-f0a6-46cd-b86f-96a7b30bcef0">

# RESULT
Simulation and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE is verified.

