Zero Sum Sub array

- Zero Sum Subarray
  ![Screenshot 2023-01-21 at 21.15.30.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9f8f752-1d1f-4099-8464-8a2fe4d147a0/Screenshot_2023-01-21_at_21.15.30.png)
  - N, N
  ```jsx
  function zeroSumSubarray(nums) {
    let set = new Set([0]);

    let currentSum = 0;
    for (let i = 0; i < nums.length; i++) {
      currentSum += nums[i];
      if (set.has(currentSum)) return true;
      set.add(currentSum);
    }

    return false;
  }

  // Do not edit the line below.
  exports.zeroSumSubarray = zeroSumSubarray;
  ```
  - Can I find index?
  ```jsx
  function zeroSumSubarray(nums) {
    const answer = [];
    let set = new Set([0]);
    let sums = [];

    let idxToStop = -1;
    let currentSum = 0;
    for (let i = 0; i < nums.length; i++) {
      currentSum += nums[i];
      sums[i] = currentSum;
      if (set.has(currentSum)) {
        idxToStop = i;
        answer.push(idxToStop);
        break;
      }
      set.add(currentSum);
    }

    if (idxToStop === -1) return [];

    for (let i = idxToStop - 1; i >= 0; --i) {
      if (sums[i] === currentSum) break;
      answer.push(i);
    }

    return answer;
  }

  // Do not edit the line below.
  exports.zeroSumSubarray = zeroSumSubarray;
  ```
