# jslib
**EN** | [PT](README.md)

JSLib class methods available for use in Holyrics program scripts.

You can use the ```jslib``` variable or the ```h``` variable to access the available methods.

For example:

```
jslib.log('example');
h.log('example');
```
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


### startTimer(key)
Start a timer

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Timer key |


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


### getTimer(key)
Retrieves how much time has elapsed on a timer according to the **key** value. If the timer has not been started, the method will start the timer and return 00:00:00

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Timer key |


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


### scriptAction(id)
Executes the action of an existing **Script** item in the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | id of item |


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
```

---


### apiAction(id)
Executes the action of an existing API item in the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | id of item |


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
```

---


### apiRequest(id, raw)
Executes a request to the associated receiver and returns the receiver's response. Valid only for URL receivers

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | id of receiver |
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


# Methods HLY


All requests for hly(...) methods return a default object:
| Name | Type  | Description |
| ---- | :---: | ------------|
| `status` | _String_ | It might be *'ok'* or *'error'* |
| `error` | _String (optional)_ | Error message if status equals *error* |
| `data` | _Object (optional)_ | Response content if *status* equals *ok* |


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


### hly('GetLyrics', input)
### hly('GetSong', input)
Returns a song.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID of music |


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


### hly('GetLyricsPlaylist')
### hly('GetSongPlaylist')
Lyrics playlist



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Lyrics](lyrics)&gt;_ |  |


**Example:**

```javascript
var r = h.hly('GetLyricsPlaylist');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].title);
}
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


### hly('GetBackgrounds', input)
List of themes and backgrounds

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object (optional)_ | Filter |
| `input.type` | _String (optional)_ | It might be: theme, my_video, my_image, video, image |
| `input.tag` | _String (optional)_ |  |
| `input.tags` | _Array&lt;String&gt; (optional)_ |  |
| `input.intersection` | _Boolean (optional)_ | If the **input.tags** field is populated with multiple items, the **input.intersection** option defines the type of junction. If **true**, the filter will only return items that contain **all** the informed tags, if **false**, the filter will return the items that have at least one tag of the informed tags _(Default=*false*)_ |


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


### hly('GetFavorites')
Favorites bar items



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Favorite Item](#favorite_item)&gt;_ |  |


**Example:**

```javascript
var r = h.hly('GetFavorites');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetHistories')
History of all tags for "Music played"



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.music_id` | _String_ | ID of music |
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


### hly('GetCurrentSchedule')
Current schedule (selected in the main program window)



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _[Schedule](#schedule)_ |  |


**Example:**

```javascript
var r = h.hly('GetCurrentSchedule');
for (var i = 0; i < r.data.length; i++) {
    var s = r.data[i];
    h.log(s.datetime);
    h.log(s.name);
    h.log(s.lyrics_playlist);
    h.log(s.media_playlist);
}
```

---


### hly('GetSchedules')
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


### hly('MediaPlaylistAction', input)
Play a media playlist item

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID if item |


_Method does not return value_

**Example:**

```javascript
h.hly('MediaPlaylistAction', {id: 'abc'});

//Alternate calls
h.mediaPlaylistAction('abc');
h.mplAction('abc');
```

---


### hly('FavoriteAction', input)
Execute an item from the bookmarks bar

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID if item |


_Method does not return value_

**Example:**

```javascript
h.hly('FavoriteAction', {id: 'abc'});

//Alternate calls
h.favoriteAction('abc');
h.favAction('abc');
```

---


### hly('ShowLyrics', input)
### hly('ShowSong', input)
Starts a lyric show.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID if item |


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
| `input.id` | _String_ | ID if item |


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
| `input.id` | _String (optional)_ | To display a verse. Item ID in BBCCCVVV format. Example: '19023001' (i.e. book 19, chapter 023, verse 001) |
| `input.ids` | _Array&lt;String&gt; (optional)_ | To display a list of verses. List with the ID of each verse. Example: ['19023001', '43003016', '45012002'] |
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


### hly('ShowQuickPresentation', input)
Quick display of text

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String_ | Text to be displayed |
| `input.theme` | _Object (optional)_ | Filter selected theme for display |
| `input.theme.id` | _String (optional)_ | ID of theme |
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


### hly('CloseCurrentPresentation')
End current presentation



_Method does not return value_

**Example:**

```javascript
h.hly('CloseCurrentPresentation');
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
| `input.intersection` | _Boolean (optional)_ | If the **input.tags** field is populated with multiple items, the **input.intersection** option defines the type of junction. If **true**, the filter will only return items that contain **all** the informed tags, if **false**, the filter will return the items that have at least one tag of the informed tags _(Default=*false*)_ |


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


### hly('SetBpm')
Change the current BPM value of the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `bpm` | _Number_ | BPM value |


_Method does not return value_

**Example:**

