- Max Subset Sum No Adjacent
  ![Screenshot 2023-01-22 at 22.21.14.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f08dd54a-1c66-4273-8536-f46d6f2b5bb3/Screenshot_2023-01-22_at_22.21.14.png)
  - n, 1
  ```jsx
  function maxSubsetSumNoAdjacent(arr) {
    if (arr.length === 0) return 0;
    if (arr.length === 1) return arr[0];

    let first = arr[0];
    let second = Math.max(arr[1], arr[0]);

    for (let i = 2; i < arr.length; i++) {
      const curr = Math.max(second, first + arr[i]);
      first = second;
      second = curr;
    }

    return second;
  }

  // Do not edit the line below.
  exports.maxSubsetSumNoAdjacent = maxSubsetSumNoAdjacent;
  ```
