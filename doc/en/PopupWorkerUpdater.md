# PopupWorkerUpdater
Object that represents a running PopupWorker

---

- [Functions](#functions)
  - [setProgress](#setprogressprogress)
  - [setProgress](#setprogresscurrent-total)
  - [setMessage](#setmessagemessage)
  - [setLog](#setloglog)
  - [cancel](#cancel)


# Functions 
### setProgress(progress)
Updates the value of the progress bar

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `progress` | _Number_ | Progress bar value. `0 ~ 100` |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
evt.setProgress(70);
```

---


### setProgress(current, total)
Updates the value of the progress bar. The value will be calculated proportionally. `current / total * 100`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `current` | _Number_ |  |
| `total` | _Number_ |  |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
evt.setProgress(15, 40);
```

---


### setMessage(message)
Changes the message displayed in the progress window

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `message` | _String_ |  |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
evt.setMessage('Message');
```

---


### setLog(log)
Changes the message displayed above the progress bar

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `log` | _String_ |  |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
evt.setLog('log');
```

---


### cancel()
Cancels the execution of the task



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
evt.cancel();
```

---
