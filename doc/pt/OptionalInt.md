# OptionalInt

Exemplo
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




**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | throws NoSuchElementException if is null |


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `other` | _Number_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ |  |


**Exemplo:**

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


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `other` | _Function_ | IntSupplier<br>`function() { return int; }` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ |  |


**Exemplo:**

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
         .max()
         .orElseThrow(function() { throw 'error'; });
h.log(r);
// r: 9
```

---


### ifPresent(consumer)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `consumer` | _Function_ | IntConsumer<br>`function(/*int*/ b) { ... }` |


_Método sem retorno_

**Exemplo:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
h.intStreamOf(arr)
 .max()
 .ifPresent(n => h.log(n)); // 9
```

---


### isPresent()




**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


**Exemplo:**

```javascript
var arr = [7, 8, 9, 4, 5, 6, 1, 2, 3];
var opt = h.intStreamOf(arr).max();
if (opt.isPresent()) {
    h.log(opt.getAsInt()); // 9
}
```

---
