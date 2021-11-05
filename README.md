# Language Cheatsheets + Algorithm Cheatsheet

# Dynamic Programming

Problem solving strategy to use math and computer science together

Use the pattern and apply it to a future iteration of the problem

When a problem has optimal substructure and repeating subproblems, DP can be used
to re-use previously computed subproblems to solve later problems

Two Properties of DP:
* Optimal Substructure
- Optimal solution to a problem contains the optimal solutions of its subproblems
* Overlapping subproblems
- A recursive solution contains a small number of distinct subproblems

There are two types of DP Approaches; Bottom-up and Top-down

## Top-Down / Memoization
A method to reduce the number of calls we are doing by caching the result of function calls
This allows us to reduce the total amount of work done by the algorithm
<b> This uses a type of caching table with efficient lookup times, loke a hash table </b>
Problems will branch into leaves, and transverses back up towards the root

Example:
`
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
`
## Bottom-up / Tabulation
Not using recursion at all, and also saves time and space.
Solves the last possible sub-problems first and uses partial results to arrive at the final result


Example:
`
factorial(n):
    fact = 1
    else:
        for num in range(2, n+1):
            fact *= num
    return num
`
## Common Applications of Dynamic Programming
* Longest Common Subsequence, Longest Increasing Subsequence, Longest Common Substring
* Bellman-Ford algorithm
* Chain Matrix Multiplication
* Subset sums
* Knapsack Problem

# Brute Force Algorithms

# Greedy Algorithms

# Recursive Algorithm

# Backtracing Algorithm

# Divide & Conquer Algorithm


