# AutomaticPresentationPlayer
Classe que representa o player da apresentação automática do programa

Exemplo
```javascript
var r = h.getAPPlayer();
if (r.isPlaying()) {
    h.logf('Total time: {} - Slide time: {}', r.getTime(), r.getSlide().getTime());
}
```

---

- [Functions](#functions)
  - [getName](#getname)
  - [isPlaying](#isplaying)
  - [getVolume](#getvolume)
  - [isMute](#ismute)
  - [getTime](#gettime)
  - [getDuration](#getduration)
  - [play](#play)
  - [pause](#pause)
  - [stop](#stop)
  - [setVolume](#setvolumevolume)
  - [setMute](#setmutemute)
  - [setCurrentTime](#setcurrenttimetime)
  - [getSlide](#getslide)


# Functions 
### getName
- v2.23.0

Nome da mídia atual no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Nome da mídia |


---


### isPlaying()
- v2.23.0

Verifica se o player está em execução



**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


---


### getVolume()
- v2.23.0

Volume atual do player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Volume. Mínimo=0, Máximo=100 |


---


### isMute()
- v2.23.0

Verifica se a opção **mudo** está ativada



**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


---


### getTime()
- v2.23.0

Tempo atual da mídia no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Tempo atual da mídia em milissegundos |


---


### getDuration()
- v2.23.0

Tempo total da mídia atual no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Tempo total em milissegundos |


---


### play()
- v2.29.0

Executar a ação **play** do player



_Método sem retorno_

---


### pause()
- v2.29.0

Executar a ação **pause** do player



_Método sem retorno_

---


### stop()
- v2.29.0

Executar a ação **stop** do player



_Método sem retorno_

---


### setVolume(volume)
- v2.29.0

Altera o volume do player

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `volume` | _Number_ | Mínimo=0, Máximo=100 |


_Método sem retorno_

---


### setMute(mute)
- v2.29.0

Altera a opção **mudo**

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `mute` | _Boolean_ |  |


_Método sem retorno_

---


### setCurrentTime(time)
- v2.29.0

Alterar o tempo atual da mídia em milissegundos

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `time` | _Number_ | Alterar o tempo atual da mídia em milissegundos |


_Método sem retorno_

---


### getSlide()
- v2.23.0

Informação sobre o slide atual em exibição



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[AutomaticPresentationSlideInfo](https://github.com/holyrics/jslib/blob/main/doc/pt/AutomaticPresentationSlideInfo.md)_ | Slide atual em exibição. Pode ser null. |


---
