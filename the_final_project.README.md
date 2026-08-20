# CE888-Data Science Project



## Description of the project:

In these days with the increasing in energy prices, a company which is providing energy to its clients aim to introduce a new service. This service is about offering free energy to local clients reside near renewable energy sources during periods of surplus energy. To test this idea, the company plans to conduct a project in May 2024, targeting a subset of customers. However, before proceeding, they require a reliable system capable of predicting surplus energy at least 24 hours in advance. This predictive capability will enable the company to notify customers in the area, allowing them to opt into the program. To develop such a system, the company has granted access to historical energy records from the area spanning from 2000 to the present. The company's primary concern is minimizing false positives, as these would result in financial losses by providing free electricity during periods of insufficient surplus energy.
We have been assigning the project to predict the surplus of energy from the historical data that is provided to us.
So first I will predict the surplus from solarradation and convert them to energy by using formula for it. After that I will make assumption about all of the component of the formula. For solarradation as well as solar panels. after that i will decide if there will be enough energy to implement this project and make my recommendation.


## instructions on how to use/run the code:

If you don't have jupyter on your computer, you can use google colab to do so go to https://colab.research.google.com/ . to run the code, you need to Create a directory called 'weatherdata_for_students/brighton' and put there all the csv files on Brighton data and you need to import data exploration and run it in order to train validation and test csv file to be saved we also need to use most of the Python packages. 
The primary libraries that we'll be using are:

1-	NumPy: Provides a fast numerical array structure and helper functions.

2-	pandas: Provides a Data Frame structure to store data in memory and work with it easily and efficiently.

3-	scikit-learn: The essential Machine Learning package in Python.

4-	matplotlib: Basic plotting library in Python; most other Python plotting libraries are built on top of it.

5-	Seaborn: Advanced statistical plotting library.


## Assumptions: 
the mean 
The mean source of energy is windspeed and solar energy or radiation I will talk about both but for the project I decided to pick solarradiation and I will make all the calculation based on it

### wind energy
First of all, The power captured by a wind turbine is given by the artical [Wind Resource and Wind Power Generation Assessment for Education in Engineering](https://www.mdpi.com/2071-1050/13/5/2444)

Pm=1/2ρACp(λ,β)u3   

 1-ρ is the air density,

 2-A is the swept area of the turbine, It's the area covered by the rotating blades as they move through the air.

 3-Cp(λ,β) is the wind-turbine power coefficient. This represents the power coefficient of the wind turbine, which is a measure of its efficiency in converting the kinetic’active’ energy of the wind into mechanical power. The power coefficient can vary based on the tip-speed ratio (λ) and the blade pitch angle (β).

 4- u is the wind speed.

1-	I will take the first component which is p the air density and I will make assumption that it is 1.225 kg/m^3.  the density of air is generally taken as 1.225 kg/m^3, its value at sea level at 15 degrees C.
In many previous studies of wind energy assessment, ρ was assumed to be a constant 1.225 kg/m3 in all conditions. However, a ρ value of 1.225 kg/m3 can only be realized under standard conditions with Ta = 15 ◦C and p = 1013 hPa at sea level [3].
2-	I will take the second component A which is  the swept area of the turbine and I will assume that the length of the blade is 50 meter the radius is 50 so the a will be 3.14159 * 50^2 = 7853.9

3-	Cp The typical range is between 0.25 and 0.45 I will consider it 0.25



### solar energy
 
form the data which we have been given there was two major component we can rely on the first one is solar energy the second one is solarradation which I will choose and make all the assumption for it.
first of all, the energy captured can be calculated by the formula which obtained from [Calculation of electrical energy with solar power plant design](https://ieeexplore.ieee.org/abstract/document/7828701)

E = A * r * H * PR

E: represents the energy 

A: stands for the area  which is exposed to the solarradation. in terms of solar panels, it represent the surface area of the panels.

r: represent the efficiency of the system or device in converting resources into energy. It accounts for losses or inefficiencies in the energy conversion process not the whole avaliable solarradation will be converted.

H: represent the amount of sunlight or solar radiation that reaches the solar panels.

PR: represent the performance ratio and represents the overall efficiency or effectiveness of the system in converting available resources into usable energy. It considers factors such as maintenance, system losses, and environmental conditions.

i will assume the A= 1.5,  r=0.5 based on [Efficiency improvement for solar cells panels by cooling](https://ieeexplore.ieee.org/abstract/document/8724625)  , h i will calcuated from my prediction, PR= 0.7

i will assume that the company has 200 solar panels.

### Consumption 
number of houses= 500

energy/house/hour= approximately 0.5 kwh

the people behaviour= 3 times consumption

based on [Energy consumption in UK households: Impact of domestic electrical appliances](https://www.sciencedirect.com/science/article/pii/0306261996000013) the energy consumption per family in UK is around 3,700 kWh per year approximately 10 kwh per day. I will divide by 24 hour the result would b be 0.416 kwh 
I assume that the company will cover 500 house.


i think that the behaviour of the people will change when they notified that there will be free energy so i assume that they will consume three times the normal consumption.
