# MATLAB-INTERFACE-PLOT
Project Tasks Address the following questions in your project report:
1. In your own words, what do the authors of the code tell you about how the code works?
(Hint: refer to comments in the code and the description section for the code on MATLAB central.
Do not simply copy and paste information from these sources.) (2 points)
2. List the references for methods/data used by the author(s) of the code. (2 points)
3. What are the potential sources of error in your final solution? Include information on the numerical methods used, 
the granularity of the problem (e.g. time step, if explicitly set) and significant digits. (3 points) 
ChE 348 Team Project Page 2 of 7 4. Make a plot of your choice by editing the code (e.g. make a plot of a specific property of a 
species or vary a parameter and plot the variation in the dependent variable as a function of the independent variable). 
Do not simply use plots already in the code. Edit them to plot other useful parameters. 
Provide information on the original and modified plots. (2 points) 5. Add labels, title, legend, etc. to the plot to make it self-explanatory.
If using numerical methods, use at least 2 different time steps. (3 points) 6. Based on the courses you have taken so far and this course,
interpret the variation in the above plot based on your chemical engineering knowledge. You can use chemical engineering equations for this,
from other references. (4 points) 7. Cite all references you use. (1 point) 8. Improve the above code. Make a list of changes and explain
their advantages in the report. Document the changes (including copying and pasting original and changed sections) in the report. 
To get full credit, make at least significant 2 changes (for example, use a better solver or develop an interface). (3 points)


Compressibility Factor Calculator for Gases: Real gases are not ideal in behavior and a parameter used to quantify non-ideality 
in gases is called the compressibility factor. By definition, it is the ratio of molar volume of a real gas divided by estimated
molar volume of the same gas when assumed ideal at the same temperature and pressure. Since the van der Waal equation of state 
better represents behavior than the ideal gas, this code uses it as a surrogate for real behavior. This code is applicable for several
gases such as ammonia, propane and sulfur dioxide and requires a user input of the gas name and temperature and pressure at which
the compressibility factor is to be determined. While the aim of the two choices is the same, there are substantial differences in the 
numerical methods/MATLAB functions and other parts of the code.
Choice 1: https://www.mathworks.com/matlabcentral/fileexchange/35874-compressibility-factor-calculator
Choice 2: https://www.mathworks.com/matlabcentral/fileexchange/59803-compressibility-factor-calculator--exact-
