# WebSocketClient

Exemplo
```javascript
function createWebSocket(receiver) {
  var client = h.ws(receiver);
  if (client != null) {
    return client;
  }
  return h.ws(receiver, {
    headers: {
      key1: 'value 1',
      key2: 'value 2'
    },
    on_open: function (evt) {
      /* evt.source; evt.http_status; evt.http_status_message; */
    },
    on_message: function (msg) {
      h.log(msg);
    },
    on_error: function (evt) {
      /* evt.source; evt.error; */
    },
    on_close: function (evt) {
      /* evt.source; evt.core; evt.reason; */
    },
    loop: function (evt) {
      //evt.source
    }
  });
}
```

---

- [Functions](#functions)
  - [send](#senddata)
  - [isOpen](#isopen)
  - [close](#close)
  - [put](#putkey-value)
  - [get](#getkey-default--null)
  - [onPropertyChange](#onpropertychangeonchange)


# Functions 
### send(data)
### sendMessage(data)
Enviar uma mensagem. Pode gerar Exception.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _String_ | String que será enviada |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[WebSocketClient](https://github.com/holyrics/jslib/blob/main/doc/pt/WebSocketClient.md)_ | `this` |


**Exemplo:**

```javascript
var client = createWebSocket('receiver_id');
client.send('message'); // utf-8

client.send(h.toJson({ message: 'test' }));
```

---


### isOpen()
Verifica se a conexão está ativa



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### close()
### disconnect()
Encerra a conexão



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[WebSocketClient](https://github.com/holyrics/jslib/blob/main/doc/pt/WebSocketClient.md)_ | `this` |


---


### put(key, value)
Armazena um valor no objeto

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ |  |
| `value` | _Object_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[WebSocketClient](https://github.com/holyrics/jslib/blob/main/doc/pt/WebSocketClient.md)_ | `this` |


**Exemplo:**

```javascript
var client = h.ws('receiver_id', {
  on_message: function (msg) {
    if (msg.startsWith('volume:')) {
        client.put('volume', msg.substring(7).trim());
    }
  }
});
```

---


### get(key, default = null)
Obtém um valor armazenado no objeto

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ |  |
| `default` | _Object (opcional)_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ |  |


**Exemplo:**

```javascript
var client = createWebSocket('receiver_id');
client.get('volume');
```

---


### onPropertyChange(onchange)
Executa uma ação sempre que uma propriedade for alterada

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `onchange` | _Function_ | `function(evt) { /* evt.source; evt.key; evt.value */ }` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[WebSocketClient](https://github.com/holyrics/jslib/blob/main/doc/pt/WebSocketClient.md)_ | `this` |


**Exemplo:**

```javascript
var client = createWebSocket('receiver_id');
client.onPropertyChange(function(evt) {
    //evt.source;  evt.key;  evt.value;
    if (evt.key == 'volume') {
        h.log('volume: ' + evt.value);
    }
});
```

---
