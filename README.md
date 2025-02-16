
# MlCOFSyn

<img alt="Static Badge" src="https://img.shields.io/badge/c++-8.1.0-red?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/python-3.12-blue?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/PyQt5-green?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/sklearn-1.4.2-black?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/numpy-1.26.4-pink?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/pandas-2.2.2-orange?style=flat">

MlCOFSyn is a machine learning framework designed for the synthesis of two-dimensional covalent organic frameworks (2D COFs). MlCOFSyn leverages machine learning algorithms and features an intuitive graphical interface, enabling it to be run on consumer-grade computers by non-experts. The MlCOFSyn framework currently integrates the NEgen1o model as the computational engine and has the following functionalities:

1. ​**Prediction**​: Predicts the crystal size based on the input monomer addition sequence.
2. ​**Design**​: Derives the required monomer addition sequence by specifying the target crystal size.
3. ​**Optimization**​: Optimizes the synthesis pathway to produce larger crystals.

If you use MlCOFSyn, please cite this: https://chemrxiv.org/XXX

## Instructions for running MlCOFSyn
### **1.Prediction Task**
`python MlCOFSyn/negen1o_ui/NEgen1_start.py`

**After startup, the left panel is used for initializing parameters, while the right panel is for generating addition lists. Click "Load COF parameters" to modify the internal parameters of different COFs(obtained through experimental measurements and reaction pathway analysis), and Clicking on the list allows the generation of different types of addition lists.**
![image1](https://github.com/studentgpt/MlCOFSyn/blob/main/image/NEgen1o_1_1.png)
<img src="https://github.com/studentgpt/MlCOFSyn/blob/main/image/function1.png" alt="image2" width="300" height="auto">

**Enter the sequence in the "NEgen1oOutput" section to obtain the final output result.**
![image3](https://github.com/studentgpt/test1/blob/main/image/NEgen1o_3.png)
**Finally, click "Output" in the "DataProcessing" section to view all corresponding result details and crystal distributions.**
![image4](https://github.com/studentgpt/test1/blob/3733c2ca3381163b403e7604c96d81fef48f1719/image/Negen1o_4.png?raw=true)

### **2.Optimization Task**

`python MlCOFSyn/bayesian/main_ui_optimization.py `

**After launching `main_ui_optimization.py`, entering the initialization and COF parameters(Click "Load COF parameters" and "Start") will redirect you to the Optimization page. Input the required reaction space and termination conditions, then click "Start Bayesian Optimization" to initiate the optimization process.**
![bayesian1](https://github.com/studentgpt/test1/blob/main/image/bayesian_1.png)

### **3.Design Task**
`python MlCOFSyn/design/multibax-sklearn-main/main_ui_design.py `

**After launching `main_ui_design.py`, entering the initialization and COF parameters(Click "Load COF parameters" and "Start") will redirect you to the Design page. Input the required design space and the corresponding termination conditions, then click "Start Bayesian Design " to initiate the design process.**
![bayesian1](https://github.com/studentgpt/test1/blob/main/image/design2.png)

## A brief description of the theory

The NEgen1 model<sup>[1]</sup> was derived from kinetic Monte Carlo simulation results. This model takes six parameters for the 2D COF and those for COF-5 are used as default as provided in the code.<sup>[1][2]</sup>Methods to derive the parameters for the other 2D COFs can be found in literature.<sup>[3][4]</sup> The NEgen1o model is optimized upon the NEgen1 model for efficiency while not affecting accuracy.<sup>[5]</sup>

The prediction task is performed by directly running the computational engine (the NEgen1o model). The optimization task leverages Bayesian algorithm.<sup>[6]</sup> The design task utilize the MeanBAX<sup>[7]</sup> as the acquisition function.

A detailed technical description can be found at: https://chemrxiv.org/XXX


## Authors

👤 **Yue Shi**

👤 **Jiaxin Tian**

👤 **Haoyuan Li**


## Contributing

Contributions, bug reports and feature requests are welcome!

Email: lihaoyuan@shu.edu.cn.

## Acknowledgments

This work was supported by the National Natural Science Foundation of China (grant number: 22103053).


## References

[1] Tian, J.; Treaster, K. A.; Xiong, L.; Wang, Z.; Evans, A. M.; Li, H. Taming Two-Dimensional Polymerization by a Machine-Learning Discovered Crystallization Model. Angew. Chem. Int. Ed. 2024, 63 (39), e202408937.

[2] Li, H.; Evans, A. M.; Dichtel, W. R.; Bredas, J.-L. Quantitative Description of the Lateral Growth of Two-Dimensional Covalent Organic Frameworks Reveals Self-Templation Effects. ACS Mater. Lett. 2021, 3 (4), 398–405.

[3] Li, H.; Chavez, A. D.; Li, H.; Li, H.; Dichtel, W. R.; Bredas, J.-L. Nucleation and Growth of Covalent Organic Frameworks from Solution: The Example of COF-5. J. Am. Chem. Soc. 2017, 139 (45), 16310–16318.

[4]	Li, H.; Li, H.; Dai, Q.; Li, H.; Brédas, J.-L. Hydrolytic Stability of Boronate Ester-Linked Covalent Organic Frameworks. Adv. Theor. Simul. 2018, 1 (2), 1700015.

[5] ChemRxiv----------

[6] Shields, B. J.; Stevens, J.; Li, J.; Parasram, M.; Damani, F.; Alvarado, J. I. M.; Janey, J. M.; Adams, R. P.; Doyle, A. G. Bayesian Reaction Optimization as a Tool for Chemical Synthesis. Nature 2021, 590 (7844), 89–96.

[7] Chitturi, S. R.; Ramdas, A.; Wu, Y.; Rohr, B.; Ermon, S.; Dionne, J.; Jornada, F. H. da; Dunne, M.; Tassone, C.; Neiswanger, W.; Ratner, D. Targeted Materials Discovery Using Bayesian Algorithm Execution. npj Comput. Mater. 2024, 10 (1), 156.
