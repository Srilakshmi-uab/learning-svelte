# Svelte Calculator
- A simple calculator made using svelte and sveltekit
- Author: Srilakshmi Malempati
- email: srilakshmiaruna32@gmail.com


## Run the application
```
npm install
```

```
npm run dev
```

## Front End

 - This is a single page app.

 - I didn't use any svelte UI library. I only used vanilla CSS.

 

- This second if statement becomes true whenever `char` is an operation or when we are in the last element of the `expression` array

- The `temp` variable stores the previously selected integer which is taken from the `stack` array using `stack.pop()`.

- Then we have a switch statement that evaluates what `sign` variable has which stores the previously selected operation.

 - Once it determines what operation it is then it executes the following blocks of code.

     - `case: +` - just push the currently selected number to the `stack` array

     - `case: -` - make the currently selected number into a negative then push it to the `stack` array

     - `case: *` - Immediately perform the operation...
    1. First by storing the previously processed number in `temp` by getting the last element in the `stack` using `stack.pop()`
    2. Then multiply the previously(`temp`) and currently(`selected`) selected number and push it to the `stack` array

    - `case: /` - Immdiately perform the operation...
    1. First by storing the previously processed number in `temp` by getting the last element in the `stack` using `stack.pop()`
    2. Then divide the previously(`temp`) and currently(`selected`) selected number and push it to the `stack` array

- Like I said earlier when we encounter an operation then `hasDecimal` will be equals to false since we will look into a new number.

- The second to the last statement which is `sign = char` proves what I said that `sign` variable stores the previously selected sign because `char` variable is the one that stores the currently selected number or operation.

- The last statement just resets the `selected` variable


- The `result` variable stores the final answer

- The `while` loop runs until we reached the first element in the `stack` array. So we will add the numbers starting from the last element of the `stack` array until the very first element.

> So the computation of the elements inside the `stack` array looks like this. e.g. +53+5+(-20)+2+(-31)

- Lastly we will just return the `result`
.