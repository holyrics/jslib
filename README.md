# jslib
**PT** | [EN](README-en.md)

Métodos da classe JSLib disponível para uso nos scripts do programa Holyrics.<br>

É possível utilizar a variável ```jslib``` ou a variável ```h``` para acessar os métodos disponíveis.

Por exemplo:
```javascript
jslib.log('Exemplo');
h.log('Exemplo');
```

## JSCommunity

Para uso da biblioteca [JSCommunity](https://github.com/holyrics/JSCommunity), utilize a variável `jsc`.<br>

Por exemplo:
```javascript
var r = jsc.utils.n3(5);
// r: 005
```

## ECMAScript - ECMA-262 Edition 5.1

Apesar do padrão `ECMA-262 Edition 5.1` ser o utilizado para criação de código JavaScript no programa, algumas praticidades foram adicionadas na `v2.23.0` do Holyrics.

### Arrow Function

Compatibilidade para criação de código utilizando a sintaxe **Arrow Function**.<br>
O programa converte o código em tempo real, transformando **Arrow Function** em **Anonymous Function**.

Por exemplo:
```javascript
//Arrow Function
var members = h.getMembers();
h.stream(members)
 .filter(m => m.name.startsWith('A'))
 .sorted((a, b) => a.name.compareToIgnoreCase(b.name))
 .forEach(m => h.log(m));

//Anonymous Function
var members = h.getMembers();
h.stream(members)
 .filter(function(m) {
   return m.name.startsWith('A'));
 })
 .sorted(function(a, b) {
   return a.name.compareToIgnoreCase(b.name);
 })
 .forEach(function(m) {
   h.log(m);
 });
```

### Stream, Optional, ...

Classes utilitárias

Por exemplo:
```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var sortedArr = h.stream(arr)
  .filter(o => o !== 'x')
  .sorted()
  .toArray();
h.log(sortedArr);
// output
// ['a', 'b', 'c', 'y', 'z']


var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
h.stream(arr)
 .max((a, b) => a.compareToIgnoreCase(b))
 .ifPresent(o => {
   h.log(o);
   // output
   // z
 });
```

### Teclas de atalho na janela de edição de código

| Tecla de Atalho | Descrição |
| ----: | ------------ |
| `Ctrl + Space` | Exibe um submenu na janela de edição com sugestões de código baseado na localização atual do cursor |
| `Ctrl + Shift + Up` | Duplicar linha(s) para cima |
| `Ctrl + Shift + Down` | Duplicar linha(s) para baixo |
| `Ctrl + F` | Localizar |
| `Ctrl + H` | Substituir |
| `Alt + Up` | Navegar para a ocorrência anterior |
| `Alt + Down` | Navegar para a próxima ocorrência |

`Tab`<br>
Modelos de código podem ser criados para inserção automática na janela de edição de código após pressionar a tecla `Tab`.<br>
Por exemplo, pressionar `Tab` após a palavra `for`, o seguinte modelo de código será inserido no local.
```javascript
for (var i = 0; i < /* cursor */; i++) {
    
}
```

Botão direito do mouse na janela de edição de código (menu de contexto), opção **Expandir com TAB**


---

# Métodos disponíveis na biblioteca jslib

- [Métodos](#métodos)
  - [log](#logobj)
  - [log](#logkey--null-obj-args--null)
  - [logf](#logfobj-args--null)
  - [logfp](#logfpobj-args--null)
  - [logp](#logpobj)
  - [log](#logkey--null-obj-args--null)
  - [log.setEnabled](#logsetenabledkey-enabled)
  - [log.enable](#logenablekey)
  - [log.enableAll](#logenableall)
  - [log.isEnabled](#logisenabledkey)
  - [log.setShowLogKey](#logsetshowlogkeyvalue)
  - [log.isShowLogKey](#logisshowlogkey)
  - [log.toggleEnabled](#logtoggleenabledkey)
  - [sleep](#sleeptime)
  - [base64Encode](#base64encodebytes)
  - [base64Decode](#base64decodestr)
  - [base64DecodeAsString](#base64decodeasstringstr-charset--utf8)
  - [uuid](#uuid)
  - [hash](#hashhashname-data)
  - [hashBytes](#hashbyteshashname-data)
  - [checksum](#checksumhashname-data)
  - [md5](#md5value)
  - [md5Str](#md5strvalue)
  - [sha256](#sha256value)
  - [sha256Str](#sha256strvalue)
  - [sha512](#sha512value)
  - [sha512Str](#sha512strvalue)
  - [security](#securitysecuritykey)
  - [toJson](#tojsonobj)
  - [toPrettyJson](#toprettyjsonobj)
  - [getClipboard](#getclipboard)
  - [normalize](#normalizestr)
  - [store](#storekey-value)
  - [restore](#restorekey-default--null)
  - [setGlobal](#setglobalkey-value-ttl--0)
  - [getGlobal](#getglobalkey-default--null)
  - [setGlobalNext](#setglobalnextkey-values-ttl--0)
  - [getGlobalAndSet](#getglobalandsetkey-default--null-newvalue)
  - [getGlobalAndSetNext](#getglobalandsetnextkey-values)
  - [setGlobalNextAndGet](#setglobalnextandgetkey-values)
  - [random](#randommin-max-keysaferepeat--null)
  - [random](#randomx-y-z)
  - [startTimer](#starttimerkey--default)
  - [getTimer](#gettimerkey--default)
  - [getTimerMillis](#gettimermilliskey)
  - [getTimerSeconds](#gettimersecondskey)
  - [startCountdown](#startcountdownkey--default-seconds)
  - [getCountdown](#getcountdownkey--default)
  - [getCountdownMillis](#getcountdownmilliskey)
  - [getCountdownSeconds](#getcountdownsecondskey)
  - [getPlaylistInfo](#getplaylistinfo)
  - [getPlayer](#getplayer)
  - [getAutomaticPresentationPlayer](#getautomaticpresentationplayer)
  - [scriptAction](#scriptactionid-input--null)
  - [apiAction](#apiactionid-input--null)
  - [apiRequest](#apirequestid-raw)
  - [getApiRequestLastError](#getapirequestlasterror)
  - [apiRequestAsync](#apirequestasyncid-raw-callback--null)
  - [apiRequestEx](#apirequestexid-raw)
  - [setTimeout](#settimeoutfunction-timeout-name--null)
  - [clearTimeout](#cleartimeoutid)
  - [setInterval](#setintervalfunction-timeout-name--null)
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
  - [getCommunityVersion](#getcommunityversion)
  - [isMinimumCommunityVersion](#isminimumcommunityversionversion)
  - [format.secondsToHMS](#formatsecondstohmsseconds-separator--)
  - [format.secondsToMS](#formatsecondstomsseconds-separator--)
  - [format.minutesToHM](#formatminutestohmminutes-separator--)
  - [format.f](#formatfformat-params)
  - [format.rgbToHex](#formatrgbtohexred-green-blue)
  - [date.getSecondOfDay](#dategetsecondofday)
  - [date.getSecondOfDay](#dategetsecondofdayhour-minute-second)
  - [csvToArray](#csvtoarraycsv)
  - [xmlToJson](#xmltojsonxml)
  - [addTriggerListener](#addtriggerlistenerinput)
  - [removeTriggerListener](#removetriggerlistenerid)
  - [containsTriggerListener](#containstriggerlistenerid)
  - [getTriggerListeners](#gettriggerlisteners)
  - [addSysVar](#addsysvarname-function)
  - [removeSysVar](#removesysvarname)
  - [getSysVar](#getsysvarvalue)
  - [applySysVar](#applysysvarvalue)
  - [readAudio](#readaudiofile)
  - [readAudioAsBase64](#readaudioasbase64file)
  - [readFileAsText](#readfileastextfile-charset--utf8)
  - [isPathEquals](#ispathequalsa-b)
  - [bytesToString](#bytestostringbytes-charset--utf-8)
  - [stringToBytes](#stringtobytesstring-charset--utf-8)
  - [trim](#trimvalue-trim)
  - [strReplace](#strreplacesearch-replace-subject)
  - [strRemoveTags](#strremovetagsvalue)
  - [htmlExtractText](#htmlextracttexthtml-keeplinebreak--false)
  - [exportTXT](#exporttxttext-settings--null)
  - [exportXLSX](#exportxlsxdata)
  - [createByteBuffer](#createbytebuffer)
  - [createByteBufferToRead](#createbytebuffertoreadreader)
  - [stream](#streamobj)
  - [intStreamOf](#intstreamofobj)
  - [intStreamRange](#intstreamrangestartinclusive-endexclusive)
  - [intStreamRangeClosed](#intstreamrangeclosedstartinclusive-endinclusive)
  - [chat.sendMessage](#chatsendmessagemessage)
  - [identifyVerseReferences](#identifyversereferencesvalue-languageid--null)
  - [getAvailableBibleBooks](#getavailablebiblebooks)
  - [getBibleBooks](#getbiblebookslanguageid)
  - [getReceiverInfo](#getreceiverinfoid)
  - [registerSettings](#registersettingskey-fromstore-inputs)
  - [ws](#wsreceiver-cacheid-modeltocreate)
  - [tcp](#tcpreceiver-cacheid-modeltocreate)
- [Métodos HLY](#métodos-hly)
  - [GetLyrics](#hlygetlyrics-input)
  - [GetSongs](#hlygetsongs)
  - [SearchLyrics](#hlysearchlyrics-input)
  - [ShowLyrics](#hlyshowlyrics-input)
  - [GetText](#hlygettext-input)
  - [GetTexts](#hlygettexts)
  - [SearchText](#hlysearchtext-input)
  - [ShowText](#hlyshowtext-input)
  - [ShowVerse](#hlyshowverse-input)
  - [GetAudios - GetVideos - GetImages](#hlygetaudios-input)
  - [PlayAudio](#hlyplayaudio-input)
  - [PlayVideo](#hlyplayvideo-input)
  - [ShowImage](#hlyshowimage-input)
  - [ExecuteFile](#hlyexecutefile-input)
  - [AudioExists - VideoExists - ImagesExists - FileExists](#hlyaudioexists-input)
  - [ShowAnnouncement](#hlyshowannouncement-input)
  - [GetCustomMessages](#hlygetcustommessages)
  - [ShowCustomMessage](#hlyshowcustommessage-input)
  - [ShowQuickPresentation](#hlyshowquickpresentation-input)
  - [ShowCountdown](#hlyshowcountdown-input)
  - [ShowQuiz](#hlyshowquiz-input)
  - [QuizAction](#hlyquizaction-input)
  - [GetAutomaticPresentations](#hlygetautomaticpresentations)
  - [GetAutomaticPresentation](#hlygetautomaticpresentation-input)
  - [PlayAutomaticPresentation](#hlyplayautomaticpresentation-input)
  - [GetAutomaticPresentationPlayerInfo](#hlygetautomaticpresentationplayerinfo)
  - [AutomaticPresentationPlayerAction](#hlyautomaticpresentationplayeraction-input)
  - [GetMediaPlayerInfo](#hlygetmediaplayerinfo)
  - [MediaPlayerAction](#hlymediaplayeraction-input)
  - [GetLyricsPlaylist](#hlygetlyricsplaylist)
  - [AddLyricsToPlaylist](#hlyaddlyricstoplaylist-input)
  - [RemoveFromLyricsPlaylist](#hlyremovefromlyricsplaylist-input)
  - [SetLyricsPlaylistItem](#hlysetlyricsplaylistitem-input)
  - [GetMediaPlaylist](#hlygetmediaplaylist)
  - [SetMediaPlaylistItem](#hlysetmediaplaylistitem-input)
  - [MediaPlaylistAction](#hlymediaplaylistaction-input)
  - [GetNextSongPlaylist](#hlygetnextsongplaylist)
  - [GetNextMediaPlaylist](#hlygetnextmediaplaylist)
  - [ShowNextSongPlaylist](#hlyshownextsongplaylist)
  - [ShowNextMediaPlaylist](#hlyshownextmediaplaylist)
  - [GetPreviousSongPlaylist](#hlygetprevioussongplaylist)
  - [GetPreviousMediaPlaylist](#hlygetpreviousmediaplaylist)
  - [ShowPreviousSongPlaylist](#hlyshowprevioussongplaylist)
  - [ShowPreviousMediaPlaylist](#hlyshowpreviousmediaplaylist)
  - [AddToPlaylist](#hlyaddtoplaylist-input)
  - [RemoveFromMediaPlaylist](#hlyremovefrommediaplaylist-input)
  - [SetPlaylistItemDuration](#hlysetplaylistitemduration-input)
  - [GetSlideDescriptions](#hlygetslidedescriptions)
  - [GetFavorites](#hlygetfavorites)
  - [FavoriteAction](#hlyfavoriteaction-input)
  - [GetApis](#hlygetapis)
  - [GetScripts](#hlygetscripts)
  - [ApiAction](#hlyapiaction-input)
  - [ScriptAction](#hlyscriptaction-input)
  - [ApiRequest](#hlyapirequest-input)
  - [GetCurrentPresentation](#hlygetcurrentpresentation-input)
  - [CloseCurrentPresentation](#hlyclosecurrentpresentation)
  - [GetF8 - F9 - F10](#hlygetf8)
  - [SetF8 - F9 - F10](#hlysetf8-input)
  - [ToggleF8 - F9 - F10](#hlytogglef8)
  - [ActionNext](#hlyactionnext)
  - [ActionPrevious](#hlyactionprevious)
  - [ActionGoToIndex](#hlyactiongotoindex-input)
  - [ActionGoToSlideDescription](#hlyactiongotoslidedescription-input)
  - [GetCurrentBackground](#hlygetcurrentbackground)
  - [GetCurrentTheme](#hlygetcurrenttheme)
  - [GetBackgrounds](#hlygetbackgrounds-input)
  - [SetCurrentBackground](#hlysetcurrentbackground-input)
  - [GetThumbnail](#hlygetthumbnail-input)
  - [GetColorMap](#hlygetcolormap-input)
  - [GetAlert](#hlygetalert)
  - [SetAlert](#hlysetalert-input)
  - [GetCurrentSchedule](#hlygetcurrentschedule)
  - [GetSchedules](#hlygetschedules-input)
  - [GetSavedPlaylists](#hlygetsavedplaylists)
  - [LoadSavedPlaylist](#hlyloadsavedplaylist-input)
  - [GetHistory](#hlygethistory-input)
  - [GetHistories](#hlygethistories)
  - [GetTeams](#hlygetteams)
  - [GetMembers](#hlygetmembers)
  - [GetRoles](#hlygetroles)
  - [GetServices](#hlygetservices)
  - [GetEvents](#hlygetevents-input)
  - [GetAnnouncement](#hlygetannouncement-input)
  - [GetAnnouncements](#hlygetannouncements)
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
  - [GetTransitionEffectSettings](#hlygettransitioneffectsettings)
  - [SetTransitionEffectSettings](#hlysettransitioneffectsettings-input)
  - [GetBibleVersions](#hlygetbibleversions)
  - [GetBibleVersionsV2](#hlygetbibleversionsv2)
  - [GetBibleSettings](#hlygetbiblesettings)
  - [SetBibleSettings](#hlysetbiblesettings-input)
  - [GetPresentationFooterSettings](#hlygetpresentationfootersettings)
  - [SetPresentationFooterSettings](#hlysetpresentationfootersettings-input)
  - [GetBpm](#hlygetbpm)
  - [SetBpm](#hlysetbpm-input)
  - [GetHue](#hlygethue)
  - [SetHue](#hlysethue-input)
  - [GetRuntimeEnvironment](#hlygetruntimeenvironment)
  - [SetRuntimeEnvironment](#hlysetruntimeenvironment-input)
  - [SetLogo](#hlysetlogo-input)
  - [GetSyncStatus](#hlygetsyncstatus)
  - [GetInterfaceInput](#hlygetinterfaceinput-input)
  - [SetInterfaceInput](#hlysetinterfaceinput-input)
  - [SelectVerse](#hlyselectverse-input)
  - [OpenDrawLots](#hlyopendrawlots-input)
  - [GetMediaDuration](#hlygetmediaduration-input)
  - [GetVersion](#hlygetversion)
- [Métodos SecurityUtils](#métodos-securityutils)
  - [encrypt](#encryptvalue)
  - [decrypt](#decryptbase64)
  - [encryptObj](#encryptobjvalue)
  - [decryptObj](#decryptobjbase64)
  - [relativeMethods](#relativemethods)
- [Métodos User Input](#métodos-user-input)
  - [input](#inputparam-notification--false)
  - [settings](#settingssaveto-savetostore-data)
  - [inputTextArea](#inputtextareatitle-notification--false)
  - [itemChooser](#itemchoosertitle-items-notification--false)
  - [multipleItemChooser](#multipleitemchoosertitle-items-notification--false)
  - [confirm](#confirmmsg-title--confirm-notification--false)
  - [yesNo](#yesnomsg-title--confirm-notification--false)
  - [notification](#notificationmsg-duration--0)
  - [lyricsChooser](#lyricschooser)
  - [textChooser](#textchooser)
  - [themeChooser](#themechooser)
  - [imageChooser](#imagechooser)
  - [audioChooser](#audiochooser)
  - [videoChooser](#videochooser)
  - [backgroundChooser](#backgroundchooser)
  - [openWindow](#openwindowname)
  - [repaint](#repaintid)
- [Classes](#classes)
  - [Lyrics](#lyrics)
  - [Text](#text)
  - [Theme](#theme)
  - [Background](#background)
  - [Slide Description](#slide-description)
  - [Item](#item)
  - [Group](#group)
  - [Announcement](#announcement)
  - [Midi](#midi)
  - [Favorite Item](#favorite-item)
  - [Service](#service)
  - [Event](#event)
  - [Schedule](#schedule)
  - [Team](#team)
  - [Member](#member)
  - [Role](#role)
  - [Automatic Presentation](#automatic-presentation)
  - [Automatic](#automatic)
  - [Presentation Slide Info](#presentation-slide-info)
  - [Input Param](#input-param)
  - [Trigger Item](#trigger-item)
  - [Play Media Settings](#play-media-settings)
  - [Display Settings](#display-settings)
  - [Transition Effect Settings](#transition-effect-settings)
  - [Bible Settings](#bible-settings)
  - [Font Settings](#font-settings)
  - [Stage View](#stage-view)
  - [Slide Additional Info](#slide-additional-info)
  - [Rectangle](#rectangle)
  - [Custom Message](#custom-message)
  - [Custom Message Param](#custom-message-param)
  - [Quiz Question](#quiz-question)
  - [Quiz Settings](#quiz-settings)
  - [Quick Presentation Slide](#quick-presentation-slide)
  - [Theme Filter](#theme-filter)
  - [Translations](#translations)
  - [Wallpaper Settings](#wallpaper-settings)
  - [Clock Settings](#clock-settings)
  - [Bible Book List](#bible-book-list)
  - [Bible Book Info](#bible-book-info)
  - [Verse Reference Group](#verse-reference-group)
  - [Verse Reference](#verse-reference)
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
  - [AddItemAddItemScript](#additemadditemscript)
  - [AddItemAddItemAPI](#additemadditemapi)
  - [AddItemURI](#additemuri)
  - [AddItemGlobalAction](#additemglobalaction)


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
| `args` | _Array&lt;Object&gt; (opcional)_ | Parâmetros para formatação de uma mensagem de log |


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


### logf(obj, args = null)
- v2.23.0

O mesmo que `h.log(key, obj, ...args)`, porém sem precisar informar key

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `obj` | _Object_ | Qualquer objeto para ser exibido na janela de log |
| `args` | _Array&lt;Object&gt; (opcional)_ | Parâmetros para formatação de uma mensagem de log |


_Método sem retorno_

**Exemplo:**

```javascript
h.logf('mensagem de log');

h.logf('mensagem de log {} abc {}', 'value 1', 'value 2');
```

---


### logfp(obj, args = null)
### logpf(obj, args = null)
- v2.23.0

O mesmo que `h.logf(key, obj, ...args)`, porém os objetos complexos serão exibidos em formato 'pretty-print'

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `obj` | _Object_ | Qualquer objeto para ser exibido na janela de log |
| `args` | _Array&lt;Object&gt; (opcional)_ | Parâmetros para formatação de uma mensagem de log |


_Método sem retorno_

**Exemplo:**

```javascript
var example = {
    key1: 'value1',
    key2: 'value2'
};
h.logfp("Item:\n{}", example);
/* OUTPUT
Item:
{
  "key1": "value1",
  "key2": "value2"
}
*/
```

---


### logp(obj)
- v2.23.0

O mesmo que `h.log(obj)`, porém os objetos complexos serão exibidos em formato 'pretty-print'

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `obj` | _Object_ | Qualquer objeto para ser exibido na janela de log |


_Método sem retorno_

**Exemplo:**

```javascript
var example = {
    key1: 'value1',
    key2: 'value2'
};
h.logp(example);
/* OUTPUT
{
  "key1": "value1",
  "key2": "value2"
}
*/
```

---


### log(key = null, obj, args = null)
- v2.23.0

Exibe a informação passada como parâmetro numa janela de log (canto inferior direito da tela, geralmente)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id de gerenciamento do log |
| `obj` | _Object_ | Qualquer objeto para ser exibido na janela de log |
| `args` | _Array&lt;Object&gt; (opcional)_ | Parâmetros para formatação de uma mensagem de log |


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


### log.setEnabled(key, enabled)
- v2.23.0

Ativar/desativar a visualização de logs da chave/id passada por parâmetro. Todas as chaves/ids iniciam desativadas por padrão

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id de gerenciamento do log |
| `enabled` | _Boolean_ |  |


_Método sem retorno_

**Exemplo:**

```javascript
h.log.setEnabled('xyz', true);
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


### log.toggleEnabled(key)
### log.toggle(key)
- v2.23.0

Alterna o valor atual

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id de gerenciamento do log |


_Método sem retorno_

**Exemplo:**

```javascript
h.log.toggleEnabled('xyz');
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


### base64DecodeAsString(str, charset = 'utf8')
- v2.21.0

Decodifica uma string em formato base64

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `str` | _String_ | String em base64 |
| `charset` | _String (opcional)_ | Charset para conversão dos bytes decodificados |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | String decodificada |


---


### uuid()
- v2.23.0

UUID



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | UUID |


**Exemplo:**

```javascript
var uuid = h.uuid();
```

---


### hash(hashName, data)
- v2.21.0

Retorna o hash do parâmetro informado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `hashName` | _String_ | Pode ser: `MD5` `SHA-1` `SHA-256` `SHA-384` `SHA-512` |
| `data` | _Object_ | Valor que será calculado. Pode ser string ou array de bytes |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | hash |


**Exemplo:**

```javascript
var hash = h.hash('SHA-512', "Exemplo");
```

---


### hashBytes(hashName, data)
- v2.21.0

Retorna o hash do parâmetro informado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `hashName` | _String_ | Pode ser: `MD5` `SHA-1` `SHA-256` `SHA-384` `SHA-512` |
| `data` | _Object_ | Valor que será calculado. Pode ser string ou array de bytes |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;byte&gt;_ | hash |


**Exemplo:**

```javascript
var bytes = h.hashBytes('SHA-512', "Exemplo");
```

---


### checksum(hashName, data)
- v2.21.0

Retorna o **checksum** do parâmetro informado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `hashName` | _String_ | Pode ser: `ADLER-32` `CRC32` |
| `data` | _Object_ | Valor que será calculado. Pode ser string ou array de bytes |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | checksum |


**Exemplo:**

```javascript
var crc32 = h.checksum('CRC32', "Exemplo");
```

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


### security(securityKey)
### sec(securityKey)
- v2.23.0

Classe para executar ações de criptografia e armazenamento de dados protegidos com senha

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `securityKey` | _String_ | Chave de segurança |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[SecurityUtils](#métodos-securityutils)_ | Objeto da classe SecurityUtils |


**Exemplo:**

```javascript
var sec = h.security('key');
var b64 = sec.enc('Test');
// b64: rNFZfSWo/J+ggo11cxPNxg==
var val = sec.dec(b64);
// val: Test
```

---


### toJson(obj)
- v2.23.0

Converter um objeto em json

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `obj` | _Object_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ |  |


**Exemplo:**

```javascript
var example = {
    key1: 'value1',
    key2: 'value2'
};
var r = h.toJson(example);
//{"key1": "value1","key2": "value2"}
```

---


### toPrettyJson(obj)
### toJsonPretty(obj)
- v2.23.0

Converter um objeto em json no formato 'pretty-print'

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `obj` | _Object_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ |  |


**Exemplo:**

```javascript
var example = {
    key1: 'value1',
    key2: 'value2'
};
var r = h.toPrettyJson(example);
/*
{
    "key1": "value1",
    "key2": "value2"
}
*/
```

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

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `str` | _String_ |  |


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
Salva um objeto em disco que pode ser recuperado mesmo após reiniciar o programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id para salvar o objeto |
| `value` | _Object_ | Objeto que será salvo. Versões anteriores a `2.23.0` são compatíveis apenas com objeto do tipo `string` |


_Método sem retorno_

**Exemplo:**

```javascript
h.store('abc', 'Exemplo');
```

---


### restore(key, default = null)
Recupera o objeto salvo em disco

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id do objeto salvo anteriormente |
| `default` | _Object (opcional)_ | Valor padrão retornado se não for encontrado objeto salvo anteriormente `v2.23.0+` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna o objeto salvo ou **default** se não for encontrado. Versões anteriores a `2.23.0` são compatíveis apenas com objeto do tipo `string` |


**Exemplo:**

```javascript
var r = h.restore('abc');
if (r == null) {
    h.log('Item abc não encontrado');
} else {
    h.log('Item abc: ' + r);
}


var r = h.restore('xyz', {});
h.logfp('Item xyz: {}', r);
```

---


### setGlobal(key, value, ttl = 0)
Salva um objeto na memória que pode ser recuperado, mas é válido somente enquanto o programa estiver aberto. O método é compartilhado com todos os scripts do programa.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id do objeto salvo |
| `value` | _Object_ | Objeto que será salvo na memória |
| `ttl` | _Number (opcional)_ | Duração em segundos para o acesso à variável expirar `v2.21.0+` |


_Método sem retorno_

**Exemplo:**

```javascript
h.setGlobal('xyz', 'Exemplo');

//expires in 1 hour
h.setGlobal('xyz', 'Exemplo', 3600);
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


### setGlobalNext(key, values, ttl = 0)
- v2.21.0

É o mesmo que `setGlobal`, porém o parâmetro `values` é uma lista de itens, e o valor que será salvo em `setGlobal` é o próximo item da lista (baseado no item atual) ou o primeiro item da lista (se o item atual for null, ou for o último item da lista, ou não existir na lista).

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id do objeto salvo |
| `values` | _Object_ | Objeto, array, map ou lista com os possíveis valores |
| `ttl` | _Number_ | Duração em segundos para o acesso à variável expirar |


_Método sem retorno_

**Exemplo:**

```javascript
//h.getGlobal('xyz') == null
h.setGlobalNext('xyz', ['a', 'b', 'c']);
//h.getGlobal('xyz') == 'a'

h.setGlobalNext('xyz', ['a', 'b', 'c']);
//h.getGlobal('xyz') == 'b'

h.setGlobalNext('xyz', ['a', 'b', 'c']);
//h.getGlobal('xyz') == 'c'

h.setGlobalNext('xyz', ['a', 'b', 'c']);
//h.getGlobal('xyz') == 'a'
```

---


### getGlobalAndSet(key, default = null, newValue)
### getGlobalAndSet(key, newValue)
- v2.21.0

É o mesmo que `getGlobal` seguido de `setGlobal`.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id do objeto |
| `default` | _Object (opcional)_ | Valor padrão se não for encontrado valor salvo anteriormente |
| `newValue` | _Object_ | Objeto que será salvo na memória |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna o objeto salvo ou **default** se não for encontrado |


**Exemplo:**

```javascript
var r = h.getGlobalAndSet('xyz', "Novo valor");
```

---


### getGlobalAndSetNext(key, values)
- v2.21.0

É o mesmo que `getGlobal` seguido de `setGlobalNext`.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id do objeto salvo |
| `values` | _Object_ | Objeto, array, map ou lista com os possíveis valores |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna o objeto salvo ou **default** se não for encontrado |


**Exemplo:**

```javascript
//h.getGlobal('xyz') == null
var r = h.getGlobalAndSetNext('xyz', ['a', 'b', 'c']);
//r == null
//h.getGlobal('xyz') == 'a'

r = h.getGlobalAndSetNext('xyz', ['a', 'b', 'c']);
//r == 'a'
//h.getGlobal('xyz') == 'b'
```

---


### setGlobalNextAndGet(key, values)
- v2.21.0

É o mesmo que `setGlobalNext` seguido de `getGlobal`

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | chave/id do objeto salvo |
| `values` | _Object_ | Objeto, array, map ou lista com os possíveis valores |


_Método sem retorno_

**Exemplo:**

```javascript
//h.getGlobal('xyz') == null
var r = h.setGlobalNextAndGet('xyz', ['a', 'b', 'c']);
//r == 'a'
//h.getGlobal('xyz') == 'a'

r = h.setGlobalNextAndGet('xyz', ['a', 'b', 'c']);
//r == 'b'
//h.getGlobal('xyz') == 'b'
```

---


### random(min, max, keySafeRepeat = null)
Gera um número aleatório

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `min` | _Number_ | valor mínimo |
| `max` | _Number_ | Valor máximo |
| `keySafeRepeat` | _String (opcional)_ | Pode ser utilizado para evitar número repetido sorteado em sequência |


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


### random(x, y, z)
- v2.21.0

Obter um valor aleatório baseado nos valores de entrada

Combinações possíveis:
(x = number)
Retorna um valor aleatório de 0 a x

(x = number, y = number)
Retorna um valor aleatório de x a y

(x = string)
Retorna um caractere aleatório da string x

(x = array)
Retorna um objeto aleatório do array x

(x = object)
Retorna um campo aleatório do objeto x

É possível adicionar um parâmetro adicional do tipo `string` como argumento nas chamadas acima para ser utilizado como 'keySafeRepeat' (para evitar um valor repetido ser sorteado em sequência)
Exemplo: (x = number, y = number, x = string)


**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `x` | _Object_ |  |
| `y` | _Object (opcional)_ |  |
| `z` | _Object (opcional)_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ |  |


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

var r = h.random(10);
h.log('Número aleatório de 0 a 10: ' + r);

var r = h.random("abcd");
h.log('Caractere aleatório da string abcd: ' + r);

var r = h.random([20, 25, 30]);

var r = h.random([20, 25, 30], 'xyz');
var r = h.random([20, 25, 30], 'xyz');
//Não repete o valor sorteado anteriormente

var r = h.random(['z', 123, false]);
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


### getTimerMillis(key)
- v2.21.0

Recupera quanto tempo foi decorrido (em milésimos de segundo) em um timer de acordo com o valor **key**. Se o timer não tiver sido iniciado, o método iniciará o timer e retornará 0

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id do timer |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Tempo decorrido em milésimos de segundo |


---


### getTimerSeconds(key)
- v2.21.0

Recupera quanto tempo foi decorrido (em segundos) em um timer de acordo com o valor **key**. Se o timer não tiver sido iniciado, o método iniciará o timer e retornará 0

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id do timer |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Tempo decorrido em segundos |


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


### getCountdownMillis(key)
- v2.21.0

Recupera quanto tempo resta em uma contagem regressiva de acordo com o valor **key**.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id da contagem regressiva |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Tempo restante em milissegundos (retorna valores negativos após limite de tempo) |


---


### getCountdownSeconds(key)
- v2.21.0

Recupera quanto tempo resta em uma contagem regressiva de acordo com o valor **key**.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave/id da contagem regressiva |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ | Tempo restante em segundos (retorna valores negativos após limite de tempo) |


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
| _[Player](https://github.com/holyrics/jslib/blob/main/doc/pt/Player.md)_ |  |


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


### getAutomaticPresentationPlayer()
### getAPPlayer()
- v2.23.0

Classe que representa o player da apresentação automática do programa



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[AutomaticPresentationPlayer](https://github.com/holyrics/jslib/blob/main/doc/pt/AutomaticPresentationPlayer.md)_ |  |


**Exemplo:**

```javascript
var r = h.getAPPlayer();
if (r.isPlaying()) {
    h.logf('Total time: {} - Slide time: {}', r.getTime(), r.getSlide().getTime());
}
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
Executa uma requisição para o receptor associado e retorna a resposta do receptor.<br>
A partir da `v2.23.0` é possível passar o host ou ip diretamente, porém é necessário adicionar o host/ip na lista de requisições permitidas.<br>
menu arquivo > configurações > avançado > javascript > configurações > requisições permitidas

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
var r = h.apiRequest('receiver_id', {
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

//Exemplo ao adicionar um host/ip na lista de requisições permitidas
var r = h.apiRequest('https://example.com/api.php', {
    headers: {
      'Content-Type': 'application/json',
      Authorization: 'Bearer token'
    },
    data: { /*json*/ }
});

var r = h.apiRequest('http://192.168.0.123', {
    data: "raw"
});

//-------------------------------------------------

//Parâmetros disponíveis para requisição
var r = h.apiRequest('receiver_id', {
    //parâmetro adicionado ao final da url definida no receptor
    url_suffix: 'test.php?x=1&y=2&z=3', /* opcional */
    
    //cabeçalho da requisição
    headers: { /* opcional */
        Authorization: '1234'
    },
    
    //corpo da requisição (exceto para tipo GET)
    //pode ser byte array para UDP e TCP
    //data: h.createByteBuffer().putString('example').toBytes(),
    data: "example",
    
    //codificação da resposta da requisição, utf-8 por padrão
    //response_data_type: "string;iso-8859-1",
    //response_data_type: "base64",
    response_data_type: "string;utf-8", /* opcional */
    
    //Disponível para: UDP
    wait_for_response: true, /* opcional */
    
    //Disponível para: UDP
    port: 1234, /* opcional */
    
    //timeout ms - default: 5000 - UDP: 2000
    timeout: 5000 /* opcional */
});
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


### apiRequestEx(id, raw)
- v2.21.0

O mesmo que}} `apiRequest(id, raw)`, porém lança uma exception ao ocorrer um erro, em vez de retornar **null**

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | id do receptor |
| `raw` | _Object_ | dados da requisição |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorno da requisição |


---


### setTimeout(function, timeout, name = null)
- v2.19.0

Executa uma função após alguns milissegundos.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `function` | _Function_ | Função que será executada |
| `timeout` | _Number_ | Tempo em milissegundos para aguardar até a execução |
| `name` | _String (opcional)_ | Nome do item. Valor compatível para exibição no **JavaScript Monitor** `v2.23.0+` |


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


### setInterval(function, timeout, name = null)
- v2.19.0

Executa uma função a cada X milissegundos. Utilize **clearInterval** para parar a execução.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `function` | _Function_ | Função que será executada |
| `timeout` | _Number_ | Intervalo em milissegundos entre cada execução |
| `name` | _String (opcional)_ | Nome do item. Valor compatível para exibição no **JavaScript Monitor** `v2.23.0+` |


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
| `version` | _String_ | Versão no formato: X.Y.Z |


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
| _String_ | Um dos seguintes valores: `DEFAULT` `DARK_SOFT` `DARK_MEDIUM` `DARK_STRONG` |


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


### getCommunityVersion()
- v2.23.0

Retorna a versão atual da biblioteca JSCommunity no programa.



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Versão no formato: X.Y.Z |


---


### isMinimumCommunityVersion(version)
### isMinCommunityVersion(version)
- v2.23.0

Verifica se a versão da biblioteca JSCommunity no programa é igual ou superior ao informado por parâmetro.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `version` | _String_ | Versão no formato: X.Y.Z |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


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
//05:05

var r = h.format.secondsToMS(305, ',');
h.log(r);
//output:
//05,05
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


### format.f(format, params)
- v2.21.0

Um alias para o formatador padrão em Java java.util.Formatter [Documentação](https://docs.oracle.com/javase/8/docs/api/java/util/Formatter.html)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `format` | _String_ |  |
| `params` | _Array&lt;Object&gt;_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Valor formatado |


**Exemplo:**

```javascript
var r = h.format.f("Exemplo: %s, %.2f", ['abc', 100.1234]);
//r == Exemplo: abc, 100,12
```

---


### format.rgbToHex(red, green, blue)
### format.rgbaToHex(red, green, blue, alpha)
- v2.23.0



**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `red` | _Number_ | `0 ~ 255` |
| `green` | _Number_ | `0 ~ 255` |
| `blue` | _Number_ | `0 ~ 255` |
| `alpha` | _Number_ | `0 ~ 255` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Cor no formato hexadecimal. `RRGGBB` or `RRGGBBAA`<br>Se `alpha = 255`, será retornado apenas `RRGGBB` |


**Exemplo:**

```javascript
var r = h.format.rgbToHex(50, 100, 150);
// r: 326496

var r = h.format.rgbaToHex(50, 100, 150, 200);
// r: 326496C8

var r = h.format.rgbaToHex(50, 100, 150, 255);
// r: 326496

var r = h.format.rgbaToHex(0, 0, 0, 0);
// r: 00000000

var r = h.format.rgbaToHex(255, 255, 255, 0);
// r: FFFFFF00
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


### date.getSecondOfDay(hour, minute, second)
- v2.20.0

Retorna a quantidade total de segundos do dia (hour * 3600 + minute * 60 + second)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `hour` | _Number_ |  |
| `minute` | _Number_ |  |
| `second` | _Number_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Number_ |  |


**Exemplo:**

```javascript
var r = h.date.getSecondOfDay(18, 30, 0);
```

---


### csvToArray(csv)
- v2.21.0

Converte um CSV (string) em um array bidimensional

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `csv` | _String_ | String no formato CSV |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;Object&gt;_ |  |


**Exemplo:**

```javascript
var csv = "1,2,3,4\n5,6,7,8\nab,c,d,e\nf,gh,i,j";
var r = h.csvToArray(csv);
//r == [
//  ['1', '2', '3', '4'],
//  ['5', '6', '7', '8'],
//  ['ab', 'c', 'd', 'e'],
//  ['f', 'gh', 'i', 'j']
//]
```

---


### xmlToJson(xml)
- v2.23.0

Converte uma string no formato xml em um objeto JavaScript. Pode gerar Exception.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `xml` | _String_ | String no formato XML |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ |  |


**Exemplo:**

```javascript
var xml = ''
    + '<?xml version="1.0" encoding="utf-8"?>'
    + '<song>'
    + '  <title>Example 1</title>'
    + '  <author>Example 2</author>'
    + '  <verses>'
    + '    <verse desc="Verse 1">Slide 1 Line 1<br/>Slide 1 Line 2</verse>'
    + '    <verse desc="Chorus">Slide 2 Line 1<br/>Slide 2 Line 2</verse>'
    + '    <verse desc="Verse 2">Slide 3 Line 1<br/>Slide 3 Line 2</verse>'
    + '  </verses>'
    + '</song>';
var r = h.xmlToJson(xml);
h.log(r);
/*
{
  "song": {
    "title": [{ "content": "Example 1" }],
    "author": [{ "content": "Example 2" }],
    "verses": [{
        "content": "    Slide 1 Line 1Slide 1 Line 2    Slide 2 Line 1Slide 2 Line 2    Slide 3 Line 1Slide 3 Line 2  ",
        "verse": [{
            "content": "Slide 1 Line 1\nSlide 1 Line 2",
            "desc": "Verse 1"
          }, {
            "content": "Slide 2 Line 1\nSlide 2 Line 2",
            "desc": "Chorus"
          }, {
            "content": "Slide 3 Line 1\nSlide 3 Line 2",
            "desc": "Verse 2"
          }]
      }]
  }
}
*/

r.song.title[0].content; //Example 1
r.song.title0; //Example 1

r.song.author[0].content; //Example 2
r.song.author0; //Example 2

r.song.verses[0].verse;
/*
[{
  "content":"Slide 1 Line 1\nSlide 1 Line 2","desc":"Verse 1"},
  {"content":"Slide 2 Line 1\nSlide 2 Line 2","desc":"Chorus"},
  {"content":"Slide 3 Line 1\nSlide 3 Line 2","desc":"Verse 2"
}]
*/

r.song.verses0.verse.forEach(v => h.log(v.content));
/*
Slide 1 Line 1
Slide 1 Line 2
Slide 2 Line 1
Slide 2 Line 2
Slide 3 Line 1
Slide 3 Line 2
*/
```

---


### addTriggerListener(input)
- v2.21.0

Registrar um gatilho para execução

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _[TriggerItem](#trigger-item)_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Retorna o ID do item registrado (gerado automaticamente se **input.id** for **null**) |


**Exemplo:**

```javascript
var r = h.addTriggerListener({
    when: 'displaying',
    item: 'any_song',
    action: function (obj) {
        if (obj.title == 'Exemplo') {
            //do action
        }
    }
});

var r = h.addTriggerListener({
    id: 'abc',
    when: 'closing',
    item: 'any_image',
    action: function (obj) {
        if (obj.file_relative_path == 'image.jpg') {
            //do action
            return;
        }
        if (h.isPathEquals(obj.file_relative_path, 'folder/image.jpg')) {
            //do action
            return;
        }
    }
});

h.addTriggerListener({
    id: 'log_bpm_changed',
    when: 'change',
    item: 'bpm',
    action: function (obj) {
        h.log("", "BPM changed, {} to {}", [obj.old_value, obj.new_value]);
    }
});
h.setTimeout(function () {
    h.removeTriggerListener('log_bpm_changed');
}, 60000);
```

---


### removeTriggerListener(id)
- v2.21.0

Remover um gatilho registrado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | Retorna **true** para removido. Retorna **false** para ID não foi encontrado |


**Exemplo:**

```javascript
var r = h.removeTriggerListener('xyz');
```

---


### containsTriggerListener(id)
- v2.21.0

Verifica se um gatilho com o ID específico já está registrado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


---


### getTriggerListeners()
- v2.21.0

Retorna a lista de gatilhos registrados



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;[TriggerItem](#trigger-item)&gt;_ |  |


**Exemplo:**

```javascript
var items = h.getTriggerListeners();
for (var i = 0; i < items.length; i++) {
    h.log("ID: " + items[i].id);
}
```

---


### addSysVar(name, function)
- v2.23.0

Adiciona uma variável do sistema que pode ser utilizada dentro dos textos exibidos pelo programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do item |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `function` | _Function_ | Function que será executada para obter o retorno e exibir o conteúdo no lugar da variável declarada na apresentação |


**Exemplo:**

```javascript
h.addSysVar('now', function() {
    return Date.now();
});
var r = h.getSysVar('@js{now}');
h.log(r);


h.addSysVar('sum', function(a, b) {
    return a + b;
});
var r = h.getSysVar('@js{sum(3, 4)}');
h.log(r); //7
```

---


### removeSysVar(name)
- v2.23.0

Remove uma variável do sistema adicionada por h.addSysVar(...)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do item |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


**Exemplo:**

```javascript
h.removeSysVar('sum');
```

---


### getSysVar(value)
- v2.23.0

Obter o valor atual de uma variável do sistema

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ | Variável do sistema na sintaxe real de uso. Exemplo: `@js{sys_var_name}` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ |  |


**Exemplo:**

```javascript
var r = h.getSysVar("@js{sum(3, 4)}");
// r: 7
```

---


### applySysVar(value)
- v2.23.0

Converter todas as variáveis do sistema no valor passado para o valor atual da respectiva variável

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ | Texto que será convertido |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ |  |


**Exemplo:**

```javascript
var r = h.applySysVar("3 + 4 = @js{sum(3, 4)}");
// r: 3 + 4 = 7
```

---


### readAudio(file)
### readVideo(file)
### readImage(file)
### readFile(file)
- v2.21.0

Ler um arquivo da biblioteca do programa (max=16mb)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `file` | _String_ | Nome do arquivo |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;byte&gt;_ | Array de bytes do arquivo |


**Exemplo:**

```javascript
var r = h.readImage('file.jpg');
```

---


### readAudioAsBase64(file)
### readImageAsBase64(file)
### readVideoAsBase64(file)
### readFileAsBase64(file)
- v2.21.0

Ler um arquivo da biblioteca do programa (max=16mb)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `file` | _String_ | Nome do arquivo |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Bytes do arquivo em formato base64 |


**Exemplo:**

```javascript
var r = h.readImageAsBase64('file.jpg');
```

---


### readFileAsText(file, charset = 'utf8')
- v2.21.0

Ler um arquivo da biblioteca do programa (max=16mb)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `file` | _String_ | Nome do arquivo |
| `charset` | _String (opcional)_ | Codificação do arquivo |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Conteúdo do arquivo em formato de texto |


**Exemplo:**

```javascript
var r = h.readFileAsText('file.txt');
```

---


### isPathEquals(a, b)
- v2.21.0

Verifica se os dois caminhos são iguais, ignorando distinção de maiúsculo para Windows e considerando '\' e '/' como iguais

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `a` | _String_ |  |
| `b` | _String (opcional)_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ |  |


**Exemplo:**

```javascript
//Windows = true, Unix|OSX = false
h.isPathEquals('file.jpg', 'File.jpg');

//true
h.isPathEquals('image/file.jpg', 'image\file.jpg');

//false
h.isPathEquals('file.jpg', 'file.jpeg');
```

---


### bytesToString(bytes, charset = 'UTF-8')
- v2.22.0

Converte um array de bytes em string

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `bytes` | _Array&lt;byte&gt;_ | Array de bytes |
| `charset` | _String (opcional)_ | Codificação utilizada `Padrão: UTF-8` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | String decodificada. O método gera um exception para charset inválido |


---


### stringToBytes(string, charset = 'UTF-8')
- v2.22.0

Converte uma string em array de bytes

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `string` | _String_ | Texto que será codificado |
| `charset` | _String (opcional)_ | Codificação utilizada `Padrão: UTF-8` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;byte&gt;_ | Array de bytes. O método gera um exception para charset inválido |


---


### trim(value, trim)
- v2.23.0

Remove caracteres do início e final de uma string

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ | Valor que será editado |
| `trim` | _String_ | lista de caracteres que deverão ser removidos do início e final do valor |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ |  |


**Exemplo:**

```javascript
var str = ' ?abc xyz .';
var r = h.trim(str, " .?");
h.log(r);
// output
// abc xyz
```

---


### strReplace(search, replace, subject)
- v2.23.0

Realiza um replace em todas as ocorrências da string em JavaScript. O método original em JavaScript faz replace apenas da primeira ocorrências.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `search` | _String_ | Valor que será pesquisado |
| `replace` | _String_ | Valor de substituição |
| `subject` | _String_ | String que será pesquisada e substituída |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ |  |


**Exemplo:**

```javascript
var r = h.strReplace("e", "?", "example test");
h.log(r);
// output
// ?xampl? t?st


var r = "example test".replace("e", "?");
h.log(r);
// output
// ?xample test
```

---


### strRemoveTags(value)
- v2.23.0

Remove todos os valores dentro de `<>` (inclusive)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ | Valor que será editado |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ |  |


**Exemplo:**

```javascript
var r = h.strRemoveTags("example <a> test</b>");
h.log(r);
// output
// example  test
```

---


### htmlExtractText(html, keepLineBreak = false)
- v2.23.0

Extrair o texto de um trecho formatado em HTML

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `html` | _String_ | Valor que será editado |
| `keepLineBreak` | _Boolean (opcional)_ | Se **true**, as quebras de linha `\n (char 10)` serão mantidas `Padrão: false` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ |  |


**Exemplo:**

```javascript
var html = "<b>Exemplo</b>\n"
        + "Exemplo - <span>Exemplo</span>\n"
        + "<div>Exemplo</div>";
var r = h.htmlExtractText(html);
/*
Exemplo Exemplo - Exemplo
Exemplo
*/

var r = h.htmlExtractText(html, true);
/*
Exemplo
Exemplo - Exemplo
Exemplo
*/
```

---


### exportTXT(text, settings = null)
- v2.22.0

Salvar um conteúdo em um arquivo TXT. Pode gerar Exception.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `text` | _String_ | Texto que será salvo |
| `settings` | _Object (opcional)_ | Configurações |
| `settings.name` | _String (opcional)_ | Nome do arquivo `Padrão: YYYY-MM-DD_HH-MM-SS` |
| `settings.charset` | _String (opcional)_ | Codificação do texto `Padrão: UTF-8` |


_Método sem retorno_

**Exemplo:**

```javascript
h.exportTXT("abc", {
    name: "txt filename"
});
```

---


### exportXLSX(data)
- v2.22.0

Salvar um conteúdo em uma planilha XLSX. Pode gerar Exception.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.name` | _String (opcional)_ | Nome do arquivo `Padrão: YYYY-MM-DD_HH-MM-SS` |
| `data.sheets` | _Array&lt;Object&gt;_ | Abas |
| `data.sheets.*.name` | _String_ | Nome da aba |
| `data.sheets.*.header` | _String_ | Cabeçalho |
| `data.sheets.*.cols_name` | _Array&lt;String&gt;_ | Título das colunas |
| `data.sheets.*.grid` | _Array&lt;Array&lt;String&gt;&gt;_ | Abas |


_Método sem retorno_

**Exemplo:**

```javascript
h.exportXLSX({
    name: "xlsx filename",
    sheets: [
      {
        name: "Name",
        header: "Example",
        cols_name: ["Col 1", "Col 2", "Col 3", "Col 4"],
        grid: [
          ['a', 'b', 'c', 'd'], //ROW 1
          ['e', 'f', 'g', 'h'], //ROW 2
          ['i', 'j', 'k', 'l'], //ROW 3
          ['m', 'n', 'o', 'p']  //ROW 4
         ]
      }
    ]
});
```

---


### createByteBuffer()
- v2.22.0

Cria um objeto para armazenar dados em forma binária.



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferReader](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferReader.md)_ |  |


**Exemplo:**

```javascript
var buf = h.createByteBuffer();
buf.putByte(48); //1 byte
buf.putInt(123); //4 bytes
buf.putLong(1234); //8 bytes
buf.putFloat(3.0); //4 bytes
buf.putDouble(4.0); //8 bytes
buf.putString("text"); //utf-8 default
buf.putString("text", "ISO-8859-1"); //text, charset

//add byte(48) 128 times
buf.fill(48, 128); //byte, times

var bytes = buf.toBytes();
var hex = buf.toHex();
var base64 = buf.toBase64();
var str1 = buf.toString(); //utf-8 default
var str2 = buf.toString("ISO-8859-1"); //charset
```

---


### createByteBufferToRead(reader)
- v2.22.0

Cria um objeto preenchido com bytes para leitura em forma binária.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `reader` | _Array&lt;byte&gt;_ | Array de bytes |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferWriter.md)_ |  |


**Exemplo:**

```javascript
var bytes = [
    48,
    0, 0, 0, 123,
    0, 0, 0, 0, 0, 0, 4, -46,
    64, 64, 0, 0, 
    64, 16, 0, 0, 0, 0, 0, 0,
    116, 101, 120, 116,
    116, 101, 120, 116
];
var buf = h.createByteBufferToRead(bytes);

var b = buf.readByte(); //1 byte
var i = buf.readInt(); //4 bytes
var l = buf.readLong(); //8 bytes
var f = buf.readFloat(); //4 bytes
var d = buf.readDouble(); //8 bytes
var s1 = buf.readString(4); //length, utf-8 default
var s2 = buf.readString(4, "ISO-8859-1"); //length, charset
var b2 = buf.readBytes(128); //length
```

---


### stream(obj)
- v2.23.0

Cria um `stream` para facilitar manipulações de uma lista

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `obj` | _Object_ | Array ou Object |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [Stream](https://github.com/holyrics/jslib/blob/main/doc/pt/Stream.md) |


**Exemplo:**

```javascript
var arr = ['x', 'y', 'z', 'a', 'b', 'c'];
var sortedArr = h.stream(arr)
  .filter(o => o !== 'x')
  .sorted()
  .toArray();
h.log(sortedArr);
// output
// ['a', 'b', 'c', 'y', 'z']
```

---


### intStreamOf(obj)
- v2.23.0

Cria um `stream` para facilitar manipulações de uma lista

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `obj` | _Array&lt;Number&gt;_ | Array de números |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [IntStream](https://github.com/holyrics/jslib/blob/main/doc/pt/IntStream.md) |


**Exemplo:**

```javascript
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
var r = h.intStreamOf(arr)
         //1, 3, 7, 9
         .filter(n => n != 5 && n % 2 == 1)
         .sum();
h.log(r);
// output
// 20
```

---


### intStreamRange(startInclusive, endExclusive)
- v2.23.0

Cria um `stream` para facilitar manipulações de uma lista

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `startInclusive` | _Number_ | Valor inicial (inclusivo) |
| `endExclusive` | _Number_ | Limite superior (exclusivo) |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [IntStream](https://github.com/holyrics/jslib/blob/main/doc/pt/IntStream.md) |


**Exemplo:**

```javascript
h.intStreamRange(0, 10); // 0...9
```

---


### intStreamRangeClosed(startInclusive, endInclusive)
- v2.23.0

Cria um `stream` para facilitar manipulações de uma lista

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `startInclusive` | _Number_ | Valor inicial (inclusivo) |
| `endExclusive` | _Number_ | Limite superior (inclusivo) |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | [IntStream](https://github.com/holyrics/jslib/blob/main/doc/pt/IntStream.md) |


**Exemplo:**

```javascript
h.intStreamRangeClosed(0, 10); // 0...10
```

---


### chat.sendMessage(message)
- v2.23.0

Enviar mensagem ao chat Holyrics.<br>
Para utilizar esta ação é necessário liberar a permissão nas configurações<br>menu arquivo > configurações > avançado > javascript > configurações > permissões avançadas

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `message` | _String_ | Mensagem de texto para envio ao chat Holyrics |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Boolean_ | Retorna **false** se a mensagem não for enviada. Por exemplo, se a permissão não estiver liberada. |


**Exemplo:**

```javascript
h.chat.sendMessage("Olá");
```

---


### identifyVerseReferences(value, languageID = null)
- v2.23.0

Identifica as possíveis referências bíblicas no texto informado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ | Texto para identificação |
| `languageID` | _String (opcional)_ | ID do idioma do conjunto de livros.<br>Caso um id não seja informado, será utilizada a lista de livros da Bíblia principal selecionada no programa.<br>Para obter a lista dos IDs disponíveis, veja: `h.getAvailableBibleBooks()` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;[VerseReferenceGroup](#verse-reference-group)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.identifyVerseReferences("... ... Rm 12:2  Gn 1:1-3  Sl 23 ... ...");
r.forEach(function(g) {
    g.verses.forEach(function(v) {
        h.log(v.id);
    });
});
// output
// 45012002
// 01001001
// 01001002
// 01001003
// 19023001
// 19023002
// 19023003
// 19023004
// 19023005
// 19023006
```

---


### getAvailableBibleBooks()
- v2.23.0

Retorna a lista do conjunto de livros disponíveis em diferentes idiomas



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;[BibleBookList](#bible-book-list)&gt;_ |  |


**Exemplo:**

```javascript
h.getAvailableBibleBooks().forEach(function(o) {
    h.logf('{}: {}', o.id, o.name);
});
// output
// pt: Português
// en: English
// ...
// ...
```

---


### getBibleBooks(languageID)
- v2.23.0

Retorna um conjunto de livros da Bíblia

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `languageID` | _String_ | ID do idioma do conjunto de livros |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Array&lt;[BibleBookInfo](#bible-book-info)&gt;_ |  |


**Exemplo:**

```javascript
h.getBibleBooks('en').forEach(function(b) {
    h.logf('{}: {} - {}', b.id, b.name, b.abbrev);
});
// output
// 1: Genesis - Gn
// 2: Exodus - Ex
// ...
// ...
// 66: Revelation - Rev
```

---


### getReceiverInfo(id)
- v2.23.0

Retorna a informação de um receptor ou **null** se não for encontrado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID ou nome do receptor |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `type` | _String_ | Tipo do item |
| `name` | _String_ | Nome do item |


**Exemplo:**

```javascript
var r = h.getReceiverInfo(id);
h.logf('{} {} {}', r.id, r.type, r.name);
```

---


### registerSettings(key, fromStore, inputs)
### registerSettings(key, inputs)
### loadSettings(key, fromStore, inputs)
### loadSettings(key, inputs)
- v2.23.0



**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `key` | _String_ | Chave de armazenamento utilizado para salvar e recuperar o valor dos itens.<br>`h.getGlobal(key, ...)`<br>`h.restore(key, ...)` |
| `fromStore` | _Boolean_ | **true** para recuperar o valor também em `h.restore(key, ...)` `Padrão: true` |
| `inputs` | _Array&lt;[InputParam](#input-param)&gt;_ | Objeto com os valores previamente armazenados, onde cada chave é o `id` do respectivo `input`.<br>O valor definido em `default_value` de cada item será retornado caso não exista valor previamente armazenado |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Objeto com os valores previamente armazenados, onde cada chave é o `id` do respectivo `input`.<br>O valor definido em `default_value` de cada item será retornado caso não exista valor previamente armazenado |


**Exemplo:**

```javascript
var inputs = [
  {
    id: 'message',
    type: 'string'
  }, {
    id: 'duration',
    type: 'number',
    default_value: 10
  }
];

var r = h.registerSettings('settings_name', inputs);
//r.message
//r.duration
```

---


### ws(receiver, cacheID, modelToCreate)
### ws(receiver, cacheIDOrModelToCreate)
### ws(receiver)
- v2.23.0

Cria uma conexão WebSocket. Pode gerar Exception.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `receiver` | _String_ | Valores aceitos<br>ID ou nome receptor<br>Host ou IP de destino, caso esteja adicionado na lista de requisições permitidas<br>`menu arquivo > configurações > avançado > javascript > configurações > requisições permitidas` |
| `cacheID` | _String (opcional)_ | ID utilizado como valor para obter a conexão já existente, em vez de criar uma nova conexão |
| `modelToCreate` | _Object (opcional)_ | Ações utilizadas ao criar uma nova conexão |
| `modelToCreate.headers` | _Object (opcional)_ |  |
| `modelToCreate.on_open` | _Function (opcional)_ | Executado ao iniciar a conexão<br>`function(evt) { /* evt.source; evt.http_status; evt.http_status_message; */ }` |
| `modelToCreate.on_message` | _Function_ | Executado a cada nova mensagem recebida<br>O objeto `message` é do tipo:  string<br>`function(message) { ... }` |
| `modelToCreate.on_error` | _Function (opcional)_ | Executado quando ocorrer um erro<br>`function(evt) { /* evt.source; evt.error; */ }` |
| `modelToCreate.on_close` | _Function (opcional)_ | Executado ao encerrar a conexão<br>`function(evt) { /* evt.source; evt.code; evt.reason; */ }` |
| `modelToCreate.loop` | _Function (opcional)_ | Executado a cada 1 segundo enquanto a conexão estiver aberta<br>Útil para conexões que precisam enviar um 'ping' para manter a conexão aberta<br>`function(evt) { /* evt.source; */ }` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[WebSocketClient](https://github.com/holyrics/jslib/blob/main/doc/pt/WebSocketClient.md)_ |  |


**Exemplo:**

```javascript
var client = createWebSocket('receiver_id');
client.send('message'); // utf-8
// client.send(h.toJson({message:'test'}));

function createWebSocket(receiver) {
  var client = h.ws(receiver);
  if (client != null) {
    return client;
  }
  return h.ws(receiver, {
    on_open: function (evt) {
      //evt.source;
      //evt.http_status;
      //evt.http_status_message;
    },
    on_message: function (msg) {
      h.log(msg);
    },
    on_error: function (evt) {
      h.logf('websocket error: {} - {}', receiver, evt.error);
    },
    on_close: function (evt) {
      //evt.source;
      //evt.core;
      //evt.reason;
    },
    loop: function (evt) {
      evt.source.send('ping');
    }
  });
}
```

---


### tcp(receiver, cacheID, modelToCreate)
### tcp(receiver, cacheIDOrModelToCreate)
### tcp(receiver)
- v2.23.0

Cria uma conexão TCP. Pode gerar Exception.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `receiver` | _String_ | Valores aceitos<br>ID ou nome receptor<br>Host ou IP de destino, caso esteja adicionado na lista de requisições permitidas<br>`menu arquivo > configurações > avançado > javascript > configurações > requisições permitidas` |
| `cacheID` | _String (opcional)_ | ID utilizado como valor para obter a conexão já existente, em vez de criar uma nova conexão |
| `modelToCreate` | _Object (opcional)_ | Ações utilizadas ao criar uma nova conexão |
| `modelToCreate.on_message` | _Function_ | Executado a cada nova mensagem recebida<br>O objeto `message` é do tipo:  [ByteBufferReader](https://github.com/holyrics/jslib/blob/main/doc/pt/ByteBufferReader.md)<br>`function(message) { ... }` |
| `modelToCreate.on_close` | _Function (opcional)_ | Executado ao encerrar a conexão<br>`function(evt) { /* evt.source; */ }` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[TCPClient](https://github.com/holyrics/jslib/blob/main/doc/pt/TCPClient.md)_ |  |


**Exemplo:**

```javascript
var client = createTCP('receiver_id');
client.send('message'); // utf-8

var buf = h.createByteBuffer()
           .putString('message', 'ascii');
client.send(buf);

function createTCP(receiver) {
  var client = h.tcp(receiver);
  if (client != null) {
    return client;
  }
  return h.tcp(receiver, {
    on_message: function (msg) {
      h.log(msg);
    },
    on_close: function (evt) {
      //evt.source;
    }
  });
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


### hly('GetSongs')
- v2.21.0

Retorna a lista de músicas



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Lyrics](#lyrics)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetSongs');
for (var i = 0; i < r.data.length; i++) {
    var s = r.data[i];
    h.log("", "ID: {}, Title: {}", [s.id, s.title]);
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
| `input.initial_index` | _Number (opcional)_ | Índice inicial da apresentação `Padrão: 0` `v2.23.0+` |


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


### hly('GetText', input)
- v2.21.0

Retorna um texto.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID do texto |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[Text](#text)_ | Texto ou NULL se não for encontrado |


**Exemplo:**

```javascript
var r = h.hly('GetText', {id: '123'});
if (r.data == null) {
    h.log('Item 123 não encontrado');
} else {
    h.log('Item 123:');
    h.log(r.data);
}
```

---


### hly('GetTexts')
- v2.21.0

Retorna a lista de textos



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Text](#text)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetTexts');
for (var i = 0; i < r.data.length; i++) {
    var t = r.data[i];
    h.log("", "ID: {}, Title: {}", [t.id, t.title]);
}
```

---


### hly('SearchText', input)
- v2.21.0

Realiza uma busca na lista de textos do usuário

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _String_ | Filtro |
| `input.text` | _String_ | Texto a ser pesquisado |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Lyrics](#lyrics)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('SearchText', {
    text: '...'
});
if (r.data.length == 0) {
    h.log("Item não encontrado");
} else {
    h.hly('ShowText', {id: r.data[0].id});
}
```

---


### hly('ShowText', input)
Inicia uma apresentação de um item da aba texto.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID do item |
| `input.initial_index` | _Number (opcional)_ | Índice inicial da apresentação `Padrão: 0` `v2.23.0+` |


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
| `input.version` | _String (opcional)_ | Nome ou abreviação da tradução utilizada `v2.21.0+` |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowVerse', {id: '19023001'});

h.hly('ShowVerse', {ids: ['19023001', '43003016', '45012002']});

h.hly('ShowVerse', {references: 'João 3:16'});

h.hly('ShowVerse', {
    references: 'Rm 12:2  Gn 1:1-3  Sl 23',
    version: 'en_kjv'
});

//Chamada alternativa
h.showVerse('Rm 12:2  Gn 1:1-3  Sl 23');
```

---


### hly('GetAudios', input)
### hly('GetVideos', input)
### hly('GetImages', input)
### hly('GetFiles', input) `v2.21.0+`
- v2.19.0

Retorna a lista de arquivos da respectiva aba: áudio, vídeo, imagem, arquivo

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.folder` | _String (opcional)_ | Nome da subpasta para listar os arquivos |
| `input.filter` | _String (opcional)_ | Filtrar arquivos pelo nome |
| `input.include_metadata` | _Boolean (opcional)_ | Adicionar metadados na resposta `Padrão: false` `v2.22.0+` |
| `input.include_thumbnail` | _Boolean (opcional)_ | Adicionar thumbnail na resposta (80x45) `Padrão: false` `v2.22.0+` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.name` | _String_ | Nome do item |
| `data.*.isDir` | _Boolean_ | Retorna **true** se for uma pasta ou **false** se for arquivo. |
| <br>Disponível se **include_metadata=true** |  |  |
| `data.*.length` | _Number_ | Tamanho do arquivo (bytes). Disponível se **isDir=false** `v2.22.0+` |
| `data.*.modified_time` | _String_ | Data de modificação do arquivo. Data e hora no formato: YYYY-MM-DD HH:MM `v2.22.0+` |
| `data.*.duration_ms` | _Number_ | Duração do arquivo. Disponível se o arquivo for: audio ou vídeo `v2.22.0+` |
| `data.*.width` | _Number_ | Largura. Disponível se o arquivo for: imagem ou vídeo `v2.22.0+` |
| `data.*.height` | _Number_ | Altura. Disponível se o arquivo for: imagem ou vídeo `v2.22.0+` |
| `data.*.position` | _String_ | Ajuste da imagem. Disponível para imagens. Pode ser: `adjust` `extend` `fill` `v2.22.0+` |
| `data.*.blur` | _Boolean_ | Aplicar efeito blur `v2.22.0+` |
| `data.*.transparent` | _Boolean_ | Exibir imagens com transparência `v2.22.0+` |
| <br>Disponível se **include_thumbnail=true** |  |  |
| `data.*.thumbnail` | _String_ | Imagem no formato base64 `v2.22.0+` |


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
| `input.settings` | _[PlayMediaSettings](#play-media-settings) (opcional)_ | Configurações para execução da mídia `v2.21.0+` |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('PlayAudio', {file: 'arquivo.mp3'});
h.hly('PlayAudio', {file: 'pasta'});
h.hly('PlayAudio', {
    file: 'pasta/arquivo.mp3',
    settings: {
        stop_time: "2:10",
        repeat: true
    }
});

//Chamada alternativa
h.playAudio('arquivo.mp3');

h.playAudio('arquivo.mp3', {
    volume: 90,
    start_time: '30'
});
```

---


### hly('PlayVideo', input)
Executa um vídeo ou uma lista de vídeos (pasta)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome do arquivo ou da pasta. Exemplo: **arquivo.mp4** ou **pasta** ou **pasta/arquivo.mp4** |
| `input.settings` | _[PlayMediaSettings](#play-media-settings) (opcional)_ | Configurações para execução da mídia `v2.21.0+` |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('PlayVideo', {file: 'arquivo.mp4'});
h.hly('PlayVideo', {
    file: 'pasta',
    settings: {
        shuffle: true
    }
});
h.hly('PlayVideo', {file: 'pasta/arquivo.mp4'});

//Chamada alternativa
h.playVideo('arquivo.mp4');

h.playVideo('arquivo.mp4', {
    volume: 0,
    repeat: true
});
```

---


### hly('ShowImage', input)
Apresenta uma imagem ou uma lista de imagens (pasta)

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome do arquivo ou da pasta. Exemplo: **arquivo.jpg** ou **pasta** ou **pasta/arquivo.jpg** |
| `input.automatic` | _[Automatic](#automatic) (opcional)_ | Se informado, a apresentação dos itens será automática |


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


### hly('ExecuteFile', input)
- v2.21.0

Executa um arquivo. Disponível apenas para extensões seguras, como áudio, vídeo, imagem, documentos, etc.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome do arquivo |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ExecuteFile', {
    file: 'file.txt'
});

//Chamada alternativa
h.executeFile("file.txt");
```

---


### hly('AudioExists', input)
### hly('VideoExists', input)
### hly('ImageExists', input)
### hly('FileExists', input)
- v2.21.0

Verifica se existe o arquivo com o nome informado

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.file` | _String_ | Nome do arquivo |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Boolean_ |  |


**Exemplo:**

```javascript
var r = h.hly('AudioExists', {file: 'audio.mp3'});
if (r.data) {
    //exists
}
h.hly('VideoExists', {file: 'video.mp4'});
h.hly('ImageExists', {file: 'image.jpg'});
h.hly('FileExists', {file: 'file.txt'});

//Chamada alternativa
if (h.audioExists("audio.mp3")) {
    //exists
}
h.videoExists("video.mp4");
h.imageExists("image.jpg");
h.fileExists("file.txt");
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
| `input.automatic` | _[Automatic](#automatic) (opcional)_ | Se informado, a apresentação dos itens será automática |


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
| `input.position_?` | _Object (opcional)_ | Variável adicionada na posição especificada conforme valor retornado em **variables.*.position** da classe CustomMessage. |
| `input.params` | _Object (opcional)_ | Método alternativo. Mapa chave/valor onde a chave é o nome do campo **variables.*.name** da classe CustomMessage. Se necessário adicionar o mesmo parâmetro, adicione `*_n` no final do nome, começando em 2<br>Exemplo: **input.params.name, input.params.name_2, input.params.name_3** `v2.21.0+` |
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

h.hly('ShowCustomMessage', {
    name: 'name',
    params: {
        abc: 'Value 1',
        xyz: 'Value 2',
        aaa: 'Value 3',
        abc_2: 'Value 4'
    },
    note: 'Com urgência'
});
```

---


### hly('ShowQuickPresentation', input)
Apresentação rápida de um texto

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.text` | _String_ | Texto que será exibido. [Styled Text](#styled-text) a partir da v2.19.0<br>Opcional se `slides` for declarado |
| `input.slides` | _Array&lt;[QuickPresentationSlide](#quick-presentation-slide)&gt;_ | Parâmetro alternativo para apresentações mais complexas<br>Opcional se `text` for declarado `v2.23.0+` |
| `input.theme` | _[ThemeFilter](#theme-filter) (opcional)_ | Filtrar tema selecionado para exibição |
| `input.custom_theme` | _[Theme](#theme) (opcional)_ | Tema personalizado utilizado para exibir o texto `v2.21.0+` |
| `input.automatic` | _[Automatic](#automatic) (opcional)_ | Se informado, a apresentação dos itens será automática |
| `input.initial_index` | _Number (opcional)_ | Índice inicial da apresentação `Padrão: 0` `v2.23.0+` |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowQuickPresentation', {
    text: "Texto que será exibido"
});

h.hly('ShowQuickPresentation', {
    text: "Slide 1\n\nSlide 2\n\nSlide 3",
    theme: {
        name: "Tema 3",
        edit: {
            font: {
                italic: true
            }
        }
    },
    automatic: {
        seconds: 5,
        repeat: true
    }
});

h.hly('ShowQuickPresentation', {
    text: "Texto que será exibido",
    custom_theme: {
        font: {
            name: "Arial",
            bold: true,
            size: 10,
            color: "FFFFFF"
        },
        background: {
            type: "color",
            id: "000000"
        }
    }
});

h.hly('ShowQuickPresentation', {
    slides: [
        {
            text: "Texto que será exibido (1)",
            theme: {
                name: "Tema 1"
            }
        }, {
            text: "Texto que será exibido (2)",
            duration: 20,
            translations: {
                "translation_name_1": "Exemplo",
                "translation_name_2": "Exemplo"
            }
        }, {
            text: "Texto que será exibido (3)",
            duration: 15,
            custom_theme: {
                font: {
                    color: "FFFFFF"
                },
                background: {
                    type: "color",
                    id: "000000"
                }
            }
        }
    ],
    //default theme
    theme: {
        name: "Tema"
    },
    automatic: {
        seconds: 10,
        repeat: true
    },
    initial_index: 2
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
| `input.theme` | _String (opcional)_ | ID do Tema `v2.21.0+` |
| `input.countdown_style` | _[FontSettings](#font-settings) (opcional)_ | Fonte personalizada para a contagem regressiva `v2.21.0+` |
| `input.custom_theme` | _[Theme](#theme) (opcional)_ | Tema personalizado `v2.21.0+` |


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
    text_after: 'Example',
    countdown_style: {
        italic: true
    }
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


### hly('GetAutomaticPresentations')
### hly('GetAPs', input)
- v2.21.0

Retorna a lista de apresentações automáticas



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.name` | _String_ | Nome do arquivo. Exemplo: **arquivo.ap** |


**Exemplo:**

```javascript
var r = h.hly('GetAutomaticPresentations');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetAutomaticPresentation', input)
### hly('GetAP', input)
- v2.21.0

Retorna uma apresentação automática

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `file` | _String_ | Nome do arquivo. Exemplo: **arquivo.ap** |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[AutomaticPresentation](#automatic-presentation)_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetAutomaticPresentation', {file: 'arquivo.ap'});
h.log(r.name);
h.log(r.song);
r.timeline.forEach(function(o) {
    h.log(o.duration);
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
| `input.theme.edit` | _[Theme](#theme) (opcional)_ | Configurações para modificar o Tema selecionado para exibição `v2.21.0+` |
| `input.custom_theme` | _[Theme](#theme) (opcional)_ | Tema personalizado utilizado para exibir a apresentação automática `v2.21.0+` |


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
| `data.duration_ms` | _Number_ | Tempo total em milissegundos `v2.21.0+` |


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


### hly('SetLyricsPlaylistItem', input)
### hly('SetSongPlaylistItem', input)
- v2.22.0

Alterar um item da lista de reprodução de letra de música

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.index` | _Number_ | Índice do item na lista |
| `input.song_id` | _String_ | Novo item |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetLyricsPlaylistItem', {
    index: 2,
    song_id: '123'
});
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


### hly('SetMediaPlaylistItem', input)
- v2.22.0

Alterar um item da lista de reprodução de mídia

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.index` | _Number_ | Índice do item na lista |
| `input.item` | _[AddItem](#add-item)_ | Novo item |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetMediaPlaylistItem', {
    index: 2,
    item: {
        type: 'song',
        id: '123'
    }
});
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


### hly('GetNextSongPlaylist')
- v2.22.0

Retorna a próxima música da lista de reprodução. Pode ser null



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[Lyrics](#lyrics)_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetNextSongPlaylist');
```

---


### hly('GetNextMediaPlaylist')
- v2.22.0

Retorna o próximo item executável da lista de reprodução de mídia. Pode ser null



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[Item](#item)_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetNextMediaPlaylist');
```

---


### hly('ShowNextSongPlaylist')
- v2.22.0

Executa a próxima música da lista de reprodução



_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowNextSongPlaylist');
```

---


### hly('ShowNextMediaPlaylist')
- v2.22.0

Executa o próximo item da lista de reprodução de mídia



_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowNextMediaPlaylist');
```

---


### hly('GetPreviousSongPlaylist')
- v2.22.0

Retorna a música anterior da lista de reprodução. Pode ser null



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[Lyrics](#lyrics)_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetPreviousSongPlaylist');
```

---


### hly('GetPreviousMediaPlaylist')
- v2.22.0

Retorna o item anterior executável da lista de reprodução de mídia. Pode ser null



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[Item](#item)_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetPreviousMediaPlaylist');
```

---


### hly('ShowPreviousSongPlaylist')
- v2.22.0

Executa a música anterior da lista de reprodução



_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowPreviousSongPlaylist');
```

---


### hly('ShowPreviousMediaPlaylist')
- v2.22.0

Executa o item anterior da lista de reprodução de mídia



_Método sem retorno_

**Exemplo:**

```javascript
h.hly('ShowPreviousMediaPlaylist');
```

---


### hly('AddToPlaylist', input)
- v2.20.0

Adicionar itens à lista de reprodução de mídias

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.items` | _Array&lt;[AddItem](#add-item)&gt;_ | Lista com os itens que serão adicionados |
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


### hly('SetPlaylistItemDuration', input)
- v2.21.0

Alterar duração de um item da lista de reprodução de mídia.

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String (opcional)_ | ID do item |
| `input.index` | _Number (opcional)_ | Posição do item na lista (inicia em zero). |
| `input.duration` | _Number (opcional)_ | Duração do item (em segundos) |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetPlaylistItemDuration', {
    id: 'abc',
    duration: 300
});
```

---


### hly('GetSlideDescriptions')
- v2.21.0

Lista das descrições do slide disponíveis



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[SlideDescription](#slide-description)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetSlideDescriptions');
for (var i = 0; i < r.data.length; i++) {
    var s = r.data[i];
    h.log("", "Name: {}, Tag: {}", [s.name, s.tag]);
}
```

---


### hly('GetFavorites')
Itens da barra de favoritos



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[FavoriteItem](#favorite-item)&gt;_ |  |


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


### hly('GetApis')
- v2.21.0

Retorna a lista de APIs



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.id` | _String_ | ID do item |
| `data.*.name` | _String_ | Nome do item |


**Exemplo:**

```javascript
var r = h.hly('GetApis');
for (var i = 0; i < r.data.length; i++) {
    var o = r.data[i];
    h.log("", "ID: {}, Name: {}", [o.id, o.name]);
}
```

---


### hly('GetScripts')
- v2.21.0

Retorna a lista de scripts



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.id` | _String_ | ID do item |
| `data.*.name` | _String_ | Nome do item |


**Exemplo:**

```javascript
var r = h.hly('GetScripts');
for (var i = 0; i < r.data.length; i++) {
    var o = r.data[i];
    h.log("", "ID: {}, Name: {}", [o.id, o.name]);
}
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

Executa uma requisição para o receptor associado e retorna a resposta do receptor.<br>
A partir da `v2.23.0` é possível passar o host ou ip diretamente, porém é necessário adicionar o host/ip na lista de requisições permitidas.<br>
menu arquivo > configurações > avançado > javascript > configurações > requisições permitidas

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


### hly('GetCurrentPresentation', input)
- v2.19.0

Item sendo apresentado no momento ou **null** se não tiver apresentação sendo exibida

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.include_slides` | _Boolean (opcional)_ | Retornar a lista de slides da apresentação atual. Indisponível para apresentação de versículos. `Padrão: false` `v2.21.0+` |
| `input.include_slide_comment` | _Boolean (opcional)_ | Incluir comentários (se houver) no texto dos slides. Disponível se **include_slides=true**. `Padrão: false` `v2.21.0+` |
| `input.include_slide_preview` | _Boolean (opcional)_ | Incluir imagem preview do slide. Disponível se **include_slides=true**. `Padrão: false` `v2.21.0+` |
| `input.lide_preview_size` | _String (opcional)_ | Tamanho do preview no formato WxH (ex. 320x180). (max 640x360)<br>Disponível se **include_slide_preview=true** `Padrão: false` `v2.21.0+` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.id` | _String_ | ID do item |
| `data.type` | _String_ | Tipo do item. Pode ser: `song` `verse` `text` `audio` `image` `announcement` `automatic_presentation` `quick_presentation` |
| `data.name` | _String_ | Nome do item |
| `data.slide_number` | _Number_ | Começa em 1 `v2.20.0+` |
| `data.total_slides` | _Number_ | Total de slides `v2.20.0+` |
| `data.slide_type` | _String_ | Um dos seguintes valores: `default`  `wallpaper`  `blank`  `black`  `final_slide` `v2.20.0+` |
| `data.slides` | _Array&lt;[PresentationSlideInfo](#presentation-slide-info)&gt;_ | Lista com os slides da apresentação atual. Disponível se **include_slides=true** `v2.21.0+` |


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


### hly('GetCurrentTheme')
- v2.22.0

Retorna o tema da apresentação em exibição.



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[Background](#background)_ | Tema atual ou NULL se não houver apresentação em exibição |


**Exemplo:**

```javascript
var r = h.hly('GetCurrentTheme');
if (r.data != null) {
    h.log('ID do tema atual: ' + r.data.id);
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
| `input.type` | _String (opcional)_ | Pode ser: `theme` `my_video` `my_image` `video` `image` |
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
| `input.type` | _String (opcional)_ | Pode ser: `theme` `my_video` `my_image` `video` `image` |
| `input.tag` | _String (opcional)_ |  |
| `input.tags` | _Array&lt;String&gt; (opcional)_ |  |
| `input.intersection` | _Boolean (opcional)_ | Se o campo **input.tags** estiver preenchido com múltiplos itens, a opção **input.intersection** define o tipo de junção. Se **true**, o filtro retornará apenas itens que contém **todas** as tags informadas, se **false**, o filtro retornará os itens que têm pelo menos uma tag das tags informadas `Padrão: false` |
| `input.edit` | _[Theme](#theme) (opcional)_ | Configurações para modificar o Tema selecionado para exibição `v2.21.0+` |
| `input.custom_theme` | _[Theme](#theme) (opcional)_ | Tema personalizado `v2.21.0+` |


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

//um vídeo que esteja definido com a tag 'água' OU com a tag 'azul'
//o tema selecionado será modificado para a fonte 'Arial' em itálico
h.hly('SetCurrentBackground', {
    type: 'theme',
    tag: 'água',
    edit: {
      font: {
        name: 'Arial',
        italic: true
      }
    }
});

//alterar para um tema personalizado
h.hly('SetCurrentBackground', {
    custom_theme: {
        font: {
            name: "Arial",
            bold: true,
            size: 10,
            color: "FFFFFF"
        },
        background: {
            type: "color",
            id: "000000"
        },
        settings: {
          uppercase: true
        }
    }
});
```

---


### hly('GetThumbnail', input)
- v2.21.0

Retorna a imagem miniatura de um item no programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String (opcional)_ | ID do item |
| `input.ids` | _Array&lt;String&gt; (opcional)_ | ID dos itens |
| `input.type` | _String_ | Tipo do item. Pode ser: `video` `image` `announcement` `theme` `background` `api` `script` |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.type` | _String_ | Tipo do item |
| `data.*.id` | _String_ | ID do item |
| `data.*.image` | _String_ | Imagem no formato base64 |


**Exemplo:**

```javascript
var r = h.hly('GetThumbnail', {
    id: 'image.jpg',
    type: 'image'
});
h.log("Image base64: " + r.data[0].image);

var r = h.hly('GetThumbnail', {
    ids: ['123', '456'],
    type: 'theme'
});
for (var i = 0; i < r.data.length; i++) {
    var t = r.data[i];
    h.log("", "Theme ID: {}\nImage base64: {}\n", [t.id, t.image]);
}
```

---


### hly('GetColorMap', input)
- v2.20.0

Retorna as informações de cor predominante de um respectivo tipo de item.<br/>O array retornado contém 8 índices, e cada índice corresponde ao trecho conforme imagem de exemplo a seguir.<br/> <br/>![Color Map Example](https://holyrics.com.br/images/color_map_item_example.png)<br/>

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
| `data.*.red` | _Number_ | Vermelho  `0 ~ 255` |
| `data.*.green` | _Number_ | Verde  `0 ~ 255` |
| `data.*.blue` | _Number_ | Azul  `0 ~ 255` |


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


### hly('GetAlert')
- v2.20.0

Retorna as configurações da mensagem de alerta



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.text` | _String_ | Texto atual do alerta |
| `data.show` | _Boolean_ | Se a exibição do alerta está ativada |


**Exemplo:**

```javascript
var r = h.hly('GetAlert');
h.log(r.text);
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
| `data` | _Array&lt;[Schedule](#schedule)&gt;_ |  |


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


### hly('GetTeams')
- v2.22.0

Lista de times



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Team](#team)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetTeams');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
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


### hly('GetServices')
- v2.22.0

Lista de cultos



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Service](#service)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetServices');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetEvents', input)
- v2.22.0

Lista de eventos

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.month` | _Number_ | Mês (1-12) |
| `input.year` | _Number_ | Ano |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Event](#event)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetEvents', {
    month: 8,
    year: 2022
});
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetAnnouncement', input)
- v2.22.0

Anúncio

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String (opcional)_ | ID do anúncio |
| `input.name` | _String (opcional)_ | Nome do anúncio |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _[Announcement](#announcement)_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetAnnouncement', {
    id: '123'
});
h.log(r.data.name);
```

---


### hly('GetAnnouncements')
- v2.22.0

Lista de anúncios



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[Announcement](#announcement)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetAnnouncements');
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
| `data.attention_icon_color` | _String_ | Cor do ícone do botão **Atenção** `v2.23.0+` |
| `data.attention_background_color` | _String_ | Cor do fundo do ícone do botão **Atenção** `v2.23.0+` |


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
| `input.theme` | _Object (opcional)_ | ID ou nome do tema padrão |
| `input.theme.id` | _String (opcional)_ |  |
| `input.theme.name` | _String (opcional)_ |  |
| `input.custom_theme` | _[Theme](#theme) (opcional)_ | Tema personalizado `v2.21.0+` |
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
| `input.attention_icon_color` | _String (opcional)_ | Cor do ícone do botão **Atenção** `v2.23.0+` |
| `input.attention_background_color` | _String (opcional)_ | Cor do fundo do ícone do botão **Atenção** `v2.23.0+` |


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
| `input.theme` | _Object (opcional)_ | ID ou nome do Tema utilizado para exibir o texto `v2.21.0+` |
| `input.custom_theme` | _[Theme](#theme) (opcional)_ | Tema personalizado para exibir o texto `v2.21.0+` |


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
| `data.extend` | _Boolean_ | `deprecated` Substituído por `adjust_type`<br>Estender papel de parede |
| `data.adjust_type` | _String_ | Ajuste da imagem: Pode ser: `ADJUST` `EXTEND` `FILL` `ADJUST_BLUR` `v2.22.0+` |
| `data.show_clock` | _Boolean_ | Exibir relógio |
| `data.by_screen` | _Object_ | Configuração independente por tela `v2.23.0+` |
| `data.by_screen.default` | _[WallpaperSettings](#wallpaper-settings)_ | Configuração padrão `v2.23.0+` |
| `data.by_screen.public` | _[WallpaperSettings](#wallpaper-settings)_ | Configuração personalizada para a tela ou **null** se estiver utilizando a configuração padrão `v2.23.0+` |
| `data.by_screen.screen_n` | _[WallpaperSettings](#wallpaper-settings)_ | n >= 2  `v2.23.0+` |


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
| `input.extend` | _Boolean (opcional)_ | `deprecated` Substituído por `adjust_type`<br>Estender papel de parede |
| `input.adjust_type` | _String_ | Ajuste da imagem: Pode ser: `ADJUST` `EXTEND` `FILL` `ADJUST_BLUR` `v2.22.0+` |
| `input.show_clock` | _Boolean (opcional)_ | Exibir relógio |
| `input.by_screen` | _Object (opcional)_ | Configuração independente por tela `v2.23.0+` |
| `input.by_screen.default` | _[WallpaperSettings](#wallpaper-settings) (opcional)_ | Configuração padrão `v2.23.0+` |
| `input.by_screen.public` | _[WallpaperSettings](#wallpaper-settings) (opcional)_ | Configuração personalizada para a tela ou **null** se estiver utilizando a configuração padrão `v2.23.0+` |
| `input.by_screen.screen_n` | _[WallpaperSettings](#wallpaper-settings) (opcional)_ | n >= 2 `v2.23.0+` |


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


### hly('GetTransitionEffectSettings')
- v2.21.0

Lista da configuração dos efeitos de transição



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `music` | _Array&lt;[TransitionEffectSettings](#transition-effect-settings)&gt;_ |  |
| `bible` | _Array&lt;[TransitionEffectSettings](#transition-effect-settings)&gt;_ |  |
| `image` | _Array&lt;[TransitionEffectSettings](#transition-effect-settings)&gt;_ |  |
| `announcement` | _Array&lt;[TransitionEffectSettings](#transition-effect-settings)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetTransitionEffectSettings');
var s = r.data.music;
h.log(s.enabled);
h.log(s.type);
h.log(s.duration);
```

---


### hly('SetTransitionEffectSettings', input)
- v2.21.0

Alterar as configurações de um efeito de transição

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _Object_ | ID do item |
| `input.settings` | _[TransitionEffectSettings](#transition-effect-settings)_ | Novas configurações. As configurações são individualmente opcionais. Preencha apenas os campos que deseja alterar. |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna **true** ou uma lista com os erros ocorridos |


**Exemplo:**

```javascript
var r = h.hly('SetTransitionEffectSettings', {
    id: 'music',
    settings: {
        enabled: true,
        type: 'fade',
        duration: 700
    }
});
var r = h.hly('SetTransitionEffectSettings', {
    id: 'image',
    settings: {
        enabled: true,
        type: 'zoom',
        duration: 1000,
        zoom_type: 'random',
        directions: {
             top_left: false,    top_center: false,    top_right: false,
          middle_left: false, middle_center: true,  middle_right: false,
          bottom_left: false, bottom_center: false, bottom_right: false
      }
    }
});
var r = h.hly('SetTransitionEffectSettings', {
    id: 'announcement',
    settings: {
        enabled: true,
        type: 'random',
        duration: 1000,
        random_enabled_types: {
                 fade: false,
                slide: true,
            accordion: false,
          linear_fade: false,
                 zoom: true,
              curtain: true
        }
    }
});
```

---


### hly('GetBibleVersions')
- v2.21.0

`deprecated` Substituído por: hly('GetBibleVersionsV2')<br>Retorna a lista de versões disponíveis da Bíblia, e também dos atalhos associados



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.key` | _String_ | Abreviação da versão ou o nome do atalho, se começar com '#shortcut ' |
| `data.*.title` | _String_ | Nome da versão |
| `data.*.version` | _String (opcional)_ | Abreviação da versão. Disponível se o item for um atalho, ou seja se 'key' começar com '#shortcut ' |


**Exemplo:**

```javascript
var r = h.hly('GetBibleVersions');
for (var i = 0; i < r.data.length; i++) {
    var o = r.data[i];
    var shortcut = o.key.startsWith("#shortcut ");
    var version = shortcut ? o.version : o.key;
    var title = shortcut ? o.key.substring(10) : o.title;
    h.log("", "Version: {}, Title: {}", [version, title]);
}
```

---


### hly('GetBibleVersionsV2')
- v2.23.0

Retorna a lista de versões disponíveis da Bíblia, e também dos atalhos associados



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.key` | _String_ | ID do item |
| `data.*.version` | _String_ | ID da versão da Bíblia |
| `data.*.title` | _String_ | Nome da versão ou nome do atalho |


**Exemplo:**

```javascript
var r = h.hly('GetBibleVersionsV2');
for (var i = 0; i < r.data.length; i++) {
    var o = r.data[i];
    h.logf("ID: {}, Version: {}, Title: {}", [o.id, o.version, o.title]);
}
```

---


### hly('GetBibleSettings')
- v2.21.0

Configurações do módulo Bíblia



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data` | _Array&lt;[BibleSettings](#bible-settings)&gt;_ |  |


**Exemplo:**

```javascript
var r = h.hly('GetBibleSettings');
h.log("Default version: " + r.data.tab_version_1);
```

---


### hly('SetBibleSettings', input)
- v2.21.0

Alterar as configurações do módulo Bíblia

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input` | _[BibleSettings](#bible-settings)_ | Novas configurações. As configurações são individualmente opcionais. Preencha apenas os campos que deseja alterar. |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna **true** ou uma lista com os erros ocorridos |


**Exemplo:**

```javascript
var r = h.hly('SetBibleSettings', {
    tab_version_1: 'pt_acf',
    show_x_verses: 1,
    theme: {
        'public': '123'
    }
});
```

---


### hly('GetPresentationFooterSettings')
- v2.23.0

Configurações do rodapé de apresentação



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.rows` | _Number_ | Quantidade de linhas. `1 ~ 4` |
| `data.preview_mode` | _String_ | Valores aceitos: `text` `image` |
| `data.minimized` | _Boolean_ |  |


---


### hly('SetPresentationFooterSettings', input)
- v2.23.0

Alterar as configurações do rodapé de apresentação

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.rows` | _Number_ | Quantidade de linhas. `1 ~ 4` |
| `input.preview_mode` | _String_ | Valores aceitos: `text` `image` |
| `input.minimized` | _Boolean_ |  |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Retorna **true** ou uma lista com os erros ocorridos |


**Exemplo:**

```javascript
var r = h.hly('SetPresentationFooterSettings', {
    minimized: false,
    preview_mode: 'text',
    rows: 2
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


### hly('GetInterfaceInput', input)
- v2.21.0

Retorna o valor de um campo da interface do programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID do item. Pode ser: <br>`main_lyrics_tab_search`<br>`main_text_tab_search`<br>`main_audio_tab_search`<br>`main_video_tab_search`<br>`main_image_tab_search`<br>`main_file_tab_search`<br>`main_automatic_presentation_tab_search`<br>`main_selected_theme` |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Conteúdo do item |


**Exemplo:**

```javascript
var r = h.hly('GetInterfaceInput', {
    id: 'main_lyrics_tab_search'
});
```

---


### hly('SetInterfaceInput', input)
- v2.21.0

Altera o valor de um campo da interface do programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID do item |
| `input.value` | _String_ | Novo valor |
| `input.focus` | _Boolean (opcional)_ | Fazer o componente receber o foco do sistema |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SetInterfaceInput', {
    id: 'main_audio_tab_search',
    value: '...',
    focus: true
});

h.hly('SetInterfaceInput', {
    id: 'main_selected_theme',
    value: '123' //Theme ID
});
```

---


### hly('SelectVerse', input)
- v2.21.0

Seleciona um versículo na janela da Bíblia

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.id` | _String (opcional)_ | ID do versículo |
| `input.reference` | _String (opcional)_ | Referência do versículo |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('SelectVerse', { id: '43003016' });
```

---


### hly('OpenDrawLots', input)
- v2.21.0

Abre a janela de sorteio a partir de uma lista de itens

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.items` | _Array&lt;String&gt;_ | Lista com os itens para serem sorteados |


_Método sem retorno_

**Exemplo:**

```javascript
h.hly('OpenDrawLots', {
    items: ['exemplo 1', 'exemplo 2', 'exemplo 3']
});
```

---


### hly('GetMediaDuration', input)
- v2.21.0

Retorna a duração da mídia

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `input.type` | _String_ | Tipo do item. Pode ser: `video`, `audio`, `automatic_presentation` |
| `input.name` | _String_ | Nome do item |


**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.type` | _String_ |  |
| `data.name` | _String_ |  |
| `data.duration` | _Number_ | Duração em segundos |
| `data.duration_ms` | _Number_ | Duração em milissegundos |


**Exemplo:**

```javascript
var r = h.hly('GetMediaDuration', {
    type: 'audio',
    name: 'file.mp3'
});
h.log("Duration: " + r.data.duration + "s");
```

---


### hly('GetVersion')
- v2.22.0

Retorna informações da versão do programa em execução



**Resposta:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `data.version` | _String_ | Versão do programa |
| `data.platform` | _String_ | Sistema operacional. Pode ser: `win` `uni` `osx` |
| `data.platformDescription` | _String_ | Nome detalhado do sistema operacional |


**Exemplo:**

```javascript
var r = h.hly('GetVersion');
h.log(r.data.version);
h.log(r.data.plaftorm);
h.log(r.data.plaftormDescription);
```

---


# Métodos SecurityUtils 
### encrypt(value)
### enc(value)
- v2.23.0

Encriptar um valor `String`

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _String_ | Valor para ser encriptado |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Valor criptografado em Base64 |


**Exemplo:**

```javascript
var b64 = h.sec('key').encrypt('Test');
// b64: rNFZfSWo/J+ggo11cxPNxg==
```

---


### decrypt(base64)
### dec(base64)
- v2.23.0

Descriptografar um valor `String`

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `base64` | _String_ | Valor em Base64 para ser descriptografado |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Valor descriptografado |


**Exemplo:**

```javascript
var r = h.sec('key').decrypt('rNFZfSWo/J+ggo11cxPNxg==');
// r: Test
```

---


### encryptObj(value)
### encObj(value)
- v2.23.0

Encriptar um valor `Object`

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `value` | _Object_ | Valor para ser encriptado |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _String_ | Valor criptografado em Base64 |


**Exemplo:**

```javascript
var example = {
  a: 1,
  b: 2
};
var b64 = h.sec('key').encObj(example);
h.log(b64);
// b64: nO2IFVws9KhnhxvQ3IBX2g==
```

---


### decryptObj(base64)
### decObj(base64)
- v2.23.0

Descriptografar um valor `Object`

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `base64` | _String_ | Valor em Base64 para ser descriptografado |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Valor descriptografado |


**Exemplo:**

```javascript
var val = h.sec('key').dec('nO2IFVws9KhnhxvQ3IBX2g==');
h.log(val);
// val: { a: 1, b: 2 }
```

---


### relativeMethods
- v2.23.0

Todos os métodos a seguir têm a mesma documentação do respectivo método original.
```
store(key, value)

restore(key, default = null)

setGlobal(key, value, ttl = 0)

getGlobal(key, default = null)

setGlobalNext(key, values, ttl = 0)

getGlobalAndSet(key, default = null, newValue)

getGlobalAndSet(key, newValue)

getGlobalAndSetNext(key, values)

setGlobalNextAndGet(key, values)
```




_Método sem retorno_

**Exemplo:**

```javascript
var sec = h.sec('key');

sec.store('name', 'value');
var r = sec.restore('name', '');
// r: value

sec.store('name2', { a: 1 });
var r = sec.restore('name2', {});
// r: { a: 1 }

sec.setGlobal('name', 'value');
var r = sec.getGlobal('name', '');
// r: value

sec.setGlobal('name2', { a: 1 });
var r = sec.getGlobal('name2', {});
// r: { a: 1 }
```

---


# Métodos User Input 
### input(param, notification = false)
Exibir uma janela com campos de entrada para receber informações de forma interativa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `param` | _Object_ | Entradas que serão solicitadas na interface. Pode ser string ou Array&lt;[InputParam](#input-param)&gt;. Se for passada uma string, ela será o nome do item e o tipo do item será **string** |
| `notification` | _Boolean (opcional)_ | Exibe uma notificação em vez de abrir a janela diretamente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Se for passado apenas um item como entrada, será retornado o valor informado pelo usuário (pode ser NULL). Se múltiplas entradas forem solicitadas, será retornado um objeto (pode ser NULL) onde cada valor será informado na variável do seu respectivo ID. |


**Exemplo:**

```javascript
var r = h.input("Nome do item");
h.log("Valor informado: " + r);

var param = [{type: 'password', name: 'Senha'}];
var r = h.input(param);
h.log("Senha informada: " + r);

var param = [
    {
        key: 'info',
        type: 'string',
        name: 'Informação'
    }, {
        key: 'type',
        type: 'string',
        name: 'Tipo',
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
        name: 'Mensagem'
    }, {
        key: 'seconds',
        type: 'number',
        name: 'Segundos',
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


### settings(saveTo, saveToStore, data)
### settings(saveTo, data)
- v2.23.0

A mesma função de `h.input(...)`, porém salva automaticamente o valor em `setGlobal` e `store`, e também exibe o valor atual salvo anteriormente.<br>O valor será armazenado apenas ao clicar em OK na janela de configurações

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `saveTo` | _String_ | Chave de armazenamento utilizado para salvar e recuperar o valor dos itens.<br>`h.setGlobal(saveTo, ...)`<br>`h.getGlobal(saveTo, ...)`<br>`h.store(saveTo, ...)`<br>`h.restore(saveTo, ...)` |
| `saveToStore` | _Boolean_ | **true** para salvar o valor também em `h.store(saveTo, ...)`, ou seja, a configuração se mantém salva mesmo após reiniciar o programa `Padrão: true` |
| `data` | _Object_ | Entradas que serão solicitadas na interface. Pode ser string ou Array&lt;[InputParam](#input-param)&gt;. Se for passada uma string, ela será o nome do item e o tipo do item será **string**.<br>`data` pode ser `saveTo` (chave de armazenamento) caso o método `h.registerSettings(saveTo, ...)` ou `h.loadSettings(saveTo, ...)` tenha sido chamado anteriormente |


**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _Object_ | Se for passado apenas um item como entrada, será retornado o valor informado pelo usuário (pode ser NULL). Se múltiplas entradas forem solicitadas, será retornado um objeto (pode ser NULL) onde cada valor será informado na variável do seu respectivo ID. |


**Exemplo:**

```javascript
var inputs = [
  {
    id: 'message',
    type: 'string'
  }, {
    id: 'duration',
    type: 'number',
    default_value: 10
  }
];
var r = h.settings('settings_name', inputs);
//r.message
//r.duration
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
var r = h.inputTextArea("Nome do item");
h.log("Valor informado: " + r);

var r = h.inputTextArea("Nome do item", true); //notificação
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


### textChooser()
- v2.22.0

Abre uma janela para selecionar um item Texto



**Resposta:**

| Tipo  | Descrição |
| :---: | ------------|
| _[Text](#text)_ | Retorna o item selecionado pelo usuário (pode ser NULL) |


**Exemplo:**

```javascript
var r = h.textChooser();
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


### openWindow(name)
- v2.22.0

Abre uma janela do programa

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome da janela. Pode ser: `main` `bible` `communication_panel` `chat`<br> <br>**v2.23.0+**<br>`js_playground` `js_monitor_interval` `js_monitor_timeout` `js_monitor_trigger` `js_monitor_global` `js_monitor_timer_and_countdown`  |


_Método sem retorno_

**Exemplo:**

```javascript
h.openWindow('main');

h.openWindow('bible');
```

---


### repaint(id)
- v2.23.0

Força a atualização de um componente da interface.<br>Disponível atualmente para: Barra de favoritos

**Parâmetros:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |


_Método sem retorno_

**Exemplo:**

```javascript
h.repaint('favorite_id');
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
| `slides` | _Array&lt;Object&gt;_ |  `v2.21.0+` |
| `slides.*.text` | _String_ | Texto do slide `v2.21.0+` |
| `slides.*.slide_description` | _Number_ | Descrição do slide `v2.21.1+` |
| `slides.*.background_id` | _Number_ | ID do tema ou plano de fundo salvo para o slide `v2.21.0+` |
| `order` | _String_ | Ordem dos slides (índice a partir do 1), separado por vírgula `v2.21.0+` |
| `key` | _String_ | Tom da música.<br>Pode ser: `C` `C#` `Db` `D` `D#` `Eb` `E` `F` `F#` `Gb` `G` `G#` `Ab` `A` `A#` `Bb` `B` `Cm` `C#m` `Dbm` `Dm` `D#m` `Ebm` `Em` `Fm` `F#m` `Gbm` `Gm` `G#m` `Abm` `Am` `A#m` `Bbm` `Bm` |
| `bpm` | _Number_ | BPM da música |
| `time_sig` | _String_ | Tempo da música.<br>Pode ser: `2/2` `2/4` `3/4` `4/4` `5/4` `6/4` `3/8` `6/8` `7/8` `9/8` `12/8` |
| `groups` | _Array&lt;[Group](#group)&gt;_ | Grupos onde a música está adicionada |
| `linked_audio_file` | _String_ | Caminho do arquivo de áudio linkado com a música `v2.22.0+` |
| `linked_backing_track_file` | _String_ | Caminho do arquivo de áudio (playback) linkado com a música `v2.22.0+` |
| `streaming` | _Object_ | URI ou ID dos streamings `v2.22.0+` |
| `streaming.audio` | _Object_ | Áudio `v2.22.0+` |
| `streaming.audio.spotify` | _String_ |  `v2.22.0+` |
| `streaming.audio.youtube` | _String_ |  `v2.22.0+` |
| `streaming.audio.deezer` | _String_ |  `v2.22.0+` |
| `streaming.backing_track` | _Object_ | Playback `v2.22.0+` |
| `streaming.backing_track.spotify` | _String_ |  `v2.22.0+` |
| `streaming.backing_track.youtube` | _String_ |  `v2.22.0+` |
| `streaming.backing_track.deezer` | _String_ |  `v2.22.0+` |
| `midi` | _[Midi](#midi)_ | Atalho MIDI do item |
| `extras` | _Object_ | Mapa de objetos extras (adicionados pelo usuário) `v2.21.0+` |
| `archived` | _Boolean_ | Se a música está arquivada |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "id": "0",
  "title": "",
  "artist": "",
  "author": "",
  "note": "",
  "copyright": "",
  "slides": [
    {
      "text": "Slide 1 line 1\nSlide 1 line 2",
      "styled_text": "Slide 1 line 1\nSlide 1 line 2",
      "slide_description": "Verse 1",
      "background_id": null,
      "translations": null
    },
    {
      "text": "Slide 2 line 1\nSlide 2 line 2",
      "styled_text": "Slide 2 line 1\nSlide 2 line 2",
      "slide_description": "Chorus",
      "background_id": null,
      "translations": null
    },
    {
      "text": "Slide 3 line 1\nSlide 3 line 2",
      "styled_text": "Slide 3 line 1\nSlide 3 line 2",
      "slide_description": "Verse 3",
      "background_id": null,
      "translations": null
    }
  ],
  "order": "1,2,3,2,2",
  "key": "",
  "bpm": 0.0,
  "time_sig": "",
  "groups": [],
  "linked_audio_file": "",
  "linked_backing_track_file": "",
  "streaming": {
    "audio": {
      "spotify": "",
      "youtube": "",
      "deezer": ""
    },
    "backing_track": {
      "spotify": "",
      "youtube": "",
      "deezer": ""
    }
  },
  "extras": {
    "extra": ""
  },
  "archived": false
}
```
</details>

## Text
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do texto |
| `title` | _String_ | Título do texto |
| `folder` | _String_ | Caminho da pasta de localização |
| `theme` | _String_ | ID do tema salvo para o texto |
| `slides` | _Array&lt;Object&gt;_ |  |
| `slides.*.text` | _String_ | Texto do slide |
| `slides.*.background_id` | _Number_ | ID do tema ou plano de fundo salvo para o slide |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "id": "",
  "title": "",
  "folder": "",
  "theme": null,
  "slides": [
    {
      "text": "Slide 1 line 1\nSlide 1 line 2",
      "styled_text": "Slide 1 line 1\nSlide 1 line 2",
      "background_id": null,
      "translations": null
    },
    {
      "text": "Slide 2 line 1\nSlide 2 line 2",
      "styled_text": "Slide 2 line 1\nSlide 2 line 2",
      "background_id": null,
      "translations": null
    },
    {
      "text": "Slide 3 line 1\nSlide 3 line 2",
      "styled_text": "Slide 3 line 1\nSlide 3 line 2",
      "background_id": null,
      "translations": null
    }
  ]
}
```
</details>

## Theme
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `copy_from_id` | _String (opcional)_ | ID de um Tema existente para utilizar como cópia inicial ao criar um novo item |
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |
| <br>**background** |  | <br>Plano de fundo |
| `background.type` | _String_ | Tipo do plano de fundo. Pode ser: `color`  `my_video`  `my_image`  `video`  `image`  `pattern`  `transparent`  `image_file`  `video_file` |
| `background.id` | _String_ | <table><tr><td><p align="right">**Tipo**</p></td><td>Valor</td></tr><tr><td><p align="right">color</p></td><td>Cor no formato hexadecimal</td></tr><tr><td><p align="right">my_video</p></td><td>ID do item</td></tr><tr><td><p align="right">my_image</p></td><td>ID do item</td></tr><tr><td><p align="right">video</p></td><td>ID do item</td></tr><tr><td><p align="right">image</p></td><td>ID do item</td></tr><tr><td><p align="right">pattern</p></td><td>ID do item</td></tr><tr><td><p align="right">transparent</p></td><td>"transparent"</td></tr><tr><td><p align="right">image_file</p></td><td>Nome do arquivo na biblioteca</td></tr><tr><td><p align="right">video_file</p></td><td>Nome do arquivo na biblioteca</td></tr></table> |
| `background.adjust_type` | _String_ | `fill` `extend` `adjust` `side_by_side` `center`<br>Disponível para: **type=my_image**, **type=image** |
| `background.opacity` | _Number_ | Opacidade. `0 ~ 100` |
| `background.velocity` | _Number_ | Disponível para: **type=my_video**, **type=video**<br>`0.25 ~ 4.0` |
| `base_color` | _String_ | Cor no formato hexadecimal. Cor base do plano de fundo ao diminuir a opacidade. |
| <br>**font** |  | <br>Fonte |
| `font.name` | _String_ | Nome da fonte |
| `font.bold` | _Boolean_ | Negrito |
| `font.italic` | _Boolean_ | Itálico |
| `font.size` | _Number_ | Tamanho `0.0 ~ 0.4`<br>Valor em porcentagem, baseado na altura do slide. |
| `font.color` | _String_ | Cor no formato hexadecimal |
| `font.line_spacing` | _Number_ | Espaçamento entre linhas. `-0.5 ~ 1.0`<br>Valor em porcentagem baseado na altura da linha. |
| `font.char_spacing` | _Number_ | Espaçamento entre caracteres. `-40 ~ 120` |
| <br>**align** |  | <br>Alinhamento |
| `align.horizontal` | _String_ | `left`  `center`  `right`  `justify` |
| `align.vertical` | _String_ | `top`  `middle`  `bottom` |
| `align.margin.top` | _Number_ | `0 ~ 90` |
| `align.margin.right` | _Number_ | `0 ~ 90` |
| `align.margin.bottom` | _Number_ | `0 ~ 90` |
| `align.margin.left` | _Number_ | `0 ~ 90` |
| <br>**effect** |  | <br>Efeitos da fonte |
| `effect.outline_color` | _String_ | Cor no formato hexadecimal |
| `effect.outline_weight` | _Number_ | `0.0 ~ 100.0` |
| `effect.brightness_color` | _String_ | Cor no formato hexadecimal |
| `effect.brightness_weight` | _Number_ | `0.0 ~ 100.0` |
| `effect.shadow_color` | _String_ | Cor no formato hexadecimal |
| `effect.shadow_x_weight` | _Number_ | `-100.0 ~ 100.0` |
| `effect.shadow_y_weight` | _Number_ | `-100.0 ~ 100.0` |
| `effect.blur` | _Boolean_ | Aplicar efeito 'blur' no brilho e sombra |
| <br>**shape_fill** |  | <br>Cor de fundo |
| `shape_fill.type` | _String_ | `box`  `line`  `line_fill`  `theme_margin` |
| `shape_fill.enabled` | _Boolean_ |  |
| `shape_fill.color` | _String_ | Cor no formato hexadecimal (RGBA) |
| `shape_fill.margin.top` | _Number_ | `0 ~ 100` |
| `shape_fill.margin.right` | _Number_ | `0 ~ 100` |
| `shape_fill.margin.bottom` | _Number_ | `0 ~ 100` |
| `shape_fill.margin.left` | _Number_ | `0 ~ 100` |
| `shape_fill.corner` | _Number_ | `0 ~ 100` |
| <br>**shape_outline** |  | <br>Contorno |
| `shape_outline.type` | _String_ | `box`  `line`  `line_fill`  `theme_margin` |
| `shape_outline.enabled` | _Boolean_ |  |
| `shape_outline.color` | _String_ | Cor no formato hexadecimal (RGBA) |
| `shape_outline.outline_thickness` | _Number_ | `0 ~ 25` |
| `shape_outline.margin.top` | _Number_ | `0 ~ 100` |
| `shape_outline.margin.right` | _Number_ | `0 ~ 100` |
| `shape_outline.margin.bottom` | _Number_ | `0 ~ 100` |
| `shape_outline.margin.left` | _Number_ | `0 ~ 100` |
| `shape_outline.corner` | _Number_ | `0 ~ 100` |
| <br>**comment** |  | <br>Comentário |
| `comment.font_name` | _String_ | Nome da fonte |
| `comment.bold` | _Boolean_ | Negrito |
| `comment.italic` | _Boolean_ | Itálico |
| `comment.relative_size` | _Number_ | tamanho relativo da fonte. `40 ~ 100` |
| `comment.color` | _String_ | Cor no formato hexadecimal |
| <br>**settings** |  | <br>Configurações |
| `settings.uppercase` | _Boolean_ | Exibir o texto em maiúsculo |
| `settings.line_break` | _String_ | Aplicar quebra de linha. `system`  `true`  `false`<br> `Padrão: system` |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "id": "123",
  "name": "",
  "background": {
    "type": "color", "id": "212121", "opacity": 100
  },
  "base_color": "FFFFFF",
  "font": {
    "name": "Arial", "bold": false,
    "italic": false,
    "size": 10.0,
    "color": "F5F5F5", "line_spacing": 0.3,
    "char_spacing": 0
  },
  "align": {
    "horizontal": "center", "vertical": "middle", "margin": {
      "top": 3.0,
      "right": 3.0,
      "bottom": 3.0,
      "left": 3.0
    }
  },
  "effect": {
    "outline_color": "404040", "outline_weight": 0.0,
    "brightness_color": "C0C0C0", "brightness_weight": 0.0,
    "shadow_color": "404040", "shadow_x_weight": 0.0,
    "shadow_y_weight": 0.0,
    "blur": true
  },
  "shape_fill": {
    "type": "box", "enabled": false,
    "color": "000000", "margin": {
      "top": 5.0,
      "right": 30.0,
      "bottom": 10.0,
      "left": 30.0
    },
    "corner": 0
  },
  "shape_outline": {
    "type": "box", "enabled": false,
    "color": "000000", "outline_thickness": 10,
    "margin": {
      "top": 5.0,
      "right": 30.0,
      "bottom": 10.0,
      "left": 30.0
    },
    "corner": 0
  },
  "comment": {
    "font_name": "Arial", "bold": false,
    "italic": true,
    "relative_size": 100,
    "color": "A0A0A0"
  },
  "settings": {
    "uppercase": false,
    "line_break": "system"
  }
}
```
</details>

## Background
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `type` | _String_ | Tipo do item. Pode ser: `theme` `my_video` `my_image` `video` `image` |
| `name` | _String_ | Nome do item |
| `tags` | _Array&lt;String&gt;_ | Lista de tags do item |
| `bpm` | _Number_ | Valor BPM do item |
| `midi` | _[Midi](#midi) (opcional)_ | Atalho MIDI do item |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "id": "10",
  "type": "video",
  "name": "Hexagons",
  "tags": [],
  "bpm": 0.0
}
```
</details>

## Slide Description
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do item |
| `tag` | _String_ | Nome curto do item |
| `aliases` | _Array&lt;String&gt;_ | Lista com os nomes alternativos |
| `font_color` | _String_ | Cor da fonte no formato hexadecimal |
| `bg_color` | _String_ | Cor de fundo no formato hexadecimal |
| `background` | _Number_ | ID do plano de fundo personalizado |
| `midi` | _[Midi](#midi) (opcional)_ | Atalho MIDI do item |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "name": "Chorus",
  "tag": "C",
  "aliases": [],
  "font_color": "FFFFFF",
  "bg_color": "000080",
  "background": null,
  "midi": null
}
```
</details>

## Item
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `type` | _String_ | Tipo do item. Pode ser: `title`  `song`  `verse`  `text`  `audio`  `video`  `image`  `file`  `announcement`  `automatic_presentation`  `countdown`  `countdown_cp`  `cp_text`  `plain_text`  `uri`  `global_action`  `api`  `script` |
| `name` | _String_ | Nome do item |

## Group
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do item |
| `songs` | _Array&lt;Number&gt;_ | Lista dos IDs das músicas |

## Announcement
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |
| `text` | _String_ | Texto do anúncio |
| `archived` | _Boolean_ | Se o item está arquivado |

## Midi
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `code` | _Number_ | Código midi |
| `velocity` | _Number_ | Velocidade/intensidade midi |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "code": 80,
  "velocity": 20
}
```
</details>

## Favorite Item
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |

## Service
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do item |
| `week` | _String_ | Semana. Pode ser: `all` `first` `second` `third` `fourth` `last` |
| `day` | _String_ | Dia da semana. Pode ser: `sun` `mon` `tue` `wed` `thu` `fri` `sat` |
| `hour` | _Number_ | Hora [0-23] |
| `minute` | _Number_ | Minuto [0-59] |
| `type` | _String_ | Tipo do item. Pode ser: `service` `event` |
| `hide_week` | _Array&lt;String&gt;_ | Lista com as semanas ocultadas. Disponível se `week=all` |

## Event
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do evento |
| `datetime` | _String_ | Data e hora no formato: YYYY-MM-DD HH:MM |
| `wallpaper` | _String_ | Caminho relativo do arquivo utilizado como papel de parede do evento |

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
| `notes` | _String_ | Anotações `v2.21.0+` |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "temporary",
  "name": "",
  "datetime": "2024-01-16 20:00",
  "lyrics_playlist": [
    {
      "id": 1,
      "title": "Title 1",
      "artist": "",
      "author": "",
      "...": ".."
    },
    {
      "id": 2,
      "title": "Title 2",
      "artist": "",
      "author": "",
      "...": ".."
    },
    {
      "id": 3,
      "title": "Title 3",
      "artist": "",
      "author": "",
      "...": ".."
    }
  ],
  "media_playlist": [
    {
      "id": "a",
      "type": "video",
      "name": "file.mp4"
    },
    {
      "id": "b",
      "type": "audio",
      "name": "file.mp3"
    },
    {
      "id": "c",
      "type": "image",
      "name": "file.jpg"
    }
  ],
  "responsible": null,
  "members": [],
  "roles": [],
  "notes": ""
}
```
</details>

## Team
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |
| `description` | _String_ | Descrição do item |

## Member
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |
| `skills` | _String_ | Habilidades |
| `roles` | _Array&lt;[Role](#role)&gt;_ | Funções |

## Role
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `name` | _String_ | Nome do item |
| `team` | _[Team](#team)_ | Time |

## Automatic Presentation
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `name` | _String_ | Nome do item |
| `duration` | _Number_ | Duração em milissegundos |
| `starts_with` | _String_ | Valores aceitos: `title` `blank` |
| `song` | _[Lyrics](#lyrics)_ |  |
| `timeline` | _Array&lt;Object&gt;_ | Informação sobre início e duração de cada slide da apresentação |
| `timeline.*.number` | _Number_ | number >= 0 |
| `timeline.*.start` | _Number_ | Tempo inicial da apresentação em milissegundos |
| `timeline.*.end` | _Number_ | Tempo final da apresentação em milissegundos |
| `timeline.*.duration` | _Number_ | Duração em milissegundos |

## Automatic
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `seconds` | _Number_ | Tempo que cada item ficará sendo apresentado |
| `repeat` | _Boolean_ | **true** para ficar repetindo a apresentação (voltar para o primeiro item após o último) |

## Presentation Slide Info
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `number` | _Number_ | Número do slide (começa em 1) |
| `text` | _String_ | Texto do slide |
| `theme_id` | _String_ | ID do tema do slide |
| `slide_description` | _String (opcional)_ | Nome da descrição do slide. Disponível se for uma apresentação de música. |
| `preview` | _String (opcional)_ | Imagem no formato base64 |

## Input Param
[documentação](https://github.com/holyrics/Scripts/blob/main/InputParam.md)


## Trigger Item
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String (opcional)_ | ID do item |
| `when` | _String_ | `displaying` `closing` `change` `event` |
| `item` | _String_ | Tipo do item. Pode ser:<br>**when=displaying**: `any_song` `any_text` `any_verse` `any_announcement` `any_audio` `any_video` `any_image` `any_automatic_presentation` `any_song_slide` `any_text_slide` `any_ppt_slide` `any_theme` `any_background` `any_title_subitem` `any_webcam` `any_audio_folder` `any_video_folder` `any_image_folder` `any_ppt` `any_countdown` `any_automatic_presentation_slide` `f8` `f9` `f10`<br><br>**when=closing**: `any_song` `any_text` `any_verse` `any_announcement` `any_audio` `any_video` `any_image` `any_automatic_presentation` `any_webcam` `any_audio_folder` `any_video_folder` `any_image_folder` `any_ppt` `f8` `f9` `f10`<br><br>**when=change**: `countdown_seconds_public` `countdown_seconds_communication_panel` `timer_seconds_communication_panel` `wallpaper` `wallpaper_service` `stage` `playlist` `bpm` `hue`<br><br>**when=event**: `new_message_chat` |
| `action` | _Function_ | Ação que será executada |
<details>
  <summary>Ver exemplo</summary>

```javascript
{
  "id": "",
  "when": "displaying",
  "item": "any_song",
  "action": function(obj) { /* TODO */ },
  "name": "name"
}
```
</details>

## Play Media Settings
Configurações para execução da mídia

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `volume` | _Number_ | Altera o volume do player |
| `repeat` | _Boolean_ | Altera a opção **repetir** |
| `shuffle` | _Boolean_ | Altera a opção **aleatório** |
| `start_time` | _String_ | Tempo inicial para execução no formato SS, MM:SS ou HH:MM:SS |
| `stop_time` | _String_ | Tempo final para execução no formato SS, MM:SS ou HH:MM:SS |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "volume": "80",
  "repeat": true,
  "shuffle": false,
  "start_time": "00:30",
  "stop_time": "02:00"
}
```
</details>

## Display Settings
Configurações de exibição

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item. `public` `screen_2` `screen_3` `screen_?` `stream_image` `stream_html_1` `stream_html_2` `stream_html_3` |
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
<details>
  <summary>Ver exemplo</summary>

```json
{
  "id": "public",
  "name": "Público",
  "slide_info": {
    "info_1": {
      "show_page_count": false,
      "show_slide_description": false,
      "horizontal_align": "right",
      "vertical_align": "bottom"
    },
    "info_2": {
      "show": false,
      "layout_row_1": "<title>< (%author_or_artist%)>",
      "horizontal_align": "right",
      "vertical_align": "bottom"
    },
    "font": {
      "name": null,
      "bold": null,
      "italic": null,
      "color": null
    },
    "height": 7,
    "paint_theme_effect": true
  },
  "slide_translation": null,
  "margin": {
    "top": 0.0,
    "right": 0.0,
    "bottom": 0.0,
    "left": 0.0
  },
  "area": {
    "x": 0,
    "y": 0,
    "width": 0,
    "height": 0
  },
  "total_area": {
    "x": 0,
    "y": 0,
    "width": 0,
    "height": 0
  },
  "hide": false,
  "media_player": {
    "margin": {
      "top": 0.0,
      "right": 0.0,
      "bottom": 0.0,
      "left": 0.0
    },
    "area": {
      "x": 0,
      "y": 0,
      "width": 0,
      "height": 0
    }
  }
}
```
</details>

## Transition Effect Settings
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | Tipo de efeito. Pode ser: `random` `fade` `slide` `accordion` `linear_fade` `zoom` `curtain` |
| `enabled` | _Boolean_ | Se está ativado ou desativado |
| `duration` | _Number_ | Duração total da transição (em milissegundos) `200 ~ 2400` |
| `only_area_within_margin` | _Number_ | Realiza o efeito de transição apenas dentro da margem definida no Tema. (Disponível somente para transição de texto) |
| <br>**type=fade** |  |  |
| `merge` | _Object_ | Valores aceitos: true,&nbsp;false |
| `division_point` | _Object_ | Valores aceitos: min:&nbsp;10,&nbsp;max:&nbsp;100 |
| `increase_duration_blank_slides` | _Object_ | Valores aceitos: true,&nbsp;false |
| <br>**type=slide** |  |  |
| `direction` | _Object_ | Valores aceitos: random,&nbsp;left,&nbsp;up |
| `slide_move_type` | _Object_ | Valores aceitos: random,&nbsp;move_new,&nbsp;move_old,&nbsp;move_both |
| <br>**type=accordion** |  |  |
| `direction` | _Object_ | Valores aceitos: random,&nbsp;horizontal,&nbsp;vertical |
| <br>**type=linear_fade** |  |  |
| `direction` | _Object_ | Valores aceitos: random,&nbsp;horizontal,&nbsp;vertical,&nbsp;up,&nbsp;down,&nbsp;left,&nbsp;right |
| `distance` | _Object_ | Valores aceitos: min:&nbsp;5,&nbsp;max:&nbsp;90 |
| `fade` | _Object_ | Valores aceitos: min:&nbsp;2,&nbsp;max:&nbsp;90 |
| <br>**type=zoom** |  |  |
| `zoom_type` | _Object_ | Valores aceitos: random,&nbsp;increase,&nbsp;decrease |
| `directions` | _Object_ | Valores aceitos: {<br>&nbsp;&nbsp;top_left:&nbsp;boolean,<br>&nbsp;&nbsp;top_center:&nbsp;boolean,<br>&nbsp;&nbsp;top_right:&nbsp;boolean,<br>&nbsp;&nbsp;middle_left:&nbsp;boolean,<br>&nbsp;&nbsp;middle_center:&nbsp;boolean,<br>&nbsp;&nbsp;middle_right:&nbsp;boolean,<br>&nbsp;&nbsp;bottom_left:&nbsp;boolean,<br>&nbsp;&nbsp;bottom_center:&nbsp;boolean,<br>&nbsp;&nbsp;bottom_right:&nbsp;boolean<br>} |
| <br>**type=curtain** |  |  |
| `direction` | _Object_ | Valores aceitos: random,&nbsp;horizontal,&nbsp;vertical |
| `direction_lines` | _Object_ | Valores aceitos: random,&nbsp;down_right,&nbsp;up_left,&nbsp;alternate |
| `slide_move_type` | _Object_ | Valores aceitos: random,&nbsp;new,&nbsp;old,&nbsp;both |
| <br>**type=random** |  |  |
| `random_enabled_types` | _Object_ | Valores aceitos: {<br>&nbsp;&nbsp;fade:&nbsp;boolean,<br>&nbsp;&nbsp;slide:&nbsp;boolean,<br>&nbsp;&nbsp;accordion:&nbsp;boolean,<br>&nbsp;&nbsp;linear_fade:&nbsp;boolean,<br>&nbsp;&nbsp;zoom:&nbsp;boolean,<br>&nbsp;&nbsp;curtain:&nbsp;boolean<br>} |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "enabled": true,
  "type": "fade",
  "duration": 500,
  "only_area_within_margin": false,
  "merge": false,
  "division_point": 30,
  "increase_duration_blank_slides": false
}
```
</details>

## Bible Settings
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `tab_version_1` | _String_ | Versão da Bíblia definida na primeira aba |
| `tab_version_2` | _String_ | Versão da Bíblia definida na segunda aba |
| `tab_version_3` | _String_ | Versão da Bíblia definida na terceira aba |
| `show_x_verses` | _Number_ | Quantidade de versículos exibidos na projeção |
| `uppercase` | _Boolean_ | Exibir o texto do versículo em maiúsculo |
| `show_only_reference` | _Boolean_ | Exibir somente a referência do versículo |
| `show_two_versions` | _Boolean_ | `deprecated` Substituído por: `show_second_version` `show_third_version`<br>Exibir duas versões. |
| `show_second_version` | _Boolean_ | Exibir segunda versão `v2.22.0+` |
| `show_third_version` | _Boolean_ | Exibir terceira versão `v2.22.0+` |
| `book_panel_type` | _String_ | Tipo de visualização dos livros da Bíblia `grid` `list` |
| `book_panel_order` | _String_ | Tipo de ordenação dos livros da Bíblia |
| `book_panel_order_available_items` | _Array&lt;String&gt;_ |  |
| `multiple_verses_separator_type` | _String_ | Tipo de separação na exibição de múltiplos versículos. Pode ser: no_line_break, single_line_break, double_line_break |
| `multiple_versions_separator_type` | _String_ | Tipo de separação na exibição de múltiplas versões. Pode ser: no_line_break, single_line_break, double_line_break `v2.22.0+` |
| `versification` | _Boolean_ | Aplicar mapeamento de versículos |
| `theme` | _Object_ | ID do Tema de exibição para as diferentes telas do sistema |
| `theme.public` | _String_ |  |
| `theme.screen_n` | _String_ | n >= 2 |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "tab_version_1": "pt_???",
  "tab_version_2": "es_???",
  "tab_version_3": "en_???",
  "show_x_verses": 1,
  "uppercase": false,
  "show_only_reference": false,
  "show_two_versions": false,
  "show_second_version": false,
  "show_third_version": false,
  "book_panel_type": "grid",
  "book_panel_order": "automatic",
  "book_panel_order_available_items": [
    "automatic", "standard", "ru", "tyv"
  ],
  "multiple_verses_separator_type": "double_line_break",
  "multiple_versions_separator_type": "double_line_break",
  "versification": true,
  "theme": {
    "public": 123,
    "screen_n": null
  }
}
```
</details>

## Font Settings
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `font_name` | _String (opcional)_ | Nome da fonte `Padrão: null` |
| `bold` | _Boolean (opcional)_ | Negrito `Padrão: null` |
| `italic` | _Boolean (opcional)_ | Itálico `Padrão: null` |
| `color` | _String (opcional)_ | Cor em hexadecimal `Padrão: null` |

## Stage View
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `enabled` | _Boolean_ | Visão do palco ativada |
| `preview_mode` | _String_ | Modo de visualização das letras. Opções disponíveis:<br/>`CURRENT_SLIDE`<br/>`FIRST_LINE_OF_THE_NEXT_SLIDE_WITH_SEPARATOR`<br/>`FIRST_LINE_OF_THE_NEXT_SLIDE_WITHOUT_SEPARATOR`<br/>`NEXT_SLIDE`<br/>`CURRENT_AND_NEXT_SLIDE`<br/>`ALL_SLIDES` |
| `uppercase` | _Boolean_ | Exibir em maiúsculo |
| `remove_line_break` | _Boolean_ | Remover quebra de linha |
| `show_comment` | _Boolean_ | Exibir comentários |
| `show_advanced_editor` | _Boolean_ | Exibir edições avançadas |
| `show_communication_panel` | _Boolean_ | Exibir conteúdo do painel de comunicação |
| `show_next_image` | _Boolean_ | Exibir imagem seguinte `v2.21.0+` |
| `custom_theme` | _Number_ | ID do tema personalizado utilizado nas apresentações |
| `apply_custom_theme_to_bible` | _Boolean_ | Utilizar o tema personalizado nos versículos |
| `apply_custom_theme_to_text` | _Boolean_ | Utilizar o tema personalizado nos textos |
| `apply_custom_theme_to_quick_presentation` | _Boolean_ | Utilizar o tema personalizado na opção **Apresentação Rápida** `v2.21.0+` |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "enabled": false,
  "preview_mode": "FIRST_LINE_OF_THE_NEXT_SLIDE_WITH_SEPARATOR",
  "uppercase": false,
  "remove_line_break": false,
  "show_comment": true,
  "show_advanced_editor": false,
  "show_communication_panel": true,
  "show_next_image": false,
  "custom_theme": null,
  "apply_custom_theme_to_bible": true,
  "apply_custom_theme_to_text": true,
  "apply_custom_theme_to_quick_presentation": false
}
```
</details>

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
| `height` | _Number_ | Altura em porcentagem em relação à altura do slide `4 ~ 15` |
| `paint_theme_effect` | _String_ | Renderizar o texto com os efeitos contorno, brilho e sombra do tema, se disponível |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "info_1": {
    "show_page_count": false,
    "show_slide_description": false,
    "horizontal_align": "right", "vertical_align": "bottom"
  },
  "info_2": {
    "show": false,
    "layout_row_1": "<title>< (%author_or_artist%)>", "horizontal_align": "right", "vertical_align": "bottom"
  },
  "font": {
    "name": null,
    "bold": null,
    "italic": null,
    "color": null
  },
  "height": 7,
  "paint_theme_effect": true
}
```
</details>

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
<details>
  <summary>Ver exemplo</summary>

```json
{
  "id": "123",
  "name": "Chamar pessoa",
  "message_model": "   , favor comparecer  .",
  "message_example": "função nome, favor comparecer local.",
  "variables": [
    {
      "position": 0,
      "name": "função",
      "only_number": false,
      "uppercase": false,
      "suggestions": [
        "Diácono",
        "Presbítero",
        "Pastor",
        "Professor",
        "Ministro"
      ]
    },
    {
      "position": 2,
      "name": "nome",
      "only_number": false,
      "uppercase": false,
      "suggestions": []
    },
    {
      "position": 22,
      "name": "local",
      "only_number": false,
      "uppercase": false,
      "suggestions": [
        "ao estacionamento",
        "ao hall de entrada",
        "à mesa de som",
        "ao berçário"
      ]
    }
  ]
}
```
</details>

## Custom Message Param
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `position` | _Number_ | Posição do parâmetro na mensagem (em número de caracteres) |
| `name` | _String_ | Nome do item |
| `only_number` | _Boolean_ | Parâmetro aceita somente números |
| `uppercase` | _Boolean_ | Parâmetro exibido sempre em maiúsculo |
| `suggestions` | _Array&lt;String&gt; (opcional)_ | Lista com valores padrões para o parâmetro |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "position": 0,
  "name": "",
  "only_number": false,
  "uppercase": false,
  "suggestions": []
}
```
</details>

## Quiz Question
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `title` | _String_ | Pergunta |
| `alternatives` | _Array&lt;String&gt;_ | Alternativas |
| `correct_alternative_number` | _Number (opcional)_ | Número da alternativa correta. Começa em 1 `Padrão: 1` |
| `source` | _String (opcional)_ | Fonte da resposta |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "title": "...",
  "alternatives": [
    "Item 1", "Item 2", "Item 3"
  ],
  "correct_alternative_number": 2,
  "source": ""
}
```
</details>

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
<details>
  <summary>Ver exemplo</summary>

```json
{
  "correct_answer_color_font": "00796B",
  "correct_answer_color_background": "CCFFCC",
  "incorrect_answer_color_font": "721C24",
  "incorrect_answer_color_background": "F7D7DB",
  "question_and_alternatives_different_slides": false,
  "display_alternatives_one_by_one": true,
  "alternative_separator_char": ".",
  "alternative_char_type": "alpha"
}
```
</details>

## Quick Presentation Slide
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `text` | _String_ | Texto do slide |
| `theme` | _[ThemeFilter](#theme-filter) (opcional)_ | Filtrar tema selecionado para exibição |
| `custom_theme` | _[Theme](#theme) (opcional)_ | Tema personalizado utilizado para exibir o texto |
| `translations` | _[Translations](#translations) (opcional)_ |  |
| `duration` | _Number (opcional)_ | Duração do slide para uso em apresentações automáticas |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "text": "text",
  "duration": 3,
  "translations": {
    "key1": "value1", "key2": "value2"
  },
  "theme": {
    "name": "...", "edit": {
      "font": {
        "name": "Arial",
        "size": 10,
        "bold": true,
        "color": "FFFFFF"
      },
      "background": {
        "type": "color",
        "id": "000000"
      }
    }
  }
}
```
</details>

## Theme Filter
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String (opcional)_ | ID do tema ou plano de fundo |
| `name` | _String (opcional)_ | Nome do tema ou plano de fundo |
| `edit` | _[Theme](#theme) (opcional)_ | Configurações para modificar o Tema selecionado para exibição |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "name": "...",
  "edit": {
    "font": {
      "name": "Arial",
      "size": 10,
      "bold": true,
      "color": "FFFFFF"
    },
    "background": {
      "type": "color",
      "id": "000000"
    }
  }
}
```
</details>

## Translations
Conjunto chave/valor

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `???` | _String_ | Valor traduzido do item, onde o nome do parâmetro `???` é o nome da tradução |
| `???` | _String_ |  |
| `...` | _String_ |  |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "key1": "value1",
  "key2": "value2"
}
```
</details>

## Wallpaper Settings
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `enabled` | _Boolean_ | Exibir papel de parede |
| `fill_color` | _String_ | Cor em hexadecimal definida na opção **preencher**. |
| `clock` | _[ClockSettings](#clock-settings)_ | Configurações do relógio |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "enabled": null,
  "fill_color": null,
  "clock": {
    "enabled": false,
    "font_name": "", "bold": false,
    "italic": false,
    "color": "FF0000", "background": "000000", "height": 12,
    "position": "top_right", "corner": 0
  }
}
```
</details>

## Clock Settings
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `enabled` | _Boolean_ |  |
| `font_name` | _String_ | Nome da fonte |
| `bold` | _Boolean_ | Negrito |
| `italic` | _Boolean_ | Itálico |
| `color` | _String_ | Cor no formato hexadecimal (RGBA) |
| `background` | _String_ | Cor no formato hexadecimal (RGBA) |
| `height` | _Number_ | Valor em porcentagem baseado na altura da linha.<br>Valores aceitos: `6` `7` `8` `9` `10` `12` `14` `15` `16` `18` `20` `25` `30` `35` `40` |
| `position` | _Boolean_ | Valores aceitos: `top_left` `top_center` `top_right` `middle_left` `middle_center` `middle_right` `bottom_left` `bottom_center` `bottom_right` |
| `corner` | _Number_ | `0 ~ 100` |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "enabled": false,
  "font_name": "",
  "bold": false,
  "italic": false,
  "color": "FF0000",
  "background": "000000",
  "height": 12,
  "position": "top_right",
  "corner": 0
}
```
</details>

## Bible Book List
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ |  |
| `name` | _String_ |  |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "id": "en",
  "name": "English"
}
```
</details>

## Bible Book Info
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do livro `01 ~ 66` |
| `name` | _String_ | Nome do livro |
| `abbrev` | _String_ | Abreviação do livro |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "id": "01",
  "name": "Genesis",
  "abbrev": "Gn"
}
```
</details>

## Verse Reference Group
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `reference` | _String_ | Referências. Exemplo: **João 3:16** ou **Rm 12:2** ou **Gn 1:1-3 Sl 23.1** |
| `ids` | _Array&lt;String&gt;_ | Exemplo:  ['19023001', '43003016', '45012002'] |
| `verses` | _Array&lt;[VerseReference](#verse-reference)&gt;_ | Lista detalhada das referências |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "reference": "Ps 23.1-2",
  "ids": [
    "19023001", "19023002"
  ],
  "verses": [
    {
      "id": "19023001",
      "book": 19,
      "chapter": 23,
      "verse": 1,
      "reference": "Psalms 23.1"
    },
    {
      "id": "19023002",
      "book": 19,
      "chapter": 23,
      "verse": 2,
      "reference": "Psalms 23.2"
    }
  ]
}
```
</details>

## Verse Reference
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `id` | _String_ | ID do item |
| `book` | _Number_ | ID do livro `1 ~ 66` |
| `chapter` | _Number_ | Capítulo |
| `verse` | _Number_ | Versículo |
| `reference` | _String_ |  |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "id": "19023001",
  "book": 19,
  "chapter": 23,
  "verse": 1,
  "reference": "Psalms 23.1"
}
```
</details>

## AddItem
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | Tipo do item. Pode ser: `title`  `song`  `verse`  `text`  `audio`  `video`  `image`  `file`  `announcement`  `automatic_presentation`  `countdown`  `countdown_cp`  `cp_text`  `plain_text`  `uri`  `global_action`  `api`  `script` |

## AddItemTitle
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | title |
| `name` | _String_ | Nome do item |
| `background_color` | _String (opcional)_ | Cor de fundo em hexadecimal, exemplo: 000080 |
| `collapsed` | _Boolean (opcional)_ |  `Padrão: false` |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "title",
  "name": "Exemplo",
  "background_color": "0000FF",
  "collapsed": false
}
```
</details>

## AddItemSong
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | song |
| `id` | _String_ | ID do item |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "song",
  "id": "123"
}
```
</details>

## AddItemVerse
**id**, **ids** ou **references**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | verse |
| `id` | _String (opcional)_ | Para exibir um versículo. ID do item no formato LLCCCVVV.<br/>Exemplo: '19023001' (livro 19, capítulo 023, versículo 001) |
| `ids` | _Array&lt;String&gt; (opcional)_ | Para exibir uma lista de versículos. Lista com o ID de cada versículo.<br/>Exemplo: ['19023001', '43003016', '45012002'] |
| `references` | _String (opcional)_ | Referências. Exemplo: **João 3:16** ou **Rm 12:2** ou **Gn 1:1-3 Sl 23.1** |
| `version` | _String (opcional)_ | Nome ou abreviação da tradução utilizada `v2.21.0+` |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "verse",
  "references": "Ps 23.1-6 Rm 12.2",
  "version": "en_kjv"
}
```
</details>

## AddItemText
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | text |
| `id` | _String_ | ID do item |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "text",
  "id": "xyz"
}
```
</details>

## AddItemAudio
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | audio |
| `name` | _String_ | Nome do arquivo |
| `settings` | _[PlayMediaSettings](#play-media-settings) (opcional)_ | Configurações para execução da mídia `v2.21.0+` |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "id": "",
  "type": "audio",
  "name": "file.mp3",
  "isDir": false
}
```
</details>

## AddItemVideo
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | video |
| `name` | _String_ | Nome do arquivo |
| `settings` | _[PlayMediaSettings](#play-media-settings) (opcional)_ | Configurações para execução da mídia `v2.21.0+` |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "id": "",
  "type": "video",
  "name": "file.mp4",
  "isDir": false
}
```
</details>

## AddItemImage
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | image |
| `name` | _String_ | Nome do arquivo |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "image",
  "name": "file.ext"
}
```
</details>

## AddItemAutomaticPresentation
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | automatic_presentation |
| `name` | _String_ | Nome do arquivo |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "automatic_presentation",
  "name": "filename.ap"
}
```
</details>

## AddItemAnnouncement
**id**, **ids**, **name** ou **names**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | announcement |
| `id` | _String (opcional)_ | ID do anúncio. Pode ser **all** para exibir todos |
| `ids` | _Array&lt;String&gt; (opcional)_ | Lista com o ID de cada anúncio |
| `name` | _String (opcional)_ | Nome do anúncio |
| `names` | _Array&lt;String&gt; (opcional)_ | Lista com o nome de cada anúncio |
| `automatic` | _[Automatic](#automatic) (opcional)_ | Se informado, a apresentação dos itens será automática |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "announcement",
  "names": [
    "Anúncio 1", "Anúncio 2", "Anúncio 3"
  ],
  "automatic": {
    "seconds": 10,
    "repeat": true
  }
}
```
</details>

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
| `theme` | _String (opcional)_ | ID do Tema `v2.21.0+` |
| `countdown_style` | _[FontSettings](#font-settings) (opcional)_ | Fonte personalizada para a contagem regressiva `v2.21.0+` |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "countdown",
  "time": "05:00",
  "exact_time": false,
  "text_before": "",
  "text_after": "",
  "zero_fill": false,
  "countdown_relative_size": 250,
  "theme": null,
  "countdown_style": {
    "font_name": null,
    "bold": null,
    "italic": true,
    "color": null
  }
}
```
</details>

## AddItemCountdownCommunicationPanel
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | countdown_cp |
| `minutes` | _Number_ | Quantidade de minutos |
| `seconds` | _Number_ | Quantidade de segundos |
| `stop_at_zero` | _Boolean (opcional)_ | Parar a contagem regressiva ao chegar em zero `Padrão: false` |
| `description` | _String_ | Descrição do item |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "countdown_cp",
  "minutes": 5,
  "seconds": 0,
  "stop_at_zero": false,
  "description": ""
}
```
</details>

## AddItemTextCommunicationPanel
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | cp_text |
| `name` | _String_ | Nome do item |
| `text` | _String_ | Texto |
| `display_ahead` | _Boolean (opcional)_ | Alterar a opção *'exibir à frente de tudo'* |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "cp_text",
  "name": "",
  "text": "Exemplo",
  "display_ahead": false
}
```
</details>

## AddItemAddItemScript
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | script |
| `id` | _String_ | ID do item |
| `description` | _String_ | Descrição do item |
| `inputs` | _Object (opcional)_ | Valor padrão para [Function Input](https://github.com/holyrics/Scripts/blob/main/FunctionInput.md) |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "script",
  "id": "xyz",
  "description": "",
  "inputs": {
    "message": "Exemplo", "duration": 30
  }
}
```
</details>

## AddItemAddItemAPI
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | api |
| `id` | _String_ | ID do item |
| `description` | _String_ | Descrição do item |
| `inputs` | _Object (opcional)_ | Valor padrão para [Function Input](https://github.com/holyrics/Scripts/blob/main/FunctionInput.md) |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "api",
  "id": "xyz",
  "description": "",
  "inputs": {
    "message": "Exemplo", "duration": 30
  }
}
```
</details>

## AddItemURI
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | uri |
| `title` | _String_ | Título do item |
| `uri_type` | _String_ | Pode ser: `spotify` `youtube` `deezer` |
| `value` | _String_ | URI |
<details>
  <summary>Ver exemplo</summary>

```json
{
  "type": "uri",
  "title": "Holyrics",
  "uri_type": "youtube",
  "value": "https://youtube.com/watch?v=umYQpAxL4dI"
}
```
</details>

## AddItemGlobalAction
| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `type` | _String_ | global_action |
| `action` | _String_ | Pode ser: `slide_exit` `vlc_stop` `vlc_stop_fade_out` |

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
Para exibir um texto com formatação avançada, inicie o texto com **<styled>**

Tags HTML disponíveis

```html
<styled>
<b>negrito</b>
<i>itálico</i>
<u>sublinhado</u>
<color:0000FF>Cor da fonte</color>
<font:Arial>Nome da fonte</font>
<size:70>Tamanho relativo da fonte 70%</size>

A partir da v2.23.0
<line-height:100>Altura da linha</line-height>
<valign:0>Alinhamento vertical  -200 ~ 200  </valign>
<bgcolor:000000>Cor de fundo</bgcolor>
<brightness-color:000000>Cor do brilho</brightness-color>
<brightness-weight:50>  0 ~ 100  </brightness-weight>
<outline-color:000000>Cor do contorno</outline-color>
<outline-weight:50>  0 ~ 100  </outline-weight>
<shadow-color:000000>Cor da sombra</shadow-color>
<shadow-x-weight:50>  -100 ~ 100  </shadow-x-weight>
<shadow-y-weight:-50>  -100 ~ 100  </shadow-y-weight>
<blur>Aplicar efeito blur</blur>
```
