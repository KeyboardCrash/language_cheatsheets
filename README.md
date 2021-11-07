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

## Approaching DP Problems
There is a sequence that can be followed to find a good DP solution

### Find the recursive relation
Analyze the problem to find what the 'optimal step' is.

i.e Robbing Houses you can choose to a.) Rob the current house or b.) Don't rob the current house
Robbing means that houses i-1 and i+1 cannot be robbed next.

Finding the most loot boils down to
    * Rob current house + loot from previous
    * Loot from previous and any prior to that

Thus we have

rob(i) = Math.max( rob(i-2) + currentValue, rob(i-1) )

### Recursive Soln (Top-down)
We can convert this recurrence to a code solution by just filling the base case
and re-calling the function

    if (i < 0):
        return 0
    return max(rob(nums, i-2) + nums[i], rob(nums, i-1))

### Recursive + Memoization (Top-down)
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

### Iterative + Memoization (Bottom-up)
Instead of recursion, we use loops to build up the memoization table

    memo = []
    # Base Case
    memo[0] = 0
    memo[1] = nums[0]

    for i to len(nums):
        memo[i+1] = max(memo[i], memo[i-1] + val)

    return memo[-1]

### Iterative + N Variables (Bottom-up)
Similar to the Iterative + Memoization solution, however we only need to remember
n variables rather than the entire table, thus we instantiate vars to hold our data instead

    prev1 = 0
    prev2 = 0
    for num in nums:
        tmp = prev1
        prev1 = max(prev2 + num, prev1)
        prev2 = tmp
    return prev1

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


