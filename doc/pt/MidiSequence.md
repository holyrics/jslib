# MidiSequence
Classe para gerar uma sequência MIDI

---

- [Functions](#functions)
  - [createTrack](#createtrackbpm--120)
  - [getTracks](#gettracks)
  - [save](#savesettings--null)
  - [setBaseOctave](#setbaseoctavebaseoctave)


# Functions 
### createTrack(bpm = 120)
Cria uma track na sequência MIDI

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `bpm` | _Object (opcional)_ | BPM `Padrão: 120` |


**Resposta:**

| Tipo  |
| :---: |
| _[MidiTrack](https://github.com/holyrics/jslib/blob/main/doc/pt/MidiTrack.md)_ | 


**Exemplo:**

```javascript
var seq = h.createMidiSequence();
var track = seq.createTrack(120);
```

---


### getTracks()
Retorna a lista de `tracks` criadas



**Resposta:**

| Tipo  |
| :---: |
| _Array&lt;[MidiTrack](https://github.com/holyrics/jslib/blob/main/doc/pt/MidiTrack.md)&gt;_ | 


---


### save(settings = null)
Salva a sequência MIDI em um arquivo

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `settings` | _Object (opcional)_ |  |
| `settings.name` | _Object (opcional)_ | Nome do arquivo `Padrão: YYYY-MM-DD_HH-MM-SS` |
| `settings.ignore_notification` | _Boolean (opcional)_ | Ignorar notificação de arquivo salvo `Padrão: false` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna `true` se o arquivo foi salvo.<br>Retorna uma mensagem de erro se o arquivo não foi salvo. |


**Exemplo:**

```javascript
seq.save({
    name: 'filename'
});
```

---


### setBaseOctave(baseOctave)
Altera a oitava base, utilizado como parâmetro ao adicionar uma mensagem MIDI baseada em notas `CDEFGAB`

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `baseOctave` | _Number_ | Valores disponíveis: `-1` `-2` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[MidiSequence](https://github.com/holyrics/jslib/blob/main/doc/pt/MidiSequence.md)_ | `this` |


---
