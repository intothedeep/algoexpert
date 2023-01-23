- Number Of Ways To Make Change
  ![Screenshot 2023-01-22 at 23.07.12.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/56ebbf15-f402-4400-84af-304099957c8d/Screenshot_2023-01-22_at_23.07.12.png)
  - d x n, n
  ```jsx
  function numberOfWaysToMakeChange(n, denoms) {
    const arr = new Array(n + 1).fill(0);
    arr[0] = 1;

    for (const denom of denoms) {
      for (let i = 0; i < n + 1; i++) {
        if (denom > i) continue;
        arr[i] = arr[i] + arr[i - denom];
      }
    }

    return arr[n];
  }

  // Do not edit the line below.
  exports.numberOfWaysToMakeChange = numberOfWaysToMakeChange;
  ```
