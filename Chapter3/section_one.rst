End-to-end workflow for the GCBM Analysis
=========================================

The GCBM simulation simulates forest landscapes with data from past events and disturbances. Understanding that the data is the backbone of this model, it is important to understand what these data are and what they represent. 


**Disturbance**

Forest landscapes undergo different disturbances. These disturbances, for example, land-use changes, selective harvesting, wildfire, hurricanes, pests, etc.,  are inescapable and are responsible for altering the C dynamics of forests.

To simulate these natural and anthropogenic disturbances and their effects on our forest landscapes, the GCBM uses disturbance matrices. Disturbance matrices contain information about 22 carbon pools that can be grouped into the five Intergovernmental Panel on Climate Change(IPCC) carbon pools. Disturbance matrices define the quantity of carbon transferred between two model pools, the pools, and the atmosphere, and between the pools and harvested wood products. 

The disturbance matrix defined the amount of carbon transferred to the wood product sector to represent harvest-type disturbances.

The GCBM also considers the afforestation disturbance type. Afforestation and reforestation is the conversion of non-forest to forest land through planting, seeding, or the human-induced promotion of natural seed sources. In other words, this disturbance type occurs when a non-forest polygon is converted into a native forest. 

The third disturbance type the GCBM considers is deforestation. Deforestation is the conversion of forest to non-forest land uses. Deforestation is typically associated with large immediate reductions in forest carbon stocks through land clearing. To represent deforestation with a disturbance matrix, 100percent of biomass in the aboveground and belowground components are converted immediately to CO2.


**Land Unit Classifiers**

For the GCBM to properly simulate the flow of carbon between pools, it requires an initial dataset known as inventory. Understood as a list or group of items, this inventory comprises the forest stands present at the simulation's start.

This forest stand inventory has to be spatially explicit, and it should contain the age of the stands and a set of features of the stand, which are referred to as “classifiers”. Classifiers are defined by the user and can be related to site productivity, leading species, ownership, etc.

The forest stands inventory is classified with three classifiers. The dominant species of the ecosystem determine the first classifier. The second inventory classifier is the “Structure” of the forest. The third classifier is “Origin”, this origin classifier tracks the emission reductions derived from non-forest to forest land-use changes.
country to provide an authoritative source of global greenhouse gas emissions. These reports underpin important international treaties like the Paris Agreement. The Paris agreement effectively negotiates between countries that are responsible for cutting emissions and who sequester the most atmospheric carbon. Broadly, we have a goal for the entire world to be carbon neutral by 2050 (this is referred to as ''net zero'' where emissions are perfectly balanced by sequestration), hopefully keeping global warming under a +2C increase in long-term mean temperature. If we fail to achieve this goal, we might end up in a +4C world which is catastrophic.

**Growth Curves**

In the biological sense, a growth curve is used to monitor growth in biological organisms and determine patterns that can be used to track previous growth and predict future growth.

A growth curve is the graphical representation of growth experienced in an organism over a specific period, in this case, trees. The GCBM uses yield or growth curves to model forest biomass accumulation over time. For each of the stand classifiers, a growth curve is created. These growth curves are defined as the merchantable volume of stem wood per year.
under nor over true emissions or removals, and those uncertainties are reduced as far as practicable.

**Climate Data**

**Initial Conditions**

**Simulations**

The GCBM uses a stepwise iterative approach to run a simulation. This approach allows users to change data sources if and when new or improved data become available.

The figure below illustrates the general workflow of the input data and the processing steps involved in the GCBM implementation. 

