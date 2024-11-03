<details> 
<summary> Day1 : Intoduction to logic synthesis</summary>
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
