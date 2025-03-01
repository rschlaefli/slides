# Automated testing in JavaScript

## Automated testing

code may be tested automatically to ensure it behaves as expected

## Tools for testing JavaScript

- _node_ is needed to provide a runtime
- _assert_: basic assertion package, built into node
- _Jest_: test runner and assertion library
- _Mocha_ and _Chai_: test runner and assertion library

popularity:

- [State of JS 2021: survey on test tools](https://2021.stateofjs.com/en-US/libraries/testing/)
- [npmtrends](https://www.npmtrends.com/jest-vs-mocha-vs-chai-vs-jasmine)

## Example: shorten

We are going to write and test a function that will shorten a string to a specified length:

```js
shorten('loremipsum', 6);
// should return 'lor...'
```

Possible approaches:

- write implementation first
- write tests first (test-driven development)

## Example: shorten

Implementation that should be tested:

```js
/**
 * shortens a given string to a specified length,
 * adding "..." at the end if it was shortened
 */
function shorten(text, maxlength) {
  if (text.length > maxlength) {
    return text.slice(0, maxlength - 3) + '...';
  }
  return text;
}
export default shorten;
```

## Example: shorten

simple tests:

```js
// shorten.test.js
import assert from 'assert';
import shorten from './shorten';

assert.equal(shorten('loremipsum', 4), 'l...');
assert.equal(shorten('loremipsum', 9), 'loremi...');
assert.equal(shorten('loremipsum', 10), 'loremipsum');
assert.equal(shorten('loremipsum', 11), 'loremipsum');
```

`assert.equal` throws an exception if the condition is not met
