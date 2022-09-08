# Master-Thesis_RWTH-Aachen-University_Centre-for-Wind-Power-Drives
This is the overview of the Master thesis topic "Analysis of Regression Models for estimating the main bearing loads of wind turbines" presented at Centre for Wind Power Drives

## Abstract 
Within the framework of the energy transition, wind energy is one of the key technologies to ensure a long-term and climate-neutral energy supply. The worldwide increasing demand for energy requires a constant expansion of more efficient and more powerful wind turbines. The trend in recent decades has been towards increasing rotor diameters and greater hub heights, which means that higher full-load hours can be achieved. At the same time, this leads to an increase in the dynamic loads on the rotor and in particular on the main bearings of wind turbines. The reliability of the system and its sub-components is crucial for economic operation of wind turbines. Main bearing failures represent a risk in this respect, which is why precise knowledge of the incoming main bearing loads is required for optimal, load-adapted operational management and predictive maintenance. The main bearing loads are usually determined by recording secondary variables. Based on displacements, for example, calculation models can be used to draw conclusions about the underlying loads. This inverse calculation can be carried out using regression models, which enable the depiction of strongly non-linear relationships.

![image](https://user-images.githubusercontent.com/102762042/189150474-d1d3fc78-1a7e-4622-a0da-ed764bc2332b.png)

In the context of this thesis, various machine learning techniques are examined and evaluated with regard to their accuracy and robustness. The data basis required for this comes from test bench tests carried out in which varying dynamic load time series were imposed on a test specimen. Based on the data sets generated, various regression models are trained so that the main bearing load can be determined using displacement signals. The robustness of the models in relation to disturbance variables and measurement errors is then examined using artificially falsified data sets. Finally, the transferability of the regression models to varying systems is evaluated using measurement data from modified test setups.

## Methodology

![image](https://user-images.githubusercontent.com/102762042/189152684-90a3920e-29b4-4e7e-97ba-5254dffd6c5e.png)

From the previous research work [CWD], a detailed eMBS model of wind turbine is developed using SIMPACK software where the model is subjected to low, medium and high turbulence windfields. For training data, the wind speed is varied from 3m/s to 24m/s with an incrementation of 1m/s and constant bearing clearance. For testing data, the wind speed is varied from 6m/s to 12m/s. The generated load time series is exported to test bench consisting of weak wind turbine of capacity 2.3MW with four point rotor suspension. 
The workflow diagram is shown in the figure 3.2 where displacement and load signal from test bench at low and high turbulence windfield is used as training data to build the model and signals from test bench at moderate turbulence windfield is used to evaluate model performance metrics.  

## Result
![image](https://user-images.githubusercontent.com/102762042/189153004-3bafd60b-79dc-4717-8482-0f3d8af30548.png)
The results of each model and its performance for each main bearing loads is discussed in dashboard which can be accessed using below link.
https://public.tableau.com/views/Thesisresults_dashboard_v3/Dashboard1?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link

### Summary
--With approach presented in thesis, Regression models can estimate main bearing loads from displacement values with certain degree of error.
--Apart from linear model, all models could capture nonlinearity due to bearing surface and clearance with Bagged ensemble showing highest robustness.
--Bagged Tree ensemble model consistently showed strong robustness for all main bearing loads.
--ANN model showed good performance with original dataset and captured nonlinearity but was inconsistent in robustness test.
--Compromise made between the accuracy and robustness.



