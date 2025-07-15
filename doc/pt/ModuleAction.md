# ModuleAction
Objeto que representa uma ação pública de um módulo adicionado no programa

---



# Fields 
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |
| `description` | _String_ | Descrição do item |
| `available_for` | _String_ | Lista de origens que a ação está disponível.<br>Se o campo estiver vazio, significa que a ação está disponível para todas as origens.<br>Valores disponíveis: `ui` `trigger` `jslib_call` `jslib_open` `add_to_playlist` |
| `unavailable_for` | _Boolean_ | Lista de origens que a ação está indisponível.<br>Valores disponíveis: `ui` `trigger` `jslib_call` `jslib_open` `add_to_playlist` |
| `input` | _Object_ | Lista de parâmetros requeridos para execução da ação |


---

- [Functions](#functions)
  - [call](#callinput--null)
  - [callEx](#callexinput--null)
  - [callAsync](#callasyncinput--null-callback--null)
  - [open](#openinput--null-callback--null)
  - [openAndWait](#openandwaitinput--null)
  - [openAndWaitEx](#openandwaitexinput--null)
  - [openNotification](#opennotificationinput--null-callback--null)
  - [openNotificationAndWait](#opennotificationandwaitinput--null)
  - [openNotificationAndWaitEx](#opennotificationandwaitexinput--null)


# Functions 
### call(input = null)
Executar a ação e obter a resposta.<br>Retorna `null` se houver erro.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object_ | Mapa chave/valor<br>Parâmetros para execução da ação |


_Método sem retorno_

**Exemplo:**

```javascript
var module = h.getModule('id');
var action = module.getAction('action_id');
var params = {
    /* ... */
};
var r = action.call(params);
```

---


### callEx(input = null)
Executar a ação e obter a resposta.<br>Gera **Exception** se houver erro.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object_ | Mapa chave/valor<br>Parâmetros para execução da ação |


_Método sem retorno_

**Exemplo:**

```javascript
try {
    var params = {
      /* ... */
    };
    action.callEx(params);
} catch (e) {
    h.log(e);
}
```

---


### callAsync(input = null, callback = null)
Executar a ação e obter a resposta.<br>Execução assíncrona.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object_ | Mapa chave/valor<br>Parâmetros para execução da ação |
| `callback` | _Function (opcional)_ | Método que será executado com a resposta da requisição ou com a mensagem de erro.<br>`function(result, error) { /* ... */ }` |


_Método sem retorno_

**Exemplo:**

```javascript
var params = {
    /* ... */
};
action.callAsync(params, function() {
    //callback
});
```

---


### open(input = null, callback = null)
Abre uma janela para o usuário inserir/editar os inputs e executar a ação.<br>Execução assíncrona.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object_ | Mapa chave/valor<br>Parâmetros para execução da ação |
| `callback` | _Function (opcional)_ | Método que será executado com a resposta da requisição ou com a mensagem de erro.<br>`function(result, error) { /* ... */ }` |


_Método sem retorno_

**Exemplo:**

```javascript
var params = {
    /* ... */
};
action.open(params, function() {
    //callback
});
```

---


### openAndWait(input = null)
Abre uma janela para o usuário inserir/editar os inputs e executar a ação..<br>Aguarda a resposta da ação.<br>Retorna `null` se houver erro.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object_ | Mapa chave/valor<br>Parâmetros para execução da ação |


_Método sem retorno_

**Exemplo:**

```javascript
var params = {
    /* ... */
};
action.openAndWait(params);
```

---


### openAndWaitEx(input = null)
Abre uma janela para o usuário inserir/editar os inputs e executar a ação.<br>Aguarda a resposta da ação.<br>Gera **Exception** se houver erro.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object_ | Mapa chave/valor<br>Parâmetros para execução da ação |


_Método sem retorno_

**Exemplo:**

```javascript
var params = {
    /* ... */
};
action.openAndWaitEx(params);
```

---


### openNotification(input = null, callback = null)
Exibe uma notificação no canto da tela para o usuário inserir/editar os inputs e executar a ação.<br>Execução assíncrona.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object_ | Mapa chave/valor<br>Parâmetros para execução da ação |
| `callback` | _Function (opcional)_ | Método que será executado com a resposta da requisição ou com a mensagem de erro.<br>`function(result, error) { /* ... */ }` |


_Método sem retorno_

**Exemplo:**

```javascript
var params = {
    /* ... */
};
action.openNotification(params, function() {
    //callback
});
```

---


### openNotificationAndWait(input = null)
Exibe uma notificação no canto da tela para o usuário inserir/editar os inputs e executar a ação.<br>Aguarda a resposta da ação.<br>Retorna `null` se houver erro.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object_ | Mapa chave/valor<br>Parâmetros para execução da ação |


_Método sem retorno_

**Exemplo:**

```javascript
var params = {
    /* ... */
};
action.openNotificationAndWait(params);
```

---


### openNotificationAndWaitEx(input = null)
Exibe uma notificação no canto da tela para o usuário inserir/editar os inputs e executar a ação.<br>Aguarda a resposta da ação.<br>Gera **Exception** se houver erro.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object_ | Mapa chave/valor<br>Parâmetros para execução da ação |


_Método sem retorno_

**Exemplo:**

```javascript
var params = {
    /* ... */
};
action.openNotificationAndWaitEx(params);
```

---
