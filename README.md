
# MlCOFSyn

<img alt="Static Badge" src="https://img.shields.io/badge/c++-8.1.0-red?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/python-3.12-blue?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/PyQt5-green?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/sklearn-1.4.2-black?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/numpy-1.26.4-pink?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/pandas-2.2.2-orange?style=flat">
![Apache License 2.0](https://img.shields.io/badge/License-Apache%202.0-brown.svg)
![Windows Badge](https://img.shields.io/badge/Platform-Windows-blue)

MlCOFSyn is a machine learning framework designed for the synthesis of two-dimensional covalent organic frameworks (2D COFs). MlCOFSyn leverages machine learning algorithms and features an intuitive graphical interface, enabling it to be run on consumer-grade computers by non-experts. The MlCOFSyn framework currently integrates the NEgen1o model as the computational engine and has the following functionalities:

1. ​**Prediction**​: Predicts the crystal size based on the input monomer addition sequence.
2. ​**Design**​: Derives the required monomer addition sequence by specifying the target crystal size.
3. ​**Optimization**​: Optimizes the synthesis pathway to produce larger crystals.

## Installation
1.You can clone the repository by running the following commands:

```bash
git clone https://github.com/studentgpt/MlCOFSyn.git
```

2.install environment requirements

```bash
pip install -r requirements.txt
```

`C++>= 8.1.0`


## Instructions for running MlCOFSyn


### **1.Prediction Task**
**1.1 Run the following command to launch the the NEgen1o Graphical User Interface(GUI):** 
```bash
python NEgen1_start.py
```


**After starting up the GUI:**

- The **left panel** (Initial System and Preparation Condition) is used to **initialize parameters**. This section allows you to set the initial conditions for the system, such as volume, concentration, and other system-related settings.

- The **right panel** is for **generating addition lists**. Here, you can create sequences for adding monomers or other materials during the reaction process.

To modify the **internal parameters** of different COFs (which are obtained through experimental measurements and reaction pathway analysis), click on the **`Load COF parameters`** button. This allows you to adjust various COF-related settings based on the data you have.

Additionally, by clicking on the options in the list, you can generate different types of **monomer addition lists**, which can be used to guide the experimental procedure based on the sequence type (e.g., constant sequence, geometric progression, etc.).

![image1](https://github.com/studentgpt/MlCOFSyn/blob/main/image/NEgen1o_1_1.png)
<img src="https://github.com/studentgpt/MlCOFSyn/blob/main/image/function1.png" alt="image2" width="300" height="auto">

**1.2 Enter the monomer addition sequence in the "NEgen1oOutput" section to obtain the final output result.**

In this section, you will need to input the **monomer addition sequence** to generate the results. The sequence can be entered in the following format:

* `0.019,0.037,0.055,0.073,0.091,0.109,0.127,0.145,0.163,0.181` represents increasing-rate addition

* `1`represents a single addition
![image3](https://github.com/studentgpt/test1/blob/main/image/NEgen1o_3.png)

**1.3 Finally, click `Output` in the "DataProcessing" section to view all the corresponding results, including detailed data and crystal distribution.**
![image4](https://github.com/studentgpt/test1/blob/3733c2ca3381163b403e7604c96d81fef48f1719/image/Negen1o_4.png?raw=true)

### **2.Optimization Task**

**2.1 Run the following command to launch the Bayesian optimization interface:**
   ```bash
   python main_ui_optimization.py
   ```

**2.2** After launching the program, enter the **initial parameters** and click **`Set COF parameters`** to set up the COF parameters.

**2.3** Then, click **`Start`** to enter the **Bayesian Optimization GUI**. Input the required **reaction space** CSV file path, **Total Iteration**, **termination conditions**, and **candidates per iteration**, and click **"Start Bayesian Optimization"** to begin the process.
 
🚨 **Recommended to use 5 experiments per batch, and the number of CPU cores should be at least 6.** 🚨

![bayesian1](https://github.com/studentgpt/test1/blob/main/image/bayesian_1.png)


### **3.Design Task**
**3.1 Run the following command to launch the Bayesian Design GUI:**
```bash
python main_ui_design.py
   ```
**3.2** After launching the program, enter the **initial parameters** and click **`Set COF parameters`** to set up the COF parameters.

**3.3** Then, click **`Start`** to enter the **Bayesian Design GUI**. Input the required **reaction space** CSV file path, **Total Iteration**, **termination conditions**, and **candidates per iteration**, and click **"Start Bayesian Design"** to begin the process.
 
🚨 **Recommended to use 5 experiments per batch, and the number of CPU cores should be at least 6.** 🚨

![bayesian1](https://github.com/studentgpt/test1/blob/main/image/design2.png)

   
   **Please verify the number of tasks and cores before submission to avoid system overload.**

## A brief description of the theory

The NEgen1 model<sup>[1]</sup> was derived from kinetic Monte Carlo simulation results. This model takes six parameters for the 2D COF and those for COF-5 are used as default as provided in the code.<sup>[1][2]</sup>Methods to derive the parameters for the other 2D COFs can be found in literature.<sup>[3][4]</sup> The NEgen1o model is optimized upon the NEgen1 model for efficiency while not affecting accuracy.<sup>[5]</sup>

The prediction task is performed by directly running the computational engine (the NEgen1o model). The optimization task leverages Bayesian algorithm.<sup>[6]</sup> The design task utilize the MeanBAX<sup>[7]</sup> as the acquisition function.

A detailed technical description can be found at: https://chemrxiv.org/XXX

## License
The Apache License 2.0 is a permissive license whose main conditions require the preservation of copyright and license notices. Contributors provide an express grant of patent rights. Licensed works, modifications, and larger works may be distributed under different terms and without source code.

| **Permissions**        | **Limitations**      | **Conditions**      |
|------------------------|----------------------|---------------------|
| Commercial use ✅       | Trademark use ❌      | License and copyright notice ⚠️ |
| Modification 	✅         | Liability ❌          | State changes ⚠️     |
| Distribution ✅         | Warranty ❌           |                     |
| Patent use ✅           |                      |                     |
| Private use ✅          |                      |                     |



## Authors

👤 **Yue Shi**

👤 **Jiaxin Tian**

👤 **Haoyuan Li**


## Contributing

Contributions, bug reports and feature requests are welcome!

Email: lihaoyuan@shu.edu.cn.

## Acknowledgments

This work was supported by the National Natural Science Foundation of China (grant number: 22103053).

## Citation

Please cite our paper: "MlCOFSyn: A Machine Learning Framework to Facilitate the Synthesis of 2D Covalent Organic Frameworks" if you find this project helpful:
[`https://chemrxiv.org/XXX`](https://chemrxiv.org/XXX)


## References

[1] Tian, J.; Treaster, K. A.; Xiong, L.; Wang, Z.; Evans, A. M.; Li, H. Taming Two-Dimensional Polymerization by a Machine-Learning Discovered Crystallization Model. Angew. Chem. Int. Ed. 2024, 63 (39), e202408937.

[2] Li, H.; Evans, A. M.; Dichtel, W. R.; Bredas, J.-L. Quantitative Description of the Lateral Growth of Two-Dimensional Covalent Organic Frameworks Reveals Self-Templation Effects. ACS Mater. Lett. 2021, 3 (4), 398–405.

[3] Li, H.; Chavez, A. D.; Li, H.; Li, H.; Dichtel, W. R.; Bredas, J.-L. Nucleation and Growth of Covalent Organic Frameworks from Solution: The Example of COF-5. J. Am. Chem. Soc. 2017, 139 (45), 16310–16318.

[4]	Li, H.; Li, H.; Dai, Q.; Li, H.; Brédas, J.-L. Hydrolytic Stability of Boronate Ester-Linked Covalent Organic Frameworks. Adv. Theor. Simul. 2018, 1 (2), 1700015.

[5] ChemRxiv----------

[6] Shields, B. J.; Stevens, J.; Li, J.; Parasram, M.; Damani, F.; Alvarado, J. I. M.; Janey, J. M.; Adams, R. P.; Doyle, A. G. Bayesian Reaction Optimization as a Tool for Chemical Synthesis. Nature 2021, 590 (7844), 89–96.

[7] Chitturi, S. R.; Ramdas, A.; Wu, Y.; Rohr, B.; Ermon, S.; Dionne, J.; Jornada, F. H. da; Dunne, M.; Tassone, C.; Neiswanger, W.; Ratner, D. Targeted Materials Discovery Using Bayesian Algorithm Execution. npj Comput. Mater. 2024, 10 (1), 156.
