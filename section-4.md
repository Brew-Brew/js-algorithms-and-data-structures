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

##### solve or simplify

- simplify
  - 당신이 하려는것에서 가장 어려운것을 찾으세요
  - 잠시동안 그 어려운것을 무시해두세요
  - 간단한 solution을 작성해보세요
  - 그 어려웠던 것을 그때 합쳐보세요

```javascript
function charCount(str) {
  // make object to return at end
  var result ={};
  // loop over string, for each character...
  for(var i=0;i<str.length;i++>){
    var char = str[i].toLowerCase()
    // -if char is a number/letter AND is a key in object, add one to count
    if(result[char] > 0){
      result[char]++;
    }
    // -if the char is a number/letter AND not in object, add it to object and set value to 1
    else{
      result[char] = 1;
    }
  }
  // -if character is something else (space, period, etc.) don't do anything
  // return object at end

  return result;
}
```
##### look back and refactor

리팩토링 질문들

- can you check the result?
- can you derive the result differently?
- can you understand it at a glance?
- can you use the result or method for some other problem?
- can you improve the performance of your solution?
- can you think of other ways to refactor?
- how have other people solved this problem?

```javascript
function charCount(str){
  var obj = {};
  for (var char of str){
    char = char.toLowerCase();
    if(/a-z0-9/.test(char)){
      if(obj[char] > 0) {
        obj[char]++;
      }else {
        obj[char] = 1;
      }
    }
  }
  return obj;
}
```
- 정규표현식은 브라우저나, 여러 상황에 따라 성능이 다를 수 있음

```javascript
function charCount(str){
  var obj = {};
  for (var char of str){
    char = char.toLowerCase();
    if(/a-z0-9/.test(char)){
      obj[char] = ++obj[char] || 1;
    }
  }
  return obj;
}
```

- 아래와 같은 답안도 있다고 명시해주는것이 좋음 
```javascript
function isAlphaNumeric(char){
  var code = char.charCodeAt(0);
  if(!(code > 47 && code < 58) && // numeric (0-9)
     !(code > 64 && code < 91) && // upper alpha (A-Z)
     !(code > 96 && code < 123>)){ // lower alpha (a-z)
       return false
     }
     return true; 
}


function charCount(str){
  var obj = {};
  for (var char of str){
    char = char.toLowerCase();
    if(isAlphaNumeric(char)){
      obj[char] = ++obj[char] || 1;
    }
  }
  return obj;
}
```