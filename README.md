# jslib

**PT** | [EN](README-en.md)

Métodos da classe JSLib disponível para uso nos scripts do programa Holyrics.

É possível utilizar a variável ```jslib``` ou a variável ```h``` para acessar os métodos disponíveis.

Por exemplo:

```
jslib.log('exemplo');
h.log('exemplo');
```
# Métodos 
### log(obj)
Exibe a informação passada como parâmetro numa janela de log (canto inferior direito da tela, geralmente)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `obj` | _Object_ | Qualquer objeto para ser exibido na janela de log |


_Método sem retorno_

**Exemplo:**

```javascript
h.log('mensagem de log');
```

---


### sleep(time)
Pausa a execução em X milissegundos, conforme o valor especificado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `time` | _Number_ | Valor em milissegundos. Mínimo=0, Máximo=60000 |


_Método sem retorno_

**Exemplo:**

```javascript
h.sleep(200); //200ms
```

---


### base64Encode(bytes)
Codifica um array de bytes em string base64

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `bytes` | _Array&lt;byte&gt;_ | array de bytes |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | String em formato base64 |


---


### base64Decode(str)
Decodifica uma string em formato base64

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `str` | _String_ | String em base64 |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;byte&gt;_ | Array de bytes decodificado |


---


### md5(value)
Hash MD5 em array de bytes

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Object_ | Valor que será calculado. Pode ser string ou array de bytes |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;byte&gt;_ | hash MD5 |


---


### md5Str(value)
Hash MD5

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Object_ | Valor que será calculado. Pode ser string ou array de bytes |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | hash MD5 |


---


### sha256(value)
Hash SHA-256 em array de bytes

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Object_ | Valor que será calculado. Pode ser string ou array de bytes |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;byte&gt;_ | hash SHA-256 |


---


### sha256Str(value)
Hash SHA-256

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Object_ | Valor que será calculado. Pode ser string ou array de bytes |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | hash SHA-256 |


---


### getClipboard()
Obtém o texto da área de transferência do sistema operacional



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Texto da área de transferência |


**Exemplo:**

```javascript
var val = h.getClipboard();
h.log('Texto da área de transferência: ' + val);
```

---


### normalize(str)
Remove a acentuação da string



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | String sem acentuação |


**Exemplo:**

```javascript
var r = h.normalize("ÁÉÍÓÚÇáéíóúç");
h.log('Texto com acentuação removida: ' + r); //AEIOUCaeiouc
```

---


### store(key, value)
Salva uma string em disco que pode ser recuperada mesmo após reiniciar o programa. O método é compartilhado com todos os scripts do programa.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id para salvar a string |
| `value` | _String_ | String que será salva |


_Método sem retorno_

**Exemplo:**

```javascript
h.store('abc', 'Exemplo');
```

---


### restore(key)
Recupera uma string salva em disco. O método é compartilhado com todos os scripts do programa.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id da string salva anteriormente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Retorna a string salva ou NULL se não for encontrado |


**Exemplo:**

```javascript
var r = h.restore('abc');
if (r == null) {
    h.log('Item abc não encontrado');
} else {
    h.log('Item abc: ' + r);
}
```

---


### setGlobal(key, value)
Salva um objeto na memória que pode ser recuperado, mas é válido somente enquanto o programa estiver aberto. O método é compartilhado com todos os scripts do programa.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id do objeto salvo |
| `value` | _Object_ | Objeto que será salvo na memória |


_Método sem retorno_

**Exemplo:**

```javascript
h.setGlobal('xyz', 'Exemplo');
```

---


### getGlobal(key, default = null)
Recupera um objeto salvo na memória. O método é compartilhado com todos os scripts do programa.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id do objeto salvo na memória |
| `default` | _Object (opcional)_ | Valor padrão se não for encontrado valor salvo anteriormente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna o objeto salvo ou **default** se não for encontrado |


**Exemplo:**

```javascript
var r = h.getGlobal('xyz');
if (r == null) {
    h.log('Item xyz não encontrado');
} else {
    h.log('Item xyz: ' + r);
}

var r2 = h.getGlobal('xyz', 'valor padrão');
h.log('Item xyz: ' + r2);
```

---


### setCache(key, value)
Salva um objeto na memória que pode ser recuperado, mas é válido somente enquanto o programa estiver aberto. O método é válido somente para o script atual.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id do objeto salvo |
| `value` | _Object_ | Objeto que será salvo na memória |


_Método sem retorno_

**Exemplo:**

```javascript
h.setCache('123', 'Exemplo');
```

---


### getCache(key, default = null)
Recupera um objeto salvo na memória. O método é válido somente para o script atual.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id do objeto salvo na memória |
| `default` | _Object (opcional)_ | Valor padrão se não for encontrado valor salvo anteriormente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna o objeto salvo ou **default** se não for encontrado |


**Exemplo:**

```javascript
var r = h.getCache('123');
if (r == null) {
    h.log('Item 123 não encontrado');
} else {
    h.log('Item 123: ' + r);
}

var r2 = h.getCache('123', 'valor padrão');
h.log('Item 123: ' + r2);
```

