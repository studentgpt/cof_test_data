
# MlCOFSyn
<img alt="Static Badge" src="https://img.shields.io/badge/c++-8.1.0-red?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/python-3.12-blue?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/PyQt5-green?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/sklearn-1.4.2-black?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/numpy-1.26.4-pink?style=flat"> <img alt="Static Badge" src="https://img.shields.io/badge/pandas-2.2.2-orange?style=flat">

MlCOFSyn is a machine learning framework designed for the synthesis of two-dimensional covalent organic frameworks (2D COFs), aiming to enhance synthesis efficiency and lower technical barriers.MlCOFSyn simplifies the parameter input process through machine learning algorithms and an intuitive graphical interface, enabling it to run on consumer-grade computers. This makes it an accessible tool for non-expert users. By addressing the lack of theoretical tools in the field of 2D COF synthesis, the MlCOFSyn framework represents a significant advancement in facilitating related research and synthesis.The framework offers the following core functionalities:

1. ​**Prediction**​: Predicts the crystal size based on the input monomer addition sequence using the NEgen1<sup>[1]</sup>
2. ​**Design**​: Derives the required monomer addition sequence by specifying the target crystal size.
3. ​**Optimization**​: Optimizes the synthesis pathway to produce larger crystals.

**A Machine Learning Framework to Facilitate the Synthesis of 2D Covalent Organic Frameworks**

## Content
### **1.Prediction Task**
`python MlCOFSyn/negen1o_ui/NEgen1_start.py`

**After startup, the left panel is used for initializing parameters, while the right panel is for generating addition lists. Clicking on the list allows the generation of different types of addition lists.**
![image1](https://github.com/studentgpt/test1/blob/main/image/NEgen1o_1_2.png)
**Enter the sequence in the "NEgen1oOutput" section to obtain the final output result.**
![image3](https://github.com/studentgpt/test1/blob/main/image/NEgen1o_3.png)
**Finally, click "Output" in the "DataProcessing" section to view all corresponding result details and crystal distributions.**
![image4](https://github.com/studentgpt/test1/blob/3733c2ca3381163b403e7604c96d81fef48f1719/image/Negen1o_4.png?raw=true)

### **2.Optimization Task**

`python MlCOFSyn/bayesian/main_ui_optimization.py `
**After launching `main_ui_optimization.py`, entering the initialization parameters will redirect you to the optimization page. Input the required reaction    space and termination conditions, then click "Start Bayesian Optimization" to initiate the optimization process.**
![bayesian1](https://github.com/studentgpt/test1/blob/main/image/bayesian_1.png)

### **3.Design Task**
`python MlCOFSyn/design/multibax-sklearn-main/main_ui_design.py `
After launching `main_ui_design.py`, entering the initialization parameters will redirect you to the Design page. Input the required optimization space and the corresponding termination conditions, then click ""Start Bayesian Design " to initiate the optimization process.	
![bayesian1](https://github.com/studentgpt/test1/blob/main/image/design1.png)

## Author

👤 **Yue Shi**

👤 **Jiaxin Tian**

👤 **Haoyuan Li**


## Contributing

Contributions, issues and feature requests are welcome!

## Reference

[1] Tian, J.; Treaster, K. A.; Xiong, L.; Wang, Z.; Evans, A. M.; Li, H. Taming Two-Dimensional Polymerization by a Machine-Learning Discovered Crystallization Model. Angew. Chem. Int. Ed. 2024, 63 (39), e202408937. https://doi.org/10.1002/anie.202408937 github: https://github.com/Tia-tie-zhu/NEgen1.git
