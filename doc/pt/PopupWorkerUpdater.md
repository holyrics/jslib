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

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `progress` | _Number_ | Valor da barra de progresso. `0 ~ 100` |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
evt.setProgress(70);
```

---


### setProgress(current, total)
Atualiza o valor da barra de progresso. O valor será calculado de forma proporcional. `current / total * 100`

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `current` | _Number_ |  |
| `total` | _Number_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
evt.setProgress(15, 40);
```

---


### setMessage(message)
Altera a mensagem exibida na janela de progresso

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `message` | _String_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
evt.setMessage('Message');
```

---


### setLog(log)
Altera a mensagem exibida em cima da barra de progresso

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `log` | _String_ |  |


**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
evt.setLog('log');
```

---


### cancel()
Cancela a execução da tarefa



**Resposta:**

| Tipo  |
| :---: |
| _Boolean_ | 


**Exemplo:**

```javascript
evt.cancel();
```

---
