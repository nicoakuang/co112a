``````
Project 5

In this project you will integrate the ALU and RAM devices built in projects 2 and 3 into a computer
system capable of executing programs written in the machine language introduced in project 4.

Objective, Build the following chips:
Memory, CPU, Computer    

precentage got help by chatgpt 50%

``````
-------------------
#Memory notes:

<img src="images/image.png" width="300">

loadM = load for memory, 
loadS = load for screen

Utilizes subcomponents like RAM16K, Screen, and Keyboard to handle specific memory regions and I/O mappings.

----------------------------------

#CPU notes:
<img src="images/image6.png" width="300">

Reference
1. from nand2tetris chapter 6, C-Instruction

https://b1391bd6-da3d-477d-8c01-38cdf774495a.filesusr.com/ugd/56440f_65a2d8eef0ed4e0ea2471030206269b5.pdf 



refer from nand2tetris chapter 5, CPU abstraction, implementation
https://drive.google.com/file/d/1nEptWuRpFF9zmqlKYq6s1UfDB_dd16vx/view 



```instruction[15] : to differ whether an instruction is an Address or a C-Instruction
instruction[12] : a
instruction[11] : c1
instruction[10] : c2
instruction[9]  : c3
instruction[8]  : c4
instruction[7]  : c5
instruction[6]  : c6
instruction[5]  : d1
instruction[4]  : d2
instruction[3]  : d3
instruction[2]  : j1
instruction[1]  : j2
instruction[0]  : j3
``````
-----------------------
#Computer notes:

<img src="images/image1.png" width="300">

refer: 

1. from nand2tetris chapter 5, Computer Architecture, Testing Computer

https://drive.google.com/file/d/1nEptWuRpFF9zmqlKYq6s1UfDB_dd16vx/view

2. 計算機結構 第九週 -- ＣＰＵ

https://www.youtube.com/live/W4KfjWvRsCE?si=MIEocsei34-6FBiW

3.計算機結構 第十週 -- CPU+Memory = Computer

https://www.youtube.com/live/v6Jxe8PsR8A?si=H23n9-vvJ1eJ13Ih