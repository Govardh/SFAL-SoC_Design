<details>
<summary> Basics of STA </summary>
  
Min and Max Delay

<img width="719" alt="STA_1" src="https://github.com/user-attachments/assets/24b33a40-1bc4-49fc-9c75-87064450697a">

Delay:

*delay is a function of input transition and load capacitance.

*Delay of any gate is function of input transition and out put load.

*Where load is not only because of leangthy nets and also depends on number of load connected to it.

<img width="951" alt="bucket_" src="https://github.com/user-attachments/assets/55564053-200f-4770-bb49-debd51b6e69a">


<img width="722" alt="STA_2" src="https://github.com/user-attachments/assets/a54e09eb-3b5f-4d8c-b097-025ff2f379be">

<img width="722" alt="STA_3" src="https://github.com/user-attachments/assets/d5d11090-90cb-4e05-8e58-0b387b961825">

<img width="719" alt="STA_4" src="https://github.com/user-attachments/assets/0573fd3c-a2d5-4354-b382-32c52b1ee746">

<img width="721" alt="STA_5" src="https://github.com/user-attachments/assets/4267556b-eec8-47ba-9118-83ea6cad5c21">

<img width="718" alt="STA_6" src="https://github.com/user-attachments/assets/5fe9b614-5f2c-4aa7-aca1-1c0fe3937d02">

<img width="722" alt="STA_7" src="https://github.com/user-attachments/assets/3930a33d-cb52-4df3-879b-207729915022">

<img width="716" alt="STA_8" src="https://github.com/user-attachments/assets/db2fe7d9-1610-48c6-8cc6-cd3b8ef71c4a">

</details>
<details>
<summary>.lib_LAB</summary>
default_max_transition : 1.5000000000;

  
Load capacitance is depends on output capacistance, net capacitance and input capacitance of other gate.
This may incress the load capacitance this may leads to incress the transition.

<img width="814" alt="library_lab" src="https://github.com/user-attachments/assets/caa82235-6d58-461f-b324-7226a0a0dea3">

<img width="719" alt="next to flling edge" src="https://github.com/user-attachments/assets/e7c859a9-37e3-48f2-8f87-266dd6cb9154">

Delay Model Look Up Table:
It contains the delay information base on the Input transition and Output load.
Based on tranition and load DC will calculate the delay of the gate.

<img width="720" alt="Delay_model_table" src="https://github.com/user-attachments/assets/942c6d9b-5813-4246-bdf4-f547defc02cc">

Unetness:

OR and AND gate ---> have positive unetbess.

NOT, NAND and NOR--->negative unetness.

XOR ---->both positive and negative unetness.

<img width="602" alt="unateness_" src="https://github.com/user-attachments/assets/5d127f28-c4e1-41a2-ad67-653b932a37c1">


<img width="821" alt="unate" src="https://github.com/user-attachments/assets/f4b54548-4e9c-43c1-9954-bba5099a93fa">


<img width="719" alt="next to flling edge" src="https://github.com/user-attachments/assets/e7c859a9-37e3-48f2-8f87-266dd6cb9154">



  
</details>
