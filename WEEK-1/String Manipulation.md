# DSA Notes — Strings
## 1. What is a String?

A **String** is a sequence of characters stored in a continuous memory location.

Example:
"hello", "DSA", "12345"

Strings are usually **immutable** in many languages (like Java, Python), meaning they cannot be changed directly; instead, new strings are created.

---

## 2. Important String Operations

* Traversing a string
* Finding length
* Reversing a string
* Checking palindrome
* Counting characters
* Substring extraction
* Comparing strings

---

## 3. Time Complexity Basics

* Traversing string → **O(n)**
* Reversing string → **O(n)**
* Checking palindrome → **O(n)**

---

## 4. Sample Workouts

### Workout 1 — Reverse a String

**Question:**
Given a string `s`, reverse the string and return the result.

**Example:**

```
Input: "hello"
Output: "olleh"
```

**Your Solution:**

```js
function rev(s){
    if(s.length==1)return s
    return rev(s.slice(1))+s[0]
}
console.log(rev("AideN"))
```

---

### Workout 2 — Check Palindrome

**Question:**
Check whether a given string is a palindrome (reads same forward and backward).

**Example:**

```
Input: "madam"
Output: true
```

**Your Solution:**

```js
function pal(s,i=0,j=s.length-1){
    if(i>=j)return console.log("the word is a palindrome")
    if(s[i]!= s[j])return console.log("It is not a palindrome")
    return pal(s,i+1,j-1)
}
pal("malayalam")
```

---

### Workout 3 — Count Vowels in a String

**Question:**
Given a string, count how many vowels (`a, e, i, o, u`) are present.

**Example:**

```
Input: "education"
Output: 5
```

**Your Solution:**

```
function countVow (s){
    let vow=['a','e','i','o','u']
    let count=0
    for(let i= 0 ; i < s.length;i++){
        if(vow.includes(s[i]))count++
    }
    console.log("count:",count)
}
countVow("aiden")
```

---

## 5. Practice Ideas (Extra)

* Remove spaces from a string
* Find first non-repeating character
* Convert lowercase to uppercase without built-in functions
* Find frequency of each character

## Workouts

1. Write a function to replace each alphabet in the given string with another alphabet occurring at the n-th position from each of them.
```js
let str = "my name is aiden"
function change(s,n){
    let ans=""
    for(let i = 0 ; i < s.length;i++){
        // ans+= s.charCodeAt(i)+n
        let code = s.charCodeAt(i)+n
        if(code>122){
            code=(code-122)+97
        }
     ans+=String.fromCharCode(code)
     
    }
    console.log(ans)
}
change(str,1)

```
2. Remove spaces from a string

```js
function remSpace(s){
    return console.log(s.split(" ").join(""))
}
remSpace("ed uc at ion")
```
3. Find the first non-repeating character

```js
function rep(s){
    for(let i = 0 ; i <s.length;i++){
        if(s.lastIndexOf(s[i])==i)return console.log("the first non repeating character:", s[i])
    }
}
rep("axizdexnaides")
```
4. Convert lowercase to uppercase without built-in functions

```js
function conv(s){
    let ans =""
    for(let i = 0 ;i <s.length;i++){
      ans+=(s[i]==" ")? " ":String.fromCharCode(s.charCodeAt(i)-32)
    }
    console.log(ans)
}
conv("aiden make it uppercase")
```
