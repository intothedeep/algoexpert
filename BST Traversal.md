BST Traversal

- BST Traversal
  ![Screenshot 2023-01-21 at 22.47.32.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/71c05d42-95ea-44d2-ae79-0decb293ff64/Screenshot_2023-01-21_at_22.47.32.png)
  -
  ```jsx
  function inOrderTraverse(tree, arr) {
    if (tree === null) {
      return;
    }

    inOrderTraverse(tree.left, arr);
    arr.push(tree.value);
    inOrderTraverse(tree.right, arr);

    return arr;
  }

  function preOrderTraverse(tree, arr) {
    if (tree === null) {
      return;
    }

    arr.push(tree.value);
    preOrderTraverse(tree.left, arr);
    preOrderTraverse(tree.right, arr);

    return arr;
  }

  function postOrderTraverse(tree, arr) {
    if (tree === null) {
      return;
    }

    postOrderTraverse(tree.left, arr);
    postOrderTraverse(tree.right, arr);
    arr.push(tree.value);

    return arr;
  }

  // Do not edit the lines below.
  exports.inOrderTraverse = inOrderTraverse;
  exports.preOrderTraverse = preOrderTraverse;
  exports.postOrderTraverse = postOrderTraverse;
  ```
