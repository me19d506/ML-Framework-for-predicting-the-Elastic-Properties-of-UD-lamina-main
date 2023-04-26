# GPR based ML-Framework-for-predicting-the-Elastic-Properties-ofcarbon fibers
Steps for running the code:
1. Install required dependencies: Abaqus, Python, Matlab and Texgen.
2. Run the following in sequential order
# datasetcreation.m & lhs.m:
Generates input dataset by Latin hypercube sampling (LHS) within specified bounds.
# creatscript.py :
Generate individual Python scripts for modeling and simulating RVE in Abaqus. 
It requries two input files: 
1. input data set generated using _datasetcreation.m_ 
2. File containing the coordinates of the fiber within the RVE. _1.py_ is one such script generated script attached for reference.
# runabaqus.py:
Automatically run the scripts generated using _creatscript.py_. The input values and results are stored in a _results.xlsx_
# gpr.m:
Script to train and test the GPR model. The output of this code (_gpr_workspace.mat and gpr55.m_) is a GPR surrogate to evaluate the UD lamina properties 
# inverse.m:
Iteratively evaluates fiber properties by minimizing the difference between stiffness matrix of experimentally evaluated properties and those computed using the forward  GPR model.
# plain.py
Generates plain woven RUC and saves the voxel meshed model (_.ori, .inp and .eld files_) to evaluated RUC properties in Abaqus. 
# dataHandling.py, dataHandlingInPlane.py & effectiveMatPropRVE.py
Execute the input file generated by _plain.py_ in Abaqus and extract the ouput properties.
# Data files included for reference
 _1.py_                           - Abaqus script for modeling and simulating the RVE for one set of input properties \
_gpr_workspace.mat and gpr55.m_   - Trained GPR models\
_results.xlsx_                    - Input and output values obtained from FE homogenizaiton in abaqus.
