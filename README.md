# realFluid3sSLFMFoam-6

## General Information
A package for simulations of turbulent non-premixed flames using real-fluid based flamelet models in OpenFOAM 6.0. The main part of the code for real-fluid models are taken from [1][2], and main part of the code for flamelet based models are taken from [3]. In this package, a pressure-based solution method with a modified PIMPLE algorithm [4] is employed to improve the stability while a fast and robust coupling Newton-Bisection algorithm is utilized to guarantee the convergency of fluid flow simulations under transcritical and supercritical conditions.

## Flamelet models can be used with this package
- Steady laminar flamelet model (SLFM) [5, 6].
- Three-feed stream steady laminar flamelet model (3s-SLFM) [7,8]

## Real-fluid models can be used with this package
- Modified Soave-Redlich-Kwong (SRK) model for equation of state [9, 10].
- Peng-Robinson (PR) model for equation of state [11]
- JANAF-based model for real-fluid thermodynamic properties.
- Chung's model (1988) for dynamic viscosity and thermal conductivity [12].

## Installation
- Since this solver is developed based on OpenFOAM 6.0 in Linux operating systems, the complete installation of OpenFOAM 6.0 framework is required. 
- Prepare a directory on your system, e.g., _yourDirectory_:

		mkdir ~/OpenFOAM/yourDirectory/
		cd ~/OpenFOAM/yourDirectory/	
- Download source files using git: 

		git clone https://github.com/danhnam11/realFluid3sSLFMFoam-6.git

- Specify the path of your _src_ directory to an environment variable, _LIB_rf3sSLFM_SRC_. For example:

		echo "export LIB_3sSLFM_SRC=~/OpenFOAM/yourDirectory/rf3sSLFMFoam-6/src/" >> ~/.bashrc
		source ~/.bashrc
- To compile the necessary libraries and solver, go to _realFluid3sSLFMFoam-6_ directory and run the _Allwmake_ script:

		cd ~/OpenFOAM/yourDirectory/realFluid3sSLFMFoam-6/
		./Allwmake

- Now all necessary libraries inlcuding _flameletCombustionModels_ library (for flame based models), _thermophysicalModels_ (for real-fluid models), solvers such as _realFluidSLFMFoam_, _realFluid3sSLFMFoam_, and pre- and post-processing utilities _flameletToFoam_, _3sFlameletToFoam_, _postSLFMFoam_, _post3sSLFMFoam_ are stored at _$FOAM_USER_LIBBIN_ and _$FOAM_USER_APPBIN_ directory. These newly compiled libraries, solvers, and utilities are ready to be used.

- To remove all compiled libraries and solvers, go to _realFluid3sSLFMFoam-6_ directory and run the _Allwclean_ script:

		cd ~/OpenFOAM/yourDirectory/realFluid3sSLFMFoam-6/
		./Allwclean

## Using this package 
- Upon completing the compilation process, all solvers and utilities can be utilized with different flamelet models by simply typing _realFluidSLFMFoam_ (for using SLFM) or _realFluid3sSLFMFoam_ (for using 3s-SLFM) in the terminal. All important instructions for case setting can be found in _tutorial_ directory. 
- Pre-processing: It is importance to note that the pre-processing step is essential. For 1-D flamelet database for generating flamelet table can be prepared by using _Cantera_ [13] with non-ideal equation of state model. Details of the pre-processing step is provided in _documentations_ directory.
- Post-processing: Readers can referred to ideal-gas version here https://github.com/danhnam11/3sSLFMFoam-6.
- Readers are referred to our paper for all validation data.

## Tutorials
Tutorials for RANS/LES of a test case is available in the _tutorial_ directory.

	cd ~/OpenFOAM/yourDirectory/realFluid3sSLFMFoam-6/tutorials/

## Authors 
This package was developed at Clean Combustion & Energy Research Lab., Dept. of Mech. Engineering, Ulsan National Institute of Science and Technology (UNIST), Korea (Prof. C.S. Yoo: https://csyoo.unist.ac.kr/). If you publish results that are obtained using this package, please cite our papers as follows:
- D. N. Nguyen, C. S. Yoo, realFluid3sSLFMFoam: An Open-FOAM based framework for simulations of turbulent non-premixed flames using real-fluid based flamelet models in OpenFOAM, Computer Physics Communications (2024)(in preparation).

Contact:
- danhnam11@gmail.com or nam.nguyendanh@hust.edu.vn 

## Reference
- [1] D. N. Nguyen, K. S. Jung, J. W. Shim, C. S. Yoo, Real-fluid thermophysicalModels library: An OpenFOAM-based library for reacting flow simulations at high pressure, Comput. Phys. Commun. 273 (2022) 108264.
- [2] D. N. Nguyen, C. S. Yoo, realFluidFoam: A low Mach number solver for simulations of turbulent flows at transcritical and supercritical conditions in OpenFOAM, Computer Physics Communications (2024)(submitted).
- [3] D. N. Nguyen, C. S. Yoo, 3sSLFMFoam: A package for simulations of turbulent non-premixed flames using three-feed stream steady laminar flamelet model in OpenFOAM, Computer Physics Communications (2024)(submitted).
- [4] M. Jarczyk, M. Pfitzner, Large eddy simulation of supercritical nitrogen jets, in: 50th AIAA Aerospace Sciences Meeting Including the New Horizons Forum and Aerospace Exposition, Nashville, Tennessee, 2012. 
- [5] H. Muller, F. Ferraro, M. Pfitzner, Implementation of a Steady Laminar Flamelet Model for non-premixed combustion in LES and RANS simulations, in 8th Int. OpenFOAM Workshop, Jeju, Korea, 2013.
- [6] N. Peters, Laminar diffusion flamelet models in non-premixed turbulent combustion, Prog. Engery Combust. Sci. 10 (1984) 319-339.
- [7] M. Ihme, Y. C. See, LES famelet modeling of a three-stream MILD combustor: Analysis of fame sensitivity to scalar infow conditions, Proceedings of the Combustion Institute 33 (2011) 1309-1317
- [8] G. Indelicato, P. E. Lapenna, R. Concetti, M. Caputo, M. Valorani, G. Magnotti, F. Creta, Numerical investigation of high pressure co2-diluted combustion using a famelet-based approach, Combustion Science and Technology 192 (2020) 2028-2049.
- [9] G. Soave, Equilibrium constants from a modified Redlich-Kwong equation of state, Chem. Eng. Sci. 27 (1972) 1197-1203.
- [10] D. Peng, D. Robinson, New two-equation of state, Ind. Eng. Chem. Fundam. 15(1976) 59-64. 
- [11] M. S. Graboski, T. E. Daubert, A modified Soave equation of state for phase equilibrium calculations. 1. Hydrocarbon systems, Ind. Eng. Chem. Process. Des. Dev. 17 (1978) 443-448.
- [12] T. C. Horng, M. Ajlan, L. L. Lee, K. E. Starling, M. Ajlan, Generalized multiparameter correlation for nonpolar and polar fluid transport properties, Ind. Eng. Chem. Res. 27 (1988) 671-679.
- [13] D. G. Goodwin, R. L. Speth, H. K. Moffat, B. W. Weber, Cantera: An object-oriented software toolkit for chemical kinetics, thermodynamics, and transport processes, https://www.cantera.org, version 3.0.0 (2023). doi:10.5281/zenodo.8137090. 