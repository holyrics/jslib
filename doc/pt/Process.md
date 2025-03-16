# Process
Objeto que representa um processo iniciado via JavaScript em execução no sistema operacional

Exemplo
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
  - [awaitForOrThrow](#awaitfororthrow)
  - [isOpen](#isopen)
  - [destroy](#destroy)
  - [put](#putkey-value)
  - [get](#getkey-default--null)
  - [onPropertyChange](#onpropertychangekey--null-onchange)


# Functions 
### send(data)
Enviar uma mensagem. Pode gerar Exception.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Object_ | Valor que será enviado. Pode ser: `string`  `byte array`  `ByteBufferWriter` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[Process](https://github.com/holyrics/jslib/blob/main/doc/pt/Process.md)_ | `this` |


**Exemplo:**

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



_Método sem retorno_

---


### awaitFor()
Aguarda o término do processo e retorna o código de saída



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Pode ser null |


**Exemplo:**

```javascript
var code = p.awaitFor();
h.log(code);
```

---


### awaitForOrThrow()
- v2.25.0

O mesmo que `awaitFor()`, porém gera exception em vez de retornar `null` quando houver erro de execução



**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


**Exemplo:**

```javascript
var r = h.awaitForOrThrow();
//o mesmo que
var code = p.awaitFor();
h.log(code);
//porém gera exception se code === null
```

---


### isOpen()
Verifica se o processo está em execução



**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


---


### destroy()
Encerra o processo



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[Process](https://github.com/holyrics/jslib/blob/main/doc/pt/Process.md)_ | `this` |


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
| _[Process](https://github.com/holyrics/jslib/blob/main/doc/pt/Process.md)_ | `this` |


**Exemplo:**

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

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ |  |
| `default` | _Object (opcional)_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _Object_ | 


**Exemplo:**

```javascript
p.get('volume');
```

---


### onPropertyChange(key = null, onchange)
Executa uma ação sempre que uma propriedade for alterada

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String (opcional)_ | Executa a ação somente para uma chave específica `v2.24.0+` |
| `onchange` | _Function_ | `function(evt) { /* evt.source; evt.key; evt.value */ }` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[Process](https://github.com/holyrics/jslib/blob/main/doc/pt/Process.md)_ | `this` |


**Exemplo:**

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
