# ByteBufferReader

Exemplo
```javascript
var bytes = h.base64Decode('ATAAACAEQEzMzQAAASCuZqLqQAmZmZmZmZp0ZXh0dGV4dAAAAAB0ZXh0ICAgIAAAAAAwMDAwMA==');
var buf = h.createByteBufferToRead(bytes);

buf.readBoolean(); // true

buf.readByte(); // 48

buf.readInt(); // 8196

buf.readFloat(); // 3.2

buf.readLong(); // 1239876543210

buf.readDouble(); // 3.2

buf.readString(4); // "text"

buf.readString(8); // "text"

buf.readString(8); // "text    "

buf.available(); // 9

buf.readBytes(4); // [0, 0, 0, 0]

buf.readBytes(5); // [48, 48, 48, 48, 48]

```

---

- [Functions](#functions)
  - [readBytes](#readbyteslength)
  - [readBoolean](#readboolean)
  - [readByte](#readbyte)
  - [readShort](#readshort)
  - [readInt](#readint)
  - [readLong](#readlong)
  - [readFloat](#readfloat)
  - [readDouble](#readdouble)
  - [readString](#readstringlength---1-charset--utf-8)
  - [available](#available)
  - [skip](#skiplength)


# Functions 
### readBytes(length)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `length` | _Number_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _Array&lt;Byte&gt;_ | 


**Exemplo:**

```javascript
var buf = h.createByteBuffer();
buf.putString('test')
   .fill(32, 4)
   .putString('test');

var reader = h.createByteBufferToRead(buf.toBytes());
var r = reader.readBytes(3);
h.log(r); // [116, 101, 115]
```

---


### readBoolean()




**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


---


### readByte()
### read()




**Resposta:**

| Tipo  |
| :---: |
| _Byte_ | 


---


### readShort()
2 bytes



**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


---


### readInt()
4 bytes



**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


---


### readLong()
8 bytes<br>max safe long: 9007199254740991



**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


---


### readFloat()
4 bytes



**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


---


### readDouble()
8 bytes



**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


---


### readString(length = -1, charset = 'utf-8')


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `length` | _Number (opcional)_ | Se `length < 0` todos os bytes **restantes** serão lidos `Padrão: -1` |
| `charset` | _String (opcional)_ |  `Padrão: utf-8` |


**Resposta:**

| Tipo  |
| :---: |
| _String_ | 


**Exemplo:**

```javascript
var buf = h.createByteBuffer();
buf.putString('test')
   .fill(32, 4)
   .putString('test');

var reader = h.createByteBufferToRead(buf.toBytes());
var r = reader.readString(4);
h.log(r); // test

reader.skip(4);

var r = reader.readString();
h.log(r); // test
```

---


### available()
Quantidade de bytes restantes a serem lidos



**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


---


### skip(length)
Ignora uma quantidade de bytes a serem lidos

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `length` | _Number_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferReader](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferReader.md)_ | `this` |


**Exemplo:**

```javascript
var bytes = h.createByteBuffer()
             .putString('test')
             .toBytes();
var reader = h.createByteBufferToRead(bytes);

reader.skip(2);

var r = reader.readString();
h.log(r); // st
```

---
