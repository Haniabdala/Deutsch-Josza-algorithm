# Deutsch’s Algorithm
## **Deutsch's Problem and Query Complexity**  
Let f : {0, 1} → {0, 1} be a one bit Boolean function. There exists only four different functions mapping bits to bits:

![Alt text](images/function.png)

Notice that, although bit-to-bit functions are “simple”, they might be very hard to compute.

## **Overview**  
Deutsch's problem is a fundamental problem in quantum computing, formulated as follows:  

> Given an oracle that computes a function **f: {0,1} → {0,1}**, determine whether the function is **constant** or **balanced**.  

- A **constant function** satisfies **f(0) = f(1)**.  
- A **balanced function** satisfies **f(0) ≠ f(1)**.  

From mathematical analysis, we observe that certain functions (e.g., **f₀ and f₃**) are constant, while others (**f₁ and f₂**) are balanced.  

## **Query Complexity**  
The complexity of solving Deutsch’s problem is measured in terms of the **number of queries** required to the oracle in the **worst-case scenario**. This is known as **query complexity**.  

Imagine an oracle as an **old wise sage on top of a high mountain**. Each time we seek an answer, we must hike up the mountain to ask a single question. Since this journey is extremely difficult, the focus is on minimizing the number of queries, as any pre-processing or post-processing steps are considered negligible in comparison.  

### **Classical Query Complexity**  
If we are given an oracle that takes **i ∈ {0,1}** as input and outputs **f(i) ∈ {0,1}**, how many queries do we need to determine whether **f** is constant or balanced?  

1. If we only query the oracle once (e.g., checking **f(0)**), we **cannot** determine whether the function is constant or balanced.
2. To be certain, we must **query twice** (checking both **f(0) and f(1)**). If **f(0) = f(1)**, the function is constant; otherwise, it is balanced.  

Thus, the **classical query complexity of Deutsch’s problem is two**.  

## **Quantum Advantage**  
Using **quantum computing**, Deutsch’s problem can be solved with just **one query** instead of two. This is achieved through quantum superposition and interference, forming the basis for the **Deutsch-Josza algorithm**, which extends this concept to more complex functions.  

---  
This repository contains an **implementation of Deutsch’s algorithm using Qiskit**, demonstrating the power of quantum computing in reducing query complexity.  

# Deutsch-Jozsa Algorithm

## Overview

The **Deutsch-Jozsa algorithm** is a quantum algorithm that solves the **Deutsch-Jozsa problem**. The problem involves determining whether a given function is **constant** or **balanced** using the fewest number of queries. The Deutsch-Jozsa algorithm demonstrates a clear quantum advantage, as it can solve this problem with just **one query** to the oracle, compared to the exponential number of queries required in classical algorithms.

This problem is an example of how quantum computing can provide exponential speedups over classical approaches by leveraging quantum superposition and interference.

## Deutsch-Jozsa Problem

Given a function \( f: \{0, 1\}^n \to \{0, 1\} \), the Deutsch-Jozsa problem asks whether the function is:

1. **Constant**: This means that the function outputs the same value (either 0 or 1) for all possible input strings \( x \in \{0, 1\}^n \).
   - Example of constant functions:
     - \( f(x) = 0 \) for all \( x \).
     - \( f(x) = 1 \) for all \( x \).

2. **Balanced**: This means that half of the possible input strings map to 0 and the other half map to 1. For a given \( n \)-bit input, there are \( 2^n \) possible input strings, so exactly half will map to 0 and the other half to 1.
   - Example of balanced functions for \( n = 2 \):
     - \( f(00) = 0, f(01) = 0, f(10) = 1, f(11) = 1 \).
     - \( f(00) = 1, f(01) = 1, f(10) = 0, f(11) = 0 \).

The goal is to determine if \( f \) is constant or balanced with the fewest queries to the oracle that implements this function. 

### Classical Approach

In the **classical case**, it is possible to determine whether the function is constant or balanced by making multiple queries to the function. In the worst-case scenario, you would need to query the function for more than half of the possible input strings to be sure of whether it is constant or balanced. This means that in the worst case, you would need **\( 2^{n-1} + 1 \) queries** to be certain.

### Quantum Approach (Deutsch-Jozsa Algorithm)

The **Deutsch-Jozsa algorithm** leverages quantum computing's ability to perform superposition and interference, allowing you to solve the problem with **just one query**. Here's how it works:

1. **Initialize qubits**: We start with \( n+1 \) qubits. The first \( n \) qubits represent the input to the oracle, and the last qubit is an auxiliary qubit initialized to \( |1\rangle \).
2. **Hadamard Transform**: We apply the Hadamard gate to all qubits, creating a superposition of all possible inputs.
3. **Oracle Query**: The oracle is applied to encode the problem’s function \( f \) into the quantum circuit. The oracle will implement either a constant or balanced function.
4. **Second Hadamard Transform**: After the oracle, a second Hadamard transform is applied to the first \( n \) qubits. This creates interference patterns based on the function's outputs.
5. **Measurement**: The first \( n \) qubits are measured. If the function is constant, the measurement will always return 0. If the function is balanced, the measurement will return 1.

This process allows the algorithm to distinguish between constant and balanced functions with just one query, offering an exponential speedup over classical methods.

## Code Implementation

The algorithm is implemented using **Qiskit**, a quantum computing framework, which allows us to simulate quantum circuits and execute quantum algorithms.
