# Optional

Example
```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var opt = h.stream(arr)
           .max((a, b) => a.compareToIgnoreCase(b));
opt.ifPresent(o => {
  h.log(o);
});
// output
// z
```

---

- [Functions](#functions)
  - [get](#get)
  - [orElse](#orelseother)
  - [orElseGet](#orelsegetother)
  - [orElseThrow](#orelsethrowexceptionsupplier)
  - [filter](#filterpredicate)
  - [ifPresent](#ifpresentconsumer)
  - [isPresent](#ispresent)
  - [map](#mapmapper)


# Functions 
### get()




**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | throws NoSuchElementException if is null |


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var opt = h.stream(arr).max((a, b) => a.compareTo(b));
var r = opt.get();
// r: z

var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var opt = h.stream(arr)
        .filter(o => o.length() > 1)
        .max((a, b) => a.compareTo(b));

var r = opt.get(); //throws exception
```

---


### orElse(other)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `other` | _Object_ |  |


**Response:**

| Type  |
| :---: |
| _Object_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var opt = h.stream(arr)
        .filter(o => o.length() > 1)
        .max((a, b) => a.compareTo(b));

var r = opt.orElse("a");
// r: a
```

---


### orElseGet(other)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `other` | _Function_ | Supplier<br>`function() { return value; }` |


**Response:**

| Type  |
| :---: |
| _Object_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var opt = h.stream(arr)
        .filter(o => o.length() > 1)
        .max((a, b) => a.compareTo(b));

var r = opt.orElseGet(function() { return 'a'; });
// r: a
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
| _Object_ | throws NoSuchElementException if is null |


**Example:**

```javascript
var r = opt.orElseThrow(function() { throw 'error'; });
```

---


### filter(predicate)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `predicate` | _Function_ | Predicate<br>`function(o) { return boolean; }` |


**Response:**

| Type  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/en/Optional.md)_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
h.stream(arr)
 .max((a, b) => a.compareTo(b))
 .filter(s => s.length() == 1)
 .ifPresent(s => h.log(s)); //z
```

---


### ifPresent(consumer)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `consumer` | _Function_ | Consumer<br>`function(a) { ... }` |


_Method does not return value_

**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
h.stream(arr)
 .max((a, b) => a.compareTo(b))
 .ifPresent(s => h.log(s)); //z
```

---


### isPresent()




**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var opt = h.stream(arr).max((a, b) => a.compareTo(b));
if (opt.isPresent()) {
    var r = opt.get(); // z
}
```

---


### map(mapper)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `mapper` | _Function_ | Function<br>`function(a) { return b; }` |


**Response:**

| Type  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/en/Optional.md)_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
h.stream(arr)
 .max((a, b) => a.compareTo(b))
 .map(s => "<" + s + ">")
 .ifPresent(s => h.log(s)); // <z>
```

---
