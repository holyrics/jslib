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
  - [play](#play)
  - [pause](#pause)
  - [stop](#stop)
  - [setVolume](#setvolumevolume)
  - [setMute](#setmutemute)
  - [setCurrentTime](#setcurrenttimetime)
  - [getSlide](#getslide)


# Functions 
### getName
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


### play()
- v2.29.0

Execute the **play** action of the player



_Method does not return value_

---


### pause()
- v2.29.0

Execute the **pause** action of the player



_Method does not return value_

---


### stop()
- v2.29.0

Execute the **stop** action of the player



_Method does not return value_

---


### setVolume(volume)
- v2.29.0

Change the volume of the player

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `volume` | _Number_ | Minimum=0, Maximum=100 |


_Method does not return value_

---


### setMute(mute)
- v2.29.0

Change the **mute** option

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `mute` | _Boolean_ |  |


_Method does not return value_

---


### setCurrentTime(time)
- v2.29.0

Change the current media time in milliseconds

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `time` | _Number_ | Change the current media time in milliseconds |


_Method does not return value_

---


### getSlide()
- v2.23.0

Information about the current slide being displayed



**Response:**

| Type  | Description |
| :---: | ------------|
| _[AutomaticPresentationSlideInfo](https://github.com/holyrics/jslib/blob/main/doc/en/AutomaticPresentationSlideInfo.md)_ | Current slide being displayed. Can be null. |


---
