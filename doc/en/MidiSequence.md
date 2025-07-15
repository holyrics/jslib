# MidiSequence
Class to generate a MIDI sequence

---

- [Functions](#functions)
  - [createTrack](#createtrackbpm--120)
  - [getTracks](#gettracks)
  - [save](#savesettings--null)
  - [setBaseOctave](#setbaseoctavebaseoctave)


# Functions 
### createTrack(bpm = 120)
Create a track in the MIDI sequence

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `bpm` | _Object (optional)_ | BPM `Default: 120` |


**Response:**

| Type  |
| :---: |
| _[MidiTrack](https://github.com/holyrics/jslib/blob/main/doc/en/MidiTrack.md)_ | 


**Example:**

```javascript
var seq = h.createMidiSequence();
var track = seq.createTrack(120);
```

---


### getTracks()
Returns the list of created `tracks`



**Response:**

| Type  |
| :---: |
| _Array&lt;[MidiTrack](https://github.com/holyrics/jslib/blob/main/doc/en/MidiTrack.md)&gt;_ | 


---


### save(settings = null)
Save the MIDI sequence to a file

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `settings` | _Object (optional)_ |  |
| `settings.name` | _Object (optional)_ | File name `Default: YYYY-MM-DD_HH-MM-SS` |
| `settings.ignore_notification` | _Boolean (optional)_ | Ignore saved file notification `Default: false` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns `true` if the file was saved.<br>Returns an error message if the file was not saved. |


**Example:**

```javascript
seq.save({
    name: 'filename'
});
```

---


### setBaseOctave(baseOctave)
Changes the eighth base, used as a parameter when adding a MIDI message based on notes `CDEFGAB`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `baseOctave` | _Number_ | Available values: `-1` `-2` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[MidiSequence](https://github.com/holyrics/jslib/blob/main/doc/en/MidiSequence.md)_ | `this` |


---
