# how to run the code

### 1. run the simulation (may take one day to complete) .
### 2. go to the simulation directory, issue the command in MATLAB:

```matlab
addpath ..
```

by doing this, the parent folder with all the post-processing m files are included in the enviromental variables.

### 3. run read_analysis.m


GENERAL NOTICE
1. it is noticed that choosing a normal compressbility for matrix and
liquid would cause error, if liquid water saturation is low. this is 
because liquid water pressure can reduced down to 1e-11 pa, if this 
pressure multiplies a storativity 1e-4. There is large amount
of water in unsaturated zone.

2. There is a issue on bcop output. specifically, terms associated with
pressure are calulated based on current time step i.e., qin=gnup(pbs-pvec), which terms
associated with concentration are calculated based on the previous time step. i.e., 
qinc=gnup(bps-piter). This may cause non-consistency at one step when pbc is experiencing
significant change. also this is the reason why solute mass balance in fort.21 is not 
correct. (but water mass is excellent!)

3. a set of parameters that can properly simulate salt precipitation
'FREUNDLICH' 1.D-47 0.05
it is been tested for simulation over 120 days using Peva. as 15mm/day
it is found that 
'FREUNDLICH' 2.D-45 0.05 
can properly approximate solid2000, but the curve is too steep at the end so 
artifitial evaporation spike may occur

4. When applied evaporation rate is above 8mm/day, artificial 
recharge could occur when tide retrieve in which a recharge moves all the way up to the supratidal zone. 
The way of preventing such recharge is to ensure nonlinear iteration is enabled.

