# Javascript Quiz (ES6)

*A collection of javascript base quiz*

## Array
  - **Q**: How to copy an array?
    ```javascript
    const items = [1,2,3];
    const itemsCopy = [...items];
    ```

  - **Q**: How to convert an array-like object to an array? (e.g. arguments in function)
    ```javascript
    function func(...args) {
        return args;
    }
    or
    function func() {
        return Array.from(arguments);
    }
    ```
**[⬆ back to top](#table-of-contents)**

## Object
  - **Q**: How to destucturing a object?
    ```javascript
    let {firstName, lastName} = {firstName: 'Paul', lastName: 'Yu'};
    
    // good
    function getFullName(user) {
        const { firstName, lastName } = user;
        return `${firstName} ${lastName}`;
    }
    
    // best
    function getFullName({ firstName, lastName }) {
        return `${firstName} ${lastName}`;
    }
    ```
**[⬆ back to top](#table-of-contents)**

## Function
  - **Q**: Difference between codes below?
    ```javascript
    function example() {
        superPower(); // => Flying

        function superPower() {
            console.log('Flying');
        }
    }
    ```
    ```javascript
    function example() {
        superPower(); // => Uncaught TypeError: superPower is not a function

        var superPower = function() {
            console.log('Flying');
        }
    }
    ```
**[⬆ back to top](#table-of-contents)**
