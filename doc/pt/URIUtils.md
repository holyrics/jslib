# URIUtils
Classe utilitária para executar algumas ações via URI no sistema operacional, como por exemplo, executar uma track de streaming

Exemplo
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

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `false` para erro. ID inválido, por exemplo. |


---


### youtube.playlist(id)
### spotify.playlist(id)
### deezer.playlist(id)
Executa uma playlist

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `false` para erro. ID inválido, por exemplo. |


---


### youtube.album(id)
### spotify.album(id)
### deezer.album(id)
Executa um álbum

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `false` para erro. ID inválido, por exemplo. |


---


### spotify.artist(id)
### deezer.artist(id)
Abre a página do artista

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | `false` para erro. ID inválido, por exemplo. |


---
