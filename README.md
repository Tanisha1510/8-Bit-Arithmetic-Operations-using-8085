# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.

## Apparatus Required:
	Laptop with internet connection

## Algorithm:

### For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
   
### Program:
```
LDA 4200H;
MOV B,A;
LDA 4201H;
ADD B;
STA 4202H;
JC STORE_CARRY;
HLT;
STORE_CARRY:MVI A,01H;
STA 4203H;
HLT;
```
### Output:
<img width="1920" height="1200" alt="Screenshot 2026-02-02 201544" src="https://github.com/user-attachments/assets/2eb12839-f020-404d-973e-4fb5f318df15" />

<img width="300" height="484" alt="Screenshot 2026-02-02 201643" src="https://github.com/user-attachments/assets/919e5ad9-ed5b-4251-a309-28cdba4c78f0" />

### Verification:
![IMG_20260203_093930](https://github.com/user-attachments/assets/bc37635c-6db1-498d-8798-91171d13b63b)

### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.

### Program:
```
LDA 3200H
MOV C,A
LDA 3201H
CMP C
JC SWAP
SWAP:
MOV B,A
MOV A,C
SUB B
STA 3202H
HLT
```
### Output:
<img width="1920" height="1200" alt="Screenshot 2026-02-02 202027" src="https://github.com/user-attachments/assets/22a98d3a-2966-4bef-b7c4-966811363050" />
<img width="295" height="443" alt="Screenshot 2026-02-02 202124" src="https://github.com/user-attachments/assets/2a41a3e5-ee63-4df2-9db4-025b6e4cac0a" />


### Verification:
![IMG_20260203_093911](https://github.com/user-attachments/assets/6ad03ff3-5fc4-4636-9b06-4ef2d1404704)

### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B,A
MVI A,00H
LOOP:ADD C
DCR B
JNZ LOOP
STA 4202H
HLT
```
### Output:
<img width="1920" height="1200" alt="Screenshot 2026-02-03 083328" src="https://github.com/user-attachments/assets/a749f9b9-c827-4690-af15-f15b7af0bd53" />
<img width="301" height="468" alt="Screenshot 2026-02-03 083412" src="https://github.com/user-attachments/assets/af4fa398-42b8-4564-8729-338651bedcf8" />


### Verification:
![IMG_20260203_093854](https://github.com/user-attachments/assets/ef0ed307-3100-4f09-80a2-fddbcf873f0b)

### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B, A
MVI A, 00H
LOOP: MOV A,C
CMP B
JC END
SUB B
MOV C,A
INR D
JMP LOOP
END: MOV A,D
STA 4202H
MOV A, C
STA 4203H
HLT
```
### Output:
<img width="1920" height="1200" alt="Screenshot 2026-02-03 084911" src="https://github.com/user-attachments/assets/2872ebf2-76ec-445e-9750-1e620b9a0313" />
<img width="297" height="490" alt="Screenshot 2026-02-03 085156" src="https://github.com/user-attachments/assets/27807b70-cf16-4c0d-9acb-282061265db3" />


### Verification:
![IMG_20260203_093825](https://github.com/user-attachments/assets/fdc2dd90-a2f1-4e96-bf83-dbd6308b87a2)

## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