---


### random(min, max, keySafeRepeat = null)
Gera um número aleatório

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `min` | _String_ | valor mínimo |
| `max` | _Object_ | Valor máximo |
| `keySafeRepeat` | _Object (opcional)_ | Pode ser utilizado para evitar número repetido sorteado em sequência |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Retorna um número aleatório de **min** a **max** |


**Exemplo:**

```javascript
var r = h.random(0, 10);
h.log('Número aleatório de 0 a 10: ' + r);
//O número sorteado pode ser repetido
r = h.random(0, 10);
h.log('Número aleatório de 0 a 10: ' + r);

//Para evitar repetição:
var r = h.random(0, 10, 'xyz');
h.log('Número aleatório de 0 a 10: ' + r);
//O número sorteado não será repetido
r = h.random(0, 10, 'xyz');
h.log('Número aleatório de 0 a 10: ' + r);

//A mecânica de não repetir também funciona quando o script for executado novamente
//e não apenas em execuções em sequência como no exemplo acima
```

---


### startTimer(key)
Inicia um timer

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id do timer |


_Método sem retorno_

**Exemplo:**

```javascript
h.startTimer('xyz');
h.sleep(2000); //2 segundos
var r = h.getTimer('xyz');
h.log('Tempo decorrido: ' + r); //provavelmente 00:00:02

//é um método global, o valor pode ser utilizado em qualquer outro script utilizando a mesma chave
```

---


### getTimer(key)
Recupera quanto tempo foi decorrido em um timer de acordo com o valor **key**. Se o timer não tiver sido iniciado, o método iniciará o timer e retornará 00:00:00

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id do timer |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Tempo decorrido no formato HH:MM:SS |


**Exemplo:**

```javascript
var r = h.getTimer('xyz');
h.log('Tempo decorrido: ' + r);
```

---


### getPlaylistInfo()
Obtém a lista de reprodução atualmente selecionada no programa



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | Tipo do evento da lista de reprodução. Pode ser: temporary, service, event |
| `name` | _String_ | Nome do evento |
| `datetime` | _String_ | Data e hora do item no formato: YYYY-MM-DD HH:MM |


**Exemplo:**

```javascript
var r = h.getPlaylistInfo();
h.log(r.name + ' - ' + r.datetime);
switch (r.type) {
    case 'temporary':
        h.log('A lista de reprodução é temporária');
        break;
    case 'service':
        h.log('A lista de reprodução é de um culto');
        break;
    case 'event':
        h.log('A lista de reprodução é de um evento');
        break;
}
```

---


