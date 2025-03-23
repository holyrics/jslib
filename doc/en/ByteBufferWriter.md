# ByteBufferWriter

Example
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


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Array&lt;Byte&gt;_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


---


### putBoolean(value)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Boolean_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


---


### putByte(value)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Byte_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


---


### putShort(value)
2 bytes

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Number_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


---


### putInt(value)
4 bytes

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Number_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


---


### putLong(value)
8 bytes<br>max safe long: 9007199254740991

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Number_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


---


### putFloat(value)
4 bytes

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Number_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


---


### putDouble(value)
8 bytes

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Number_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


---


### putString(value, charset = 'utf-8')


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ |  |
| `charset` | _String (optional)_ |  `Default: utf-8` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


**Example:**

```javascript
var buf = h.createByteBuffer();

buf.putString('example'); //utf-8

buf.putString('example', 'ascii');
```

---


### putBytesAndFill(value, length, fill = 0)
Adds a value and fills the remaining space with the value of `fill`.<br>For example, if `value.length == 14` and `length == 16`, 2 bytes with the value `fill` will be added after `value` is added.<br>If `length` is negative, the bytes will be added before `value`.<br>the `length` value **does not limit** the number of bytes added if `value.length > length`, in this case all bytes in `value` will be added and no extra byte will be added.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Array&lt;Byte&gt;_ |  |
| `length` | _Number_ |  |
| `fill` | _Number (optional)_ |  `Default: 0` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


---


### putStringAndFill(value, length, fill = 0, charset = 'utf-8')
Adds a value and fills the remaining space with the value of `fill`.<br>Follows the same rule as `putBytesAndFill(...)`<br>Note: `length` refers to the bytes generated by the string and not to the number of characters.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ |  |
| `length` | _Number_ |  |
| `fill` | _Number (optional)_ |  `Default: 0` |
| `charset` | _String (optional)_ |  `Default: utf-8` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


**Example:**

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
Adds `value` the number of times specified in `repeat`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Byte_ |  |
| `repeat` | _Number_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


**Example:**

```javascript
var buf = h.createByteBuffer();
buf.fill(32, 8);
```

---


### fillBytes(value, repeat)
Adds `value` the number of times specified in `repeat`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Array&lt;Byte&gt;_ |  |
| `repeat` | _Number_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | `this` |


---


### size()
Current amount of bytes added



**Response:**

| Type  |
| :---: |
| _Number_ | 


**Example:**

```javascript
var buf = h.createByteBuffer()
           .putString('test')
           .fill(32, 8);
var r = h.size(); // 12
```

---


### toString(charset = 'utf-8')
Converts the added bytes into String

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `charset` | _String (optional)_ |  `Default: utf-8` |


**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

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
Converts the added bytes to hexadecimal



**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

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
Converts the added bytes to base64



**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

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
Returns the added bytes



**Response:**

| Type  |
| :---: |
| _Array&lt;Byte&gt;_ | 


**Example:**

```javascript
var buf = h.createByteBuffer();
buf.putString('test');
buf.fill(32, 4);
buf.putString('test');

// [116,101,115,116,32,32,32,32,116,101,115,116]
h.log(buf.toBytes());
```

---
