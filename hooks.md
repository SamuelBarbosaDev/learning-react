# React

## Hooks mais importantes do React

### 1. **useState**

O `useState` é utilizado para declarar variáveis de estado em componentes funcionais. Ele retorna um par: o estado atual e uma função que permite atualizá-lo.

**Uso:**

```javascript
import React, { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Você clicou {count} vezes</p>
            <button onClick={() => setCount(count + 1)}>
                Clique aqui
            </button>
        </div>
    );
}
```

### 2. **useEffect**

O `useEffect` permite executar efeitos colaterais em componentes funcionais, como buscar dados, atualizar o DOM, ou configurar um timer. Ele roda após a renderização.

**Uso:**

```javascript
import React, { useEffect, useState } from 'react';

function ExampleComponent() {
    const [data, setData] = useState(null);

    useEffect(() => {
        fetch('https://api.example.com/data')
            .then(response => response.json())
            .then(data => setData(data));
    }, []); // O array vazio faz com que o efeito rode apenas uma vez

    return (
        <div>
            {data ? <p>Data: {data}</p> : <p>Loading...</p>}
        </div>
    );
}
```

### 3. **useContext**

O `useContext` permite usar o contexto do React para compartilhar valores entre componentes sem precisar passar props manualmente em cada nível.

**Uso:**

```javascript
import React, { useContext } from 'react';

const MyContext = React.createContext();

function MyComponent() {
    const value = useContext(MyContext);

    return <div>{value}</div>;
}

function App() {
    return (
        <MyContext.Provider value="Hello, World!">
            <MyComponent />
        </MyContext.Provider>
    );
}
```

### 4. **useReducer**

O `useReducer` é semelhante ao `useState`, mas é mais adequado para gerenciamento de estados complexos onde há múltiplas sub-valores ou onde o próximo estado depende fortemente do anterior.

**Uso:**

```javascript
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
    switch (action.type) {
        case 'increment':
            return { count: state.count + 1 };
        case 'decrement':
            return { count: state.count - 1 };
        default:
            throw new Error();
    }
}

function Counter() {
    const [state, dispatch] = useReducer(reducer, initialState);

    return (
        <div>
            <p>Count: {state.count}</p>
            <button onClick={() => dispatch({ type: 'increment' })}>+</button>
            <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
        </div>
    );
}
```

### 5. **useRef**

O `useRef` retorna um objeto mutável que persiste por toda a vida do componente. Pode ser usado para acessar diretamente elementos DOM e armazenar valores mutáveis que não causam nova renderização.

**Uso:**

```javascript
import React, { useRef } from 'react';

function TextInputWithFocusButton() {
    const inputEl = useRef(null);

    const onButtonClick = () => {
        inputEl.current.focus();
    };

    return (
        <div>
            <input ref={inputEl} type="text" />
            <button onClick={onButtonClick}>Focus no input</button>
        </div>
    );
}
```

[React Hooks - Youtube](https://www.youtube.com/watch?v=MA3Ngo32qiI)
[React Hooks - Alura](https://www.alura.com.br/artigos/react-hooks)
[React Hooks - Documentação do React](https://pt-br.react.dev/reference/react/hooks)