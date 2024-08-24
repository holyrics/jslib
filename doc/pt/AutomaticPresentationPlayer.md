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
  - [getSlide](#getslidegetnumber)
  - [getSlide](#getslidegettext)
  - [getSlide](#getslidegetdescription)
  - [getSlide](#getslidegetstart)
  - [getSlide](#getslidegetend)
  - [getSlide](#getslidegetduration)
  - [getSlide](#getslidegettime)


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
|  | _Object_ | Slide atual em exibição. Pode ser null. |


_Método sem retorno_

---


### getSlide().getNumber()
- v2.23.0



**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
|  | _Number_ | Número do slide. Começa em zero |


_Método sem retorno_

---


### getSlide().getText()
- v2.23.0



**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
|  | _String_ | Texto do slide |


_Método sem retorno_

---


### getSlide().getDescription()
- v2.23.0



**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
|  | _String_ | Descrição do slide |


_Método sem retorno_

---


### getSlide().getStart()
- v2.23.0



**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
|  | _Number_ | Tempo inicial da apresentação em milissegundos |


_Método sem retorno_

---


### getSlide().getEnd()
- v2.23.0



**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
|  | _Number_ | Tempo final da apresentação em milissegundos |


_Método sem retorno_

---


### getSlide().getDuration()
- v2.23.0



**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
|  | _Number_ | Duração em milissegundos |


_Método sem retorno_

---


### getSlide().getTime()
- v2.23.0



**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
|  | _Number_ | Tempo atual do slide. `time >= 0 && time <= duration` |


_Método sem retorno_

---
