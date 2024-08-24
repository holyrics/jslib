# OptionalDouble

Example
```javascript
var arr = [3, -1, 8, 4, 2];
var opt = h.intStreamOf(arr).average();
opt.ifPresent(o => {
  h.log(o);
});
// output
// 3.2
```

---

- [Functions](#functions)
  - [getAsDouble](#getasdouble)
  - [orElse](#orelseother)
  - [orElseGet](#orelsegetother)
  - [orElseThrow](#orelsethrowexceptionsupplier)
  - [ifPresent](#ifpresentconsumer)
  - [isPresent](#ispresent)


# Functions 
### getAsDouble()




**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | throws NoSuchElementException if is null |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .average()
         .getAsDouble();
h.log(r);
// r: 5
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
         .average()
         .orElse(0);
h.log(r);
// r: 5
```

---


### orElseGet(other)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `other` | _Function_ | DoubleSupplier<br>`function() { return double; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .average()
         .orElseGet(function() { return 0; });
h.log(r);
// r: 5
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
         .average()
         .orElseThrow(function() { throw 'error'; });
h.log(r);
// r: 5
```

---


### ifPresent(consumer)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `consumer` | _Function_ | DoubleConsumer<br>`function(/*double*/ b) { ... }` |


_Method does not return value_

**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
h.intStreamOf(arr)
 .average()
 .ifPresent(n => h.log(n)); // 5
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
var opt = h.intStreamOf(arr).average();
if (opt.isPresent()) {
    h.log(opt.getAsDouble()); // 5
}
```

---
