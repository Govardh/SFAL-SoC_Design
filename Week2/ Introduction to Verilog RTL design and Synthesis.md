<details>
    <summary>Day 1: Introduction to Verilog RTL design and Synthesis</summary>
    <ul>
        <li>
            <details>
                <summary>Lab using Iverilog and GTKWave</summary>
                <pre>
Load mux & its testbench to Iverilog.

![Day1-iverlog](https://github.com/user-attachments/assets/56b62b0d-78b7-43dd-89ed-c05dfb55696f)

a.out file is executed and Load the .vcd file into GTKWave generator.

![day1_gtkwave](https://github.com/user-attachments/assets/8698f384-181f-4479-b740-b05a780cc488)

 </pre>

  </details>
        </li>

  <li>
            <details>
              
  <summary>Lab using Yosys & Logic Synthesis</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: Realising the Logic and Generating Library Specific Design</summary>
                            <pre>
Invoke Yosys by using command yosys.

  ![Ysoys](https://github.com/user-attachments/assets/53ddb340-d42f-4516-839d-6992622a2651)


</pre>
                            <pre>
Read the library using read_liberty.
 
                              
  ![Day1_reading from lib(1)](https://github.com/user-attachments/assets/6de91a21-c088-4667-895e-d5e210802de6)
                            </pre>
                            <pre>
Read the design using read_verilog.
![day1_(2)](https://github.com/user-attachments/assets/088b66d9-770d-46ef-91ef-1946f217f3a4)

  </pre>
                            <pre>
Define the module that needs to be synthesized.

![day1-(4)](https://github.com/user-attachments/assets/e3a2408f-92c6-494a-b483-967bfafc7257)
![day_1(3)](https://github.com/user-attachments/assets/9318d929-800f-41a3-97a7-23538612e46a)
                            </pre>
                            <pre>
Use command show to view the design.
![day1_(5)](https://github.com/user-attachments/assets/9d3a3ca8-87df-4dba-8edb-2fc6fcb357c8)

   </pre>
                            <pre>
Generate the netlist using abc command.

  ![abc ](https://github.com/user-attachments/assets/c12406e8-bb34-44f3-b0ee-a81c84d99248)

    
  </pre>          
                        </details>
                    </li>
                </ul>
                <ul>
                    <li>
                        <details>    
                            <summary>PART 2: Write the netlist & Modify to View Without Additional Attributes</summary>
                            <pre>
Write the netlist using command 'write_netlist'.

![day1_(6)](https://github.com/user-attachments/assets/f4cbf78f-3fb4-45f1-af51-c587cadb5a9d)
      
  </pre>
                            <pre>
View the netlist using command '!gvim'
The Generated Netlist:

![day1_7](https://github.com/user-attachments/assets/59d989e0-3f65-4991-abd3-f3d25e92e745)


   </pre>
                        </details>
                    </li>
                </ul>
            </details>
        </li>
    </ul>
</details>
