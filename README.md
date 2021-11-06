# Language Cheatsheets + Algorithm Cheatsheet

# Dynamic Programming

Problem solving strategy to use math and computer science together

Use the pattern and apply it to a future iteration of the problem

When a problem has optimal substructure and repeating subproblems, DP can be used
to re-use previously computed subproblems to solve later problems

Two Properties of DP:
* Optimal Substructure
    * Optimal solution to a problem contains the optimal solutions of its subproblems
* Overlapping subproblems
    * A recursive solution contains a small number of distinct subproblems

There are two types of DP Approaches; Bottom-up and Top-down

## Top-Down / Memoization
A method to reduce the number of calls we are doing by caching the result of function calls.
This allows us to reduce the total amount of work done by the algorithm.\
<b>This uses a type of caching table with efficient lookup times, like a hash table.</b>\
Problems will branch into leaves, and transverses back up towards the root

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

## Bottom-up / Tabulation
Not using recursion at all, and also saves time and space.
Solves the last possible sub-problems first and uses partial results to arrive at the final result

<b>This method allows you to reduce cost by just using previous numbers instead of computing a table</b>

Example:

    factorial(n):  
        fact = 1  
        else:  
            for num in range(2, n+1):  
                fact *= num  
        return num  

## Common Applications of Dynamic Programming
* Longest Common Subsequence, Longest Increasing Subsequence, Longest Common Substring
* Bellman-Ford algorithm
* Chain Matrix Multiplication
* Subset sums
* Knapsack Problem

# Brute Force Algorithms
Simplest algorithm at the expense of space and time complexity. Used to formulate a solution that is conceptually simple but runs unnecessary computations.\

Will typically have O(n^2) or worse runtime.

Example:

    contains(arr, n):
        arr = [1, 2, 3, 4, 5]
        for i in range(len(arr)):
            if n == arr[i]:
                return True

# Greedy Algorithms
A decision is made at a point which is considered optimal without considering the future.

The local best option is chosen, and is considered the global optimal.

Two choices are available for these algorithms:
* Greedily Choosing
    * The current choice will be picked optimally
* Optimal Substructure Property
    * If an optimal solution can be found by retrieving the optimal solution to its subproblems

## Common Applications of Greedy Algorithms
* Sorting
    * Selection Sort, Topological sort
* Prim's and Kruskal's graph algorithms
* Coin change problem
* Fractional Knapsack Problem
* Job / Interval Scheduling problems

# Recursive Algorithm
The calling of itself to solve subproblems. Think about existing cases and solutions of the simplest subproblem, and the complexity will be handled by breaking the big problem into subproblems.

While a powerful tool, memory management should be considered as well as considering the size of
the recursion stack.

A base case must be considered in order to stop infinite recursion

Example:

    factorial(n):
        if (n == 0):
            return 1
        return n * factorial(n - 1)

# Backtracing Algorithm
Improves on the brute force approach. Starts at one of the possible available solutions and attempts
to solve it if possible. If not, then it continues with the next best choice

## Common Applications of Backtracing Algorithms
* Generating all Binary Strings
* N-Queens Problem
* Knapsack Problem
* Graph Coloring Problem

# Divide & Conquer Algorithm
Also a problem method to solve algorithm problems. Divides the problem into subproblems and solves each of them before combining them to form the solution of the given problem.

Relies on being able to <b>divide the problem into subproblems</b> and <b>solve the subproblems</b>

## Common Applications of D&C Algorithms
* Binary Search
* Merge Sort and Quick Sort
* Median Finding
* Matrix Multiplication


