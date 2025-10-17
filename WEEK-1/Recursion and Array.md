# 📘 Arrays in JavaScript

## 🧩 What is an Array?

An **array** is a linear data structure used to store multiple values in a single variable.  
It stores **elements of the same or different types** in a **contiguous memory block**, allowing efficient indexing and traversal.

```js
let arr = [10, 20, 30, 40];
```
# Recursion 

Recursion means a function calling itself to solve a smaller version of the same problem — until it reaches a point where it stops (called the base case).
Consists of 2 cases, a base case and a recursive case

## 🔁 Real-life example:

Imagine you’re standing on a staircase and want to count how many steps are there.

Instead of counting all at once:

You look at the first step and say:
“I’ll count this one, and then I’ll ask the person on the next step to count the rest.”

That person does the same — asks the next person — until the last person says:
“There are no more steps!”

Then everyone adds their count while going back up.

That’s recursion — each person (function call) depends on the next smaller step (subproblem).

 ## Array question and answers:
### Sum of first N natural numbers 
 ```js
let n =5
function sum(n){
    if(n==0)return n
    return n+sum(n-1) 
}
console.log(sum(n))
```


### Factorial of a number
```js
let n = 3
function fac(n){
    if(n==1)return n
    return n*fac(n-1) 
}
console.log(fac(n))
```

### Check if  a string is a **Palindrome**
```js
let str ='MalayalaM'
function palindrome(s){
    let rev = reverse(s)
     return rev == s
}
function reverse(a){
    if(a.length==1)return a
    return reverse(a.slice(1))+a[0]
}
console.log(palindrome(str))
//or..

function isPalindrome(str, i = 0, j = str.length - 1) {
  if (i >= j) return true;
  if (str[i] !== str[j]) return false;
  return isPalindrome(str, i + 1, j - 1);
}

```

```js


### Reverse a string and array with recursion
```js
function revStr(a) {
  if (a.length <= 1) return a;
  return a[a.length - 1] + revStr(a.slice(0, -1));
}

function reverseString(str) {
  if (str.length <= 1) return str;
  return reverseString(str.slice(1)) + str[0];
}


function revArr(a) {
  if (a.length <= 1) return a;
  return [a[a.length - 1], ...revArr(a.slice(0, -1))];
}
```


