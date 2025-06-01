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
