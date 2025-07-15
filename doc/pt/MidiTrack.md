# MidiSequence
Classe para gerar uma sequência MIDI

---

- [Functions](#functions)
  - [add](#adddata)


# Functions 
### add(data)
Adiciona uma mensagem MIDI na respectiva Track

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Object_ | Pode ser uma `string`, um `array` ou um `object`<br><br> **string**<br>`"code,velocity,time_ms"`<br>O caractere separador pode ser `,:;`<br><br> **array**<br>`[code, velocity, time_ms]`<br><br> **object**<br>Parâmetros do objeto<br>`code`<br>`velocity`<br>`time_ms`<br>`channel` __Opcional__<br>`duration_ms` __Opcional__<br>`action` __Opcional__<br><br> <br> Valores permitidos para cada parâmetro<br>**code:** `0 ~ 127` ou a respectiva nota baseada em `C` `C#` `D` etc. <br>**velocity:** `0 ~ 127`<br>**time_ms:** Tempo absoluto em milissegundos<br>**channel:** `0 ~ 15`<br>**duration_ms:** Duração da nota em milissegundos (caso a mensagem seja `note_on`)<br>**action:** `note_on` `control_change` `program_change` `polyphonic_key_pressure` `channel_pressure` `pitch_bend_change` `midi_time_code` `song_position_pointer` `song_select` `tune_request` `timing_clock` `start` `continue` `stop` `active_sensing` `system_reset`<br> |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[MidiTrack](https://github.com/holyrics/jslib/blob/main/doc/pt/MidiTrack.md)_ | `this` |


**Exemplo:**

```javascript
var seq = h.createMidiSequence();
var track = seq.createTrack(120);
var data = {
    code: 10,
    velocity: 127,
    time_ms: 1000
};
track.add(data);
track.add("15,127,2000");
```

---
