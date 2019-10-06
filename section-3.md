### Analyzing performance of arrays and objects

##### Big O of Objects

- insertion : O(1)
- Removal : O(1)
- Searching : O(N)
- Access : O(1)

```javascript
let instructor = {
  firstName: "kelly",
  isInstructor: true,
  favoriteNumbers: [1, 2, 3, 4]
};
```

##### Big O of method of Objects

- Object.keys : (O(N))
- Object.values : (O(N))
- Object.entries : (O(N))
- hasOwnProperty : (O(1))

##### When are arrays slow?

Arrays => ordered lists!

- Insertion : It depends ...
- Removal : It depends ...
- Searching : O(N)
- Access : O(1)

Insertion and Removal in beginning of Array is worth than End of Array

##### Big O of Array method

이 모든것을 알 필요는 없다...

- push: O(1)
- pop: O(1)
- shift: O(N)
- unshift: O(N)
- concat: O(N)
- slice: O(N)
- splice: O(N)
- sort: O(N\*logN)
- forEach/map/filter/reduce/etc ... : O(N)
