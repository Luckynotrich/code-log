[Free Code Camp](https://www.freecodecamp.org/news/how-to-validate-a-date-in-javascript/)
August 22, 2023 / [#JavaScript](https://www.freecodecamp.org/news/tag/javascript/)

# [JS Date Validations – How To Validate a Date in JavaScript (With Examples)](https://www.freecodecamp.org/news/how-to-validate-a-date-in-javascript/)
```js
et dateInput = "2019/05/15"; // YYYY/MM/DD format

let dateObj = new Date(dateInput);

console.log(dateObj); // 2019-05-15T00:00:00.000Z
console.log(typeof dateObj)// object
```

Check function for string as valid date
```js
function isDateValid(dateStr) {
  return !isNaN(new Date(dateStr));
}

// DD/MM/YYYY
console.log(isDateValid("15/05/2019")); // false

// MM/DD/YYYY
console.log(isDateValid("05/15/2019")); // true

// YYYY/MM/DD
console.log(isDateValid("2019/05/15")); // true
```


## How to Check if a Date is in the Past or Future

To check if a date is in the past or future, you can use the less than `<` operator to compare the input date with the current date.

When the result is `true`, then the input date is in the past:

```js
// The date you want to check
const inputDate = new Date('2023-08-20'); 

// Get the current date
const currentDate = new Date();

// Compare the input date with the current date
if (inputDate < currentDate) {
  console.log('The input date is in the past.');
} else {
  console.log('The input date is in the future.');
}
```