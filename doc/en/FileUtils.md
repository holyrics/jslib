# FileUtils
Classe utilitária para alguns métodos de manipulação de arquivos

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
  - [getAudios](#getaudiosfolder--null)
  - [getAudio](#getaudioname)
  - [audioExists](#audioexistsname)
  - [exists](#existsname)


# Functions 
### mkdir(name)
Criar uma nova pasta

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Nome da pasta que será criada. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Example:**

```javascript
var r = h.files.mkdir('image/new folder');
```

---


### mkdir(input)
Criar uma nova pasta

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _Object_ | Nome da pasta que será criada. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (optional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Example:**

```javascript
var r = h.files.mkdir({
    file: 'image/new folder'
});
```

---


### rename(from, to)
Renomear um arquivo ou pasta

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Example:**

```javascript
var r = h.files.rename('image/filename.jpg', 'image/filename renamed.jpg');
```

---


### rename(input)
Renomear um arquivo ou pasta

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (optional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |
| `update_references` | _Boolean (optional)_ |  `Default: true` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Example:**

```javascript
var r = h.files.rename({
    from: 'image/filename.jpg',
    to: 'image/filename renamed.jpg'
});
```

---


### copyFile(from, to, progress = null)
Copiar um arquivo

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `progress` | _Function_ | Function de callback executada a cada atualização de progresso da execução `0 ~ 100` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Example:**

```javascript
var r = h.files.copyFile('image/filename.jpg', 'image/filename copy.jpg');
```

---


### copyFile(input)
Copiar um arquivo

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (optional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |
| `input.progress` | _Function (optional)_ | Function de callback executada a cada atualização de progresso da execução `0 ~ 100` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Example:**

```javascript
var r = h.files.copyFile({
    from: 'image/filename.jpg',
    to: 'image/filename renamed.jpg'
});
```

---


### copyFolder(from, to, progress = null)
Copiar uma pasta

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `progress` | _Function (optional)_ | Function de callback executada a cada atualização de progresso da execução `0 ~ 100` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Example:**

```javascript
var r = h.files.copyFolder('video/folder', 'video/folder', function(progress) {
    h.log(progress + "%");
});
```

---


### copyFolder(input)
Copiar uma pasta

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (optional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |
| `input.progress` | _Function (optional)_ | Function de callback executada a cada atualização de progresso da execução `0 ~ 100` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


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
Apagar um arquivo

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do arquivo que será apagado. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Example:**

```javascript
var r = h.files.deleteFile('image/filename.jpg');
```

---


### deleteFile(input)
Apagar um arquivo

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome do arquivo que será apagado. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (optional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Example:**

```javascript
var r = h.files.deleteFile({
    file: 'image/filename.jpg'
});
```

---


### deleteFolder(name)
Apagar uma pasta

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Nome da pasta que será apagada. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Example:**

```javascript
var r = h.files.deleteFolder('video/folder');
```

---


### deleteFolder(input)
Apagar uma pasta

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome da pasta que será apagada. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (optional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (optional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |
| `recursively` | _Boolean (optional)_ | Apagar recursivamente. Se `false`, a pasta será apagada somente se estiver vazia `Default: false` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Example:**

```javascript
var r = h.files.deleteFolder({
    file: 'video/folder'
});
```

---


### hasImageExtension(path)
Verifica se o valor informado termina com uma extensão do tipo correspondente.<br>Image (png, jpg, ...)

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
Verifica se o valor informado termina com uma extensão do tipo correspondente.<br>Audio (mp3, wma, ...)

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
Verifica se o valor informado termina com uma extensão do tipo correspondente.<br>Vídeo (mp4, mkv, ...)

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
Lista com as extensões do tipo correspondente.<br>Image (png, jpg, ...)



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
Lista com as extensões do tipo correspondente.<br>Audio (mp3, wma, ...)



**Response:**

| Type  |
| :---: |
| _Array&lt;String&gt;_ | 


---


### getVideoExtensions()
Lista com as extensões do tipo correspondente.<br>Vídeo (mp4, mkv, ...)



**Response:**

| Type  |
| :---: |
| _Array&lt;String&gt;_ | 


---


### getAudios(folder = null)
### getVideos(folder)
### getImages(folder)
### getFiles(folder)
Returns the list of files from the respective tab: audio, video, image, file May generate Exception

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `Nome da pasta` | _String (optional)_ |  |


**Response:**

| Type  |
| :---: |
| _Array&lt;[FileItem](#file-item)&gt;_ | 


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
| _[FileItem](#file-item)_ | 


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
| `name` | _String_ | File name (including subfolder)<br>Deve começar com:  `audio/`  `video/`  `image/`  `file/` |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---
