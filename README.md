# Javascript Quiz (ES6)

*A collection of javascript base quiz*

## Array
  - **Q**: How to copy an array?

    **A**:
    ```javascript
    const items = [1,2,3];
    const itemsCopy = [...items];
    const itemsCopy1 = items.slice();
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

  - **Q**: How to prevent multiple click (multiple function excution)?

    **A**: Use debounce && throttle (Could be found in lodash).
    ```javascript
    function debounce(fn, delay) {
        let timer = null;

        return function() {
            let context = this;
            let args = arguments;

            timer && clearTimeout(timer);
            timer = setTimeout(function() {
                fn.apply(context, args);
            }, delay);
        }
    }
    ```
**[⬆ back to top](#table-of-contents)**

## Events
  - **Q**: How to add large mount of event listeners?

    **A**: Add listener to their container or use jQuery 'on'
    ```javascript
    let app = document.getElementById('todo-app');

    document.getElementByTagName('ul').addEventListener('click', function(e) {
        if (e.target && e.target.nodeName === 'LI') {
          let item = e.target;
          alert('you clicked on item: ' + item.innerHTML);
        }
    });
    or
    $('ul').on('click', 'li', function() {});
    ```
  - **Q**: Difference between e.target and e.currentTarget?

    **A**: e.target trigger the event, e.currentTarget register the event

**[⬆ back to top](#table-of-contents)**

## Closure
  - **Q**: Verify the code below?
    ```javascript
    const arr = [10, 12, 15, 21];
    for (var i = 0; i < arr.length; i++) {
        setTimeout(function() {
            console.log('The index of this number is: ' + i);
        }, 3000);
    }
    ```

    **A**:
    ```javascript
    const arr = [10, 12, 15, 21];
    for (var i = 0; i < arr.length; i++) {
        setTimeout(function(i_local) {
            return function() {
                console.log('The index of this number is: ' + i_local);
            }
        }(i), 3000);
    }
    or
    const arr = [10, 12, 15, 21];
    for (let i = 0; i < arr.length; i++) {
        // 'let' will create a new scope
        setTimeout(function() {
            console.log('The index of this number is: ' + i);
        }, 3000);
    }
    ```
**[⬆ back to top](#table-of-contents)**