# JS Sync & Async

Este texto foi produzido pelo [ChatGPT](https://chat.openai.com/) com co-autoria de [Walmyr Lima e Silva Filho](https://github.com/wlsf82).

---

## Diferenças entre código síncrono e assíncrono em JavaScript

O JavaScript é uma linguagem de programação que permite escrever código tanto síncrono quanto assíncrono. O código síncrono é o código que é executado de forma linear, de cima para baixo, enquanto o código assíncrono é o código que é executado de forma não linear. O código assíncrono é frequentemente usado para realizar operações que levam um longo tempo para serem concluídas, como fazer uma solicitação de rede ou ler um arquivo do disco. Existem várias maneiras de escrever código assíncrono no JavaScript, como usando callbacks e promises. A recente adição de async/await ao JavaScript torna mais fácil escrever código assíncrono que parece e se comporta como código síncrono. Neste texto, vamos explorar as diferenças entre o código síncrono e o código assíncrono no JavaScript e como usar async/await para escrever código assíncrono de maneira mais fácil e legível.

### Código síncrono

No JavaScript, o código síncrono é o código que é executado de forma linear, de cima para baixo. Isso significa que cada linha de código será executada uma de cada vez, na ordem em que aparece. Por exemplo:

```js
const x = 1;
const y = 2;
const z = x + y;
console.log(z); // 3

```

Neste exemplo, as três linhas de código são executadas em ordem, e o valor de `z` é calculado antes de ser escrito no console.

### Código assíncrono

Por outro lado, o código assíncrono é o código que é executado de forma não linear. Isso significa que a ordem em que o código é executado pode não ser a mesma ordem em que ele aparece. O código assíncrono é frequentemente usado para realizar operações que levam muito tempo para serem concluídas, como fazer uma solicitação de rede ou ler um arquivo do disco.

#### _Callbacks_

Uma maneira de escrever código assíncrono no JavaScript é com o uso de callbacks. Por exemplo:

```js
function getData(callback) {
  // simula uma operação demorada
  setTimeout(() => {
    const data = "algum dado";
    callback(data);
  }, 1000);
}

getData((data) => {
  console.log(data); // "algum dado"
});

```

Neste exemplo, a função `getData` simula uma operação demorada usando a função `setTimeout` para atrasar a execução do `callback` por um segundo. Quando o `callback` é finalmente executado, ele escreve o valor de `data` no console.

#### _Promises_ (Promessas)

Outra maneira de escrever código assíncrono no JavaScript é com o uso de promises. Promises são objetos que representam o resultado eventual de uma operação assíncrona. Por exemplo:

```js
function getData() {
  return new Promise((resolve, reject) => {
    // simula uma operação demorada
    setTimeout(() => {
      const data = "algum dado";
      resolve(data);
    }, 1000);
  });
}

getData()
  .then((data) => {
    console.log(data); // "algum dado"
  })
  .catch((error) => {
    console.error(error);
  });

```

Neste exemplo, a função `getData` retorna uma promise que é resolvida com o valor de `data` após um segundo. O método `then` é usado para especificar um callback que é executado quando a promise é resolvida, e o método `catch` é usado para especificar um callback que é executado se a promise for rejeitada.

#### Async/await

Async/await é uma adição mais recente ao JavaScript que torna mais fácil escrever código assíncrono que parece e se comporta como código síncrono. Com **async/await**, é possível usar a palavra-chave `async` para definir uma função assíncrona e a palavra-chave `await` para esperar por uma promise ser resolvida. Por exemplo:

```js
async function getData() {
  // simula uma operação demorada
  const data = await new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("algum dado");
    }, 1000);
  });
  return data;
}

(async () => {
  const data = await getData();
  console.log(data); // "algum dado"
})();

```

Neste exemplo, a função `getData` é definida como uma função assíncrona (`async`) e a palavra-chave `await` é usada para esperar pela promise retornada pelo construtor `new Promise` ser resolvida. Quando a promise é resolvida, o valor de `data` é retornado pela função `getData`.

Em resumo, o JavaScript permite escrever código tanto síncrono quanto assíncrono. O código síncrono é executado de forma linear, enquanto o código assíncrono é executado de forma não linear e pode ser usado para realizar operações demoradas. Existem várias maneiras de escrever código assíncrono no JavaScript, como usando callbacks e promises, mas a adição de async/await torna essa tarefa mais fácil e legível. Ao usar async/await, é possível escrever código assíncrono que se parece e se comporta como código síncrono, o que pode tornar o código mais fácil de escrever, ler e entender.
