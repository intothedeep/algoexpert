-   h, h

```jsx
function maxPathSum(tree) {
    const max = {
        sum: -Infinity,
    };

    findMaxSum(tree, max);
    return max.sum;
}

function findMaxSum(node, max) {
    if (node === null) {
        return 0;
    }

    const left = findMaxSum(node.left, max);
    const right = findMaxSum(node.right, max);

    const currentValue = node.value;
    const pathMax = left + right + node.value;
    max.sum = Math.max(
        max.sum,
        pathMax,
        currentValue,
        left + currentValue,
        right + currentValue
    );

    return Math.max(left, right) + currentValue;
}

exports.maxPathSum = maxPathSum;
```

> sum 기초값 0
> 값이 음수일 수도 있는지 확인
> 어떤 값들이 input으로 주어지는 지 확인
> distinct?
> positive?
> negative?
> just one node?
> 리턴 해야할 값 확인
