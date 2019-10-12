### Problem solving Approach

#### Introduction to problem solving

What is an algorithm?

- a process or set of steps to accomplish a certain task

How do you improve?

1. devise a plan for solving problems
2. master common problem solving patterns

Problem solving

- understand the problem
- explore concrete examples
- break it down
- solve/simplify
- look back and refactor

##### understand the problem

1. 이 문제에 대해서 나만의 말로 표현할 수 있는지?
2. 이 문제를 해결함에 있어서 input은 어떤것들이 될 것인지?
3. 이 문제의 해결책으로 어떠한 output들이 나올 수 있는지?
4. input들로부터 output이 결정될수 있는지, 문제를 풀기위한 충분한 정보가 있는지?
5. 어떻게 이 문제를 풀기위한 중요한 정보들에 labeling 할수 있는지?

##### explore examples

- 간단한 example로 생각해보기
- 더 어려운 example로 생각해보기
- 빈 input으로 example 생각해보기
- invalid input으로 생각해보기

ex: write a function whicj takes in as tring and returns counts of each character in the string.

```javascript
- 간단한 example로 생각해보기
  charCount("aaaa") // {a: 4}
  charCount("hello") // {h: 1, e: 1, l: 2, o: 1}

- 더 어려운 example로 생각해보기
  charCount("my phone number is 182763")
  charCount("Hello hi")

- 빈 input으로 example 생각해보기
  charCount("")

- invalid input으로 생각해보기
  charCount({} or null)

```

##### break in down

- explicitly write out the steps you need to take
  - 오해하고 있는것이나, 말로써 헷갈릴수 있는 컨셉들을 미리 생각해볼 수 있다.

```javascript
function charCount(str) {
  // make object to return at end
  // loop over string, for each character...
  // -if char is a number/letter AND is a key in object, add one to count
  // -if the char is a number/letter AND not in object, add it to object and set value to 1
  // -if character is something else (space, period, etc.) don't do anything
  // return object at end
}
```
