## Registers

https://wiki.skullsecurity.org/index.php?title=Registers

A register is like a variable, except that there are a fixed number of registers. Each register is a special spot in the CPU where a single value is stored.

A register is the only place where math can be done (addition, subtraction, etc). Registers frequently hold pointers which reference memory. Movement of values between registers and memory is very common.

## General Purpose Registers

This section will look at the 8 general purpose registers on the x86 architecture.

## **eax**

**eax** is a 32-bit general-purpose register with two common uses: to store the return value of a function and as a special register for certain calculations. It is technically a volatile register, since the value isn't preserved.

Instead, its value is set to the return value of a function before a function returns. Other than **esp**, this is probably the most important register to remember for this reason. **eax** is also used specifically in certain calculations, such as multiplication and division, as a special register. That use will be examined in the instructions section.

Here is an example of a function returning in C:

```
return 3;  // Return the value 3
```

Here's the same code in assembly:

```
mov eax, 3 ; Set eax (the return value) to 3
ret        ; Return
```

## **ebx**

**ebx** is a non-volatile general-purpose register. It has no specific uses, but is often set to a commonly used value (such as 0) throughout a function to speed up calculations.

## **ecx**

**ecx** is a volatile general-purpose register that is occasionally used as a function parameter or as a loop counter.

Functions of the "\_\_fastcall" convention pass the first two parameters to a function using **ecx** and **edx**. Additionally, when calling a member function of a class, a pointer to that class is often passed in ecx no matter what the calling convention is.

Additionally, **ecx** is often used as a loop counter. for loops generally, although not always, set the accumulator variable to **ecx**. rep- instructions also use ecx as a counter, automatically decrementing it till it reaches 0. This class of function will be discussed in a later section.

## **edx**

**edx** is a volatile general-purpose register that is occasionally used as a function parameter. Like **ecx**, **edx** is used for "\_\_fastcall" functions.

Besides fastcall, **edx** is generally used for storing short-term variables within a function.

## **esi**

**esi** is a non-volatile general-purpose register that is often used as a pointer. Specifically, for "rep-" class instructions, which require a source and a destination for data, **esi** points to the "source". **esi** often stores data that is used throughout a function because it doesn't change.

## **edi**

**edi** is a non-volatile general-purpose register that is often used as a pointer. It is similar to **esi**, except that it is generally used as a destination for data.

## **ebp**

**ebp** is a non-volatile general-purpose register that has two distinct uses depending on compile settings: it is either the frame pointer or a general purpose register.

If compilation is not optimized, or code is written by hand, **ebp** keeps track of where the stack is at the beginning of a function (the stack will be explained in great detail in a later section). Because the stack changes throughout a function, having **ebp** set to the original value allows variables stored on the stack to be referenced easily. This will be explored in detail when the stack is explained.

If compilation is optimized, **ebp** is used as a general register for storing any kind of data, while calculations for the stack pointer are done based on the stack pointer moving (which gets confusing -- luckily, IDA automatically detects and corrects a moving stack pointer!)

## **esp**

**esp** is a special register that stores a pointer to the top of the stack (the top is actually at a lower virtual address than the bottom as the stack grows downwards in memory towards the heap). Math is rarely done directly on **esp**, and the value of **esp** must be the same at the beginning and the end of each function. **esp** will be examined in much greater detail in a later section.
