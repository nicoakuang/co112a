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
```
Runs an infinite loop that listens to the keyboard input.
When a key is pressed (any key), the program blackens the screen,
i.e. writes "black" in every pixel;
the screen should remain fully black as long as the key is pressed. 
When no key is pressed, the program clears the screen, i.e. writes
"white" in every pixel;
the screen should remain fully clear as long as no key is pressed.

In this program, the black screen loop will change the screen start from the top of the screen
while white screen loop will start from the bottom of the screen.

```
<img src="images/image4.png" width="300">
Translating asm program into hack

----------------------------------

#mult.asm notes:
``````
This program multiplies the values stored in RAM[0] and RAM[1] and saves the result in RAM[2].

The program achieves the multiplication by using a loop that runs R1 times. Within the loop, the value in RAM[2] is incremented by the value in RAM[0]. This process is repeated until the loop finishes. The initial value of RAM[2] is set to 0.

Example:
Assuming RAM[0] = 3 and RAM[1] = 2.

1. Increment RAM[2] by RAM[0]:
   RAM[0] = 3
   RAM[1] = 2
   RAM[2] = 3

2. Decrement the value in RAM[1] by one:
   RAM[0] = 3
   RAM[1] = 1
   RAM[2] = 3

3. Increment RAM[2] by RAM[0]:
   RAM[0] = 3
   RAM[1] = 1
   RAM[2] = 6

4. Decrement the value in RAM[1] by one:
   RAM[0] = 3
   RAM[1] = 0
   RAM[2] = 6

5. Since the value in RAM[1] is zero, the loop ends. The program stores the value in RAM[2] as the final result.
   RAM[0] = 3
   RAM[1] = 0
   RAM[2] = 6

``````
<img src="images/imag1.png" width="300">

Translating asm program into hack

<img src="images/image3.png" width="300">



refer from CPU emulator demo
https://www.youtube.com/watch?v=8XieZhHNFVY&list=PLYM3zllSC3SVdjWQUfedxssewHRS7EHuA&index=9

ChatGPT use percentage 50%, chatgpt help for understand