# EC1801-DLC-EXP1
### EXPERIMENT 1 
### MINIMIZATION AND IMPLEMENTATION OF BOOLEAN FUNCTION
## Aim
To minimize and implement a Boolean function using logic gates and verify the functionality using Synopsys VCS and DVE.
## Software Required
•	Synopsys VCS
•	Synopsys DVE
•	Linux Terminal
•	Verilog HDL
## Boolean Function
Consider the Boolean function:
F(A,B)=Σm(0,1,3)
The minimized Boolean expression is: F=B'D'+BD
The function is implemented using Verilog HDL.
## Files Used
File	Description
exp1_boolean_min.v	Verilog design file
exp1_boolean_min_tb.v	Verilog testbench
exp1_boolean_min.vcd	VCD waveform dump generated during simulation

## Verilog Program
module fun (
input wire A, 
input wire B, 
output wire F 
); 
assign F = (~A) | B ;    // F = A' + B 
endmodule


## TestBench Program



module tb;
    reg A, B;
    wire F;
    // Instantiate the design under test (DUT)
    fun uut (
        .A(A),
        .B(B),
        .F(F)
    );



    
## Truth Table
 
<img width="795" height="311" alt="image" src="https://github.com/user-attachments/assets/dd4ba5b9-016b-4ae5-a693-f309c60c4c0e" />

## Simulation Procedure
STEP 1 – Open Terminal
Open a terminal in the experiment folder.
bash

STEP 2 – Load Synopsys Environment
source /synopsys/start.sh

STEP 3 – Compile Using VCS
vcs exp1_boolean_min.v exp1_boolean_min_tb.v -full64
 
If compilation is successful, VCS generates the simulation executable:
simv

STEP 4 – Run Simulation
./simv
The terminal displays the input combinations and corresponding output F.
A VCD waveform file is also generated:
exp1_boolean_min.vcd

STEP 5 – Open DVE
dve -full64
Other option
dve -full64 &
A DVE environment will open.

## DVE Waveform Verification
In DVE:
1.	Open the testbench hierarchy.
2.	Locate the signals:
o	A
o	B
o	C
o	D<img width="607" height="388" alt="image" src="https://github.com/user-attachments/assets/912abb13-079c-4a3a-b28e-714cbc65f9a6" />

o	F
3.	Add the signals to the waveform window.
4.	Run/inspect the waveform.
5.	Verify that F = 1 whenever B and D are equal.
6.	Verify that F = 0 whenever B and D are different.
The waveform should agree with the truth table.
 
### Expected Result
The Boolean function
F(A,B)=Σm(0,1,3), which simplifies to F=: F=A'+B
was minimized to F=: F=A'+B.
and successfully implemented using Verilog HDL.

## OUTPUT

<img width="1600" height="900" alt="WhatsApp Image 2026-11-02 at 11 53 25 AM" src="https://github.com/user-attachments/assets/dcc8b8b5-f87c-499b-85d6-ec8561789143" />


The design was compiled and simulated using Synopsys VCS, and the functionality was verified using DVE waveform analysis.


Result
Thus, the Boolean function was minimized, implemented using Verilog HDL, successfully simulated using Synopsys VCS, and verified using Synopsys DVE.

