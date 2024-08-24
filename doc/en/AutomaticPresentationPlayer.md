# AutomaticPresentationPlayer
Class representing the program's automatic presentation player

Example
```javascript
var r = h.getAPPlayer();
if (r.isPlaying()) {
    h.logf('Total time: {} - Slide time: {}', r.getTime(), r.getSlide().getTime());
}
```

---

- [Functions](#functions)
  - [getName](#getname)
  - [isPlaying](#isplaying)
  - [getVolume](#getvolume)
  - [isMute](#ismute)
  - [getTime](#gettime)
  - [getDuration](#getduration)
  - [getSlide](#getslide)
  - [getSlide](#getslidegetnumber)
  - [getSlide](#getslidegettext)
  - [getSlide](#getslidegetdescription)
  - [getSlide](#getslidegetstart)
  - [getSlide](#getslidegetend)
  - [getSlide](#getslidegetduration)
  - [getSlide](#getslidegettime)


# Functions 
### getName()
- v2.23.0

Name of current media in player



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Nome da mídia |


---


### isPlaying()
- v2.23.0

Checks if the player is running



**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


---


### getVolume()
- v2.23.0

Current player volume



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Volume. Mínimo=0, Máximo=100 |


---


### isMute()
- v2.23.0

Checks if the **mute** option is enabled



**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


---


### getTime()
- v2.23.0

Tempo atual da mídia no player



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Current media time in milliseconds |


---


### getDuration()
- v2.23.0

Tempo total da mídia atual no player



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Total time in milliseconds |


---


### getSlide()
- v2.23.0

Informação sobre o slide atual em exibição

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Object_ | Slide atual em exibição. Can be null. |


_Method does not return value_

---


### getSlide().getNumber()
- v2.23.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Number_ | Número do slide. Começa em zero |


_Method does not return value_

---


### getSlide().getText()
- v2.23.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _String_ | Slide text |


_Method does not return value_

---


### getSlide().getDescription()
- v2.23.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _String_ | Slide description |


_Method does not return value_

---


### getSlide().getStart()
- v2.23.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Number_ | Start time of the presentation in milliseconds |


_Method does not return value_

---


### getSlide().getEnd()
- v2.23.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Number_ | End time of the presentation in milliseconds |


_Method does not return value_

---


### getSlide().getDuration()
- v2.23.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Number_ | Duration in milliseconds |


_Method does not return value_

---


### getSlide().getTime()
- v2.23.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Number_ | Tempo atual do slide. `time >= 0 && time <= duration` |


_Method does not return value_

---
