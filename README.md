<p align="center">
  <img src="docs/_static/spainn.svg">
</p>

# SPaiNN - Exited State Dynamics with Machine Learning

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/python/black)
![version](https://img.shields.io/badge/version-1.0.0-blue)

A SchNetPack[1]/SHARC[3] interface for machine-learning accelerated excited state simulations.  
Based on [SchNarc](https://github.com/schnarc/SchNarc)[2] with major performance and usability improvements.

## Installation

### SPaiNN
Clone the repository and install with pip.
```bash
git clone https://github.com/smausenberger/SPaiNN.git
cd SPaiNN
pip install .
```

### SHARC and pySHARC

Install SHARC with pysharc (see [SHARC manual](https://sharc-md.org/?page_id=50#tth_sEc2.3); version 2.1.1) 

**IMPORTANT**

Currently there is a not yet fixed bug in pySHARC.
Open ``source/input_list.f90`` and change line 96 from
```fortran
read(nunit,'(A)', iostat=io) line
```
to 
```fortran
read(nunit,'(A)', iostat=stat) line
```

Then open ``pysharc/sharc/__init__.py``  there and make the following changes:  
```python
#import sharc as sharc
```

## Documentation
[How to setup data for SPaiNN](docs/database.md)  
... under construction

## References


* [1] K.T. Schütt, P. Kessel, M. Gastegger, K. Nicoli, A. Tkatchenko, K.-R. Müller.  
*SchNetPack: A Deep Learning Toolbox For Atomistic Systems.*  
J. Chem. Theory Comput. [10.1021/acs.jctc.8b00908](http://dx.doi.org/10.1021/acs.jctc.8b00908) [arXiv:1809.01072](https://arxiv.org/abs/1809.01072). (2018)
* [2] J. Westermayr, M. Gastegger, P. Marquetand.  
*Combining SchNet and SHARC: The SchNarc Machine Learning Approach for Excited-State Dynamics*  
The Journal of Physical Chemistry Letters 2020 11 (10), 3828-3834  
DOI: [10.1021/acs.jpclett.0c00527](https://pubs.acs.org/doi/10.1021/acs.jpclett.0c00527)
* [3] S. Mai, M. Richter, M. Heindl, M. F. S. J. Menger, A. Atkins, M. Ruckenbauer, F. Plasser, L.M. Ibele, S. Kropf, M. Oppel, P. Marquetand, L. González.  
*SHARC2.1: Surface Hopping Including Arbitrary Couplings – Program Package for Non-Adiabatic Dynamics (2019).*  
[SHARC 2.1](https://sharc-md.org)
