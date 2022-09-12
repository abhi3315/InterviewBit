# [Wave Array](https://www.interviewbit.com/problems/wave-array/)

## Approach 1

> TC - O(n*log(n))
> SC - O(1)

- Sort the array.
- Swap the adjacent elements of the array.

```c++
vector < int > Solution::wave(vector < int > & A) {
  sort(A.begin(), A.end());
  for (int i = 1; i < A.size(); i++) {
    swap(A[i - 1], A[i]);
    i++;
  }
  return A;
}
```
