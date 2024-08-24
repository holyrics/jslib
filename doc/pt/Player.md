# Player
Classe player para obter informações e executar ações no player do programa

Exemplo
```javascript
var r = h.getPlayer();
if (r.isPlaying()) {
    h.log('O player está em execução');
} else {
    h.log('O player não está em execução');
}

//alterar volume
r.setVolume(80);

//deixar no mudo
r.setMute(true);

//parar execução atual
r.stop();
```

---

- [Functions](#functions)
  - [getMediaName](#getmedianame)
  - [getMedia](#getmedia)
  - [isPlaying](#isplaying)
  - [getDuration](#getduration)
  - [getCurrentTime](#getcurrenttime)
  - [setCurrentTime](#setcurrenttimetime)
  - [getTimeElapsed](#gettimeelapsed)
  - [getTimeRemaining](#gettimeremaining)
  - [play](#play)
  - [pause](#pause)
  - [stop](#stop)
  - [next](#next)
  - [previous](#previous)
  - [isRepeat](#isrepeat)
  - [setRepeat](#setrepeatrepeat)
  - [isExecuteAll](#isexecuteall)
  - [setExecuteAll](#setexecuteallexecuteall)
  - [isExecuteSingle](#isexecutesingle)
  - [setExecuteSingle](#setexecutesingleexecutesingle)
  - [isShuffle](#isshuffle)
  - [setShuffle](#setshuffleshuffle)
  - [isFullscreen](#isfullscreen)
  - [setFullscreen](#setfullscreenfullscreen)
  - [getVolume](#getvolume)
  - [setVolume](#setvolumevolume)
  - [isMute](#ismute)
  - [setMute](#setmutemute)


# Functions 
### getMediaName()
Nome da mídia atual no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Nome da mídia |


---


### getMedia()
Caminho completo da mídia no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Caminho completo da mídia |


---


### isPlaying()
Verifica se o player está em execução



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### getDuration()
Tempo total da mídia atual no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Tempo total em milissegundos |


---


### getCurrentTime()
Tempo atual da mídia no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Tempo atual da mídia em milissegundos |


---


### setCurrentTime(time)
- v2.20.0

Alterar o tempo atual da mídia em milissegundos

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `time` | _Number_ | Alterar o tempo atual da mídia em milissegundos |


_Método sem retorno_

---


### getTimeElapsed()
Tempo decorrido da mídia no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Tempo decorrido no formato HH:MM:SS |


---


### getTimeRemaining()
Tempo restante da mídia no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Tempo restante no formato HH:MM:SS |


---


### play()
Executar a ação **play** do player



_Método sem retorno_

---


### pause()
Executar a ação **pause** do player



_Método sem retorno_

---


### stop()
Executar a ação **stop** do player



_Método sem retorno_

---


### next()
Passa para o próximo item da lista no player



_Método sem retorno_

---


### previous()
Passa para o item anterior da lista no player



_Método sem retorno_

---


### isRepeat()
Verifica se a opção **repetir** está ativada



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setRepeat(repeat)
Altera a opção **repetir**

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `repeat` | _Boolean_ |  |


_Método sem retorno_

---


### isExecuteAll()
Verifica se o player está definido para executar itens em sequência



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setExecuteAll(executeAll)
Altera a configuração do player para executar itens em sequência

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `executeAll` | _Boolean_ |  |


_Método sem retorno_

---


### isExecuteSingle()
Verifica se o player está definido para executar somente o item atual da lista



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setExecuteSingle(executeSingle)
Altera a configuração do player para executar somente o item atual da lista

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `executeSingle` | _Boolean_ |  |


_Método sem retorno_

---


### isShuffle()
Verifica se a opção **aleatório** está ativada



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setShuffle(shuffle)
Altera a opção **aleatório**

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `shuffle` | _Boolean_ |  |


_Método sem retorno_

---


### isFullscreen()
Verifica se a opção **tela cheia** está ativada



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setFullscreen(fullscreen)
Altera a opção **tela cheia** do player

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `fullscreen` | _Boolean_ |  |


_Método sem retorno_

---


### getVolume()
Volume atual do player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Volume. Mínimo=0, Máximo=100 |


---


### setVolume(volume)
Altera o volume do player

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `volume` | _Number_ | Mínimo=0, Máximo=100 |


_Método sem retorno_

---


### isMute()
Verifica se a opção **mudo** está ativada



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setMute(mute)
Altera a opção **mudo**

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `mute` | _Boolean_ |  |


_Método sem retorno_

---
