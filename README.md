
# MlCOFSyn

<img alt="Static Badge" src="https://img.shields.io/badge/c++-8.1.0-red?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/python-3.12-blue?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/PyQt5-green?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/sklearn-1.4.2-black?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/numpy-1.26.4-pink?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/pandas-2.2.2-orange?style=flat">
![Apache License 2.0](https://img.shields.io/badge/License-Apache%202.0-brown.svg)
![Windows Badge](https://img.shields.io/badge/Platform-Windows-blue)

MlCOFSyn is a machine learning framework designed for the synthesis of two-dimensional covalent organic frameworks (2D COFs). MlCOFSyn leverages machine learning algorithms and features an intuitive graphical interface, enabling it to be run on consumer-grade computers by non-experts. The MlCOFSyn framework currently integrates the NEgen1o model as the computational engine and has the following functionalities:

1. ​**Prediction**​: Predicts the crystal size based on the input monomer addition sequence.
2. ​**Design**​: Derives the required monomer addition sequence by specifying the target crystal size.
3. ​**Optimization**​: Optimizes the monomer addition sequence to produce larger crystals.

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

## Requirement for running MlCOFSyn
### Python Libraries
The following Python libraries must be installed:
- numpy
- pandas
- scipy
- scikit-learn
- matplotlib
- tqdm
- joblib
- psutil

### System Requirements
- **Operating System**: Windows  
- **CPU**: A minimum of 6 CPU cores is required.
- **C++ Version**: `C++ >= 8.1.0` must be installed.

## Instructions for running MlCOFSyn


### **1.Prediction Task**
**1.1 Run the following command to launch the the NEgen1o Graphical User Interface(GUI):** 
```bash
cd MlCOFSyn\prediction
```
```bash
python NEgen1_start.py
```


**After starting up the GUI:**

- **`Set COF Parameters`** Button: Click this button to adjust the material parameters of the 2D COF, which can be determined through experimental measurements and reaction pathway analysis.

- The **Initial System**: This section enables you to define the initial conditions of the system, such as the initial volume, initial nuclei concentration, diameter, and height.

- The **Conditions to Add Monomer**: In this section, you are required to input the **Monomer (core) Concentration** first, followed by the **Monomer Addition Sequence**, which is a list of the monomer volume added at each time (in L). Once the **Monomer Addition Sequence** is entered, you may click the `Check Input` button to display the corresponding **Number of Additions** and the **Total Added Volume**.

The monomer addition sequence can be entered in the following format:

* `0.019,0.037,0.055,0.073,0.091,0.109,0.127,0.145,0.163,0.181` represents increasing-rate addition

* `1` represents a single addition

![image1](https://github.com/studentgpt/MlCOFSyn/blob/main/image/NEgen1o_1_1.png)
<img src="https://github.com/studentgpt/MlCOFSyn/blob/main/image/function1.png" alt="image2" width="300" height="auto">

**1.2  `Run Computational Engine` section:**

In this section, you can initiate the calculation by clicking the `Run` button to execute the NEgen1o model. Once the model starts running, you can view detailed computational information directly from the panel in real-time.

![image3](https://github.com/studentgpt/test1/blob/main/image/NEgen1o_3.png)

🚨 **Before performing the next addition sequence calculation with the same number of additions, please ensure that all addition sequence files with the same number of additions (e.g., `nuc__1_0_x`, where `x`is identical) in the `MlCOFSyn\negen1o` directory are first backed up to another folder or deleted. Otherwise, the program will not run when you click `Start`**

**1.3 Finally, click `Get Result Summary` in the "Post Processing" section to view all the corresponding results, including detailed data and crystal distribution.**
![image4](https://github.com/studentgpt/MlCOFSyn/blob/main/image/Negen1o_4.png)

### **2.Optimization Task**

**2.1 Run the following command to launch the Bayesian optimization interface:**
   ```bash
   cd MlCOFSyn\optimization
   ```
   ```bash
   python main_ui_optimization.py
   ```

**2.2** After launching the program, you will enter the **Bayesian Optimization GUI**. To proceed, first click **`Set COF parameters`** to configure the COF parameters, and then input the **Monomer Concentration**.

**2.3** After entering the initial parameters, follow these steps to begin the Bayesian optimization process:

  1. **Load Monomer Addition Sequence Space File**:  
     Upload the file containing the monomer addition sequence space to be optimized.
     The reaction space must be in CSV format with the following structure:
  ```bash
     r1,r2,r3,r4,r5,r6,r7,r8,r9,r10,r11,r12,r13,r14,r15,r16,r17,r18,r19,r20
  
     0.062,0.109,0.082,0.025,0.165,0.147,0.131,0.146,0.102,0.031,0,0,0,0,0,0,0,0,0,0
  
     0.031,0.036,0.07,0.054,0.021,0.086,0.027,0.012,0.092,0.013,0.089,0.075,0.028,0.028,0.088,0.071,0.076,0.019,0.022,0.062

   ```
  - The first row contains feature names.
  - The following rows represent monomer addition sequences.
  - You can find data examples in the file: `MlCOFSyn\optimization\space\all_space.csv`
  - To ensure the proper functioning of the surrogate model, **please make sure that all monomer addition sequences in the `reaction_space.csv` have the same number of features** (use `0` to fill any empty spaces).
  
  2. **Stop Conditions**:  
     - Input the **Maximum Number of Iterations**.  
     - Specify the **No-Improvement Criterion** as a stop condition.  
  
  3. **Start the Optimization**:  
     Once the **monomer addition sequence space file** and **stop conditions** are confirmed, click the **`Start Bayesian Optimization`** button to initiate the process.

The **Maximum Q value** and its corresponding **monomer addition sequence** will be displayed on the interface, and all other results will be saved to `optimization/result.csv`.
 
🚨 **Recommended to use 5 experiments per batch, and the number of CPU cores should be at least 6.** 🚨



![bayesian1](https://github.com/studentgpt/test1/blob/main/image/bayesian_1.png)


### **3.Design Task**
**3.1 Run the following command to launch the Bayesian Design GUI:**
```bash
cd MlCOFSyn\design\multibax-sklearn-main
   ```
```bash
python main_ui_design.py
   ```
**3.2** After launching the program, you will enter the **Bayesian Design GUI**. To proceed, first click **`Set COF parameters`** to configure the COF parameters, and then input the **Monomer Concentration**.

**3.3** After entering the initial parameters, follow these steps to begin the Bayesian Design process:
1. **Load Monomer Addition Sequence Space File**:
   The reaction space format for the **Bayesian Design** task is **identical** to the one used in the **Bayesian Optimization** task.

   You can find data examples in the file: `MlCOFSyn/design/multibax-sklearn-main/dataset/all_space.csv`

2.  **Stop Conditions**:  
     - Input the **Maximum Number of Iterations**.  
     - Specify the **Number of Design Sequences** as a stop condition.
       
3. **Target Q range**：
   Please input the target range for the Q you aim to design.
   
4.**Start the Design**:
   Once the **monomer addition sequence space file**, **stop conditions**, and **target Q range** are confirmed, click the **`Start Bayesian Design`** button to initiate the process.


![bayesian1](https://github.com/studentgpt/MlCOFSyn/blob/main/image/design2.png)

   
🚨**Please verify the number of tasks and cores before submission to avoid system overload.**

## A brief description of the theory

The NEgen1 model<sup>[1]</sup> was derived from kinetic Monte Carlo simulation results. This model takes six parameters for the 2D COF and those for COF-5 are used as default as provided in the code.<sup>[1][2]</sup>Methods to derive the parameters for the other 2D COFs can be found in literature.<sup>[3][4]</sup> The NEgen1o model is optimized upon the NEgen1 model for efficiency while not affecting accuracy.<sup>[5]</sup>

The prediction task is performed by directly running the computational engine (the NEgen1o model). The optimization task leverages Bayesian algorithm.<sup>[6]</sup> The design task utilize the MeanBAX<sup>[7]</sup> as the acquisition function.

A detailed technical description can be found at: https://chemrxiv.org/XXX and https://doi.org/10.1002/anie.202408937

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

If you find this project helpful, please cite our papers:

1. **MlCOFSyn: A Machine Learning Framework to Facilitate the Synthesis of 2D Covalent Organic Frameworks**  
   DOI: [`https://chemrxiv.org/XXX`](https://chemrxiv.org/XXX)

2. **Taming Two-Dimensional Polymerization by a Machine-Learning Discovered Crystallization Model**  
   DOI: [`https://doi.org/10.1002/anie.202408937`](https://doi.org/10.1002/anie.202408937)


## References

[1] Tian, J.; Treaster, K. A.; Xiong, L.; Wang, Z.; Evans, A. M.; Li, H. Taming Two-Dimensional Polymerization by a Machine-Learning Discovered Crystallization Model. Angew. Chem. Int. Ed. 2024, 63 (39), e202408937.

[2] Li, H.; Evans, A. M.; Dichtel, W. R.; Bredas, J.-L. Quantitative Description of the Lateral Growth of Two-Dimensional Covalent Organic Frameworks Reveals Self-Templation Effects. ACS Mater. Lett. 2021, 3 (4), 398–405.

[3] Li, H.; Chavez, A. D.; Li, H.; Li, H.; Dichtel, W. R.; Bredas, J.-L. Nucleation and Growth of Covalent Organic Frameworks from Solution: The Example of COF-5. J. Am. Chem. Soc. 2017, 139 (45), 16310–16318.

[4]	Li, H.; Li, H.; Dai, Q.; Li, H.; Brédas, J.-L. Hydrolytic Stability of Boronate Ester-Linked Covalent Organic Frameworks. Adv. Theor. Simul. 2018, 1 (2), 1700015.

[5] ChemRxiv----------

[6] Shields, B. J.; Stevens, J.; Li, J.; Parasram, M.; Damani, F.; Alvarado, J. I. M.; Janey, J. M.; Adams, R. P.; Doyle, A. G. Bayesian Reaction Optimization as a Tool for Chemical Synthesis. Nature 2021, 590 (7844), 89–96.

[7] Chitturi, S. R.; Ramdas, A.; Wu, Y.; Rohr, B.; Ermon, S.; Dionne, J.; Jornada, F. H. da; Dunne, M.; Tassone, C.; Neiswanger, W.; Ratner, D. Targeted Materials Discovery Using Bayesian Algorithm Execution. npj Comput. Mater. 2024, 10 (1), 156.
