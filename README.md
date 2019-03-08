# Challange 1
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


# Challange 2
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


# Challange 3
```js
  Test.describe("FindEvenIndex", function() {
    Test.it("Tests", function() {
      Test.assertEquals(findEvenIndex([1,2,3,4,3,2,1]),3, "The array was: [1,2,3,4,3,2,1] \n");
      Test.assertEquals(findEvenIndex([1,100,50,-51,1,1]),1, "The array was: [1,100,50,-51,1,1] \n");
      Test.assertEquals(findEvenIndex([1,2,3,4,5,6]),-1, "The array was: [1,2,3,4,5,6] \n");
      Test.assertEquals(findEvenIndex([20,10,30,10,10,15,35]),3, "The array was: [20,10,30,10,10,15,35] \n");
    });
  });
```

## Solution
```js
  const findEvenIndex = arr => {
    let index = -1;
    arr.forEach((_, i) => {
      const left = arr.slice(0, i).reduce((acc, item) => acc + item, 0);
      const right = arr.slice(i + 1).reduce((acc, item) => acc + item, 0)
      if (left === right) index = i
    });
    return index
  }
```


# Challange 4
```js
  Test.assertEquals(createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]), "(123) 456-7890");
```

## Solution
```js
  const createPhoneNumber = numbers => "(xxx) xxx-xxxx".replace(/[x]/g, () => numbers.shift());
```

## Others Solution
```js
  function createPhoneNumber(numbers){
    return numbers.join('').replace(/(...)(...)(.*)/, '($1) $2-$3');
  }

  function createPhoneNumber(numbers){
    return numbers.join('').replace(/(\d{3})(\d{3})(\d{4})/,'($1) $2-$3');
  }
```


# Challange 5
```js
  Test.assertEquals(seven(times(five())), 35);
  Test.assertEquals(four(plus(nine())), 13);
  Test.assertEquals(eight(minus(three())), 5);
  Test.assertEquals(six(dividedBy(two())), 3);
```

## Solution
```js
  const valueFor = num => func => func ? func(num) : num

  const one = valueFor(1);
  const two = valueFor(2);
  const three = valueFor(3);
  const four = valueFor(4);
  const five = valueFor(5);
  const six = valueFor(6);
  const seven = valueFor(7);
  const eight = valueFor(8);
  const nine = valueFor(9);
  const zero = valueFor(0);

  const plus = rightValue => leftValue => leftValue + rightValue;
  const minus = rightValue => leftValue => leftValue - rightValue;
  const times = rightValue => leftValue => Math.floor(leftValue * rightValue);
  const dividedBy = rightValue => leftValue => Math.floor(leftValue / rightValue);
```

# Challange 6
```js
  Test.assertEquals( digital_root(16), 7 )
  Test.assertEquals( digital_root(456), 6 )
```

## Solution
```js
  const digital_root = n => (''+n).length > 1 ? digital_root(Array.from(''+n, Number).reduce((acc, item) => acc + item)) : n;
```

## Others Solution
```js
  function digital_root(n) {
    return (n - 1) % 9 + 1;
  }
```


# Challange 7
```js
  Test.describe("longestConsec",function() {
  Test.it("Basic tests",function() { 
      testing(longestConsec(["zone", "abigail", "theta", "form", "libe", "zas"], 2), "abigailtheta")
      testing(longestConsec(["ejjjjmmtthh", "zxxuueeg", "aanlljrrrxx", "dqqqaaabbb", "oocccffuucccjjjkkkjyyyeehh"], 1), "oocccffuucccjjjkkkjyyyeehh")
      testing(longestConsec([], 3), "")
      testing(longestConsec(["itvayloxrp","wkppqsztdkmvcuwvereiupccauycnjutlv","vweqilsfytihvrzlaodfixoyxvyuyvgpck"], 2), "wkppqsztdkmvcuwvereiupccauycnjutlvvweqilsfytihvrzlaodfixoyxvyuyvgpck")
      testing(longestConsec(["wlwsasphmxx","owiaxujylentrklctozmymu","wpgozvxxiu"], 2), "wlwsasphmxxowiaxujylentrklctozmymu")
      testing(longestConsec(["zone", "abigail", "theta", "form", "libe", "zas"], -2), "")
      testing(longestConsec(["it","wkppv","ixoyx", "3452", "zzzzzzzzzzzz"], 3), "ixoyx3452zzzzzzzzzzzz")
      testing(longestConsec(["it","wkppv","ixoyx", "3452", "zzzzzzzzzzzz"], 15), "")
      testing(longestConsec(["it","wkppv","ixoyx", "3452", "zzzzzzzzzzzz"], 0), "")
  })})
```

## Solution
```js
  const longestConsec = (strarr, k) => {
    let longest = '';

    if (strarr.length === 0 || k > strarr.length || k <= 0)
      return longest;
    
    strarr.forEach((_, i) => {
      const newStr = [...strarr].splice(i, k).join('');
      if (newStr.length > longest.length)
        longest = newStr
    })
    return longest;
  }
```