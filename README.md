# 8085 Microprocessor - 8-Bit Arithmetic Operations  

## Aim  
To perform 8-bit arithmetic operations (**Addition, Subtraction, Multiplication, and Division**) using the 8085 microprocessor.  

---

## Apparatus Required  
- Laptop with Internet connection  

---

## Algorithm  
1. Load the first and second numbers from memory.  
2. Perform the selected arithmetic operation (Add / Subtract / Multiply / Divide).  
3. Store the result in the specified memory location.  
4. Halt the program.  

---

## Program with Output  
```asm
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
```
## ➤ Final Output Summary  

| Operation       | Input (Example) | Result (Hex) | Result (Decimal) |
|-----------------|-----------------|--------------|------------------|
| Addition        | 10, 2           | 0CH          | 12               |
| Subtraction     | 10, 2           | 08H          | 8                |
| Multiplication  | 10 × 2          | 14H          | 20               |
| Division        | 10 ÷ 2          | 05H / 00H    | 5 Quotient / 0 Remainder |



<img width="679" height="348" alt="image" src="https://github.com/user-attachments/assets/72034db1-02f5-450d-9cf7-201c836aadbf" />
<img width="663" height="311" alt="image" src="https://github.com/user-attachments/assets/38a77aa5-375b-41bd-8241-7b5e1792d4ab" />
<img width="664" height="308" alt="image" src="https://github.com/user-attachments/assets/164a09d1-8603-4765-8d36-bfc153496781" />
<img width="662" height="315" alt="image" src="https://github.com/user-attachments/assets/179f4a51-fdf8-4417-b0ac-2e5698c669c6" />



