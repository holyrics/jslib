# FileItem

---

$FIELDS$

---

- [Functions](#functions)
  - [name](#name)
  - [type](#type)
  - [filename](#filename)
  - [is_dir](#isdir)
  - [properties](#properties)
  - [getExtension](#getextension)
  - [isType](#istypetype)
  - [isTypeAudio](#istypeaudio)
  - [isTypeVideo](#istypevideo)
  - [isTypeImage](#istypeimage)
  - [isTypeFile](#istypefile)
  - [getMetadata](#getmetadata)
  - [getThumbnail](#getthumbnail)


# Functions 
| `name` | _String_ |  |

| `type` | _String_ | `audio`  `video`  `image`  `file` |

| `filename` | _String_ |  |

| `is_dir` | _Boolean_ |  |

| `properties` | _Object_ |  |

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
### isAudio


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### isTypeVideo()
### isVideo


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### isTypeImage()
### isImage


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### isTypeFile()


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
| `data.modified_time_millis` | _String_ | File modification date. (timestamp) |
| `data.duration_ms` | _Number_ | File duration. Available if the file is: audio or vídeo |
| `data.width` | _Number_ | Width. Available if the file is: imagem or vídeo |
| `data.height` | _Number_ | Height. Available if the file is: imagem or vídeo |
| `data.position` | _String_ | Image adjustment. Available for images. Can be: `adjust` `extend` `fill` |
| `data.blur` | _Boolean_ | Apply blur effect |
| `data.transparent` | _Boolean_ | Display images with transparency |
| `data.last_executed_time` | _Boolean_ | Date of the last execution of the file. Date and time format: YYYY-MM-DD HH:MM |
| `data.last_executed_time_millis` | _Boolean_ |  |


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
