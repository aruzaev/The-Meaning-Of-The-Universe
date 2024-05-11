# [[Introduction to big O]]
[[Leetcode Crash Course]]

## What are algorithms?

An algorithm is a recipe that computers follow, it can also be called a series of step by step instructions that a computer follows in order to solve a problem

Algorithms have one point of entry (input), and one point of exit (output) and each program that you will write will follow this criteria

The output will be the answer or result of a question for the **input**

***Example***
If you had an array called `nums` filled with positive integers and you wanted to find out what the largest number inside of `nums` was, you could do something like this:
1. Create a temporary variable called `largestNumber` and set it to the default value of 0
2. Iterate over each element inside of `nums` (for each num inside of nums)
3. If `num` (or any counter variable that you choose) is greater than `largestNumber`
	1. set `largestNumber = num` 
4. Print out `largestNumber`

When working with Leetcode and interview questions, the following rules must be implemented:
- Algorithms should be **deterministic** which means that when a particular **input** is given, the same **output** should be given in return (There shouldn't be any randomness or unpredictability)
- An algorithm should work for any arbitrary valid **input**. In the numbers example, there can be an infinite amount of possibilities for our array with different values and sizes. However they can only work for valid inputs, meaning that only positive integers would work

The above can also be used in normal programming, as it ensures that the code is clear and simple

## Big O

Big O is a notation that is commonly used to describe the computational complexity of an algorithm.

There are two parts to computational complexity:
- Time complexity
- Space complexity

**Time complexity** of an algorithm is the amount of time that a program needs to run to completion based on it's **input size** (an efficient program will be able to run quickly no matter the size)

As the input size **grows**, how much **longer** does the algorithm take to complete?

**Space complexity** of an algorithm is the amount of memory that the algorithm needs to use given its **input size**

As the input size **grows**, how much **more memory** does the algorithm use?

Usually people mainly care about the time complexity more than space complexity, however both are really important to take into account

## How complexity works

Complexity is usually described by a function (math formula)

The most common variable (also called an argument) that is used for complexity is `n`, this usually represents the length of an array or string that is used for the input

Thus, it can be said that `n` is equal to `nums`

The length of the `nums` or `n` **directly** influences the behaviour of the algorithm

The longer that the array of numbers is, the more numbers that we have to iterate through, which takes the algorithm **longer to complete**

When complexity is written, the function is enclosed in a capital O, here are some examples:

- O(n)
- O(n^2)
- O(2^n)
- O(log n)
- O(n * m)

In the last example, m can be used as any arbitrary variable. It can be used for problems when we have two arrays, as `n` can represent the first array and `m` the second

## Calculating complexity

The function that you have for your algorithm calculates the number of operations or amount of memory (depending on if you're looking at time or space) your algorithm uses depending on its **input size**

The numbers example above uses a time complexity of O(n)

In the example, n is the size of our array and as such determines how many operations (or steps) our algorithm will execute (if the array is the size of 10,000 elements it will execute 10,000 times)

Time complexity isn't meant to be a way to measure **exactly** how many operations an algorithm will need (creating the `largestNum = 0` variable and outputting the final answer would take 12 operations if the size of the array is 10)

Instead, **the point of time complexity** is to describe how the number of operations changes as the input changes

The number of operations depends on `n` or `nums`, NOT the other misc. steps

### Rules

1. We ignore constants

   Big O notation focuses on describing how the number of operations grows with input size, not the exact number of operations that are found in the entire program
   
   This means that functions such as O(9999999n), O(Sn), and O(500n) are all the same as O(n)
   
   ***Example***
   Lets say that Algorithm A has `n` operations and Algorithm B has `5n` operations, when `n = 100`, A uses 100 operations and B uses 500
   
   However, when we double the number `n` of elements in the array, A now uses 200 operations and B uses 1000, even though the operations are larger in B, both algorithms still need **double the operations, no matter what their constants are**
   
   The main point of figuring out complexity is to see how the algorithm changes as **the input changes**, meaning that it doesn't matter that B is 5x slower because the number of operations changes **linearly** in both algorithms, both algorithms are O(n)
   
   That is the main thing that we care about, how the performance of the algorithm changes when the number of inputs (size of the data) change

2. Variables tend to infinity
   
   Big O considers the change in behaviour of the algorithm as the input size grows indefinitely large (tends to infinity)
   
   This essentially means that all of the variables that are added or subtracted from the main `n` can be ignored since as the input size grows to **infinity**, those additions or subtractions become pretty much close to zero
   
   ***Example***
   O(2^n + n^2 - 500n) = O(2^n)
   
   If we had an algorithm that required n + 500 operations with a time complexity of O(n)
   
   When `n` is small, the 500 makes a big impact on the algorithm, however as we increase the size of `n` towards infinity. 500 becomes nothing

The algorithm with the best complexity possible is O(1), which means that the algorithm **always** uses the same amount of resources, no matter the size of the input

The runtime is completely independent of the input size, but it doesn't necessarily mean that a program is fast since O(50000000) = O(1)

When discussing complexity, there are usually three cases:

- best case scenario 
	- the most optimal conditions under which an algorithm can operate, represents the minimum time or space required by the algorithm. This isn't a good thing because it assumes ideal conditions exist which almost never happens
- average case
	- considers the performance of the algorithm under typical conditions. Requires the use of probabilistic analysis to figure out the average case across all possible inputs. Even though this is better than best case it still has a fair amount of assumptions with probability things like distribution
- worst case scenario
	- assumes the most challenging conditions under which an algorithm can operate. It provides the uppermost bound for the time and space the algorithm needs to be able to operate. Using the worst case is best practice because it guarantees that the algorithm won't exceed the complexity in any situation

For most algorithms, all of these will be equal, however some algorithms will be slightly different

When choosing one to represent the algorithm's space or time complexity, you should never do to best case scenario, instead do the **worst case** and talk about the difference between the cases

The reason for this is because it allows for us to see if the system can handle the maximum expected load without issues in performance, which gives us a guarantee that the algorithm will perform well under any kind of circumstances

## Analyzing time complexity

```
// Given an integer array "arr" with length n,

for (int num: arr) {
    print(num)
}
```

This algorithm has a time complexity of O(n); this means that for each iteration of the loop, we make a print

Each element of the array `arr` is printed exactly once
If the array has `n` elements, there will be `n` print operations

This print costs us O(1). Since the for loop iterates `n` times, we get a time complexity of O(1 * n) = O(n)

This means that we will have a direct execution where the time needed to execute is **directly proportional** to the number of elements in the array

If we double the size of the array, we will double the amount of print statements executed, which will double the execution time

```
// Given an integer array "arr" with length n,

for (int num: arr) {
    for (int i = 0; i < 500,000; i++) {
        print(num)
    }
}
```

This algorithm also has a time complexity of O(n), for each loop iteration, we are printing, which costs us O(1) for the print statement

For each element of the array, the inner loop will execute 500,000 print executions, thereby causing a significant slowdown of the algorithm

Since there is a constant factor to it, it would be described as O(n * 500000), however the constant will be ignored

And once again, since the for loop iterates `n` times, we get a time complexity of O(n)

**Important**
Although constants are usually ignored when talking about increasing `n` input size (which is why the algorithm is still O(n) like the first one), it is worth noting that executing 500,000 print statements after each element iteration will significantly slow things down

The algorithm scales very poorly due to the high constant factor

```
// Given an integer array "arr" with length n,

for (int num: arr) {
    for (int num2: arr) {
        print(num * num2)
    }
}
```

This algorithm has a time complexity of O(n^2), for each inner loop iteration, we perform a multiplication and print, which both cost O(1)

Both the inner and outer loops cost O(n) because each loop runs `n` times, this means that we get a complexity of O(n * n) = O(n^2)

This means that if the size of the array doubles, then the total amount of operations will quadruple

This makes it quite practical and efficient for small arrays however scaling in the future will be very poor

```
// Given integer arrays "arr" with length n and "arr2" with length m,

for (int num: arr) {
    print(num)
}

for (int num: arr) {
    print(num)
}

for (int num: arr2) {
    print(num)
}
```

This algorithm has a time complexity of O(n + m)

The first two loops both cost O(n) and the final loop costs O(m) since it uses a different dataset

This means that there's a time complexity of O(2n + m) = O(n + m)

```
// Given an integer array "arr" with length n,

for (int i = 0; i < arr.length; i++) {
    for (int j = i; j < arr.length; j++) {
        print(arr[i] + arr[j])
    }
}
```