### getPlayer()
Classe player para obter informações e executar ações no player do programa



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[Player](#métodos-player)_ | Objeto da classe Player |


**Exemplo:**

```javascript
var r = h.getPlayer();
if (r.isPlaying()) {
    h.log('O player está em execução');
} else {
    h.log('O player não está em execução');
}

//alterar volume
r.setVolume(80);

//deixar no mudo
r.setMute(true);

//parar execução atual
r.stop();
```

---


### scriptAction(id)
Executa a ação de um item **Script** existente no programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | id do item |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | Retorna **false** se o item não for encontrado |


**Exemplo:**

```javascript
var r = h.scriptAction('abcxyz');
if (r) {
    h.log('Ação executada');
} else {
    h.log('Item abcxyz não econtrado');
}
```

---


### apiAction(id)
Executa a ação de um item API existente no programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | id do item |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | Retorna **false** se o item não for encontrado |


**Exemplo:**

```javascript
var r = h.apiAction('abcxyz');
if (r) {
    h.log('Ação executada');
} else {
    h.log('Item abcxyz não econtrado');
}
```

---


### apiRequest(id, raw)
Executa uma requisição para o receptor associado e retorna a resposta do receptor. Válido somente para receptores URL

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | id do receptor |
| `raw` | _Object_ | dados da requisição |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorno da requisição ou NULL para erro/timeout |


**Exemplo:**

```javascript
//É possível realizar requisição diretamente para um receptor criado
//Por exemplo:
//Considerando que você tenha um receptor criado para comunicação com OBS Studio
//via websocket e o ID do receptor seja 'abcyxz', você pode fazer uma requisição
//como no exemplo abaixo
var r = h.apiRequest('abcxyz', {
    'request-type': 'GetSourceActive',
    'sourceName': 'exemplo'
});
h.log('Resposta da requisição: ' + r);
var obj = JSON.parse(r);
if (obj.sourceActive) {
    h.log('A fonte exemplo está ativa');
} else {
    h.log('A fonte exemplo não está ativa');
}
```

---


# Métodos HLY


Todas as requisições dos métodos hly(...) retornam um objeto padrão:
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `status` | _String_ | Pode ser *'ok'* ou *'error'* |
| `error` | _String (opcional)_ | Mensagem de erro se *status* for igual a *error* |
| `data` | _Object (opcional)_ | Conteúdo da resposta se *status* for igual a *ok* |


---

### hly('GetCurrentBackground')
Retorna o plano de fundo da apresentação em exibição.



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[Background](#background)_ | Plano de fundo atual ou NULL se não houver apresentação em exibição |


**Exemplo:**

```javascript
var r = h.hly('GetCurrentBackground');
if (r.data != null) {
    h.log('ID do plano de fundo atual: ' + r.data.id);
} else {
    h.log('Não há apresentação em exibição');
}
```

---


### hly('GetLyrics', input)
### hly('GetSong', input)
Retorna uma música.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID da música |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[Lyrics](#lyrics)_ | Música ou NULL se não for encontrado |


**Exemplo:**

```javascript
var r = h.hly('GetLyrics', {id: '123'});
if (r.data == null) {
    h.log('Item 123 não encontrado');
} else {
    h.log('Item 123:');
    h.log(r.data);
}
```

---


### hly('GetLyricsPlaylist')
### hly('GetSongPlaylist')
Lista de reprodução de letras



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Lyrics](lyrics)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetLyricsPlaylist');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].title);
}
```

---


### hly('GetMediaPlaylist')
Lista de reprodução de mídia



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Item](#item)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetMediaPlaylist');
for (var i = 0; i < r.data.length; i++) {
    var item = r.data[i];
    h.log(item.type + ": " + item.name);
}
```

---


### hly('GetBackgrounds', input)
Lista dos temas e planos de fundo

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object (opcional)_ | Filtro |
| `input.type` | _String (opcional)_ | Pode ser: theme, my_video, my_image, video, image |
| `input.tag` | _String (opcional)_ |  |
| `input.tags` | _Array&lt;String&gt; (opcional)_ |  |
| `input.intersection` | _Boolean (opcional)_ | Se o campo **input.tags** estiver preenchido com múltiplos itens, a opção **input.intersection** define o tipo de junção. Se **true**, o filtro retornará apenas itens que contém **todas** as tags informadas, se **false**, o filtro retornará os itens que têm pelo menos uma tag das tags informadas _(Padrão=*false*)_ |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Background](#background)&gt;_ |  |


**Exemplo:**

```javascript
//todos
var r = h.hly('GetBackgrounds', {});
for (var i = 0; i < r.data.length; i++) {
    var bg = r.data[i];
    h.log(bg.type + ": " + bg.name);
}

//somente "Meus Vídeos" e com as tags 'água' E 'azul'
r = h.hly('GetBackgrounds', {
    type: 'my_video',
    tags: ['água', 'azul'],
    intersection: true
});
for (var i = 0; i < r.data.length; i++) {
    var bg = r.data[i];
    h.log(bg.name);
}
```

---


### hly('GetFavorites')
Itens da barra de favoritos



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Favorite Item](#favorite_item)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetFavorites');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetHistories')
Histórico de todas as marcações de "Música tocada"



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.music_id` | _String_ | ID da música |
| `data.*.history` | _Array&lt;String&gt;_ | Date e hora no formato YYYY-MM-DD HH:MM |


**Exemplo:**

```javascript
var r = h.hly('GetHistories');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].music_id);
    h.log(r.data[i].history);
}
```

---


### hly('GetHistory', input)
Histórico de "Música tocada"

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID da letra da música |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;String&gt;_ | Data e hora no formato YYYY-MM-DD HH:MM |


**Exemplo:**

```javascript
var r = h.hly('GetHistory', {id: '123'});
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i]);
}
```

---


### hly('GetMembers')
Lista de integrantes



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Member](#member)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetMembers');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetRoles')
Lista de funções



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Role](#role)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetRoles');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetCurrentSchedule')
Programação atual (selecionada na janela principal do programa)



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[Schedule](#schedule)_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetCurrentSchedule');
for (var i = 0; i < r.data.length; i++) {
    var s = r.data[i];
    h.log(s.datetime);
    h.log(s.name);
    h.log(s.lyrics_playlist);
    h.log(s.media_playlist);
}
```

---


### hly('GetSchedules')
Retorna a lista de programação de um mês específico

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.month` | _Number_ | Mês (1-12) |
| `input.year` | _Number_ | Ano |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Schedule](#schedule)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetSchedules', {
    month: 8,
    year: 2022
});
for (var i = 0; i < r.data.length; i++) {
    var s = r.data[i];
    h.log(s.datetime);
    h.log(s.name);
    h.log(s.lyrics_playlist);
    h.log(s.media_playlist);
}
```

---


### hly('MediaPlaylistAction', input)
Executa um item da lista de reprodução de mídia

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID do item |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('MediaPlaylistAction', {id: 'abc'});

//Chamadas alternativas
h.mediaPlaylistAction('abc');
h.mplAction('abc');
```

---


### hly('FavoriteAction', input)
Executa um item da barra de favoritos

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID do item |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('FavoriteAction', {id: 'abc'});

//Chamadas alternativas
h.favoriteAction('abc');
h.favAction('abc');
```

---


### hly('ShowLyrics', input)
### hly('ShowSong', input)
Inicia uma apresentação de letra de música.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID do item |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowLyrics', {id: '123'});

