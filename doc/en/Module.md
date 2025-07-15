# Module
Object that represents a module added to the program

---



# Fields 
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `jscommunity_id` | _String_ | Global ID of the item in the JSCommunity repository<br>Alternative names: `community_id` `jsc_id` |
| `info_id` | _String_ | ID defined for the item in `function info()`<br>If the module is from the JSCommunity source, the value is the same as `jscommunity_id` |
| `name` | _String_ | Module name |
| `active` | _Boolean_ | If the module is active. active is a result of `enabled_by_user && conditional_execution` |
| `enabled_by_user` | _Boolean_ | If the module is enabled by the user (checkbox in the interface) |
| `conditional_execution` | _Boolean_ | If the module is activated based on the possible conditional executions defined for it by the user |
| `show_panel` | _Boolean_ | Display the module in the Modules panel |
| `available_in_main_window` | _Boolean_ | Module available for use in the main window panel |
| `available_in_bible_window` | _Boolean_ | Module available for use in the Bible window panel |
| `actions` | _Object_ | Key/value map<br>Each key is the action id and each value is a `ModuleAction` object [ModuleAction](https://github.com/holyrics/jslib/blob/main/doc/en/ModuleAction.md) |


---

- [Functions](#functions)
  - [getID](#getid)
  - [getName](#getname)
  - [getActions](#getactions)
  - [getAction](#getactionactionid)
  - [adminAction](#adminactionactiontype-securitytoken)


# Functions 
### getID()
Item ID



**Response:**

| Type  |
| :---: |
| _String_ | 


---


### getName()
Item name



**Response:**

| Type  |
| :---: |
| _String_ | 


---


### getActions()
Returns the list of available actions



**Response:**

| Type  |
| :---: |
| _Array&lt;[ModuleAction](https://github.com/holyrics/jslib/blob/main/doc/en/ModuleAction.md)&gt;_ | 


**Example:**

```javascript
var module = h.getModule('id');
var actions = module.getActions();
for (var i = 0; i < actions.length; i++) {
    //h.logp(list[i]);
    h.log(actions[i].id + " | " + actions[i].name);
}
```

---


### getAction(action_id)
Returns a specific action

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action_id` | _String_ | Action ID |


**Response:**

| Type  |
| :---: |
| _[ModuleAction](https://github.com/holyrics/jslib/blob/main/doc/en/ModuleAction.md)_ | 


**Example:**

```javascript
var module = h.getModule('id');
var action = module.getAction('action_id');
```

---


### adminAction(action_type, security_token)
Execute an advanced action in a module<br>The security token can be obtained in the modules window, in the 3-dot icon of the respective module

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action_type` | _String_ | Type of action<br>`update_panel` `repaint_panel` `restart` `enable` `disable` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `security_token` | _String_ | Security token |


**Example:**

```javascript
h.adminAction('restart', 'abcxyz');
```

---
