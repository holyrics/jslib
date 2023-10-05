# jslib
**EN** | [PT](README.md)

JSLib class methods available for use in Holyrics program scripts.

You can use the ```jslib``` variable or the ```h``` variable to access the available methods.

For example:

```
jslib.log('example');
h.log('example');
```
---

- [Methods](#methods)
  - [log](#logobj)
  - [log](#logkey--null-obj-args--null)
  - [log.enable](#logenablekey)
  - [log.enableAll](#logenableall)
  - [log.isEnabled](#logisenabledkey)
  - [log.setShowLogKey](#logsetshowlogkeyvalue)
  - [log.isShowLogKey](#logisshowlogkey)
  - [sleep](#sleeptime)
  - [base64Encode](#base64encodebytes)
  - [base64Decode](#base64decodestr)
  - [md5](#md5value)
  - [md5Str](#md5strvalue)
  - [sha256](#sha256value)
  - [sha256Str](#sha256strvalue)
  - [sha512](#sha512value)
  - [sha512Str](#sha512strvalue)
  - [getClipboard](#getclipboard)
  - [normalize](#normalizestr)
  - [store](#storekey-value)
  - [restore](#restorekey)
  - [setGlobal](#setglobalkey-value)
  - [getGlobal](#getglobalkey-default--null)
  - [setCache](#setcachekey-value)
  - [getCache](#getcachekey-default--null)
  - [random](#randommin-max-keysaferepeat--null)
  - [startTimer](#starttimerkey--default)
  - [getTimer](#gettimerkey--default)
  - [startCountdown](#startcountdownkey--default-seconds)
  - [getCountdown](#getcountdownkey--default)
  - [getPlaylistInfo](#getplaylistinfo)
  - [getPlayer](#getplayer)
  - [scriptAction](#scriptactionid-input--null)
  - [apiAction](#apiactionid-input--null)
  - [apiRequest](#apirequestid-raw)
  - [getApiRequestLastError](#getapirequestlasterror)
  - [apiRequestAsync](#apirequestasyncid-raw-callback--null)
  - [setTimeout](#settimeoutfunction-timeout)
  - [clearTimeout](#cleartimeoutid)
  - [setInterval](#setintervalfunction-timeout)
  - [clearInterval](#clearintervalid)
  - [getHostname](#gethostname)
  - [getRuntimeEnvironment](#getruntimeenvironment)
  - [setRuntimeEnvironment](#setruntimeenvironmentname)
  - [isRuntimeEnvironment](#isruntimeenvironmentname)
  - [getVersion](#getversion)
  - [isMinimumVersion](#isminimumversionversion)
  - [getLanguage](#getlanguage)
  - [isLanguage](#islanguagelanguage)
  - [getUITheme](#getuitheme)
  - [isUITheme](#isuithemevalue)
  - [format.secondsToHMS](#formatsecondstohmsseconds-separator--)
  - [format.secondsToMS](#formatsecondstomsseconds-separator--)
  - [format.minutesToHM](#formatminutestohmminutes-separator--)
  - [date.getSecondOfDay](#dategetsecondofday)
- [Methods HLY](#methods-hly)
  - [GetLyrics](#hlygetlyrics-input)
  - [SearchLyrics](#hlysearchlyrics-input)
  - [ShowLyrics](#hlyshowlyrics-input)
  - [ShowText](#hlyshowtext-input)
  - [ShowVerse](#hlyshowverse-input)
  - [GetAudios - GetVideos - GetImages](#hlygetaudios-input)
  - [PlayAudio](#hlyplayaudio-input)
  - [PlayVideo](#hlyplayvideo-input)
  - [ShowImage](#hlyshowimage-input)
  - [ShowAnnouncement](#hlyshowannouncement-input)
  - [GetCustomMessages](#hlygetcustommessages)
  - [ShowCustomMessage](#hlyshowcustommessage-input)
  - [ShowQuickPresentation](#hlyshowquickpresentation-input)
  - [ShowCountdown](#hlyshowcountdown-input)
  - [ShowQuiz](#hlyshowquiz-input)
  - [QuizAction](#hlyquizaction-input)
  - [PlayAutomaticPresentation](#hlyplayautomaticpresentation-input)
  - [GetAutomaticPresentationPlayerInfo](#hlygetautomaticpresentationplayerinfo)
  - [AutomaticPresentationPlayerAction](#hlyautomaticpresentationplayeraction-input)
  - [GetMediaPlayerInfo](#hlygetmediaplayerinfo)
  - [MediaPlayerAction](#hlymediaplayeraction-input)
  - [GetLyricsPlaylist](#hlygetlyricsplaylist)
  - [AddLyricsToPlaylist](#hlyaddlyricstoplaylist-input)
  - [RemoveFromLyricsPlaylist](#hlyremovefromlyricsplaylist-input)
  - [GetMediaPlaylist](#hlygetmediaplaylist)
  - [MediaPlaylistAction](#hlymediaplaylistaction-input)
  - [AddToPlaylist](#hlyaddtoplaylist-input)
  - [RemoveFromMediaPlaylist](#hlyremovefrommediaplaylist-input)
  - [GetFavorites](#hlygetfavorites)
  - [FavoriteAction](#hlyfavoriteaction-input)
  - [ApiAction](#hlyapiaction-input)
  - [ScriptAction](#hlyscriptaction-input)
  - [ApiRequest](#hlyapirequest-input)
  - [GetCurrentPresentation](#hlygetcurrentpresentation)
  - [CloseCurrentPresentation](#hlyclosecurrentpresentation)
  - [GetF8 - F9 - F10](#hlygetf8)
  - [SetF8 - F9 - F10](#hlysetf8-input)
  - [ToggleF8 - F9 - F10](#hlytogglef8)
  - [ActionNext](#hlyactionnext)
  - [ActionPrevious](#hlyactionprevious)
  - [ActionGoToIndex](#hlyactiongotoindex-input)
  - [ActionGoToSlideDescription](#hlyactiongotoslidedescription-input)
  - [GetCurrentBackground](#hlygetcurrentbackground)
  - [GetBackgrounds](#hlygetbackgrounds-input)
  - [SetCurrentBackground](#hlysetcurrentbackground-input)
  - [GetColorMap](#hlygetcolormap-input)
  - [SetAlert](#hlysetalert-input)
  - [GetCurrentSchedule](#hlygetcurrentschedule)
  - [GetSchedules](#hlygetschedules-input)
  - [GetSavedPlaylists](#hlygetsavedplaylists)
  - [LoadSavedPlaylist](#hlyloadsavedplaylist-input)
  - [GetHistory](#hlygethistory-input)
  - [GetHistories](#hlygethistories)
  - [GetMembers](#hlygetmembers)
  - [GetRoles](#hlygetroles)
  - [GetCommunicationPanelInfo](#hlygetcommunicationpanelinfo)
  - [SetCommunicationPanelSettings](#hlysetcommunicationpanelsettings-input)
  - [StartCountdownCommunicationPanel](#hlystartcountdowncommunicationpanel-input)
  - [StopCountdownCommunicationPanel](#hlystopcountdowncommunicationpanel)
  - [StartTimerCommunicationPanel](#hlystarttimercommunicationpanel)
  - [StopTimerCommunicationPanel](#hlystoptimercommunicationpanel)
  - [SetTextCommunicationPanel](#hlysettextcommunicationpanel-input)
  - [SetAlertCommunicationPanel](#hlysetalertcommunicationpanel-input)
  - [CommunicationPanelCallAttention](#hlycommunicationpanelcallattention)
  - [GetWallpaperSettings](#hlygetwallpapersettings)
  - [SetWallpaperSettings](#hlysetwallpapersettings-input)
  - [GetDisplaySettings](#hlygetdisplaysettings)
  - [SetDisplaySettings](#hlysetdisplaysettings-input)
  - [GetBpm](#hlygetbpm)
  - [SetBpm](#hlysetbpm-input)
  - [GetHue](#hlygethue)
  - [SetHue](#hlysethue-input)
  - [GetRuntimeEnvironment](#hlygetruntimeenvironment)
  - [SetRuntimeEnvironment](#hlysetruntimeenvironment-input)
  - [SetLogo](#hlysetlogo-input)
  - [GetSyncStatus](#hlygetsyncstatus)
- [Methods Player](#methods-player)
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
- [User input Methods](#user-input-methods)
  - [input](#inputparam-notification--false)
  - [inputTextArea](#inputtextareatitle-notification--false)
  - [itemChooser](#itemchoosertitle-items-notification--false)
  - [multipleItemChooser](#multipleitemchoosertitle-items-notification--false)
  - [confirm](#confirmmsg-title--confirm-notification--false)
  - [yesNo](#yesnomsg-title--confirm-notification--false)
  - [notification](#notificationmsg-duration--0)
  - [lyricsChooser](#lyricschooser)
  - [themeChooser](#themechooser)
  - [imageChooser](#imagechooser)
  - [audioChooser](#audiochooser)
  - [videoChooser](#videochooser)
  - [backgroundChooser](#backgroundchooser)
- [Classes](#classes)
  - [Lyrics](#lyrics)
  - [Background](#background)
  - [Item](#item)
  - [Group](#group)
  - [Midi](#midi)
  - [Favorite Item](#favorite-item)
  - [Schedule](#schedule)
  - [Member](#member)
  - [Role](#role)
  - [Automatic Presentation](#automatic-presentation)
  - [Input Param](#input-param)
  - [Display Settings](#display-settings)
  - [Stage View](#stage-view)
  - [Slide Additional Info](#slide-additional-info)
  - [Rectangle](#rectangle)
  - [Custom Message](#custom-message)
  - [Custom Message Param](#custom-message-param)
  - [Quiz Question](#quiz-question)
  - [Quiz Settings](#quiz-settings)
  - [AddItem](#additem)
  - [AddItemTitle](#additemtitle)
  - [AddItemSong](#additemsong)
  - [AddItemVerse](#additemverse)
  - [AddItemText](#additemtext)
  - [AddItemAudio](#additemaudio)
  - [AddItemVideo](#additemvideo)
  - [AddItemImage](#additemimage)
  - [AddItemAutomaticPresentation](#additemautomaticpresentation)
  - [AddItemAnnouncement](#additemannouncement)
  - [AddItemCountdown](#additemcountdown)
  - [AddItemCountdownCommunicationPanel](#additemcountdowncommunicationpanel)
  - [AddItemTextCommunicationPanel](#additemtextcommunicationpanel)
  - [AddItemScript](#additemscript)
  - [AddItemAPI](#additemapi)


# Methods 
### log(obj)
Display the information passed as a parameter in a log window (lower right corner of the screen, usually)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `obj` | _Object_ | Any object to be displayed in the log window |


_Method does not return value_

**Example:**

```javascript
h.log('log message');
```

---


### log(key = null, obj, args = null)
### log.add(key = null, obj, args = null)
- v2.20.0

Display the information passed as a parameter in a log window (lower right corner of the screen, usually)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id de gerenciamento do log |
| `obj` | _Object_ | Any object to be displayed in the log window |
| `args` | _Array&lt;Object&gt;_ | Parâmetros para formatação de uma mensagem de log |


_Method does not return value_

**Example:**

```javascript
h.log('xyz', 'log message');

h.log('xyz', 'log message {} abc {}', ['value 1', 'value 2']);
//output:
//log message value 1 abc value 2

h.log('log message {} abc {}', ['value 1', 'value 2']);
//output:
//log message value 1 abc value 2
```

---


### log.enable(key)
### log.disable(key)
- v2.20.0

Ativar/desativar a visualização de logs da chave/id passada por parâmetro. Todas as chaves/ids iniciam desativadas por padrão

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id de gerenciamento do log |


_Method does not return value_

**Example:**

```javascript
h.log.enable('xyz');
h.log.disable('xyz');
```

---


### log.enableAll()
### log.disableAll()
- v2.20.0

Ativa/desativa a visualização de todos os logs



_Method does not return value_

**Example:**

```javascript
h.log.enableAll();
h.log.disableAll();
```

---


### log.isEnabled(key)
### log.isDisabled(key)
- v2.20.0

Verifica se a visualização está ativada/desativada para a respectiva chave/id

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id de gerenciamento do log |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


**Example:**

```javascript
if (h.log.isEnabled('xyz')) {
    //...
}

if (h.log.isDisabled('xyz')) {
    //...
}
```

---


### log.setShowLogKey(value)
- v2.20.0

Ativa/desativa a exibição chave/id junto da mensagem na janela de log

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Boolean_ |  |


_Method does not return value_

**Example:**

```javascript
h.log.setShowLogKey(false);
```

---


### log.isShowLogKey()
- v2.20.0

Verifica se a exibição da chave está ativada



**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


**Example:**

```javascript
if (h.log.isShowLogKey()) {
    //...
}
```

---


### sleep(time)
Pause execution in X milliseconds as specified value

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `time` | _Number_ | Value in milliseconds. Minimum=0, Maximum=60000 |


_Method does not return value_

**Example:**

```javascript
h.sleep(200); //200ms
```

---


### base64Encode(bytes)
Encodes an array of bytes to base64 string

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `bytes` | _Array&lt;byte&gt;_ | array of bytes |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | String in base64 format |


---


### base64Decode(str)
Decodes a string in base64 format

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `str` | _String_ | String in base64 |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;byte&gt;_ | Array of bytes decoded |


---


### md5(value)
MD5 hash in byte array

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;byte&gt;_ | MD5 hash |


---


### md5Str(value)
MD5 hash

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | MD5 hash |


---


### sha256(value)
Hash SHA-256 in byte array

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;byte&gt;_ | SHA-256 hash |


---


### sha256Str(value)
SHA-256 hash

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | SHA-256 hash |


---


### sha512(value)
- v2.20.0

Hash SHA-512 em array de bytes

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;byte&gt;_ | hash SHA-512 |


---


### sha512Str(value)
- v2.20.0

Hash SHA-512

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | hash SHA-512 |


---


### getClipboard()
Get the operating system clipboard text



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Clipboard text |


**Example:**

```javascript
var val = h.getClipboard();
h.log('Clipboard text: ' + val);
```

---


### normalize(str)
Remove accent from string



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | String without accent |


**Example:**

```javascript
var r = h.normalize("ÁÉÍÓÚÇáéíóúç");
h.log('Text with accent removed: ' + r); //AEIOUCaeiouc
```

---


### store(key, value)
Saves a string to disk that can be recovered even after restarting the program. The method is shared with all scripts in the program.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | key to save the string |
| `value` | _String_ | String to be saved |


_Method does not return value_

**Example:**

```javascript
h.store('abc', 'Example');
```

---


### restore(key)
Retrieves a string saved on disk. The method is shared with all scripts in the program.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Previously saved string key |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Returns the saved string or NULL if not found |


**Example:**

```javascript
var r = h.restore('abc');
if (r == null) {
    h.log('Item abc not found');
} else {
    h.log('Item abc: ' + r);
}
```

---


### setGlobal(key, value)
Saves an object in memory that can be retrieved, but is valid only as long as the program is open. The method is shared with all scripts in the program.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Saved object key |
| `value` | _Object_ | Object to be saved in memory |


_Method does not return value_

**Example:**

```javascript
h.setGlobal('xyz', 'Example');
```

---


### getGlobal(key, default = null)
Retrieves an object saved in memory. The method is shared with all scripts in the program.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key of object saved in memory |
| `default` | _Object (optional)_ | Default value if no previously saved value is found |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns the saved object or **default** if not found |


**Example:**

```javascript
var r = h.getGlobal('xyz');
if (r == null) {
    h.log('Item xyz not found');
} else {
    h.log('Item xyz: ' + r);
}

var r2 = h.getGlobal('xyz', 'default value');
h.log('Item xyz: ' + r2);
```

---


### setCache(key, value)
Saves an object in memory that can be retrieved, but is valid only as long as the program is open. The method is only valid for the current script.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Saved object key |
| `value` | _Object_ | Object to be saved in memory |


_Method does not return value_

**Example:**

```javascript
h.setCache('123', 'Example');
```

---


### getCache(key, default = null)
Retrieves an object saved in memory. The method is only valid for the current script.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key of object saved in memory |
| `default` | _Object (optional)_ | Default value if no previously saved value is found |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns the saved object or **default** if not found |


**Example:**

```javascript
var r = h.getCache('123');
if (r == null) {
    h.log('Item 123 not found');
} else {
    h.log('Item 123: ' + r);
}

var r2 = h.getCache('123', 'default value');
h.log('Item 123: ' + r2);
```

---


### random(min, max, keySafeRepeat = null)
Generate a random number

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `min` | _String_ | minimum value |
| `max` | _Object_ | Maximum value |
| `keySafeRepeat` | _Object (optional)_ | Can be used to avoid repeated number drawn in sequence |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Returns a random number from **min** to **max** |


**Example:**

```javascript
var r = h.random(0, 10);
h.log('Random number from 0 to 10: ' + r);
//The number drawn can be repeated
r = h.random(0, 10);
h.log('Random number from 0 to 10: ' + r);

//To avoid repetition:
var r = h.random(0, 10, 'xyz');
h.log('Random number from 0 to 10: ' + r);
//The number drawn will not be repeated
r = h.random(0, 10, 'xyz');
h.log('Random number from 0 to 10: ' + r);

//The do not repeat mechanic also works when the script is run again
//and not just in sequence executions as in the example above
```

---


### startTimer(key = 'default')
Start a timer

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String (optional)_ | Timer key `Default: 'default'` |


_Method does not return value_

**Example:**

```javascript
h.startTimer('xyz');
h.sleep(2000); //2 seconds
var r = h.getTimer('xyz');
h.log('Elapsed time: ' + r); //Like 00:00:02

//is a global method, the value can be used in any other script using the same key
```

---


### getTimer(key = 'default')
Retrieves how much time has elapsed on a timer according to the **key** value. If the timer has not been started, the method will start the timer and return 00:00:00

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String (optional)_ | Timer key `Default: 'default'` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Elapsed time in format HH:MM:SS |


**Example:**

```javascript
var r = h.getTimer('xyz');
h.log('Elapsed time: ' + r);
```

---


### startCountdown(key = 'default', seconds)
- v2.20.0

Inicia uma contagem regressiva

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String (optional)_ | Chave/id da contagem regressiva `Default: 'default'` |
| `seconds` | _Number_ | Duração total da contagem regressiva em segundos |


_Method does not return value_

**Example:**

```javascript
h.startCountdown('xyz', 300);
h.sleep(2000); //2 seconds
var r = h.getCountdown('xyz');
h.log('Tempo restante: ' + r); //provavelmente 00:04:58

//is a global method, the value can be used in any other script using the same key
```

---


### getCountdown(key = 'default')
- v2.20.0

Recupera quanto tempo resta em uma contagem regressiva de acordo com o valor **key**.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String (optional)_ | Chave/id da contagem regressiva `Default: 'default'` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Tempo restante no formato HH:MM:SS (retorna valores negativos após limite de tempo) |


**Example:**

```javascript
var r = h.getCountdown('xyz');
h.log('Tempo restante: ' + r);
```

---


### getPlaylistInfo()
Gets the currently selected playlist in the program



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | Playlist event type. Can be: temporary, service, event |
| `name` | _String_ | Event name |
| `datetime` | _String_ | Item date and time in format: YYYY-MM-DD HH:MM |


**Example:**

```javascript
var r = h.getPlaylistInfo();
h.log(r.name + ' - ' + r.datetime);
switch (r.type) {
    case 'temporary':
        h.log('Playlist is temporary');
        break;
    case 'service':
        h.log('The playlist is from a service');
        break;
    case 'event':
        h.log('The playlist is from an event');
        break;
}
```

---


### getPlayer()
Player class to get information and perform actions on the program's player



**Response:**

| Type  | Description |
| :---: | ------------|
| _[Player](#métodos-player)_ | Player class object |


**Example:**

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


### scriptAction(id, input = null)
Executes the action of an existing **Script** item in the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | item id |
| `input` | _Object (optional)_ | Valores que serão definidos para [Function Input](https://github.com/holyrics/Scripts/blob/main/FunctionInput.md) `v2.20.0+` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Returns **false** if the item is not found |


**Example:**

```javascript
var r = h.scriptAction('abcxyz');
if (r) {
    h.log('Action performed');
} else {
    h.log('Item abcxyz not found');
}

var r = h.scriptAction('abcxyz', {
    id_example_1: 'abc',
    id_example_2: 10
});
if (r) {
    h.log('Action performed');
} else {
    h.log('Item abcxyz not found');
}
```

---


### apiAction(id, input = null)
Executes the action of an existing API item in the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | item id |
| `input` | _Object (optional)_ | Valores que serão definidos para [Function Input](https://github.com/holyrics/Scripts/blob/main/FunctionInput.md) `v2.20.0+` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Returns **false** if the item is not found |


**Example:**

```javascript
var r = h.apiAction('abcxyz');
if (r) {
    h.log('Action performed');
} else {
    h.log('Item abcxyz not found');
}

var r = h.apiAction('abcxyz', {
    id_example_1: 'abc',
    id_example_2: 10
});
if (r) {
    h.log('Action performed');
} else {
    h.log('Item abcxyz not found');
}
```

---


### apiRequest(id, raw)
Executes a request to the associated receiver and returns the receiver's response.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | receiver id |
| `raw` | _Object_ | requisition data |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Request return or NULL for error/timeout |


**Example:**

```javascript
//It is possible to make a request directly to a receiver created
//For example:
//Assuming you have a receiver created to communicate with OBS Studio via websocket and the receiver ID is 'abcyxz'
//you can make a request as in the example below
var r = h.apiRequest('abcxyz', {
    'request-type': 'GetSourceActive',
    'sourceName': 'example'
});
h.log('Requisition response: ' + r);
var obj = JSON.parse(r);
if (obj.sourceActive) {
    h.log('The example source is active');
} else {
    h.log('The example source is not active');
}
```

---


### getApiRequestLastError()
- v2.19.0

Returns the error of the last apiRequest request performed.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Last request error or NULL if no error |


---


### apiRequestAsync(id, raw, callback = null)
- v2.19.0

Executes a request to the associated receiver asynchronously. The result can be accessed by creating an anonymous function as a callback.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | receiver id |
| `raw` | _Object_ | requisition data |
| `callback` | _Function (optional)_ | anonymous function used as request callback. function(response, error){} |


_Method does not return value_

**Example:**

```javascript
//works like apiRequest, but asynchronously
//
//wait for the return, it may take a while
//the next line is executed only when the request is completed
var r = h.apiRequest('abcxyz', {
    'request-type': 'GetSceneList'
});
//next line

//do not wait for the return
//the next line is executed right after
h.apiRequestAsync('abcxyz', {
    'request-type': 'GetSceneList'
}, function (response, error) {
    //request callback
});
//next line
```

---


### setTimeout(function, timeout)
- v2.19.0

Runs a function after a few milliseconds.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `function` | _Function_ | Function that will be executed |
| `timeout` | _Number_ | Time in milliseconds to wait until execution |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Returns the task ID. You can use the ID to cancel the run. |


**Example:**

```javascript
var id = h.setTimeout(function () {
    //task that will run in 60 seconds
}, 60000);
```

---


### clearTimeout(id)
- v2.19.0

Cancels previously scheduled function execution.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _Function_ | ID returned from method **setTimeout** |


_Method does not return value_

**Example:**

```javascript
var id = h.setTimeout(function () {
    //task that will run in 60 seconds
}, 60000);

//cancel task execution
h.clearTimeout(id);
```

---


### setInterval(function, timeout)
- v2.19.0

Runs a function every X milliseconds. Use **clearInterval** to stop execution.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `function` | _Function_ | Function that will be executed |
| `timeout` | _Number_ | Interval in milliseconds between each run |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Returns the task ID. You can use the ID to stop the execution. |


**Example:**

```javascript
var id = h.setInterval(function () {
    //task that will run every 15 seconds
}, 15000);
```

---


### clearInterval(id)
- v2.19.0

Cancels previously scheduled function execution.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _Function_ | ID returned from method **setInterval** |


_Method does not return value_

**Example:**

```javascript
var id = h.setInterval(function () {
    //task that will run every 15 seconds
}, 15000);

//stop execution
h.clearInterval(id);
```

---


### getHostname()
- v2.19.0

Returns the device name.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Device name |


---


### getRuntimeEnvironment()
### getRE()
- v2.19.0

Returns the name of the currently defined runtime environment in the program settings.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Runtime environment name |


---


### setRuntimeEnvironment(name)
### setRE(name)
- v2.19.0

Change the current runtime environment.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Runtime environment name |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Return **true** or **item not found** |


---


### isRuntimeEnvironment(name)
### isRE(name)
- v2.19.0

Checks whether the current execution environment is the same as the one passed by parameter.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Runtime environment name |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Return **true** or **false** |


---


### getVersion()
- v2.20.0

Retorna a versão atual do programa.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Versão no formato: X.Y.Z |


**Example:**

```javascript
if (h.getVersion() == "2.20.0") {
    //...
}
```

---


### isMinimumVersion(version)
### isMinVersion(version)
- v2.20.0

Verifica se a versão do programa é igual ou superior ao informado por parâmetro.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Versão no formato: X.Y.Z |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


**Example:**

```javascript
if (h.isMinimumVersion('2.20.0')) {
    //A versão atual é igual ou superior a 2.20.0
}
```

---


### getLanguage()
- v2.20.0

Retorna o idioma atual definido nas configurações do programa.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Idioma no formato ISO 639 two-letter |


**Example:**

```javascript
switch (h.getLanguage()) {
    case 'en':
        //...
        break;
    case 'pt':
        //...
        break;
    case 'es':
        //...
        break;
    default:
        //...
        break;
}
```

---


### isLanguage(language)
- v2.20.0

Verifica se o idioma atual definido nas configurações do programa é igual ao valor passado por parâmetro.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `language` | _String_ | Idioma no formato ISO 639 two-letter |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


**Example:**

```javascript
if (h.isLanguage('pt')) {
    //...
}
```

---


### getUITheme()
- v2.20.0

Retorna o tema atual da interface do programa.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Um dos seguintes valores: DEFAULT, DARK_SOFT, DARK_MEDIUM, DARK_STRONG |


**Example:**

```javascript
if (h.getUITheme() == 'DEFAULT') {
    //...
}
```

---


### isUITheme(value)
- v2.20.0

Verifica se o tema atual atual da interface é igual ao valor passado por parâmetro.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Theme name |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


**Example:**

```javascript
if (h.isUITheme('DARK_STRONG')) {
    //...
}
```

---


### format.secondsToHMS(seconds, separator = ':')
### secToHMS(seconds, separator)
- v2.20.0

Formatar uma quantidade de segundos como hora|minuto|segundo.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `seconds` | _Number_ | Quantidade total de segundos |
| `separator` | _String (optional)_ | Separador `Default: ':'` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Valor formatado |


**Example:**

```javascript
var r = h.format.secondsToHMS(3905);
h.log(r);
//output:
//01:05:05

var r = h.format.secondsToHMS(3905, ',');
h.log(r);
//output:
//01,05,05
//
```

---


### format.secondsToMS(seconds, separator = ':')
### secToMS(seconds, separator)
- v2.20.0

Formatar uma quantidade de segundos como minuto|segundo.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `seconds` | _Number_ | Quantidade total de segundos |
| `separator` | _String (optional)_ | Separador `Default: ':'` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Valor formatado |


**Example:**

```javascript
var r = h.format.secondsToMS(305);
h.log(r);
//output:
//00:05:05

var r = h.format.secondsToMS(305, ',');
h.log(r);
//output:
//00,05,05
```

---


### format.minutesToHM(minutes, separator = ':')
- v2.20.0

Formatar uma quantidade de minutos como hora|minuto.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `minutes` | _Number_ | Quantidade total de minutos |
| `separator` | _String (optional)_ | Separador `Default: ':'` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Valor formatado |


**Example:**

```javascript
var r = h.format.minutesToHM(90);
h.log(r);
//output:
//01:30

var r = h.format.minutesToHM(90, ',');
h.log(r);
//output:
//01,30
```

---


### date.getSecondOfDay()
- v2.20.0

Retorna a quantidade total de segundos do dia (hour * 3600 + minute * 60 + second)



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ |  |


**Example:**

```javascript
var r = h.date.getSecondOfDay();
//00:00:00 = 0
//23:59:59 = 86399
```

---


# Methods HLY 


All requests for hly(...) methods return a default object:
| Name | Type  | Description |
| ---- | :---: | ------------|
| `status` | _String_ | It might be *'ok'* or *'error'* |
| `error` | _String (optional)_ | Error message if status equals *error* |
| `data` | _Object (optional)_ | Response content if *status* equals *ok* |


---


### hly('GetLyrics', input)
### hly('GetSong', input)
Returns a song.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Song ID |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _[Lyrics](#lyrics)_ | Music or NULL if not found |


**Example:**

```javascript
var r = h.hly('GetLyrics', {id: '123'});
if (r.data == null) {
    h.log('Item 123 not found');
} else {
    h.log('Item 123:');
    h.log(r.data);
}
```

---


### hly('SearchLyrics', input)
### hly('SearchSong', input)
Performs a search in the user's lyrics list

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _String_ | Filter |
| `input.text` | _String_ | Text to be searched |
| `input.title` | _Boolean (optional)_ |  `Default: true` |
| `input.artist` | _Boolean (optional)_ |  `Default: true` |
| `input.note` | _Boolean (optional)_ |  `Default: true` |
| `input.lyrics` | _Boolean (optional)_ |  `Default: false` |
| `input.group` | _String (optional)_ |  |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Lyrics](#lyrics)&gt;_ |  |


**Example:**

```javascript
var r = h.hly('SearchLyrics', {
    text: 'example',
    lyrics: true
});
if (r.data.length == 0) {
    h.log("No results found");
} else {
    for (var i = 0; i < r.data.length; i++) {
        var m = r.data[i];
        h.log(m.title);
    }
}
```

---


### hly('ShowLyrics', input)
### hly('ShowSong', input)
Starts a lyric show.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowLyrics', {id: '123'});

//search for a song and execute the first result found
var r = h.hly('SearchLyrics', {
    text: 'song title'
});
if (r.data.length == 0) {
    h.log("Music not found");
} else {
    h.hly('ShowLyrics', {id: r.data[0].id});
}

//Alternate calls
h.showLyrics('123');
h.showSong('123');
```

---


### hly('ShowText', input)
Starts a presentation of a text tab item.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowText', {id: 'abc'});

//Alternate call
h.showText('abc');
```

---


### hly('ShowVerse', input)
Starts a Bible verse presentation.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | **id**, **ids** or **references** |
| `input.id` | _String (optional)_ | To display a verse. Item ID in BBCCCVVV format.<br/>Example: '19023001' (book 19, chapter 023, verse 001) |
| `input.ids` | _Array&lt;String&gt; (optional)_ | To display a list of verses. List with the ID of each verse.<br/>Example: ['19023001', '43003016', '45012002'] |
| `input.references` | _String (optional)_ | References. Example: **John 3:16** or **Rm 12:2** or **Gn 1:1-3 Sl 23.1** |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowVerse', {id: '19023001'});

h.hly('ShowVerse', {ids: ['19023001', '43003016', '45012002']});

h.hly('ShowVerse', {references: 'John 3:16'});

h.hly('ShowVerse', {references: 'Rm 12:2  Gn 1:1-3  Sl 23'});

//Alternate call
h.showVerse('Rm 12:2  Gn 1:1-3  Sl 23');
```

---


### hly('GetAudios', input)
### hly('GetVideos', input)
### hly('GetImages', input)
- v2.19.0

Returns the file list of the respective tab: audio, video, image

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.folder` | _String (optional)_ | Subfolder name to list files |
| `input.filter` | _String (optional)_ | Filter files by name |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.name` | _String_ | Item name |
| `data.*.isDir` | _Boolean_ | Return **true** if it's a folder or **false** if it's a file. |


**Example:**

```javascript
var r = h.hly('GetAudios');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}

var r = h.hly('GetVideos', {folder: 'abc'});

var r = h.hly('GetImages', {filter: 'text'});

var r = h.hly('GetFiles', {
    folder: 'name 1/name 2',
    filter: 'text'
});
```

---


### hly('PlayAudio', input)
Play an audio or a list of audios (folder)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | File or folder name. Example: **file.mp3** or **folder** or **folder/file.mp3** |


_Method does not return value_

**Example:**

```javascript
h.hly('PlayAudio', {file: 'file.mp3'});
h.hly('PlayAudio', {file: 'folder'});
h.hly('PlayAudio', {file: 'folder/file.mp3'});

//Alternate call
h.playAudio('file.mp3');
```

---


### hly('PlayVideo', input)
Play a video or a list of videos (folder)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | File or folder name. Example: **file.mp4** or **folder** or **folder/file.mp4** |


_Method does not return value_

**Example:**

```javascript
h.hly('PlayVideo', {file: 'file.mp4'});
h.hly('PlayVideo', {file: 'folder'});
h.hly('PlayVideo', {file: 'folder/file.mp4'});

//Alternate call
h.playVideo('file.mp4');
```

---


### hly('ShowImage', input)
Displays an image or a list of images (folder)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | File or folder name. Example: **file.jpg** or **folder** or **folder/file.jpg** |
| `input.automatic` | _[Automatic](#automatic-presentation) (optional)_ | If informed, the presentation of the items will be automatic |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowImage', {file: 'file.jpg'});
h.hly('ShowImage', {file: 'folder'});
h.hly('ShowImage', {file: 'folder/file.jpg'});

h.hly('ShowImage', {
    file: 'folder',
    automatic: {
        seconds: 5,
        repeat: true
    }
});

//Alternate call
h.showImage('file.jpg');
```

---


### hly('ShowAnnouncement', input)
Displays an announcement or a list of announcements

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Announcement ID. Can be **all** to display all |
| `input.ids` | _Array&lt;String&gt; (optional)_ | List with the ID of each announcement |
| `input.name` | _String (optional)_ | Announcement name |
| `input.names` | _Array&lt;String&gt; (optional)_ | List with the name of each announcement |
| `input.automatic` | _[Automatic](#automatic-presentation) (optional)_ | If informed, the presentation of the items will be automatic |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowAnnouncement', {id: '123'});

h.hly('ShowAnnouncement', {
    names: ['Announcement 1', 'Announcement 2', 'Announcement 3'],
    automatic: {
        seconds: 10,
        repeat: true
    }
});
```

---


### hly('GetCustomMessages')
- v2.19.0

List of custom messages



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[CustomMessage](#custom-message)&gt;_ |  |


**Example:**

```javascript
var r = h.hly('GetCustomMessages');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('ShowCustomMessage', input)
- v2.19.0

Display a custom message. Note: A custom message is not displayed directly on the screen. a notification is created in the corner of the screen for the operator to accept and display.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.name` | _String_ | custom message name |
| `input.position_?` | _Object_ | Variable added at the specified position according to the value returned in **variables.*.position** of the CustomMessage class. |
| `input.note` | _String_ | Extra information displayed in popup window for operator |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowCustomMessage', {
    name: 'name',
    position_15: 'Value 1',
    position_28: 'Value 2',
    note: 'Urgently'
});
```

---


### hly('ShowQuickPresentation', input)
Quick display of text

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String_ | Text to be displayed. [Styled Text](#styled-text) from v2.19.0 |
| `input.theme` | _Object (optional)_ | Filter selected theme for display |
| `input.theme.id` | _String (optional)_ | Theme ID |
| `input.theme.name` | _String (optional)_ | Theme name |
| `input.automatic` | _[Automatic](#automatic-presentation) (optional)_ | If informed, the presentation of the items will be automatic |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowQuickPresentation', {
    text: "Text to be displayed"
});

h.hly('ShowQuickPresentation', {
    text: "Slide 1\n\nSlide 2\n\nSlide 3",
    theme: {
        name: "Theme 3"
    },
    automatic: {
        seconds: 5,
        repeat: true
    }
});
```

---


### hly('ShowCountdown', input)
- v2.20.0

Exibir uma contagem regressiva na tela público

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.time` | _String_ | HH:MM ou MM:SS |
| `input.exact_time` | _Boolean (optional)_ | Se **true**, `time` deve ser HH:MM (hora e minuto exato). Se **false**, `time` deve ser MM:SS (quantidade de minutos e segundos) `Default: false` |
| `input.text_before` | _String (optional)_ | Texto exibido na parte superior da contagem regressiva |
| `input.text_after` | _String (optional)_ | Texto exibido na parte inferior da contagem regressiva |
| `input.zero_fill` | _Boolean (optional)_ | Preencher o campo 'minuto' com zero à esquerda `Default: false` |
| `input.countdown_relative_size` | _Number (optional)_ | Tamanho relativo da contagem regressiva `Default: 250` |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowCountdown', {
    time: '05:00', //5 minutes
    zero_fill: true
});

h.hly('ShowCountdown', {
    time: '19:00', //19:00
    exact_time: true,
    text_after: 'Example'
});
```

---


### hly('ShowQuiz', input)
- v2.20.0

Iniciar uma apresentação no formato múltipla escolha

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.questions` | _Array&lt;[QuizQuestion](#quiz-question)&gt;_ | Questões para exibir |
| `input.settings` | _[QuizSettings](#quiz-settings)_ | Configurações |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowQuiz', {
    questions: [
        {
            title: 'Example 1',
            alternatives: [
                'Example 1a',
                'Example 2a',
                'Example 3a',
                'Example 4a'
            ],
            correct_alternative_number: 2
        }, {
            title: 'Example 2',
            alternatives: [
                'Example 1b',
                'Example 2b',
                'Example 3b',
                'Example 4b'
            ],
            correct_alternative_number: 2
        }
    ],
    settings: {
        display_alternatives_one_by_one: false,
        alternative_char_type: 'number'
    }
});
```

---


### hly('QuizAction', input)
- v2.20.0

Executar uma ação em uma apresentação de múltipla escolha

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.action` | _String (optional)_ | Um dos seguintes valores: `previous_slide`  `next_slide`  `previous_question`  `next_question`  `show_result`  `close` |
| `input.hide_alternative` | _Number (optional)_ | Ocultar uma alternativa. Começa em 1 |
| `input.select_alternative` | _Number (optional)_ | Selecionar uma alternativa. Começa em 1 |
| `input.countdown` | _Number (optional)_ | Iniciar uma contagem regressiva. [1-120] |


_Method does not return value_

**Example:**

```javascript
h.hly('QuizAction', { 
    action: 'next_slide'
});

h.hly('QuizAction', {
    hide_alternative: 3
});

h.hly('QuizAction', {
    select_alternative: 1
});
```

---


### hly('PlayAutomaticPresentation', input)
### hly('PlayAP', input)
- v2.19.0

Play an automatic presentation item

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | File name. Example: **file.ap** |
| `input.theme` | _Object (optional)_ | Filter selected theme for display |
| `input.theme.id` | _String (optional)_ | Theme ID |
| `input.theme.name` | _String (optional)_ | Theme name |


_Method does not return value_

**Example:**

```javascript
h.hly('PlayAutomaticPresentation', {file: 'file.ap'});

h.hly('PlayAP', {file: 'file.ap'});

h.hly('PlayAP', {
    file: 'file.ap',
    theme: {
        name: "Theme 3"
    }
});

//Alternate calls
h.playAutomaticPresentation('file.ap');
h.playAP('file.ap');
```

---


### hly('GetAutomaticPresentationPlayerInfo')
### hly('GetAPPlayerInfo')
- v2.20.0

Retorna as informações da apresentação automática em exibição



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.name` | _String_ | Item name |
| `data.playing` | _Boolean_ | Checks if the player is running |
| `data.time_ms` | _Number_ | Current media time in milliseconds |
| `data.volume` | _Number_ | Current player volume. Minimum=0, Maximum=100 |
| `data.mute` | _Boolean_ | Checks if the **mute** option is enabled |


**Example:**

```javascript
var r = h.hly('GetAutomaticPresentationPlayerInfo');
if (r.data.name == 'abc') {
    //...
}
```

---


### hly('AutomaticPresentationPlayerAction', input)
### hly('APPlayerAction', input)
- v2.20.0

Perform actions in the player

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.action` | _String (optional)_ | Name of the action that will be performed on the player. play, pause, stop |
| `input.volume` | _Number (optional)_ | Change the volume of the player. Minimum=0, Maximum=100 |
| `input.mute` | _Boolean (optional)_ | Change the **mute** option |
| `input.time_ms` | _Boolean (optional)_ | Alterar o tempo atual da mídia em milissegundos |


_Method does not return value_

**Example:**

```javascript
h.hly('AutomaticPresentationPlayerAction', {
    action: 'play',
    volume: 80
});
```

---


### hly('GetMediaPlayerInfo')
Returns player information



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.name` | _String_ | Name of current media in player |
| `data.path` | _String_ | Full path of media in player |
| `data.playing` | _Boolean_ | Checks if the player is running |
| `data.duration_ms` | _Number_ | Total time in milliseconds |
| `data.time_ms` | _Number_ | Current media time in milliseconds |
| `data.time_elapsed` | _String_ | Elapsed time in format HH:MM:SS |
| `data.time_remaining` | _String_ | Remaining time in format HH:MM:SS |
| `data.volume` | _Number_ | Current player volume. Minimum=0, Maximum=100 |
| `data.mute` | _Boolean_ | Checks if the **mute** option is enabled |
| `data.repeat` | _Boolean_ | Checks if the **repeat** option is enabled |
| `data.execute_single` | _Boolean_ | Checks if the player is set to play only the current list item |
| `data.shuffle` | _Boolean_ | Checks if the **random** option is enabled |
| `data.fullscreen` | _Boolean_ | Checks if the **full screen** option is enabled |


**Example:**

```javascript
var r = h.hly('GetMediaPlayerInfo');
if (r.data.playing) {
    h.log('The player is running');
} else {
    h.log('The player is not running');
}
```

---


### hly('MediaPlayerAction', input)
- v2.19.0

Perform actions in the player

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.action` | _String (optional)_ | Name of the action that will be performed on the player. play, pause, stop, next, previous |
| `input.volume` | _Number (optional)_ | Change the volume of the player. Minimum=0, Maximum=100 |
| `input.mute` | _Boolean (optional)_ | Change the **mute** option |
| `input.repeat` | _Boolean (optional)_ | Change the **repeat** option |
| `input.shuffle` | _Boolean (optional)_ | Change the **random** option |
| `input.execute_single` | _Boolean (optional)_ | Change player setting to play only current list item |
| `input.fullscreen` | _Boolean (optional)_ | Change player **full screen** option |
| `input.time_ms` | _Boolean (optional)_ | Alterar o tempo atual da mídia em milissegundos `v2.20.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('MediaPlayerAction', {
    mute: false,
    repeat: true,
    volume: 80,
    action: 'play'
});

//change volume
h.hly('MediaPlayerAction', {volume: 80});

//mute
h.hly('MediaPlayerAction', {mute: true});

//stop current execution
h.hly('MediaPlayerAction', {action: 'stop'});
```

---


### hly('GetLyricsPlaylist')
### hly('GetSongPlaylist')
Lyrics playlist



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Lyrics](#lyrics)&gt;_ |  |


**Example:**

```javascript
var r = h.hly('GetLyricsPlaylist');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].title);
}
```

---


### hly('AddLyricsToPlaylist', input)
### hly('AddSongsToPlaylist', input)
Add song lyrics to playlist

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Lyrics ID |
| `input.ids` | _Array&lt;String&gt; (optional)_ | List with id of each lyics |
| `input.index` | _Number (optional)_ | Position in the list where the item will be added (starts at zero). Items are added to the end of the list by default. `Default: -1` |
| `input.media_playlist` | _Boolean (optional)_ | Add the lyrics to the media playlist `Default: false` |


_Method does not return value_

**Example:**

```javascript
h.hly('AddLyricsToPlaylist', {id: '123'});

h.hly('AddLyricsToPlaylist', {ids: ['123', '456']});

h.hly('AddLyricsToPlaylist', {
    ids: ['123', '456'],
    index: 3
});

h.hly('AddLyricsToPlaylist', {
    ids: ['123', '456'],
    index: 3,
    media_playlist: true
});
```

---


### hly('RemoveFromLyricsPlaylist', input)
### hly('RemoveFromSongPlaylist', input)
Remove lyrics from playlist

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Lyrics ID |
| `input.ids` | _Array&lt;String&gt; (optional)_ | List with id of each lyics |
| `input.index` | _Number (optional)_ | Position of the item in the list to be removed (starts at zero). |
| `input.indexes` | _Array&lt;Number&gt; (optional)_ | List with the position of each item in the list that will be removed. (Starts at zero) |


_Method does not return value_

**Example:**

```javascript
h.hly('RemoveFromLyricsPlaylist', {id: '123'});

h.hly('RemoveFromLyricsPlaylist', {ids: ['123', '456']});

h.hly('RemoveFromLyricsPlaylist', {index: 3});

h.hly('RemoveFromLyricsPlaylist', {indexes: [3, 4, 5]});
```

---


### hly('GetMediaPlaylist')
Media playlist



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Item](#item)&gt;_ |  |


**Example:**

```javascript
var r = h.hly('GetMediaPlaylist');
for (var i = 0; i < r.data.length; i++) {
    var item = r.data[i];
    h.log(item.type + ": " + item.name);
}
```

---


### hly('MediaPlaylistAction', input)
Play a media playlist item

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |


_Method does not return value_

**Example:**

```javascript
h.hly('MediaPlaylistAction', {id: 'abc'});

//Alternate calls
h.mediaPlaylistAction('abc');
h.mplAction('abc');
```

---


### hly('AddToPlaylist', input)
- v2.20.0

Adicionar itens à lista de reprodução de mídias

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.items` | _Array&lt;[AddItem](#additem)&gt;_ | Lista com os itens que serão adicionados |
| `input.index` | _Number (optional)_ | Position in the list where the item will be added (starts at zero). Items are added to the end of the list by default. `Default: -1` |
| `input.ignore_duplicates` | _Boolean (optional)_ | Não duplicar itens ao adicionar novos itens, ou seja, não adiciona um item se ele já estiver na lista. `Default: false` |


_Method does not return value_

**Example:**

```javascript
var r = h.hly('AddToPlaylist', {
    items: [
        {
            type: 'song',
            id: 123456
        }, {
            type: 'song',
            id: 12345678
        }
    ],
    index: 3,
    ignore_duplicates: true
});

if (r.status != 'ok') {
    h.log(r.error);
}

var items = [
    {
        type: 'title',
        name: 'Título',
        background_color: "000080"
    }, {
        type: 'song',
        id: 12345678
    }, {
        type: 'verse',
        id: '19023001'
    }, {
        type: 'verse',
        ids: ['19023001', '43003016']
    }, {
        type: 'verse',
        references: 'Sl 23.1 Rm 12:2'
    }, {
        type: 'text',
        id: 'abcxyz'
    }, {
        type: 'audio',
        name: 'example.mp3'
    }, {
        type: 'video',
        name: 'example.mp4'
    }, {
        type: 'image',
        name: 'example.jpg'
    }, {
        type: 'automatic_presentation',
        name: 'example.ap'
    }, {
        type: 'title',
        name: 'Título 2'
    }, {
        type: 'announcement',
        id: 12345678
    }, {
        type: 'announcement',
        ids: [123, 456]
    }, {
        type: 'announcement',
        name: 'example'
    }, {
        type: 'announcement',
        names: ['example 2', 'example 3']
    }, {
        type: 'announcement',
        id: 'all',
        automatic: {
            seconds: 8,
            repeat: false
        }
    }, {
        type: 'title',
        name: 'Título 3'
    }, {
        type: 'countdown',
        time: '03:15'
    }, {
        type: 'countdown_cp',
        minutes: 15,
        stop_at_zero: true
    }, {
        type: 'cp_text',
        text: 'example'
    }, {
        type: 'script',
        id: 'abcxyz'
    }, {
        type: 'api',
        id: 'abcxyz'
    }
];

var r = h.hly('AddToPlaylist', {
    items: items
});
if (r.status != 'ok') {
    h.log(r.error);
}
```

---


### hly('RemoveFromMediaPlaylist', input)
Remove items from media playlist

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Item ID |
| `input.ids` | _Array&lt;String&gt; (optional)_ | List with id of each item |
| `input.index` | _Number (optional)_ | Position of the item in the list to be removed (starts at zero). |
| `input.indexes` | _Array&lt;Number&gt; (optional)_ | List with the position of each item in the list that will be removed. (Starts at zero) |


_Method does not return value_

**Example:**

```javascript
h.hly('RemoveFromMediaPlaylist', {id: 'abc'});

h.hly('RemoveFromMediaPlaylist', {ids: ['abc', 'xyz']});

h.hly('RemoveFromMediaPlaylist', {index: 3});

h.hly('RemoveFromMediaPlaylist', {indexes: [3, 4, 5]});
```

---


### hly('GetFavorites')
Favorites bar items



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Favorite Item](#favorite-item)&gt;_ |  |


**Example:**

```javascript
var r = h.hly('GetFavorites');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('FavoriteAction', input)
Execute an item from the bookmarks bar

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |


_Method does not return value_

**Example:**

```javascript
h.hly('FavoriteAction', {id: 'abc'});

//Alternate calls
h.favoriteAction('abc');
h.favAction('abc');
```

---


### hly('ApiAction', input)
- v2.19.0

Executes the action of an existing API item in the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |


_Method does not return value_

**Example:**

```javascript
var r = h.hly('ApiAction', {id: 'abcxyz'});

if (r.status == 'ok') {
    h.log('Action performed');
} else {
    h.log('Error: ' + r.error);
}
```

---


### hly('ScriptAction', input)
- v2.19.0

Executes the action of an existing **Script** item in the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |


_Method does not return value_

**Example:**

```javascript
var r = h.hly('ScriptAction', {id: 'abcxyz'});

if (r.status == 'ok') {
    h.log('Action performed');
} else {
    h.log('Error: ' + r.error);
}
```

---


### hly('ApiRequest', input)
- v2.19.0

Executes a request to the associated receiver and returns the receiver's response.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | receiver id |
| `input.raw` | _Object_ | requisition data |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Request return or NULL for error/timeout |


**Example:**

```javascript
//It is possible to make a request directly to a receiver created
//For example:
//Assuming you have a receiver created to communicate with OBS Studio via websocket and the receiver ID is 'abcyxz'
//you can make a request as in the example below
var r = h.hly('ApiRequest', {
    id: 'abcxyz',
    raw: {
        'request-type': 'GetSourceActive',
        'sourceName': 'example'
    }
});
if (r.status == 'ok') {
    h.log('Requisition response: ' + r.data);
    var obj = JSON.parse(r.data);
    if (obj.sourceActive) {
        h.log('The example source is active');
    } else {
        h.log('The example source is not active');
    }
} else {
    h.log('Error: ' + r.error);
}
```

---


### hly('GetCurrentPresentation')
- v2.19.0

Item currently being presented or **null** if no presentation is being displayed



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.id` | _String_ | Item ID |
| `data.type` | _String_ | Tipo do item. Pode ser: `title`  `song`  `verse`  `text`  `audio`  `video`  `image`  `announcement`  `automatic_presentation`  `countdown`  `countdown_cp`  `cp_text`  `api`  `script` |
| `data.name` | _String_ | Item name |
| `data.slide_number` | _Number_ | Começa em 1 `v2.20.0+` |
| `data.total_slides` | _Number_ | Total de slides `v2.20.0+` |
| `data.slide_type` | _String_ | Um dos seguintes valores: `default`  `wallpaper`  `blank`  `black`  `final_slide` `v2.20.0+` |


**Example:**

```javascript
var r = h.hly('GetCurrentPresentation');
if (r.data == null) {
    //there is no presentation currently showing
}

switch (r.data.type) {
    case 'song':
        //a song being performed
        break;
    case 'verse':
        //a verse being presented
        break;
}
```

---


### hly('CloseCurrentPresentation')
End current presentation



_Method does not return value_

**Example:**

```javascript
h.hly('CloseCurrentPresentation');
```

---


### hly('GetF8')
### hly('GetF9')
### hly('GetF10')
- v2.19.0

Returns the current state of the respective option **F8 (wallpaper), F9 (empty screen) or F10 (black screen)**



**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | **true** or **false** |


**Example:**

```javascript
var r = h.hly('GetF8');
h.log('F8: ' + r.data);

var r = h.hly('GetF9');
h.log('F9: ' + r.data);

var r = h.hly('GetF10');
h.log('F10: ' + r.data);
```

---


### hly('SetF8', input)
### hly('SetF9', input)
### hly('SetF10', input)
- v2.19.0

Changes the current state of the respective option **F8 (wallpaper), F9 (empty screen) or F10 (black screen)**

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.enable` | _Boolean_ | **true** or **false** |


_Method does not return value_

**Example:**

```javascript
h.hly('SetF8', {enable: true});

h.hly('SetF9', {enable: false});

h.hly('SetF10', {enable: true});
```

---


### hly('ToggleF8')
### hly('ToggleF9')
### hly('ToggleF10')
- v2.19.0

Changes the current state of the respective option **F8 (wallpaper), F9 (empty screen) or F10 (black screen)**



_Method does not return value_

**Example:**

```javascript
h.hly('ToggleF8');

h.hly('ToggleF9');

h.hly('ToggleF10');
```

---


### hly('ActionNext')
- v2.19.0

Performs a **next** command on the current presentation



_Method does not return value_

---


### hly('ActionPrevious')
- v2.19.0

Performs a **back** command on the current presentation



_Method does not return value_

---


### hly('ActionGoToIndex', input)
- v2.19.0

Changes the slide in view from the slide index

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.index` | _Number_ | Slide index in presentation (starts at zero) |


_Method does not return value_

**Example:**

```javascript
h.hly('ActionGoToIndex', {index: 3});
```

---


### hly('ActionGoToSlideDescription', input)
- v2.19.0

Changes the slide in view from the name of the slide description

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.name` | _String_ | Slide description name |


_Method does not return value_

**Example:**

```javascript
h.hly('ActionGoToSlideDescription', {name: 'Verse 1'});
```

---


### hly('GetCurrentBackground')
Returns the background of the currently displayed presentation.



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _[Background](#background)_ | Current background or NULL if no presentation is displayed |


**Example:**

```javascript
var r = h.hly('GetCurrentBackground');
if (r.data != null) {
    h.log('Current background ID: ' + r.data.id);
} else {
    h.log('There is no presentation on display');
}
```

---


### hly('GetBackgrounds', input)
List of themes and backgrounds

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object (optional)_ | Filter |
| `input.type` | _String (optional)_ | It might be: theme, my_video, my_image, video, image |
| `input.tag` | _String (optional)_ |  |
| `input.tags` | _Array&lt;String&gt; (optional)_ |  |
| `input.intersection` | _Boolean (optional)_ | If the **input.tags** field is populated with multiple items, the **input.intersection** option defines the type of junction. If **true**, the filter will only return items that contain **all** the informed tags, if **false**, the filter will return the items that have at least one tag of the informed tags `Default: false` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Background](#background)&gt;_ |  |


**Example:**

```javascript
//all
var r = h.hly('GetBackgrounds', {});
for (var i = 0; i < r.data.length; i++) {
    var bg = r.data[i];
    h.log(bg.type + ": " + bg.name);
}

//only "My Videos" and tagged 'water' AND 'blue'
r = h.hly('GetBackgrounds', {
    type: 'my_video',
    tags: ['water', 'blue'],
    intersection: true
});
for (var i = 0; i < r.data.length; i++) {
    var bg = r.data[i];
    h.log(bg.name);
}
```

---


### hly('SetCurrentBackground', input)
Changes the background (or theme) of the current presentation. If more than one item is found according to the filters, random item will be chosen from the list

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object (optional)_ | Filter |
| `input.id` | _String (optional)_ | Theme or background ID |
| `input.name` | _String (optional)_ | Theme name or background |
| `input.type` | _String (optional)_ | It might be: theme, my_video, my_image, video, image |
| `input.tag` | _String (optional)_ |  |
| `input.tags` | _Array&lt;String&gt; (optional)_ |  |
| `input.intersection` | _Boolean (optional)_ | If the **input.tags** field is populated with multiple items, the **input.intersection** option defines the type of junction. If **true**, the filter will only return items that contain **all** the informed tags, if **false**, the filter will return the items that have at least one tag of the informed tags `Default: false` |


_Method does not return value_

**Example:**

```javascript
h.hly('SetCurrentBackground', {id: 'abc'});

h.hly('SetCurrentBackground', {name: 'xyz'});

//a video that is defined with the tag 'water'
h.hly('SetCurrentBackground', {
    type: 'my_video',
    tag: 'water'
});

//a video that is tagged 'water' OR tagged 'blue'
h.hly('SetCurrentBackground', {
    type: 'my_video',
    tags: ['water', 'blue']
});

//a video that is defined with the tag 'water' AND the tag 'blue'
h.hly('SetCurrentBackground', {
    type: 'my_video',
    tags: ['water', 'blue'],
    intersection: true
});
```

---


### hly('GetColorMap', input)
- v2.20.0

Retorna as informações de cor predominante de um respectivo tipo de item<br/>O array retornado contém 8 índices, e cada índice corresponde ao trecho conforme imagem de exemplo a seguir.<br/> <br/>![Color Map Example](https://holyrics.com.br/images/color_map_item_example.png)<br/>

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.type` | _String_ | Um dos seguintes valores:<br/>**background** - um item de tema ou plano de fundo<br/>**presentation** - apresentação atual em exibição<br/>**image** - uma imagem da aba 'imagens'<br/>**video** - um vídeo da aba 'vídeos'<br/>**printscreen** - um printscreen atual de uma tela do sistema<br/> |
| `input.source` | _Object (optional)_ | O item de acordo com o tipo informado:<br/>**background** - ID do tema ou plano de fundo<br/>**presentation** - não é necessário informar um valor, a apresentação da tela público será retornada<br/>**image** - o nome do arquivo da aba 'imagens'<br/>**video** - o nome do arquivo da aba 'vídeos'<br/>**printscreen** `opcional` -  o nome da tela (public, screen_2, screen_3, ...); o padrão é `public`<br/> |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.hex` | _String_ | Cor no formato hexadecimal |
| `data.*.red` | _Number_ | Vermelho  0-255 |
| `data.*.green` | _Number_ | Verde  0-255 |
| `data.*.blue` | _Number_ | Azul  0-255 |


**Example:**

```javascript
var r = h.hly('GetColorMap', {
    type: 'background',
    source: 12345678
});

if (r.data[0].red >= 200) {
    //red >= 200
}

var r = h.hly('GetColorMap', {
    type: 'presentation'
});

var r = h.hly('GetColorMap', {
    type: 'image',
    source: 'example.png'
});

var r = h.hly('GetColorMap', {
    type: 'video',
    source: 'dir/video.mp4'
});

var r = h.hly('GetColorMap', {
    type: 'printscreen'
});

var r = h.hly('GetColorMap', {
    type: 'printscreen',
    source: 'screen_2'
});

//Alternate calls
var arr = h.getColorMap('presentation');
var arr = h.getColorMap('video', 'filename.mp4');
```

---


### hly('SetAlert', input)
Change alert message settings

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String (optional)_ | Change alert text |
| `input.show` | _Boolean (optional)_ | Show/hide the alert |


_Method does not return value_

**Example:**

```javascript
h.hly('SetAlert', {
    text: "alert text",
    show: true
});

//remove
h.hly('SetAlert', {show: false});
```

---


### hly('GetCurrentSchedule')
Current schedule (selected in the main program window)



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _[Schedule](#schedule)_ |  |


**Example:**

```javascript
var r = h.hly('GetCurrentSchedule');
var s = r.data[0];
h.log(s.datetime);
h.log(s.name);
h.log(s.lyrics_playlist);
h.log(s.media_playlist);
```

---


### hly('GetSchedules', input)
Returns the schedule list for a specific month

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.month` | _Number_ | Month (1-12) |
| `input.year` | _Number_ | Year |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Schedule](#schedule)&gt;_ |  |


**Example:**

```javascript
var r = h.hly('GetSchedules', {
    month: 8,
    year: 2022
});
for (var i = 0; i < r.data.length; i++) {
    var s = r.data[i];
    h.log(s.datetime);
    h.log(s.name);
    h.log(s.lyrics_playlist);
    h.log(s.media_playlist);
}
```

---


### hly('GetSavedPlaylists')
- v2.19.0

Returns saved playlists



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.id` | _String_ | Item ID |
| `data.*.name` | _String_ | Item name |
| `data.*.items` | _Array&lt;[Item](#item)&gt;_ | Items saved in the list |


**Example:**

```javascript
var r = h.hly('GetSavedPlaylists');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('LoadSavedPlaylist', input)
- v2.19.0

Populates the media list of the currently selected playlist in the program with the given list

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.name` | _String_ | Saved playlist name |


_Method does not return value_

**Example:**

```javascript
var r = h.hly('LoadSavedPlaylist', {name: 'name'});
```

---


### hly('GetHistory', input)
"Music played" history

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Song lyric ID |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;String&gt;_ | Date and time in format: YYYY-MM-DD HH:MM |


**Example:**

```javascript
var r = h.hly('GetHistory', {id: '123'});
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i]);
}
```

---


### hly('GetHistories')
History of all tags for "Music played"



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.music_id` | _String_ | Song ID |
| `data.*.history` | _Array&lt;String&gt;_ | Date and time in format: YYYY-MM-DD HH:MM |


**Example:**

```javascript
var r = h.hly('GetHistories');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].music_id);
    h.log(r.data[i].history);
}
```

---


### hly('GetMembers')
List of members



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Member](#member)&gt;_ |  |


**Example:**

```javascript
var r = h.hly('GetMembers');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetRoles')
List of functions



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Role](#role)&gt;_ |  |


**Example:**

```javascript
var r = h.hly('GetRoles');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetCommunicationPanelInfo')
### hly('GetCPInfo')
### hly('GetCPSettings')
Current communication panel configuration



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.text` | _String_ | Current text |
| `data.show` | _Boolean_ | Whether the current text is displayed |
| `data.display_ahead` | _Boolean_ | Whether the *'display in front of all'* option is enabled |
| `data.alert_text` | _String_ | Current alert text |
| `data.alert_show` | _Boolean_ | Whether the alert display is enabled |
| `data.countdown_show` | _Boolean_ | If a countdown is on display |
| `data.countdown_time` | _Number_ | The current countdown time displayed (in seconds) |
| `data.stopwatch_show` | _Boolean_ | Se um cronômetro está em exibição `v2.20.0+` |
| `data.stopwatch_time` | _Number_ | O tempo atual do cronômetro em exibição (em segundos) `v2.20.0+` |
| `data.theme` | _Number_ | Theme ID `v2.20.0+` |
| `data.countdown_font_relative_size` | _Number_ | Tamanho relativo da contagem regressiva `v2.20.0+` |
| `data.countdown_font_color` | _String_ | Cor da fonte da contagem regressiva `v2.20.0+` |
| `data.stopwatch_font_color` | _String_ | Cor da fonte do cronômetro `v2.20.0+` |
| `data.time_font_color` | _String_ | Cor da fonte da hora `v2.20.0+` |
| `data.display_clock_as_background` | _Boolean_ | Exibir relógio como plano de fundo `v2.20.0+` |
| `data.display_clock_on_alert` | _Boolean_ | Exibir relógio no alerta `v2.20.0+` |
| `data.countdown_display_location` | _String_ | Local de exibição da contagem regressiva ou cronômetro. `FULLSCREEN`  `FULLSCREEN_OR_ALERT`  `ALERT` `v2.20.0+` |
| `data.display_clock_with_countdown_fullscreen` | _Boolean_ | Exibir relógio junto da contagem regressiva ou cronômetro quando exibido em tela cheia `v2.20.0+` |
| `data.display_vlc_player_remaining_time` | _Boolean_ | Exibir tempo restante da mídia em execução no VLC Player `v2.20.0+` |


**Example:**

```javascript
var r = h.hly('GetCommunicationPanelInfo');
if (r.data.countdown_show) {
    h.log("Communication panel countdown is active");
    h.log(r.data.countdown_time + " seconds");
} else {
    h.log("Communication panel countdown is not active");
}
```

---


### hly('SetCommunicationPanelSettings', input)
### hly('SetCPSettings')
- v2.20.0

Alterar configuração atual do painel de comunicação

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String (optional)_ | Current text |
| `input.show` | _Boolean (optional)_ | Exibir o texto atual |
| `input.display_ahead` | _Boolean (optional)_ | Opção *'exibir à frente de tudo'* |
| `input.theme` | _Boolean (optional)_ | ID ou nome do tema padrão |
| `input.alert_text` | _String (optional)_ | Current alert text |
| `input.alert_show` | _Boolean (optional)_ | Ativar a exibição do alerta |
| `input.countdown_font_relative_size` | _Number (optional)_ | Tamanho relativo da contagem regressiva |
| `input.countdown_font_color` | _String (optional)_ | Cor da fonte da contagem regressiva |
| `input.stopwatch_font_color` | _String (optional)_ | Cor da fonte do cronômetro |
| `input.time_font_color` | _String (optional)_ | Cor da fonte da hora |
| `input.display_clock_as_background` | _Boolean (optional)_ | Exibir relógio como plano de fundo |
| `input.display_clock_on_alert` | _Boolean (optional)_ | Exibir relógio no alerta |
| `input.countdown_display_location` | _String (optional)_ | Local de exibição da contagem regressiva ou cronômetro. `FULLSCREEN`  `FULLSCREEN_OR_ALERT`  `ALERT` |
| `input.display_clock_with_countdown_fullscreen` | _Boolean (optional)_ | Exibir relógio junto da contagem regressiva ou cronômetro quando exibido em tela cheia |
| `input.display_vlc_player_remaining_time` | _Boolean (optional)_ | Exibir tempo restante da mídia em execução no VLC Player |


_Method does not return value_

**Example:**

```javascript
var r = h.hly('SetCommunicationPanelSettings', {
    display_clock_as_background: false,
    display_clock_on_alert: true
});
```

---


### hly('StartCountdownCommunicationPanel', input)
### hly('StartCountdownCP', input)
Starts a countdown on the communication panel

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.minutes` | _Number_ | Number of minutes |
| `input.seconds` | _Number_ | Number of seconds |
| `input.yellow_starts_at` | _Number (optional)_ | Value in seconds to define how long the countdown will be yellow from |
| `input.stop_at_zero` | _Boolean (optional)_ | Stop the countdown when it reaches zero `Default: false` |


_Method does not return value_

**Example:**

```javascript
h.hly('StartCountdownCommunicationPanel', {minutes: 3});

h.hly('StartCountdownCommunicationPanel', {
    minutes: 1,
    seconds: 30,
    yellow_starts_at: 30,
    stop_at_zero: true
});
```

---


### hly('StopCountdownCommunicationPanel')
### hly('StopCountdownCP')
Ends current communication panel countdown



_Method does not return value_

**Example:**

```javascript
h.hly('StopCountdownCommunicationPanel');
```

---


### hly('StartTimerCommunicationPanel')
### hly('StartTimerCP', input)
- v2.20.0

Inicia um cronômetro no painel de comunicação



_Method does not return value_

**Example:**

```javascript
h.hly('StartTimerCommunicationPanel');
h.hly('StartTimerCP');
```

---


### hly('StopTimerCommunicationPanel')
### hly('StopTimerCP')
- v2.20.0

Encerra o cronômetro atual do painel de comunicação



_Method does not return value_

**Example:**

```javascript
h.hly('StopTimerCommunicationPanel');
h.hly('StopTimerCP');
```

---


### hly('SetTextCommunicationPanel', input)
### hly('SetTextCP', input)
Change communication panel text

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String (optional)_ | Change the text of the communication panel. [Styled Text](#styled-text) from v2.19.0 |
| `input.show` | _Boolean (optional)_ | Show/hide the text |
| `input.display_ahead` | _Boolean (optional)_ | Change the *'display in front of all'* option |


_Method does not return value_

**Example:**

```javascript
h.hly('SetTextCommunicationPanel', {
    text: "communication panel text",
    show: true,
    display_ahead: true
});

//remove
h.hly('SetTextCommunicationPanel', {show: false});
```

---


### hly('SetAlertCommunicationPanel', input)
### hly('SetAlertCP', input)
Change communication panel alert settings

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String (optional)_ | Change alert text |
| `input.show` | _Boolean (optional)_ | Show/hide the alert |


_Method does not return value_

**Example:**

```javascript
h.hly('SetAlertCommunicationPanel', {
    text: "communication panel alert text",
    show: true
});

//remove
h.hly('SetAlertCommunicationPanel', {show: false});
```

---


### hly('CommunicationPanelCallAttention')
### hly('CPCallAttention')
- v2.20.0

Executa a opção 'chamar atenção' disponível no painel de comunicação



_Method does not return value_

**Example:**

```javascript
h.hly('CommunicationPanelCallAttention');
```

---


### hly('GetWallpaperSettings')
- v2.19.0

Wallpaper settings



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.image_base64` | _String_ | Wallpaper image in base 64 |
| `data.enabled` | _Boolean_ | Show wallpaper |
| `data.fill_color` | _String_ | Color in hexadecimal defined in the **fill** option. |
| `data.extend` | _Boolean_ | Extend wallpaper |
| `data.show_clock` | _Boolean_ | Show clock |


**Example:**

```javascript
var r = h.hly('GetWallpaperSettings');
h.log('Wallpaper enabled: ' + r.data.enabled);
```

---


### hly('SetWallpaperSettings', input)
- v2.19.0

Change wallpaper settings

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String (optional)_ | File location in the **Images** tab |
| `input.enabled` | _Boolean (optional)_ | Show wallpaper |
| `input.fill_color` | _String (optional)_ | Color in hexadecimal defined in the **fill** option. **NULL** to disable |
| `input.extend` | _Boolean (optional)_ | Extend wallpaper |
| `input.show_clock` | _Boolean (optional)_ | Show clock |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Return **true** or a list of errors that occurred |


**Example:**

```javascript
var r = h.hly('SetWallpaperSettings', {
    file: 'image.jpg',
    enabled: true,
    fill_color: '000000'
});
```

---


### hly('GetDisplaySettings')
- v2.19.0

List of display settings for each screen



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[DisplaySettings](#display-settings)&gt;_ |  |


**Example:**

```javascript
var r = h.hly('GetDisplaySettings');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].id);
    h.log(r.data[i].name);
    h.log('');
}
```

---


### hly('SetDisplaySettings', input)
- v2.19.0

Change a screen's display settings

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _[DisplaySettings](#display-settings)_ | New settings. Settings are individually optional. Fill in only the fields you want to change. |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Return **true** or a list of errors that occurred |


**Example:**

```javascript
var r = h.hly('SetDisplaySettings', {
    id: 'public',
    margin: {
        top: 10, right: 5, bottom: 10, left: 5
    }
});
```

---


### hly('GetBpm')
Returns the current BPM value set in the program



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Current BPM value |


**Example:**

```javascript
var r = h.hly('GetBpm');
h.log('BPM: ' + r.data);
```

---


### hly('SetBpm', input)
Change the current BPM value of the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.bpm` | _Number_ | BPM value |


_Method does not return value_

**Example:**

```javascript
h.hly('SetBpm', {bpm: 80});
```

---


### hly('GetHue')
- v2.19.0

Returns the current hue value defined in the program



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Current hue value. Minimum=0, Maximum=360. Returns **null** if disabled. |


**Example:**

```javascript
var r = h.hly('GetHue');
h.log('HUE: ' + r.data);
```

---


### hly('SetHue', input)
- v2.19.0

Changes the program's current hue value

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.hue` | _Number_ | Hue value. Minimum=0, Maximum=360 or **null** to disable. |


_Method does not return value_

**Example:**

```javascript
h.hly('SetHue', {hue: 250});

h.hly('SetHue', {hue: null});
```

---


### hly('GetRuntimeEnvironment')
### hly('GetRE')
- v2.19.0

Returns the name of the currently defined runtime environment in the program settings.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Runtime environment name |


**Example:**

```javascript
var r = h.hly('GetRuntimeEnvironment');
h.log('current runtime environment: ' + r.data);
```

---


### hly('SetRuntimeEnvironment', input)
### hly('SetRE', input)
- v2.19.0

Change the current runtime environment.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.name` | _String_ | Runtime environment name |


_Method does not return value_

**Example:**

```javascript
h.hly('SetRuntimeEnvironment', {name: 'abc'});
```

---


### hly('SetLogo', input)
Change the settings for the program's *Logo* functionality (tools menu)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.enable` | _Boolean (optional)_ | Enable/disable functionality |
| `input.hide` | _Boolean (optional)_ | Show/hide functionality |


_Method does not return value_

**Example:**

```javascript
h.hly('SetLogo', {enable: true});

h.hly('SetLogo', {hide: true});
```

---


### hly('GetSyncStatus')
- v2.19.0

Returns the current state of online synchronization via Google Drive™



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.enabled` | _Boolean_ | If sync is turned on |
| `data.started` | _Boolean_ | Whether synchronization has started (internet available for example) |
| `data.progress` | _Number_ | Sync progress from 0 to 100 |


---


# Methods Player 
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

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


---


### getDuration()
Total time of current media in player



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Total time in milliseconds |


---


### getCurrentTime()
Current media time in player



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Current media time in milliseconds |


---


### setCurrentTime(time)
- v2.20.0

Alterar o tempo atual da mídia em milissegundos

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `time` | _Number_ | Alterar o tempo atual da mídia em milissegundos |


_Method does not return value_

---


### getTimeElapsed()
Elapsed time of media in player



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Elapsed time in format HH:MM:SS |


---


### getTimeRemaining()
Remaining media time in player



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Remaining time in format HH:MM:SS |


---


### play()
Run player **play** action



_Method does not return value_

---


### pause()
Perform player **pause** action



_Method does not return value_

---


### stop()
Perform player **stop** action



_Method does not return value_

---


### next()
Moves to the next item in the list in the player



_Method does not return value_

---


### previous()
Moves to the previous item in the list in the player



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
Checks if the player is set to play items in sequence



**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ |  |


---


### setExecuteAll(executeAll)
Change player setting to play items in sequence

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
| _Number_ | Volume. Minimum=0, Maximum=100 |


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


# User input Methods 
### input(param, notification = false)
Display a window with input fields to receive information interactively

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `param` | _Object_ | Entries that will be requested in the interface. It can be string or Array&lt;[InputParam](#input-param)&gt;. If a string is passed it will be the item name and the item type will be **text** |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | If only one item is passed as input, the value informed by the user will be returned (can be NULL). If multiple entries are requested, an object will be returned (can be NULL) where each value will be informed in the variable of its respective ID. |


**Example:**

```javascript
var r = h.input("Item name");
h.log("Reported value: " + r);

var param = [{type: 'password', label: 'Password'}];
var r = h.input(param);
h.log("Informed password: " + r);

var param = [
    {
        key: 'info',
        type: 'text',
        label: 'Information'
    }, {
        key: 'type',
        type: 'text',
        label: 'Type',
        allowed_values: ['Type 1', 'Type 2', 'Type 3']
    }
];
var r = h.input(param);
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Information: " + r.info);
    h.log("Type: " + r.type);
}

var param = [
    {
        key: 'message',
        type: 'textarea',
        label: 'Message'
    }, {
        key: 'seconds',
        type: 'number',
        label: 'Seconds',
        min: 30,
        max: 300,
        default_value: 60
    }
];
var r = h.input(param);
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Message: " + r.message);
    h.log("Seconds: " + r.seconds);
}
```

---


### inputTextArea(title, notification = false)
Requests input in **textarea** format allowing multi-line text

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `title` | _String_ | Component name |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Returns the text entered by the user (can be NULL) |


**Example:**

```javascript
var r = h.inputTextArea("Item name");
h.log("Reported value: " + r);

var r = h.inputTextArea("Item name", true); //notification
h.log("Reported value: " + r);
```

---


### itemChooser(title, items, notification = false)
Opens a window for selecting an item from a list of values

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `title` | _String_ | Window title |
| `items` | _Object_ | List of items that will be displayed in the list |
| `items.*.label` | _String (optional)_ | Name that will be displayed representing the item |
| `items.*.selected` | _Boolean (optional)_ | To set the item selected by default. v2.19.0+ |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns the item selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.itemChooser("Select an item", ["abc", "xyz", "123"]);
h.log("Selected item: " + r);

var r = h.itemChooser("Select a number", [1, 2, 3, 4, 5]);
h.log("Selected number: " + r);

var items = [
    {
        id: 1,
        type: 'test1',
        label: 'ABC'
    }, {
        id: 2,
        type: 'test2',
        label: 'XYZ',
        selected: true //selected by default
    }, {
        id: 3,
        type: 'test3',
        label: '123'
    }
];
var r = h.itemChooser("Select an item", items, true); //notification
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item");
    h.log("ID: " + r.id);
    h.log("Type: " + r.type);
    h.log("Name: " + r.label);
}

var arr1 = ['a', 'b', 'c'];
var arr2 = ['x', 'y', 'z'];
var arr3 = [1, 2, 3];
var items = [
    {source: arr1, label: 'List 1 (a, b, c)'},
    {source: arr2, label: 'List 2 (x, y, z)'},
    {source: arr3, label: 'List 3 (1, 2, 3)'}
];
var r = h.itemChooser("Select an item", items);
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.source);
}
```

---


### multipleItemChooser(title, items, notification = false)
- v2.19.0

Opens a window for selecting multiple items from a list of values

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `title` | _String_ | Window title |
| `items` | _Object_ | List of items that will be displayed in the list |
| `items.*.label` | _String (optional)_ | Name that will be displayed representing the item |
| `items.*.selected` | _Boolean (optional)_ | To define if the item will be selected by default. |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns items selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.multipleItemChooser("select the items", ["abc", "xyz", "123"]);
h.log("Selected items: " + r);

var r = h.multipleItemChooser("select the numbers", [1, 2, 3, 4, 5]);
h.log("Selected numbers: " + r);

var items = [
    {
        id: 1,
        type: 'test1',
        label: 'ABC',
        selected: true //selected by default
    }, {
        id: 2,
        type: 'test2',
        label: 'XYZ'
    }, {
        id: 3,
        type: 'test3',
        label: '123',
        selected: true //selected by default
    }
];
var r = h.multipleItemChooser("select the items", items, true); //notification
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected items");
    for (var i = 0; i < r.length; i++) {
        h.log("ID: " + r[i].id);
        h.log("Type: " + r[i].type);
        h.log("Name: " + r[i].label);
    }
}
```

---


### confirm(msg, title = 'Confirm', notification = false)
- v2.19.0

Opens a confirmation window, displaying **OK** and **Cancel** buttons

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `msg` | _String_ | Message that will be displayed |
| `title` | _String_ | Window title |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Return **true** or **false** |


**Example:**

```javascript
if (h.confirm("Do task now?", "title")) {
    //ok
} else {
    //cancel
}
```

---


### yesNo(msg, title = 'Confirm', notification = false)
- v2.19.0

Opens a confirmation window, displaying **Yes** and **No** buttons

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `msg` | _String_ | Message that will be displayed |
| `title` | _String_ | Window title |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Return **true** or **false** |


**Example:**

```javascript
if (h.yesNo("Do task now?", "title")) {
    //yes
} else {
    //no
}
```

---


### notification(msg, duration = 0)
### notificationError(msg, duration = 0)
### notificationWarning(msg, duration = 0)
- v2.19.0

Displays a notification in the corner of the screen

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `msg` | _String_ | Message that will be displayed |
| `duration` | _Number (optional)_ | Time for the notification to be automatically hidden. If the value is less than or equal to zero, the notification will not be automatically hidden. |


_Method does not return value_

**Example:**

```javascript
h.notification("Task accomplished");
```

---


### lyricsChooser()
### songChooser()
- v2.19.0

Opens a window to select a song



**Response:**

| Type  | Description |
| :---: | ------------|
| _[Lyrics](#lyrics)_ | Returns the item selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.lyricsChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.title);
}
```

---


### themeChooser()
- v2.19.0

Opens a window to select a theme



**Response:**

| Type  | Description |
| :---: | ------------|
| _[Background](#background)_ | Returns the item selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.themeChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.name);
}
```

---


### imageChooser()
- v2.19.0

Opens a window to select an image



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Object_ | Returns the item selected by the user (can be NULL) |
| `*.id` | _String_ | Item ID |
| `*.name` | _String_ | Item name |
| `*.isDir` | _Boolean_ | Return **true** if it's a folder or **false** if it's a file. |


**Example:**

```javascript
var r = h.imageChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.name);
}
```

---


### audioChooser()
- v2.19.0

Opens a window to select an audio



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Object_ | Returns the item selected by the user (can be NULL) |
| `*.id` | _String_ | Item ID |
| `*.name` | _String_ | Item name |
| `*.isDir` | _Boolean_ | Return **true** if it's a folder or **false** if it's a file. |


**Example:**

```javascript
var r = h.audioChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.name);
}
```

---


### videoChooser()
- v2.19.0

Opens a window to select a video



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Object_ | Returns the item selected by the user (can be NULL) |
| `*.id` | _String_ | Item ID |
| `*.name` | _String_ | Item name |
| `*.isDir` | _Boolean_ | Return **true** if it's a folder or **false** if it's a file. |


**Example:**

```javascript
var r = h.videoChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.name);
}
```

---


### backgroundChooser()
- v2.19.0

Opens a window to select a background



**Response:**

| Type  | Description |
| :---: | ------------|
| _[Background](#background)_ | Returns the item selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.backgroundChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.name);
}
```

---


# Classes 
Complex classes used as a return in some methods
## Lyrics
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Song ID |
| `title` | _String_ | Song title |
| `artist` | _String_ | Music artist |
| `author` | _String_ | Music author |
| `note` | _String_ | Music annotation |
| `copyright` | _String_ | Copyright da música |
| `key` | _String_ | Tone of music |
| `time_sig` | _String_ | Music time |
| `groups` | _Array&lt;[Group](#group)&gt;_ | Groups where music is added |
| `midi` | _[Midi](#midi)_ | Item MIDI shortcut |
| `archived` | _Boolean_ | If the song is archived |

## Background
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `type` | _String_ | Item type. It might be:theme, my_video, my_image, video, image |
| `name` | _String_ | Item name |
| `tags` | _Array&lt;String&gt;_ | Item tag list |
| `bpm` | _Number_ | BPM value of item |
| `midi` | _[Midi](#midi) (optional)_ | Item MIDI shortcut |

## Item
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `type` | _String_ | Tipo do item. Pode ser: `title`  `song`  `verse`  `text`  `audio`  `video`  `image`  `announcement`  `automatic_presentation`  `countdown`  `countdown_cp`  `cp_text`  `api`  `script` |
| `name` | _String_ | Item name |

## Group
| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Item name |

## MIDI
| Name | Type  | Description |
| ---- | :---: | ------------|
| `code` | _Number_ | MIDI code |
| `velocity` | _Number_ | Speed/intensity midi |

## Favorite Item
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |

## Schedule
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | Playlist type. Can be: temporary, service, event |
| `name` | _String_ |  |
| `datetime` | _String_ | Date and time in format: YYYY-MM-DD HH:MM |
| `lyrics_playlist` | _Array&lt;[Lyrics](#lyrics)&gt;_ | Lyrics list |
| `media_playlist` | _Array&lt;[Item](#item)&gt;_ | Media list |
| `responsible` | _[Member](#member)_ | Member defined as responsible for the event |
| `members` | _Array&lt;Object&gt;_ | List of members |
| `members.*.id` | _String_ | Member ID |
| `members.*.name` | _String_ | Name of the member |
| `members.*.scheduled` | _Boolean_ | Whether the integrand is scaled or defined for a function |
| `roles` | _Array&lt;Object&gt;_ | List of functions on the scale |
| `roles.*.id` | _String_ | Function ID |
| `roles.*.name` | _String_ | Function name |
| `roles.*.member` | _[Member](#member)_ | Member assigned to the role |

## Member
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |

## Role
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |

## Automatic Presentation
| Name | Type  | Description |
| ---- | :---: | ------------|
| `seconds` | _Number_ | Time each item will be displayed |
| `repeat` | _Boolean_ | **true** to keep repeating the presentation (go back to the first item after the last one) |

## Input Param
| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key of item |
| `type` | _String_ | Input type. Can be: text, textarea, number, password, title, separator |
| `label` | _String_ | Item name |
| `default_value` | _Object (optional)_ | Item default value |
| `allowed_values` | _Array&lt;String&gt; (optional)_ | Available if type is **text**. Defines a list of allowed values, to be selected as a combobox |
| `suggested_values` | _Array&lt;String&gt; (optional)_ | Available if type is **text**. Defines a list of suggested values, however the user can enter any value in the text field |
| `min` | _Number (optional)_ | Available if type is **number**. Sets the minimum allowed value `Default: 0` |
| `max` | _Number (optional)_ | Available if type is **number**. Sets the maximum allowed value `Default: 100` |
| `show_as_combobox` | _Boolean (optional)_ | Available if type is **number**. Display the list of values as a combobox and not as a spinner `Default: false` |

## Display Settings
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |
| `stage_view` | _[StageView](#stage-view)_ | Stage view settings. (Unavailable for public screen) |
| `slide_info` | _[SlideAdditionalInfo](#slide-additional-info)_ | Additional slide info |
| `slide_translation` | _String_ | translation name |
| `bible_version_tab` | _Number_ | Tab number (1, 2 or 3) of the Bible translation displayed on the screen, as translations are loaded in the Bible window |
| `margin` | _Object_ | Margins set in **Edit screen position** option. margin.top, margin.right, margin.bottom, margin.left |
| `area` | _[Rectangle](#rectangle)_ | Screen area with margins applied (if available) |
| `total_area` | _[Rectangle](#rectangle)_ | Total screen area on the system |
| `hide` | _Boolean_ | Hide screen |
| `show_items` | _Object_ | Defines the presentation types that will be displayed (only available for stream screens - image and html) |
| `show_items.lyrics` | _Boolean_ | Song lyrics |
| `show_items.text` | _Boolean_ | Text |
| `show_items.verse` | _Boolean_ | Verse |
| `show_items.image` | _Boolean_ | Image |
| `show_items.alert` | _Boolean_ | Alert |
| `show_items.announcement` | _Boolean_ | Announcement |
| `media_player.show` | _Boolean_ | Exibir VLC Player `v2.20.0+` |
| `media_player.margin` | _[Rectangle](#rectangle)_ | Margem para exibição dos vídeos pelo VLC Player `v2.20.0+` |

## Stage View
| Name | Type  | Description |
| ---- | :---: | ------------|
| `enabled` | _Boolean_ | Stage view enabled |
| `preview_mode` | _String_ | Lyrics display mode. Available options:<br/>CURRENT_SLIDE<br/>FIRST_LINE_OF_THE_NEXT_SLIDE_WITH_SEPARATOR<br/>FIRST_LINE_OF_THE_NEXT_SLIDE_WITHOUT_SEPARATOR<br/>NEXT_SLIDE<br/>CURRENT_AND_NEXT_SLIDE<br/>ALL_SLIDES |
| `uppercase` | _Boolean_ | Show in capital letters |
| `remove_line_break` | _Boolean_ | remove line break |
| `show_comment` | _Boolean_ | Show comments |
| `show_advanced_editor` | _Boolean_ | Show advanced editor |
| `show_communication_panel` | _Boolean_ | Show communication panel content |
| `custom_theme` | _Number_ | Custom Theme ID used in presentations |
| `apply_custom_theme_to_bible` | _Boolean_ | Use custom theme in verses |
| `apply_custom_theme_to_text` | _Boolean_ | Use custom theme in texts |

## Slide Additional Info
| Name | Type  | Description |
| ---- | :---: | ------------|
| `info_1` | _Object_ |  |
| `info_1.show_page_count` | _Boolean_ | Show slide count |
| `info_1.show_slide_description` | _Boolean_ | Show slide description (chorus, i.e.) |
| `info_1.horizontal_align` | _String_ | Horizontal alignment of information on the slide. left, center, right |
| `info_1.vertical_align` | _String_ | Vertical alignment of information on the slide. top, bottom |
| `info_2` | _Object_ |  |
| `info_2.show` | _Boolean_ |  |
| `info_2.layout_row_1` | _String_ | First row information layout [Slide Additional Info Layout](#slide-additional-info-layout) |
| `info_2.layout_row_2` | _String (optional)_ | Second line information layout [Slide Additional Info Layout](#slide-additional-info-layout) |
| `info_2.horizontal_align` | _String_ | Horizontal alignment of information on the slide. left, center, right |
| `info_2.vertical_align` | _String_ | Vertical alignment of information on the slide. top, bottom |
| `font` | _Object_ |  |
| `font.name` | _String_ | Font name. If it is **null**, it uses the theme's default font. |
| `font.bold` | _Boolean_ | Bold. If it is **null**, use the default theme setting |
| `font.italic` | _Boolean_ | Italid. If it is **null**, use the default theme setting |
| `font.color` | _String_ | Font color in hexadecimal. If it is **null**, use the theme's default font color |
| `height` | _Number_ | Height in percent of slide height |
| `paint_theme_effect` | _String_ | Render text with theme outline, glow, and shadow effects, if available |

## Rectangle
| Name | Type  | Description |
| ---- | :---: | ------------|
| `x` | _Number_ |  |
| `y` | _Number_ |  |
| `width` | _Number_ |  |
| `height` | _Number_ |  |

## Custom Message
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |
| `message_model` | _String_ | message without filling |
| `message_example` | _String_ | Example message with the name of the parameters filled in |
| `variables` | _Array&lt;[CustomMessageParam](#custom-message-param)&gt;_ | message parameters |

## Custom Message Param
| Name | Type  | Description |
| ---- | :---: | ------------|
| `position` | _Number_ | Parameter position in the message (in number of characters) |
| `name` | _String_ | Item name |
| `only_number` | _Boolean_ | Parameter accepts only numbers |
| `uppercase` | _Boolean_ | Parameter always displayed in uppercase |
| `suggestions` | _Array&lt;String&gt; (optional)_ | List with default values for the parameter |

## Quiz Question
| Name | Type  | Description |
| ---- | :---: | ------------|
| `title` | _String_ | Pergunta |
| `alternatives` | _Array&lt;String&gt;_ | Alternativas |
| `correct_alternative_number` | _Number (optional)_ | Número da alternativa correta. Começa em 1 `Default: 1` |
| `source` | _String (optional)_ | Fonte da resposta |

## Quiz Settings
| Name | Type  | Description |
| ---- | :---: | ------------|
| `correct_answer_color_font` | _String (optional)_ | Cor da fonte para a resposta correta |
| `correct_answer_color_background` | _String (optional)_ | Cor de fundo para a resposta correta |
| `incorrect_answer_color_font` | _String (optional)_ | Cor da fonte para a resposta incorreta |
| `incorrect_answer_color_background` | _String (optional)_ | Cor de fundo para a resposta incorreta |
| `question_and_alternatives_different_slides` | _Boolean (optional)_ | Exibir a pergunta e as alternativas em slides separados `Default: false` |
| `display_alternatives_one_by_one` | _Boolean (optional)_ | Exibir as alternativas uma a uma `Default: true` |
| `alternative_char_type` | _String (optional)_ | Tipo de caractere para listar as alternativas `number (1, 2, 3...)`  `alpha (A, B, C...)` `Default: 'alpha'` |
| `alternative_separator_char` | _String (optional)_ | Caractere separador. Valores permitidos:  ` `  `.`  `)`  `-`  `:` `Default: '.'` |

## AddItem
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | Tipo do item. Pode ser: `title`  `song`  `verse`  `text`  `audio`  `video`  `image`  `announcement`  `automatic_presentation`  `countdown`  `countdown_cp`  `cp_text`  `api`  `script` |

## AddItemTitle
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | title |
| `name` | _String_ | Item name |
| `background_color` | _String (optional)_ | Cor de fundo em hexadecimal, exemplo: 000080 |
| `collapsed` | _Boolean (optional)_ |  `Default: false` |

## AddItemSong
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | song |
| `id` | _String_ | Item ID |

## AddItemVerse
**id**, **ids** or **references**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | verse |
| `id` | _String (optional)_ | To display a verse. Item ID in BBCCCVVV format.<br/>Example: '19023001' (book 19, chapter 023, verse 001) |
| `ids` | _Array&lt;String&gt; (optional)_ | To display a list of verses. List with the ID of each verse.<br/>Example: ['19023001', '43003016', '45012002'] |
| `references` | _String (optional)_ | References. Example: **John 3:16** or **Rm 12:2** or **Gn 1:1-3 Sl 23.1** |

## AddItemText
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | text |
| `id` | _String_ | Item ID |

## AddItemAudio
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | audio |
| `name` | _String_ | Nome do arquivo |

## AddItemVideo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | video |
| `name` | _String_ | Nome do arquivo |

## AddItemImage
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | image |
| `name` | _String_ | Nome do arquivo |

## AddItemAutomaticPresentation
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | automatic_presentation |
| `name` | _String_ | Nome do arquivo |

## AddItemAnnouncement
**id**, **ids**, **name** ou **names**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | announcement |
| `id` | _String (optional)_ | Announcement ID. Can be **all** to display all |
| `ids` | _Array&lt;String&gt; (optional)_ | List with the ID of each announcement |
| `name` | _String (optional)_ | Announcement name |
| `names` | _Array&lt;String&gt; (optional)_ | List with the name of each announcement |
| `automatic` | _[Automatic](#automatic-presentation) (optional)_ | If informed, the presentation of the items will be automatic |

## AddItemCountdown
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | countdown |
| `time` | _String_ | HH:MM ou MM:SS |
| `exact_time` | _Boolean (optional)_ | Se **true**, `time` deve ser HH:MM (hora e minuto exato). Se **false**, `time` deve ser MM:SS (quantidade de minutos e segundos) `Default: false` |
| `text_before` | _String (optional)_ | Texto exibido na parte superior da contagem regressiva |
| `text_after` | _String (optional)_ | Texto exibido na parte inferior da contagem regressiva |
| `zero_fill` | _Boolean (optional)_ | Preencher o campo 'minuto' com zero à esquerda `Default: false` |
| `countdown_relative_size` | _Number (optional)_ | Tamanho relativo da contagem regressiva `Default: 250` |

## AddItemCountdownCommunicationPanel
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | countdown_cp |
| `minutes` | _Number_ | Number of minutes |
| `seconds` | _Number_ | Number of seconds |
| `stop_at_zero` | _Boolean (optional)_ | Stop the countdown when it reaches zero `Default: false` |
| `description` | _String_ | Descrição do item |

## AddItemTextCommunicationPanel
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | cp_text |
| `name` | _String_ | Item name |
| `text` | _String_ | Text |
| `display_ahead` | _Boolean (optional)_ | Change the *'display in front of all'* option |

## AddItemScript
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | script |
| `description` | _String_ | Descrição do item |
| `inputs` | _Object (optional)_ | Valor padrão para [Function Input](https://github.com/holyrics/Scripts/blob/main/FunctionInput.md) |

## AddItemAPI
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | api |
| `description` | _String_ | Descrição do item |
| `inputs` | _Object (optional)_ | Valor padrão para [Function Input](https://github.com/holyrics/Scripts/blob/main/FunctionInput.md) |

# Slide Additional Info Layout
Type between the characters **< >** the texts you want to display
<br/>
And type inside **% %** the name of the field you want to use
<br/>
Example:

`<%title%>< (%author%)>`
<br/>
Turns into: **Title (Author)**
<br/>
But if the **author** field is not available, only **Title** will be displayed, not **Title ()**
<br/>

`<%title%>< - %author%>`
<br/>
Turns into: **Title - Author**
<br/>
But if the **author** field is not available, only **Title** will be displayed, not **Title -**
<br/>

It is also possible to use the **extra** fields created by the user for the songs, for example:
<br/>
If there is an extra field called **Year**, it can be used like this:
<br/>
`<title>< - %author%><, %Year%>`
<br/>
Turns into: **Title - Author, 2023**

# Styled Text
To display richly formatted text, start the text with **&lt;styled&gt;**

HTML tags available

```
<styled>
<b>bold</b>
<i>italic</i>
<u>underlined</u>
<color:0000FF>font color</color>
<font:Times New Roman>font name</font>
<size:70>relative font size 70%</size>
```
