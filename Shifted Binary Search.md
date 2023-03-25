-   logN, 1

```js
function shiftedBinarySearch(arr, target) {
    let s = -1;
    let e = arr.length;

    while (s + 1 < e) {
        const m = s + Math.floor((e - s) / 2);
        const left = arr[Math.max(0, s)];
        const mid = arr[m];
        const right = arr[Math.min(arr.length - 1, e)];

        if (right >= mid) {
            e = m;
        } else {
            s = m;
        }
    }

    let pivot = e;
    if (arr[pivot] !== undefined) {
        if (arr[pivot] <= target && target <= arr[arr.length - 1]) {
            e = arr.length;
        } else {
            s = -1;
        }
    } else {
        // arr not shifted
        s = -1;
    }

    while (s + 1 < e) {
        const m = s + Math.floor((e - s) / 2);

        if (arr[m] >= target) {
            e = m;
        } else {
            s = m;
        }
    }

    if (arr[e] !== target) return -1;
    return e;
}
```

```py
def shifted_binary_search(arr, target):
    # Find the pivot element
    left, right = 0, len(arr) - 1
    while left < right:
        mid = (left + right) // 2
        if arr[mid] > arr[right]:
            left = mid + 1
        else:
            right = mid

    # Determine which subarray to search
    pivot = left
    left, right = 0, len(arr) - 1
    if target >= arr[pivot] and target <= arr[right]:
        left = pivot
    else:
        right = pivot - 1

    # Perform a binary search on the subarray
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    # Return -1 if target is not found
    return -1

```
