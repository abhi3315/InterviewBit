# [Find Missing Integer](https://www.interviewbit.com/problems/first-missing-integer/)

## Approach 1

> TC - O(n*log(n))

> SC - O(1)

- Sort the Array.
- Initialize a variable `n` to 1;
- Traverse the sorted array.
- If element is less than or equal to zero then continue
- If current element is not equal to `n` then return `n`
- Else increment `n`
- After traversal `n` is the ans.

```c++
int Solution::firstMissingPositive(vector < int > & A) {
  sort(A.begin(), A.end());

  int n = 1;
  for (int i = 0; i < A.size(); i++) {
    if (A[i] <= 0) {
      continue;
    }

    if (A[i] != n) {
      return n;
    }
    n++;
  }

  return n;
}
```

## Approach 2

> TC - O(n)

> SC - O(n)

- We know the ans will lie in between 1 to N+1.
- So we can create a bucket of size of given array.
- Traverse the given array.
- If current element is smaller than or equal to zero then continue;
- If the current element is greater than the size of given array then continue;
- Add element to the bucket `bucket[x - 1] = x`.
- Traverse the bucket array if `bucket[i] != i + 1` then `i + 1`
- If all the elements are present in bucket then return `N + 1`

```c++
int Solution::firstMissingPositive(vector < int > & A) {
  vector < int > bucket(A.size(), 0);

  for (auto x: A) {
    if (x <= 0) continue;
    if (x > A.size()) continue;

    bucket[x - 1] = x;
  }

  for (int i = 0; i < A.size(); i++) {
    if (bucket[i] != i + 1) return i + 1;
  }

  return A.size() + 1;
}
```

## Approach 3

> TC - O(n)

> SC - O(1)

- Instead of using external space use the given array for bucket.

```c++
int Solution::firstMissingPositive(vector < int > & A) {
  for (int i = 0; i < A.size(); i++) {
    if (A[i] <= 0) continue;
    if (A[i] > A.size()) continue;

    int index = A[i] - 1;
    if (A[index] != A[i]) {
      swap(A[index], A[i]);
      i--;
    }
  }

  for (int i = 0; i < A.size(); i++) {
    if (A[i] != i + 1) return i + 1;
  }

  return A.size() + 1;
}
```
