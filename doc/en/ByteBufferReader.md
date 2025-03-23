# ByteBufferReader

Example
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


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `length` | _Number_ |  |


**Response:**

| Type  |
| :---: |
| _Array&lt;Byte&gt;_ | 


**Example:**

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




**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### readByte()
### read()




**Response:**

| Type  |
| :---: |
| _Byte_ | 


---


### readShort()
2 bytes



**Response:**

| Type  |
| :---: |
| _Number_ | 


---


### readInt()
4 bytes



**Response:**

| Type  |
| :---: |
| _Number_ | 


---


### readLong()
8 bytes<br>max safe long: 9007199254740991



**Response:**

| Type  |
| :---: |
| _Number_ | 


---


### readFloat()
4 bytes



**Response:**

| Type  |
| :---: |
| _Number_ | 


---


### readDouble()
8 bytes



**Response:**

| Type  |
| :---: |
| _Number_ | 


---


### readString(length = -1, charset = 'utf-8')


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `length` | _Number (optional)_ | If `length < 0` all **remaining** bytes will be read `Default: -1` |
| `charset` | _String (optional)_ |  `Default: utf-8` |


**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

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
Number of bytes remaining to be read



**Response:**

| Type  |
| :---: |
| _Number_ | 


---


### skip(length)
Ignore a number of bytes to be read

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `length` | _Number_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferReader](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferReader.md)_ | `this` |


**Example:**

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
