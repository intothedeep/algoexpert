- Reverse Words in String
    
    ![Screenshot 2023-02-05 at 14.27.30.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/10b2016c-e97b-43cc-9e18-a4161677c884/Screenshot_2023-02-05_at_14.27.30.png)
    
    - n, n
    
    ```tsx
    function reverseWordsInString(str) {
    
      const arr = [];
      let word = [];
      for (let i = 0; i < str.length; i++) {
        const curr = str[i];
        if (curr !== ' ') {
          word.push(curr);
          continue;
        }
        
        arr.unshift(...word);
        arr.unshift(curr)
        word = [];
      }
    
      if (word.length > 0) 
        arr.unshift(...word);
    
      return arr.join('');
    }
    
    // Do not edit the line below.
    exports.reverseWordsInString = reverseWordsInString;
    ```
