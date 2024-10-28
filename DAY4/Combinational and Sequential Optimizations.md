 <details> 
<summary> DAY 3 - Combinational and Sequential Optimizations </summary>

## DAY 3 - Combinational and Sequential Optimizations

### Intro to optimizations

#### Combinational Logic Optimisation:
#### Why Combinational Logic Optimisation?

-> Squeezing the logic to get the most optimised design (in terms of Area and Power savings- PPA)
#### Technique used for combinatinal optimisation:
1. Constant propogation.
2. Boolean logic optimization.
#### 1. Constant Propagation: 
This is direct optimisation technique using boolean expression.

![D4 1](https://github.com/user-attachments/assets/c97bad5a-6062-4fac-8847-eed1a6830bfa)

#### 2. Boolean Logic Optimizations: 
This using K-map and Quine Mckluskey and boolean expression methos to optimize the logic.

#### Sequential Logic Optimisation:
#### Basic:
1. Sequestianl constant propogation.
#### Advance:
1. State optimization.
2. Retiming.
3. Sequential logic cloning.
   
#### Sequestianl constant propogation:
Output can be constant irespective of reset and clock.

![D4 2](https://github.com/user-attachments/assets/a681c80f-266c-4684-91c2-ddfdc474425f)

Note: Every flop if D input tied off is not a sequential constant and Q pin always take a constant value as shown below .

![D4 3](https://github.com/user-attachments/assets/be026de0-36b3-41d1-8a29-837dd70e8914)

#### State optimization:
Optimization of unused stae in the finate state meachine.
#### Cloning:
#### Retiming:
Spliting the logic equally to match the timing.
![D4 4](https://github.com/user-attachments/assets/0cd25c1b-3dd8-4d02-9450-9cd239d6c191)


## DAY 3 - Combinational Lab 1
###### Code we are using for optimizing.
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule
###### Invoke the YOSYS tool.
###### Read the library.
###### Read the verilog.
###### Synthsise the code.
![D4 5](https://github.com/user-attachments/assets/e2bd3d9c-e74b-44de-82a2-01e90746a3bb)

###### To optimze use the command below.
![D4 6](https://github.com/user-attachments/assets/47696fb7-47bd-4228-9062-76295fdca668)

###### It has been optimized to AND gate.
![D4 8](https://github.com/user-attachments/assets/7648bf50-2e33-4ef9-a846-6237105f5d35)
![D4 7](https://github.com/user-attachments/assets/c6f1d89f-8dee-441c-8072-48fb4f686fa9)

## DAY 3 - Combinational Lab 2
###### Code we are using for optimizing.
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
###### Invoke the YOSYS tool.
###### Read the library.
###### Read the verilog.
###### Synthsise the code.
![D4 9](https://github.com/user-attachments/assets/3ad08aec-769d-4c81-9bbf-edec4e10219d)

###### To optimze use the command below.
![D4 10](https://github.com/user-attachments/assets/cc57457d-ba58-42ce-a17b-5f12ca465baf)

###### It has been optimized to OR gate.
![D4 11](https://github.com/user-attachments/assets/9046233f-725d-4c8b-9fd2-3612c4d099d8)

## DAY 3 - Combinational Lab 3
###### Code we are using for optimizing.
![D4 12](https://github.com/user-attachments/assets/3f54c452-c533-4035-9a64-7018d13218a4)

###### Invoke the YOSYS tool.
###### Read the library.
###### Read the verilog.
###### Synthsise the code.
![D4 13](https://github.com/user-attachments/assets/5eebd254-5919-47e2-b863-73982686b920)

###### To optimze use the command below.
![D4 10](https://github.com/user-attachments/assets/cc57457d-ba58-42ce-a17b-5f12ca465baf)

###### It has been optimized to 3 input AND gate.

![D4 14](https://github.com/user-attachments/assets/29bbfbc0-fe6f-4a44-b887-72a2bdf76e84)
![D4 15](https://github.com/user-attachments/assets/f3641f06-87c5-44f6-b27e-42b15994b950)

## DAY 3 - Combinational Lab 4
###### Code we are using for optimizing.
![D4 16](https://github.com/user-attachments/assets/922ca49b-0504-476d-a6d0-fd80f0584f90)

###### Invoke the YOSYS tool.
###### Read the library.
###### Read the verilog.
###### Synthsise the code.
![D4 17](https://github.com/user-attachments/assets/4daae1ce-c196-447f-882b-03db507a52f1)

###### To optimze use the command below.

![D4 10](https://github.com/user-attachments/assets/cc57457d-ba58-42ce-a17b-5f12ca465baf)

###### It has been optimized.

![D4 18](https://github.com/user-attachments/assets/f1f57425-257f-4beb-b375-6b13221fdd0f)


## DAY 3 - Sequential Lab 1
![D4 25](https://github.com/user-attachments/assets/e3d08d94-33a2-4c41-97cd-ba2073ab9781)
![D4 24](https://github.com/user-attachments/assets/f6a40c37-fc1b-49b7-ae3c-c6d837b4ddd8)
![D4 23](https://github.com/user-attachments/assets/63093181-b757-4eaf-9b44-2a765a0ee73a)
![D4 22](https://github.com/user-attachments/assets/07f24942-462c-4074-89d9-063efca7e9df)
![D4 21](https://github.com/user-attachments/assets/00746fbf-1677-4f4a-ae7c-ea23351c99a4)
![D4 20](https://github.com/user-attachments/assets/6d0fe4e7-228a-49eb-826a-0e56cd180622)
![D4 19](https://github.com/user-attachments/assets/205d1287-da3a-41d8-ac21-e1ffbfe69059)


## DAY 3 - Sequential Lab 2

![D4 30](https://github.com/user-attachments/assets/b237d8ee-6398-47f1-a7d1-1d3eea7f0144)
![D4 29](https://github.com/user-attachments/assets/384c1c9a-549d-48bf-bc0e-90e2d2304d3e)
![D4 28](https://github.com/user-attachments/assets/d7cbd1d0-2b77-4a5e-8ca6-464e872d779a)
![D4 27](https://github.com/user-attachments/assets/f7a05db4-8f87-408b-b00e-ec287592815f)
![D4 26](https://github.com/user-attachments/assets/49b52636-fa91-414e-a888-b522e09b5660)

## DAY 3 - Sequential Lab 3
#### Unused Output Optimization:
![D4 34](https://github.com/user-attachments/assets/c1faacf5-142a-4ac0-88e1-2bccb035d1de)
![D4 33](https://github.com/user-attachments/assets/0bde6949-6aaa-4e53-b9c9-b22b011da837)
![D4 32](https://github.com/user-attachments/assets/13a83fc5-ec98-40c8-8d68-19d42fc5980f)
![D4 31](https://github.com/user-attachments/assets/15fbb27d-c3d5-4ff6-aeeb-81cfd2f9b2e3)
#### After mofifying above code:

![D4 37](https://github.com/user-attachments/assets/bff97dbf-8de2-446e-8fb9-6879d4357624)
![D4 36](https://github.com/user-attachments/assets/47bbfe56-0854-4255-bf11-a15b9dcbbd25)
![D4 35](https://github.com/user-attachments/assets/a23b9096-6c94-48fd-a14c-3170f8c489f1)
 </details> 
