## EXP.NO.6-Simulation-of-Hamming-and-Shannon-Fano-Code

## AIM:
 Simulation of Hamming and Shannon-Fano Code

## SOFTWARE REQUIRED:

 Google Collab

## ALGORITHMS:

### Huffman Coding Algorithm:

Input the probability of each symbol/message (e.g., P₁, P₂, ..., Pₙ).

Create leaf nodes for each symbol and sort them in increasing order of probability.

Repeat until only one node remains:
a. Pick the two nodes with the lowest probabilities.
b. Combine them into a new node. The probability of this node = sum of the two.
c. Assign 0 to one branch and 1 to the other (left → 0, right → 1).

After building the tree, trace the path from root to each symbol to assign the binary code:

Going left = 0

Going right = 1

The result is a prefix-free binary code for each symbol.

### Shannon–Fano Coding Algorithm:

Input the probabilities P₁, P₂, ..., Pₙ of each symbol.

Sort the symbols in descending order of their probability.

Divide the list into two parts such that the total probability of both parts is nearly equal.

Assign 0 to the upper group and 1 to the lower group.

Recursively apply steps 3–4 to each group:

Keep appending the new bit (0 or 1) to the code as you go down each level.

After all divisions, each symbol will have a unique binary code.


## PROGRAM:
### Huffman and Shannon-Fano coding
```
import numpy as np
import math 
L  = 0
hs = 0
p = []
lk = []
n = int(input("Enter the number of Samples : "))
for i in range (n): 
    pr = float(input(f"Enter the probability of sample values {i + 1}: "))  
    p.append(pr)
for j in range (n): 
    l = float(input(f"Enter the length of the sample values {j + 1}: "))  
    lk.append(l)
# Avg length of the code word
for k in range (n):
    Avg1 = p[k] * lk[k]
    L = L + Avg1
# Entropy
for k in range (n):
    e = p[k] * math.log(1 / p[k], 2)
    hs = hs + e
hs = round(hs,3)
# Efficiency
eff =  hs / L
eff = round(eff,3)
# Redundancy 
red =  round(1 - eff,3) 
# Variance
var = 0
for k in range(n):
    var1 = p[k] * (lk[k]-L)**2
    var = var + var1
var = round(var,3)
print(f"Average Codeword Length is : {L}")
print(f"Entropy is : {hs}")
print(f"Efficiency is : {eff}")
print(f"Redudancy is : {red}")
print(f"Variance is : {var}")

```

## OUTPUT:
![image](https://github.com/user-attachments/assets/b365733b-e380-4646-89ac-4f2c675f3c15)


 
## RESULT:
Simulation of Huffman and Shannon–Fano Code was verified successfully. The computed values of entropy, average codeword length, efficiency, redundancy, and variance confirmed the correctness of the coding techniques.
