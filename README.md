# algo-stuff
A personal repo to document different approaches to algorithm questions

1) [Remove Duplicates](https://github.com/therealtylerwells/algo-stuff#remove-duplicates)
2) [Replace Something](https://github.com/therealtylerwells/algo-stuff#replace-something)
3) [Fizzbuzz](https://github.com/therealtylerwells/algo-stuff#fizzbuzz)
4) [Two Sum (LeetCode)](https://github.com/therealtylerwells/algo-stuff#two-sum)
5) [Median of Two Sorted Arrays (LeetCode)](https://github.com/therealtylerwells/algo-stuff#median-of-two-sorted-arrays)
6) [Reverse Integer (LeetCode)](https://github.com/therealtylerwells/algo-stuff#reverse-integer)
7) [Palindrome Number (LeetCode)](https://github.com/therealtylerwells/algo-stuff#palindrome-number)
8) [Remove Element (LeetCode)](https://github.com/therealtylerwells/algo-stuff#remove-element)
9) [Anagram Detection](https://github.com/therealtylerwells/algo-stuff#anagram-detection)
10) [Palindrome String Detection](https://github.com/therealtylerwells/algo-stuff#palindrome-string-detection)
11) [Get nth Fibonacci number](https://github.com/therealtylerwells/algo-stuff#get-nth-fibonacci-number)

## Remove Duplicates
Assume we need to remove any duplicate characters or words from a string
```js
// Set, an ES6 object, creates a store of unique values

const removeDuplicates = (string) => {
  const set = new Set(string.split(''))
  return Array.from(set).join('');
}

// removeDuplicates('1122344444') returns '1234'
// removeDuplicates('aabcdeffgaabc') returns 'abcdefg'

```

## Replace Something
Assume we need to replace any specific words or characters in a string with something else
```js
// Regex to the rescue. Let's replace 'American' with 'British' in the following string

const string = "I am American"
const longString = "I am American and my wife is American"

return string.replace(/American/g, "British") // "I am British"
return longString.replace(/American/g, "British") // "I am British and my wife is British"
return longString.replace(/American/, "British") // "I am British and my wife is American"
```

## Fizzbuzz
Classic Fizzbuzz. From 1 to 100, print 'fizz' if multiple of 3, print 'buzz' if multiple of 5, and if multiple of both 3 and 5, print 'fizzbuzz'. Else print the number.
```js
// Use the modulas operator and a for loop

for (i = 1; i <= 100; i++) {
  if (i % 3 == 0 && i % 5 == 0) console.log('fizzbuzz')
  else if (i % 3 == 0) console.log('fizz')
  else if (i % 5 == 0) console.log('buzz')
  else console.log(i)
}
```

## Two Sum
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

```js
// We can utilize nested for loops and check if indicies add up to the target we want

const twoSum = (nums, target) => {
    for (i = 0; i < nums.length; i++) {
        for (j = i+1; j < nums.length; j++) {
            if (nums[i] + nums[j] === target) {
                return [i, j]
            }
        }
    }
};
```

## Median of Two Sorted Arrays
```js
// We can concat and sort the arrays and then use Math.floor to find the median based on whether the 
// length of the array is even or odd. We use the modulas operator to determine even or odd.

const findMedianSortedArrays = (nums1, nums2) => {
    const length = nums1.concat(nums2).length;
    const arr = nums1.concat(nums2).sort(function (a, b) {return a - b})
    return length % 2 == 0 ? (arr[Math.floor(length / 2) -1] + arr[Math.floor(length / 2)]) / 2 : arr[Math.floor(length / 2)]
};
```

## Reverse Integer
Given a 32-bit signed integer, reverse digits of an integer. Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.
```js
// We use Math.sign to determine if number is negative or postive and proceed conditionally 
// with a basic toString -> split -> reverse -> join. 
// We then convert our value back to a number using Number.

const reverse = (x) => {
    if (Math.sign(x) > 0) {
        const x = x.toString().split('').reverse().join('')
        const y = Number(x)
    } else if (Math.sign(x) < 0) {
        const z = x.toString().substr(1);
        // A hacky way to change to negative. Could probably improve this
        const y = '-' + z.toString().split('').reverse().join('')
    } else {
        const y = 0;
    }
    if (Number(y) > 2147483647 || Number(y) < -2147483647) {
        return 0
    } else {
        return Number(y);
    }
};
```
## Palindrome Number
Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

```js
// Check if number/string is the same backwards as it is forwards

const isPalindrome = (x) => {
    return x == x.toString().split('').reverse().join('');
};
```
## Remove Element
Given an array nums and a value val, remove all instances of that value in-place and return the new length.

```js
// Loop through array. If we encounter val, then splice that index from the array.

const removeElement = (nums, val) => {
    for(var i = nums.length - 1; i >= 0; i--){
        if(nums[i] === val){
            nums.splice(i, 1);
        }
    }
};
```

## Anagram Detection
Given two strings, return true if they are anagrams, false if not

```js
// Ensure both strings are lowercase ->  split, sort, and join the strings -> compare them.

const detectAnagrams = (stringOne, stringTwo) => {
  let a = stringOne.toLowerCase();
  let b = stringTwo.toLowerCase();
  
  a = a.split('').sort().join('');
  b = b.split('').sort().join('');
  
  return a == b;
}
```

## Palindrome String Detection
Given a string, return true if it is a palindrome, false if not

```js
// Use Regex to replace any non-letter character with "", change to lowerCase, and 
// compare string vs reversed string

const palindromeDetection = (string) => {
  const letters = string.toLowerCase().replace(/\s/g, "");
  const reversed = letters.split('').reverse().join('');
  return letters == reversed;
}
```

## Get nth Fibonacci number
Given an input nth Fibonacci number, return the nth number in the Fibonacci sequence
(In the Fibonacci sequence, each number is the sum of the two preceding ones, starting from 0 and 1)

```js
const fibonacci = (n) => {
  let fibo = [0, 1];
  if (n <= 2) return 1;
  for (i = 2; i <=n; i++) {
    fibo[i] = fibo[i - 1] + fibo[i-2];
  }
  return fibo[n];
}

// fibonacci(10) returns 55
// fibonacci(12) returns 144
// fibonacci(2) returns 1
```
