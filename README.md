# Language Cheatsheets + Algorithm Cheatsheet
Personal repository for storing algorithm notes and cheatsheets for quick development in different languages.

Will add more things that I may find useful while leetcoding and learning how to solve new methods.

# Algorithms
List of various algorithm development techniques. These are used to solve the most common problems.

## Dynamic Programming

Problem solving strategy to use math and computer science together

Use the pattern and apply it to a future iteration of the problem

When a problem has optimal substructure and repeating subproblems, DP can be used
to re-use previously computed subproblems to solve later problems

Two Properties of DP:
   
* Optimal Substructure
    * Optimal solution to a problem contains the optimal solutions of its subproblems
* Overlapping subproblems
    * A recursive solution contains a small number of distinct subproblems

There are two types of DP Approaches; Bottom-up and Top-down.

### Top-Down / Memoization
A method to reduce the number of calls we are doing by caching the result of function calls.
This allows us to reduce the total amount of work done by the algorithm.

<b>This uses a type of caching table with efficient lookup times, like a hash table.</b>

Problems will branch into leaves, and transverses back up towards the root to reach a final solution.

Example:

    factorial(n):
        memo = {}
        if n == 0:
            return 1
        else if n in memo:
            return memo
        else
            ans = factorial(n-1) * factorial(n)
            memo.push(ans)
            return ans

### Bottom-up / Tabulation
Not using recursion at all, and also saves time and space.
Solves the last possible sub-problems first and uses partial results to arrive at the final result.
Can use for loops to generate a table instead of recursion down into base cases.

<b>This method allows you to reduce cost by just using previous numbers instead of computing a full table to find a solution.</b>

Example:

    factorial(n):  
        fact = 1  
        else:  
            for num in range(2, n+1):  
                fact *= num  
        return num  

### Approaching DP Problems
There is a sequence that can be followed to find a good DP solution

#### <b>Find the recursive relation</b>

    Analyze the problem to find what the 'optimal step' is.
    
    e.g Robbing Houses you can choose to
        a.) Rob the current house or
        b.) Don't rob the current house
        
    Robbing means that houses i-1 and i+1 cannot be robbed next.
    
    For this instance, finding the most value boils down to:
    
        1. Rob current house + loot from previous
        2. Loot from previous and any prior to that
    
    Thus we have
    
        rob(i) = Math.max( rob(i-2) + currentValue, rob(i-1) )

#### <b>Recursive Soln (Top-down)</b>
We can convert this recurrence to a code solution by just filling the base case
and re-calling the function

    if (i < 0):
        return 0
    return max(rob(nums, i-2) + nums[i], rob(nums, i-1))

#### <b>Recursive + Memoization (Top-down)</b>
We can use a memoization table to remember the values that we solved.
This will similarly use the recursion method, however we check for values, then compute, then add to the memoization table.

    if (i < 0):
        return 0
    if memo[i] > 0:
        return memo[i]
    result = max(rob(nums, i-2) + nums[i], rob(nums, i-1))
    if result not in memo:
        memo[i] = result
    return result

#### <b>Iterative + Memoization (Bottom-up)</b>
Instead of recursion, we use loops to build up the memoization table

    memo = []
    # Base Case
    memo[0] = 0
    memo[1] = nums[0]

    for i to len(nums):
        memo[i+1] = max(memo[i], memo[i-1] + val)

    return memo[-1]

#### <b>Iterative + N Variables (Bottom-up)</b>
Similar to the Iterative + Memoization solution, however we only need to remember
n variables rather than the entire table, thus we instantiate vars to hold our data instead

    prev1 = 0
    prev2 = 0
    for num in nums:
        tmp = prev1
        prev1 = max(prev2 + num, prev1)
        prev2 = tmp
    return prev1

### Common Subproblem problem types

#### SequenceF
Given a sequence n of x1, x2, ..., xn, then the subproblem will involve some sequence of x1, x2, ..., xi

#### Sequence of n in random order
Given a sequence n of x1, x2, ..., xn, the subproblem will require us to sort the input and return some optimal subsequence of x1, x2, ..., xi

#### Multiple sequences
Given an input x1, x2, ..., xn and y1, y2, ..., yn, the subproblem will be an appropriate subsequence of these two sequences such that x1, x2, ..., xi and y1, y2, ..., yi

#### Unique sequence
Given an input x1, x2, ..., xn, the subproblem will need to expand outward from the middle forming a subsequence of x1, xi+1, ..., xj

#### Matrix
Given a 2 dimension array or matrix of Amn, the subproblem will boil down to some submatrix of Aij

### Common DP Patterns


#### Fibonacci Numbers

