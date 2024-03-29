# pymatrices
A Python 3.x package to implement Matrices and almost all its Properties.
It is also available on [PyPI](https://pypi.org/project/pymatrices/0.0.1/)

## Installation
***Please Note :- Requires Python Version 3.x***

**If there are 2 or more versions of Python installed in your system (which mostly occurs in UNIX/Linux systems) then please run any one of the commands in the BASH/ZSH Shell \:-**
```bash
$ pip3 install pymatrices
```
```bash
$ python3 -m pip install pymatrices
```

**If there is only Python 3.x installed in your system like in Windows systems then please run any one of commands in the Command Prompt \:-**
```console
> pip install pymatrices
```
```console
> python -m pip install pymatrices
```

## Quick Guide :-
***Please Read Till the End***

**Importing the Package :-**

- Import the module by `import pymatrices as pm`.

**Creating a Matrix and its Methods :-**

- `pm.matrix()` creates a Matrix object.
	- It requires a **2-Dimensional List**.
	- It stores it as a **List**, therefore it is **mutable**. To change the values, use `<matrix object>.matrix[i][j] = value`. ***Please Note that here i, j must be indices that obeys python's rules i.e '0' points to the 1st value***.
- `<matrix object>.matrix` returns the **List** form of the matrix.
- `<matrix object>.order` returns the order of the matrix in a **Tuple** in the format of `(rows, columns)`.
- `<matrix object>.transpose` returns the transpose of the matrix, which is another matrix object.
- All the Arithmetic Operations can be done by using their usual symbols.
	- However, two types of Product can be done :-
		- Scalar Product : `<matrix.object>*(int or float)` returns a Matrix with the `int` multiplied with each element of the matrix.
		- Vector Product : `<matrix object>*<matrix object>` returns a Matrix which is the product of the 2 matrices.
- `<matrix object>.primaryDiagonalValues` returns a List which has the **Primany Diagonal Elements** of the Matrix.
- `<matrix object>.secondaryDiagonalValues` returns a List which has the **Secondary Diagonal Elements** of the Matrix.
- `<matrix object>.valueAt(row, column)` returns the **value** at the given row and column. **Please Note that here the `row` and `column` are _normal_ indices and not _python_ respective indices i.e '1' points to the first element**. _Refer Sample Implementation_
- `<matrix object>.minorOfValueAt(row, column)` returns the matrix, which is the **minor of the value at the given `row` and `column`**.
- `<matrix object>.positionOf(value)` returns a Tuple which are the indices of the given value; If the value is not found, it raises ***ValueError***.


**Uses of Additional Functions available in the Package :-**

- `pm.adjoint(<matrix>)` returns the **Adjoint Matrix (Adjugate Matrix)** which is a matrix object.
- `pm.createByFilling(value, order)` returns a Matrix of given order and filled with the given value.
- `pm.createColumnMatrix(values)` returns a **Column Matrix** with the given values.
- `pm.createRowMatrix(<matrix>)` returns a **Row Matrix** with the given values.
- `pm.determinant(<matrix>)` returns the **Determinant** of the given matrix.
- `pm.eigenvalues(<matrix>)` returns the **Eigenvalues** of the matrix in a Tuple.
- `pm.inverse(<matrix>)` returns the **Inverse** of the matrix, which is another matrix object.
- `pm.I(order)` returns the Identity matrix of the given order.
- `pm.isDiagonal(<matrix>)` returns _True_ if the given matrix is a **Diagonal Matrix** else returns _False_.
- `pm.isScalar(<matrix>)` returns _True_ if the given matrix is a **Scalar Matrix** else returns _False_.
- `pm.isSingular(<matrix>)` returns _True_ if the given matrix is a **Singular Matrix** else returns _False_.
- `pm.isSquare(<matrix>)` returns _True_ if the given matrix is a **Square Matrix** else returns _False_.
- `pm.isSymmetric(<matrix>)` returns _True_ if the given matrix is a **Symmetric Matrix** else returns _False_.
- `pm.isSkewSymmetric(<matrix>)` returns _True_ if the given matrix is a **Skew Symmetric Matrix** else returns _False_.
- `pm.isIdentity(<matrix>)` returns _True_ if the given matrix is an **Identity Matrix** else returns _False_.

## A Sample Implementation :-
_Just Run the Script in your IDE after installing the package_

```python3
import pymatrices as pm

M1 = pm.matrix([[1,-1,3],[4,5,6],[7,8,9]])
M2 = pm.matrix([[1,2],[3,4]])
M3 = pm.I(3)

print("M1 :\n", M1, sep="")
print("M2 :\n", M2, sep="")
print("M3 :\n", M3, sep="")

M1.matrix[0][1] = 2
print("After changing a value of M1 :\n", M1, sep="")

print(f"Matrix in List Form : {M1.matrix}")

print("Transpose of M1 :\n", M1.transpose, sep="")
print("Transpose of M2 :\n", M2.transpose, sep="")
print("Transpose of M3 :\n", M3.transpose, sep="")

print("M1+M3 :\n", M1+M3, sep="")
print("M1-M3 :\n", M1-M3, sep="")

print("M1*M3 :\n", M1*M3, sep="")
print("M1*3 :\n", M3*3, sep="")

print("\nPrimary Diagonal Values of M1 :", M1.primaryDiagonalValues)
print("Primary Diagonal Values of M2 :", M2.primaryDiagonalValues)

print("\nSecondary Diagonal Values of M1 :", M1.secondaryDiagonalValues)
print("Secondary Diagonal Values of M2 :", M2.secondaryDiagonalValues)

print("\nM1[1][1] :", M1.valueAt(1, 1))
print("M1[1][2] :", M1.valueAt(1, 2))

print("\nMinor of 1 in M1:\n", M1.minorOfValueAt(1, 1), sep="")
print("Minor of 2 in M1 :\n", M1.minorOfValueAt(2, 2), sep="")

print("Index of 1 in M1 :", M1.positionOf(1))
print("Index of 8 in M1 :", M1.positionOf(8))

print("\nadj M1 :\n", pm.adjoint(M1), sep="")
print("adj M2 :\n", pm.adjoint(M2), sep="")

print("Matrix created by Filling a particular value :\n", pm.createByFilling(2, (2, 3)), sep="")

print("A Sample Column Matrix :\n", pm.createColumnMatrix([2,3,4,5]), sep="")

print("A Sample Row Matrix :\n", pm.createRowMatrix([2,3,4,5]), sep="")

print("|M1| :", pm.determinant(M1))
print("|M2| :", pm.determinant(M2))

print("\nEigenvalues of M1 :", pm.eigenvalues(M1))
print("Eigenvalues of M2 :", pm.eigenvalues(M2))

print("\nInverse of M1 :\n", pm.inverse(M1), sep="")
print("Inverse of M1 :\n", pm.inverse(M2), sep="")

print("A 3x3 Identity Matrix :\n", pm.I(3), sep="")

print("Is M1 a Diagonal Matrix? ", pm.isDiagonal(M1), sep="")
print("Is M1 a Scalar Matrix? ", pm.isScalar(M1), sep="")
print("Is M1 a Singular Matrix? ", pm.isSingular(M1), sep="")
print("Is M1 a Square Matrix? ", pm.isSquare(M1), sep="")
print("Is M1 a Symmetric Matrix? ", pm.isSymmetric(M1), sep="")
print("Is M1 a Skew Symmetric Matrix? ", pm.isSkewSymmetric(M1), sep="")
print("Is M1 a Identity Matrix? ", pm.isIdentity(M1), sep="")
```
