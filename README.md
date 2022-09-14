# Master-Thesis_RWTH-Aachen-University_Centre-for-Wind-Power-Drives
This is the overview of the Master thesis topic "Analysis of Regression Models for estimating the main bearing loads of wind turbines" presented at Centre for Wind Power Drives at RWTH Aachen University,Aachen.

## Abstract 
Within the framework of the energy transition, wind energy is one of the key technologies to ensure a long-term and climate-neutral energy supply. The worldwide increasing demand for energy requires a constant expansion of more efficient and more powerful wind turbines. The trend in recent decades has been towards increasing rotor diameters and greater hub heights, which means that higher full-load hours can be achieved. At the same time, this leads to an increase in the dynamic loads on the rotor and in particular on the main bearings of wind turbines. The reliability of the system and its sub-components is crucial for economic operation of wind turbines. Main bearing failures represent a risk in this respect, which is why precise knowledge of the incoming main bearing loads is required for optimal, load-adapted operational management and predictive maintenance. The main bearing loads are usually determined by recording secondary variables. Based on displacements, for example, calculation models can be used to draw conclusions about the underlying loads. This inverse calculation can be carried out using regression models, which enable the depiction of strongly non-linear relationships.

![image](https://user-images.githubusercontent.com/102762042/189150474-d1d3fc78-1a7e-4622-a0da-ed764bc2332b.png)

In the context of this thesis, various machine learning techniques are examined and evaluated with regard to their accuracy and robustness. The data basis required for this comes from test bench tests carried out in which varying dynamic load time series were imposed on a test specimen. Based on the data sets generated, various regression models are trained so that the main bearing load can be determined using displacement signals. The robustness of the models in relation to disturbance variables and measurement errors is then examined using artificially falsified data sets. Finally, the transferability of the regression models to varying systems is evaluated using measurement data from modified test setups.

## Methodology

![image](https://user-images.githubusercontent.com/102762042/189152684-90a3920e-29b4-4e7e-97ba-5254dffd6c5e.png)

From the previous research work [CWD], a detailed eMBS model of wind turbine is developed using SIMPACK software where the model is subjected to low, medium and high turbulence windfields. For training data, the wind speed is varied from 3m/s to 24m/s with an incrementation of 1m/s and constant bearing clearance. For testing data, the wind speed is varied from 6m/s to 12m/s. The generated load time series is exported to test bench consisting of weak wind turbine of capacity 2.3MW with four point rotor suspension. 
The workflow diagram is shown in the figure 3.2 where displacement and load signal from test bench at low and high turbulence windfield is used as training data to build the model and signals from test bench at moderate turbulence windfield is used to evaluate model performance metrics.  

## Result
![image](https://user-images.githubusercontent.com/102762042/189188809-18498360-99de-4e0f-ade2-8fec371b23f5.png)
The results of each model and its performance for each main bearing loads is discussed in dashboard which can be accessed using below link.
https://public.tableau.com/views/Thesisresults_dashboard_v4/Dashboard12?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link

![image](https://user-images.githubusercontent.com/102762042/190120026-81bdaa51-4ff0-4de8-8b08-9cf9a9e0359a.png)


### Summary
* With approach presented in thesis, Regression models can estimate main bearing loads from displacement values with certain degree of error.
* Apart from linear model, all models could capture nonlinearity due to bearing surface and clearance with Bagged ensemble showing highest robustness.
* Bagged Tree ensemble model consistently showed strong robustness for all main bearing loads.
* ANN model showed good performance with original dataset and captured nonlinearity but was inconsistent in robustness test.
* The load monitoring system has the capability to replace physical sensor like strain gauge.
* Compromise made between the accuracy and robustness.

With the approach presented in this thesis of using regression models like linear regression,
polynomial regression, Interaction regression, Tree model, Bagged Ensemble tree model, Support
Vector Regressor, Gaussian Process Regression and Artificial Neural Network, it was possible to
estimate individual main bearing load with displacement signals measured across the bearings.
The use of machine learning models to replace strain gauges to build the load monitoring system
not only makes the system more robust and durable, but also capable for real time data for
commercial use. This data also improve the reliability of wind turbines by improvising on inspection
and maintainance decisions. The study began with the understanding of the previous work on
using the artificial neural network to estimate the main bearing loads and the model‘s capability to
capture nonlinearity due to disturbances in data and robustness to certain degree of errors.
In the first part of the study, the datasets with its parameters were studied followed with exploratory
data analysis and feature engineering. The next stage was building the machine learning models
and optimizing it with hyperparameter tuning. The machine learning models were subjected to
different kinds of measurement uncertainities and nonlinearities like gain error, offset error and
surface error to mimic varying radial clearances, surface imperfections etc in practical usecase.
The perfromance paramterics of every model were studied and compared to draw the best
performing model for these individual errors. In order to mimic the real world scenario where these
errors can occur simultaneously, different random combinations of these errors were added to
original test data over 500 iterations to find the most robust model. The results showed that
Bagged ensemble tree model and coarse tree model were found to be the most robust models to
determine the radial loads in y and z direction and axial loads in x direction. Coarse tree showed
an error gain of 12kN followed by ensemble bagged tree with 14kN for axial load in x direction for
the fixed bearing (FB) with other models in the range of 38kN to 44kN. Bagged ensemble model
showed significantly low error gain of 78kN followed by coarse tree with 83kN for radial load in y
direction for fixed bearing (FB) with other models ranging around 170kN to 230 kN. For the radial
load in z direction for fixed bearing, SVR and Linear regression showed lower error gain of around
5kN to 6kN followed by bagged ensemble model with error gain of 9kN. Bagged ensemble tree
performed significantly better with error gain of 62kN followed by coarse tree with 73kN for radial
load in y direction for loose bearing (LB) which was similar to observations made in fixed bearing
(FB). Bagged ensemble model again outclassed other models with an error gain of 11kN for radial
load in z direction for loose bearing (LB). Apart from subjecting the models to different errors,
model were also tested with new dataset, Misalignment and Generator support dataset, obtained
from modification in test bench. In first modification, generator was supported with only one vertical
aligned pressure ram resulting in relatively stronger vibrations in the drive train. These modified
lateral dynamics are reflected particularly in determination of radial load in z direction and is
evident from weak robustness observed across the models for radial load in z direction. The
second modification included changing positions of torque supports which resulted in preload in
torque arm which in turn affected the x-z symmetry plane. This is evident from weak robustness
observed in loads in x and z compared to y direction. In overall, Bagged ensemble tree model
showed atleast 60 to 70% better performace in comparison to other models due to its high
resilence to disturbances, thus making it suitable model to trial it in real world application. The next
step would be to transfer the methodology applied here to real load monitoring system of a wind
turbine and further monitor on its performance and robustness.
Further research can be done on training these models to new dataset with high disturbances,
especially the bagged ensemble model which showed resilience to generating errors, and
therefore, perform well with the test data. The study also showed that high accuracy in most cases
is accompanied by weak robustness and vice versa. Further study is needed on the minimum
threshold for accuracy and robustness required for these models to be implemented in real world
system because these models showed some degree of errors in load measurement and there is no
research on how these errors can affect in load monitoring especially when wind turbines
encounter turbulence outside of design limits.

## Tools
![image](https://user-images.githubusercontent.com/102762042/190120196-dae575c0-12b1-46ff-bdd9-f505b6c10587.png) ![image](https://user-images.githubusercontent.com/102762042/190120278-384e894f-47d1-4ba0-bfe2-c3854ff18644.png) ![image](https://user-images.githubusercontent.com/102762042/190120370-791f2321-cdcb-4171-88a7-b082456cb363.png) ![image](https://user-images.githubusercontent.com/102762042/190120450-ecf38b61-c2df-4355-a03e-0cf4a3296823.png) ![image](https://user-images.githubusercontent.com/102762042/190120617-21b53ce4-bd09-4e21-8d38-e76c64f6f955.png) ![image](https://user-images.githubusercontent.com/102762042/190120689-c8a0290f-e1a9-4834-8e50-ee6e255d33da.png) ![image](https://user-images.githubusercontent.com/102762042/190120762-fa514c14-7f85-4549-8658-79dbe01eed9e.png)








