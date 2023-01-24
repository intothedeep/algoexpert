```js
// Do not edit the class below except for the buildHeap,
// siftDown, siftUp, peek, remove, and insert methods.
// Feel free to add new properties and methods to the class.
class MinHeap {
  constructor(array) {
    this.heap = this.buildHeap(array);
  }

  buildHeap(arr) {
    let startIndex = Math.floor((arr.length - 1 - 1) / 2);
    while (startIndex >= 0) {
      this.siftDown(arr, startIndex, arr.length - 1);
      startIndex -= 1;
      console.log({
        arr,
      });
    }
    return arr;
  }

  siftDown(heap, startIndex, endIndex) {
    let currentIndex = startIndex;
    let left = currentIndex * 2 + 1;
    while (left <= endIndex) {
      let min = left;
      const right = currentIndex * 2 + 2;
      if (heap[right] !== undefined && heap[right] < heap[left]) {
        min = right;
      }

      if (heap[currentIndex] < heap[min]) break;

      this.swap(heap, min, currentIndex);
      currentIndex = min;
      left = currentIndex * 2 + 1;
    }
  }

  siftUp(heap, endIndex) {
    let currenIndex = endIndex;
    let parentIndex = Math.floor((currenIndex - 1) / 2);
    while (parentIndex >= 0) {
      if (heap[parentIndex] <= heap[currenIndex]) break;
      this.swap(heap, parentIndex, currenIndex);
      currenIndex = parentIndex;
      parentIndex = Math.floor((currenIndex - 1) / 2);
    }
  }

  peek() {
    return this.heap[0] ?? null;
  }

  remove() {
    this.swap(this.heap, 0, this.heap.length - 1);
    const min = this.heap.pop();
    this.siftDown(this.heap, 0, this.heap.length - 1);
    return min;
  }

  insert(value) {
    this.heap.push(value);
    const endIndex = this.heap.length - 1;
    this.siftUp(this.heap, endIndex);
  }

  swap(arr, a, b) {
    [arr[b], arr[a]] = [arr[a], arr[b]];
    return arr;
  }
}

// Do not edit the line below.
exports.MinHeap = MinHeap;
```
