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

### LC33. Finding the index of smallest element in the rotated list

<img src="LC33.png" width="500" />

```cpp
// Time complexity: O(log n)
// Space complexity: O(1)
int search(vector<int> &nums, int target)
{
    int n = nums.size();
    int left_ptr = 0;
    int right_ptr = n - 1;

    // 1단계: 가장 작은 값의 인덱스 찾기
    while (left_ptr < right_ptr)
    {
        int middle_ptr = (left_ptr + right_ptr) / 2;
        if (nums[middle_ptr] < nums[n - 1])
        {
            right_ptr = middle_ptr;
        }
        else if (nums[middle_ptr] > nums[n - 1])
        {
            left_ptr = middle_ptr + 1;
        }
    }

    int index_of_smallest = right_ptr;

    // 2단계: target이 위치한 범위 찾기
    int L, R;
    if (target > nums[index_of_smallest] and target > nums[n - 1])
    {
        L = 0;
        R = index_of_smallest - 1;
    }
    else
    {
        L = index_of_smallest;
        R = n - 1;
    }

    // 3단계: 2단계에서 찾은 범위내에서 일반적인 binary search
    while (L <= R)
    {
        int m = (L + R) / 2;
        if (nums[m] < target)
        {
            L = m + 1;
        }
        else if (nums[m] > target)
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
