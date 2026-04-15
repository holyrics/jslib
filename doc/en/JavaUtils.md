# JavaUtils
Utility class for creating some native Java objects (for better manipulation than native JavaScript objects)

---

- [Functions](#functions)
  - [list](#list)
  - [list](#listargs)
  - [set](#set)
  - [set](#setargs)
  - [map](#map)
  - [lmap](#lmap)
  - [toList](#tolistarray)
  - [toSet](#tosetarray)
  - [toMap](#tomapobj)
  - [toLMap](#tolmapobj)
  - [optional](#optionalobj)


# Functions 
### list()




**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [ArrayList](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html) |


**Example:**

```javascript
var list = h.j.list();
```

---


### list(...args)




**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [ArrayList](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html) |


**Example:**

```javascript
var list = h.j.list('item 1', 'item 2', 'item 3');
```

---


### set()




**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) |


**Example:**

```javascript
var set = h.j.set();
```

---


### set(...args)




**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) |


**Example:**

```javascript
var set = h.j.set('item 1', 'item 2', 'item 3');
```

---


### map()




**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [HashMap](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) |


**Example:**

```javascript
var map = h.j.map();
```

---


### lmap()




**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [LinkedHashMap](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html) |


**Example:**

```javascript
var lmap = h.j.lmap();
```

---


### toList(array)
Converts a native JavaScript array into a Java ArrayList



**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [ArrayList](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html) |


**Example:**

```javascript
var arr = [1, 2, 3];
var list = h.j.toList(arr);
```

---


### toSet(array)
Converts a native JavaScript array into a Java HashSet



**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) |


**Example:**

```javascript
var arr = [1, 2, 3];
var set = h.j.toSet(arr);
```

---


### toMap(obj)
Converts a native JavaScript object into a Java HashMap



**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [HashMap](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) |


**Example:**

```javascript
var m = {
    a: 1,
    b: 2,
    c: 3
};
var map = h.j.toMap(m);
```

---


### toLMap(obj)
Converts a native JavaScript object into a Java LinkedHashMap



**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [LinkedHashMap](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html) |


**Example:**

```javascript
var m = {
    a: 1,
    b: 2,
    c: 3
};
var lmap = h.j.toLMap(m);
```

---


### optional(obj)
### opt(obj)
Optional Java



**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [Optional](https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html) |


**Example:**

```javascript
var opt = h.j.optional(obj);
```

---
