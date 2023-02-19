Kruskal’s algorithm

- ElogE, E + V

```jsx
function kruskalsAlgorithm(edges) {
  // create arr to store edge
  const weightEdges = [];
  for (let i = 0; i < edges.length; i++) {
    const here = i;
    for (const [there, weight] of edges[here]) {
      weightEdges.push([here, there, weight]);
    }
  }

  // sort arr asc depending on edge weight
  weightEdges.sort((a, b) => a[2] - b[2]);

  // crate union find
  const uf = new UnionFind(edges.length);
  // create mst to find 
  const mst = edges.map(a => []);
  for (let i = 0; i < weightEdges.length; i++) {
    const [here, there, weight] = weightEdges[i];
    if (uf.find(here) === uf.find(there)) continue;
    mst[here].push([there, weight]);
    mst[there].push([here, weight]);
    uf.union(here, there);
  }
  
  return mst;
}

class UnionFind {
  constructor(size) {
    this.arr = new Array(size);
    for (let i = 0; i < size; i++) {
      this.arr[i] = i;
    }
    this.weights = new Array(size).fill(0);
  }
  

  create(a) {
    return this.arr[a] = a;
  }

  find(value) {
    if (value === undefined) 
      return null;

    if (this.arr[value] === value)
      return value;

    return this.arr[value] = this.find(this.arr[value]);
  }

  union(a, b) {
    const rootA = this.find(a);
    const rootB = this.find(b);
    if (rootA === rootB) return;
    
    if (this.weights[rootA] > this.weights[rootB]) {
      this.arr[rootB] = rootA;
      this.weights[rootA]++;
    } else {
      this.arr[rootA] = rootB;
      this.weights[rootB]++;
    }
    
    return;
  }
  
}

// Do not edit the line below.
exports.kruskalsAlgorithm = kruskalsAlgorithm;
```
