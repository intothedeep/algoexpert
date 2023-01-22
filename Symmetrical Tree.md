- Symmetrical Tree
  ![Screenshot 2023-01-22 at 22.01.24.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e0301e4b-c578-48f5-a324-01d286cdfb5c/Screenshot_2023-01-22_at_22.01.24.png)
  - n, h
  ```jsx
  // This is an input class. Do not edit.
  class BinaryTree {
    constructor(value) {
      this.value = value;
      this.left = null;
      this.right = null;
    }
  }

  exports.BinaryTree = BinaryTree;

  function symmetricalTree(tree) {
    return validate(tree.left, tree.right);
  }

  function validate(left, right) {
    if (left === null && right === null) {
      return true;
    }

    if (left === null || right === null || left.value !== right.value) {
      return false;
    }

    const outer = validate(left.left, right.right);
    const inner = validate(left.right, right.left);

    return outer && inner;
  }

  // Do not edit the line below.
  exports.symmetricalTree = symmetricalTree;
  ```
  - iteration
  ```jsx
  // This is an input class. Do not edit.
  class BinaryTree {
    constructor(value) {
      this.value = value;
      this.left = null;
      this.right = null;
    }
  }

  exports.BinaryTree = BinaryTree;

  function symmetricalTree(tree) {
    const leftStack = [tree.left];
    const rightStack = [tree.right];

    while (leftStack.length > 0) {
      const left = leftStack.pop();
      const right = rightStack.pop();

      if (left === null && right === null) continue;
      if (left === null || right === null || left.value !== right.value)
        return false;

      leftStack.push(left.left);
      leftStack.push(left.right);
      rightStack.push(right.right);
      rightStack.push(right.left);
    }

    return true;
  }

  // Do not edit the line below.
  exports.symmetricalTree = symmetricalTree;
  ```
