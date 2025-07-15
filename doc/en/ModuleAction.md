# ModuleAction
Object that represents a public action of a module added to the program

---



# Fields 
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |
| `description` | _String_ | Item description |
| `available_for` | _String_ | Lista de origens que a ação está disponível.<br>If the field is empty, it means that the action is available for all sources.<br>Available values: `ui` `trigger` `jslib_call` `jslib_open` `add_to_playlist` |
| `unavailable_for` | _Boolean_ | Lista de origens que a ação está indisponível.<br>Available values: `ui` `trigger` `jslib_call` `jslib_open` `add_to_playlist` |
| `input` | _Object_ | List of required parameters for action execution |


---

- [Functions](#functions)
  - [call](#callinput--null)
  - [callEx](#callexinput--null)
  - [callAsync](#callasyncinput--null-callback--null)
  - [open](#openinput--null-callback--null)
  - [openAndWait](#openandwaitinput--null)
  - [openAndWaitEx](#openandwaitexinput--null)
  - [openNotification](#opennotificationinput--null-callback--null)
  - [openNotificationAndWait](#opennotificationandwaitinput--null)
  - [openNotificationAndWaitEx](#opennotificationandwaitexinput--null)


# Functions 
### call(input = null)
Execute the action and get the response.<br>Returns `null` if there is an error.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | Key/value map<br>Parameters for executing the action |


_Method does not return value_

**Example:**

```javascript
var module = h.getModule('id');
var action = module.getAction('action_id');
var params = {
    /* ... */
};
var r = action.call(params);
```

---


### callEx(input = null)
Execute the action and get the response.<br>Generates **Exception** if there is an error.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | Key/value map<br>Parameters for executing the action |


_Method does not return value_

**Example:**

```javascript
try {
    var params = {
      /* ... */
    };
    action.callEx(params);
} catch (e) {
    h.log(e);
}
```

---


### callAsync(input = null, callback = null)
Execute the action and get the response.<br>Asynchronous execution.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | Key/value map<br>Parameters for executing the action |
| `callback` | _Function (optional)_ | Method that will be executed with the response of the request or with the error message.<br>`function(result, error) { /* ... */ }` |


_Method does not return value_

**Example:**

```javascript
var params = {
    /* ... */
};
action.callAsync(params, function() {
    //callback
});
```

---


### open(input = null, callback = null)
Opens a window for the user to input/edit the inputs and execute the action.<br>Asynchronous execution.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | Key/value map<br>Parameters for executing the action |
| `callback` | _Function (optional)_ | Method that will be executed with the response of the request or with the error message.<br>`function(result, error) { /* ... */ }` |


_Method does not return value_

**Example:**

```javascript
var params = {
    /* ... */
};
action.open(params, function() {
    //callback
});
```

---


### openAndWait(input = null)
Opens a window for the user to input/edit the inputs and execute the action..<br>Awaiting the response of the action.<br>Returns `null` if there is an error.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | Key/value map<br>Parameters for executing the action |


_Method does not return value_

**Example:**

```javascript
var params = {
    /* ... */
};
action.openAndWait(params);
```

---


### openAndWaitEx(input = null)
Opens a window for the user to input/edit the inputs and execute the action.<br>Awaiting the response of the action.<br>Generates **Exception** if there is an error.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | Key/value map<br>Parameters for executing the action |


_Method does not return value_

**Example:**

```javascript
var params = {
    /* ... */
};
action.openAndWaitEx(params);
```

---


### openNotification(input = null, callback = null)
Displays a notification in the corner of the screen for the user to input/edit the inputs and execute the action.<br>Asynchronous execution.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | Key/value map<br>Parameters for executing the action |
| `callback` | _Function (optional)_ | Method that will be executed with the response of the request or with the error message.<br>`function(result, error) { /* ... */ }` |


_Method does not return value_

**Example:**

```javascript
var params = {
    /* ... */
};
action.openNotification(params, function() {
    //callback
});
```

---


### openNotificationAndWait(input = null)
Displays a notification in the corner of the screen for the user to input/edit the inputs and execute the action.<br>Awaiting the response of the action.<br>Returns `null` if there is an error.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | Key/value map<br>Parameters for executing the action |


_Method does not return value_

**Example:**

```javascript
var params = {
    /* ... */
};
action.openNotificationAndWait(params);
```

---


### openNotificationAndWaitEx(input = null)
Displays a notification in the corner of the screen for the user to input/edit the inputs and execute the action.<br>Awaiting the response of the action.<br>Generates **Exception** if there is an error.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | Key/value map<br>Parameters for executing the action |


_Method does not return value_

**Example:**

```javascript
var params = {
    /* ... */
};
action.openNotificationAndWaitEx(params);
```

---
