# Deutsch’s Algorithm
## Deutsch’s problem
Let f : {0, 1} → {0, 1} be a one bit Boolean function. There exists only four different functions mapping bits to bits:

![Alt text](iamges/function.png)

Notice that, although bit-to-bit functions are “simple”, they might be very hard to compute.

Deutsch’s problem is then defined as following: given an oracle to computes a function f :
{0, 1} → {0, 1}, is the function f constant, or balanced ? A function is constant when f(0) = f(1),
and a bit-to-bit function is balanced if f(0) ̸= f(1). From Eq. (287) we can see that f0 and f3
are constant, and f1 and f2 are balanced. The complexity for solving Deutsch’s problem will be
quantified by how many queries to the oracle are required to solve it in the worst case. This
approach to complexity is called query complexity, and will be discussed in more generality later.
For now, we may imagine that querying the oracle is something expensive, and the only complexity
for solving the problem is given by how many times we need to access this oracle, all other steps
are viewed as cheap, hence with negligible complexity. One popular analogy for the oracle could be
an old wise mage on the top of a high mountain, which allows us to ask a single question each time
we hike the mountain. For each query to the oracle, we need to complete a full hike. Since this
hike is very hard, all the effort of pre-processing and post-processing is negligible when compared
to this long hike.

We now return to Deutsch’s problem. If we are given an oracle that takes i ∈ {0, 1} as
inputs and outputs f(i) ∈ {0, 1}. How many queries we need to ensure that the Boolean function
f : {0, 1} → {0, 1} is constant or balanced? Well, if we know the value of the function for one
bit, we have no idea if the function is constant or balanced. If the oracle tells us that f(0) = 0,
we still have no idea whether f is constant or balanced. The only way to solve this problem is by
querying the oracle twice, so that we know the value of f(0) and f(1). Hence, the (classical) query
complexity of Deutsch’s problem is two.
