# Module
Objeto que representa um módulo adicionado no programa

---



# Fields 
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `jscommunity_id` | _String_ | ID global do item no repositório JSCommunity<br>Nomes alternativos: `community_id` `jsc_id` |
| `info_id` | _String_ | ID definido para o item em `function info()`<br>Se o módulo for de origem do JSCommunity, o valor é o mesmo de `jscommunity_id` |
| `name` | _String_ | Nome do módulo |
| `active` | _Boolean_ | Se o módulo está ativo. active é um resultado de `enabled_by_user && conditional_execution` |
| `enabled_by_user` | _Boolean_ | Se o módulo está ativado pelo usuário (checkbox na interface) |
| `conditional_execution` | _Boolean_ | Se o módulo está ativado baseado nas possíveis execuções condicionais definidos a ele pelo usuário |
| `show_panel` | _Boolean_ | Exibir o módulo no painel Módulos |
| `available_in_main_window` | _Boolean_ | Módulo disponível para uso no painel da janela principal |
| `available_in_bible_window` | _Boolean_ | Módulo disponível para uso no painel da janela da Bíblia |
| `actions` | _Object_ | Mapa chave/valor<br>Cada chave é o id da ação e cada valor é um objeto `ModuleAction` [ModuleAction](https://github.com/holyrics/jslib/blob/main/doc/pt/ModuleAction.md) |


---

- [Functions](#functions)
  - [getID](#getid)
  - [getName](#getname)
  - [getActions](#getactions)
  - [getAction](#getactionaction_id)
  - [adminAction](#adminactionaction_type-security_token)


# Functions 
### getID()
ID do item



**Resposta:**

| Tipo  |
| :---: |
| _String_ | 


---


### getName()
Nome do item



**Resposta:**

| Tipo  |
| :---: |
| _String_ | 


---


### getActions()
Retorna a lista de ações disponíveis



**Resposta:**

| Tipo  |
| :---: |
| _Array&lt;[ModuleAction](https://github.com/holyrics/jslib/blob/main/doc/pt/ModuleAction.md)&gt;_ | 


**Exemplo:**

```javascript
var module = h.getModule('id');
var actions = module.getActions();
for (var i = 0; i < actions.length; i++) {
    //h.logp(list[i]);
    h.log(actions[i].id + " | " + actions[i].name);
}
```

---


### getAction(action_id)
Retorna uma ação específica

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action_id` | _String_ | ID da ação |


**Resposta:**

| Tipo  |
| :---: |
| _[ModuleAction](https://github.com/holyrics/jslib/blob/main/doc/pt/ModuleAction.md)_ | 


**Exemplo:**

```javascript
var module = h.getModule('id');
var action = module.getAction('action_id');
```

---


### adminAction(action_type, security_token)
Executar uma ação avançada em um módulo<br>O token de segurança pode ser obtido na janela de módulos, nos ícone de 3 pontinhos do respectivo módulo

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action_type` | _String_ | Tipo da ação<br>`update_panel` `repaint_panel` `restart` `enable` `disable` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `security_token` | _String_ | Token de segurança |


**Exemplo:**

```javascript
h.adminAction('restart', 'abcxyz');
```

---
