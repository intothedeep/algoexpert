Validate Bst

- Validate Bst
  ![Screenshot 2023-01-21 at 22.46.50.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6ec565fe-f82c-4e6f-8b8c-6656c00d92fd/Screenshot_2023-01-21_at_22.46.50.png)
  -
  ```jsx
  // This is an input class. Do not edit.
  class BST {
    constructor(value) {
      this.value = value;
      this.left = null;
      this.right = null;
    }
  }

  function validateBst(tree) {
    return validateHelper(tree, -Infinity, Infinity);
  }

  function validateHelper(node, min, max) {
    if (node === null) {
      return true;
    }

    if (node.value < min || node.value >= max) {
      return false;
    }

    const left = validateHelper(node.left, min, node.value);
    const right = validateHelper(node.right, node.value, max);

    return left && right;
  }

  // Do not edit the line below.
  exports.BST = BST;
  exports.validateBst = validateBst;
  ```
