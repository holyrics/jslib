# WebSocketClient

Example
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
  - [onPropertyChange](#onpropertychangekey--null-onchange)


# Functions 
### send(data)
### sendMessage(data)
Enviar uma mensagem. May generate Exception.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _String_ | String que será enviada |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[WebSocketClient](https://github.com/holyrics/jslib/blob/main/doc/en/WebSocketClient.md)_ | `this` |


**Example:**

```javascript
var client = createWebSocket('receiver_id');
client.send('message'); // utf-8

client.send(h.toJson({ message: 'test' }));
```

---


### isOpen()
Verifica se a conexão está ativa



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### close()
### disconnect()
Encerra a conexão



**Response:**

| Type  | Description |
| :---: | ------------|
| _[WebSocketClient](https://github.com/holyrics/jslib/blob/main/doc/en/WebSocketClient.md)_ | `this` |


---


### put(key, value)
Armazena um valor no objeto

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ |  |
| `value` | _Object_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[WebSocketClient](https://github.com/holyrics/jslib/blob/main/doc/en/WebSocketClient.md)_ | `this` |


**Example:**

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

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ |  |
| `default` | _Object (optional)_ |  |


**Response:**

| Type  |
| :---: |
| _Object_ | 


**Example:**

```javascript
var client = createWebSocket('receiver_id');
client.get('volume');
```

---


### onPropertyChange(key = null, onchange)
Executa uma ação sempre que uma propriedade for alterada

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String (optional)_ | Executa a ação somente para uma chave específica `v2.24.0+` |
| `onchange` | _Function_ | `function(evt) { /* evt.source; evt.key; evt.value */ }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[WebSocketClient](https://github.com/holyrics/jslib/blob/main/doc/en/WebSocketClient.md)_ | `this` |


**Example:**

```javascript
var client = createWebSocket('receiver_id');
client.onPropertyChange(function(evt) {
    //evt.source;  evt.key;  evt.value;
    if (evt.key == 'volume') {
        h.log('volume: ' + evt.value);
    }
});

var client = createWebSocket('receiver_id');
client.onPropertyChange('volume', function(evt) {
    //evt.source;  evt.key;  evt.value;
    h.log('volume: ' + evt.value);
});
```

---
