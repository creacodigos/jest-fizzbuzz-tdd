# Prueba sencilla con test TDD
## javascript, jest y node

Carlos Azaustre resuelve una prueba técnica típica de entrevistas.

Se requiere que listes unos números y compruebes que:
- Los múltiplos de 3 devuelvan `fizz`.
- Los múltiplos de 5 devuelvan `buzz`.
- Los múltiplos de 3 y 5 devuelvan `fizzbuzz`.

### fizzbuzz.js
```js
function fizzbuzz(num) {

    const divisible = (divisor, num) => num % divisor === 0;

    if(num === 0)
    {
        return 0;
    }
    if(typeof num !== 'number')
    {
        return 'Error: the argument must be a number';
    }
    if(divisible(3,num) && divisible(5,num))
    {
        return 'fizzbuzz';
    }
    if(divisible(3,num))
    {
        return 'fizz';
    }
    if(divisible(5,num))
    {
        return 'buzz';
    }

    return num;
}

function print(num) {
    for(let i = 0; i < num; i++){
        console.log(`${i}; ${fizzbuzz(i)}`);
    }
}

print(16);

module.exports = fizzbuzz;
```

### fizzbuzz.tst.js
```js
const fizzbuzz = require('./fizzbuzz');

describe('fizzbuzz', () => {
    test('test', () => {
        expect(true).toBe(true);
    });    
    test('should print and error message if the argument is not a number', () => {
        const expected = 'Error: the argument must be a number';
        const result = fizzbuzz('16');
        expect(expected).toBe(result);
    })
    test('should print 1 if the recive 1', () => {
        const expected = 1;
        const result = fizzbuzz(1);
        expect(expected).toBe(result);
    })
    test('should print fizz if they receive 3', () => {
        const expected = 'fizz';
        const result = fizzbuzz(3);
        expect(expected).toBe(result);
    })
    test('should print fizz if they receive a multiple of 3', () => {
        const expected = 'fizz';
        const result = fizzbuzz(6);
        expect(expected).toBe(result);
    })
    test('should print buzz if they receive 5', () => {
        const expected = 'buzz';
        const result = fizzbuzz(5);
        expect(expected).toBe(result);
    })
    test('should print buzz if they receive a multiple of 5', () => {
        const expected = 'buzz';
        const result = fizzbuzz(10);
        expect(expected).toBe(result);
    })
    test('should print fizzbuzz if they receive a multiple of 3 and 5', () => {
        const expected = 'fizzbuzz';
        const result = fizzbuzz(15);
        expect(expected).toBe(result);
    })
});
```
Para correr los test en escucha:

`npm test:watch`

Parra correr el listado de números:

`node fizzbuzz`
```
node fizzbuzz      
0; 0
1; 1
2; 2
3; fizz
4; 4
5; buzz
6; fizz
7; 7
8; 8
9; fizz
10; buzz
11; 11
12; fizz
13; 13
14; 14
15; fizzbuzz
```