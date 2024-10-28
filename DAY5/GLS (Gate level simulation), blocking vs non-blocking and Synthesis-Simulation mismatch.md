 <details> 
<summary> Day 4 - GLS (Gate level simulation), blocking vs non-blocking and Synthesis-Simulation mismatch </summary>
	 
## Day 4 - GLS (Gate level simulation), blocking vs non-blocking and Synthesis-Simulation mismatch

### Gate level simulation (GLS) :
#### What is GLS?
Running test bench wiht Netlist as design under test.
#### Why is GLS?
1. To verify the logical corrects of design after synthesis.
2. Ensuring the timing of the design is met.
![D5 1](https://github.com/user-attachments/assets/18938211-964e-4764-aaa4-46d1408c0159)
![D5 2](https://github.com/user-attachments/assets/f2c00001-baf8-44ee-82bc-68bb72283181)

#### Why we need to validate the functinality of the Netlist?
Because there could be synthesis and simulation mismatch.

### Synthesis simulation mismatch :
#### Simulation mismatch happens becuse of following reasons.
1. Missing sensistivity list.
2. Blocking vs Non blocking assignment.
3. Non standard verilog coading.

### Missing sensistivity list :
In verilog code we need to take care of the providing sensistivity list.
![D5 3](https://github.com/user-attachments/assets/0c0bcf1b-2c12-4be7-8fa5-eddedde7b84d)
In simulation time it looks like double edge flop.
In synthesis it looks line mux.

### Blocking vs Non blocking assignment :
In side always block we use blocking and non clocking state ments.
#### Blocking (=):
Here the blocking stesments are executed in the sequesntial manner.
Use always non blokcing with sequential circuit.
![D5 6](https://github.com/user-attachments/assets/b65e114c-4262-431e-8d5f-22d6c25d8ae2)
![D5 5](https://github.com/user-attachments/assets/9fd96be4-4ad7-4ca8-aecb-6e7994c9bc8b)
![D5 4](https://github.com/user-attachments/assets/67fc3f42-575e-4cae-8022-4d2bda2a7768)


#### Non Blocking (<=):
Here executes all the RHS and assigned to LHS means non blocking statements are executed in the parllel.

## DAY 4 - GLS Lab 1
![D5 10](https://github.com/user-attachments/assets/49eecd6b-38e9-497b-8e00-ac6cf1bc971d)
![D5 9](https://github.com/user-attachments/assets/f761de75-c959-468c-bd0a-bc52afe2d788)
![D5 8](https://github.com/user-attachments/assets/0a28950d-1897-43db-9df9-a56cd7b922aa)
![D5 7](https://github.com/user-attachments/assets/32a980f0-bb0f-4eff-bd03-141661c4196c)
#### Do GLS:

![D5 latest](https://github.com/user-attachments/assets/273dedbb-62b1-4dc1-9fa6-83c21a2f094b)


## DAY 4 - GLS Lab 2
![D5 13](https://github.com/user-attachments/assets/713ee2fd-6401-49c2-88be-3767f81b9f9b)
![D5 12](https://github.com/user-attachments/assets/06795c1e-08d8-4ceb-a526-159e748d6987)

#### Do GLS:
Synsthesis simulation miss match.
![D5 14](https://github.com/user-attachments/assets/63eb1c56-56fb-48d1-bc86-24b5f0e3749f)


## DAY 4 - GLS Lab 3
![D5 18](https://github.com/user-attachments/assets/e3df95f0-dedd-4a14-9929-21bb6359e686)
![D5 17](https://github.com/user-attachments/assets/d723a09f-1325-401d-b590-d524a988d89f)
![D5 16](https://github.com/user-attachments/assets/9da2d8ee-4fe5-47ba-b547-3f1995c44d7b)
![D5 15](https://github.com/user-attachments/assets/dc282b90-e45a-4b3e-adb3-3b4b85b295c6)

#### Do GLS:
![D5 19](https://github.com/user-attachments/assets/3d803c5c-3bee-4553-ba11-9b9469317557)


 </details>
