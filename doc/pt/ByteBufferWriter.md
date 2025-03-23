# ByteBufferWriter

Exemplo
```javascript
var buf = h.createByteBuffer();

// [1]
buf.putBoolean(true);

// [48]
buf.putByte(48);

// [0, 0, 32, 4]
buf.putInt(8196);

// [64, 76, -52, -51]
buf.putFloat(3.2);

// [0, 0, 1, 32, -82, 102, -94, -22]
buf.putLong(1239876543210);

// [64, 9, -103, -103, -103, -103, -103, -102]
buf.putDouble(3.2);

// [116, 101, 120, 116]
buf.putString("text");

// [116, 101, 120, 116, 0, 0, 0, 0]
buf.putStringAndFill("text", 8);

// [116, 101, 120, 116, 32, 32, 32, 32]
buf.putStringAndFill("text", 8, 32);

// [0, 0, 0, 0]
buf.put0(4);

// [48, 48, 48, 48, 48]
buf.fill(48, 5);

var hex = buf.toHex();
// 013000002004404ccccd00000120ae66a2ea400999999999999a7465787474657874000000007465787420202020000000003030303030

var base64 = buf.toBase64();
// 013000002004404ccccd00000120ae66a2ea400999999999999a7465787474657874000000007465787420202020000000003030303030

var bytes = buf.toBytes();
/*
[
    1,
   48,
    0,   0,   32,    4,
   64,  76,  -52,  -51,
    0,   0,    1,   32,  -82,  102,  -94,  -22,
   64,   9, -103, -103, -103, -103, -103, -102,
  116, 101,  120,  116,
  116, 101,  120,  116,    0,    0,    0,    0,
  116, 101,  120,  116,   32,   32,   32,   32,
    0,   0,    0,    0,
   48,  48,   48,   48,   48
  ]
*/

```

---

- [Functions](#functions)
  - [putBytes](#putbytesvalue)
  - [putBoolean](#putbooleanvalue)
  - [putByte](#putbytevalue)
  - [putShort](#putshortvalue)
  - [putInt](#putintvalue)
  - [putLong](#putlongvalue)
  - [putFloat](#putfloatvalue)
  - [putDouble](#putdoublevalue)
  - [putString](#putstringvalue-charset--utf-8)
  - [putBytesAndFill](#putbytesandfillvalue-length-fill--0)
  - [putStringAndFill](#putstringandfillvalue-length-fill--0-charset--utf-8)
  - [fill](#fillvalue-repeat)
  - [fillBytes](#fillbytesvalue-repeat)
  - [size](#size)
  - [toString](#tostringcharset--utf-8)
  - [toHex](#tohex)
  - [toBase64](#tobase64)
  - [toBytes](#tobytes)


# Functions 
### putBytes(value)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Array&lt;Byte&gt;_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


---


### putBoolean(value)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Boolean_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


---


### putByte(value)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Byte_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


---


### putShort(value)
2 bytes

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Number_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


---


### putInt(value)
4 bytes

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Number_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


---


### putLong(value)
8 bytes<br>max safe long: 9007199254740991

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Number_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


---


### putFloat(value)
4 bytes

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Number_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


---


### putDouble(value)
8 bytes

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Number_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


---


### putString(value, charset = 'utf-8')


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ |  |
| `charset` | _String (opcional)_ |  `Padrão: utf-8` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


**Exemplo:**

```javascript
var buf = h.createByteBuffer();

buf.putString('example'); //utf-8

buf.putString('example', 'ascii');
```

---


### putBytesAndFill(value, length, fill = 0)
Adiciona um valor e preenche o restante do espaço com o valor de `fill`.<br>Por exemplo, se `value.length == 14` e `length == 16`, serão adicionados 2 bytes com valor `fill` após `value` ser adicionado.<br>Se `length` for negativo, os bytes serão adicionados antes de `value`.<br>o valor `length` **não limita** a quantidade de bytes adicionados se `value.length > length`, nesse caso todos os bytes em `value` serão adicionados e nenhum byte extra será adicionado.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Array&lt;Byte&gt;_ |  |
| `length` | _Number_ |  |
| `fill` | _Number (opcional)_ |  `Padrão: 0` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


---


### putStringAndFill(value, length, fill = 0, charset = 'utf-8')
Adiciona um valor e preenche o restante do espaço com o valor de `fill`.<br>Segue a mesma regra de `putBytesAndFill(...)`<br>Observação: `length` é referente aos bytes gerados pela string e não pela quantidade de caracteres.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ |  |
| `length` | _Number_ |  |
| `fill` | _Number (opcional)_ |  `Padrão: 0` |
| `charset` | _String (opcional)_ |  `Padrão: utf-8` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


**Exemplo:**

```javascript
var buf = h.createByteBuffer();

// [116, 101, 115, 116, 0, 0, 0, 0]
buf.putStringAndFill('test', 8);

// [116, 101, 115, 116, 32, 32, 32, 32]
buf.putStringAndFill('test', 8, 32);

// [0, 0, 0, 0, 116, 101, 115, 116]
buf.putStringAndFill('test', -8);

// [116, 101, 115, 116]
buf.putStringAndFill('test', 2);
```

---


### fill(value, repeat)
Adiciona `value` na quantidade de vezes informada em `repeat`

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Byte_ |  |
| `repeat` | _Number_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


**Exemplo:**

```javascript
var buf = h.createByteBuffer();
buf.fill(32, 8);
```

---


### fillBytes(value, repeat)
Adiciona `value` na quantidade de vezes informada em `repeat`

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Array&lt;Byte&gt;_ |  |
| `repeat` | _Number_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ | `this` |


---


### size()
Quantidade atual de bytes adicionados



**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


**Exemplo:**

```javascript
var buf = h.createByteBuffer()
           .putString('test')
           .fill(32, 8);
var r = h.size(); // 12
```

---


### toString(charset = 'utf-8')
Converte os bytes adicionados em String

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `charset` | _String (opcional)_ |  `Padrão: utf-8` |


**Resposta:**

| Tipo  |
| :---: |
| _String_ | 


**Exemplo:**

```javascript
var buf = h.createByteBuffer();
buf.putString('test');
buf.fill(32, 4);
buf.putString('test');

// test    test
h.log(buf.toString());
```

---


### toHex()
Converte os bytes adicionados em hexadecimal



**Resposta:**

| Tipo  |
| :---: |
| _String_ | 


**Exemplo:**

```javascript
var buf = h.createByteBuffer();
buf.putString('test');
buf.fill(32, 4);
buf.putString('test');

// 746573742020202074657374
h.log(buf.toHex());
```

---


### toBase64()
Converte os bytes adicionados em base64



**Resposta:**

| Tipo  |
| :---: |
| _String_ | 


**Exemplo:**

```javascript
var buf = h.createByteBuffer();
buf.putString('test');
buf.fill(32, 4);
buf.putString('test');

// dGVzdCAgICB0ZXN0
h.log(buf.toBase64());
```

---


### toBytes()
Retorna os bytes adicionados



**Resposta:**

| Tipo  |
| :---: |
| _Array&lt;Byte&gt;_ | 


**Exemplo:**

```javascript
var buf = h.createByteBuffer();
buf.putString('test');
buf.fill(32, 4);
buf.putString('test');

// [116,101,115,116,32,32,32,32,116,101,115,116]
h.log(buf.toBytes());
```

---
