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
```
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: V G SAIRAIMA
RegisterNumber: 212225040359
'''
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
def QR_Decomposition(a):
    m,n=np.shape(a)
    q=np.empty((m,n))
    u=np.empty((m,n))
    r=np.zeros((m,n))
    u[:,0]=a[:,0]
    q[:,0]=a[:,0]/np.linalg.norm(u[:,0])
    for i in range(1,m):
        u[:,i]=a[:,i]
        for j in range(i):
            u[:,i]-=(a[:,i]@q[:,j])*q[:,j]
        q[:,i]=u[:,i]/np.linalg.norm(u[:,i])
    print("The Q Matrix is")
    print(f" {q}")
    for i in range(n):
        for j in range(i,n):
            r[i,j]=a[:,j]@q[:,i]
    print(f"The R Matrix is")
    print(f" {r}")
a = np.array(eval(input()))
QR_Decomposition(a)
```

## Output
![alt text](<Screenshot 2026-03-22 172630.png>)

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.