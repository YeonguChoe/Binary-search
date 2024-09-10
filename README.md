# Binary Search

## Finding index of a Target
```
// A: original list
// n: elements in A
// T: target
int binary_search(vector<int> A, int n, int T)
{
    int L = 0;
    int R = n - 1;
    while (L <= R)
    {
        int m = floor((L + R) / 2);
        if (A[m] < T)
        {
            L = m + 1;
        }
        else if (A[m] > T)
        {
            R = m - 1;
        }
        else
        {
            return m;
        }
    }
    return -1;
}
```

## (Faster) Finding index of a Target

```cpp
// A: original list
// n: elements in A
// T: target
int binary_search(vector<int> A, int n, int T)
{
    int L = 0;
    int R = n - 1;

    while (L != R)
    {
        int m = ceil((L + R) / 2);
        if (A[m] > T)
        {
            R = m - 1;
        }
        else
        {
            L = m;
        }
    }
    if (A[L] = T)
    {
        return L;
    }
    return -1;
}
```
