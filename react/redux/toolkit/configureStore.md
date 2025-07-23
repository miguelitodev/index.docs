Facilita a configuração da store

```js
import { configureStore } from '@reduxjs/toolkit';

const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});
```

A chave `reducer` dentro da configuração é onde definimos como o estado global da aplicação será dividido. Ele mapeia as partes do estado para as slices que temos na nossa aplicação.

