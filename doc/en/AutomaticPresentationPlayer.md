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
|  | _[AutomaticPresentationSlideInfo](https://github.com/holyrics/jslib/blob/main/doc/en/AutomaticPresentationSlideInfo.md)_ | Slide atual em exibição. Can be null. |


_Method does not return value_

---