```javascript
h.hly('SetBpm', {bpm: 80});
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
| `input.title` | _Boolean (optional)_ |  _(Default=*true*)_ |
| `input.artist` | _Boolean (optional)_ |  _(Default=*true*)_ |
| `input.note` | _Boolean (optional)_ |  _(Default=*true*)_ |
| `input.lyrics` | _Boolean (optional)_ |  _(Default=*false*)_ |
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


### hly('AddLyricsToPlaylist', input)
### hly('AddSongsToPlaylist', input)
Add song lyrics to playlist

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | ID of the lyrics |
| `input.ids` | _Array&lt;String&gt; (optional)_ | List with id of each lyics |
| `input.index` | _Number (optional)_ | Position in the list where the item will be added (starts at zero). Items are added to the end of the list by default. _(Default=*-1*)_ |
| `input.media_playlist` | _Boolean (optional)_ | Add the lyrics to the media playlist _(Default=*false*)_ |


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
| `input.id` | _String (optional)_ | ID of the lyrics |
| `input.ids` | _Array&lt;String&gt; (optional)_ | List with id of each lyics |
| `input.index` | _Number (optional)_ | Position of the item in the list to be removed (starts at zero). |
| `input.indexes` | _Boolean (optional)_ | List with the position of each item in the list that will be removed. (Starts at zero) |


_Method does not return value_

**Example:**

```javascript
h.hly('RemoveFromLyricsPlaylist', {id: '123'});

h.hly('RemoveFromLyricsPlaylist', {ids: ['123', '456']});

h.hly('RemoveFromLyricsPlaylist', {index: 3});

h.hly('RemoveFromLyricsPlaylist', {indexes: [3, 4, 5]});
```

---


### hly('RemoveFromMediaPlaylist', input)
Remove items from media playlist

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | ID if item |
| `input.ids` | _Array&lt;String&gt; (optional)_ | List with id of each item |
| `input.index` | _Number (optional)_ | Position of the item in the list to be removed (starts at zero). |
| `input.indexes` | _Boolean (optional)_ | List with the position of each item in the list that will be removed. (Starts at zero) |


_Method does not return value_

**Example:**

```javascript
h.hly('RemoveFromMediaPlaylist', {id: 'abc'});

h.hly('RemoveFromMediaPlaylist', {ids: ['abc', 'xyz']});

h.hly('RemoveFromMediaPlaylist', {index: 3});

h.hly('RemoveFromMediaPlaylist', {indexes: [3, 4, 5]});
```

---


### hly('GetCommunicationPanelInfo')
### hly('GetCPInfo')
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


### hly('StartCountdownCommunicationPanel', input)
### hly('StartCountdownCP', input)
Starts a countdown on the communication panel

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.minutes` | _Number_ | Number of minutes |
| `input.seconds` | _Number_ | Number of seconds |
| `input.yellow_starts_at` | _Number (optional)_ | Value in seconds to define how long the countdown will be yellow from |
| `input.stop_at_zero` | _Boolean (optional)_ | Stop the countdown when it reaches zero _(Default=*false*)_ |


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


### hly('SetTextCommunicationPanel', input)
### hly('SetTextCP', input)
Change communication panel text

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _Number (optional)_ | Change communication panel text |
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
    },{
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
    },{
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
| `items.*.label` | _Boolean (optional)_ | Name that will be displayed representing the item |


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
    },{
        id: 2,
        type: 'test2',
        label: 'XYZ'
    },{
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


# Classes
Complex classes used as a return in some methods
## Lyrics
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | ID of music |
| `title` | _String_ | Song title |
| `artist` | _String_ | Music artist |
| `author` | _String_ | Music author |
| `note` | _String_ | Music annotation |
| `key` | _String_ | Tone of music |
| `time_sig` | _String_ | Music time |
| `groups` | _Array&lt;[Group](#group)&gt;_ | Groups where music is added |
| `midi` | _[Midi](#midi)_ | Item MIDI shortcut |
| `archived` | _Boolean_ | If the song is archived |

## Background
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | ID if item |
| `type` | _String_ | Item type. It might be:theme, my_video, my_image, video, image |
| `name` | _String_ | Item name |
| `tags` | _Array&lt;String&gt;_ | Item tag list |
| `bpm` | _Number_ | BPM value of item |
| `midi` | _[Midi](#midi) (optional)_ | Item MIDI shortcut |

## Item
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | ID if item |
| `type` | _String_ | Item type. It might be: song, verse, text, audio, video, image, file, custom-text, announcement, countdown, countdown-cp, automatic_presentation, api, script |
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
| `id` | _String_ | ID if item |
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
| `id` | _String_ | ID if item |
| `name` | _String_ | Item name |

## Role
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | ID if item |
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
| `min` | _Number (optional)_ | Available if type is **number**. Sets the minimum allowed value _(Default=*0*)_ |
| `max` | _Number (optional)_ | Available if type is **number**. Sets the maximum allowed value _(Default=*100*)_ |
| `show_as_combobox` | _Boolean (optional)_ | Available if type is **number**. Display the list of values as a combobox and not as a spinner _(Default=*false*)_ |
