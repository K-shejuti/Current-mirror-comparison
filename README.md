# Current-mirror-comparison

This project will introduce a current mirror at different complexity levels. we will compare between a basic current mirror, cascode current mirror.

---------------------------------
For this project we will use TSMC 180nm technolodgy 

Our goal is to copy $1uA$ -> $1uA$ current with the below spec - 
* $I_{ref} = 1uA$
* $I_{out} = 1uA$
* $V_{VDD} = 1.8V$

### 1. Basic current mirror
 A basic current mirror consist of a diode-connected transistor (M1) connected to a 2nd transistor by its $V_{GS}$ voltage. Described by the following basic equation -
