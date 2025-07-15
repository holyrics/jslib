# MidiSequence
Class to generate a MIDI sequence

---

- [Functions](#functions)
  - [add](#adddata)


# Functions 
### add(data)
Adds a MIDI message to the respective Track

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Object_ | It can be a `string`, an `array`, or an `object`<br><br> **string**<br>`"code,velocity,time_ms"`<br>The separator character can be `,:;`<br><br> **array**<br>`[code, velocity, time_ms]`<br><br> **object**<br>Object parameters<br>`code`<br>`velocity`<br>`time_ms`<br>`channel` __Optional__<br>`duration_ms` __Optional__<br>`action` __Optional__<br><br> <br> Allowed values for each parameter<br>**code:** `0 ~ 127` or the respective grade based on `C` `C#` `D` etc. <br>**velocity:** `0 ~ 127`<br>**time_ms:** Absolute time in milliseconds<br>**channel:** `0 ~ 15`<br>**duration_ms:** Duration of the note in milliseconds (if the message is `note_on`)<br>**action:** `note_on` `control_change` `program_change` `polyphonic_key_pressure` `channel_pressure` `pitch_bend_change` `midi_time_code` `song_position_pointer` `song_select` `tune_request` `timing_clock` `start` `continue` `stop` `active_sensing` `system_reset`<br> |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[MidiTrack](https://github.com/holyrics/jslib/blob/main/doc/en/MidiTrack.md)_ | `this` |


**Example:**

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
