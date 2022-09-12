# [Set Matrix Zeros](https://www.interviewbit.com/problems/set-matrix-zeros/)

## Approach 1

> TC - O(m*n)
> SC - O(m+n)

- Traverse through the matrix.
- Store the row and col of the elements which are zero.
- Mark all the elements to zero of the stored rows.
- Mark all the elements to zero of the stored cols.

```c++
void Solution::setZeroes(vector < vector < int > > & A) {
  int rows = A.size();
  int cols = A[0].size();

  set < int > markedRows;
  set < int > markedCols;
  for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
      if (A[i][j] == 0) {
        markedRows.insert(i);
        markedCols.insert(j);
      }
    }
  }

  for (auto itr = markedRows.begin(); itr != markedRows.end(); itr++) {
    for (int i = 0; i < cols; i++) {
      A[ * itr][i] = 0;
    }
  }

  for (auto itr = markedCols.begin(); itr != markedCols.end(); itr++) {
    for (int i = 0; i < rows; i++) {
      A[i][ * itr] = 0;
    }
  }
}
```

## Approach 2

> TC - O(m*n)
> SC - O(1)

- Find if the first row and cols contains any zero or not.
- Now traverse from 2nd row and 2nd col.
- If an element is zero then mark the elements of first row and first col to zero.
- Now traverse again from 2nd row and 2nd col.
- If the element in first row or first col is zero then mark current element zero.
- If first row/col had any zero initially then mark the whole first row/col to zero.

```c++
void Solution::setZeroes(vector < vector < int > > & A) {
  int rows = A.size();
  int cols = A[0].size();
  bool hasZeroFirstRow = false;
  bool hasZeroFirstCol = false;

  for (int i = 0; i < cols; i++) {
    if (A[0][i] == 0) {
      hasZeroFirstRow = true;
      break;
    }
  }

  for (int i = 0; i < rows; i++) {
    if (A[i][0] == 0) {
      hasZeroFirstCol = true;
      break;
    }
  }

  for (int i = 1; i < rows; i++) {
    for (int j = 1; j < cols; j++) {
      if (A[i][j] == 0) {
        A[0][j] = 0;
        A[i][0] = 0;
      }
    }
  }

  for (int i = 1; i < rows; i++) {
    for (int j = 1; j < cols; j++) {
      if (A[i][0] == 0 || A[0][j] == 0) {
        A[i][j] = 0;
      }
    }
  }

  if (hasZeroFirstRow) {
    for (int i = 0; i < cols; i++) {
      A[0][i] = 0;
    }
  }

  if (hasZeroFirstCol) {
    for (int i = 0; i < rows; i++) {
      A[i][0] = 0;
    }
  }
}
```