//procura uma música e executa o primeiro resultado encontrado
var r = h.hly('SearchLyrics', {
    text: 'título da música'
});
if (r.data.length == 0) {
    h.log("Música não encontrada");
} else {
    h.hly('ShowLyrics', {id: r.data[0].id});
}

//Chamadas alternativas
h.showLyrics('123');
h.showSong('123');
```

---


### hly('ShowText', input)
Inicia uma apresentação de um item da aba texto.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID do item |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowText', {id: 'abc'});

//Chamada alternativa
h.showText('abc');
```

---


### hly('ShowVerse', input)
Inicia uma apresentação de versículo da Bíblia.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object_ | **id**, **ids** ou **references** |
| `input.id` | _String (opcional)_ | Para exibir um versículo. ID do item no formato LLCCCVVV. Exemplo: '19023001' (ou seja, livro 19, capítulo 023, versículo 001) |
| `input.ids` | _Array&lt;String&gt; (opcional)_ | Para exibir uma lista de versículos. Lista com o ID de cada versículo. Exemplo: ['19023001', '43003016', '45012002'] |
| `input.references` | _String (opcional)_ | Referências. Exemplo: **João 3:16** ou **Rm 12:2** ou **Gn 1:1-3 Sl 23.1** |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowVerse', {id: '19023001'});

h.hly('ShowVerse', {ids: ['19023001', '43003016', '45012002']});

h.hly('ShowVerse', {references: 'João 3:16'});

h.hly('ShowVerse', {references: 'Rm 12:2  Gn 1:1-3  Sl 23'});

//Chamada alternativa
h.showVerse('Rm 12:2  Gn 1:1-3  Sl 23');
```

---


### hly('PlayAudio', input)
Executa um áudio ou uma lista de áudios (pasta)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome do arquivo ou da pasta. Exemplo: **arquivo.mp3** ou **pasta** ou **pasta/arquivo.mp3** |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('PlayAudio', {file: 'arquivo.mp3'});
h.hly('PlayAudio', {file: 'pasta'});
h.hly('PlayAudio', {file: 'pasta/arquivo.mp3'});

//Chamada alternativa
h.playAudio('arquivo.mp3');
```

---


### hly('PlayVideo', input)
Executa um vídeo ou uma lista de vídeos (pasta)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome do arquivo ou da pasta. Exemplo: **arquivo.mp4** ou **pasta** ou **pasta/arquivo.mp4** |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('PlayVideo', {file: 'arquivo.mp4'});
h.hly('PlayVideo', {file: 'pasta'});
h.hly('PlayVideo', {file: 'pasta/arquivo.mp4'});

//Chamada alternativa
h.playVideo('arquivo.mp4');
```

---


### hly('ShowImage', input)
Apresenta uma imagem ou uma lista de imagens (pasta)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome do arquivo ou da pasta. Exemplo: **arquivo.jpg** ou **pasta** ou **pasta/arquivo.jpg** |
| `input.automatic` | _[Automatic](#automatic-presentation) (opcional)_ | Se informado, a apresentação dos itens será automática |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowImage', {file: 'arquivo.jpg'});
h.hly('ShowImage', {file: 'pasta'});
h.hly('ShowImage', {file: 'pasta/arquivo.jpg'});

h.hly('ShowImage', {
    file: 'pasta',
    automatic: {
        seconds: 5,
        repeat: true
    }
});

//Chamada alternativa
h.showImage('arquivo.jpg');
```

---


### hly('ShowQuickPresentation', input)
Apresenta rápida de um texto

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.text` | _String_ | Texto que será exibido |
| `input.theme` | _Object (opcional)_ | Filtrar tema selecionado para exibição |
| `input.theme.id` | _String (opcional)_ | ID do tema |
| `input.theme.name` | _String (opcional)_ | Nome do tema |
| `input.automatic` | _[Automatic](#automatic-presentation) (opcional)_ | Se informado, a apresentação dos itens será automática |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowQuickPresentation', {
    text: "Texto que será exibido"
});

h.hly('ShowQuickPresentation', {
    text: "Slide 1\n\nSlide 2\n\nSlide 3",
    theme: {
        name: "Tema 3"
    },
    automatic: {
        seconds: 5,
        repeat: true
    }
});
```

---


