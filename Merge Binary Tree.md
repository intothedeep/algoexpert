- Merge Binary Trees
  ![Screenshot 2023-01-22 at 21.47.15.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/74690cad-1a4e-4d9e-b661-bfd29a88eeff/Screenshot_2023-01-22_at_21.47.15.png)
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

  function mergeBinaryTrees(tree1, tree2) {
    return mergeHelper(tree1, tree2);
  }

  function mergeHelper(tree1, tree2) {
    if (tree1 === null && tree2 === null) {
      return null;
    }

    if (tree1 === null) {
      return tree2;
    }

    if (tree2 === null) {
      return tree1;
    }

    tree1.value += tree2.value;
    const left = mergeHelper(tree1.left, tree2.left);
    const right = mergeHelper(tree1.right, tree2.right);

    tree1.left = left;
    tree1.right = right;

    return tree1;
  }

  // Do not edit the line below.
  exports.mergeBinaryTrees = mergeBinaryTrees;
  ```
