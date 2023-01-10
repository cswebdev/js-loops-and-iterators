#### Looping Methods

Loops offer a quick and easy way to do something repeatedly.

**for statement**

A `for` loop repeats until a specified condition evaluates to `false`.

- Use when you need to increment by more than 1 or return early
- Requires 3 things: initialExpression, condition and incrementExpression

```
for(initialExpression, condition, incrementExpression) {
  // code block
}
```

- Use let to ensure the variable is scoped to the code block
- If you use var, the variable "leaks" out of the the for statement into the outer scope

```
for (let i = 2; i <= 100; i += 2) {
  console.log(i);
}
```

```
const numbers = [2, 34, 3, 23, 42, 3, 1, 65];

for (let i = 0; i < numbers.length; i++) {
  console.log(numbers[i]);
}
```

**for...of (2015)**

The `for...of` statement creates a loop that iterates over property values.

- Used for looping over an iterable - something that has a length (e.g. an array or a string)
- CAN NOT be used to loop over an object

```
const numbers = [2, 34, 3, 23, 42, 3, 1, 65];

for (const number of numbers) {
  console.log(number)
}

const name = 'Gavin Figueruelo';

for (const letter of name) {
  console.log(letter);
}
```

By default, when you loop over an array using `for...of`, you don't have access to the index. But you can use destructuring to access both the index and the value.

```
for (const [index, number] of numbers.entries()) {
  console.log(`index ${index} is ${number}`);
}
```

- Make sure you use `const` or `let` instead of `var`. If you use `var`, you'll override the variable everytime and leak it to the global (outer) namespace.

```
for (var number of numbers) {
  setTimeout(() => console.log(number), 1000);
}
```

```
for (const number of numbers) {
  setTimeout(() => console.log(number), 1000);
}
```

**for...in**

The `for...in` statement creates a loop that iterates over all the enumerable properties of an object.

- Used for looping over keys of an object
- Will loop over properties and methods on the prototype chain (this will make more sense when we cover constructors and prototypes)

```
const student = {
  name: 'sally',
  age: 100,
  isCool: true
}

for (const prop in student) {
  console.log(prop);
}
```

**while statement**

A `while` statement executes its statements as long as a specified condition evaluates to `true`.

- Be careful that you don't create an infite loop. Don't forget the exit condition!

```
/* This create an infinite loop! We don't want that. */
let cool = true;

while (cool === true) {
  console.log('You are cool');
}
```

```
/* This does not create an infinite loop. This is what we want! */
let cool = true, i = 1;
while (cool === true) {
  console.log('You are cool');
  i++;
  if (i > 100) {
    cool = false; // triggers exit condition
  }
}
```

**do...while**

A `do...while` statement repeats until a specified condition evaluates to false.

- Different from a `while` loop because it will run first and then check the condition.

```
let check = false;

do {
  statement
} while(check);
```

```
let i = 0;
do {
  i += 1;
  console.log(i);
} while (i < 5);
```

**Supplemental**

Example of `for of` using a function with unknown arguments

```
function addUpNumbers() {
  console.log(arguments); // array like - not an array
  // you could convert it to an array and call reduce
  // const args = Array.from(arguments)

  // but you can also loop over it as is
  let total = 0;
  for (num of arguments) {
    total += num;
  }
  return total;
}

addUpNumbers(1,2,4,5,6,4,3,2,6,5,4,2);
```

When working with `Arrays`, be careful using `for...in` if you've modified the proptotype.

```
Array.prototype.shuffle = function() {
  let i = this.length, j, temp;

  if(i == 0) return this;

  while(--i) {
    j = Math.floor(Math.random() * (i + 1));
    temp = this[i];
    this[i] = this[j];
    this[j] = temp;
  }

  return this;
}

for (const index in numbers){
  console.log(index); // will loop over items added to the prototype
}
```
