<details> 
<summary>Intoduction to logic synthesis</summary>
  
## Logic Synthesis
### What is synthesis?
RTL to gate level transistion is called synthesis.
Or converting design into gates and making connection between the gates.
The out put of the synthesis is called as gate levle Netlist.

<img width="595" alt="synthesis_1" src="https://github.com/user-attachments/assets/a6948943-6b02-4c0f-a606-b0e805f536a9">

### What is .lib?
It is a collection of logic modules incluedes logic gates. It contains information of standard cell like timing, area, power.<br>
It contains different flavors of same gates.<br>
Ex:<br>
2 input AND : slow, medium, fast.<br>
3 input AND : slow, medium, fast.<br>
4 input AND : slow, medium, fast.<br>

<img width="454" alt="Lib_2" src="https://github.com/user-attachments/assets/1ec4c8d5-f98b-4cab-b04d-3baaef5e1857">
<img width="594" alt="faster vs slower_3" src="https://github.com/user-attachments/assets/56084223-d904-41e8-93d6-2cec452a1da3">

In .lib it contain fast and slow working cells. We requires fast workign cells to meet setup and slow working cells to meethe hold requirement
<img width="695" alt="logic_synthesis_4" src="https://github.com/user-attachments/assets/0077acf1-7764-443e-bc58-56d0af4aa084">
<img width="659" alt="compriosn_5" src="https://github.com/user-attachments/assets/460b5fd6-656c-45bd-a709-e1fb5359062b">
</details>
<details>
<summary>Intro to DC</summary>
  
<img width="706" alt="DC_1" src="https://github.com/user-attachments/assets/970d26c2-4184-40fb-976f-a178bf85f561">

<img width="665" alt="DC_SET_UP_2" src="https://github.com/user-attachments/assets/568a7434-f540-4a00-a23d-8fca89fd203b">

<img width="683" alt="ASIC_FLOW_3" src="https://github.com/user-attachments/assets/2a754a14-2025-49b6-8a7f-317e27f4cdf6">

.LIB -->library which contains standard cells

DB  --> same as LIB but different format.  DC uses .db format for cell libraries

DDC --> format to store design information .DC can read and write out in .DDC

DESIGN --> RTL models
</details>
<details>
<Summary>DC LABS</Summary>
<img width="263" alt="shell_6" src="https://github.com/user-attachments/assets/4cd8db3d-9a03-420d-b016-25d5c31928ad">



<img width="251" alt="linklibrary_7" src="https://github.com/user-attachments/assets/4e6a53ca-e429-4dc2-9c9c-e7b68f24ac79">


<img width="614" alt="Netlist_8" src="https://github.com/user-attachments/assets/f11a1b35-2fe4-4ad1-99e8-48d7e9ea1501">
<img width="578" alt="synopsys_dc_9" src="https://github.com/user-attachments/assets/c6e86a6b-956e-46f2-9500-39c2a83fbaaf">
</details>
