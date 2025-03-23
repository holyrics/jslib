# FileUtils
Utility class for some file manipulation methods

---

- [Functions](#functions)
  - [mkdir](#mkdirname)
  - [mkdir](#mkdirinput)
  - [rename](#renamefrom-to)
  - [rename](#renameinput)
  - [copyFile](#copyfilefrom-to-progress--null)
  - [copyFile](#copyfileinput)
  - [copyFolder](#copyfolderfrom-to-progress--null)
  - [copyFolder](#copyfolderinput)
  - [deleteFile](#deletefilename)
  - [deleteFile](#deletefileinput)
  - [deleteFolder](#deletefoldername)
  - [deleteFolder](#deletefolderinput)
  - [hasImageExtension](#hasimageextensionpath)
  - [hasAudioExtension](#hasaudioextensionpath)
  - [hasVideoExtension](#hasvideoextensionpath)
  - [getImageExtensions](#getimageextensions)
  - [getAudioExtensions](#getaudioextensions)
  - [getVideoExtensions](#getvideoextensions)
  - [getAudios - getVideos - getImages - getFiles](#getaudiosfolder--null)
  - [getAudio - getVideo - getImage - getFile](#getaudioname)
  - [audioExists - videoExists - imageExists - fileExists](#audioexistsname)
  - [exists](#existsname)


# Functions 
### mkdir(name)
Create a new folder

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Name of the folder that will be created. Must start with:  `audio/`  `video/`  `image/`  `file/` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.mkdir('image/new folder');
```

---


### mkdir(input)
Create a new folder

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _Object_ | Name of the folder that will be created. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Message displayed to the user in the permission request window for performing the action |
| `input.notification` | _Boolean (optional)_ | Show notification in the corner of the screen instead of opening the permission window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.mkdir({
    file: 'image/new folder'
});
```

---


### rename(from, to)
Rename a file or folder

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `from` | _String_ | Source file. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `to` | _String_ | Destination file. Must start with:  `audio/`  `video/`  `image/`  `file/` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.rename('image/filename.jpg', 'image/filename renamed.jpg');
```

---


### rename(input)
Rename a file or folder

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.from` | _String_ | Source file. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `input.to` | _String_ | Destination file. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Message displayed to the user in the permission request window for performing the action |
| `input.notification` | _Boolean (optional)_ | Show notification in the corner of the screen instead of opening the permission window directly |
| `update_references` | _Boolean (optional)_ |  `Default: true` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.rename({
    from: 'image/filename.jpg',
    to: 'image/filename renamed.jpg'
});
```

---


### copyFile(from, to, progress = null)
Copy a file

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `from` | _String_ | Source file. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `to` | _String_ | Destination file. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `progress` | _Function_ | Callback function executed on each progress update of the execution `0 ~ 100` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.copyFile('image/filename.jpg', 'image/filename copy.jpg');
```

---


### copyFile(input)
Copy a file

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.from` | _String_ | Source file. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `input.to` | _String_ | Destination file. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Message displayed to the user in the permission request window for performing the action |
| `input.notification` | _Boolean (optional)_ | Show notification in the corner of the screen instead of opening the permission window directly |
| `input.progress` | _Function (optional)_ | Callback function executed on each progress update of the execution `0 ~ 100` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.copyFile({
    from: 'image/filename.jpg',
    to: 'image/filename renamed.jpg'
});
```

---


### copyFolder(from, to, progress = null)
Copy a folder

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `from` | _String_ | Source file. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `to` | _String_ | Destination file. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `progress` | _Function (optional)_ | Callback function executed on each progress update of the execution `0 ~ 100` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.copyFolder('video/folder', 'video/folder', function(progress) {
    h.log(progress + "%");
});
```

---


### copyFolder(input)
Copy a folder

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.from` | _String_ | Source file. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `input.to` | _String_ | Destination file. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Message displayed to the user in the permission request window for performing the action |
| `input.notification` | _Boolean (optional)_ | Show notification in the corner of the screen instead of opening the permission window directly |
| `input.progress` | _Function (optional)_ | Callback function executed on each progress update of the execution `0 ~ 100` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.copyFolder({
    from: 'video/folder',
    to: 'video/folder',
    progress: function(progress) {
        h.log(progress + "%");
    }
});
```

---


### deleteFile(name)
Delete a file

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Name of the file that will be deleted. Must start with:  `audio/`  `video/`  `image/`  `file/` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.deleteFile('image/filename.jpg');
```

---


### deleteFile(input)
Delete a file

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | Name of the file that will be deleted. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Message displayed to the user in the permission request window for performing the action |
| `input.notification` | _Boolean (optional)_ | Show notification in the corner of the screen instead of opening the permission window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.deleteFile({
    file: 'image/filename.jpg'
});
```

---


### deleteFolder(name)
Delete a folder

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Name of the folder that will be deleted. Must start with:  `audio/`  `video/`  `image/`  `file/` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.deleteFolder('video/folder');
```

---


### deleteFolder(input)
Delete a folder

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | Name of the folder that will be deleted. Must start with:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Message displayed to the user in the permission request window for performing the action |
| `input.notification` | _Boolean (optional)_ | Show notification in the corner of the screen instead of opening the permission window directly |
| `recursively` | _Boolean (optional)_ | Delete recursively. If `false`, the folder will be deleted only if it is empty `Default: false` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` was executed successfully<br>`false` if it was canceled by the user<br>Exception if there was any error |


**Example:**

```javascript
var r = h.files.deleteFolder({
    file: 'video/folder'
});
```

---


### hasImageExtension(path)
Checks if the provided value ends with a corresponding type extension.<br>Image (png, jpg, ...)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `path` | _String_ |  |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
var r = h.files.hasImageExtension('path example/folder/subfolder/filename.jpg');
//r = true

var r = h.files.hasImageExtension('path example/folder/subfolder/filename.mp3');
//r = false
```

---


### hasAudioExtension(path)
Checks if the provided value ends with a corresponding type extension.<br>Audio (mp3, wma, ...)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `path` | _String_ |  |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### hasVideoExtension(path)
Checks if the provided value ends with a corresponding type extension.<br>Video (mp4, mkv, ...)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `path` | _String_ |  |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### getImageExtensions()
List of corresponding type extensions.<br>Image (png, jpg, ...)



**Response:**

| Type  |
| :---: |
| _Array&lt;String&gt;_ | 


**Example:**

```javascript
var r = h.files.getImageExtensions();
//r = ['jpg', 'bmp', 'gif', 'png', 'jpeg', 'webp'];
```

---


### getAudioExtensions()
List of corresponding type extensions.<br>Audio (mp3, wma, ...)



**Response:**

| Type  |
| :---: |
| _Array&lt;String&gt;_ | 


---


### getVideoExtensions()
List of corresponding type extensions.<br>Video (mp4, mkv, ...)



**Response:**

| Type  |
| :---: |
| _Array&lt;String&gt;_ | 


---


### getAudios(folder = null)
### getVideos(folder = null)
### getImages(folder = null)
### getFiles(folder = null)
Returns the list of files from the respective tab: audio, video, image, file May generate Exception

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `folder` | _String (optional)_ | Folder name |


**Response:**

| Type  |
| :---: |
| _[FileItem](https://github.com/holyrics/jslib/blob/main/doc/en/FileItem.md)_ | 


**Example:**

```javascript
var r = h.files.getAudios();

var r = h.files.getAudios('folder name');
```

---


### getAudio(name)
### getVideo(name)
### getImage(name)
### getFile(name)
Returns the data of a file from the list of files in the respective tab: audio, video, image, file May generate Exception

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | File name (including subfolder) |


**Response:**

| Type  |
| :---: |
| _[FileItem](https://github.com/holyrics/jslib/blob/main/doc/en/FileItem.md)_ | 


**Example:**

```javascript
var r = h.files.getAudio('filename.mp3');
```

---


### audioExists(name)
### videoExists(name)
### imageExists(name)
### fileExists(name)
Checks if there is a file with the informed name

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | File name (including subfolder) |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
var r = h.files.audioExists('filename.mp3');
```

---


### exists(name)
Checks if there is a file with the informed name

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | File name (including subfolder)<br>Must start with:  `audio/`  `video/`  `image/`  `file/` |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---
