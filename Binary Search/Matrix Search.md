# [Matrix Search](https://www.interviewbit.com/problems/matrix-search/)

## Approach 1

> TC - O(log(m+n))

> SC - O(1)

- Treat the matrix a single sorted Array.
- Where `low = 0`, `high = m * n - 1`
- Now we split mid into to 2 indices.
- `i = mid/n` and `j = mid%n`

```c++
int Solution::searchMatrix(vector < vector < int > > & A, int B) {
  int m = A.size(), n = A[0].size();
  int low = 0, high = m * n - 1, mid;

  while (low <= high) {
    mid = low + (high - low) / 2;

    int i = mid / n;
    int j = mid % n;

    if (A[i][j] == B) return 1;
    else if (A[i][j] < B) low = mid + 1;
    else high = mid - 1;

  }

  return 0;
}
```