* [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) Easy
* [House Robber](https://leetcode.com/problems/house-robber/) Easy
* [Fibonacci Number](https://leetcode.com/problems/fibonacci-number/) Easy

#### Zero / One Knapsack

* [Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/) Medium
* [Target Sum](https://leetcode.com/problems/target-sum/) Medium

#### Unbounded Knapsack

* [Coin Change](https://leetcode.com/problems/coin-change/) Medium
* [Coin Change 2](https://leetcode.com/problems/coin-change-2/) Medium
* [Minimum Cost for Tickets](https://leetcode.com/problems/minimum-cost-for-tickets/) Medium

#### Longest Common Subsequence

* [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/) Medium
* [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/) Medium
* [Edit Distance](https://leetcode.com/problems/edit-distance/) Hard
* [Distinct Subsequences](https://leetcode.com/problems/distinct-subsequences/) Hard

#### Palindrome

* [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/) Medium
* [Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/) Medium
* [Longest Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/) Medium

### Common Applications of Dynamic Programming
* [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/) Medium
* [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)
* [Longest Common Substring (e.g Max Length of Repeated Subarray)](https://leetcode.com/problems/maximum-length-of-repeated-subarray/) Medium
* [Bellman-Ford Algorithm (Used in weighted graph min cost paths)](https://leetcode.com/problems/network-delay-time/) Medium
* Chain Matrix Multiplication
* [Subset sums (e.g Partition sum)](https://leetcode.com/problems/partition-equal-subset-sum/) Medium
* [Knapsack Problem (e.g Coin Change)](https://leetcode.com/problems/coin-change/) Medium

## Brute Force Algorithms
Simplest algorithm at the expense of space and time complexity. Used to formulate a solution that is conceptually simple but runs unnecessary computations.

Will typically have O(n^2) or worse runtime.

Example:

    contains(arr, n):
        arr = [1, 2, 3, 4, 5]
        for i in range(len(arr)):
            if n == arr[i]:
                return True

## Greedy Algorithms
A decision is made at a point which is considered optimal without considering the future.

The local best option is chosen, and is considered the global optimal.

Two choices are available for these algorithms:
* Greedily Choosing
    * The current choice will be picked optimally
* Optimal Substructure Property
    * If an optimal solution can be found by retrieving the optimal solution to its subproblems

### Common Applications of Greedy Algorithms
* Sorting
    * Selection Sort, Topological sort
* Prim's and Kruskal's graph algorithms
* Simple coin change problem (1, 2, 5)
* Fractional Knapsack Problem
* Job / Interval Scheduling problems

## Recursive Algorithm
The calling of itself to solve subproblems. Think about existing cases and solutions of the simplest subproblem, and the complexity will be handled by breaking the big problem into subproblems.

While a powerful tool, memory management should be considered as well as considering the size of
the recursion stack.

A base case must be considered in order to stop infinite recursion

Example:

    factorial(n):
        if (n == 0):
            return 1
        return n * factorial(n - 1)

## Backtracing Algorithm
Improves on the brute force approach. Starts at one of the possible available solutions and attempts
to solve it if possible. If not, then it continues with the next best choice

### Common Applications of Backtracing Algorithms
* Generating all Binary Strings
* N-Queens Problem
* Knapsack Problem
* Graph Coloring Problem

## Divide & Conquer Algorithm
Also a problem method to solve algorithm problems. Divides the problem into subproblems and solves each of them before combining them to form the solution of the given problem.

Relies on being able to <b>divide the problem into subproblems</b> and <b>solve the subproblems</b>

### Common Applications of D&C Algorithms
* Binary Search
* Merge Sort and Quick Sort
* Median Finding
* Matrix Multiplication

# Design Principles
Most commonly used paradigms in industry. They are used in practice to develop 'good' code such that they follow a set of rules that should be followed for consistency rather than arguing over inconsistencies in code practice.

Using design principles removes the need to debate simple tradeoffs, and helps designers not worry about complex problems.

## SOLID
SOLID is a set of the most popular design principles that are used in OO software development.

### Single Responsibility Principle
Classes should only have one reason to change - ie a class should only be responsible for one job.

### Open-Closed Principle
Objects or entities should be open for extension without modifying the class itself
The abstractions shouldn't handle what the extendables should handle.

### Liskov Substitution Principle
Every subclass or derived class should be substitutable for their base or parent class.

### Interface Segregation Principle
A client should not implement an interface that it doesn't use, or clients shouldn't be forced to depend on methods they do not use.

Instead of implementing a general property that is of no use to most inherited objects, instead create another interface to implement the property.

### Dependency Inversion Principle
Entities must depend on abstractions, not concretions. High level models must not depend on the low-level module, but should depend on abstraction.

This principle allows for decoupling.

Eg. A high-level password-reset function should not rely on the low-level MySQLConnection.\
Instead, a DBConnectionInterface will allow for minimal coupling to the existing DB module.

## Code Reuse
A principle for the reuse of existing software (knowledge) to build new software, following reusability principles.

## DRY (Don't Repeat Yourself)
A principle of software development to reduce repetitions in software patterns through the use of data normalization and abstractions.

## KISS (Keep it Simple Stupid)
States that most systems work best when simple rather than complicated. Thus, simplicity should be a key goal in design.

## YAGNI (You Ain't Gonna Need It)
States that to always implement things when you actually need them, never before you need them.


