---
jupyter:
  jupytext:
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.15.2
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Quantum Informatics
## Basics of Quantum Theory (meeting 1-3)  

Quantum theory, just like the name, is a theory about the behaviors and properties of sub-atomic particles. In this material, we're talking about electrons. 
There are a few fundamental properties of quantum particles that we need to understand:  

### Spin  
If we heat water, the hydrogen and oxygen atoms shake in place, getting excited. As a result, they expand to occupy more space. If the heat continues, eventually the atoms will shake so much, it frees itself from the others, entering a gaseous state. This example describes that the behavior of the atoms directly affects the behavior of the matter as a whole.  

Just like the earth orbiting the sun while spinning in place, electrons also spin in place while orbiting the nucleus. They all spin in only one way, but has an infinite amount of possible angles or rotations.  

![electron spins](assets/spin.gif)  

Why electron spins? and does it spin at a different rate? we'll leave that to the Physicists. We're programmers, we just need to know the basics, then take advantage of its properties to perform work.  

### Entanglement

Electron is a subatomic particles that orbits the nucleus in multiple levels or shells. Each shell has a maximum number of electron. The number of maximum electron in the inner-most shell is always two, and they will always be entangled. 

![electron orbits](assets/electronshell.png)  

Entangled or paired electron always have opposite spins. if electron a and b are entangled, and electron a has 45deg spin (3 o-clock), then electron b will always has 315deg spin (9 o-clock) no matter what.  

