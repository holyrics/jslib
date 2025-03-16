# Player
Player class to get information and perform actions on the program's player

Example
```javascript
var r = h.getPlayer();
if (r.isPlaying()) {
    h.log('The player is running');
} else {
    h.log('The player is not running');
}

//change volume
r.setVolume(80);

//mute
r.setMute(true);

//stop current execution
r.stop();
```

---

- [Functions](#functions)
  - [getMediaName](#getmedianame)
  - [getMedia](#getmedia)
  - [isPlaying](#isplaying)
  - [getDuration](#getduration)
  - [getCurrentTime](#getcurrenttime)
  - [setCurrentTime](#setcurrenttimetime)
  - [getTimeElapsed](#gettimeelapsed)
  - [getTimeRemaining](#gettimeremaining)
  - [play](#play)
  - [pause](#pause)
  - [stop](#stop)
  - [next](#next)
  - [previous](#previous)
  - [isRepeat](#isrepeat)
  - [setRepeat](#setrepeatrepeat)
  - [isExecuteAll](#isexecuteall)
  - [setExecuteAll](#setexecuteallexecuteall)
  - [isExecuteSingle](#isexecutesingle)
  - [setExecuteSingle](#setexecutesingleexecutesingle)
  - [isShuffle](#isshuffle)
  - [setShuffle](#setshuffleshuffle)
  - [isFullscreen](#isfullscreen)
  - [setFullscreen](#setfullscreenfullscreen)
  - [getVolume](#getvolume)
  - [setVolume](#setvolumevolume)
  - [isMute](#ismute)
  - [setMute](#setmutemute)


# Functions 
### getMediaName()
Name of current media in player



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Media name |


---


### getMedia()
Full path of media in player



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Full media path |


---


### isPlaying()
Checks if the player is running



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### getDuration()
Total media time in the player



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Total time in milliseconds |


---


### getCurrentTime()
Current media time in the player



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Current media time in milliseconds |


---


### setCurrentTime(time)
- v2.20.0

Change the current media time in milliseconds

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `time` | _Number_ | Change the current media time in milliseconds |


_Method does not return value_

---


### getTimeElapsed()
Elapsed media time in the player



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Elapsed time in format HH:MM:SS |


---


### getTimeRemaining()
Remaining media time in the player



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Remaining time in format HH:MM:SS |


---


### play()
Execute the **play** action of the player



_Method does not return value_

---


### pause()
Execute the **pause** action of the player



_Method does not return value_

---


### stop()
Execute the **stop** action of the player



_Method does not return value_

---


### next()
Move to the next item in the list in the player



_Method does not return value_

---


### previous()
Go to the previous item in the list in the player



_Method does not return value_

---


### isRepeat()
Checks if the **repeat** option is enabled



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### setRepeat(repeat)
Change the **repeat** option

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `repeat` | _Boolean_ |  |


_Method does not return value_

---


### isExecuteAll()
Check if the player is set to execute items in sequence



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### setExecuteAll(executeAll)
Changes the player settings to play items in sequence

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `executeAll` | _Boolean_ |  |


_Method does not return value_

---


### isExecuteSingle()
Checks if the player is set to play only the current list item



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### setExecuteSingle(executeSingle)
Change player setting to play only current list item

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `executeSingle` | _Boolean_ |  |


_Method does not return value_

---


### isShuffle()
Checks if the **random** option is enabled



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### setShuffle(shuffle)
Change the **random** option

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `shuffle` | _Boolean_ |  |


_Method does not return value_

---


### isFullscreen()
Checks if the **full screen** option is enabled



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### setFullscreen(fullscreen)
Change player **full screen** option

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `fullscreen` | _Boolean_ |  |


_Method does not return value_

---


### getVolume()
Current player volume



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Volume Minimum=0 Maximum=100 |


---


### setVolume(volume)
Change the volume of the player

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `volume` | _Number_ | Minimum=0, Maximum=100 |


_Method does not return value_

---


### isMute()
Checks if the **mute** option is enabled



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### setMute(mute)
Change the **mute** option

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `mute` | _Boolean_ |  |


_Method does not return value_

---
