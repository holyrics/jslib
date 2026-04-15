# JavaUtils
Classe utilitária para criar alguns objetos nativos Java (para melhor manipulação que objetos nativos JavaScript)

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




**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [ArrayList](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html) |


**Exemplo:**

```javascript
var list = h.list();
```

---


### list(...args)




**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [ArrayList](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html) |


**Exemplo:**

```javascript
var list = h.list('item 1', 'item 2', 'item 3');
```

---


### set()




**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) |


**Exemplo:**

```javascript
var set = h.set();
```

---


### set(...args)




**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) |


**Exemplo:**

```javascript
var set = h.set('item 1', 'item 2', 'item 3');
```

---


### map()




**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [HashMap](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) |


**Exemplo:**

```javascript
var map = h.map();
```

---


### lmap()




**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [LinkedHashMap](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html) |


**Exemplo:**

```javascript
var lmap = h.lmap();
```

---


### toList(array)
Converte um array nativo JavaScript em ArrayList Java



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [ArrayList](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html) |


**Exemplo:**

```javascript
var arr = [1, 2, 3];
var list = h.toList(arr);
```

---


### toSet(array)
Converte um array nativo JavaScript em HashSet Java



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) |


**Exemplo:**

```javascript
var arr = [1, 2, 3];
var set = h.toSet(arr);
```

---


### toMap(obj)
Converte um objeto nativo JavaScript em HashMap Java



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [HashMap](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) |


**Exemplo:**

```javascript
var m = {
    a: 1,
    b: 2,
    c: 3
};
var map = h.toMap(m);
```

---


### toLMap(obj)
Converte um objeto nativo JavaScript em LinkedHashMap Java



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [LinkedHashMap](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html) |


**Exemplo:**

```javascript
var m = {
    a: 1,
    b: 2,
    c: 3
};
var lmap = h.toLMap(m);
```

---


### optional(obj)
### opt(obj)
Optional Java



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [Optional](https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html) |


**Exemplo:**

```javascript
var opt = h.optional(obj);
```

---
