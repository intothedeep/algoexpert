- Sunset Views
    
    ![Screenshot 2023-02-04 at 17.08.34.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6ace1f4b-7b65-4a8f-9702-5f471246321c/Screenshot_2023-02-04_at_17.08.34.png)
    
    - n, n
    
    ```tsx
    const EAST = 'EAST';
    const WEST = 'WEST';
    
    function sunsetViews(buildings, direction) {
    
      if (direction === EAST) {
        buildings.reverse();
      }
    
      let maxHeight = -Infinity;
    
      let answer = [];
      for (let i = 0; i < buildings.length; i++) {
        const curr = buildings[i];
        if (maxHeight >= curr) continue;
        
        maxHeight = curr;
        answer.push(i);
      }
    
      if (direction === EAST) {
        answer = answer.map(idx => buildings.length - 1 - idx).reverse();
      }
      
      return answer;
    }
    
    // Do not edit the line below.
    exports.sunsetViews = sunsetViews;
    ```
