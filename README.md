# algo-stuff
A personal repo to document different approaches to algorithm questions

1) [Remove Duplicates](https://github.com/therealtylerwells/algo-stuff#remove-duplicates)
2) [Replace Something](https://github.com/therealtylerwells/algo-stuff#replace-something)
3) [Fizzbuzz](https://github.com/therealtylerwells/algo-stuff#fizzbuzz)

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
