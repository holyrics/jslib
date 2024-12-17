# Optional

Exemplo
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




**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | throws NoSuchElementException if is null |


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `other` | _Object_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _Object_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `other` | _Function_ | Supplier<br>`function() { return value; }` |


**Resposta:**

| Tipo  |
| :---: |
| _Object_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `exceptionSupplier` | _Function_ | Supplier<br>`function() { return value; }` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | throws NoSuchElementException if is null |


**Exemplo:**

```javascript
var r = opt.orElseThrow(function() { throw 'error'; });
```

---


### filter(predicate)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `predicate` | _Function_ | Predicate<br>`function(o) { return boolean; }` |


**Resposta:**

| Tipo  |
| :---: |
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/pt/Optional.md)_ | 


**Exemplo:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
h.stream(arr)
 .max((a, b) => a.compareTo(b))
 .filter(s => s.length() == 1)
 .ifPresent(s => h.log(s)); //z
```

---


### ifPresent(consumer)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `consumer` | _Function_ | Consumer<br>`function(a) { ... }` |


_Método sem retorno_

**Exemplo:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
h.stream(arr)
 .max((a, b) => a.compareTo(b))
 .ifPresent(s => h.log(s)); //z
```

---


### isPresent()




**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var opt = h.stream(arr).max((a, b) => a.compareTo(b));
if (opt.isPresent()) {
    var r = opt.get(); // z
}
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
| _[Optional](https://github.com/holyrics/jslib/blob/main/doc/pt/Optional.md)_ | 


**Exemplo:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
h.stream(arr)
 .max((a, b) => a.compareTo(b))
 .map(s => "<" + s + ">")
 .ifPresent(s => h.log(s)); // <z>
```

---
