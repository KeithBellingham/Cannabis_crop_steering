#Cannabis crop steering<br />



![Screen Shot 2022-10-18 at 6 46 00 AM](https://user-images.githubusercontent.com/62969383/197302490-7dd177b9-a653-40b7-8a10-0af5c79e2f80.png)


**Introduction**<br />

Indoor grown cannabis has three stages within a 3-month growing season, a seeding stage, vegetive stage and a flowering stage. Water and fertigation content in the grow media directly impacts the heath of the crop and the concentration of the THC produced. Soil moisture was monitored every 5 minutes in 20 cannabis plants in a single irrigation zone. The irrigation zone consists of 630 cannabis plants in total and the moisture monitoring took place over two months during veg and flowering stages.  During these growth stages, soil moisture sensors insure adequate moisture from daily irrigation events. The cannabis plant will become stress and susceptible to disease if the moisture gets too low or stays too wet. Toward the end of the growing season before harvest, a dry-back procedure is carried out where the irrigation zone is not watered for 3 to 5 days. This intentionally stresses the cannabis causing the cannabis plant to produce more THC and CBD in the flower.  Soil moisture data can give the grower valuable insight during the dry-back and help ensure crop heath during the growth stages. 

**Theory**<br />
The relationship between soil moisture and crop health is not straightforward and usually not well understood.  Techniques and tools commonly used in the field of data science are used to understand the flow and retention of water in the soil.  

Water movement in soil is driven by two physical forces, gravity and capillarity. If the soil is completely saturated or very wet (After an irrigation event), the primary force acting on the water will be gravity and can be best disrobed be Darcy’s Law; 


$$\frac{\partial \theta}{\partial t} = flow  = -K_s(dh/dz)$$

Where $\theta$  is volumetric soil moisture, *K_s* is the saturated hydraulic conductivity, *h* is hydraulic head and *z* is depth.  

After gravity gets finish pulling the water out of the soil, the predominant force acting on the water is capillary forces which is the force of the surface tension between water and air. Water movement from capillary forces is commonly called “wicking” and is described by the Richard’s Equation;


$$\frac{\partial \theta}{\partial t} = flow  =   \frac{\partial (K_h   \frac{\partial h}{\partial z}         }{\partial z} )  + \frac{\partial K_h} {\partial z }   -S(h) $$    



In the Richard’s equation *K_h* is now the head dependent hydraulic conductivity, and *-S(h)* is basically evaporation. 

In plant/water dynamics, the optimal soil water content for most crops and most plants is call the available water capacity (AWC) and is largely a function of the soil. The upper limit of the AWC is the soil’s “field capacity”. The field capacity is an important hydrological threshold in agriculture and agronomy. Field capacity is defined as the soil moisture after the water drains out. It is where the gravitational force acting on the water in soil is equal to the capillary forces acting on the water and thus *K_h* from the Richard’s equation is equal to *K_s* in Darcy’s Law.  The lower limit of the AWC can be assumed to be 80% of the Field capacity. Basically, the optimal soil moisture for most crops is between field capacity and 80% of field capacity. 

Field capacity may be expensive and difficult to measure in the lab. Also, field capacity is highly variable because soil is highly variable. Factors such as compaction, organic matter, texture, particle size distribution, and the roots of the plant all affect the soil moisture values where field capacity would occur.  Because of this variability, each individual soil sensor experiences a local field capacity, and the mathematical and algorithmic determination of field capacity needs to be carried out for each sensor separately. 

Since the local soil field capacity is not likely to change during a grow season, a select time range of the soil moisture time series data can be chosen as training data. This would eliminate errors in the calculation of field capacity if the crop is under or over irrigated.    

The goal is to determine the AWC and determine when crops would become stressed form the time series soil moisture data. 
