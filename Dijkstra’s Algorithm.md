Dijkstra’s Algorithm

-   O((E + V)logV), O(V)

```jsx
// Do not edit the class below except for the buildHeap,
// siftDown, siftUp, peek, remove, and insert methods.
// Feel free to add new properties and methods to the class.
class MinHeap {
    constructor(arr, comparator = (a, b) => (a - b > 0 ? false : true)) {
        this.comparator = comparator;
        // if (this.comparator === undefined) {
        //   this.comparator = function (a, b) {
        //     return a - b > 0 ? false : true;
        //   }
        // }
        this.heap = this.buildHeap(arr);
    }

    buildHeap(arr) {
        let startIdx = Math.floor((arr.length - 1 - 1) / 2);
        while (startIdx >= 0) {
            this.siftDown(arr, startIdx, arr.length - 1);
            startIdx--;
        }
        return arr;
    }

    siftDown(heap, startIdx, endIdx) {
        let currentIndex = startIdx;
        let left = currentIndex * 2 + 1;
        console.log("down:: ", {
            currentIndex,
            left,
            endIdx,
        });
        while (left <= endIdx) {
            let min = left;
            let right = currentIndex * 2 + 2;
            if (
                heap[right] !== undefined &&
                this.comparator(heap[right], heap[left])
            ) {
                min = right;
            }

            console.log("----> ", {
                current: heap[currentIndex],
                left: heap[left],
                right: heap[right],
            });
            if (this.comparator(heap[currentIndex], heap[min])) break;

            this.swap(heap, currentIndex, min);
            currentIndex = min;
            left = currentIndex * 2 + 1;
        }

        console.log({
            heap: this.heap,
        });
    }

    siftUp(heap, currentIndex) {
        let parentIndex = Math.floor((currentIndex - 1) / 2);
        while (parentIndex >= 0) {
            const isAsc = this.comparator(
                this.heap[parentIndex],
                this.heap[currentIndex]
            );
            if (isAsc) break;
            this.swap(heap, parentIndex, currentIndex);
            currentIndex = parentIndex;
            parentIndex = Math.floor((currentIndex - 1) / 2);
        }
    }

    insert(value) {
        this.heap.push(value);
        this.siftUp(this.heap, this.heap.length - 1);
        return;
    }

    remove(value) {
        this.swap(this.heap, 0, this.heap.length - 1);
        const elementToRemove = this.heap.pop();
        this.siftDown(this.heap, 0, this.heap.length - 1);
        return elementToRemove;
    }

    peek() {
        return this.heap[0];
    }

    swap(arr, a, b) {
        [arr[b], arr[a]] = [arr[a], arr[b]];
        return arr;
    }
}

// Do not edit the line below.
exports.MinHeap = MinHeap;

function dijkstrasAlgorithm(start, edges) {
    // create array to store shortest distance from start to i vertex
    const shortest = new Array(edges.length).fill(Infinity);

    // construct min heap to get minimum distance edge
    const instance = new MinHeap([], (a, b) => a[0] - b[0]);
    instance.insert([0, start]);
    shortest[start] = 0;

    const visited = new Set();
    while (instance.heap.length > 0) {
        const [, here] = instance.remove();
        // if (visited.has(here)) continue;

        for (const [there, distance] of edges[here]) {
            const fromHereToThere = distance + shortest[here];
            if (shortest[there] <= fromHereToThere) continue;

            instance.insert([distance, there]);
            shortest[there] = fromHereToThere;
        }
    }

    for (let i = 0; i < shortest.length; i++) {
        if (shortest[i] !== Infinity) continue;
        shortest[i] = -1;
    }

    return shortest;
}

// Do not edit the line below.
exports.dijkstrasAlgorithm = dijkstrasAlgorithm;
```
