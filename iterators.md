## ARRAY ITERATOR FUNCTIONS

1. `forEach()`
  * The `forEach()` method executes a provided function once for each array element
  * The reason to use `forEach` is to have side effects for each item in an array
  ```
  [1, 2, 3].forEach(function(item) {
    console.log(item);
  });
  ```
  ```
  const copy = [];
  [1, 2, 3].forEach(function(item){
    copy.push(item);
  });
  console.log(copy);
  ```
2. `map()`
  * The `map()` method creates a new array with the results of calling a provided function on every element in the calling array
  * The reason to use `map()` is to transform each item in the array and get a new array
  * Etiquette says that map should never have side effects, though this isn't enforced in any way.
  ```
  const doubles = [1, 2, 3].map(function(num) {
    return num * 2;
  });
  ```
  ```
  var numbers = [1, 4, 9];
  var roots = numbers.map(Math.sqrt);

  console.log('numbers', numbers);
  console.log('roots', roots);
  ```
3. `filter()`
  * The `filter()` method creates a new array with all elements that pass the test implemented by the provided function
  * The reason to use `filter()` is to get a new array that only contains items that match the criteria you're looking for
  * The internal function must return `true` or `false`
  * Etiquette says that `filter()` should never have side effects, though this isn't enforced in any way
  ```
  [1, 2, 3].filter(function(num) {
    return num >= 3;
  });
  ```
  ```
  /* ES6 Function Syntax */
  ["spray", "exuberant", "destruction", "happy"].filter(
    word => word.length > 6
  );
  ```
4. `reduce()`
  * The `reduce()` method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value
  * The reason to use `reduce()` is to "reduce" an array of values or objects into a single value or object
  * If no initial value is supplied, the first element in the array will be used
  ```
  /* Using reduce() to sum values in an array */
  [1, 2, 3].reduce(function(total, current) {
    return total + current;
  });
  ```
  ```
  /* Using reduce() with an initial accumulator value */
  [1, 2, 3].reduce(function(acc, i) {
    return acc + i;
  }, 2);
  ```
  ```
  /* Using reduce() to count instances of values in an object */
  var names = ['Mady', 'Joey', 'Charlie', 'Rock', 'Oz', 'Buck', 'Mady'];
  var countedNames = names.reduce(function (count, name) {
    if (name in count) {
      count[name]++;
    }
    else {
      count[name] = 1;
    }
    return count;
  }, {});
  ```
How could you simplify the previous reduce method? (hint: you don't need an `if...else` statement)
