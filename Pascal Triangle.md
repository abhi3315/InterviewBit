# [Pascal Triangle](https://www.interviewbit.com/problems/pascal-triangle/)

## Approach 1

> TC - O(n*n)
> SC - O(n*n)

```text
[
    [1],
   [1,1],
  [1,2,1],
 [1,3,3,1],
[1,4,6,4,1]
]

For Row i, Row[i][0] = Row[i][i] = 1. And Row[i][j] = Row[i-1][j] + Row[i-1][j-1], when j belongs to [1, i)
```

```c++
vector < vector < int > > Solution::solve(int A) {
  vector < vector < int >> res;

  for (int i = 0; i < A; i++) {
    vector < int > row;
    row.resize(i + 1, 1);
    for (int j = 0; j < i - 1; j++) {
      row[j + 1] = res[i - 1][j] + res[i - 1][j + 1];
    }

    res.push_back(row);
  }

  return res;
}
```
