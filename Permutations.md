Permutations

- bad
- n^n, n\*n!

```jsx
let permutations;
function getPermutations(arr) {
  permutations = [];

  for (const n of arr) {
    permutate(arr, [n]);
  }

  return permutations;
}

function permutate(arr, currArr = []) {
  if (arr.length === currArr.length) {
    permutations.push(currArr);
    return;
  }

  for (const n of arr) {
    if (currArr.includes(n)) continue;
    permutate(arr, [...currArr, n]);
  }

  return;
}

// Do not edit the line below.
exports.getPermutations = getPermutations;
```

- 2nd try
- space: n! x n^2, n! for each step, there is n steps, inside n steps iterate n
- space: n x n!, there are n! cases, each case is n

```jsx
let permutations;
function getPermutations(arr) {
  permutations = [];
  permutate(arr);
  return permutations;
}

function permutate(arr, current = []) {
  if (arr.length === 0 && current.length !== 0) {
    permutations.push(current);
    return;
  }

  for (let i = 0; i < arr.length; i++) {
    const newArr = arr.slice(0, i).concat(arr.slice(i + 1));
    const newCurrent = current.concat(arr[i]);
    permutate(newArr, newCurrent);
  }

  return;
}

// Do not edit the line below.
exports.getPermutations = getPermutations;
```

- 3rd try
- n! x n, n x n!

```jsx
let permutations;
function getPermutations(arr) {
  permutations = [];
  permutate(arr);
  return permutations;
}

function permutate(arr, idx = 0) {
  if (idx === arr.length - 1) {
    permutations.push(arr.slice(0));
    return;
  }

  // j start from idx => we want to keep the base =>
  // e.g.,
  // [1, 2, 3] after each 0, 1, 2 swap itself
  for (let j = idx; j < arr.length; j++) {
    swap(arr, idx, j);
    permutate(arr, idx + 1);
    swap(arr, j, idx);
  }

  return;
}

function swap(arr, a, b) {
  [arr[b], arr[a]] = [arr[a], arr[b]];
  return arr;
}

// Do not edit the line below.
exports.getPermutations = getPermutations;
```
