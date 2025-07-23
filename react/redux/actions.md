São objetos que descrevem "o que aconteceu" na aplicação. Cada ação possui um tipo (uma string que descreve a ação) e, opcionalmente, alguns dados associados (payload).

Exemplos de actions:

```js
const increment = { type: 'INCREMENT' }; 
const setUser = { type: 'SET_USER', payload: { name: 'Miguel' } };
```