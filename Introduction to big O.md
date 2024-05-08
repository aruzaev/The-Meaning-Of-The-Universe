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
- Algorithms should be **deterministic** which means that when a particular **input** is given, the same **output** should be given (There shouldn't be any randomness or unpredictability)
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

