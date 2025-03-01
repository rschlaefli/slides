# Automatisiertes Testen in JavaScript

## Automatisiertes Testen

Code kann automatisch getestet werden, um sicherzustellen, dass er wie erwartet funktioniert

## Tools für das Testen

- _node_ wird als Runtime benötigt
- _assert_: einfache Assertions, in node beinhaltet
- _Jest_: test runner und assertion library
- _Mocha_ und _Chai_: test runner und assertion library

Popularität:

- [State of JS 2021: Umfrage zu Test-Tools](https://2021.stateofjs.com/en-US/libraries/testing/)
- [npmtrends](https://www.npmtrends.com/jest-vs-mocha-vs-chai-vs-jasmine)

## Einfaches Beispiel: shorten

Wir werden eine Funktion schreiben und testen, die einen String auf eine vorgegebene Länge kürzt:

```js
shorten('loremipsum', 6);
// should return 'lor...'
```

Mögliche Zugänge:

- mit Implementierung beginnen
- mit Tests beginnen (test-driven development)

## Einfaches Beispiel: shorten

Implementierung, die getestet werden soll:

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

## Beispiel: shorten

einfache Tests:

```js
// shorten.test.js
import assert from 'assert';
import shorten from './shorten';

assert.equal(shorten('loremipsum', 4), 'l...');
assert.equal(shorten('loremipsum', 9), 'loremi...');
assert.equal(shorten('loremipsum', 10), 'loremipsum');
assert.equal(shorten('loremipsum', 11), 'loremipsum');
```

`assert.equal` wirf eine Exception, wenn die Bedingung nicht erfüllt wird
