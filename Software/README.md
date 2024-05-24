Quick Sort & Integer Square Root
====================
<div align="justify">

This directory contains source files of user codes which will be executed on the phoeniX processor. In this directory, there are two subdirectories included:
- `quicksort`
- `rootsquare`

</div>

### Quick Sort

#### explanation of codes
<div align="justify">

We have two functions in this project . `PrintArr` & `QuickSort` .

The first one for print array before and after sort and another for execution of quick sort on a array.

First Choose a number in array as a pivot, and we need to make all the numbers on the left of the pivot are smaller than the pivot, all the numbers on the right of the pivot are bigger than the pivot.

this is the line that we realize that we can't go further.

```
beq  s4, s5, EndSortLoop
```

Next, look upon all numbers on the left of the pivot as new array, and do the same in numbers on the right side.
Repeat the step 1 and 2, until you can't divide more small array.

In the  two below part `Recursion1` and `Recursion1` we repeat quick sort algorithm recursively for sub array that generated in left and right of the pivot:

```
Recursion1:
    mv   a0, s0
    mv   a1, s1
    addi a2, s4, -1
    jal  ra, QuickSort
```

```
Recursion2:
    mv   a0, s0
    addi a1, s4, 1
    mv   a2, s2
    jal  ra, QuickSort
```


</div>

### Integer Square Root

#### explanation of codes
<div align="justify">
Basically this problem asks us to find  𝑦 of  𝑦=√⌊𝑥⌋  with given variable 𝑥.
where 𝑥 is a non-negative integer that ranges between [0,2^31−1].

The solution exploits the fact that we are looking for an integer, and the relationship between 𝑥 and √𝑦
 follows a strict order. So we can just enumerate each bit to find the integer that is closest to 𝑥.

First Attempts to retrieve the MSB of that given number 𝑥.
Multiply the number by 0x07C4ACDD. Shift it by 27 bits.
Lookup the table. Now you got the index of the MSB of 𝑥 (0-based index).

 Here is where we call ```floor_sqrt``` function for example number 1024 :

```
  li  a0, 1024
  jal ra, floor_sqrt
```

and here we print the result:

```
  mv a1, a0             # integer to print
  li a0, 1              # print int environment call (1)
  ecall
```

### Contributers
* [Setare Khosravi](https://github.com/setarekhosravi)
* [Mahshid Hosseini](https://github.com/MahshidHosseinii)
