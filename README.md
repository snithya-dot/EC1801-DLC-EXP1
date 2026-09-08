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
F(A,B,C,D)=Σm(0,2,5,7,8,10,13,15)
The minimized Boolean expression is: F=B'D'+BD
The function is implemented using Verilog HDL.
## Files Used
File	Description
exp1_boolean_min.v	Verilog design file
exp1_boolean_min_tb.v	Verilog testbench
exp1_boolean_min.vcd	VCD waveform dump generated during simulation

1. Verilog Design File
    //gedit exp1_boolean_min. v
   ```
   module boolean(
    input A,
    input B,
    input C,
    input D,
    output F
);

    assign F = (~B & ~D) | (B & D);

endmodule
```
2. Testbench
// gedit tb.v
```
module tb;

    reg A;
    reg B;
    reg C;
    reg D;

    wire F;

    exp1_boolean_min dut (
        .A(A),
        .B(B),
        .C(C),
        .D(D),
        .F(F)
    );

    initial begin

        $dumpfile("exp1_boolean_min.vcd");
        $dumpvars(0, tb);

        A=0; B=0; C=0; D=0; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=0; B=0; C=0; D=1; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=0; B=0; C=1; D=0; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=0; B=0; C=1; D=1; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=0; B=1; C=0; D=0; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=0; B=1; C=0; D=1; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=0; B=1; C=1; D=0; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=0; B=1; C=1; D=1; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=1; B=0; C=0; D=0; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=1; B=0; C=0; D=1; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=1; B=0; C=1; D=0; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=1; B=0; C=1; D=1; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=1; B=1; C=0; D=0; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=1; B=1; C=0; D=1; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=1; B=1; C=1; D=0; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        A=1; B=1; C=1; D=1; #10;
        $display("A=%b B=%b C=%b D=%b F=%b",A,B,C,D,F);

        $finish;

    end

endmodule
```

### Truth Table
A	B	C	D	F
0	0	0	0	1
0	0	0	1	0
0	0	1	0	1
0	0	1	1	0
0	1	0	0	0
0	1	0	1	1
0	1	1	0	0
0	1	1	1	1
1	0	0	0	1
1	0	0	1	0
1	0	1	0	1
1	0	1	1	0
1	1	0	0	0
1	1	0	1	1
1	1	1	0	0
1	1	1	1	1

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
o	D
o	F
3.	Add the signals to the waveform window.
4.	Run/inspect the waveform.
5.	Verify that F = 1 whenever B and D are equal.
6.	Verify that F = 0 whenever B and D are different.
The waveform should agree with the truth table.
 
### Expected Result
The Boolean function
F(A,B,C,D)=Σm(0,2,5,7,8,10,13,15), which simplifies to F=B'D'+BD.
was minimized to F=B'D'+BD.
and successfully implemented using Verilog HDL.


<img width="940" height="476" alt="image" src="https://github.com/user-attachments/assets/ae3b1554-b603-4184-b259-55e9f4a698d2" />


The design was compiled and simulated using Synopsys VCS, and the functionality was verified using DVE waveform analysis.
7. Viva-Voce Questions
1.	What is Boolean function minimization?
2.	What is a minterm?
3.	What is a Karnaugh map?
4.	Why is Boolean minimization required?
5.	What are universal gates?
6.	What is the difference between SOP and POS?
7.	What is the purpose of a Verilog testbench?
8.	Why is a VCD file generated?
9.	What is the purpose of ./simv?
10.	What is the purpose of DVE?
11.	What is the difference between simulation and synthesis?
12.	Why are A and C absent from the minimized expression?
13.	What is the purpose of $dumpfile?
14.	What is the purpose of $dumpvars?

Result
Thus, the Boolean function was minimized, implemented using Verilog HDL, successfully simulated using Synopsys VCS, and verified using Synopsys DVE.

