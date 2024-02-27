# SPaiNN - Equivariant Message Passing for Excited-State Nonadiabatic Molecular Dynamics

<p align="center">
  <img src="docs/_static/spainn.svg">
</p>

## An Interface between SchNetPack and SHARC for performing Machine Learning-accelerated Photodynamics Simulations
__________________________

# SPaiNN

SPaiNN is a Python package that provides a flexible and efficient interface to the [SchNetPack 2.0](https://github.com/atomistic-machine-learning/schnetpack/tree/master)<sup>1</sup> package a toolbox for the development and application of deep neural networks to the prediction of potential energy surfaces and other quantum-chemical properties of molecules and materials.
SPaiNN allows users to predict energies, forces, dipoles, and non-adiabatic couplings for multiple electronic states, and additionally provides an interface to the [SHARC](https://www.sharc-md.org/)<sup>2</sup> (Surface Hopping including Arbitrary Couplings) software for running excited-state dynamics simulations.
SPaiNN is an extension to the [SchNarc](https://github.com/schnarc/SchNarc)<sup>3</sup> software, *i.e.*, a python software that combines [SchNetPack 1.0](https://github.com/atomistic-machine-learning/schnetpack/tree/schnetpack1.0)<sup>4-7</sup> and [SHARC](https://www.sharc-md.org/)<sup>2</sup>.

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/python/black)
![version](https://img.shields.io/badge/version-1.0.0-blue)

## Features

- Predict potential energy surfaces of multiple electronic states (SchNet<sup>4-7</sup>, PaiNN<sup>8</sup>)
- Predict vector-properties of multiple electronic states, such as non-adiabatic couplings or dipole moments (SchNet<sup>4-7</sup>, PaiNN<sup>8</sup>)
- Interface to the [SHARC](https://www.sharc-md.org/)<sup>2</sup> software for running excited state dynamics simulations
- Flexible implementation in Python

## Requirements

- python 3.8
- [SchNetPack 2.0](https://github.com/atomistic-machine-learning/schnetpack)
- Atomic Simulation Environment (ASE) 3.21
- NumPy
- PyTorch 1.9
- PyTorch Lightning 1.9.0
- Hydra 1.1
- [SHARC 2.1](https://www.sharc-md.org/)

## Documentation
[How to setup data for SPaiNN](docs/database.md)  
... under construction

## Usage

For a quick start, see the [tutorials](https://github.com/CompPhotoChem/SPaiNN/tree/main/tutorials) directory, which contains Jupyter Notebooks showing the workflow for predicting PES for multiple electronic states or NACs as vectorial property.
You can also consult the [documentation]( ) for detailed information about the workflows, API and general usage of SPaiNN.

```bash
src/
├── spainn/
│   ├── __init__.py
│   ├── plotting.py
│   ├── atomistic/
│   │   ├── __init__.py
│   │   ├── phase.py
│   │   └── response.py
│   ├── processing/
│   │   ├── __init__.py
│   │   ├── multistate.py
│   │   └── statistics.py
│   └── configs/
│       ├── train.yaml
│       └── predict.yaml
└── scripts/
    ├── train_spainn.py
    └── eval_spainn.py
examples/
├── NNpot_butene.ipynb
├── NACs_butene.ipynb
└── data/
    ├── 3Sing_butene.db
    ├── 2Sing_butene.db
    └── 1Sing_butene.db
```

## Installation

### SPaiNN

SPaiNN can be installed using pip in two ways, either directly

```bash
pip install spainn
```

or from the source code (cloning the repository):

```bash
git clone https://github.com/CompPhotoChem/SPaiNN.git
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

## Contributing

Contributions to SPaiNN are welcome! Please refer to the [contributing guidelines](https://github.com/CompPhotoChem/SPaiNN/blob/main/Contributing.md) for more information.

## License

SPaiNN is released under the [MIT License](https://github.com/CompPhotoChem/SPaiNN/blob/main/LICENSE).

## References

- [1] K.T. Schütt, S. S. P. Hessmann, N. W. A. Gebauer, J. Lederer, M. Gastegger, *Journal of Chemical Physics* **2023**, 158, 144801–144801, [10.1063/5.0138367](https://pubs.aip.org/aip/jcp/article/158/14/144801/2877924/SchNetPack-2-0-A-neural-network-toolbox-for)
- [2] S. Mai, M. Richter, M. Heindl, M. F. S. J. Menger, A. Atkins, M. Ruckenbauer, F. Plasser, L.M. Ibele, S. Kropf, M. Oppel, P. Marquetand, L. González, *SHARC2.1: Surface Hopping Including Arbitrary Couplings – Program Package for Non-Adiabatic Dynamics* **2019**, [SHARC 2.1](https://sharc-md.org)
- [3] J. Westermayr, M. Gastegger, P. Marquetand, *Phys. Chem. Lett.* **2020**, 11, 10, 3828–3834, [10.1021/acs.jpclett.0c00527](https://doi.org/10.1021/acs.jpclett.0c00527)
- [4] K.T. Schütt, P. Kessel, M. Gastegger, K. Nicoli, A. Tkatchenko, K.-R. Müller, *J. Chem. Theory Comput.* **2019**, 15, 1, 448–455, [10.1021/acs.jctc.8b00908](http://dx.doi.org/10.1021/acs.jctc.8b00908)
- [5] K.T. Schütt. F. Arbabzadah. S. Chmiela, K.-R. Müller, A. Tkatchenko, *Nat. Comm.* **2017**, 8, 13890, [10.1038/ncomms13890](https://www.nature.com/articles/ncomms13890)
- [6] K.T. Schütt. P.-J. Kindermans, H. E. Sauceda, S. Chmiela, A. Tkatchenko, K.-R. Müller, *Advances in Neural Information Processing Systems* **2017**, 30, 992-1002, [Paper](https://proceedings.neurips.cc/paper/2017/hash/303ed4c69846ab36c2904d3ba8573050-Abstract.html)
- [7] K.T. Schütt. P.-J. Kindermans, H. E. Sauceda, S. Chmiela, A. Tkatchenko, K.-R. Müller, *J. Chem. Phys.* **2018**, 148, 24, 241722, [10.1063/1.5019779](https://aip.scitation.org/doi/10.1063/1.5019779)
- [8] K. T. Schütt, O. T. Unke, M. Gastegger, *Proceedings of the 38th International Conference on Machine Learning* **2021**, PMLR 139:9377-9388, [Paper](https://proceedings.mlr.press/v139/schutt21a.html)

