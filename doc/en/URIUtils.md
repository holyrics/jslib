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
Plays an audio track

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `false` for error Invalid ID for example. |


---


### youtube.playlist(id)
### spotify.playlist(id)
### deezer.playlist(id)
Plays a playlist

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `false` for error Invalid ID for example. |


---


### youtube.album(id)
### spotify.album(id)
### deezer.album(id)
Plays an album

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `false` for error Invalid ID for example. |


---


### spotify.artist(id)
### deezer.artist(id)
Open the artist's page

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `false` for error Invalid ID for example. |


---
