# [Spiral Order Matrix II](https://www.interviewbit.com/problems/spiral-order-matrix-ii/)

## Approach 1

> TC - O(m*n)
> SC - O(m*n)

- Considered that both rows and cols are different.

```c++
vector < vector < int > > Solution::generateMatrix(int A) {

  vector < vector < int >> ans(A, vector < int > (A));
  int ele = 1;
  int rot = 0;
  int top = 0, bottom = A - 1, left = 0, right = A - 1;

  while (top <= bottom && left <= right) {
    switch (rot) {
    case 0:
      for (int i = left; i <= right; i++) ans[top][i] = ele++;
      top++;
      break;

    case 1:
      for (int i = top; i <= bottom; i++) ans[i][right] = ele++;
      right--;
      break;

    case 2:
      for (int i = right; i >= left; i--) ans[bottom][i] = ele++;
      bottom--;
      break;

    case 3:
      for (int i = bottom; i >= top; i--) ans[i][left] = ele++;
      left++;
      break;
    }

    rot = (rot + 1) % 4;
  }

  return ans;
}
```

## Approach 2

> TC - O(m*m)
> SC - O(m*m)

- Considered both rows and cols are equal.

```c++
vector < vector < int > > Solution::generateMatrix(int A) {
  vector < vector < int > > arr(A, vector < int > (A, 0));
  int start, end, i;
  long long int x;
  x = 1;
  for (start = 0, end = A - 1; start <= end; start++, end--) {
    for (i = start; i <= end; i++) arr[start][i] = x++;
    for (i = start + 1; i <= end; i++) arr[i][end] = x++;
    for (i = end - 1; i >= start; i--) arr[end][i] = x++;
    for (i = end - 1; i >= start + 1; i--) arr[i][start] = x++;
  }
  return arr;
}
```
