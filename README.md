# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by:sameem
RegisterNumber: 212225040242
'''
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
import ast
import sys

def main():
    input_str = sys.stdin.read().strip()
    if not input_str:
        return
    if input_str.startswith('(') and input_str.endswith(')'):
        input_str = input_str[1:-1]
    A = np.array(ast.literal_eval(input_str), dtype=float)
    
    n, m = A.shape
    Q = np.zeros((n, m))
    R = np.zeros((m, m))
    
    for j in range(m):
        v = A[:, j]
        for i in range(j):
            R[i, j] = np.dot(Q[:, i], A[:, j])
            v = v - R[i, j] * Q[:, i]
            
        R[j, j] = np.linalg.norm(v)
        Q[:, j] = v / R[j, j]
        
    print("The Q Matrix is")
    print('',Q)
    print("The R Matrix is")
    print('',R)

if __name__ == '__main__':
    main()
```

## Output
```
<img width="1920" height="911" alt="image" src="https://github.com/user-attachments/assets/88fe2e68-4ae4-4c01-8e11-2d0cbaab659a" />

```

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
