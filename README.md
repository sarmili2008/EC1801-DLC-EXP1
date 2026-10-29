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

## Verilog Program
```
module boolean(
       input wire a,b,
       output wire y
);
       assign y = (~a)|b;
endmodule
```


## TestBench Program

```

module tb;
reg a, b;
wire y;
boolean uut (.a(a), .b(b), .y(y));
initial begin
        // ---- VCD dump setup ----
        $dumpfile("boolean.vcd");   // name of the VCD file to be generated
        $dumpvars(0, tb);   // dump all signals in this testbench hierarchy

	$monitor("a=%b b=%b y=%b", 
	a,b,y);
	a=0; b=0; #10;
	a =0; b=1; #10;
	a =1; b=0; #10;
	a =1; b=1; #10;
	$finish;
	end
endmodule

```





    
## Truth Table
 

<img width="1532" height="158" alt="Screenshot 2026-10-27 083420" src="https://github.com/user-attachments/assets/16c67a19-7d76-4058-8111-cb9286c1ddb9" />

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

## OUTPUT

<img width="1128" height="180" alt="Screenshot 2026-10-27 083441" src="https://github.com/user-attachments/assets/a9be0be9-e949-43de-a477-b4d75cbe654f" />


The design was compiled and simulated using Synopsys VCS, and the functionality was verified using DVE waveform analysis.


Result
Thus, the Boolean function was minimized, implemented using Verilog HDL, successfully simulated using Synopsys VCS, and verified using Synopsys DVE.

