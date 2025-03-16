# Process
Object that represents a process started via JavaScript running on the operating system

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
  - [awaitForOrThrow](#awaitfororthrow)
  - [isOpen](#isopen)
  - [destroy](#destroy)
  - [put](#putkey-value)
  - [get](#getkey-default--null)
  - [onPropertyChange](#onpropertychangekey--null-onchange)


# Functions 
### send(data)
Send a message. May generate Exception.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Object_ | Value that will be sent. Can be: `string`  `byte array`  `ByteBufferWriter` |


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
Wait for the end of the process



_Method does not return value_

---


### awaitFor()
Waits for the process to finish and returns the exit code



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


### awaitForOrThrow()
- v2.25.0

The same as `awaitFor()`, but throws an exception instead of returning `null` when there is an execution error



**Response:**

| Type  |
| :---: |
| _Number_ | 


**Example:**

```javascript
var r = h.awaitForOrThrow();
//the same as
var code = p.awaitFor();
h.log(code);
//but it raises an exception if code === null
```

---


### isOpen()
Check if the process is running



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### destroy()
Ends the process



**Response:**

| Type  | Description |
| :---: | ------------|
| _[Process](https://github.com/holyrics/jslib/blob/main/doc/en/Process.md)_ | `this` |


---


### put(key, value)
Stores a value in the object

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
Gets a value stored in the object

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
Executes an action whenever a property is changed

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String (optional)_ | Executes the action only for a specific key `v2.24.0+` |
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
