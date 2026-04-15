# DBUtils
Utility class for accessing the main data of the program

---



# Fields 
| Name | Type  | Description |
| ---- | :---: | ------------|
| `list` | _Object_ | List with all the data |
| `ids` | _Object_ | List of all IDs |


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
Returns a list with all the data



**Response:**

| Type  |
| :---: |
| _Array&lt;Object&gt;_ | 


**Example:**

```javascript
var songs = h.db.song.list();
```

---


### ids()
Returns a list of all IDs



**Response:**

| Type  |
| :---: |
| _Array&lt;Object&gt;_ | 


**Example:**

```javascript
var ids = h.db.song.ids();
```

---


### getSize()
Returns the quantity of items



**Response:**

| Type  |
| :---: |
| _Number_ | 


**Example:**

```javascript
var size = h.db.song.getSize();
```

---


### getOptional(id)
### getOpt
Gets an item inside an `Optional` from the ID

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | it can be `Optional.empty()` |


**Example:**

```javascript
var opt = h.db.song.getOpt('123');
```

---


### filteredList(predicate)
Gets the list of items based on a specified filter

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `predicate` | _Function_ | `function` with the respective object that should return `true` or `false` |


**Response:**

| Type  |
| :---: |
| _Array&lt;Object&gt;_ | 


**Example:**

```javascript
var list = h.db.song.filteredList(function(s) {
    return s.title.startsWith("A");
});
```

---


### search(predicate)
Gets an item from the list (within an `Optional`) based on a specified filter

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `predicate` | _Function_ | `function` with the respective object that should return `true` or `false` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | it can be `Optional.empty()` |


**Example:**

```javascript
var opt = h.db.song.search(function(s) {
    return s.title.startsWith("A");
});
```

---
