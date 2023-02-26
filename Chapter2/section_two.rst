Inputs
======

The inputs to any module are the data required to run that module. This section discusses the inputs or data required to run the various models and what the data represent.


**Roth C Soil Model**

This section discusses the data required to run the Roth C model.

- Monthly rainfall is the total amount of rainfall a forest experiences in a month. This data parameter is measured in millimeters (mm)
- Monthly open pan evaporation: This data parameter is measured in millimeters(mm). Rainfall and open-pan evaporation are used to calculate the topsoil moisture deficit, and this is because it is easier than obtaining the monthly measurements of topsoil water deficit.
- Average monthly mean air temperature: This parameter is expressed in Celsius ©. It is used in the Roth C model as it is easier to deduce or obtain than the actual soil temperature.
- Clay content of the soil: This parameter is expressed in percentage. The clay content calculates how much water topsoil can hold.
- An estimate of the decomposability of the incoming plant material - the DPM/RPM ratio. 
- Soil cover: The soil cover parameter tells if the soil is bare or vegetated in a specific month.
- Monthly input of plant residues. The plant residue can be explained as the amount of carbon ingested by the soil per month. This parameter is measured in t C ha-1. To help generate the value of these input parameters, the Roth C model runs in 'inverse' mode, which infers that it generates its input from known soil and weather data.
- Monthly input of farmyard manure. This parameter is measured in t C ha-1 . This parameter is input separately because it is treated differently from inputs of fresh plant residues. The amount of farmyard manure in the soil also referred to as FYM, is not a required parameter.
- Depth of soil layer. This parameter is measured in centimeters (cm).

**Chapman Richards Forest Model**

The data required to run the Chapman Richards Model are listed below:
- Time step (Monthly)
- Dead Organic Matter
- Soil Organic Matter
- Pool 1 
- Forest Age
- Forest Type
- Forest Cover
- Soil Carbon
- Spatial Location of Forest
