##### counting operations

컴퓨팅 속도에 따라 달라지는 연산 시간을 재기 보다는, 컴퓨터가 해야 하는 **연산의 횟수**에 초점을 맞추기

```javascript
function addupTo(n) {
  return (n * (n + 1)) / 2;
}
```

- 1 multiplication , 1 addition , 1 division
- input에 상관없이 연산횟수 동일

```javascript
function addUpTo(n) {
  let total = 0;
  for (let i = 1; i <= n; i++) {
    total += i;
  }
  return total;
}
```

- 1 assignment
- 1 assignment , n comparisons, n additions and n assignments
- n additions, n assignments
- 5n+2 (확실한숫자보다는, 연산횟수는 n에 비교해 러프하게 증가함

참고: https://rithmschool.github.io/function-timer-demo/ 각 함수들 퍼포먼스 트래커

##### Big O

- Big o notation is a way to formalize fuzzy counting
- we only care about details, only trends
- O(f(n))

f(n) = n => linear
f(n) = n² => quadratic
f(n) = 1 => constant

```javascript
function addupTo(n) {
  return (n * (n + 1)) / 2;
}
```

- O(1)

```javascript
function addUpTo(n) {
  let total = 0;
  for (let i = 1; i <= n; i++) {
    total += i;
  }
  return total;
}
```

- O(n)

```javascript
function countUpAndDown(n) {
  console.log("Going up!");
  for (var i = 0; i < n; i++) {
    console.log(i);
  }
  console.log("At the top!\nGoing down...");
  for (var j = n - 1; j >= 0; j--) {
    console.log(j);
  }
  console.log("Back down. Bye!");
}
```

- O(n)

```javascript
function printAllPairs(n) {
  for (var i = 0; i < n; i++) {
    for (var j = 0; j < n; j++) {
      console.log(i, j);
    }
  }
}
```

- O(n²)

##### Simplifying Big O expressions

- constants don't matter

  - o(2n) => o(n), o(500)=> o(1), o(n²+ 5n+ 8)=> o(n²)

- Big O shorthands

  1. arithmetic operations are constant
  2. variable assignment is constant
  3. accessing elements in an array (by index) or object(by key) is constant
  4. in loop, complexity is the **length of the loop times** the complexity of whatever happens inside of the loop

- couple more examples

```javascript
function logAtLeast5(n) {
  for (var i = 1; i <= Math.max(5, n); i++) {
    console.log(i);
  }
}
```

- O(n) , n이 무한정 증가하는 것에 따라 생각하라 (함수의 극한값과 연관지으면 좋을것 같음)

```javascript
function logAtMost5(n) {
  for (var i = 1; i <= Math.min(5, n); i++) {
    console.log(i);
  }
}
```

- O(1) , n이 무한정 증가하는 것에 따라 생각하라 (함수의 극한값과 연관지으면 좋을것 같음)

- big o 참고용 그래프
  ![image](https://i.imgur.com/VXkPNWj.png)

quiz 중 하나

```javascript
function subtotals(array) {
  var subtotalArray = Array(array.length);
  for (var i = 0; i < array.length; i++) {
    var subtotal = 0;
    for (var j = 0; j <= i; j++) {
      subtotal += array[j];
    }
    subtotalArray[i] = subtotal;
  }
  return subtotalArray;
}
```

- O(n²)

##### space complexity

- 알고리즘의 메모리 사용량에 대한 분석결과

- auxiliary space complexity
  - **not including space taken by the inputs**
- space complexity in js
  - most primitives(boolean, numbers, undefined, null) -> `constant space`
  - `strings` -> require O(n) space -> string 길이 = n
  - reference types are generally O(n)
    - where n is the length (`for array`)
    - or the number of keys (`for object`)

```javascript
function sum(arr){
  let total = 0;
  for(let i=0; i <arr.length; i++>){
    total += arr[i];
  }
  return total;
}
```

- O(1) space

```javascript
function double(arr) {
  let newArr = [];
  for (let i = 0; i < arr.length; i++) {
    newArr.push(2 * arr[i]);
  }
  return newArr;
}
```

= O(n) space

##### logarithms

- time complexity is log + algorithms
- 때때로 big o notation이 log와 같은 복잡도를 가지기도 한다.
- logarithm of a number roughly measures the number of times you can divide that number by 2 **before you get a value less than or equal to one**

  ![스크린샷 2019-09-28 오후 6 24 54](https://user-images.githubusercontent.com/26598542/65814501-a1eb6b80-e21d-11e9-802a-774663740c20.png)
