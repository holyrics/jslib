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
| _String_ | Nome da mídia |


---


### getMedia()
Full path of media in player



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Caminho completo da mídia |


---


### isPlaying()
Checks if the player is running



**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


---


### getDuration()
Tempo total da mídia atual no player



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Total time in milliseconds |


---


### getCurrentTime()
Tempo atual da mídia no player



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
Tempo decorrido da mídia no player



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Elapsed time in format HH:MM:SS |


---


### getTimeRemaining()
Tempo restante da mídia no player



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Remaining time in format HH:MM:SS |


---


### play()
Executar a ação **play** do player



_Method does not return value_

---


### pause()
Executar a ação **pause** do player



_Method does not return value_

---


### stop()
Executar a ação **stop** do player



_Method does not return value_

---


### next()
Passa para o próximo item da lista no player



_Method does not return value_

---


### previous()
Passa para o item anterior da lista no player



_Method does not return value_

---


### isRepeat()
Checks if the **repeat** option is enabled



**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


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
Verifica se o player está definido para executar itens em sequência



**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


---


### setExecuteAll(executeAll)
Altera a configuração do player para executar itens em sequência

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `executeAll` | _Boolean_ |  |


_Method does not return value_

---


### isExecuteSingle()
Checks if the player is set to play only the current list item



**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


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

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


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

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


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
| _Number_ | Volume. Mínimo=0, Máximo=100 |


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

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


---


### setMute(mute)
Change the **mute** option

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `mute` | _Boolean_ |  |


_Method does not return value_

---
