# Current-mirror-comparison

This project will introduce a current mirror at different complexity levels. we will compare between a basic current mirror and cascode current mirror.

---------------------------------
For this project we will use TSMC 180nm technolodgy 

Our goal is to copy $1uA$ -> $1uA$ current with the below spec - 
* $I_{ref} = 1uA$
* $I_{out} = 1uA$
* $V_{VDD} = 1.8V$

### 1. Basic current mirror
 A basic current mirror consist of a diode-connected transistor (M1) connected to a 2nd transistor by its $V_{GS}$ voltage. 
 Described by the following basic equation -
 
  
  ![basic_cm](https://github.com/dsapir4422/Current-Mirrors-comparison/assets/87266625/67c109e3-aeac-4e78-9b63-4bd1ff0e7566)



 
 This basic circuit has 2 problems to solve:
 - Different in $V_{DS}$ due to channel length modulation
 - If Vout changing, Iout should not change
<img width="609" alt="normal_current-mirror_schematic (1)" src="https://github.com/user-attachments/assets/fc314786-8469-421b-bdb4-ccb521204071" />


In this basic circuit - $R_{out} = r_{o2}$, which is the right NMOS output resistance.

### 2. Cascode current mirror

From Sansen book  - 

<img src="https://github.com/dsapir4422/Current-Mirrors-comparison/assets/87266625/34d2de6c-10f9-4e9b-bb5a-e43c3341b4a7" alt="Image Alt Text" width="250" height="250" align="center" />

Adding a cascode device will increase output resistance by -  $R{out}$ = $g_{m2}$ * $r_{o2}$ * $r_{o4}$ which solves the 2 problems stated before, but Vout CM is very high -> $V_{out,min} = V_{gs}+V_{ov} = 2V_{ov} + V{th}$
 i.e not ideal to low power design
 
Simulated circuit DC point - 

<img width="493" alt="cascode_schemtaic" src="https://github.com/user-attachments/assets/4a5e5a96-58fe-4269-92c5-4c1c3e6afc1d" />


**Results summary**

Below is the schematic in ltspice to comapre between normal and cascode current mirror.

<img width="610" alt="cascode+normal current mirror_schematic (1)" src="https://github.com/user-attachments/assets/9ef6416e-1ca0-4481-860f-049fcb6248c7" />

We introduce Iout vs. Vout (Voltage as load) graph to compare between the different current mirrors. 

<img width="558" alt="cascode+normal current mirror" src="https://github.com/user-attachments/assets/a46130aa-d0d9-477f-bfe2-5a489791e1a5" />

From the plots, we observe that the normal current mirror has a lower output resistance but also a lower minimum voltage required for saturation. In contrast, the cascode current mirror exhibits a higher output resistance, but it also requires a higher minimum voltage to enter saturation. This means it needs a higher voltage to begin functioning effectively as a current mirror and produce the desired output.

Below is the result summary is a table

| Type of current mirror| Minimum voltage for saturation| output resistance | Accuracy |
| :---:  | :-: | :-: | :-: |
| Normal current mirror| $V_{out,min} = V_{ov}$| low($g_{m}$ * $r_{o}$)| low |
| Cascode current mirror| $V_{out,min} = V_{gs}+V_{ov} = 2V_{ov} + V{th}$ |high($g_{m}$ * $r_{o}$ * $r_{o}$)| high |
