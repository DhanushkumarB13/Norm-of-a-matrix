# Norm of a matrix
## Aim
To write a program to find the 1-norm, 2-norm and infinity norm of the matrix and display the result in two decimal places.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
	1. Get the input matrix using np.array()   
    2. Find the 2-norm of the matrix using np.linalg.norm()
	3. Print the norm of the matrix in two decimal places.
## Program:
```Python


A = eval(input())

norm = max(sum(abs(A[i][j]) for i in range(len(A)))
           for j in range(len(A[0])))

print(f"{norm:.2f}")


# 2-Norm of a Matrix
import math

A = eval(input())

m = len(A)
n = len(A[0])

B = [[sum(A[k][i] * A[k][j] for k in range(m))
      for j in range(n)] for i in range(n)]

for _ in range(1000):
    p, q = 0, 0
    maximum = 0

    for i in range(n):
        for j in range(i + 1, n):
            if abs(B[i][j]) > maximum:
                maximum = abs(B[i][j])
                p, q = i, j

    if maximum < 1e-12:
        break

    theta = 0.5 * math.atan2(2 * B[p][q], B[q][q] - B[p][p])
    c = math.cos(theta)
    s = math.sin(theta)

    app = B[p][p]
    aqq = B[q][q]
    apq = B[p][q]

    B[p][p] = c*c*app - 2*s*c*apq + s*s*aqq
    B[q][q] = s*s*app + 2*s*c*apq + c*c*aqq
    B[p][q] = B[q][p] = 0.0

    for k in range(n):
        if k != p and k != q:
            x = B[k][p]
            y = B[k][q]
            B[k][p] = B[p][k] = c*x - s*y
            B[k][q] = B[q][k] = s*x + c*y

norm = math.sqrt(max(0, max(B[i][i] for i in range(n))))

print(f"{norm:.2f}")

# Infinity Norm of a Matrix

A = eval(input())

norm = max(sum(abs(x) for x in row) for row in A)

print(f"{norm:.2f}")



```
## Output:
### 1-Norm of a Matrix
<img width="1188" height="190" alt="image" src="https://github.com/user-attachments/assets/d92beae2-301e-4289-a8e9-26e5e4594a1f" />


### 2-Norm of a Matrix
<img width="1202" height="255" alt="image" src="https://github.com/user-attachments/assets/bfbf474a-232a-4cb9-aafc-d3290f6b06f9" />

### Infinity Norm of a Matrix
<img width="1187" height="202" alt="image" src="https://github.com/user-attachments/assets/50b2124d-45b5-46b6-a319-2c9af217a808" />


## Result
Thus the program for 1-norm, 2-norm and Infinity norm of a matrix are written and verified.