### hly('ShowAnnouncement', input)
Apresenta um anúncio ou uma lista de anúncios

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String (opcional)_ | ID do anúncio. Pode ser **all** para exibir todos |
| `input.ids` | _Array&lt;String&gt; (opcional)_ | Lista com o ID de cada anúncio |
| `input.name` | _String (opcional)_ | Nome do anúncio |
| `input.names` | _Array&lt;String&gt; (opcional)_ | Lista com o nome de cada anúncio |
| `input.automatic` | _[Automatic](#automatic-presentation) (opcional)_ | Se informado, a apresentação dos itens será automática |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowAnnouncement', {id: '123'});

h.hly('ShowAnnouncement', {
    names: ['Anúncio 1', 'Anúncio 2', 'Anúncio 3'],
    automatic: {
        seconds: 10,
        repeat: true
    }
});
```

---


### hly('CloseCurrentPresentation')
Encerra a apresentação atual



_Método sem retorno_

**Exemplo:**

```javascript
h.hly('CloseCurrentPresentation');
```

---


### hly('SetCurrentBackground', input)
Altera o plano de fundo (ou tema) da apresentação atual. Se mais de um item for encontrado de acordo com os filtros, será escolhido um item da lista de forma aleatória

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object (opcional)_ | Filtro |
| `input.id` | _String (opcional)_ | ID do tema ou plano de fundo |
| `input.name` | _String (opcional)_ | Nome do tema ou plano de fundo |
| `input.type` | _String (opcional)_ | Pode ser: theme, my_video, my_image, video, image |
| `input.tag` | _String (opcional)_ |  |
| `input.tags` | _Array&lt;String&gt; (opcional)_ |  |
| `input.intersection` | _Boolean (opcional)_ | Se o campo **input.tags** estiver preenchido com múltiplos itens, a opção **input.intersection** define o tipo de junção. Se **true**, o filtro retornará apenas itens que contém **todas** as tags informadas, se **false**, o filtro retornará os itens que têm pelo menos uma tag das tags informadas _(Padrão=*false*)_ |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetCurrentBackground', {id: 'abc'});

h.hly('SetCurrentBackground', {name: 'xyz'});

//um vídeo que esteja definido com a tag 'água'
h.hly('SetCurrentBackground', {
    type: 'my_video',
    tag: 'água'
});

//um vídeo que esteja definido com a tag 'água' OU com a tag 'azul'
h.hly('SetCurrentBackground', {
    type: 'my_video',
    tags: ['água', 'azul']
});

//um vídeo que esteja definido com a tag 'água' E com a tag 'azul'
h.hly('SetCurrentBackground', {
    type: 'my_video',
    tags: ['água', 'azul'],
    intersection: true
});
```

---


### hly('GetBpm')
Retorna o valor BPM atual definido no programa



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Valor BPM atual |


**Exemplo:**

```javascript
var r = h.hly('GetBpm');
h.log('BPM: ' + r.data);
```

---


### hly('SetBpm')
Altera o valor BPM atual do programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `bpm` | _Number_ | Valor BPM |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetBpm', {bpm: 80});
```

---


### hly('SearchLyrics', input)
### hly('SearchSong', input)
Realiza uma busca na lista de letras do usuário

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _String_ | Filtro |
| `input.text` | _String_ | Texto a ser pesquisado |
| `input.title` | _Boolean (opcional)_ |  _(Padrão=*true*)_ |
| `input.artist` | _Boolean (opcional)_ |  _(Padrão=*true*)_ |
| `input.note` | _Boolean (opcional)_ |  _(Padrão=*true*)_ |
| `input.lyrics` | _Boolean (opcional)_ |  _(Padrão=*false*)_ |
| `input.group` | _String (opcional)_ |  |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Lyrics](#lyrics)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('SearchLyrics', {
    text: 'exemplo',
    lyrics: true
});
if (r.data.length == 0) {
    h.log("Nenhum resultado encontrado");
} else {
    for (var i = 0; i < r.data.length; i++) {
        var m = r.data[i];
        h.log(m.title);
    }
}
```

---


### hly('AddLyricsToPlaylist', input)
### hly('AddSongsToPlaylist', input)
Adicionar letra de música na lista de reprodução

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String (opcional)_ | ID da letra |
| `input.ids` | _Array&lt;String&gt; (opcional)_ | Lista com id de cada letra |
| `input.index` | _Number (opcional)_ | Posição na lista onde o item será adicionado (inicia em zero). Os itens são adicionados no final da lista por padrão. _(Padrão=*-1*)_ |
| `input.media_playlist` | _Boolean (opcional)_ | Adicionar as letras na lista de reprodução de mídia _(Padrão=*false*)_ |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('AddLyricsToPlaylist', {id: '123'});

h.hly('AddLyricsToPlaylist', {ids: ['123', '456']});

h.hly('AddLyricsToPlaylist', {
    ids: ['123', '456'],
    index: 3
});

h.hly('AddLyricsToPlaylist', {
    ids: ['123', '456'],
    index: 3,
    media_playlist: true
});
```

---


### hly('RemoveFromLyricsPlaylist', input)
### hly('RemoveFromSongPlaylist', input)
Remover letra de música na lista de reprodução

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String (opcional)_ | ID da letra |
| `input.ids` | _Array&lt;String&gt; (opcional)_ | Lista com id de cada letra |
| `input.index` | _Number (opcional)_ | Posição do item na lista que será removido (inicia em zero). |
| `input.indexes` | _Boolean (opcional)_ | Lista com a posição de cada item na lista que será removido. (Inicia em zero) |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('RemoveFromLyricsPlaylist', {id: '123'});

h.hly('RemoveFromLyricsPlaylist', {ids: ['123', '456']});

h.hly('RemoveFromLyricsPlaylist', {index: 3});

h.hly('RemoveFromLyricsPlaylist', {indexes: [3, 4, 5]});
```

---


### hly('RemoveFromMediaPlaylist', input)
Remover itens da lista de reprodução de mídia

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String (opcional)_ | ID do item |
| `input.ids` | _Array&lt;String&gt; (opcional)_ | Lista com id de cada item |
| `input.index` | _Number (opcional)_ | Posição do item na lista que será removido (inicia em zero). |
| `input.indexes` | _Boolean (opcional)_ | Lista com a posição de cada item na lista que será removido. (Inicia em zero) |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('RemoveFromMediaPlaylist', {id: 'abc'});

h.hly('RemoveFromMediaPlaylist', {ids: ['abc', 'xyz']});

h.hly('RemoveFromMediaPlaylist', {index: 3});

h.hly('RemoveFromMediaPlaylist', {indexes: [3, 4, 5]});
```

---


### hly('GetCommunicationPanelInfo')
### hly('GetCPInfo')
Configuração atual do painel de comunicação



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.text` | _String_ | Texto atual |
| `data.show` | _Boolean_ | Se o texto atual está em exibição |
| `data.display_ahead` | _Boolean_ | Se a opção *'exibir à frente de tudo'* está ativada |
| `data.alert_text` | _String_ | Texto atual do alerta |
| `data.alert_show` | _Boolean_ | Se a exibição do alerta está ativada |
| `data.countdown_show` | _Boolean_ | Se uma contagem regressiva está em exibição |
| `data.countdown_time` | _Number_ | O tempo atual da contagem regressiva em exibição (em segundos) |


**Exemplo:**

```javascript
var r = h.hly('GetCommunicationPanelInfo');
if (r.data.countdown_show) {
    h.log("A contagem regressiva do painel de comunicação está ativa");
    h.log(r.data.countdown_time + " segundos");
} else {
    h.log("A contagem regressiva do painel de comunicação não está ativa");
}
```

---


### hly('SetAlert', input)
Altera as configurações da mensagem de alerta

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.text` | _String (opcional)_ | Alterar o texto de alerta |
| `input.show` | _Boolean (opcional)_ | Exibir/ocultar o alerta |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetAlert', {
    text: "texto de alerta",
    show: true
});

//remover
h.hly('SetAlert', {show: false});
```

---


### hly('StartCountdownCommunicationPanel', input)
### hly('StartCountdownCP', input)
Inicia uma contagem regressiva no painel de comunicação

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.minutes` | _Number_ | Quantidade de minutos |
| `input.seconds` | _Number_ | QUantidade de segundos |
| `input.yellow_starts_at` | _Number (opcional)_ | Valor em segundos para definir a partir de quanto tempo a contagem regressiva ficará amarela |
| `input.stop_at_zero` | _Boolean (opcional)_ | Parar a contagem regressiva ao chegar em zero _(Padrão=*false*)_ |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('StartCountdownCommunicationPanel', {minutes: 3});

h.hly('StartCountdownCommunicationPanel', {
    minutes: 1,
    seconds: 30,
    yellow_starts_at: 30,
    stop_at_zero: true
});
```

---


### hly('StopCountdownCommunicationPanel')
### hly('StopCountdownCP')
Encerra a contagem regressiva atual do painel de comunicação



_Método sem retorno_

**Exemplo:**

```javascript
h.hly('StopCountdownCommunicationPanel');
```

---


### hly('SetTextCommunicationPanel', input)
### hly('SetTextCP', input)
Alterar o texto do painel de comunicação

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.text` | _Number (opcional)_ | Alterar o texto do painel de comunicação |
| `input.show` | _Boolean (opcional)_ | Exibir/ocultar o texto |
| `input.display_ahead` | _Boolean (opcional)_ | Alterar a opção *'exibir à frente de tudo'* |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetTextCommunicationPanel', {
    text: "texto painel de comunicação",
    show: true,
    display_ahead: true
});

//remover
h.hly('SetTextCommunicationPanel', {show: false});
```

---


### hly('SetAlertCommunicationPanel', input)
### hly('SetAlertCP', input)
Alterar as configurações de alerta do painel de comunicação

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.text` | _String (opcional)_ | Alterar o texto de alerta |
| `input.show` | _Boolean (opcional)_ | Exibir/ocultar o alerta |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetAlertCommunicationPanel', {
    text: "texto de alerta painel de comunicação",
    show: true
});

//remover
h.hly('SetAlertCommunicationPanel', {show: false});
```

---


### hly('SetLogo', input)
Alterar as configurações da funcionalidade *Logo* do programa (menu ferramentas)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.enable` | _Boolean (opcional)_ | Ativar/desativar a funcionalidade |
| `input.hide` | _Boolean (opcional)_ | Exibir/ocultar a funcionalidade |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetLogo', {enable: true});

h.hly('SetLogo', {hide: true});
```

---


# Métodos Player
### getMediaName()
Nome da mídia atual no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Nome da mídia |


---


### getMedia()
Caminho completo da mídia no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Caminho completo da mídia |


---


### isPlaying()
Verifica se o player está em execução



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### getDuration()
Tempo total da mídia atual no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Tempo total em milissegundos |


---


### getCurrentTime()
Tempo atual da mídia no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Tempo atual da mídia em milissegundos |


---


### getTimeElapsed()
Tempo decorrido da mídia no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Tempo decorrido no formato HH:MM:SS |


---


### getTimeRemaining()
Tempo restante da mídia no player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Tempo restante no formato HH:MM:SS |


---


### play()
Executar a ação **play** do player



_Método sem retorno_

---


### pause()
Executar a ação **pause** do player



_Método sem retorno_

---


### stop()
Executar a ação **stop** do player



_Método sem retorno_

---


### next()
Passa para o próximo item da lista no player



_Método sem retorno_

---


### previous()
Passa para o item anterior da lista no player



_Método sem retorno_

---


### isRepeat()
Verifica se a opção **repetir** está ativada



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setRepeat(repeat)
Altera a opção **repetir**

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `repeat` | _Boolean_ |  |


_Método sem retorno_

---


### isExecuteAll()
Verifica se o player está definido para executar itens em sequência



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setExecuteAll(executeAll)
Altera a configuração do player para executar itens em sequência

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `executeAll` | _Boolean_ |  |


_Método sem retorno_

---


### isExecuteSingle()
Verifica se o player está definido para executar somente o item atual da lista



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setExecuteSingle(executeSingle)
Altera a configuração do player para executar somente o item atual da lista

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `executeSingle` | _Boolean_ |  |


_Método sem retorno_

---


### isShuffle()
Verifica se a opção **aleatório** está ativada



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setShuffle(shuffle)
Altera a opção **aleatório**

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `shuffle` | _Boolean_ |  |


_Método sem retorno_

---


### isFullscreen()
Verifica se a opção **tela cheia** está ativada



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setFullscreen(fullscreen)
Altera a opção **tela cheia** do player

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `fullscreen` | _Boolean_ |  |


_Método sem retorno_

---


### getVolume()
Volume atual do player



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Volume. Mínimo=0, Máximo=100 |


---


### setVolume(volume)
Altera o volume do player

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `volume` | _Number_ | Mínimo=0, Máximo=100 |


_Método sem retorno_

---


### isMute()
Verifica se a opção **mudo** está ativada



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### setMute(mute)
Altera a opção **mudo**

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `mute` | _Boolean_ |  |


_Método sem retorno_

---


# Métodos User Input
### input(param, notification = false)
Exibir uma janela com campos de entrada para receber informações de forma interativa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `param` | _Object_ | Entradas que serão solicitadas na interface. Pode ser string ou Array&lt;[InputParam](#input-param)&gt;. Se for passada uma string, ela será o nome do item e o tipo do item será **text** |
| `notification` | _Boolean (opcional)_ | Exibe uma notificação em vez de abrir a janela diretamente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Se for passado apenas um item como entrada, será retornado o valor informado pelo usuário (pode ser NULL). Se múltiplas entradas forem solicitadas, será retornado um objeto (pode ser NULL) onde cada valor será informado na variável do seu respectivo ID. |


**Exemplo:**

```javascript
var r = h.input("Nome do Item");
h.log("Valor informado: " + r);

var param = [{type: 'password', label: 'Senha'}];
var r = h.input(param);
h.log("Senha informada: " + r);

var param = [
    {
        key: 'info',
        type: 'text',
        label: 'Informação'
    },{
        key: 'type',
        type: 'text',
        label: 'Tipo',
        allowed_values: ['Tipo 1', 'Tipo 2', 'Tipo 3']
    }
];
var r = h.input(param);
if (r == null) {
    h.log("Cancelado");
} else {
    h.log("Informação: " + r.info);
    h.log("Tipo: " + r.type);
}

var param = [
    {
        key: 'message',
        type: 'textarea',
        label: 'Mensagem'
    },{
        key: 'seconds',
        type: 'number',
        label: 'Segundos',
        min: 30,
        max: 300,
        default_value: 60
    }
];
var r = h.input(param);
if (r == null) {
    h.log("Cancelado");
} else {
    h.log("Mensagem: " + r.message);
    h.log("Segundos: " + r.seconds);
}
```

---


### inputTextArea(title, notification = false)
Solicita uma entrada em formato *textarea* possibilitando texto com múltiplas linhas

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `title` | _String_ | Nome do componente textarea |
| `notification` | _Boolean (opcional)_ | Exibe uma notificação em vez de abrir a janela diretamente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Retorna o texto informado pelo usuário (pode ser NULL) |


**Exemplo:**

```javascript
var r = h.inputTextArea("Nome do Item");
h.log("Valor informado: " + r);

var r = h.inputTextArea("Nome do Item", true); //notificação
h.log("Valor informado: " + r);
```

---


### itemChooser(title, items, notification = false)
Abre uma janela para selecionar um item em uma lista de valores

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `title` | _String_ | Título na janela |
| `items` | _Object_ | Lista de itens que serão exibidos na lista |
| `items.*.label` | _Boolean (opcional)_ | Nome que será exibido representando o item |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna o item selecionado pelo usuário (pode ser NULL) |


**Exemplo:**

```javascript
var r = h.itemChooser("Selecione um item", ["abc", "xyz", "123"]);
h.log("Item selecionado: " + r);

var r = h.itemChooser("Selecione um número", [1, 2, 3, 4, 5]);
h.log("Número selecionado: " + r);

var items = [
    {
        id: 1,
        type: 'test1',
        label: 'ABC'
    },{
        id: 2,
        type: 'test2',
        label: 'XYZ'
    },{
        id: 3,
        type: 'test3',
        label: '123'
    }
];
var r = h.itemChooser("Selecione um item", items, true); //notificação
if (r == null) {
    h.log("Cancelado");
} else {
    h.log("Item selecionado");
    h.log("ID: " + r.id);
    h.log("Tipo: " + r.type);
    h.log("Nome: " + r.label);
}

var arr1 = ['a', 'b', 'c'];
var arr2 = ['x', 'y', 'z'];
var arr3 = [1, 2, 3];
var items = [
    {source: arr1, label: 'Lista 1 (a, b, c)'},
    {source: arr2, label: 'Lista 2 (x, y, z)'},
    {source: arr3, label: 'Lista 3 (1, 2, 3)'}
];
var r = h.itemChooser("Selecione um item", items);
if (r == null) {
    h.log("Cancelado");
} else {
    h.log("Item selecionado: " + r.source);
}
```

---


# Classes
Classes complexas utilizadas como retorno em alguns métodos
## Lyrics
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID da música |
| `title` | _String_ | Título da música |
| `artist` | _String_ | Artista da música |
| `author` | _String_ | Autor da música |
| `note` | _String_ | Anotação da música |
| `key` | _String_ | Tom da música |
| `time_sig` | _String_ | Tempo da música |
| `groups` | _Array&lt;[Group](#group)&gt;_ | Grupos onde a música está adicionada |
| `midi` | _[Midi](#midi)_ | Atalho MIDI do item |
| `archived` | _Boolean_ | Se a música está arquivada |

## Background
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `type` | _String_ | Tipo do item. Pode ser: theme, my_video, my_image, video, image |
| `name` | _String_ | Nome do item |
| `tags` | _Array&lt;String&gt;_ | Lista de tags do item |
| `bpm` | _Number_ | Valor BPM do item |
| `midi` | _[Midi](#midi) (opcional)_ | Atalho MIDI do item |

## Item
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `type` | _String_ | Tipo do item. Pode ser: song, verse, text, audio, video, image, file, custom-text, announcement, countdown, countdown-cp, automatic_presentation, api, script |
| `name` | _String_ | Nome do item |

## Group
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do item |

## Midi
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `code` | _Number_ | Código midi |
| `velocity` | _Number_ | Velocidade/intensidade midi |

## Favorite Item
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |

## Schedule
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | Tipo da lista de reprodução. Pode ser: temporary, service, event |
| `name` | _String_ |  |
| `datetime` | _String_ | Data e hora do item no formato: YYYY-MM-DD HH:MM |
| `lyrics_playlist` | _Array&lt;[Lyrics](#lyrics)&gt;_ | Lista de letras |
| `media_playlist` | _Array&lt;[Item](#item)&gt;_ | Lista de mídias |
| `responsible` | _[Member](#member)_ | Integrante definido como responsável pelo evento |
| `members` | _Array&lt;Object&gt;_ | Lista dos integrantes escalados |
| `members.*.id` | _String_ | ID do integrante |
| `members.*.name` | _String_ | Nome do integrante escalado |
| `members.*.scheduled` | _Boolean_ | Se o integrande está escalado ou definido para uma função |
| `roles` | _Array&lt;Object&gt;_ | Lista das funções na escala |
| `roles.*.id` | _String_ | ID da função |
| `roles.*.name` | _String_ | Nome da função |
| `roles.*.member` | _[Member](#member)_ | Integrante escalado para a função |

## Member
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |

## Role
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |

## Automatic Presentation
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `seconds` | _Number_ | Tempo que cada item ficará sendo apresentado |
| `repeat` | _Boolean_ | **true** para ficar repetindo a apresentação (voltar para o primeiro item após o último) |

## Input Param
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/ID do item |
| `type` | _String_ | Tipo de entrada. Pode ser: text, textarea, number, password, title, separator |
| `label` | _String_ | Nome do item |
| `default_value` | _Object (opcional)_ | Valor padrão do item |
| `allowed_values` | _Array&lt;String&gt; (opcional)_ | Disponível se o tipo for **text**. Define uma lista de valores permitidos, para serem selecionados como um combobox |
| `suggested_values` | _Array&lt;String&gt; (opcional)_ | Disponível se o tipo for **text**. Define uma lista de valores sugeridos, porém o usuário pode inserir qualquer valor no campo de texto |
| `min` | _Number (opcional)_ | Disponível se o tipo for **number**. Define o valor mínimo permitido _(Padrão=*0*)_ |
| `max` | _Number (opcional)_ | Disponível se o tipo for **number**. Define o valor máximo permitido _(Padrão=*100*)_ |
| `show_as_combobox` | _Boolean (opcional)_ | Disponível se o tipo for **number**. Exibe a lista de valores como combobox e não como spinner _(Padrão=*false*)_ |

