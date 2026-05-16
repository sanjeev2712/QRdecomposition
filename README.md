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
#Program to QR decomposition using the Gram-Schmidt method
#Developed by: K.Sanjeev Kumar
#RegisterNumber: 212225230246
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
def QR_Decomposition(A):
    n,m=A.shape
    q=np.empty((n,n))
    u=np.empty((n,n))
    u[:,0]=A[:,0]
    q[:,0]=u[:,0]/np.linalg.norm(u[:,0])
    for i in range(1,n):
        u[:,i]=A[:,i]
        for j in range(i):
            u[:,i]-=(A[:,i]@q[:,j])*q[:,j]
        q[:,i]=u[:,i]/np.linalg.norm(u[:,i])
    r = np.zeros((n,m))
    for i in range(n):
        for j in range(i,m):
            r[i,j]=A[:,j]@q[:,i]
    print("The Q Matrix is \n",q)
    print("The R Matrix is \n",r)
x=eval(input())
a = np.array(x)
QR_Decomposition(a)
```

## Output
<img width="1168" height="395" alt="Screenshot 2026-05-16 132632" src="https://github.com/user-attachments/assets/60640572-547d-4773-9187-1f5ca9fbcc27" />
<img width="1157" height="532" alt="Screenshot 2026-05-16 132652" src="https://github.com/user-attachments/assets/64645f96-bf89-46aa-a1ea-c89eaf30c093" />
<img width="1166" height="596" alt="Screenshot 2026-05-16 132706" src="https://github.com/user-attachments/assets/fe97dd3b-668c-4343-aeff-6b27ea561b8d" />


## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
