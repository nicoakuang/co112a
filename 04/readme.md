``````
Project 4

In this project you will write and execute some low-level machine language programs. In
particular, you will write programs in the Hack assembly language, use an assembler to translate
them into binary code, and test the resulting code. Since the Hack computer will be built only in
the next project, in this project you will run the programs on a CPU Emulator, designed to execute
binary code written in the Hack instruction set.

Tasks
Write and test two programs: Mult & Fill.asm
``````
-------------------
#fill.asm notes:

Program uses a loop to repeatedly set either the white or black color in the screen memory based on keyboard input. The loop for the white screen sets the corresponding memory locations to 0, and the loop for the black screen sets them to -1. The program keeps looping between these two states based on keyboard input.

<img src="images/image4.png" width="300">

Translating asm program into hack

Reference:

1. Fill the Screen when a key is pressed (Nand2Tetris)

https://youtu.be/7ftil7E7x-Y?si=gWBHn2kRtksC1RrY

----------------------------------

#mult.asm notes:
``````
This program multiplies the values stored in RAM[0] and RAM[1] and saves the result in RAM[2].

The program achieves the multiplication using a loop that runs R1 times. Within the loop:
  - Increment RAM[2] by the value in RAM[0].
  - Decrement the value in RAM[1] by one.

Example:
Assuming RAM[0] = 3 and RAM[1] = 2.

1. Increment RAM[2] by RAM[0]:
   RAM[0] = 3, RAM[1] = 2, RAM[2] = 3

2. Decrement the value in RAM[1] by one:
   RAM[0] = 3, RAM[1] = 1, RAM[2] = 3

3. Increment RAM[2] by RAM[0]:
   RAM[0] = 3, RAM[1] = 1, RAM[2] = 6

4. Decrement the value in RAM[1] by one:
   RAM[0] = 3, RAM[1] = 0, RAM[2] = 6

5. Since the value in RAM[1] is zero, the loop ends. The program stores the value in RAM[2] as the final result.
   RAM[0] = 3, RAM[1] = 0, RAM[2] = 6


``````
<img src="images/imag1.png" width="300">

Translating asm program into hack

<img src="images/image3.png" width="300">



refer from CPU emulator demo
https://www.youtube.com/watch?v=8XieZhHNFVY&list=PLYM3zllSC3SVdjWQUfedxssewHRS7EHuA&index=9

ChatGPT use percentage 50%, chatgpt help for understand