+++
title = 'The simplicity of C'
date = 2024-07-19
draft = false
+++

### 'An idiot admires complexity, a genius admires simplicity' - Terry A Davis

The more i've programmed in C the more i've admired it's simplicity.
Even when i'm working on different programming languages I always try to think of problems in terms of how it would be implemented in C. 

I want to give examples of features and explain why it's simpler than other programming languages.

### 1. The C compilers
The compiler has a very simple job; to turn C code to assembly (machine code). The compiler does many other stuffs like optimization and linking etc but turning C code to assembly is it's main job. 
And the compiler does this task in a non complicated way

![alt text](/c_cat.PNG)

When we look at the assembly produced by gcc for the given code this is what we get.

![](/c_assembly_cat.PNG)

If you  just know some basic assembly we can reason about the things that the compiler produced. It loaded some constant string called "Hello world", it has a section called main where it loaded the number 2 and 100 to some register, it multiplied them and called the printf function and exited.

As a programmer we should learn to treat compiler as a friend. Compiler isn't gonna fix all the bugs for you, it is gonna point out error, it's not magic, it's a tool. 

### 2. Low level
If gcc is a translater from c to assembly, then C is just a high level assembly, turns out it really helps thinking that way.

Unlike other high level languages C dosen't limit you from thinking in low level as assembly. You pretty much have full controll over what goes into your executable.
Some of the few things c provides that helps you get full control of your programs are; manual memory management, control over struct layout, pointers, c calling convention. 








