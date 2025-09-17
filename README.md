# Seven-Segment Display Driver using Verilog HDL

## Aim  
To design and simulate a seven-segment display driver using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 environment. The objective is to implement the logic that converts a 4-bit binary input into the corresponding 7-segment display output for the digits 0 to 9.

## Apparatus Required  
- **Vivado 2023.1**  

## Procedure  

### 1. Launch Vivado 2023.1  
- Open Vivado and create a new project.  

### 2. Design the Verilog Code  
- Write the Verilog code for the seven-segment display, defining the logic that maps a 4-bit binary input to the corresponding segments (a to g) of the display.  

### 3. Create the Testbench  
- Write a testbench to simulate the seven-segment display behavior. The testbench should apply various 4-bit input values and monitor the corresponding output on the seven-segment display.  

### 4. Create the Verilog Files  
- Create both the design module and the testbench in the Vivado project.  

### 5. Run Simulation  
- Run the behavioral simulation to verify the output. Ensure the seven-segment display behaves correctly for binary inputs **0000 to 1001** (decimal **0 to 9**).  

### 6. Observe the Waveforms  
- Analyze the output waveforms in the simulation window, and verify that the correct segments light up for each digit.  

### 7. Save and Document Results  
- Capture screenshots of the waveform and save the simulation logs. These will be included in the lab report.  

---
## Logic Diagram

![image](https://github.com/user-attachments/assets/e561cdb5-b1b0-42d0-94f5-e1efaec9704c)

![image](https://github.com/user-attachments/assets/dc32254e-f88d-471a-a2ba-e4ec5eb3fc11)

![image](https://github.com/user-attachments/assets/a8a8921e-0a37-4697-86d8-0c43cd8aef5a)

## Verilog Code for Seven-Segment Display  

```verilog
module bcd_to_7seg(bcd, seg);
input [3:0] bcd;
output reg [6:0] seg;
always @(*) begin
case (bcd)
    4'd0: seg = 7'b0000001;  
    4'd1: seg = 7'b1001111;  
    4'd2: seg = 7'b0010010;  
    4'd3: seg = 7'b0000110;  
    4'd4: seg = 7'b1001100;  
    4'd5: seg = 7'b0100100;  
    4'd6: seg = 7'b0100000;  
    4'd7: seg = 7'b0001111;  
    4'd8: seg = 7'b0000000;  
    4'd9: seg = 7'b0000100;  
    default: seg = 7'b1111111; 
  endcase
end
endmodule
```
## Testbench for Seven-Segment Display
```verilog

`timescale 1ns / 1ps
module bcd_to_7seg_tb;
  reg [3:0] bcd;
  wire [6:0] seg;
  bcd_to_7seg uut (bcd,seg);
  initial 
  begin
    bcd = 4'b0000;
    #10 bcd = 4'b0000; 
    #10 bcd = 4'b0001; 
    #10 bcd = 4'b0010; 
    #10 bcd = 4'b0011; 
    #10 bcd = 4'b0100; 
    #10 bcd = 4'b0101; 
    #10 bcd = 4'b0110; 
    #10 bcd= 4'b0111; 
    #10 bcd = 4'b1000; 
    #10 bcd = 4'b1001; 
    #10 $stop;
end
initial 
begin
    $monitor("Time=%0t | binary_input=%b | seg_output=%b", $time, bcd, seg);
end

endmodule
```
## Simulated Output

<img width="1919" height="1078" alt="Screenshot 2025-09-17 195017" src="https://github.com/user-attachments/assets/7ea13dda-fb35-4d04-be30-c3fa9fb4db06" />


---

## Conclusion
In this experiment, a seven-segment display driver was successfully designed and simulated using Verilog HDL. The simulation results confirmed that the display correctly represented the digits 0 to 9 based on the 4-bit binary input. The testbench effectively verified the functionality of the seven-segment display by applying various input combinations and observing the corresponding segment outputs.

This experiment highlights how Verilog HDL can be used to control hardware components like a seven-segment display in digital systems.
