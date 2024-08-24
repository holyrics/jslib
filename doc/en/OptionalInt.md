# OptionalInt

Example
```javascript
var arr = [3, -1, 8, 4, 2];
var opt = h.intStreamOf(arr).max();
opt.ifPresent(o => {
  h.log(o);
});
// output
// 8
```

---

- [Functions](#functions)
  - [getAsInt](#getasint)
  - [orElse](#orelseother)
  - [orElseGet](#orelsegetother)
  - [orElseThrow](#orelsethrowexceptionsupplier)
  - [ifPresent](#ifpresentconsumer)
  - [isPresent](#ispresent)


# Functions 
### getAsInt()




**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | throws NoSuchElementException if is null |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .max()
         .getAsInt();
h.log(r);
// r: 9
```

---


### orElse(other)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `other` | _Number_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .max()
         .orElse(0);
h.log(r);
// r: 9
```

---


### orElseGet(other)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `other` | _Function_ | IntSupplier<br>`function() { return int; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .max()
         .orElseGet(function() { return 0; });
h.log(r);
// r: 9
```

---


### orElseThrow(exceptionSupplier)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `exceptionSupplier` | _Function_ | Supplier<br>`function() { return value; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | throws NoSuchElementException if is null |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .max()
         .orElseThrow(function() { throw 'error'; });
h.log(r);
// r: 9
```

---


### ifPresent(consumer)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `consumer` | _Function_ | IntConsumer<br>`function(/*int*/ b) { ... }` |


_Method does not return value_

**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
h.intStreamOf(arr)
 .max()
 .ifPresent(n => h.log(n)); // 9
```

---


### isPresent()




**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var opt = h.intStreamOf(arr).max();
if (opt.isPresent()) {
    h.log(opt.getAsInt()); // 9
}
```

---
