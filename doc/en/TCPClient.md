# TCPClient

Example
```javascript
function createTCP(receiver) {
  var client = h.tcp(receiver);
  if (client != null) {
    return client;
  }
  return h.tcp(receiver, {
    on_message: function (/* ByteBuffer */ data) {
      // data.toString();
      // data.toHex();
      // data.toBase64();
      // data.toBytes();
    },
    on_close: function (evt) {
      /* evt.source; */
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
| `data` | _Object_ | Valor que será enviado |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[TCPClient](https://github.com/holyrics/jslib/blob/main/doc/en/TCPClient.md)_ | `this` |


**Example:**

```javascript
var client = createTCP('receiver_id');
client.send('message');

var buf = h.createByteBuffer()
           .putString('message', 'ascii');
client.send(buf);
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
| _[TCPClient](https://github.com/holyrics/jslib/blob/main/doc/en/TCPClient.md)_ | `this` |


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
| _[TCPClient](https://github.com/holyrics/jslib/blob/main/doc/en/TCPClient.md)_ | `this` |


**Example:**

```javascript
var client = h.tcp('receiver_id', {
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
var client = createTCP('receiver_id');
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
| _[TCPClient](https://github.com/holyrics/jslib/blob/main/doc/en/TCPClient.md)_ | `this` |


**Example:**

```javascript
var client = createTCP('receiver_id');
client.onPropertyChange(function(evt) {
    //evt.source;  evt.key;  evt.value;
    if (evt.key == 'volume') {
        h.log('volume: ' + evt.value);
    }
});

var client = createTCP('receiver_id');
client.onPropertyChange('volume', function(evt) {
    //evt.source;  evt.key;  evt.value;
    h.log('volume: ' + evt.value);
});
```

---
