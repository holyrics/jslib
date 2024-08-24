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
  - [getSlide](#getslide)


# Functions 
### getName()
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

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


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

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


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


### getSlide()
- v2.23.0

Informação sobre o slide atual em exibição

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
|  | _[AutomaticPresentationSlideInfo](https://github.com/holyrics/jslib/blob/main/doc/pt/AutomaticPresentationSlideInfo.md)_ | Slide atual em exibição. Pode ser null. |


_Método sem retorno_

---
