- Min Max Stack Construction
    
    ![Screenshot 2023-01-25 at 1.45.04.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5fd4e48a-e2d6-477c-baa9-eeb3027c47d2/Screenshot_2023-01-25_at_1.45.04.png)
    
    - 1, 1
    
    ```jsx
    // Feel free to add new properties and methods to the class.
    class MinMaxStack {
    
      constructor() {
        this.stack = []; 
        this.minMax = [];
        this.min = Infinity;
        this.max = -Infinity;
      }
      
      peek() {
        return this.stack[this.stack.length - 1];
      }
    
      pop() {
        this.minMax.pop();
        return this.stack.pop();
      }
    
      push(number) {
        this.stack.push(number);
        const nextMinMax = [Math.min(this.getMin(), number), Math.max(this.getMax(), number)];
        this.minMax.push(nextMinMax);
      }
    
      getMin() {
        return this.getMinMax()[0];
      }
    
      getMax() {
        return this.getMinMax()[1];
      }
    
      getMinMax() {
        const minMax = this.minMax[this.minMax.length - 1];    
        if (minMax === undefined) return [Infinity, -Infinity];
        return minMax;
      }
    }
    
    // Do not edit the line below.
    exports.MinMaxStack = MinMaxStack;
    ```
