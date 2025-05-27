# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm

1. **Input** the size $n$ of the system and initialize augmented matrix $a$ and solution vector $x$.
2. **Read** the augmented matrix $a$ of size $n \times (n+1)$ from user input.
3. **Forward Elimination**: For each row $i$, eliminate the variables below the pivot element $a[i][i]$.
4. **Check** for division by zero (i.e., if pivot element is 0), and exit with an error if found.
5. **Compute** the ratio of the current row and pivot row to eliminate variables.
6. **Update** the rows below the pivot by subtracting the appropriate multiple of the pivot row.
7. **Start Back Substitution**: Set the last variable $x[n-1]$ using the last row.
8. **Back-substitute**: For each row from $n-2$ to 0, compute $x[i]$ by substituting known values.
9. **Divide** each $x[i]$ by its corresponding diagonal element to isolate the variable.
10. **Display** the solution vector $x$, formatted to two decimal places.


## Program:
```
/*
Program to find the solution of a matrix using Gaussian Elimination.
Developed by: Sanjeev A
RegisterNumber: 212224230246
*/

import numpy as np
import sys

n=int(input())

a=np.zeros((n,n+1))
x=np.zeros(n)

for i in range(n):
    for j in range(n+1):
        a[i][j]=float(input())
        
for i in range(n):
    if a[i][i]==0.0:
        sys.exit('Divide by zero detected!')
        
    for j in range(i+1,n):
        ratio=a[j][i] / a[i][i]
        
        for k in range(n+1):
            a[j][k] = a[j][k] - ratio*a[i][k]
            
x[n-1]=a[n-1][n]/a[n-1][n-1]

for i in range(n-2,-1,-1):
    x[i]=a[i][n]
    
    for j in range(i+1,n):
        x[i]=x[i]-a[i][j]*x[j]
    x[i]=x[i]/a[i][i]
    
for i in range(n):
    print('X%d = %0.2f' %(i,x[i]), end=' ')
```

## Output:
![image](https://github.com/user-attachments/assets/db9de84f-4240-4bf0-a75d-918f70057ae7)


## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

