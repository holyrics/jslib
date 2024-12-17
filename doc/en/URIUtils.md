# URIUtils
Utility class to execute some actions via URI in the operating system, such as executing a streaming track

Example
```javascript
h.uri.youtube.track('umYQpAxL4dI');
```

Observação:<br>
A execução do áudio pode não ser automática, depende do próprio programa instalado no computador que vai receber a ação.<br>
Por exemplo, nos testes feitos, ao executar uma TRACK, o Spotify toca a faixa automaticamente, mas o Deezer não<br>

Porém ao executar uma PLAYLIST, o Spotify não toca a primeira faixa automaticamente

---

- [Functions](#functions)
  - [youtube.track](#youtubetrackid)
  - [youtube.playlist](#youtubeplaylistid)
  - [youtube.album](#youtubealbumid)
  - [spotify.artist](#spotifyartistid)


# Functions 
### youtube.track(id)
### spotify.track(id)
### deezer.track(id)
Executa uma faixa de áudio

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `false` para erro. ID inválido, por exemplo. |


---


### youtube.playlist(id)
### spotify.playlist(id)
### deezer.playlist(id)
Executa uma playlist

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `false` para erro. ID inválido, por exemplo. |


---


### youtube.album(id)
### spotify.album(id)
### deezer.album(id)
Executa um álbum

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `false` para erro. ID inválido, por exemplo. |


---


### spotify.artist(id)
### deezer.artist(id)
Abre a página do artista

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `false` para erro. ID inválido, por exemplo. |


---
