# DBUtils
Classe utilitária para acessar os principais dados do programa<br>
<br>
Acessar um item pelo ID:
```javascript
var song = h.db.song['123'];
```

---



# Fields 
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `list` | _Object_ | Lista com todos os dados |
| `ids` | _Object_ | Lista com todos os IDs |


---

- [Functions](#functions)
  - [list](#list)
  - [ids](#ids)
  - [getSize](#getsize)
  - [getOptional](#getoptionalid)
  - [filteredList](#filteredlistpredicate)
  - [search](#searchpredicate)


# Functions 
### list()
Retorna uma lista com todos os dados



**Resposta:**

| Tipo  |
| :---: |
| _Array&lt;Object&gt;_ | 


**Exemplo:**

```javascript
var songs = h.db.song.list();
```

---


### ids()
Retorna uma lista com todos os IDs



**Resposta:**

| Tipo  |
| :---: |
| _Array&lt;Object&gt;_ | 


**Exemplo:**

```javascript
var ids = h.db.song.ids();
```

---


### getSize()
Retorna a quantidade de itens



**Resposta:**

| Tipo  |
| :---: |
| _Number_ | 


**Exemplo:**

```javascript
var size = h.db.song.getSize();
```

---


### getOptional(id)
### getOpt
Obtém um item dentro de um `Optional` a partir do ID

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | pode ser `Optional.empty()` |


**Exemplo:**

```javascript
var opt = h.db.song.getOpt('123');
```

---


### filteredList(predicate)
Obtém a lista de itens baseado em um filtro determinado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `predicate` | _Function_ | `function` com o respectivo objeto que deve retornar `true` ou `false` |


**Resposta:**

| Tipo  |
| :---: |
| _Array&lt;Object&gt;_ | 


**Exemplo:**

```javascript
var list = h.db.song.filteredList(function(s) {
    return s.title.startsWith("A");
});
```

---


### search(predicate)
Obtém um item da lista (dentro de um `Optional`) baseado em um filtro determinado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `predicate` | _Function_ | `function` com o respectivo objeto que deve retornar `true` ou `false` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | pode ser `Optional.empty()` |


**Exemplo:**

```javascript
var opt = h.db.song.search(function(s) {
    return s.title.startsWith("A");
});
```

---
