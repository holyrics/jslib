# Stream
Classe para facilitar a manipulação de listas

Exemplo
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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `predicate` | _Function_ | Predicate<br>`function(o) { return boolean; }` |


**Resposta:**

| Tipo  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/pt/Stream.md)_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `mapper` | _Function_ | Function<br>`function(a) { return b; }` |


**Resposta:**

| Tipo  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/pt/Stream.md)_ | 


**Exemplo:**

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




**Resposta:**

| Tipo  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/pt/Stream.md)_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `comparator` | _Function_ | Comparator<br>`function(a, b) { return int; }` |


**Resposta:**

| Tipo  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/pt/Stream.md)_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _Function_ | Consumer<br>`function(a) { ... }` |


_Método sem retorno_

**Exemplo:**

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




**Resposta:**

| Tipo  |
| :---: |
| _Array&lt;Object&gt;_ | 


**Exemplo:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var arr2 = h.stream(arr)
            .sorted()
            .toArray();
```

---


### distinct()




**Resposta:**

| Tipo  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/pt/Stream.md)_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `maxSize` | _Number_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/pt/Stream.md)_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `comparator` | _Function_ | Comparator<br>`function(a, b) { return int; }` |


**Resposta:**

| Tipo  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/pt/Optional.md)_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `comparator` | _Function_ | Comparator<br>`function(a, b) { return int; }` |


**Resposta:**

| Tipo  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/pt/Optional.md)_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `predicate` | _Function_ | Predicate<br>`function(o) { return boolean; }` |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
var arr = ['z', 'a', 'b', 'c', 'b', 'a', 'x', 'y'];
var r = h.stream(arr).noneMatch(o => o === 'a');
// r: false

var r = h.stream(arr).noneMatch(o => o === 'd');
// r: true
```

---


### allMatch(predicate)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `predicate` | _Function_ | Predicate<br>`function(o) { return boolean; }` |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
var arr = ['z', 'a', 'b', 'c', 'b', 'a', 'x', 'y'];
var r = h.stream(arr).allMatch(o => o.length() == 1);
// r: true

var r = h.stream(arr).allMatch(o => o.length() != 1);
// r: false
```

---


### anyMatch(predicate)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `predicate` | _Function_ | Predicate<br>`function(o) { return boolean; }` |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
var arr = ['z', 'a', 'b', 'c', 'b', 'a', 'x', 'y'];
var r = h.stream(arr).anyMatch(o => o === 'a');
// r: true

var r = h.stream(arr).anyMatch(o => o === 'd');
// r: false
```

---


### collect(collector)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `collector` | _Function_ | Collector<br>`h.stream.toList()`  `h.stream.toSet()`  `h.stream.toMap(function, function)`  `h.stream.joining()`  `h.stream.joining(delimiter)`  `h.stream.joining(delimiter, prefix, suffix)` |


**Resposta:**

| Tipo  |
| :---: |
| _Object_ | 


**Exemplo:**

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




**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


**Exemplo:**

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




**Resposta:**

| Tipo  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/pt/Optional.md)_ | 


**Exemplo:**

```javascript
var arr = ['aa', 'b', 'cc', 'x', 'yy', 'z'];
h.stream(arr)
 .filter(o => o.length() == 2)
 .findAny()
 .ifPresent(o => h.log(o));
```

---


### findFirst()




**Resposta:**

| Tipo  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/pt/Optional.md)_ | 


**Exemplo:**

```javascript
var arr = ['aa', 'b', 'cc', 'x', 'yy', 'z'];
h.stream(arr)
 .filter(o => o.length() == 2)
 .findFirst()
 .ifPresent(o => h.log(o));
```

---


### flatMap(mapper)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `mapper` | _Function_ | Function<br>`function(a) { return b; }` |


**Resposta:**

| Tipo  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/pt/Stream.md)_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `n` | _Number_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _[Stream](https://github.com/holyrics/jslib/blob/main/doc/pt/Stream.md)_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `accumulator` | _Function_ | BinaryOperator<br>`function(a, b) { return c; }` |


**Resposta:**

| Tipo  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/pt/Optional.md)_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `identity` | _Object_ |  |
| `accumulator` | _Function_ | BinaryOperator<br>`function(a, b) { return c; }` |


**Resposta:**

| Tipo  |
| :---: |
| _Object_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `mapper` | _Function_ | ToIntFunction<br>`function(a) { return /*int*/ c; }` |


**Resposta:**

| Tipo  |
| :---: |
| _[IntStream](https://github.com/holyrics/jslib/blob/main/doc/pt/IntStream.md)_ | 


**Exemplo:**

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
