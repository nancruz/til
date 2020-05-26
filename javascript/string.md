# String

## How to

### Split a camelCase string into an array

```javascript
function getCamelCaseArray(camel) {
    const reg = /([a-z0-9])([A-Z])/g;

    return camel.replace(reg, '$1 $2').split(' ');
}

const camelArray = getCamelCaseArray('nunoCruz');
console.log(camelArray);
// ['nuno', 'Cruz']

```

### Capitalize word
```javascript
function capitalizeWord(word) {
    if (typeof word !=== 'string') {
        return '';
    }

    return word.charAt(0).toUpperCase() + word.splice(1);
}

const capitalizedWord = capitalizeWord('nuno');
console.log(capitalizedWord);
// 'Nuno'

```
