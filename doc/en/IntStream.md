# IntStream
Classe para facilitar a manipulação de listas de números

Example
```javascript
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
var r = h.intStreamOf(arr)
         //1, 3, 7, 9
         .filter(n => n != 5 && n % 2 == 1)
         .sum();
h.log(r);
// output
// 20
```

---

- [Functions](#functions)
  - [filter](#filterpredicate)
  - [map](#mapmapper)
  - [mapToObj](#maptoobjmapper)
  - [sorted](#sorted)
  - [forEach](#foreachaction)
  - [toArray](#toarray)
  - [distinct](#distinct)
  - [limit](#limitmaxsize)
  - [max](#max)
  - [min](#min)
  - [sum](#sum)
  - [average](#average)
  - [noneMatch](#nonematchpredicate)
  - [allMatch](#allmatchpredicate)
  - [anyMatch](#anymatchpredicate)
  - [count](#count)
  - [findAny](#findany)
  - [findFirst](#findfirst)
  - [flatMap](#flatmapmapper)
  - [skip](#skipn)
  - [reduce](#reduceop)
  - [reduce](#reduceidentityop)


# Functions 
### filter(predicate)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `predicate` | _Function_ | IntPredicate<br>`function(/*int*/ a) { return boolean; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[IntStream](https://github.com/holyrics/jslib/blob/main/doc/en/IntStream.md)_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .filter(n => n != 5 && n % 2 == 1)
         .toArray();
h.log(r);
// output
// [7, 9, 1, 3]
```

---


### map(mapper)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `mapper` | _Function_ | IntUnaryOperator<br>`function(/*int*/ a) { return int; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[IntStream](https://github.com/holyrics/jslib/blob/main/doc/en/IntStream.md)_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .map(n => n + 2)
         .toArray();
h.log(r);
// output
// [9, 10, 11, 6, 7, 8, 3, 4, 5]
```

---


### mapToObj(mapper)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `mapper` | _Function_ | IntFunction<br>`function(/*int*/ a) { return value; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/en/Stream.md)_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .filter(n => n != 5 && n % 2 == 1)
         .mapToObj(n => "n" + n)
         .toArray();
h.log(r);
// output
// ["n7", "n9", "n1", "n3"]
```

---


### sorted()




**Response:**

| Type  | Description |
| :---: | ------------|
| _[IntStream](https://github.com/holyrics/jslib/blob/main/doc/en/IntStream.md)_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .sorted()
         .toArray();
h.log(r);
// output
// [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

---


### forEach(action)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _Function_ | IntConsumer<br>`function(/*int*/ b) { ... }` |


_Method does not return value_

**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .filter(n => n != 5 && n % 2 == 1)
         .forEach(n => h.log(n));
// output
// 7
// 9
// 1
// 3
```

---


### toArray()




**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;Number&gt;_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .sorted()
         .toArray();
```

---


### distinct()




**Response:**

| Type  | Description |
| :---: | ------------|
| _[IntStream](https://github.com/holyrics/jslib/blob/main/doc/en/IntStream.md)_ |  |


**Example:**

```javascript
var arr = [1, 3, 2, 4, 3, 5, 2, 4];
var r = h.intStreamOf(arr)
         .distinct()
         .toArray();
h.log(r);
// output
// [1, 3, 2, 4, 5]
```

---


### limit(maxSize)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `maxSize` | _Number_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[IntStream](https://github.com/holyrics/jslib/blob/main/doc/en/IntStream.md)_ |  |


**Example:**

```javascript
var arr = [1, 3, 2, 4, 3, 5, 2, 4];
var r = h.intStreamOf(arr)
         .distinct()
         .limit(3)
         .toArray();
h.log(r);
// output
// [1, 3, 2]
```

---


### max()




**Response:**

| Type  | Description |
| :---: | ------------|
| _[OptionalInt](https://github.com/holyrics/jslib/blob/main/doc/en/OptionalInt.md)_ |  |


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


### min()




**Response:**

| Type  | Description |
| :---: | ------------|
| _[OptionalInt](https://github.com/holyrics/jslib/blob/main/doc/en/OptionalInt.md)_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .min()
         .orElse(0);
h.log(r);
// r: 1
```

---


### sum()




**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr).sum();
h.log(r);
// r: 45
```

---


### average()




**Response:**

| Type  | Description |
| :---: | ------------|
| _[OptionalDouble](https://github.com/holyrics/jslib/blob/main/doc/en/OptionalDouble.md)_ |  |


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


### noneMatch(predicate)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `predicate` | _Function_ | IntPredicate<br>`function(/*int*/ a) { return boolean; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


**Example:**

```javascript
var arr = [1, 3, 5, 7, 9];
var r = h.intStreamOf(arr).noneMatch(o => o === 1);
// r: false

var r = h.intStreamOf(arr).noneMatch(o => o === 2);
// r: true
```

---


### allMatch(predicate)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `predicate` | _Function_ | IntPredicate<br>`function(/*int*/ a) { return boolean; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


**Example:**

```javascript
var arr = [1, 3, 5, 7, 9];
var r = h.intStreamOf(arr).allMatch(o => o > 0);
// r: true

var r = h.intStreamOf(arr).allMatch(o => o > 1);
// r: false
```

---


### anyMatch(predicate)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `predicate` | _Function_ | IntPredicate<br>`function(/*int*/ a) { return boolean; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


**Example:**

```javascript
var arr = [1, 3, 5, 7, 9];
var r = h.intStreamOf(arr).anyMatch(o => o === 3);
// r: true

var r = h.intStreamOf(arr).anyMatch(o => o === 4);
// r: false
```

---


### count()




**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ |  |


**Example:**

```javascript
var arr = [1, 3, 2, 4, 3, 5, 2, 4];
var r = h.intStreamOf(arr)
         .distinct()
         .count();
h.log(r);
// r: 5
```

---


### findAny()




**Response:**

| Type  | Description |
| :---: | ------------|
| _[OptionalInt](https://github.com/holyrics/jslib/blob/main/doc/en/OptionalInt.md)_ |  |


**Example:**

```javascript
var arr = [1, 3, 2, 4, 3, 5, 2, 4];
var opt = h.intStreamOf(arr)
         .filter(o => o % 2 == 0)
         .findAny();
```

---


### findFirst()




**Response:**

| Type  | Description |
| :---: | ------------|
| _[OptionalInt](https://github.com/holyrics/jslib/blob/main/doc/en/OptionalInt.md)_ |  |


**Example:**

```javascript
var arr = [1, 3, 2, 4, 3, 5, 2, 4];
var opt = h.intStreamOf(arr)
         .filter(o => o % 2 == 0)
         .findFirst();
```

---


### flatMap(mapper)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `mapper` | _Function_ | IntFunction<br>`function(/*int*/ a) { return value; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[IntStream](https://github.com/holyrics/jslib/blob/main/doc/en/IntStream.md)_ |  |


---


### skip(n)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `n` | _Number_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[IntStream](https://github.com/holyrics/jslib/blob/main/doc/en/IntStream.md)_ |  |


**Example:**

```javascript
var arr = [1, 3, 2, 4, 3, 5, 2, 4];
var r = h.intStreamOf(arr)
         .distinct()
         .skip(2)
         .toArray();
h.log(r);
// output
// [2, 4, 5]
```

---


### reduce(op)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `op` | _Function_ | IntBinaryOperator<br>`function(/*int*/ a, /*int*/ b) { return /*int*/ c; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[OptionalInt](https://github.com/holyrics/jslib/blob/main/doc/en/OptionalInt.md)_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .reduce((a, b) => a - b)
         .orElse(0);
h.log(r);
// r: -31
```

---


### reduce(identity,op)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `identity` | _Number_ |  |
| `op` | _Function_ | IntBinaryOperator<br>`function(/*int*/ a, /*int*/ b) { return /*int*/ c; }` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ |  |


**Example:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var r = h.intStreamOf(arr)
         .reduce(100, function(a, b) { return a - b; });
h.log(r);
// r: -31
```

---
