- Min Number Of Coins For Change
  ![Screenshot 2023-01-22 at 23.21.20.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2090e3ed-bc7a-4201-98c8-71b948bde2d6/Screenshot_2023-01-22_at_23.21.20.png)
  - n, n
  ```jsx
  function minNumberOfCoinsForChange(n, denoms) {
    denoms.sort((a, b) => a - b);
    const coins = new Array(n + 1).fill(Infinity);
    coins[0] = 0;

    for (const denom of denoms) {
      for (let i = 1; i < n + 1; i++) {
        if (denom > i) continue;
        coins[i] = Math.min(coins[i], coins[i - denom] + 1);
      }
    }

    return coins[n] === Infinity ? -1 : coins[n];
  }

  // Do not edit the line below.
  exports.minNumberOfCoinsForChange = minNumberOfCoinsForChange;
  ```
