# jslib
**PT** | [EN](README-en.md)

Métodos da classe JSLib disponível para uso nos scripts do programa Holyrics.

É possível utilizar a variável ```jslib``` ou a variável ```h``` para acessar os métodos disponíveis.

Por exemplo:

```
jslib.log('exemplo');
h.log('exemplo');
```
---

- [Métodos](#métodos)
  - [log](#logobj)
  - [log](#logkey--null-obj-args--null)
  - [log.enable](#logenablekey)
  - [log.enableAll](#logenableall)
  - [log.isEnabled](#logisenabledkey)
  - [log.setShowLogKey](#logsetshowlogkeyvalue)
  - [log.isShowLogKey](#logisshowlogkey)
  - [sleep](#sleeptime)
  - [base64Encode](#base64encodebytes)
  - [base64Decode](#base64decodestr)
  - [md5](#md5value)
  - [md5Str](#md5strvalue)
  - [sha256](#sha256value)
  - [sha256Str](#sha256strvalue)
  - [sha512](#sha512value)
  - [sha512Str](#sha512strvalue)
  - [getClipboard](#getclipboard)
  - [normalize](#normalizestr)
  - [store](#storekey-value)
  - [restore](#restorekey)
  - [setGlobal](#setglobalkey-value)
  - [getGlobal](#getglobalkey-default--null)
  - [setCache](#setcachekey-value)
  - [getCache](#getcachekey-default--null)
  - [random](#randommin-max-keysaferepeat--null)
  - [startTimer](#starttimerkey--default)
  - [getTimer](#gettimerkey--default)
  - [startCountdown](#startcountdownkey--default-seconds)
  - [getCountdown](#getcountdownkey--default)
  - [getPlaylistInfo](#getplaylistinfo)
  - [getPlayer](#getplayer)
  - [scriptAction](#scriptactionid-input--null)
  - [apiAction](#apiactionid-input--null)
  - [apiRequest](#apirequestid-raw)
  - [getApiRequestLastError](#getapirequestlasterror)
  - [apiRequestAsync](#apirequestasyncid-raw-callback--null)
  - [setTimeout](#settimeoutfunction-timeout)
  - [clearTimeout](#cleartimeoutid)
  - [setInterval](#setintervalfunction-timeout)
  - [clearInterval](#clearintervalid)
  - [getHostname](#gethostname)
  - [getRuntimeEnvironment](#getruntimeenvironment)
  - [setRuntimeEnvironment](#setruntimeenvironmentname)
  - [isRuntimeEnvironment](#isruntimeenvironmentname)
  - [getVersion](#getversion)
  - [isMinimumVersion](#isminimumversionversion)
  - [getLanguage](#getlanguage)
  - [isLanguage](#islanguagelanguage)
  - [getUITheme](#getuitheme)
  - [isUITheme](#isuithemevalue)
  - [format.secondsToHMS](#formatsecondstohmsseconds-separator--)
  - [format.secondsToMS](#formatsecondstomsseconds-separator--)
  - [format.minutesToHM](#formatminutestohmminutes-separator--)
  - [date.getSecondOfDay](#dategetsecondofday)
- [Métodos HLY](#métodos-hly)
  - [GetLyrics](#hlygetlyrics-input)
  - [SearchLyrics](#hlysearchlyrics-input)
  - [ShowLyrics](#hlyshowlyrics-input)
  - [ShowText](#hlyshowtext-input)
  - [ShowVerse](#hlyshowverse-input)
  - [GetAudios - GetVideos - GetImages](#hlygetaudios-input)
  - [PlayAudio](#hlyplayaudio-input)
  - [PlayVideo](#hlyplayvideo-input)
  - [ShowImage](#hlyshowimage-input)
  - [ShowAnnouncement](#hlyshowannouncement-input)
  - [GetCustomMessages](#hlygetcustommessages)
  - [ShowCustomMessage](#hlyshowcustommessage-input)
  - [ShowQuickPresentation](#hlyshowquickpresentation-input)
  - [ShowCountdown](#hlyshowcountdown-input)
  - [ShowQuiz](#hlyshowquiz-input)
  - [QuizAction](#hlyquizaction-input)
  - [PlayAutomaticPresentation](#hlyplayautomaticpresentation-input)
  - [GetAutomaticPresentationPlayerInfo](#hlygetautomaticpresentationplayerinfo)
  - [AutomaticPresentationPlayerAction](#hlyautomaticpresentationplayeraction-input)
  - [GetMediaPlayerInfo](#hlygetmediaplayerinfo)
  - [MediaPlayerAction](#hlymediaplayeraction-input)
  - [GetLyricsPlaylist](#hlygetlyricsplaylist)
  - [AddLyricsToPlaylist](#hlyaddlyricstoplaylist-input)
  - [RemoveFromLyricsPlaylist](#hlyremovefromlyricsplaylist-input)
  - [GetMediaPlaylist](#hlygetmediaplaylist)
  - [MediaPlaylistAction](#hlymediaplaylistaction-input)
  - [AddToPlaylist](#hlyaddtoplaylist-input)
  - [RemoveFromMediaPlaylist](#hlyremovefrommediaplaylist-input)
  - [GetFavorites](#hlygetfavorites)
  - [FavoriteAction](#hlyfavoriteaction-input)
  - [ApiAction](#hlyapiaction-input)
  - [ScriptAction](#hlyscriptaction-input)
  - [ApiRequest](#hlyapirequest-input)
  - [GetCurrentPresentation](#hlygetcurrentpresentation)
  - [CloseCurrentPresentation](#hlyclosecurrentpresentation)
  - [GetF8 - F9 - F10](#hlygetf8)
  - [SetF8 - F9 - F10](#hlysetf8-input)
  - [ToggleF8 - F9 - F10](#hlytogglef8)
  - [ActionNext](#hlyactionnext)
  - [ActionPrevious](#hlyactionprevious)
  - [ActionGoToIndex](#hlyactiongotoindex-input)
  - [ActionGoToSlideDescription](#hlyactiongotoslidedescription-input)
  - [GetCurrentBackground](#hlygetcurrentbackground)
  - [GetBackgrounds](#hlygetbackgrounds-input)
  - [SetCurrentBackground](#hlysetcurrentbackground-input)
  - [GetColorMap](#hlygetcolormap-input)
  - [SetAlert](#hlysetalert-input)
  - [GetCurrentSchedule](#hlygetcurrentschedule)
  - [GetSchedules](#hlygetschedules-input)
  - [GetSavedPlaylists](#hlygetsavedplaylists)
  - [LoadSavedPlaylist](#hlyloadsavedplaylist-input)
  - [GetHistory](#hlygethistory-input)
  - [GetHistories](#hlygethistories)
  - [GetMembers](#hlygetmembers)
  - [GetRoles](#hlygetroles)
  - [GetCommunicationPanelInfo](#hlygetcommunicationpanelinfo)
  - [SetCommunicationPanelSettings](#hlysetcommunicationpanelsettings-input)
  - [StartCountdownCommunicationPanel](#hlystartcountdowncommunicationpanel-input)
  - [StopCountdownCommunicationPanel](#hlystopcountdowncommunicationpanel)
  - [StartTimerCommunicationPanel](#hlystarttimercommunicationpanel)
  - [StopTimerCommunicationPanel](#hlystoptimercommunicationpanel)
  - [SetTextCommunicationPanel](#hlysettextcommunicationpanel-input)
  - [SetAlertCommunicationPanel](#hlysetalertcommunicationpanel-input)
  - [CommunicationPanelCallAttention](#hlycommunicationpanelcallattention)
  - [GetWallpaperSettings](#hlygetwallpapersettings)
  - [SetWallpaperSettings](#hlysetwallpapersettings-input)
  - [GetDisplaySettings](#hlygetdisplaysettings)
  - [SetDisplaySettings](#hlysetdisplaysettings-input)
  - [GetBpm](#hlygetbpm)
  - [SetBpm](#hlysetbpm-input)
  - [GetHue](#hlygethue)
  - [SetHue](#hlysethue-input)
  - [GetRuntimeEnvironment](#hlygetruntimeenvironment)
  - [SetRuntimeEnvironment](#hlysetruntimeenvironment-input)
  - [SetLogo](#hlysetlogo-input)
  - [GetSyncStatus](#hlygetsyncstatus)
- [Métodos Player](#métodos-player)
  - [getMediaName](#getmedianame)
  - [getMedia](#getmedia)
  - [isPlaying](#isplaying)
  - [getDuration](#getduration)
  - [getCurrentTime](#getcurrenttime)
  - [setCurrentTime](#setcurrenttimetime)
  - [getTimeElapsed](#gettimeelapsed)
  - [getTimeRemaining](#gettimeremaining)
  - [play](#play)
  - [pause](#pause)
  - [stop](#stop)
  - [next](#next)
  - [previous](#previous)
  - [isRepeat](#isrepeat)
  - [setRepeat](#setrepeatrepeat)
  - [isExecuteAll](#isexecuteall)
  - [setExecuteAll](#setexecuteallexecuteall)
  - [isExecuteSingle](#isexecutesingle)
  - [setExecuteSingle](#setexecutesingleexecutesingle)
  - [isShuffle](#isshuffle)
  - [setShuffle](#setshuffleshuffle)
  - [isFullscreen](#isfullscreen)
  - [setFullscreen](#setfullscreenfullscreen)
  - [getVolume](#getvolume)
  - [setVolume](#setvolumevolume)
  - [isMute](#ismute)
  - [setMute](#setmutemute)
- [Métodos User Input](#métodos-user-input)
  - [input](#inputparam-notification--false)
  - [inputTextArea](#inputtextareatitle-notification--false)
  - [itemChooser](#itemchoosertitle-items-notification--false)
  - [multipleItemChooser](#multipleitemchoosertitle-items-notification--false)
  - [confirm](#confirmmsg-title--confirm-notification--false)
  - [yesNo](#yesnomsg-title--confirm-notification--false)
  - [notification](#notificationmsg-duration--0)
  - [lyricsChooser](#lyricschooser)
  - [themeChooser](#themechooser)
  - [imageChooser](#imagechooser)
  - [audioChooser](#audiochooser)
  - [videoChooser](#videochooser)
  - [backgroundChooser](#backgroundchooser)
- [Classes](#classes)
  - [Lyrics](#lyrics)
  - [Background](#background)
  - [Item](#item)
  - [Group](#group)
  - [Midi](#midi)
  - [Favorite Item](#favorite-item)
  - [Schedule](#schedule)
  - [Member](#member)
  - [Role](#role)
  - [Automatic Presentation](#automatic-presentation)
  - [Input Param](#input-param)
  - [Display Settings](#display-settings)
  - [Stage View](#stage-view)
  - [Slide Additional Info](#slide-additional-info)
  - [Rectangle](#rectangle)
  - [Custom Message](#custom-message)
  - [Custom Message Param](#custom-message-param)
  - [Quiz Question](#quiz-question)
  - [Quiz Settings](#quiz-settings)
  - [AddItem](#additem)
  - [AddItemTitle](#additemtitle)
  - [AddItemSong](#additemsong)
  - [AddItemVerse](#additemverse)
  - [AddItemText](#additemtext)
  - [AddItemAudio](#additemaudio)
  - [AddItemVideo](#additemvideo)
  - [AddItemImage](#additemimage)
  - [AddItemAutomaticPresentation](#additemautomaticpresentation)
  - [AddItemAnnouncement](#additemannouncement)
  - [AddItemCountdown](#additemcountdown)
  - [AddItemCountdownCommunicationPanel](#additemcountdowncommunicationpanel)
  - [AddItemTextCommunicationPanel](#additemtextcommunicationpanel)
  - [AddItemScript](#additemscript)
  - [AddItemAPI](#additemapi)


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


### log(key = null, obj, args = null)
### log.add(key = null, obj, args = null)
- v2.20.0

Exibe a informação passada como parâmetro numa janela de log (canto inferior direito da tela, geralmente)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id de gerenciamento do log |
| `obj` | _Object_ | Qualquer objeto para ser exibido na janela de log |
| `args` | _Array&lt;Object&gt;_ | Parâmetros para formatação de uma mensagem de log |


_Método sem retorno_

**Exemplo:**

```javascript
h.log('xyz', 'mensagem de log');

h.log('xyz', 'mensagem de log {} abc {}', ['value 1', 'value 2']);
//output:
//mensagem de log value 1 abc value 2

h.log('mensagem de log {} abc {}', ['value 1', 'value 2']);
//output:
//mensagem de log value 1 abc value 2
```

---


### log.enable(key)
### log.disable(key)
- v2.20.0

Ativar/desativar a visualização de logs da chave/id passada por parâmetro. Todas as chaves/ids iniciam desativadas por padrão

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id de gerenciamento do log |


_Método sem retorno_

**Exemplo:**

```javascript
h.log.enable('xyz');
h.log.disable('xyz');
```

---


### log.enableAll()
### log.disableAll()
- v2.20.0

Ativa/desativa a visualização de todos os logs



_Método sem retorno_

**Exemplo:**

```javascript
h.log.enableAll();
h.log.disableAll();
```

---


### log.isEnabled(key)
### log.isDisabled(key)
- v2.20.0

Verifica se a visualização está ativada/desativada para a respectiva chave/id

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id de gerenciamento do log |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


**Exemplo:**

```javascript
if (h.log.isEnabled('xyz')) {
    //...
}

if (h.log.isDisabled('xyz')) {
    //...
}
```

---


### log.setShowLogKey(value)
- v2.20.0

Ativa/desativa a exibição chave/id junto da mensagem na janela de log

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Boolean_ |  |


_Método sem retorno_

**Exemplo:**

```javascript
h.log.setShowLogKey(false);
```

---


### log.isShowLogKey()
- v2.20.0

Verifica se a exibição da chave está ativada



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


**Exemplo:**

```javascript
if (h.log.isShowLogKey()) {
    //...
}
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


### sha512(value)
- v2.20.0

Hash SHA-512 em array de bytes

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Object_ | Valor que será calculado. Pode ser string ou array de bytes |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;byte&gt;_ | hash SHA-512 |


---


### sha512Str(value)
- v2.20.0

Hash SHA-512

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Object_ | Valor que será calculado. Pode ser string ou array de bytes |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | hash SHA-512 |


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


### startTimer(key = 'default')
Inicia um timer

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String (opcional)_ | Chave/id do timer `Padrão: 'default'` |


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


### getTimer(key = 'default')
Recupera quanto tempo foi decorrido em um timer de acordo com o valor **key**. Se o timer não tiver sido iniciado, o método iniciará o timer e retornará 00:00:00

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String (opcional)_ | Chave/id do timer `Padrão: 'default'` |


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


### startCountdown(key = 'default', seconds)
- v2.20.0

Inicia uma contagem regressiva

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String (opcional)_ | Chave/id da contagem regressiva `Padrão: 'default'` |
| `seconds` | _Number_ | Duração total da contagem regressiva em segundos |


_Método sem retorno_

**Exemplo:**

```javascript
h.startCountdown('xyz', 300);
h.sleep(2000); //2 segundos
var r = h.getCountdown('xyz');
h.log('Tempo restante: ' + r); //provavelmente 00:04:58

//é um método global, o valor pode ser utilizado em qualquer outro script utilizando a mesma chave
```

---


### getCountdown(key = 'default')
- v2.20.0

Recupera quanto tempo resta em uma contagem regressiva de acordo com o valor **key**.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String (opcional)_ | Chave/id da contagem regressiva `Padrão: 'default'` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Tempo restante no formato HH:MM:SS (retorna valores negativos após limite de tempo) |


**Exemplo:**

```javascript
var r = h.getCountdown('xyz');
h.log('Tempo restante: ' + r);
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


### scriptAction(id, input = null)
Executa a ação de um item **Script** existente no programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | id do item |
| `input` | _Object (opcional)_ | Valores que serão definidos para [Function Input](https://github.com/holyrics/Scripts/blob/main/FunctionInput.md) `v2.20.0+` |


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

var r = h.scriptAction('abcxyz', {
    id_example_1: 'abc',
    id_example_2: 10
});
if (r) {
    h.log('Ação executada');
} else {
    h.log('Item abcxyz não econtrado');
}
```

---


### apiAction(id, input = null)
Executa a ação de um item API existente no programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | id do item |
| `input` | _Object (opcional)_ | Valores que serão definidos para [Function Input](https://github.com/holyrics/Scripts/blob/main/FunctionInput.md) `v2.20.0+` |


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

var r = h.apiAction('abcxyz', {
    id_example_1: 'abc',
    id_example_2: 10
});
if (r) {
    h.log('Ação executada');
} else {
    h.log('Item abcxyz não econtrado');
}
```

---


### apiRequest(id, raw)
Executa uma requisição para o receptor associado e retorna a resposta do receptor.

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
//Considerando que você tenha um receptor criado para comunicação com OBS Studio via websocket e o ID do receptor seja 'abcyxz'
//você pode fazer uma requisição como no exemplo abaixo
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


### getApiRequestLastError()
- v2.19.0

Retorna o erro da última requisição apiRequest realizada.



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Erro da última requisição ou NULL se não houver erro |


---


### apiRequestAsync(id, raw, callback = null)
- v2.19.0

Executa uma requisição para o receptor associado de forma assíncrona. O resultado pode ser acessado criando uma função anônima como callback.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | id do receptor |
| `raw` | _Object_ | dados da requisição |
| `callback` | _Function (opcional)_ | função anônima utilizada como callback da requisição. function(response, error){} |


_Método sem retorno_

**Exemplo:**

```javascript
//funciona como apiRequest, porém de forma assíncrona
//
//aguarda o retorno, pode demorar
//a próxima linha é executada somente quando a requisição for concluída
var r = h.apiRequest('abcxyz', {
    'request-type': 'GetSceneList'
});
//próxima linha

//não aguarda o retorno
//a próxima linha é executada logo em seguida
h.apiRequestAsync('abcxyz', {
    'request-type': 'GetSceneList'
}, function (response, error) {
    //callback da requisição
});
//próxima linha
```

---


### setTimeout(function, timeout)
- v2.19.0

Executa uma função após alguns milissegundos.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `function` | _Function_ | Função que será executada |
| `timeout` | _Number_ | Tempo em milissegundos para aguardar até a execução |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Retorna o ID da tarefa. Você pode utilizar o ID para cancelar a execução. |


**Exemplo:**

```javascript
var id = h.setTimeout(function () {
    //tarefa que será executada em 60 segundos
}, 60000);
```

---


### clearTimeout(id)
- v2.19.0

Cancela a execução da função agendada anteriormente.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _Function_ | ID retornado do método **setTimeout** |


_Método sem retorno_

**Exemplo:**

```javascript
var id = h.setTimeout(function () {
    //tarefa que será executada em 60 segundos
}, 60000);

//cancela a execução da tarefa
h.clearTimeout(id);
```

---


### setInterval(function, timeout)
- v2.19.0

Executa uma função a cada X milissegundos. Utilize **clearInterval** para parar a execução.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `function` | _Function_ | Função que será executada |
| `timeout` | _Number_ | Intervalo em milissegundos entre cada execução |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Retorna o ID da tarefa. Você pode utilizar o ID para parar a execução. |


**Exemplo:**

```javascript
var id = h.setInterval(function () {
    //tarefa que será executada a cada 15 segundos
}, 15000);
```

---


### clearInterval(id)
- v2.19.0

Cancela a execução da função agendada anteriormente.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _Function_ | ID retornado do método **setInterval** |


_Método sem retorno_

**Exemplo:**

```javascript
var id = h.setInterval(function () {
    //tarefa que será executada a cada 15 segundos
}, 15000);

//parar a execução
h.clearInterval(id);
```

---


### getHostname()
- v2.19.0

Retorna o nome do equipamento.



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Nome do equipamento |


---


### getRuntimeEnvironment()
### getRE()
- v2.19.0

Retorna o nome do ambiente de execução definido atualmente nas configurações do programa.



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Nome do ambiente de execução |


---


### setRuntimeEnvironment(name)
### setRE(name)
- v2.19.0

Altera o ambiente de execução atual.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do ambiente de execução |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna **true** ou **item not found** |


---


### isRuntimeEnvironment(name)
### isRE(name)
- v2.19.0

Verifica se o ambiente de execução atual é igual ao passado por parâmetro.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do ambiente de execução |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | Retorna **true** ou **false** |


---


### getVersion()
- v2.20.0

Retorna a versão atual do programa.



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Versão no formato: X.Y.Z |


**Exemplo:**

```javascript
if (h.getVersion() == "2.20.0") {
    //...
}
```

---


### isMinimumVersion(version)
### isMinVersion(version)
- v2.20.0

Verifica se a versão do programa é igual ou superior ao informado por parâmetro.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ | Versão no formato: X.Y.Z |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


**Exemplo:**

```javascript
if (h.isMinimumVersion('2.20.0')) {
    //A versão atual é igual ou superior a 2.20.0
}
```

---


### getLanguage()
- v2.20.0

Retorna o idioma atual definido nas configurações do programa.



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Idioma no formato ISO 639 two-letter |


**Exemplo:**

```javascript
switch (h.getLanguage()) {
    case 'en':
        //...
        break;
    case 'pt':
        //...
        break;
    case 'es':
        //...
        break;
    default:
        //...
        break;
}
```

---


### isLanguage(language)
- v2.20.0

Verifica se o idioma atual definido nas configurações do programa é igual ao valor passado por parâmetro.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `language` | _String_ | Idioma no formato ISO 639 two-letter |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


**Exemplo:**

```javascript
if (h.isLanguage('pt')) {
    //...
}
```

---


### getUITheme()
- v2.20.0

Retorna o tema atual da interface do programa.



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Um dos seguintes valores: DEFAULT, DARK_SOFT, DARK_MEDIUM, DARK_STRONG |


**Exemplo:**

```javascript
if (h.getUITheme() == 'DEFAULT') {
    //...
}
```

---


### isUITheme(value)
- v2.20.0

Verifica se o tema atual atual da interface é igual ao valor passado por parâmetro.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ | Nome do tema |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


**Exemplo:**

```javascript
if (h.isUITheme('DARK_STRONG')) {
    //...
}
```

---


### format.secondsToHMS(seconds, separator = ':')
### secToHMS(seconds, separator)
- v2.20.0

Formatar uma quantidade de segundos como hora|minuto|segundo.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `seconds` | _Number_ | Quantidade total de segundos |
| `separator` | _String (opcional)_ | Separador `Padrão: ':'` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Valor formatado |


**Exemplo:**

```javascript
var r = h.format.secondsToHMS(3905);
h.log(r);
//output:
//01:05:05

var r = h.format.secondsToHMS(3905, ',');
h.log(r);
//output:
//01,05,05
//
```

---


### format.secondsToMS(seconds, separator = ':')
### secToMS(seconds, separator)
- v2.20.0

Formatar uma quantidade de segundos como minuto|segundo.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `seconds` | _Number_ | Quantidade total de segundos |
| `separator` | _String (opcional)_ | Separador `Padrão: ':'` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Valor formatado |


**Exemplo:**

```javascript
var r = h.format.secondsToMS(305);
h.log(r);
//output:
//00:05:05

var r = h.format.secondsToMS(305, ',');
h.log(r);
//output:
//00,05,05
```

---


### format.minutesToHM(minutes, separator = ':')
- v2.20.0

Formatar uma quantidade de minutos como hora|minuto.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `minutes` | _Number_ | Quantidade total de minutos |
| `separator` | _String (opcional)_ | Separador `Padrão: ':'` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Valor formatado |


**Exemplo:**

```javascript
var r = h.format.minutesToHM(90);
h.log(r);
//output:
//01:30

var r = h.format.minutesToHM(90, ',');
h.log(r);
//output:
//01,30
```

---


### date.getSecondOfDay()
- v2.20.0

Retorna a quantidade total de segundos do dia (hour * 3600 + minute * 60 + second)



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ |  |


**Exemplo:**

```javascript
var r = h.date.getSecondOfDay();
//00:00:00 = 0
//23:59:59 = 86399
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


### hly('SearchLyrics', input)
### hly('SearchSong', input)
Realiza uma busca na lista de letras do usuário

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _String_ | Filtro |
| `input.text` | _String_ | Texto a ser pesquisado |
| `input.title` | _Boolean (opcional)_ |  `Padrão: true` |
| `input.artist` | _Boolean (opcional)_ |  `Padrão: true` |
| `input.note` | _Boolean (opcional)_ |  `Padrão: true` |
| `input.lyrics` | _Boolean (opcional)_ |  `Padrão: false` |
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
| `input.id` | _String (opcional)_ | Para exibir um versículo. ID do item no formato LLCCCVVV.<br/>Exemplo: '19023001' (livro 19, capítulo 023, versículo 001) |
| `input.ids` | _Array&lt;String&gt; (opcional)_ | Para exibir uma lista de versículos. Lista com o ID de cada versículo.<br/>Exemplo: ['19023001', '43003016', '45012002'] |
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


### hly('GetAudios', input)
### hly('GetVideos', input)
### hly('GetImages', input)
- v2.19.0

Retorna a lista de arquivos da respectiva aba: áudio, vídeo, imagem

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.folder` | _String (opcional)_ | Nome da subpasta para listar os arquivos |
| `input.filter` | _String (opcional)_ | Filtrar arquivos pelo nome |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.name` | _String_ | Nome do item |
| `data.*.isDir` | _Boolean_ | Retorna **true** se for uma pasta ou **false** se for arquivo. |


**Exemplo:**

```javascript
var r = h.hly('GetAudios');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}

var r = h.hly('GetVideos', {folder: 'abc'});

var r = h.hly('GetImages', {filter: 'text'});

var r = h.hly('GetFiles', {
    folder: 'name 1/name 2',
    filter: 'text'
});
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


### hly('GetCustomMessages')
- v2.19.0

Lista das mensagens personalizadas



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[CustomMessage](#custom-message)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetCustomMessages');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('ShowCustomMessage', input)
- v2.19.0

Exibir uma mensagem personalizada. Obs.: Uma mensagem personalizada não é exibida diretamente na tela. é criada uma notificação no canto da tela para o operador aceitar e exibir.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.name` | _String_ | Nome da mensagem personalizada |
| `input.position_?` | _Object_ | Variável adicionada na posição especificada conforme valor retornado em **variables.*.position** da classe CustomMessage. |
| `input.note` | _String_ | Informação extra exibida na janela popup para o operador |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowCustomMessage', {
    name: 'name',
    position_15: 'Value 1',
    position_28: 'Value 2',
    note: 'Com urgência'
});
```

---


### hly('ShowQuickPresentation', input)
Apresentação rápida de um texto

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.text` | _String_ | Texto que será exibido. [Styled Text](#styled-text) a partir da v2.19.0 |
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


### hly('ShowCountdown', input)
- v2.20.0

Exibir uma contagem regressiva na tela público

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.time` | _String_ | HH:MM ou MM:SS |
| `input.exact_time` | _Boolean (opcional)_ | Se **true**, `time` deve ser HH:MM (hora e minuto exato). Se **false**, `time` deve ser MM:SS (quantidade de minutos e segundos) `Padrão: false` |
| `input.text_before` | _String (opcional)_ | Texto exibido na parte superior da contagem regressiva |
| `input.text_after` | _String (opcional)_ | Texto exibido na parte inferior da contagem regressiva |
| `input.zero_fill` | _Boolean (opcional)_ | Preencher o campo 'minuto' com zero à esquerda `Padrão: false` |
| `input.countdown_relative_size` | _Number (opcional)_ | Tamanho relativo da contagem regressiva `Padrão: 250` |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowCountdown', {
    time: '05:00', //5 minutes
    zero_fill: true
});

h.hly('ShowCountdown', {
    time: '19:00', //19:00
    exact_time: true,
    text_after: 'Example'
});
```

---


### hly('ShowQuiz', input)
- v2.20.0

Iniciar uma apresentação no formato múltipla escolha

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.questions` | _Array&lt;[QuizQuestion](#quiz-question)&gt;_ | Questões para exibir |
| `input.settings` | _[QuizSettings](#quiz-settings)_ | Configurações |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowQuiz', {
    questions: [
        {
            title: 'Example 1',
            alternatives: [
                'Example 1a',
                'Example 2a',
                'Example 3a',
                'Example 4a'
            ],
            correct_alternative_number: 2
        }, {
            title: 'Example 2',
            alternatives: [
                'Example 1b',
                'Example 2b',
                'Example 3b',
                'Example 4b'
            ],
            correct_alternative_number: 2
        }
    ],
    settings: {
        display_alternatives_one_by_one: false,
        alternative_char_type: 'number'
    }
});
```

---


### hly('QuizAction', input)
- v2.20.0

Executar uma ação em uma apresentação de múltipla escolha

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.action` | _String (opcional)_ | Um dos seguintes valores: `previous_slide`  `next_slide`  `previous_question`  `next_question`  `show_result`  `close` |
| `input.hide_alternative` | _Number (opcional)_ | Ocultar uma alternativa. Começa em 1 |
| `input.select_alternative` | _Number (opcional)_ | Selecionar uma alternativa. Começa em 1 |
| `input.countdown` | _Number (opcional)_ | Iniciar uma contagem regressiva. [1-120] |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('QuizAction', { 
    action: 'next_slide'
});

h.hly('QuizAction', {
    hide_alternative: 3
});

h.hly('QuizAction', {
    select_alternative: 1
});
```

---


### hly('PlayAutomaticPresentation', input)
### hly('PlayAP', input)
- v2.19.0

Executa um item apresentação automática

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome do arquivo. Exemplo: **arquivo.ap** |
| `input.theme` | _Object (opcional)_ | Filtrar tema selecionado para exibição |
| `input.theme.id` | _String (opcional)_ | ID do tema |
| `input.theme.name` | _String (opcional)_ | Nome do tema |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('PlayAutomaticPresentation', {file: 'arquivo.ap'});

h.hly('PlayAP', {file: 'arquivo.ap'});

h.hly('PlayAP', {
    file: 'arquivo.ap',
    theme: {
        name: "Tema 3"
    }
});

//Chamadas alternativas
h.playAutomaticPresentation('arquivo.ap');
h.playAP('arquivo.ap');
```

---


### hly('GetAutomaticPresentationPlayerInfo')
### hly('GetAPPlayerInfo')
- v2.20.0

Retorna as informações da apresentação automática em exibição



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.name` | _String_ | Nome do item |
| `data.playing` | _Boolean_ | Verifica se o player está em execução |
| `data.time_ms` | _Number_ | Tempo atual da mídia em milissegundos |
| `data.volume` | _Number_ | Volume atual do player. Mínimo=0, Máximo=100 |
| `data.mute` | _Boolean_ | Verifica se a opção **mudo** está ativada |


**Exemplo:**

```javascript
var r = h.hly('GetAutomaticPresentationPlayerInfo');
if (r.data.name == 'abc') {
    //...
}
```

---


### hly('AutomaticPresentationPlayerAction', input)
### hly('APPlayerAction', input)
- v2.20.0

Executa ações no player

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.action` | _String (opcional)_ | Nome da ação que será executada no player. play, pause, stop |
| `input.volume` | _Number (opcional)_ | Altera o volume do player. Mínimo=0, Máximo=100 |
| `input.mute` | _Boolean (opcional)_ | Altera a opção **mudo** |
| `input.time_ms` | _Boolean (opcional)_ | Alterar o tempo atual da mídia em milissegundos |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('AutomaticPresentationPlayerAction', {
    action: 'play',
    volume: 80
});
```

---


### hly('GetMediaPlayerInfo')
Retorna as informações do player



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.name` | _String_ | Nome da mídia atual no player |
| `data.path` | _String_ | Caminho completo da mídia no player |
| `data.playing` | _Boolean_ | Verifica se o player está em execução |
| `data.duration_ms` | _Number_ | Tempo total em milissegundos |
| `data.time_ms` | _Number_ | Tempo atual da mídia em milissegundos |
| `data.time_elapsed` | _String_ | Tempo decorrido no formato HH:MM:SS |
| `data.time_remaining` | _String_ | Tempo restante no formato HH:MM:SS |
| `data.volume` | _Number_ | Volume atual do player. Mínimo=0, Máximo=100 |
| `data.mute` | _Boolean_ | Verifica se a opção **mudo** está ativada |
| `data.repeat` | _Boolean_ | Verifica se a opção **repetir** está ativada |
| `data.execute_single` | _Boolean_ | Verifica se o player está definido para executar somente o item atual da lista |
| `data.shuffle` | _Boolean_ | Verifica se a opção **aleatório** está ativada |
| `data.fullscreen` | _Boolean_ | Verifica se a opção **tela cheia** está ativada |


**Exemplo:**

```javascript
var r = h.hly('GetMediaPlayerInfo');
if (r.data.playing) {
    h.log('O player está em execução');
} else {
    h.log('O player não está em execução');
}
```

---


### hly('MediaPlayerAction', input)
- v2.19.0

Executa ações no player

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.action` | _String (opcional)_ | Nome da ação que será executada no player. play, pause, stop, next, previous |
| `input.volume` | _Number (opcional)_ | Altera o volume do player. Mínimo=0, Máximo=100 |
| `input.mute` | _Boolean (opcional)_ | Altera a opção **mudo** |
| `input.repeat` | _Boolean (opcional)_ | Altera a opção **repetir** |
| `input.shuffle` | _Boolean (opcional)_ | Altera a opção **aleatório** |
| `input.execute_single` | _Boolean (opcional)_ | Altera a configuração do player para executar somente o item atual da lista |
| `input.fullscreen` | _Boolean (opcional)_ | Altera a opção **tela cheia** do player |
| `input.time_ms` | _Boolean (opcional)_ | Alterar o tempo atual da mídia em milissegundos `v2.20.0+` |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('MediaPlayerAction', {
    mute: false,
    repeat: true,
    volume: 80,
    action: 'play'
});

//alterar volume
h.hly('MediaPlayerAction', {volume: 80});

//deixar no mudo
h.hly('MediaPlayerAction', {mute: true});

//parar execução atual
h.hly('MediaPlayerAction', {action: 'stop'});
```

---


### hly('GetLyricsPlaylist')
### hly('GetSongPlaylist')
Lista de reprodução de letras



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Lyrics](#lyrics)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetLyricsPlaylist');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].title);
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
| `input.index` | _Number (opcional)_ | Posição na lista onde o item será adicionado (inicia em zero). Os itens são adicionados no final da lista por padrão. `Padrão: -1` |
| `input.media_playlist` | _Boolean (opcional)_ | Adicionar as letras na lista de reprodução de mídia `Padrão: false` |


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
| `input.indexes` | _Array&lt;Number&gt; (opcional)_ | Lista com a posição de cada item na lista que será removido. (Inicia em zero) |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('RemoveFromLyricsPlaylist', {id: '123'});

h.hly('RemoveFromLyricsPlaylist', {ids: ['123', '456']});

h.hly('RemoveFromLyricsPlaylist', {index: 3});

h.hly('RemoveFromLyricsPlaylist', {indexes: [3, 4, 5]});
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


### hly('AddToPlaylist', input)
- v2.20.0

Adicionar itens à lista de reprodução de mídias

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.items` | _Array&lt;[AddItem](#additem)&gt;_ | Lista com os itens que serão adicionados |
| `input.index` | _Number (opcional)_ | Posição na lista onde o item será adicionado (inicia em zero). Os itens são adicionados no final da lista por padrão. `Padrão: -1` |
| `input.ignore_duplicates` | _Boolean (opcional)_ | Não duplicar itens ao adicionar novos itens, ou seja, não adiciona um item se ele já estiver na lista. `Padrão: false` |


_Método sem retorno_

**Exemplo:**

```javascript
var r = h.hly('AddToPlaylist', {
    items: [
        {
            type: 'song',
            id: 123456
        }, {
            type: 'song',
            id: 12345678
        }
    ],
    index: 3,
    ignore_duplicates: true
});

if (r.status != 'ok') {
    h.log(r.error);
}

var items = [
    {
        type: 'title',
        name: 'Título',
        background_color: "000080"
    }, {
        type: 'song',
        id: 12345678
    }, {
        type: 'verse',
        id: '19023001'
    }, {
        type: 'verse',
        ids: ['19023001', '43003016']
    }, {
        type: 'verse',
        references: 'Sl 23.1 Rm 12:2'
    }, {
        type: 'text',
        id: 'abcxyz'
    }, {
        type: 'audio',
        name: 'example.mp3'
    }, {
        type: 'video',
        name: 'example.mp4'
    }, {
        type: 'image',
        name: 'example.jpg'
    }, {
        type: 'automatic_presentation',
        name: 'example.ap'
    }, {
        type: 'title',
        name: 'Título 2'
    }, {
        type: 'announcement',
        id: 12345678
    }, {
        type: 'announcement',
        ids: [123, 456]
    }, {
        type: 'announcement',
        name: 'example'
    }, {
        type: 'announcement',
        names: ['example 2', 'example 3']
    }, {
        type: 'announcement',
        id: 'all',
        automatic: {
            seconds: 8,
            repeat: false
        }
    }, {
        type: 'title',
        name: 'Título 3'
    }, {
        type: 'countdown',
        time: '03:15'
    }, {
        type: 'countdown_cp',
        minutes: 15,
        stop_at_zero: true
    }, {
        type: 'cp_text',
        text: 'example'
    }, {
        type: 'script',
        id: 'abcxyz'
    }, {
        type: 'api',
        id: 'abcxyz'
    }
];

var r = h.hly('AddToPlaylist', {
    items: items
});
if (r.status != 'ok') {
    h.log(r.error);
}
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
| `input.indexes` | _Array&lt;Number&gt; (opcional)_ | Lista com a posição de cada item na lista que será removido. (Inicia em zero) |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('RemoveFromMediaPlaylist', {id: 'abc'});

h.hly('RemoveFromMediaPlaylist', {ids: ['abc', 'xyz']});

h.hly('RemoveFromMediaPlaylist', {index: 3});

h.hly('RemoveFromMediaPlaylist', {indexes: [3, 4, 5]});
```

---


### hly('GetFavorites')
Itens da barra de favoritos



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Favorite Item](#favorite-item)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetFavorites');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
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


### hly('ApiAction', input)
- v2.19.0

Executa a ação de um item API existente no programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID do item |


_Método sem retorno_

**Exemplo:**

```javascript
var r = h.hly('ApiAction', {id: 'abcxyz'});

if (r.status == 'ok') {
    h.log('Ação executada');
} else {
    h.log('Erro: ' + r.error);
}
```

---


### hly('ScriptAction', input)
- v2.19.0

Executa a ação de um item **Script** existente no programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID do item |


_Método sem retorno_

**Exemplo:**

```javascript
var r = h.hly('ScriptAction', {id: 'abcxyz'});

if (r.status == 'ok') {
    h.log('Ação executada');
} else {
    h.log('Erro: ' + r.error);
}
```

---


### hly('ApiRequest', input)
- v2.19.0

Executa uma requisição para o receptor associado e retorna a resposta do receptor.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | id do receptor |
| `input.raw` | _Object_ | dados da requisição |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorno da requisição ou NULL para erro/timeout |


**Exemplo:**

```javascript
//É possível realizar requisição diretamente para um receptor criado
//Por exemplo:
//Considerando que você tenha um receptor criado para comunicação com OBS Studio via websocket e o ID do receptor seja 'abcyxz'
//você pode fazer uma requisição como no exemplo abaixo
var r = h.hly('ApiRequest', {
    id: 'abcxyz',
    raw: {
        'request-type': 'GetSourceActive',
        'sourceName': 'exemplo'
    }
});
if (r.status == 'ok') {
    h.log('Resposta da requisição: ' + r.data);
    var obj = JSON.parse(r.data);
    if (obj.sourceActive) {
        h.log('A fonte exemplo está ativa');
    } else {
        h.log('A fonte exemplo não está ativa');
    }
} else {
    h.log('Erro: ' + r.error);
}
```

---


### hly('GetCurrentPresentation')
- v2.19.0

Item sendo apresentado no momento ou **null** se não tiver apresentação sendo exibida



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.id` | _String_ | ID do item |
| `data.type` | _String_ | Tipo do item. Pode ser: `title`  `song`  `verse`  `text`  `audio`  `video`  `image`  `announcement`  `automatic_presentation`  `countdown`  `countdown_cp`  `cp_text`  `api`  `script` |
| `data.name` | _String_ | Nome do item |
| `data.slide_number` | _Number_ | Começa em 1 `v2.20.0+` |
| `data.total_slides` | _Number_ | Total de slides `v2.20.0+` |
| `data.slide_type` | _String_ | Um dos seguintes valores: `default`  `wallpaper`  `blank`  `black`  `final_slide` `v2.20.0+` |


**Exemplo:**

```javascript
var r = h.hly('GetCurrentPresentation');
if (r.data == null) {
    //não há apresentação em exibição no momento
}

switch (r.data.type) {
    case 'song':
        //uma música sendo apresentada
        break;
    case 'verse':
        //um versículo sendo apresentado
        break;
}
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


### hly('GetF8')
### hly('GetF9')
### hly('GetF10')
- v2.19.0

Retorna o estado atual da respectiva opção **F8 (papel de parede), F9 (tela vazia) ou F10 (tela preta)**



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | **true** ou **false** |


**Exemplo:**

```javascript
var r = h.hly('GetF8');
h.log('F8: ' + r.data);

var r = h.hly('GetF9');
h.log('F9: ' + r.data);

var r = h.hly('GetF10');
h.log('F10: ' + r.data);
```

---


### hly('SetF8', input)
### hly('SetF9', input)
### hly('SetF10', input)
- v2.19.0

Altera o estado atual da respectiva opção **F8 (papel de parede), F9 (tela vazia) ou F10 (tela preta)**

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.enable` | _Boolean_ | **true** ou **false** |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetF8', {enable: true});

h.hly('SetF9', {enable: false});

h.hly('SetF10', {enable: true});
```

---


### hly('ToggleF8')
### hly('ToggleF9')
### hly('ToggleF10')
- v2.19.0

Troca o estado atual da respectiva opção **F8 (papel de parede), F9 (tela vazia) ou F10 (tela preta)**



_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ToggleF8');

h.hly('ToggleF9');

h.hly('ToggleF10');
```

---


### hly('ActionNext')
- v2.19.0

Executa um comando de **avançar** na apresentação atual



_Método sem retorno_

---


### hly('ActionPrevious')
- v2.19.0

Executa um comando de **voltar** na apresentação atual



_Método sem retorno_

---


### hly('ActionGoToIndex', input)
- v2.19.0

Altera o slide em exibição a partir do índice do slide

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.index` | _Number_ | Índice do slide na apresentação (começa em zero) |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ActionGoToIndex', {index: 3});
```

---


### hly('ActionGoToSlideDescription', input)
- v2.19.0

Altera o slide em exibição a partir do nome da descrição do slide

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.name` | _String_ | Nome da descrição do slide |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ActionGoToSlideDescription', {name: 'Verse 1'});
```

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


### hly('GetBackgrounds', input)
Lista dos temas e planos de fundo

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _Object (opcional)_ | Filtro |
| `input.type` | _String (opcional)_ | Pode ser: theme, my_video, my_image, video, image |
| `input.tag` | _String (opcional)_ |  |
| `input.tags` | _Array&lt;String&gt; (opcional)_ |  |
| `input.intersection` | _Boolean (opcional)_ | Se o campo **input.tags** estiver preenchido com múltiplos itens, a opção **input.intersection** define o tipo de junção. Se **true**, o filtro retornará apenas itens que contém **todas** as tags informadas, se **false**, o filtro retornará os itens que têm pelo menos uma tag das tags informadas `Padrão: false` |


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
| `input.intersection` | _Boolean (opcional)_ | Se o campo **input.tags** estiver preenchido com múltiplos itens, a opção **input.intersection** define o tipo de junção. Se **true**, o filtro retornará apenas itens que contém **todas** as tags informadas, se **false**, o filtro retornará os itens que têm pelo menos uma tag das tags informadas `Padrão: false` |


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


### hly('GetColorMap', input)
- v2.20.0

Retorna as informações de cor predominante de um respectivo tipo de item<br/>O array retornado contém 8 índices, e cada índice corresponde ao trecho conforme imagem de exemplo a seguir.<br/> <br/>![Color Map Example](https://holyrics.com.br/images/color_map_item_example.png)<br/>

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.type` | _String_ | Um dos seguintes valores:<br/>**background** - um item de tema ou plano de fundo<br/>**presentation** - apresentação atual em exibição<br/>**image** - uma imagem da aba 'imagens'<br/>**video** - um vídeo da aba 'vídeos'<br/>**printscreen** - um printscreen atual de uma tela do sistema<br/> |
| `input.source` | _Object (opcional)_ | O item de acordo com o tipo informado:<br/>**background** - ID do tema ou plano de fundo<br/>**presentation** - não é necessário informar um valor, a apresentação da tela público será retornada<br/>**image** - o nome do arquivo da aba 'imagens'<br/>**video** - o nome do arquivo da aba 'vídeos'<br/>**printscreen** `opcional` -  o nome da tela (public, screen_2, screen_3, ...); o padrão é `public`<br/> |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.hex` | _String_ | Cor no formato hexadecimal |
| `data.*.red` | _Number_ | Vermelho  0-255 |
| `data.*.green` | _Number_ | Verde  0-255 |
| `data.*.blue` | _Number_ | Azul  0-255 |


**Exemplo:**

```javascript
var r = h.hly('GetColorMap', {
    type: 'background',
    source: 12345678
});

if (r.data[0].red >= 200) {
    //red >= 200
}

var r = h.hly('GetColorMap', {
    type: 'presentation'
});

var r = h.hly('GetColorMap', {
    type: 'image',
    source: 'example.png'
});

var r = h.hly('GetColorMap', {
    type: 'video',
    source: 'dir/video.mp4'
});

var r = h.hly('GetColorMap', {
    type: 'printscreen'
});

var r = h.hly('GetColorMap', {
    type: 'printscreen',
    source: 'screen_2'
});

//Chamadas alternativas
var arr = h.getColorMap('presentation');
var arr = h.getColorMap('video', 'filename.mp4');
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


### hly('GetCurrentSchedule')
Programação atual (selecionada na janela principal do programa)



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[Schedule](#schedule)_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetCurrentSchedule');
var s = r.data[0];
h.log(s.datetime);
h.log(s.name);
h.log(s.lyrics_playlist);
h.log(s.media_playlist);
```

---


### hly('GetSchedules', input)
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


### hly('GetSavedPlaylists')
- v2.19.0

Retorna as listas de reprodução salvas



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.id` | _String_ | ID do item |
| `data.*.name` | _String_ | Nome do item |
| `data.*.items` | _Array&lt;[Item](#item)&gt;_ | Itens salvos na lista |


**Exemplo:**

```javascript
var r = h.hly('GetSavedPlaylists');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('LoadSavedPlaylist', input)
- v2.19.0

Preenche a lista de mídias da lista de reprodução selecionada atualmente no programa com a lista informada

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.name` | _String_ | Nome da lista de reprodução salva |


_Método sem retorno_

**Exemplo:**

```javascript
var r = h.hly('LoadSavedPlaylist', {name: 'name'});
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
| `data` | _Array&lt;String&gt;_ | Data e hora no formato: YYYY-MM-DD HH:MM |


**Exemplo:**

```javascript
var r = h.hly('GetHistory', {id: '123'});
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i]);
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
| `data.*.history` | _Array&lt;String&gt;_ | Data e hora no formato: YYYY-MM-DD HH:MM |


**Exemplo:**

```javascript
var r = h.hly('GetHistories');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].music_id);
    h.log(r.data[i].history);
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


### hly('GetCommunicationPanelInfo')
### hly('GetCPInfo')
### hly('GetCPSettings')
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
| `data.stopwatch_show` | _Boolean_ | Se um cronômetro está em exibição `v2.20.0+` |
| `data.stopwatch_time` | _Number_ | O tempo atual do cronômetro em exibição (em segundos) `v2.20.0+` |
| `data.theme` | _Number_ | ID do tema `v2.20.0+` |
| `data.countdown_font_relative_size` | _Number_ | Tamanho relativo da contagem regressiva `v2.20.0+` |
| `data.countdown_font_color` | _String_ | Cor da fonte da contagem regressiva `v2.20.0+` |
| `data.stopwatch_font_color` | _String_ | Cor da fonte do cronômetro `v2.20.0+` |
| `data.time_font_color` | _String_ | Cor da fonte da hora `v2.20.0+` |
| `data.display_clock_as_background` | _Boolean_ | Exibir relógio como plano de fundo `v2.20.0+` |
| `data.display_clock_on_alert` | _Boolean_ | Exibir relógio no alerta `v2.20.0+` |
| `data.countdown_display_location` | _String_ | Local de exibição da contagem regressiva ou cronômetro. `FULLSCREEN`  `FULLSCREEN_OR_ALERT`  `ALERT` `v2.20.0+` |
| `data.display_clock_with_countdown_fullscreen` | _Boolean_ | Exibir relógio junto da contagem regressiva ou cronômetro quando exibido em tela cheia `v2.20.0+` |
| `data.display_vlc_player_remaining_time` | _Boolean_ | Exibir tempo restante da mídia em execução no VLC Player `v2.20.0+` |


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


### hly('SetCommunicationPanelSettings', input)
### hly('SetCPSettings')
- v2.20.0

Alterar configuração atual do painel de comunicação

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.text` | _String (opcional)_ | Texto atual |
| `input.show` | _Boolean (opcional)_ | Exibir o texto atual |
| `input.display_ahead` | _Boolean (opcional)_ | Opção *'exibir à frente de tudo'* |
| `input.theme` | _Boolean (opcional)_ | ID ou nome do tema padrão |
| `input.alert_text` | _String (opcional)_ | Texto atual do alerta |
| `input.alert_show` | _Boolean (opcional)_ | Ativar a exibição do alerta |
| `input.countdown_font_relative_size` | _Number (opcional)_ | Tamanho relativo da contagem regressiva |
| `input.countdown_font_color` | _String (opcional)_ | Cor da fonte da contagem regressiva |
| `input.stopwatch_font_color` | _String (opcional)_ | Cor da fonte do cronômetro |
| `input.time_font_color` | _String (opcional)_ | Cor da fonte da hora |
| `input.display_clock_as_background` | _Boolean (opcional)_ | Exibir relógio como plano de fundo |
| `input.display_clock_on_alert` | _Boolean (opcional)_ | Exibir relógio no alerta |
| `input.countdown_display_location` | _String (opcional)_ | Local de exibição da contagem regressiva ou cronômetro. `FULLSCREEN`  `FULLSCREEN_OR_ALERT`  `ALERT` |
| `input.display_clock_with_countdown_fullscreen` | _Boolean (opcional)_ | Exibir relógio junto da contagem regressiva ou cronômetro quando exibido em tela cheia |
| `input.display_vlc_player_remaining_time` | _Boolean (opcional)_ | Exibir tempo restante da mídia em execução no VLC Player |


_Método sem retorno_

**Exemplo:**

```javascript
var r = h.hly('SetCommunicationPanelSettings', {
    display_clock_as_background: false,
    display_clock_on_alert: true
});
```

---


### hly('StartCountdownCommunicationPanel', input)
### hly('StartCountdownCP', input)
Inicia uma contagem regressiva no painel de comunicação

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.minutes` | _Number_ | Quantidade de minutos |
| `input.seconds` | _Number_ | Quantidade de segundos |
| `input.yellow_starts_at` | _Number (opcional)_ | Valor em segundos para definir a partir de quanto tempo a contagem regressiva ficará amarela |
| `input.stop_at_zero` | _Boolean (opcional)_ | Parar a contagem regressiva ao chegar em zero `Padrão: false` |


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


### hly('StartTimerCommunicationPanel')
### hly('StartTimerCP', input)
- v2.20.0

Inicia um cronômetro no painel de comunicação



_Método sem retorno_

**Exemplo:**

```javascript
h.hly('StartTimerCommunicationPanel');
h.hly('StartTimerCP');
```

---


### hly('StopTimerCommunicationPanel')
### hly('StopTimerCP')
- v2.20.0

Encerra o cronômetro atual do painel de comunicação



_Método sem retorno_

**Exemplo:**

```javascript
h.hly('StopTimerCommunicationPanel');
h.hly('StopTimerCP');
```

---


### hly('SetTextCommunicationPanel', input)
### hly('SetTextCP', input)
Alterar o texto do painel de comunicação

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.text` | _String (opcional)_ | Alterar o texto do painel de comunicação. [Styled Text](#styled-text) a partir da v2.19.0 |
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


### hly('CommunicationPanelCallAttention')
### hly('CPCallAttention')
- v2.20.0

Executa a opção 'chamar atenção' disponível no painel de comunicação



_Método sem retorno_

**Exemplo:**

```javascript
h.hly('CommunicationPanelCallAttention');
```

---


### hly('GetWallpaperSettings')
- v2.19.0

Configurações do papel de parede



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.image_base64` | _String_ | Imagem do papel de parede em base 64 |
| `data.enabled` | _Boolean_ | Exibir papel de parede |
| `data.fill_color` | _String_ | Cor em hexadecimal definida na opção **preencher**. |
| `data.extend` | _Boolean_ | Estender papel de parede |
| `data.show_clock` | _Boolean_ | Exibir relógio |


**Exemplo:**

```javascript
var r = h.hly('GetWallpaperSettings');
h.log('Wallpaper enabled: ' + r.data.enabled);
```

---


### hly('SetWallpaperSettings', input)
- v2.19.0

Alterar as configurações do papel de parede

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _String (opcional)_ | Local do arquivo na aba **Imagens** |
| `input.enabled` | _Boolean (opcional)_ | Exibir papel de parede |
| `input.fill_color` | _String (opcional)_ | Cor em hexadecimal definida na opção **preencher**. **NULL** para desativar |
| `input.extend` | _Boolean (opcional)_ | Estender papel de parede |
| `input.show_clock` | _Boolean (opcional)_ | Exibir relógio |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna **true** ou uma lista com os erros ocorridos |


**Exemplo:**

```javascript
var r = h.hly('SetWallpaperSettings', {
    file: 'image.jpg',
    enabled: true,
    fill_color: '000000'
});
```

---


### hly('GetDisplaySettings')
- v2.19.0

Lista das configurações de exibição de cada tela



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[DisplaySettings](#display-settings)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetDisplaySettings');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].id);
    h.log(r.data[i].name);
    h.log('');
}
```

---


### hly('SetDisplaySettings', input)
- v2.19.0

Alterar as configurações de exibição de uma tela

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _[DisplaySettings](#display-settings)_ | Novas configurações. As configurações são individualmente opcionais. Preencha apenas os campos que deseja alterar. |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna **true** ou uma lista com os erros ocorridos |


**Exemplo:**

```javascript
var r = h.hly('SetDisplaySettings', {
    id: 'public',
    margin: {
        top: 10, right: 5, bottom: 10, left: 5
    }
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


### hly('SetBpm', input)
Altera o valor BPM atual do programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.bpm` | _Number_ | Valor BPM |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetBpm', {bpm: 80});
```

---


### hly('GetHue')
- v2.19.0

Retorna o valor matiz atual definido no programa



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Valor matiz atual. Mínimo=0, Máximo=360. Retorna **null** se desativado. |


**Exemplo:**

```javascript
var r = h.hly('GetHue');
h.log('HUE: ' + r.data);
```

---


### hly('SetHue', input)
- v2.19.0

Altera o valor matiz atual do programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.hue` | _Number_ | Valor matiz. Mínimo=0, Máximo=360 ou **null** para desativar. |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetHue', {hue: 250});

h.hly('SetHue', {hue: null});
```

---


### hly('GetRuntimeEnvironment')
### hly('GetRE')
- v2.19.0

Retorna o nome do ambiente de execução definido atualmente nas configurações do programa.



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Nome do ambiente de execução |


**Exemplo:**

```javascript
var r = h.hly('GetRuntimeEnvironment');
h.log('current runtime environment: ' + r.data);
```

---


### hly('SetRuntimeEnvironment', input)
### hly('SetRE', input)
- v2.19.0

Altera o ambiente de execução atual.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.name` | _String_ | Nome do ambiente de execução |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetRuntimeEnvironment', {name: 'abc'});
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


### hly('GetSyncStatus')
- v2.19.0

Retorna o estado atual da sincronização online via Google Drive™



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.enabled` | _Boolean_ | Se a sincronização está ativada |
| `data.started` | _Boolean_ | Se a sincronização foi iniciada (internet disponível, por exemplo) |
| `data.progress` | _Number_ | Progresso da sincronização de 0 a 100 |


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


### setCurrentTime(time)
- v2.20.0

Alterar o tempo atual da mídia em milissegundos

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `time` | _Number_ | Alterar o tempo atual da mídia em milissegundos |


_Método sem retorno_

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
    }, {
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
    }, {
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
Solicita uma entrada em formato **textarea** possibilitando texto com múltiplas linhas

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `title` | _String_ | Nome do componente |
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
| `items.*.label` | _String (opcional)_ | Nome que será exibido representando o item |
| `items.*.selected` | _Boolean (opcional)_ | Para definir o item selecionado por padrão. v2.19.0+ |
| `notification` | _Boolean (opcional)_ | Exibe uma notificação em vez de abrir a janela diretamente |


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
    }, {
        id: 2,
        type: 'test2',
        label: 'XYZ',
        selected: true //selecionado por padrão
    }, {
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


### multipleItemChooser(title, items, notification = false)
- v2.19.0

Abre uma janela para selecionar múltiplos itens em uma lista de valores

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `title` | _String_ | Título na janela |
| `items` | _Object_ | Lista de itens que serão exibidos na lista |
| `items.*.label` | _String (opcional)_ | Nome que será exibido representando o item |
| `items.*.selected` | _Boolean (opcional)_ | Para definir se o item será selecionado por padrão. |
| `notification` | _Boolean (opcional)_ | Exibe uma notificação em vez de abrir a janela diretamente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna os itens selecionados pelo usuário (pode ser NULL) |


**Exemplo:**

```javascript
var r = h.multipleItemChooser("Selecione os itens", ["abc", "xyz", "123"]);
h.log("Itens selecionados: " + r);

var r = h.multipleItemChooser("Selecione os números", [1, 2, 3, 4, 5]);
h.log("Números selecionados: " + r);

var items = [
    {
        id: 1,
        type: 'test1',
        label: 'ABC',
        selected: true //selecionado por padrão
    }, {
        id: 2,
        type: 'test2',
        label: 'XYZ'
    }, {
        id: 3,
        type: 'test3',
        label: '123',
        selected: true //selecionado por padrão
    }
];
var r = h.multipleItemChooser("Selecione os itens", items, true); //notificação
if (r == null) {
    h.log("Cancelado");
} else {
    h.log("Itens selecionados");
    for (var i = 0; i < r.length; i++) {
        h.log("ID: " + r[i].id);
        h.log("Tipo: " + r[i].type);
        h.log("Nome: " + r[i].label);
    }
}
```

---


### confirm(msg, title = 'Confirm', notification = false)
- v2.19.0

Abre uma janela de confirmação, exibindo os botões **OK** e **Cancelar**

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `msg` | _String_ | Mensagem que será exibida |
| `title` | _String_ | Título da janela |
| `notification` | _Boolean (opcional)_ | Exibe uma notificação em vez de abrir a janela diretamente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | Retorna **true** ou **false** |


**Exemplo:**

```javascript
if (h.confirm("Realizar tarefa agora?", "title")) {
    //ok
} else {
    //cancel
}
```

---


### yesNo(msg, title = 'Confirm', notification = false)
- v2.19.0

Abre uma janela de confirmação, exibindo os botões **Sim** e **Não**

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `msg` | _String_ | Mensagem que será exibida |
| `title` | _String_ | Título da janela |
| `notification` | _Boolean (opcional)_ | Exibe uma notificação em vez de abrir a janela diretamente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | Retorna **true** ou **false** |


**Exemplo:**

```javascript
if (h.yesNo("Realizar tarefa agora?", "title")) {
    //yes
} else {
    //no
}
```

---


### notification(msg, duration = 0)
### notificationError(msg, duration = 0)
### notificationWarning(msg, duration = 0)
- v2.19.0

Exibe uma notificação no canto da tela

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `msg` | _String_ | Mensagem que será exibida |
| `duration` | _Number (opcional)_ | Tempo para a notificação ser ocultada automaticamente. Se o valor for menor ou igual a zero a notificação não será ocultada automaticamente. |


_Método sem retorno_

**Exemplo:**

```javascript
h.notification("Tarefa realizada");
```

---


### lyricsChooser()
### songChooser()
- v2.19.0

Abre uma janela para selecionar uma música



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[Lyrics](#lyrics)_ | Retorna o item selecionado pelo usuário (pode ser NULL) |


**Exemplo:**

```javascript
var r = h.lyricsChooser();
if (r == null) {
    h.log("Cancelado");
} else {
    h.log("Item selecionado: " + r.title);
}
```

---


### themeChooser()
- v2.19.0

Abre uma janela para selecionar um tema



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[Background](#background)_ | Retorna o item selecionado pelo usuário (pode ser NULL) |


**Exemplo:**

```javascript
var r = h.themeChooser();
if (r == null) {
    h.log("Cancelado");
} else {
    h.log("Item selecionado: " + r.name);
}
```

---


### imageChooser()
- v2.19.0

Abre uma janela para selecionar uma imagem



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
|  | _Object_ | Retorna o item selecionado pelo usuário (pode ser NULL) |
| `*.id` | _String_ | ID do item |
| `*.name` | _String_ | Nome do item |
| `*.isDir` | _Boolean_ | Retorna **true** se for uma pasta ou **false** se for arquivo. |


**Exemplo:**

```javascript
var r = h.imageChooser();
if (r == null) {
    h.log("Cancelado");
} else {
    h.log("Item selecionado: " + r.name);
}
```

---


### audioChooser()
- v2.19.0

Abre uma janela para selecionar um áudio



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
|  | _Object_ | Retorna o item selecionado pelo usuário (pode ser NULL) |
| `*.id` | _String_ | ID do item |
| `*.name` | _String_ | Nome do item |
| `*.isDir` | _Boolean_ | Retorna **true** se for uma pasta ou **false** se for arquivo. |


**Exemplo:**

```javascript
var r = h.audioChooser();
if (r == null) {
    h.log("Cancelado");
} else {
    h.log("Item selecionado: " + r.name);
}
```

---


### videoChooser()
- v2.19.0

Abre uma janela para selecionar um vídeo



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
|  | _Object_ | Retorna o item selecionado pelo usuário (pode ser NULL) |
| `*.id` | _String_ | ID do item |
| `*.name` | _String_ | Nome do item |
| `*.isDir` | _Boolean_ | Retorna **true** se for uma pasta ou **false** se for arquivo. |


**Exemplo:**

```javascript
var r = h.videoChooser();
if (r == null) {
    h.log("Cancelado");
} else {
    h.log("Item selecionado: " + r.name);
}
```

---


### backgroundChooser()
- v2.19.0

Abre uma janela para selecionar um plano de fundo



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[Background](#background)_ | Retorna o item selecionado pelo usuário (pode ser NULL) |


**Exemplo:**

```javascript
var r = h.backgroundChooser();
if (r == null) {
    h.log("Cancelado");
} else {
    h.log("Item selecionado: " + r.name);
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
| `copyright` | _String_ | Copyright da música |
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
| `type` | _String_ | Tipo do item. Pode ser: `title`  `song`  `verse`  `text`  `audio`  `video`  `image`  `announcement`  `automatic_presentation`  `countdown`  `countdown_cp`  `cp_text`  `api`  `script` |
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
| `datetime` | _String_ | Data e hora no formato: YYYY-MM-DD HH:MM |
| `lyrics_playlist` | _Array&lt;[Lyrics](#lyrics)&gt;_ | Lista de letras |
| `media_playlist` | _Array&lt;[Item](#item)&gt;_ | Lista de mídias |
| `responsible` | _[Member](#member)_ | Integrante definido como responsável pelo evento |
| `members` | _Array&lt;Object&gt;_ | Lista de integrantes |
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
| `min` | _Number (opcional)_ | Disponível se o tipo for **number**. Define o valor mínimo permitido `Padrão: 0` |
| `max` | _Number (opcional)_ | Disponível se o tipo for **number**. Define o valor máximo permitido `Padrão: 100` |
| `show_as_combobox` | _Boolean (opcional)_ | Disponível se o tipo for **number**. Exibe a lista de valores como combobox e não como spinner `Padrão: false` |

## Display Settings
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |
| `stage_view` | _[StageView](#stage-view)_ | Configurações da visão do palco. (Indisponível para tela público) |
| `slide_info` | _[SlideAdditionalInfo](#slide-additional-info)_ | Informações adicionais do slide |
| `slide_translation` | _String_ | Nome da tradução |
| `bible_version_tab` | _Number_ | Número da aba (1, 2 ou 3) da tradução da Bíblia exibida na tela, conforme traduções carregadas na janela da Bíblia |
| `margin` | _Object_ | Margens definidas na opção **Editar posição da tela**. margin.top, margin.right, margin.bottom, margin.left |
| `area` | _[Rectangle](#rectangle)_ | Área da tela com as margens aplicadas (se disponível) |
| `total_area` | _[Rectangle](#rectangle)_ | Área total da tela no sistema |
| `hide` | _Boolean_ | Ocultar a tela |
| `show_items` | _Object_ | Define os tipos de apresentação que serão exibidos (disponível apenas para telas de transmissão - imagem e html) |
| `show_items.lyrics` | _Boolean_ | Letra de música |
| `show_items.text` | _Boolean_ | Texto |
| `show_items.verse` | _Boolean_ | Versículo |
| `show_items.image` | _Boolean_ | Imagem |
| `show_items.alert` | _Boolean_ | Alerta |
| `show_items.announcement` | _Boolean_ | Anúncio |
| `media_player.show` | _Boolean_ | Exibir VLC Player `v2.20.0+` |
| `media_player.margin` | _[Rectangle](#rectangle)_ | Margem para exibição dos vídeos pelo VLC Player `v2.20.0+` |

## Stage View
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `enabled` | _Boolean_ | Visão do palco ativada |
| `preview_mode` | _String_ | Modo de visualização das letras. Opções disponíveis:<br/>CURRENT_SLIDE<br/>FIRST_LINE_OF_THE_NEXT_SLIDE_WITH_SEPARATOR<br/>FIRST_LINE_OF_THE_NEXT_SLIDE_WITHOUT_SEPARATOR<br/>NEXT_SLIDE<br/>CURRENT_AND_NEXT_SLIDE<br/>ALL_SLIDES |
| `uppercase` | _Boolean_ | Exibir em maiúsculo |
| `remove_line_break` | _Boolean_ | Remover quebra de linha |
| `show_comment` | _Boolean_ | Exibir comentários |
| `show_advanced_editor` | _Boolean_ | Exibir edições avançadas |
| `show_communication_panel` | _Boolean_ | Exibir conteúdo do painel de comunicação |
| `custom_theme` | _Number_ | ID do tema personalizado utilizado nas apresentações |
| `apply_custom_theme_to_bible` | _Boolean_ | Utilizar o tema personalizado nos versículos |
| `apply_custom_theme_to_text` | _Boolean_ | Utilizar o tema personalizado nos textos |

## Slide Additional Info
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `info_1` | _Object_ |  |
| `info_1.show_page_count` | _Boolean_ | Exibir contador de slides |
| `info_1.show_slide_description` | _Boolean_ | Exibir descrição do slide (coro, por exemplo) |
| `info_1.horizontal_align` | _String_ | Alinhamento horizontal da informação no slide. left, center, right |
| `info_1.vertical_align` | _String_ | Alinhamento vertical da informação no slide. top, bottom |
| `info_2` | _Object_ |  |
| `info_2.show` | _Boolean_ |  |
| `info_2.layout_row_1` | _String_ | Layout da informação da primeira linha [Slide Additional Info Layout](#slide-additional-info-layout) |
| `info_2.layout_row_2` | _String (opcional)_ | Layout da informação da segunda linha [Slide Additional Info Layout](#slide-additional-info-layout) |
| `info_2.horizontal_align` | _String_ | Alinhamento horizontal da informação no slide. left, center, right |
| `info_2.vertical_align` | _String_ | Alinhamento vertical da informação no slide. top, bottom |
| `font` | _Object_ |  |
| `font.name` | _String_ | Nome da fonte. Se for **null**, utiliza a fonte padrão do tema. |
| `font.bold` | _Boolean_ | Negrito. Se for **null**, utiliza a configuração padrão do tema |
| `font.italic` | _Boolean_ | Itálido. Se for **null**, utiliza a configuração padrão do tema |
| `font.color` | _String_ | Cor da fonte em hexadecimal. Se for **null**, utiliza a cor da fonte padrão do tema |
| `height` | _Number_ | Altura em porcentagem em relação à altura do slide |
| `paint_theme_effect` | _String_ | Renderizar o texto com os efeitos contorno, brilho e sombra do tema, se disponível |

## Rectangle
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `x` | _Number_ |  |
| `y` | _Number_ |  |
| `width` | _Number_ |  |
| `height` | _Number_ |  |

## Custom Message
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |
| `message_model` | _String_ | Mensagem sem preenchimento |
| `message_example` | _String_ | Mensagem de exemplo com o nome dos parâmetros preenchidos |
| `variables` | _Array&lt;[CustomMessageParam](#custom-message-param)&gt;_ | Parâmetros da mensagem |

## Custom Message Param
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `position` | _Number_ | Posição do parâmetro na mensagem (em número de caracteres) |
| `name` | _String_ | Nome do item |
| `only_number` | _Boolean_ | Parâmetro aceita somente números |
| `uppercase` | _Boolean_ | Parâmetro exibido sempre em maiúsculo |
| `suggestions` | _Array&lt;String&gt; (opcional)_ | Lista com valores padrões para o parâmetro |

## Quiz Question
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `title` | _String_ | Pergunta |
| `alternatives` | _Array&lt;String&gt;_ | Alternativas |
| `correct_alternative_number` | _Number (opcional)_ | Número da alternativa correta. Começa em 1 `Padrão: 1` |
| `source` | _String (opcional)_ | Fonte da resposta |

## Quiz Settings
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `correct_answer_color_font` | _String (opcional)_ | Cor da fonte para a resposta correta |
| `correct_answer_color_background` | _String (opcional)_ | Cor de fundo para a resposta correta |
| `incorrect_answer_color_font` | _String (opcional)_ | Cor da fonte para a resposta incorreta |
| `incorrect_answer_color_background` | _String (opcional)_ | Cor de fundo para a resposta incorreta |
| `question_and_alternatives_different_slides` | _Boolean (opcional)_ | Exibir a pergunta e as alternativas em slides separados `Padrão: false` |
| `display_alternatives_one_by_one` | _Boolean (opcional)_ | Exibir as alternativas uma a uma `Padrão: true` |
| `alternative_char_type` | _String (opcional)_ | Tipo de caractere para listar as alternativas `number (1, 2, 3...)`  `alpha (A, B, C...)` `Padrão: 'alpha'` |
| `alternative_separator_char` | _String (opcional)_ | Caractere separador. Valores permitidos:  ` `  `.`  `)`  `-`  `:` `Padrão: '.'` |

## AddItem
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | Tipo do item. Pode ser: `title`  `song`  `verse`  `text`  `audio`  `video`  `image`  `announcement`  `automatic_presentation`  `countdown`  `countdown_cp`  `cp_text`  `api`  `script` |

## AddItemTitle
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | title |
| `name` | _String_ | Nome do item |
| `background_color` | _String (opcional)_ | Cor de fundo em hexadecimal, exemplo: 000080 |
| `collapsed` | _Boolean (opcional)_ |  `Padrão: false` |

## AddItemSong
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | song |
| `id` | _String_ | ID do item |

## AddItemVerse
**id**, **ids** ou **references**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | verse |
| `id` | _String (opcional)_ | Para exibir um versículo. ID do item no formato LLCCCVVV.<br/>Exemplo: '19023001' (livro 19, capítulo 023, versículo 001) |
| `ids` | _Array&lt;String&gt; (opcional)_ | Para exibir uma lista de versículos. Lista com o ID de cada versículo.<br/>Exemplo: ['19023001', '43003016', '45012002'] |
| `references` | _String (opcional)_ | Referências. Exemplo: **João 3:16** ou **Rm 12:2** ou **Gn 1:1-3 Sl 23.1** |

## AddItemText
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | text |
| `id` | _String_ | ID do item |

## AddItemAudio
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | audio |
| `name` | _String_ | Nome do arquivo |

## AddItemVideo
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | video |
| `name` | _String_ | Nome do arquivo |

## AddItemImage
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | image |
| `name` | _String_ | Nome do arquivo |

## AddItemAutomaticPresentation
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | automatic_presentation |
| `name` | _String_ | Nome do arquivo |

## AddItemAnnouncement
**id**, **ids**, **name** ou **names**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | announcement |
| `id` | _String (opcional)_ | ID do anúncio. Pode ser **all** para exibir todos |
| `ids` | _Array&lt;String&gt; (opcional)_ | Lista com o ID de cada anúncio |
| `name` | _String (opcional)_ | Nome do anúncio |
| `names` | _Array&lt;String&gt; (opcional)_ | Lista com o nome de cada anúncio |
| `automatic` | _[Automatic](#automatic-presentation) (opcional)_ | Se informado, a apresentação dos itens será automática |

## AddItemCountdown
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | countdown |
| `time` | _String_ | HH:MM ou MM:SS |
| `exact_time` | _Boolean (opcional)_ | Se **true**, `time` deve ser HH:MM (hora e minuto exato). Se **false**, `time` deve ser MM:SS (quantidade de minutos e segundos) `Padrão: false` |
| `text_before` | _String (opcional)_ | Texto exibido na parte superior da contagem regressiva |
| `text_after` | _String (opcional)_ | Texto exibido na parte inferior da contagem regressiva |
| `zero_fill` | _Boolean (opcional)_ | Preencher o campo 'minuto' com zero à esquerda `Padrão: false` |
| `countdown_relative_size` | _Number (opcional)_ | Tamanho relativo da contagem regressiva `Padrão: 250` |

## AddItemCountdownCommunicationPanel
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | countdown_cp |
| `minutes` | _Number_ | Quantidade de minutos |
| `seconds` | _Number_ | Quantidade de segundos |
| `stop_at_zero` | _Boolean (opcional)_ | Parar a contagem regressiva ao chegar em zero `Padrão: false` |
| `description` | _String_ | Descrição do item |

## AddItemTextCommunicationPanel
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | cp_text |
| `name` | _String_ | Nome do item |
| `text` | _String_ | Texto |
| `display_ahead` | _Boolean (opcional)_ | Alterar a opção *'exibir à frente de tudo'* |

## AddItemScript
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | script |
| `description` | _String_ | Descrição do item |
| `inputs` | _Object (opcional)_ | Valor padrão para [Function Input](https://github.com/holyrics/Scripts/blob/main/FunctionInput.md) |

## AddItemAPI
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | api |
| `description` | _String_ | Descrição do item |
| `inputs` | _Object (opcional)_ | Valor padrão para [Function Input](https://github.com/holyrics/Scripts/blob/main/FunctionInput.md) |

# Slide Additional Info Layout
Coloque entre os caracteres **< >** os textos que deseja exibir
<br/>
E coloque dentro de **% %** o nome do campo que deseja utilizar
<br/>
Exemplo:

`<%title%>< (%author%)>`
<br/>
Se transforma em: **Título (Autor)**
<br/>
Mas se o campo **autor** não estiver disponível, será exibido apenas **Título**, e não **Título ()**
<br/>

`<%title%>< - %author%>`
<br/>
Se transforma em: **Título - Autor**
<br/>
Mas se o campo **autor** não estiver disponível, será exibido apenas **Título**, e não **Título -**
<br/>

Também é possível utilizar os campos **extras** criados pelo próprio usuário para as músicas, por exemplo:
<br/>
Caso exista um campo extra chamado **Ano**, pode ser utilizado dessa forma:
<br/>
`<title>< - %author%><, %Ano%>`
<br/>
Se transforma em: **Título - Autor, 2023**

# Styled Text
Para exibir um texto com formatação avançada, inicie o texto com **&lt;styled&gt;**

Tags HTML disponíveis

```
<styled>
<b>negrito</b>
<i>itálico</i>
<u>sublinhado</u>
<color:0000FF>cor da fonte</color>
<font:Times New Roman>nome da fonte</font>
<size:70>tamanho relativo da fonte 70%</size>
```
