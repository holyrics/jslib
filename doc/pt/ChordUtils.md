# ChordUtils
Classe utilitária para alguns métodos de identificação e manipulação de acordes

---

- [Functions](#functions)
  - [isChord](#ischordvalue)
  - [changeKey](#changekeyvalue-step)
  - [identifyTonality](#identifytonalityvalue)


# Functions 
### isChord(value)
Verifica se a linha é uma linha de acordes musicais

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ | Texto que será analisado |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
var r = h.chord.isChord('Em  A  D'); //true
var r = h.chord.isChord('Em  Example  A  D'); //false
```

---


### changeKey(value, step)
Altera a tonalidade dos acordes

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ | Acordes que serão alterados |
| `step` | _Number_ | Quantidade de 'meios-tons' que será aumentada ou diminuída |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Tonalidade alterada |


**Exemplo:**

```javascript
var r = h.chord.changeKey('Em  A  D', -2);
h.log(r);
//output: Dm  G  C
```

---


### identifyTonality(value)
Identificar a tonalidade

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ | Texto que será analisado |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | `C` `C#` `D` `D#` `E` `F` `F#` `G` `G#` `A` `A#` `B` |


**Exemplo:**

```javascript
var r = h.chord.identifyTonality('Em  A  D');
h.log(r);
//output: D
```

---
