Power Set

![Screenshot 2023-01-24 at 23.18.35.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/36dd2b01-f456-43f9-86af-d4c5ecdfb06b/Screenshot_2023-01-24_at_23.18.35.png)

- n x 2^n, n x 2^n

```jsx
function powerset(arr) {
  let answer = [[]];

  for (const n of arr) {
    const temp = [];
    for (const el of answer) {
      const next = [...el, n];
      temp.push(next);
    }
    answer.push(...temp);
  }

  return answer;
}

// Do not edit the line below.
exports.powerset = powerset;
```

- simpler

```jsx
function powerset(arr) {
  let answer = [[]];

  for (const n of arr) {
    const answerLenBeforeThisIter = answer.length;
    for (let i = 0; i < answerLenBeforeThisIter; i++) {
      answer.push(answer[i].concat(n));
    }
  }

  return answer;
}

// Do not edit the line below.
exports.powerset = powerset;
```
