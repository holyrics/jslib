# Process
Objeto que representa um processo iniciado via JavaScript em execução no sistema operacional

Example
```javascript
var p = h.process('filename.exe', {
  cli: ['param 1', 'param 2'],
  on_message: function(msg) {
    h.log(msg.readString());
  },
  on_error: function(msg) {
    h.log("error: " + msg.readString());
  },
  on_finish: function(code) {
    //todo
  },
  timeout: 10000
});
p.send('example');
p.await();
```

---

- [Functions](#functions)
  - [send](#senddata)
  - [await](#await)
  - [awaitFor](#awaitfor)
  - [isOpen](#isopen)
  - [destroy](#destroy)
  - [put](#putkey-value)
  - [get](#getkey-default--null)
  - [onPropertyChange](#onpropertychangekey--null-onchange)


# Functions 
### send(data)
Enviar uma mensagem. May generate Exception.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Object_ | Valor que será enviado. Can be: `string`  `byte array`  `ByteBufferWriter` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[Process](https://github.com/holyrics/jslib/blob/main/doc/en/Process.md)_ | `this` |


**Example:**

```javascript
p.send('example');

var buf = h.createByteBuffer()
           .putString('message', 'Windows-1252');
p.send(buf);
```

---


### await()
### waitFinish()
Aguarda o término do processo



_Method does not return value_

---


### awaitFor()
Aguarda o término do processo e retorna o código de saída



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Can be null |


**Example:**

```javascript
var code = p.awaitFor();
h.log(code);
```

---


### isOpen()
Verifica se o processo está em execução



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### destroy()
Encerra o processo



**Response:**

| Type  | Description |
| :---: | ------------|
| _[Process](https://github.com/holyrics/jslib/blob/main/doc/en/Process.md)_ | `this` |


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
| _[Process](https://github.com/holyrics/jslib/blob/main/doc/en/Process.md)_ | `this` |


**Example:**

```javascript
var p = h.process('filename.exe', {
  on_message: function (buf) {
    var msg = buf.readString();
    if (msg.startsWith('volume:')) {
        p.put('volume', msg.substring(7).trim());
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
p.get('volume');
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
| _[Process](https://github.com/holyrics/jslib/blob/main/doc/en/Process.md)_ | `this` |


**Example:**

```javascript
p.onPropertyChange(function(evt) {
    //evt.source;  evt.key;  evt.value;
    if (evt.key == 'volume') {
        h.log('volume: ' + evt.value);
    }
});

p.onPropertyChange('volume', function(evt) {
    //evt.source;  evt.key;  evt.value;
    h.log('volume: ' + evt.value);
});
```

---
