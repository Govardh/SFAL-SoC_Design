<details>
    <summary>Day 2: Timing Libs, Hierarchial vs Flat Synthesis & Efficient Flop Coding Styles and Optimization </summary>
    <ul>
        <li>
            <details>
                <summary>Introduction to Timing .libs</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: Understanding the name of .libs</summary>
                            <pre>
View the library using 'gvim'.
                                
![week2 1](https://github.com/user-attachments/assets/edce5b75-e857-4554-aedd-3c5b163795ae)

   </pre>
                            <pre>
Reading the library name contain following information.
From the name, 
'130' technology node '130nm',
 tt_025C_1V80 - referes to PVT cornner
'tt' typical type library,
'025C' referes to temperature, &
'1v80' refers to the voltage.
These give us the operating conditions of the cells in the library
In .lib we have following informtion:
Tells about technology lis CMOS.
Delay module look up table.
Time unit 1ns.
Voltage unit 1v.
Leakage power unit 1nW.
Current unit 1mA.
Pulling resistance unit 1kohm.
Capacitive load unit pf.
Operation condition.
                            </pre>          
                        </details>
                    </li>



   <li>
            <details>
                <summary>Hierarchial vs Flat Synthesis</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: Hierarchial Synthesiss</summary>
                            <pre>
Read the library
  
![Day1_reading from lib(1)](https://github.com/user-attachments/assets/b0f27ed4-009b-4648-b53e-036fd8381304)
                            </pre>
                            <pre>
Read the verilog file

![d2 2](https://github.com/user-attachments/assets/5b87408c-8304-4929-945a-3bce5f74065f)
                            </pre>          
                            <pre>
Define the module to be synthesized 

![d2 3](https://github.com/user-attachments/assets/3328eb74-201f-456d-a0e2-110862710d79)

View the design hierarchy:

![d2 4](https://github.com/user-attachments/assets/31985fb0-3531-4029-9fc3-441a178e2fa4)
                            </pre>
                            <pre>
Generate the netlist
 ![d2 13](https://github.com/user-attachments/assets/f6955330-81dd-4aad-bc52-9fb5a322e0f9)
                            </pre>
                            <pre>
run command 'show' to view the design
![d2 6](https://github.com/user-attachments/assets/1b2799a0-ae8c-4acd-9c2b-67fa6ceb3f43)
As both submodule 1 and submodule 2 are instantiated seperately, hierachy is maintained and such design is a Hierarchial Design.
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 2: Flat Synthesis</summary>
                            <pre>
run command 'flatten' to write a flat netlist

![d2 7](https://github.com/user-attachments/assets/373510fe-b136-43ae-91de-66fa8dc86be9)
                            </pre>
                            <pre>
Write the netlist to a .v file

![d2 8](https://github.com/user-attachments/assets/4ab288d0-8ac6-4c39-ad34-d9a4d95a7f16)
                            </pre>
                            <pre>
View the netlist

![d2 9](https://github.com/user-attachments/assets/ae23591c-4ebc-458e-ba2f-514ada34c3de)
As we can see the sub-modules don't appear in the netlist indicating that the design has been flattened out
                            </pre>
                            <pre>
Run command 'show' to view the flattened module

![d2 10](https://github.com/user-attachments/assets/66708084-01d2-4ad3-970f-4eaab9f2ae3e)
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 3: Sub-Module Level Synthesis</summary>
                            <pre>
Read library

![d2 11](https://github.com/user-attachments/assets/60f7494e-2cb5-49ff-a4ad-b04148df8a3a)

   </pre>
                            <pre>
Read Verilog

![d2 12](https://github.com/user-attachments/assets/fc83fe87-1ef8-4b85-9ec7-1fb0c5c6644b)
                            </pre>
                            <pre>
Synthesize at sub module level using 'synth -top'

![d2 14](https://github.com/user-attachments/assets/df8f8bd5-4895-4620-9ca3-6726bb8576b2)
                            </pre>
                            <pre>
Generate the netlist
![d2 13](https://github.com/user-attachments/assets/f6955330-81dd-4aad-bc52-9fb5a322e0f9)

  </pre>
                            <pre>
Run show command

![d2 15](https://github.com/user-attachments/assets/731bb1b9-31cc-443e-bdb8-ff6a5081fe02)


Multiple Instances: Such module level synthesis is done when multiple instances of the 
same module are used in the top level design.
Divide & Conquer: If you have a massive design, this type of synthesis can be done to 
generate multiple understandable netlists that can be stitched together.
                            </pre>
                        </details>
                    </li>
                </ul>
            </details>
        </li>




  <li>
            <details>
                <summary>Flop Coding Styles</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: Different Flip Flops</summary>
                            <pre>
Run iverilog for an Asynchronous Reset D-Flip Flop using its testbench
                            </pre>
                            <pre>
Execute the output file (a.out)

![D3 1](https://github.com/user-attachments/assets/576e55ac-4733-4c89-874e-12aab57a9b8e)
             </pre>          
                            <pre>
Run GTKWave to view the behaviour of the Asynchronous Reset D-Flip Flop
Observe the behaviour of the Asynchronous Reset D-Flip Flop

![D3 2](https://github.com/user-attachments/assets/f1f777fc-3612-4ce9-9044-10258b98e2f9)
                </pre>
                            <pre>
Repeat Steps 1-3 using the Asynchronous Set D-Flip Flop

![D3 3](https://github.com/user-attachments/assets/d0e583ca-5d8a-4fc5-9ddb-5f1226bd99c9)
                            </pre>
                            <pre>
Observe the behaviour of the Asynchronous Set D-Flip Flop

![D3 4](https://github.com/user-attachments/assets/c6ca6d88-44b6-402e-ab3a-2e70da988635)
                            </pre>
                            <pre>
Repeat Steps 1-3 using the Synchronous Reset D-Flip Flop

![D3 5](https://github.com/user-attachments/assets/1ad515f7-b4b3-4f84-9d31-6df76c30b743)
                            <pre>
Observe the behaviour of the Synchronous Reset D-Flip Flop

![D3 6](https://github.com/user-attachments/assets/5a9b4e6f-246b-4a9e-bd5d-8cb856116ef7)
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 2: Flop Synthesis</summary>
                            <pre>
In Yosys, read the library
Read the verilog file for Asynchronous Reset for D-Flip Flop
Define the module to be sunthesized

![D3 7](https://github.com/user-attachments/assets/d6921767-c4fb-49eb-81a1-05cf0934eda5)
                            </pre>
                            <pre>
Map  the flip flops in the library for synthesis

![D3 8](https://github.com/user-attachments/assets/bdfeeae1-91c0-4938-91ab-f634ca4407df)
                            </pre>
                            <pre>
Generate the netlist

![D3 9](https://github.com/user-attachments/assets/eb389f62-4775-4e44-9205-f86e5997ba70)
                            </pre>
                            <pre>
Execute show to view the netlist for the Asynchronous Reset D-Flip Flop

![D3 10](https://github.com/user-attachments/assets/926d2a11-aade-413b-9e8a-e722c33d5436)
    </pre>
                            <pre>
Execute show to view the netlist design for the Ashynchronous Set D-Flip Flop

![D3 11](https://github.com/user-attachments/assets/3686bb9f-b321-4a74-a4cc-534f3a9ac85a)
                            </pre>
                            <pre>
Execute show to view the netlist design for the Synchronous Reset D-Flip Flop

![D3 12](https://github.com/user-attachments/assets/c11346f5-988d-49f0-a6c1-140cfae97635)
                            </pre>
                        </details>
                    </li>
                </ul>   
<details>
                <summary>Special Case Optimizations</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: mul2 Synthesis</summary>
                            <pre>
In Yosys, read the library
Read the verilog file for mult_2
Define the module to be synthesized
                                
![D3 13](https://github.com/user-attachments/assets/fbb6483f-766e-402f-a66a-a9dae015339e)
                       </pre>
                            <pre>
Generate the netlist and notice the prompt to not call for abc as there are no cells to be synthesized

![D3 14](https://github.com/user-attachments/assets/c423f981-169b-486e-92a1-3b62d555de84)
                            </pre>
                            <pre>
Execute show to view the netlist design

![D3 15](https://github.com/user-attachments/assets/34d6a666-14b9-43b6-8532-8813fd9e3d2e)

   </pre>
                            <pre>
Write the netlist
View the netlist

![D3 16](https://github.com/user-attachments/assets/e3cc38c4-7030-46b3-8d6b-7c2c19346479)
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 2: mult8 Synthesis</summary>
                            <pre>
Read the verilog file for mult_8
Define the module to be sunthesized
Generate the netlist and notice the prompt to not call for abc as there are no cells to be synthesized

![D3 17](https://github.com/user-attachments/assets/c795828e-5122-4d7b-b292-e37f3dc1e2f8)

![D3 18](https://github.com/user-attachments/assets/8e4e86f6-f9f9-41a6-8b9f-a1cc9ccf7225)
                            </pre>
                            <pre>
Execute show to view the netlist design

![D3 19](https://github.com/user-attachments/assets/afba7be0-0166-4618-8638-6b02f542354b)

   </pre>
                            <pre>
Write the netlist
View the netlist

![D3 20](https://github.com/user-attachments/assets/5363dd02-e354-4bb0-9595-4aa78cfe1a71)

   </pre>
                        </details>
                    </li>    
                </ul>
            </details>
        </li>
    </ul>
</details>
