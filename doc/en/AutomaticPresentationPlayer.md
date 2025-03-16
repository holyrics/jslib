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
| _String_ | Media name |


---


### isPlaying()
- v2.23.0

Checks if the player is running



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### getVolume()
- v2.23.0

Current player volume



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Volume Minimum=0 Maximum=100 |


---


### isMute()
- v2.23.0

Checks if the **mute** option is enabled



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### getTime()
- v2.23.0

Current media time in the player



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Current media time in milliseconds |


---


### getDuration()
- v2.23.0

Total media time in the player



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Total time in milliseconds |


---


### getSlide()
- v2.23.0

Information about the current slide being displayed



**Response:**

| Type  | Description |
| :---: | ------------|
| _[AutomaticPresentationSlideInfo](https://github.com/holyrics/jslib/blob/main/doc/en/AutomaticPresentationSlideInfo.md)_ | Current slide being displayed. Can be null. |


---
