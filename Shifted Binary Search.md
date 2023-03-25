

- logN, 1
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
    } else { // arr not shifted
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
