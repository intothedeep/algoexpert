Remove Kth Node From End

- Remove Kth Node From End
  ![Screenshot 2023-01-24 at 17.21.08.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7c6c2cb5-eaf5-4050-81eb-6d2e74950cc9/Screenshot_2023-01-24_at_17.21.08.png)
  - n, 1
  ```jsx
  // This is an input class. Do not edit.
  class LinkedList {
    constructor(value) {
      this.value = value;
      this.next = null;
    }
  }

  function removeKthNodeFromEnd(head, k) {
    let first = head;
    let second = head;

    // whenn k is equal to the length of this linkedList with head
    // second is null
    let count = 1;
    while (count <= k) {
      second = second.next;
      count++;
    }

    // second is null, it means remove head
    if (second === null) {
      head.value = head.next.value;
      head.next = head.next.next;
      return;
    }

    while (second.next !== null) {
      second = second.next;
      first = first.next;
    }

    console.log({
      k,
      first: first.value,
      second: second.value,
    });

    first.next = first.next.next;
    return head;
  }

  // Do not edit the lines below.
  exports.LinkedList = LinkedList;
  exports.removeKthNodeFromEnd = removeKthNodeFromEnd;
  ```
