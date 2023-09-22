# KM_2019_Emergence-Antibiotic-Resistance
Emergence of Antibiotic Resistance in Immunocompromised Host Populations, Myers, DeNegre, Ndeffo, Fefferman

This code was used for the following paper:
A. DeNegre, K. Myers, M. Ndeffo-Mbah, and N.H. Fefferman. 2019. Emergence of Antibiotic Resistance in Immunocompromised Host Populations. PLoS One 14 (2), e0212969

This is the first of three papers (and three respective repositories) in a series. This code was put together in a fairly ad hoc way, and was not organized into a single final version. For that reason, these repositories are separate, even though much of the code is very similar or identical. 

There are three self-contained (except for import/export) Mathematica notebooks.

## File 1: HIV-v25-CH1.nb

Main modules are:
- RUNCHAPTER1[c1_, noaids_, lowtb_, indo_ : False, aidsprev_ : - 1]
- RUNCHAPTER1v2[c1_, noaids_, lowtb_, indo_ : False, aidsprev_ : - 1]
- RUNCHAPTER1POP[c1_, noaids_, lowtb_, indo_ : False, aidsprev_ : - 1]

Those inputs are:
  c1, also noted c[+1] or c+, which is the adherence parameter, representing how many adhere to the protocol
  noaids (boolean) runs the simulation without HIV/AIDS, or else with it
  lowtb (boolean) runs the simulation with low TB parameters, or else the high ones
  indo (boolean) runs the simulation as Indonesia, or else Swaziland (now Eswatini)
  aidsprev is just a default parameter, where it will use the default value (depends on country) unless you want to override
  
V2 is never used, it just has slightly different ouptut, intended for debugging.

POP is also nearly identical, just having different output. (It is used.)

The output, figures, etc. used in analysis are under heading "Executions" and mianly they are self-explanatory. Data is collected for various inputs.

Note that this code is used, almost as-is, for the two other papers / repos. This is because this code was done with all three in mind. Certain parameters are fixed, a few at just zero, for this version, which allows for future flexibility and use with minimal changes to the core of this code.

## File 2: Sensitivity v4.nb

This file (and the next) does the sensitivity analysis for this paper. It uses routines vec, LHC, LHP, snp, and LHCS to generate the parameter values based on Latin hypercube sampling, and then picking values randomly (using LHCS methodology) for each paramter within a provided range. That range is, subsequently, taken to be the baseline value plus or minus 10%.

The subsequent block of code (still part of the first cell) outputs to a file stream the output from the RUNCHAPTER1TRIAL function. Then there are some import functions to look at these data and find the correlation between parameters and outputs, i.e. the sensitivity analysis. (See next file.)

## File 3: Sensitivity v5.nb

In this file, the data from the previous is imported and displayed in a more redable way, outputting a table (as csv and png) and a bar chart.

Data files from this senstivity analysis are available, by request, but are about 200MB. They cannot be stored with a GitHub repo. Note that these files can be (stochastically) reproduced using "Sensitivity v4.nb" above, but we have also retained our data as well.
