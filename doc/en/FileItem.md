# FileItem

```javascript
var f = h.files.getImage('image.jpg');
h.log(f.name);
h.log(f.properties.abc);
f.properties.abc = 'xyz';
```



# Fields 
| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ |  |
| `type` | _String_ | `audio`  `video`  `image`  `file` |
| `filename` | _String_ |  |
| `is_dir` | _Boolean_ |  |
| `properties` | _Object_ |  |


---

- [Functions](#functions)
  - [getExtension](#getextension)
  - [isType](#istypetype)
  - [isTypeAudio](#istypeaudio)
  - [getMetadata](#getmetadata)
  - [getThumbnail](#getthumbnail)


# Functions 
### getExtension()


**Response:**

| Type  |
| :---: |
| _String_ | 


---


### isType(type)
**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | `audio`  `video`  `image`  `file` |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
var r = h.isType('audio');
```

---


### isTypeAudio()
### isTypeVideo()
### isTypeImage()
### isTypeFile()
### isAudio()
### isVideo()
### isImage()


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### getMetadata()


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Object_ |  |
| `data.length` | _Number_ | File size (bytes). Available if **isDir=false** |
| `data.modified_time` | _String_ | File modification date. Date and time format: YYYY-MM-DD HH:MM |
| `data.modified_time_millis` | _Number_ | File modification date. (timestamp) |
| `data.duration_ms` | _Number_ | File duration. Available if the file is: audio or vídeo |
| `data.width` | _Number_ | Width. Available if the file is: imagem or vídeo |
| `data.height` | _Number_ | Height. Available if the file is: imagem or vídeo |
| `data.position` | _String_ | Image adjustment. Available for images. Can be: `adjust` `extend` `fill` |
| `data.blur` | _Boolean_ | Apply blur effect |
| `data.transparent` | _Boolean_ | Display images with transparency |
| `data.last_executed_time` | _String_ | Date of the last execution of the file. Date and time format: YYYY-MM-DD HH:MM |
| `data.last_executed_time_millis` | _Number_ |  |


**Example:**

```javascript
var r = h.getMetadata();
r.length;
```

---


### getThumbnail()


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Image in base64 format |


---
