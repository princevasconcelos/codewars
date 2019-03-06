# Code Wars code

## Challange 1

```
describe('example tests', function() {
  it('should return correct text', function() {
    Test.assertEquals(likes([]), 'no one likes this');
    Test.assertEquals(likes(['Peter']), 'Peter likes this');
    Test.assertEquals(likes(['Jacob', 'Alex']), 'Jacob and Alex like this');
    Test.assertEquals(likes(['Max', 'John', 'Mark']), 'Max, John and Mark like this');
    Test.assertEquals(likes(['Alex', 'Jacob', 'Mark', 'Max']), 'Alex, Jacob and 2 others like this');
  });
});
```

## Solution
```
function likes(names) {
  if (Object.prototype.toString.call(names) === '[object Array]' && names.length > 0) {
    return names.reduce((acc, item, index, arr) => {
      const isLast = index === arr.length - 1;
      const hasAnd = !!acc.match(/and/g);
      const hasNameWithSemicolon = !!acc.match(/\w+,/g)
    	let separator = ' and ';
    	if (isLast)
    		separator = ' ';
    	if (hasAnd)
    		separator = ', ';
    	if (hasNameWithSemicolon)
    		acc = `${acc.split(',')[0]} and ${arr.length - 2} others like this`;

    	return item + separator + acc;
    }, names.length === 1 ? 'likes this' : 'like this');
  }
  
  return 'no one likes this';
}
```