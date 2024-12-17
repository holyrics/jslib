# PopupWorkerUpdater
Objeto que representa um PopupWorker em execução

---

- [Functions](#functions)
  - [setProgress](#setprogressprogress)
  - [setProgress](#setprogresscurrent-total)
  - [setMessage](#setmessagemessage)
  - [setLog](#setloglog)
  - [cancel](#cancel)


# Functions 
### setProgress(progress)
Atualiza o valor da barra de progresso

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `progress` | _Number_ | Valor da barra de progresso. `0 ~ 100` |


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
Atualiza o valor da barra de progresso. O valor será calculado de forma proporcional. `current / total * 100`

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
Altera a mensagem exibida na janela de progresso

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
Altera a mensagem exibida em cima da barra de progresso

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
Cancela a execução da tarefa



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
evt.cancel();
```

---
