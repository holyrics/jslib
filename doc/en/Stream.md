# Stream
Classe para facilitar a manipulação de listas

Example
```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var sortedArr = h.stream(arr)
  .filter(o => o !== 'x')
  .sorted()
  .toArray();
h.log(sortedArr);
// output
// ['a', 'b', 'c', 'y', 'z']
```

---

- [Functions](#functions)
  - [filter](#filterpredicate)
  - [map](#mapmapper)
  - [sorted](#sorted)
  - [sorted](#sortedcomparator)
  - [forEach](#foreachaction)
  - [toArray](#toarray)
  - [distinct](#distinct)
  - [limit](#limitmaxsize)
  - [max](#maxcomparator)
  - [min](#mincomparator)
  - [noneMatch](#nonematchpredicate)
  - [allMatch](#allmatchpredicate)
  - [anyMatch](#anymatchpredicate)
  - [collect](#collectcollector)
  - [count](#count)
  - [findAny](#findany)
  - [findFirst](#findfirst)
  - [flatMap](#flatmapmapper)
  - [skip](#skipn)
  - [reduce](#reduceaccumulator)
  - [reduce](#reduceidentityaccumulator)
  - [mapToInt](#maptointmapper)


# Functions 
### filter(predicate)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `predicate` | _Function_ | Predicate<br>`function(o) { return boolean; }` |


**Response:**

| Type  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/en/Stream.md)_ | 


**Example:**

```javascript
var arr = ['a', 'b', 'c', 'x', 'y', 'z'];
var arr2 = h.stream(arr)
            .filter(o => o !== 'x')
            .toArray();
h.log(arr2);
// output
// ['a', 'b', 'c', 'y', 'z']
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
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/en/Stream.md)_ | 


**Example:**

```javascript
var arr = ['a', 'b', 'c', 'x', 'y', 'z'];
var arr2 = h.stream(arr)
            .map(o => '?' + o)
            .toArray();
h.log(arr2);
// output
// ['?a', '?b', '?c', '?x', '?y', '?z']
```

---


### sorted()




**Response:**

| Type  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/en/Stream.md)_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var arr2 = h.stream(arr)
            .sorted()
            .toArray();
h.log(arr2);
// output
// ['a', 'b', 'c', 'x', 'y', 'z']
```

---


### sorted(comparator)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `comparator` | _Function_ | Comparator<br>`function(a, b) { return int; }` |


**Response:**

| Type  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/en/Stream.md)_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var arr2 = h.stream(arr)
            .sorted((a, b) => b.compareToIgnoreCase(a))
            .toArray();
h.log(arr2);
// output
// ['z', 'y', 'x', 'c', 'b', 'a']
```

---


### forEach(action)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _Function_ | Consumer<br>`function(a) { ... }` |


_Method does not return value_

**Example:**

```javascript
var arr = ['x', 'y', 'z'];
h.stream(arr)
 .sorted()
 .forEach(o => h.log(o));
// output
// x
// y
// z
```

---


### toArray()




**Response:**

| Type  |
| :---: |
| _Array&lt;Object&gt;_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var arr2 = h.stream(arr)
            .sorted()
            .toArray();
```

---


### distinct()




**Response:**

| Type  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/en/Stream.md)_ | 


**Example:**

```javascript
var arr = ['a', 'b', 'c', 'z', 'b', 'a', 'x', 'y', 'z'];
var arr2 = h.stream(arr)
            .distinct()
            .toArray();
h.log(arr2);
// output
// ['a', 'b', 'c', 'z', 'x', 'y']
```

---


### limit(maxSize)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `maxSize` | _Number_ |  |


**Response:**

| Type  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/en/Stream.md)_ | 


**Example:**

```javascript
var arr = ['a', 'b', 'c', 'z', 'b', 'a', 'x', 'y', 'z'];
var arr2 = h.stream(arr)
            .distinct()
            .limit(4)
            .toArray();
h.log(arr2);
// output
// ['a', 'b', 'c', 'z']
```

---


### max(comparator)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `comparator` | _Function_ | Comparator<br>`function(a, b) { return int; }` |


**Response:**

| Type  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/en/Optional.md)_ | 


**Example:**

```javascript
var arr = ['a', 'b', 'c', 'z', 'b', 'a', 'x', 'y'];
var arr2 = h.stream(arr)
            .max((a, b) => a.compareToIgnoreCase(b));
h.log(arr2.orElse(null));
// output
// z

h.stream(arr)
 .max((a, b) => a.compareToIgnoreCase(b))
 .ifPresent(o => h.log(o));
// output
// z
```

---


### min(comparator)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `comparator` | _Function_ | Comparator<br>`function(a, b) { return int; }` |


**Response:**

| Type  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/en/Optional.md)_ | 


**Example:**

```javascript
var arr = ['z', 'a', 'b', 'c', 'b', 'a', 'x', 'y'];
var arr2 = h.stream(arr)
            .min((a, b) => a.compareToIgnoreCase(b));
h.log(arr2.orElse(null));
// output
// a

h.stream(arr)
 .min((a, b) => a.compareToIgnoreCase(b))
 .ifPresent(o => h.log(o));
// output
// a
```

---


### noneMatch(predicate)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `predicate` | _Function_ | Predicate<br>`function(o) { return boolean; }` |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
var arr = ['z', 'a', 'b', 'c', 'b', 'a', 'x', 'y'];
var r = h.stream(arr).noneMatch(o => o === 'a');
// r: false

var r = h.stream(arr).noneMatch(o => o === 'd');
// r: true
```

---


### allMatch(predicate)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `predicate` | _Function_ | Predicate<br>`function(o) { return boolean; }` |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
var arr = ['z', 'a', 'b', 'c', 'b', 'a', 'x', 'y'];
var r = h.stream(arr).allMatch(o => o.length() == 1);
// r: true

var r = h.stream(arr).allMatch(o => o.length() != 1);
// r: false
```

---


### anyMatch(predicate)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `predicate` | _Function_ | Predicate<br>`function(o) { return boolean; }` |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
var arr = ['z', 'a', 'b', 'c', 'b', 'a', 'x', 'y'];
var r = h.stream(arr).anyMatch(o => o === 'a');
// r: true

var r = h.stream(arr).anyMatch(o => o === 'd');
// r: false
```

---


### collect(collector)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `collector` | _Function_ | Collector<br>`h.stream.toList()`  `h.stream.toSet()`  `h.stream.toMap(function, function)`  `h.stream.joining()`  `h.stream.joining(delimiter)`  `h.stream.joining(delimiter, prefix, suffix)` |


**Response:**

| Type  |
| :---: |
| _Object_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var str = h.stream(arr)
           .sorted((a, b) => b.compareToIgnoreCase(a))
           .collect(h.stream.joining(";"));
h.log(str);
// output
// z;y;x;c;b;a
```

---


### count()




**Response:**

| Type  |
| :---: |
| _Number_ | 


**Example:**

```javascript
var arr = ['aa', 'b', 'cc', 'x', 'yy', 'z'];
var r = h.stream(arr)
         .filter(o => o.length() == 2)
         .count();
h.log(r);
// r: 3
```

---


### findAny()




**Response:**

| Type  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/en/Optional.md)_ | 


**Example:**

```javascript
var arr = ['aa', 'b', 'cc', 'x', 'yy', 'z'];
h.stream(arr)
 .filter(o => o.length() == 2)
 .findAny()
 .ifPresent(o => h.log(o));
```

---


### findFirst()




**Response:**

| Type  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/en/Optional.md)_ | 


**Example:**

```javascript
var arr = ['aa', 'b', 'cc', 'x', 'yy', 'z'];
h.stream(arr)
 .filter(o => o.length() == 2)
 .findFirst()
 .ifPresent(o => h.log(o));
```

---


### flatMap(mapper)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `mapper` | _Function_ | Function<br>`function(a) { return b; }` |


**Response:**

| Type  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/en/Stream.md)_ | 


**Example:**

```javascript
var arr = ['aa', 'b', 'cc', 'x', 'yy', 'z'];
var arr2 = h.stream(arr)
            .filter(o => o.length() == 2)
            .flatMap(o => h.stream(o.split("")))
            .toArray();
h.log(arr2);
// output
// ['a', 'a', 'c', 'c', 'y', 'y']
```

---


### skip(n)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `n` | _Number_ |  |


**Response:**

| Type  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/en/Stream.md)_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var arr2 = h.stream(arr)
            .sorted()
            .skip(2)
            .toArray();
h.log(arr2);
// output
// ['c', 'x', 'y', 'z']
```

---


### reduce(accumulator)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `accumulator` | _Function_ | BinaryOperator<br>`function(a, b) { return c; }` |


**Response:**

| Type  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/en/Optional.md)_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
h.stream(arr)
 .sorted()
 .skip(2)
 .reduce((a, b) => a + b)
 .ifPresent(o => h.log(o));
 // output
 // cxyz
```

---


### reduce(identity,accumulator)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `identity` | _Object_ |  |
| `accumulator` | _Function_ | BinaryOperator<br>`function(a, b) { return c; }` |


**Response:**

| Type  |
| :---: |
| _Object_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var r = h.stream(arr)
         .sorted()
         .skip(2)
         .reduce('test', function(a, b) { return a + b });
h.log(r);
// output
// testcxyz
```

---


### mapToInt(mapper)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `mapper` | _Function_ | ToIntFunction<br>`function(a) { return /*int*/ c; }` |


**Response:**

| Type  |
| :---: |
| _[IntStream](https://github.com/holyrics/jslib/blob/main/doc/en/IntStream.md)_ | 


**Example:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var arr2 = h.stream(arr)
            .sorted()
            .mapToInt(o => o.codePointAt(0))
            .toArray();
h.log(arr2);
// output
// [97, 98, 99, 120, 121, 122]
```

---
