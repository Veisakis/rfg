# PQ Curve
Developed for DigSilent PowerFactory 15.1 .

This script runs multiple loadflows by varying the active power setting of the selected generators and calculates the resulting active and reactive power flow on the Point of Common Coupling (PCC).

These values of P,Q are plotted in a graph along with the required boundary as depicted in the RfG 'IPTO Regulation (EU) 631/2016'.

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/40bbc9e5-20af-41b1-a3c3-d5b551704f2a" />

## Initial Setup
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/8ab11774-0347-48bc-856e-c5076567e50f" />

Open Data Manager
- Create a new Study Case
- Create a DPL Command (ComDPL) in that Study Case
- Select the Generators involved in the RfG Study, define a DPL Commands Set and rename it as 'GENERATORS'

Select DPL Script
- Create a Loadflow Calculation (ComLdf) with the parameter 'Consider Reactive Power Limits' enabled and rename it as 'LOADFLOW'
- Create a Results file (ElmRes) and rename it as 'RESULTS'
- Create two vectors, rename them as 'RFG_P_VECTOR' and 'RFG_Q_VECTOR' and insert the values for the nominal boundary as described in the RfG Regulation

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/f192020e-737a-46a5-a34c-3bbd413f98ae" />

Edit DPL Script
- Edit the script and select the DPL Commands Set in the 'General Selection' field
- In the input parameters field, create two variables of type int named N_GEN and IS_PV. The value of N_GEN should equal the number of generators selected and IS_PV should equal to '1' if the generators are PV
- In the external objects field, select the busbar which is considered the PCC and name it 'PCC'
- In the Advanced Options tab, create four variables of type double and rename them as 'RFG_P', 'RFG_Q', 'PCC_P', 'PCC_Q' and of unit 'p.u.'
- In the Script tab, paste the script

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/e9cbd6ad-b862-4870-a0ea-a6b882286816" />

New Graph
- Create a new XY graph and select for the first curve 'RFG_P' and 'RFG_Q' variables for the Y,X values
- Create a new XY graph and select for the first curve 'PCC_P' and 'PCC_Q' variables for the Y,X values

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/7b1a0162-35a5-4842-ae9b-562d58c792e8" />

