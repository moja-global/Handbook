Modules
=======

Carbon stocks are usually transferred from one pool to the other in nature. To move carbon between pools, FLINT uses **operations**.

A module is a self-contained set of operations designed to describe the processes driving carbon changes in a landscape across a specified period. The FLINT tool uses modules to simulate different environments and processes related to carbon transfer.

Modules manage state variables and carbon pools. State variables are variables used to represent environmental features like the height or age of a tree. At the same time, carbon pools are natural reservoirs or containers that hold carbon.

Modules collect data like climate or disturbance information to calculate changes in state variables and, more importantly, how much carbon has been transferred between pools as the simulation progresses. At the end of the simulation, the module outputs the updated version of state variables.

**Roth C Soil Model**

RothC is a module that simulates carbon turnover in non-waterlogged soil, allowing for the effects of soil type, temperature, moisture content, and plant cover on the turnover process. It uses a monthly time step to calculate total organic and microbial biomass carbon on a year to centuries timescale. The Roth C model requires a few readily accessible inputs. 

The RothC module runs in two modes:
Forward mode: This mode happens when the inputs or data that are known are used to calculate changes in soil organic matter 
Inverse mode happens when unknown inputs are calculated from known changes in soil organic matter.


**Chapman Richards Forest Model**

The Chapman Richards module is a tier 3 module. This tier 3 module uses the Chapman Richards equation to evaluate the greenhouse gas emissions and removals due to changes in the total quantity of carbon for forests. 

The Chapman Richards equation calculates the above-ground and below-ground biomass using the module. The Chapman Richards equation can be expressed mathematically below.

``AGC = * [ 1 - e ^ { -k *Age } ] ^ { ( 1 / (1-m) }``

Where :
- **AGC** is the Above-ground stand carbon (Tonne's carbon per hectare)
- **Max** is the Asymptote, which is the maximum peak carbon yield (Tonne's carbon per hectare)
- **k** is the parameter used in modeling tree growth. This parameter is dimensionless therefore having no physical unit
- **age** is the age of the forest in years 
- **M** is the parameter used in modeling tree growth. This parameter is dimensionless