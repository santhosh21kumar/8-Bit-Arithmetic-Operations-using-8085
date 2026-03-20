8-Bit-Arithmetic-Operations-using-8085
Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor. Apparatus Required: • Laptop with internet connection

Algorithm:
For Addition (With Carry Consideration):
Load the first number from memory location 4200H into register A.
Load the second number from memory location 4201H into register B.
Add the contents of registers A and B.
If carry is generated, store carry in 4301H.
Store the sum in memory location 4300H.
For Subtraction (Considering Greater Number):
Load the first number from memory location 4200H into register A.
Load the second number from memory location 4201H into register B.
Compare A and B.
If A < B, swap the values of A and B to ensure positive result.
Subtract the content of B from A.
Store the result in memory location 4300H.
For Multiplication:
Load the first number from memory location 4200H into register A.
Load the second number from memory location 4201H into register B.
Multiply A and B using repeated addition.
Store the result in memory locations 4300H and 4301H (if required for higher bits).
For Division:
Load the dividend from memory location 4200H into register A.
Load the divisor from memory location 4201H into register B.
Perform division using repeated subtraction.
Store the quotient in 4300H and remainder in 4301H.
Program:
; ---------- ADDITION ----------
LDA 4150H
MOV B,A
LDA 4151H
ADD B
STA 4152H

; ---------- SUBTRACTION ----------
LDA 4150H
MOV B,A
LDA 4151H
MOV C,A
MOV A,B
SUB C
STA 4153H

; ---------- MULTIPLICATION ----------
MVI A,00H
MVI D,00H
LXI H,0020H
MOV B,M
INX H
MOV C,M
MUL_LOOP: ADD B
JNC NO_CARRY
INR D
NO_CARRY: DCR C
JNZ MUL_LOOP
STA 0022H
MOV A,D
STA 0023H

; ---------- DIVISION ----------
LXI H,0020H
MOV A,M
INX H
MOV C,M
MVI D,00H
DIV_LOOP: CMP C
JC DIV_END
SUB C
INR D
JMP DIV_LOOP
DIV_END: STA 0025H
MOV A,D
STA 0024H

HLT
Output:
image image image image
➤ Final Output Summary
Operation	Input (Example)	Result (Hex)	Result (Decimal)
Addition	10, 2	0CH	12
Subtraction	10, 2	08H	8
Multiplication	10 × 2	14H	20
Division	10 ÷ 2	05H / 00H	5 Quotient / 0 Remainder
Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.
