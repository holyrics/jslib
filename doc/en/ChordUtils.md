# ChordUtils
Utility class for some methods of identification and manipulation of chords

---

- [Functions](#functions)
  - [isChord](#ischordvalue)
  - [changeKey](#changekeyvalue-step)
  - [identifyTonality](#identifytonalityvalue)


# Functions 
### isChord(value)
Checks if the line is a line of musical chords

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Text that will be analyzed |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
var r = h.chord.isChord('Em  A  D'); //true
var r = h.chord.isChord('Em  Example  A  D'); //false
```

---


### changeKey(value, step)
Changes the tone of the chords

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Chords that will be changed |
| `step` | _Number_ | Amount of 'half-tones' that will be increased or decreased |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Altered tone |


**Example:**

```javascript
var r = h.chord.changeKey('Em  A  D', -2);
h.log(r);
//output: Dm  G  C
```

---


### identifyTonality(value)
Identify the tone

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Text that will be analyzed |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | `C` `C#` `D` `D#` `E` `F` `F#` `G` `G#` `A` `A#` `B` |


**Example:**

```javascript
var r = h.chord.identifyTonality('Em  A  D');
h.log(r);
//output: D
```

---
