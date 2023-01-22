Min Height BST

- Min Height BST
  ![Screenshot 2023-01-21 at 22.16.37.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c5e67d6a-9335-43b3-a223-5b2f3dab0b75/Screenshot_2023-01-21_at_22.16.37.png)
  - N, h
  ```jsx
  function minHeightBst(arr) {
    return buildBst(arr, 0, arr.length - 1);
  }

  function buildBst(arr, s, e) {
    if (s > e) {
      return null;
    }

    const m = s + Math.floor((e - s) / 2);

    const bst = new BST(arr[m]);
    bst.left = buildBst(arr, s, m - 1);
    bst.right = buildBst(arr, m + 1, e);

    return bst;
  }

  class BST {
    constructor(value) {
      this.value = value;
      this.left = null;
      this.right = null;
    }

    insert(value) {
      if (value < this.value) {
        if (this.left === null) {
          this.left = new BST(value);
        } else {
          this.left.insert(value);
        }
      } else {
        if (this.right === null) {
          this.right = new BST(value);
        } else {
          this.right.insert(value);
        }
      }
    }
  }

  // Do not edit the line below.
  exports.minHeightBst = minHeightBst;
  ```
