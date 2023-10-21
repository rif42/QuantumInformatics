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

$ = \dfrac{9}{100}\ket{10} + \dfrac{27}{100}\ket{11}$

$ = \dfrac{9}{25}$  

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





