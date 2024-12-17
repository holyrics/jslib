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

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome da pasta que será criada. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

```javascript
var r = h.files.mkdir('image/new folder');
```

---


### mkdir(input)
Criar uma nova pasta

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _Object_ | Nome da pasta que será criada. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (opcional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (opcional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

```javascript
var r = h.files.mkdir({
    file: 'image/new folder'
});
```

---


### rename(from, to)
Renomear um arquivo ou pasta

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

```javascript
var r = h.files.rename('image/filename.jpg', 'image/filename renamed.jpg');
```

---


### rename(input)
Renomear um arquivo ou pasta

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (opcional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (opcional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |
| `update_references` | _Boolean (opcional)_ |  `Padrão: true` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

```javascript
var r = h.files.rename({
    from: 'image/filename.jpg',
    to: 'image/filename renamed.jpg'
});
```

---


### copyFile(from, to, progress = null)
Copiar um arquivo

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `progress` | _Function_ | Function de callback executada a cada atualização de progresso da execução `0 ~ 100` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

```javascript
var r = h.files.copyFile('image/filename.jpg', 'image/filename copy.jpg');
```

---


### copyFile(input)
Copiar um arquivo

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (opcional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (opcional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |
| `input.progress` | _Function (opcional)_ | Function de callback executada a cada atualização de progresso da execução `0 ~ 100` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

```javascript
var r = h.files.copyFile({
    from: 'image/filename.jpg',
    to: 'image/filename renamed.jpg'
});
```

---


### copyFolder(from, to, progress = null)
Copiar uma pasta

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `progress` | _Function (opcional)_ | Function de callback executada a cada atualização de progresso da execução `0 ~ 100` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

```javascript
var r = h.files.copyFolder('video/folder', 'video/folder', function(progress) {
    h.log(progress + "%");
});
```

---


### copyFolder(input)
Copiar uma pasta

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.from` | _String_ | Arquivo de origem. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.to` | _String_ | Arquivo de destino. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (opcional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (opcional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |
| `input.progress` | _Function (opcional)_ | Function de callback executada a cada atualização de progresso da execução `0 ~ 100` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

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

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do arquivo que será apagado. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

```javascript
var r = h.files.deleteFile('image/filename.jpg');
```

---


### deleteFile(input)
Apagar um arquivo

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome do arquivo que será apagado. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (opcional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (opcional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

```javascript
var r = h.files.deleteFile({
    file: 'image/filename.jpg'
});
```

---


### deleteFolder(name)
Apagar uma pasta

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome da pasta que será apagada. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

```javascript
var r = h.files.deleteFolder('video/folder');
```

---


### deleteFolder(input)
Apagar uma pasta

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome da pasta que será apagada. Deve começar com:  `audio/`  `video/`  `image/`  `file/` |
| `input.description` | _String (opcional)_ | Mensagem exibida ao usuário na janela de solicitação de permissão para execução da ação |
| `input.notification` | _Boolean (opcional)_ | Exibir notificação no canto da tela em vez de abrir a janela de permissão diretamente |
| `recursively` | _Boolean (opcional)_ | Apagar recursivamente. Se `false`, a pasta será apagada somente se estiver vazia `Padrão: false` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `true` se foi executado com sucesso<br>`false` se foi cancelado pelo usuário<br>Exception se ocorreu algum erro |


**Exemplo:**

```javascript
var r = h.files.deleteFolder({
    file: 'video/folder'
});
```

---


### hasImageExtension(path)
Verifica se o valor informado termina com uma extensão do tipo correspondente.<br>Imagem (png, jpg, ...)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `path` | _String_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
var r = h.files.hasImageExtension('path example/folder/subfolder/filename.jpg');
//r = true

var r = h.files.hasImageExtension('path example/folder/subfolder/filename.mp3');
//r = false
```

---


### hasAudioExtension(path)
Verifica se o valor informado termina com uma extensão do tipo correspondente.<br>Áudio (mp3, wma, ...)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `path` | _String_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


---


### hasVideoExtension(path)
Verifica se o valor informado termina com uma extensão do tipo correspondente.<br>Vídeo (mp4, mkv, ...)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `path` | _String_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


---


### getImageExtensions()
Lista com as extensões do tipo correspondente.<br>Imagem (png, jpg, ...)



**Resposta:**

| Tipo  |
| :---: |
| _Array&lt;String&gt;_ | 


**Exemplo:**

```javascript
var r = h.files.getImageExtensions();
//r = ['jpg', 'bmp', 'gif', 'png', 'jpeg', 'webp'];
```

---


### getAudioExtensions()
Lista com as extensões do tipo correspondente.<br>Áudio (mp3, wma, ...)



**Resposta:**

| Tipo  |
| :---: |
| _Array&lt;String&gt;_ | 


---


### getVideoExtensions()
Lista com as extensões do tipo correspondente.<br>Vídeo (mp4, mkv, ...)



**Resposta:**

| Tipo  |
| :---: |
| _Array&lt;String&gt;_ | 


---


### getAudios(folder = null)
### getVideos(folder)
### getImages(folder)
### getFiles(folder)
Retorna a lista de arquivos da respectiva aba: áudio, vídeo, imagem, arquivo Pode gerar Exception

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `Nome da pasta` | _String (opcional)_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _[FileItem](https://github.com/holyrics/jslib/blob/main/doc/pt/FileItem.md)_ | 


**Exemplo:**

```javascript
var r = h.files.getAudios();

var r = h.files.getAudios('folder name');
```

---


### getAudio(name)
### getVideo(name)
### getImage(name)
### getFile(name)
Retorna os dados de um arquivo da lista de arquivos da respectiva aba: áudio, vídeo, imagem, arquivo Pode gerar Exception

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do arquivo (incluindo subpasta) |


**Resposta:**

| Tipo  |
| :---: |
| _[FileItem](https://github.com/holyrics/jslib/blob/main/doc/pt/FileItem.md)_ | 


**Exemplo:**

```javascript
var r = h.files.getAudio('filename.mp3');
```

---


### audioExists(name)
### videoExists(name)
### imageExists(name)
### fileExists(name)
Verifica se existe o arquivo com o nome informado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do arquivo (incluindo subpasta) |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
var r = h.files.audioExists('filename.mp3');
```

---


### exists(name)
Verifica se existe o arquivo com o nome informado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do arquivo (incluindo subpasta)<br>Deve começar com:  `audio/`  `video/`  `image/`  `file/` |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


---