Logically, since the possibilities of spin variation is infinite, we would assume that electrons has a random spin directions such as 20deg, 92deg, 145deg and so on. However, [Stern-Gerlach experiment](assets/https://en.wikipedia.org/wiki/Stern%E2%80%93Gerlach_experiment) proved otherwise. 

![electron orbits](assets/Stern-Gerlach_experiment.png)  

The experiment shows that **measured** electrons only appears in two states instead of randomly infinite states as suggested earlier.  
The explanation is that upon measuring the electron, the spin direction is **quantized**, meaning all infinitely possible spin directions fall into two states: north and south or 1 and 0.  
This checks out with the famous Schrodinger's Cat thought experiment.  

### Qubits  
Using these two unique properties of quantum particles, we can create a whole new circuitry out of qubits to program something.  
Normal or classical bits has 2 states, 1 and 0. but qubits can have as many as it wants, because qubits follows the spin property, which has infinite amount of possible angles or rotations.  
However, all quantum particles (therefore qubits) will be [quantized](assets/https://en.wikipedia.org/wiki/Quantization_(physics)) when measured, so they become classical bits with 1 and 0.  

## Meeting 4 (part 1) - Measuring Rotated Qubit
![lecture1](assets/1.jpg)  

This image shows the calculation of rotating a qubit spin and measuring its probability output.  
lets say we have a pair of qubits with two basis which we want to transform into another basis:  

$$
\begin{bmatrix}  
1 \\  
0 \\  
\end{bmatrix}  
\begin{bmatrix}  
0 \\  
1 \\   
\end{bmatrix} 
\rightarrow
\begin{bmatrix}
\dfrac{1}{\sqrt{2}} \\
-\dfrac{1}{\sqrt{2}} \\
\end{bmatrix}
\begin{bmatrix}
\dfrac{1}{\sqrt{2}} \\
-\dfrac{1}{\sqrt{2}} \\
\end{bmatrix}
$$

which is equivalent to (in ket notation):  

$$
\begin{bmatrix}
\ket{\uparrow} 
\end{bmatrix}
\begin{bmatrix}
\ket{\downarrow}
\end{bmatrix}
\rightarrow
\begin{bmatrix}
\ket{\rightarrow}
\end{bmatrix}
\begin{bmatrix}
\ket{\leftarrow}
\end{bmatrix}
$$

assuming the spin direction is 90deg, and we want to rotate it 30deg, that means the alpha is 30  
$$\alpha = 30\degree$$  

Therefore we have to calculate the matrix operator by substituting the alpha into following matrix:    

$$  
\begin{bmatrix}
cos\alpha & sin\alpha  \\
-sin\alpha & cos\alpha \\ 
\end{bmatrix}=
\begin{bmatrix}
cos30 & sin30  \\
-sin30 & cos30  \\ 
\end{bmatrix}=
\begin{bmatrix}
\dfrac{1}{2}\sqrt{3} & \dfrac{1}{2}  \\
-\dfrac{1}{2} & \dfrac{1}{2}\sqrt{3}  \\
\end{bmatrix}
$$

then we use the matrix operator on each basis to calculate the new basis.  
for the $\ket{\uparrow}$ basis: 

$$
\begin{bmatrix}
\dfrac{1}{2}\sqrt{3} & \dfrac{1}{2}  \\
-\dfrac{1}{2} & \dfrac{1}{2}\sqrt{3}  \\
\end{bmatrix}
\begin{bmatrix}
1 \\
0 \\ 
\end{bmatrix}=
\begin{bmatrix}
\dfrac{\sqrt{3}}{2}\\
-\dfrac{1}{2} \\
\end{bmatrix}
$$

for the $\ket{\downarrow}$ basis:  

$$
\begin{bmatrix}
\dfrac{1}{2}\sqrt{3} & \dfrac{1}{2}  \\
-\dfrac{1}{2} & \dfrac{1}{2}\sqrt{3}  \\
\end{bmatrix}
\begin{bmatrix}
0 \\
1 \\ 
\end{bmatrix}=
\begin{bmatrix}
\dfrac{1}{2} \\ 
\dfrac{\sqrt{3}}{2}\\
\end{bmatrix}
$$

therefore we can construct the new basis using ket notation :  
$\ket{\uparrow} = \dfrac{\sqrt{3}}{2} \ket{\rightarrow} - \dfrac{1}{2}\ket{\leftarrow}$  

$\ket{\downarrow} = \dfrac{1}{2} \ket{\rightarrow} + \dfrac{\sqrt{3}}{2}\ket{\leftarrow}$  


we can prove this equation by substituting all the ket notation to its original matrix values :  
$\ket{\uparrow} = \dfrac{\sqrt{3}}{2} \ket{\rightarrow} - \dfrac{1}{2}\ket{\leftarrow}$  

$$
\begin{bmatrix}
1 \\
0 \\ 
\end{bmatrix}=
\dfrac{1}{\sqrt{2}}
\begin{bmatrix}
\dfrac{1}{\sqrt{2}} \\
-\dfrac{1}{\sqrt{2}} \\
\end{bmatrix}+
\dfrac{1}{\sqrt{2}}
\begin{bmatrix}
\dfrac{1}{\sqrt{2}} \\
\dfrac{1}{\sqrt{2}} \\
\end{bmatrix}
$$

$$
\begin{bmatrix}
1 \\
0 \\ 
\end{bmatrix}=
\begin{bmatrix}
\dfrac{1}{{2}} \\
-\dfrac{1}{{2}} \\
\end{bmatrix}+
\begin{bmatrix}
\dfrac{1}{{2}} \\
\dfrac{1}{{2}} \\
\end{bmatrix}
$$

$$
\begin{bmatrix}
1 \\
0 \\ 
\end{bmatrix}=
\begin{bmatrix}
1 \\
0 \\ 
\end{bmatrix}
$$

So now the equation is proven correct  
We can also calculate the probability of each basis when its measured for real by simply increasing its power.  

for the $\ket{\uparrow}$ basis:  
$\ket{\uparrow} = \dfrac{\sqrt{3}}{2} \ket{\rightarrow} - \dfrac{1}{2}\ket{\leftarrow}$  

$\ket{\uparrow} = (\dfrac{\sqrt{3}}{2})^2 \ket{\rightarrow} + (-\dfrac{1}{2})^2\ket{\leftarrow}$  

$\ket{\uparrow} = \dfrac{3}{4}\ket{\rightarrow} + \dfrac{1}{4}\ket{\leftarrow}$  

$\ket{\uparrow} = 75\%\ket{\rightarrow} + 25\%\ket{\leftarrow}$  

That means for every 100 electrons measured this way, 75 electrons will have $\ket{\rightarrow}$ spin, while 25 electrons will have $\ket{\leftarrow}$ spin

for the $\ket{\downarrow}$ basis:   
$\ket{\downarrow} = \dfrac{1}{2} \ket{\rightarrow} + \dfrac{\sqrt{3}}{2} \ket{\leftarrow}$  

$\ket{\downarrow} = (\dfrac{1}{2})^2 \ket{\rightarrow} + (\dfrac{\sqrt{3}}{2})^2\ket{\leftarrow}$  

$\ket{\downarrow} = \dfrac{1}{4}\ket{\rightarrow} + \dfrac{3}{4}\ket{\leftarrow}$  

$\ket{\downarrow} = 25\%\ket{\rightarrow} + 75\%\ket{\leftarrow}$  

That means for every 100 electrons measured this way, 75 electrons will have $\ket{\rightarrow}$ spin, while 5 electrons will have $\ket{\leftarrow}$ spin

## Meeting 4 (part 2) - Entanglement of Two Qubits
![lecture1-part2](assets/2.jpg)  

When when we measure one qubit from a pair of qubits, and we get its spin, and the second (paired) qubit shows the opposite of the first qubit's spin, we call the pair of qubits **entangled**  

Quantum entanglement plays an extremely important role in cybersecurity due to its instantenous information transfer and privacy through infinite states of a qubit. See [this video](https://www.youtube.com/watch?v=-UrdExQW0cs) for further explanation. 

Let's say we have two person; Alice and Bob. They want to exchange messages through qubits.  
Alice has one qubit and two basis,  $\ket{v} = \ket{A_0}, \ket{A_1}$  
Bob also has one qubit and two basis, $\ket{w} =\ket{B_0}, \ket{B_1}$  

First we perform a tensor (or outer product) operation on qubit $\ket{v}$ and $\ket{w}$  

$\ket{v} \otimes \ket{w} = \ket{A_0}\ket{B_0} + \ket{A_0}\ket{B_1} + \ket{A_1}\ket{B_0} + \ket{A_1}\ket{B_1}$  

We substitute them with r s t u for clarity:  

$r = \ket{A_0}\ket{B_0}$  

$s = \ket{A_0}\ket{B_1}$  

$t = \ket{A_1}\ket{B_0}$  

$u = \ket{A_1}\ket{B_1}$  

When rstu is exponentiated, it must be equal to 1, otherwise the calculation is invalid  

$r^2 + s^2 + t^2 + u^2 = 1$  

if $ru = st$, then two qubits are not entangled.  
if $ru \neq st$, then two qubits are entangled.  


### Example
Lets say Alice and Bob's qubits are as follows :  

$\dfrac{1}{2}\ket{A_0}\ket{B_0} + \dfrac{1}{2}\ket{A_0}\ket{B_1} + \dfrac{1}{\sqrt{2}}\ket{A_1}\ket{B_0} + 0\ket{A_1}\ket{B_1}$  

First we determine whether the qubits are entangled or not :  

$ru \neq st$  

$\dfrac{1}{2}\ket{A_0}\ket{B_0} * 0\ket{A_1}\ket{B_1} \neq \dfrac{1}{2}\ket{A_0}\ket{B_1} * \dfrac{1}{\sqrt{2}}\ket{A_1}\ket{B_0}$

$0 \neq \dfrac{\sqrt{2}}{4}$

Its proven that the qubits are **entangled**  

Then we calculate the final probability :  

$r^2 + s^2 + t^2 + u^2 = 1$  

$r = \dfrac{1}{2}\ket{A_0}\ket{B_0}$  

$s = \dfrac{1}{2}\ket{A_0}\ket{B_1}$

$t = \dfrac{1}{\sqrt{2}}\ket{A_1}\ket{B_0}$  

$u = 0\ket{A_1}\ket{B_1}$

$= (\dfrac{1}{2})^2 + (\dfrac{1}{2})^2 + (\dfrac{1}{\sqrt{2}})^2 + 0^2$  

$= \dfrac{1}{4} + \dfrac{1}{4} + \dfrac{1}{2} + 0$  

$=  1$ 
 
Okay, our equation is valid because it equals to 1.  
This equation also shows the final probability of each basis, which is :  

$25\ket{A_0}\ket{B_0} + 25\ket{A_0}\ket{B_1} + 50\ket{A_1}\ket{B_0} + 0\\ket{A_1}\ket{B_1}$  

That means, the probability of qubit A and qubit B showing 0 is 25%

But what if we want to check the relationship between two qubits, we must measure only one qubit, then the other.

## Practice 

---
jupyter:
  jupytext:
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.15.2
---

```python
import numpy as np
import math
from math import sqrt
from qiskit import ClassicalRegister, QuantumRegister, QuantumCircuit
from qiskit import execute
from qiskit import Aer
from qiskit import BasicAer
from qiskit.tools.visualization import circuit_drawer
from qiskit.tools.visualization import plot_histogram
from qiskit.tools.visualization import plot_bloch_multivector
from qiskit.quantum_info import Statevector
from qiskit import transpile
```

**1. Calculate the probability of this quantum state equation:**  
$\ket{\psi} = \dfrac{\sqrt{3}}{2\sqrt{2}}\ket{0} + \dfrac{\sqrt{5}}{2\sqrt{2}}\ket{1}$

To find the probability we simply exponent each kets  

$\ket{\psi} = (\dfrac{\sqrt{3}}{2\sqrt{2}})^2\ket{0} +  (\dfrac{\sqrt{5}}{2\sqrt{2}})^2\ket{1}$ 

$\ket{\psi} = \dfrac{3}{8}\ket{0} +  \dfrac{5}{8}\ket{1}$  

Probability of ket $\ket{0}$ is 3/8, while the probability of ket $\ket{1}$ is 5/8



**2. Calculate the probability of this quantum state equation:**  

$\ket{\psi} = -\dfrac{4}{10}\ket{00} -\dfrac{4\sqrt{3}}{10}\ket{01} + \dfrac{3}{10}\ket{10} + \dfrac{3\sqrt{3}}{10}\ket{11}$

a. what is the probability of psi? 

$\ket{\psi} = (-\dfrac{4}{10})^2\ket{00} (-\dfrac{4\sqrt{3}}{10})^2\ket{01} + (\dfrac{3}{10})^2\ket{10} + (\dfrac{3\sqrt{3}}{10})^2\ket{11}$  

$\ket{\psi} = \dfrac{4}{25}\ket{00} \dfrac{12}{25}\ket{01} + \dfrac{9}{100}\ket{10} + \dfrac{27}{100}\ket{11}$  

b. what is the probability of the first qubit to be 1 ?  

we simply need to add the probability of ket $\ket{10}$ and ket 
$\ket{11}$

$= \dfrac{9}{100}\ket{10} + \dfrac{27}{100}\ket{11}$

$= \dfrac{9}{25}$  

the probability of the first qubit to be 1 is 9/25  



3. Prove below matrix equation :  
$CX \ket{10} = \ket{11}$  
$CX \ket{11} = \ket{10}$   
$CZ \ket{10} = \ket{10}$  
$CZ \ket{11} = -\ket{11}$   
$SWAP \ket{01} = \ket{10}$  
$SWAP \ket{10} = \ket{01}$  
$CCX \ket{110} = \ket{111}$  
$CCX \ket{111} = \ket{110}$  

First, we need to define all the basis used in these equation using matrix, starting from the very basic 1 and 0:  

$$\ket{1}=
\begin{bmatrix}
0 \\
1 \\
\end{bmatrix}
$$

$$\ket{0}=
\begin{bmatrix}
1 \\
0 \\
\end{bmatrix}
$$

Then if we want to construct other basis using 1 and 0, we perform a tensor operation on them :  

$\ket{10} = \ket{1} \otimes \ket{0}$  

$$\ket{10}=
\begin{bmatrix}
0 \\
1 \\
\end{bmatrix}
\otimes
\begin{bmatrix}
1 \\
0 \\
\end{bmatrix}$$  

$$\ket{10}=
\begin{bmatrix}
0\begin{pmatrix}
1 \\
0
\end{pmatrix} \\
1\begin{pmatrix}
1 \\
0
\end{pmatrix}
\end{bmatrix}=
\begin{bmatrix}
0 \\
0 \\
0 \\
1 \\
\end{bmatrix}
$$
