### 🔹 O que é?

Middleware é uma camada intermediária entre a **action** e o **reducer** no Redux. Ele permite interceptar as actions antes que cheguem ao reducer e realizar operações como **logs, chamadas de API, debounce**, entre outras.

### 🔹 Como funciona no Redux?

Quando uma action é disparada (`dispatch(action)`), ela passa pelo **middleware** antes de chegar ao reducer. O middleware pode modificar a action, disparar novas actions ou até **bloquear** a ação antes que chegue ao reducer.

### 🔹 Exemplo de Middleware simples:

```js
const loggerMiddleware = store => next => action => {
  console.log('Dispatching:', action);
  let result = next(action); // Passa a action adiante
  console.log('Next State:', store.getState());
  return result;
};
```

🔹 Aqui, o middleware apenas **loga** as actions antes de passá-las para o próximo passo.

No caso do **Redux Saga**, ele é um middleware especializado em **ações assíncronas**, como chamadas de API.


---

## **3️⃣ Efeitos (`effects`)**:



---

### **🎯 Res