# FileItem

```javascript
var f = h.files.getImage('image.jpg');
h.log(f.name);
h.log(f.properties.abc);
f.properties.abc = 'xyz';
```



# Fields 
| Nome | Tipo  | Descrição |
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


**Resposta:**

| Tipo  |
| :---: |
| _String_ | 


---


### isType(type)
**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | `audio`  `video`  `image`  `file` |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

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


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


---


### getMetadata()


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Object_ |  |
| `data.length` | _Number_ | Tamanho do arquivo (bytes). Disponível se **isDir=false** |
| `data.modified_time` | _String_ | Data de modificação do arquivo. Data e hora no formato: YYYY-MM-DD HH:MM |
| `data.modified_time_millis` | _Number_ | Data de modificação do arquivo. (timestamp) |
| `data.duration_ms` | _Number_ | Duração do arquivo. Disponível se o arquivo for: audio ou vídeo |
| `data.width` | _Number_ | Largura. Disponível se o arquivo for: imagem ou vídeo |
| `data.height` | _Number_ | Altura. Disponível se o arquivo for: imagem ou vídeo |
| `data.position` | _String_ | Ajuste da imagem. Disponível para imagens. Pode ser: `adjust` `extend` `fill` |
| `data.blur` | _Boolean_ | Aplicar efeito blur |
| `data.transparent` | _Boolean_ | Exibir imagens com transparência |
| `data.last_executed_time` | _String_ | Data da última execução do arquivo. Data e hora no formato: YYYY-MM-DD HH:MM |
| `data.last_executed_time_millis` | _Number_ |  |


**Exemplo:**

```javascript
var r = h.getMetadata();
r.length;
```

---


### getThumbnail()


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Imagem no formato base64 |


---
