# OptionalDouble

Exemplo
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




**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | throws NoSuchElementException if is null |


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `other` | _Number_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `other` | _Function_ | DoubleSupplier<br>`function() { return double; }` |


**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `exceptionSupplier` | _Function_ | Supplier<br>`function() { return value; }` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | throws NoSuchElementException if is null |


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `consumer` | _Function_ | DoubleConsumer<br>`function(/*double*/ b) { ... }` |


_Método sem retorno_

**Exemplo:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
h.intStreamOf(arr)
 .average()
 .ifPresent(n => h.log(n)); // 5
```

---


### isPresent()




**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var opt = h.intStreamOf(arr).average();
if (opt.isPresent()) {
    h.log(opt.getAsDouble()); // 5
}
```

---
