# Code Wars code

## Challange 1
```js
  divisors(12); // should return [2,3,4,6]
  divisors(25); // should return [5]
  divisors(13); // should return "13 is prime"
```

## Solution
```js
function divisors(integer) {
  const numbers = Array.from({ length: integer }, (_, i) => i + 1).slice(1)
  const divisibles = numbers.filter(i => integer !== i  && integer % i === 0)
  if (divisibles.length === 0) 
    return `${integer} is prime`
  return divisibles
};
```

## Challange 2
```js
  a = "xyaabbbccccdefww"
  b = "xxxxyyyyabklmopq"
  longest(a, b) -> "abcdefklmopqwxy"

  a = "abcdefghijklmnopqrstuvwxyz"
  longest(a, a) -> "abcdefghijklmnopqrstuvwxyz"
```

## Solution
```js
  const longest = (s1, s2) => [...new Set(s1+s2)].sort().join('')
```

