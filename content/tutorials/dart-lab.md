---
title: "DART\_LAB"
date: 2020-01-24T13:36:06+06:00
image: images/tutorial/dart-lab-thumb.png
feature_image: images/tutorial/dart-lab.png
weight: 1
category: "MATLAB"
author: dart
---
#### An introduction to Data Assimilation using MATLAB


DART\_LAB is a MATLAB®-based tutorial to demonstrate the principles of 
ensemble data assimilation. The DART\_LAB tutorial begins at a more introductory 
level than the materials in the tutorial directory, and includes hands-on exercises.
DART\_LAB consists of PDF tutorial materials and MATLAB® exercises.
See below for links to the PDF files and a list of the 
corresponding MATLAB scripts.

#### DART\_LAB tutorial slides

[1. The basics in 1D.](/pdfs/dart_lab/DART_LAB_Section01.pdf)

[2. Multivariate assimilation.](/pdfs/dart_lab/DART_LAB_Section02.pdf)  How should observations of a state variable impact an unobserved state variable?

[3. Sampling error and localization.](/pdfs/dart_lab/DART_LAB_Section03.pdf)

[4. The Ensemble Kalman Filter (Perturbed Observations).](/pdfs/dart_lab/DART_LAB_Section04.pdf)

[5. Adaptive Inflation.](/pdfs/dart_lab/DART_LAB_Section05.pdf)


#### Hands-on Exercises

The DART\_LAB materials are bundled with DART. 

You can download [DART](https://github.com/NCAR/DART) from Github using 

````
git clone https://github.com/NCAR/DART.git
````

To try the MATLAB hands-on exercises, start MATLAB® in the `DART/docs/DART_LAB` directory.

````
cd DART/docs/DART_LAB
matlab
````

In the `matlab` subdirectory are a set of MATLAB scripts and 
graphical user interface (GUI) programs which are exercises that go with the 
tutorial. Each is interactive with settings that can be changed and 
rerun to explore various options. A valid
[MATLAB](http://www.mathworks.com/products/matlab/)
license is needed to run these scripts.

The exercises use the following functions:


| function            | description |
| ---                 | :---         |   
| `gaussian_product`  | graphical representation of the product of two gaussians |
| `oned_ensemble`     | explore the details of ensemble data assimilation for a scalar |
| `oned_model`        | simple ensemble data assimilation example |
| `oned_model_inf`    | simple ensemble data assimilation example *with inflation* |
| `run_lorenz_63`     | ensemble DA with the 3-variable Lorenz '63 dynamical model - the "butterfly" model |
| `run_lorenz_96`     | ensemble DA with the 40-variable Lorenz '96 dynamical model |
| `run_lorenz_96_inf` | ensemble DA with the 40-variable Lorenz '96 dynamical model *with inflation* |
| `twod_ensemble`     | demonstrates the impact of observations on unobserved state variables |


