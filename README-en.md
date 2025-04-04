# jslib
**EN** | [PT](README.md)

JSLib class methods available for use in Holyrics program scripts.<br>

You can use the ```jslib``` variable or the ```h``` variable to access the available methods.

For example:
```javascript
jslib.log('Example');
h.log('Example');
```

## JSCommunity

To use the [JSCommunity](https://github.com/holyrics/JSCommunity/blob/main/README-en.md) library, use the `jsc` variable.<br>

For example:
```javascript
var r = jsc.utils.n3(5);
// r: 005
```

## ECMAScript - ECMA-262 Edition 5.1

Although the `ECMA-262 Edition 5.1` standard is used for creating JavaScript code in the program, some conveniences were added in `v2.23.0` of Holyrics.

### Arrow Function

Compatibility for creating code using **Arrow Function** syntax.<br>
The program converts the code in real-time, transforming **Arrow Function** into **Anonymous Function**.

For example:
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

Utility classes

For example:
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

### Shortcut keys in the code editing window

| Tecla de Atalho | Descrição |
| ----: | ------------ |
| `Ctrl + Space` | Displays a submenu in the editing window with code suggestions based on the current cursor location |
| `Ctrl + Shift + Up` | Duplicate line(s) up |
| `Ctrl + Shift + Down` | Duplicate line(s) down |
| `Ctrl + F` | Find |
| `Ctrl + H` | Replace |
| `Alt + Up` | Navigate to the previous occurrence |
| `Alt + Down` | Navigate to the next occurrence |
| `Ctrl + Alt + Up` | Highlight previous occurrence without moving the cursor `v2.24.0+` |
| `Ctrl + Alt + Down` | Highlight next occurrence without moving the cursor `v2.24.0+` |
| `Ctrl + B` | Go to declaration __(or mouse scroll button)__ `v2.24.0+` |
| `Ctrl + Tab` | Navigate to the next tab `v2.24.0+` |
| `Ctrl + Shift + Tab` | Navigate to the previous tab `v2.24.0+` |

`Tab`<br>
Code templates can be created for automatic insertion in the code editing window after pressing the `Tab` key.<br>
For example, pressing `Tab` after the word `for`, the following code template will be inserted in place.
```javascript
for (var i = 0; i < /* cursor */; i++) {
    
}
```

Right-click in the code editing window (context menu), option **Expand with TAB**


---

# Methods and variables available in the jslib library

- [General](#general)
  - [global](#global)
  - [storage](#storage)
  - [files](#files)
  - [uri](#uri)
  - [image](#image)
  - [stream](#stream)
  - [local](#local)
  - [globalSettings](#globalsettings)
  - [log](#logobj)
  - [log](#logkey--null-obj-args--null)
  - [logf](#logfobj-args--null)
  - [logfp](#logfpobj-args--null)
  - [logp](#logpobj)
  - [log](#logkey--null-obj-args--null)
  - [logt](#logtobj)
  - [log.setEnabled](#logsetenabledkey-enabled)
  - [log.enable](#logenablekey)
  - [log.enableAll](#logenableall)
  - [log.isEnabled](#logisenabledkey)
  - [log.setShowLogKey](#logsetshowlogkeyvalue)
  - [log.isShowLogKey](#logisshowlogkey)
  - [log.toggleEnabled](#logtoggleenabledkey)
  - [sleep](#sleeptime)
  - [base64Encode](#base64encodeinput)
  - [base64Decode](#base64decodestr)
  - [base64DecodeAsString](#base64decodeasstringstr-charset--utf8)
  - [hexEncode](#hexencodeinput)
  - [hexDecode](#hexdecodehex)
  - [hexDecodeAsString](#hexdecodeasstringhex-charset--utf-8)
  - [hexDecodeAsNumber](#hexdecodeasnumberhex)
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
  - [runAt](#runatinput)
  - [cancelRunAt](#cancelrunatid)
  - [getHostname](#gethostname)
  - [getRuntimeEnvironment](#getruntimeenvironment)
  - [setRuntimeEnvironment](#setruntimeenvironmentname)
  - [isRuntimeEnvironment](#isruntimeenvironmentname)
  - [getVersion](#getversion)
  - [isMinimumVersion](#isminimumversionversion)
  - [getDeviceID](#getdeviceid)
  - [getLanguage](#getlanguage)
  - [isLanguage](#islanguagelanguage)
  - [getUITheme](#getuitheme)
  - [isUITheme](#isuithemevalue)
  - [getCommunityVersion](#getcommunityversion)
  - [isMinimumCommunityVersion](#isminimumcommunityversionversion)
  - [getHolyricsPluginVersion](#getholyricspluginversion)
  - [isHolyricsPluginOpened](#isholyricspluginopened)
  - [isHolyricsPluginStarted](#isholyricspluginstarted)
  - [format.secondsToHMS](#formatsecondstohmsseconds-separator--)
  - [format.secondsToMS](#formatsecondstomsseconds-separator--)
  - [format.minutesToHM](#formatminutestohmminutes-separator--)
  - [format.f](#formatfformat-params)
  - [format.rgbToHex](#formatrgbtohexred-green-blue)
  - [format.applyJSHighlightHTML](#formatapplyjshighlighthtmlcode)
  - [date.getSecondOfDay](#dategetsecondofday)
  - [date.getSecondOfDay](#dategetsecondofdayhour-minute-second)
  - [date.toMillis](#datetomillisvalue)
  - [date.getElapsedTime](#dategetelapsedtimeunit-a-b)
  - [date.format](#dateformatformat-date--null)
  - [date.get](#dategetformat--null)
  - [date.parse](#dateparseformat-value)
  - [csvToArray](#csvtoarraycsv)
  - [xmlToJson](#xmltojsonxml)
  - [addTriggerListener](#addtriggerlistenerinput)
  - [removeTriggerListener](#removetriggerlistenerid)
  - [containsTriggerListener](#containstriggerlistenerid)
  - [getTriggerListeners](#gettriggerlisteners)
  - [addSysVar](#addsysvarname-function-cachedelay--null)
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
  - [fixNonspacingMark](#fixnonspacingmarkvalue)
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
  - [process](#processfile-input--null)
  - [executeCmdAndWait](#executecmdandwaitfile-cli--null-timeout--5000)
  - [triggerHotkey](#triggerhotkeyid)
  - [isAllowedExtensionToExecute](#isallowedextensiontoexecuteextension)
  - [isAllowedFileToExecute](#isallowedfiletoexecutefile)
  - [getAvailableFontFamilyNames](#getavailablefontfamilynames)
  - [hlyOrThrow](#hlyorthrowaction-input--null)
- [Methods HLY](#methods-hly)
  - [GetLyrics](#hlygetlyrics-input)
  - [GetSongs](#hlygetsongs-input)
  - [SearchLyrics](#hlysearchlyrics-input)
  - [ShowLyrics](#hlyshowlyrics-input)
  - [GetText](#hlygettext-input)
  - [GetTexts](#hlygettexts-input)
  - [SearchText](#hlysearchtext-input)
  - [ShowText](#hlyshowtext-input)
  - [ShowVerse](#hlyshowverse-input)
  - [GetAudios - GetVideos - GetImages - GetFiles](#hlygetaudios-input)
  - [GetAudio - GetVideo - GetImage - GetFile](#hlygetaudio-input)
  - [SetAudioItemProperty](#hlysetaudioitemproperty-input)
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
  - [GetCurrentSchedule](#hlygetcurrentschedule-input)
  - [GetSchedules](#hlygetschedules-input)
  - [GetSavedPlaylists](#hlygetsavedplaylists)
  - [LoadSavedPlaylist](#hlyloadsavedplaylist-input)
  - [GetHistory](#hlygethistory-input)
  - [GetHistories](#hlygethistories-input)
  - [GetNearestHistory](#hlygetnearesthistory-input)
  - [GetSongGroup](#hlygetsonggroup-input)
  - [GetSongGroups](#hlygetsonggroups)
  - [GetTeams](#hlygetteams)
  - [GetMembers](#hlygetmembers-input)
  - [GetRoles](#hlygetroles-input)
  - [GetServices](#hlygetservices-input)
  - [GetEvents](#hlygetevents-input)
  - [GetAnnouncement](#hlygetannouncement-input)
  - [GetAnnouncements](#hlygetannouncements)
  - [GetCommunicationPanelInfo](#hlygetcommunicationpanelinfo)
  - [SetCommunicationPanelSettings](#hlysetcommunicationpanelsettings-input)
  - [StartCountdownCommunicationPanel](#hlystartcountdowncommunicationpanel-input)
  - [StopCountdownCommunicationPanel](#hlystopcountdowncommunicationpanel)
  - [StartTimerCommunicationPanel](#hlystarttimercommunicationpanel-input)
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
  - [GetRealTimeSongKey](#hlygetrealtimesongkey-input)
  - [SetRealTimeSongKey](#hlysetrealtimesongkey-input)
  - [ActionNextQuickPresentation](#hlyactionnextquickpresentation)
  - [ActionPreviousQuickPresentation](#hlyactionpreviousquickpresentation)
  - [CloseCurrentQuickPresentation](#hlyclosecurrentquickpresentation)
  - [GetCurrentQuickPresentation](#hlygetcurrentquickpresentation)
  - [GetTriggers](#hlygettriggers)
  - [GetGlobalSettings](#hlygetglobalsettings-input)
  - [SetGlobalSettings](#hlysetglobalsettings-input)
  - [GetStyledModels](#hlygetstyledmodels)
  - [GetStyledModelsAsMap](#hlygetstyledmodelsasmap)
  - [CreateItem](#hlycreateitem-input)
  - [EditItem](#hlyedititem-input)
  - [DeleteItem](#hlydeleteitem-input)
  - [AddSongsToSongGroup](#hlyaddsongstosonggroup-input)
  - [RemoveSongsFromSongGroup](#hlyremovesongsfromsonggroup-input)
- [SecurityUtils methods](#securityutils-methods)
  - [encrypt](#encryptvalue)
  - [decrypt](#decryptbase64)
  - [encryptObj](#encryptobjvalue)
  - [decryptObj](#decryptobjbase64)
  - [relativeMethods](#relativemethods)
- [User input Methods](#user-input-methods)
  - [input](#inputparam-notification--false)
  - [settings](#settingssaveto-savetostore-data)
  - [inputTextArea](#inputtextareatitle-notification--false)
  - [itemChooser](#itemchoosertitle-items-notification--false)
  - [multipleItemChooser](#multipleitemchoosertitle-items-notification--false)
  - [confirm](#confirmmsg-title--confirm-notification--false)
  - [yesNo](#yesnomsg-title--confirm-notification--false)
  - [ok](#okmsg-title--confirm-notification--false)
  - [error](#errormsg-notification--false)
  - [notification](#notificationmsg-duration--0)
  - [lyricsChooser](#lyricschooser)
  - [textChooser](#textchooser)
  - [themeChooser](#themechooser)
  - [imageChooser](#imagechooser)
  - [audioChooser](#audiochooser)
  - [videoChooser](#videochooser)
  - [fileChooser](#filechooser)
  - [backgroundChooser](#backgroundchooser)
  - [verseChooser](#versechooser)
  - [openWindow](#openwindowname)
  - [repaint](#repaintid)
  - [popupWorker](#popupworkerinput)
  - [popupCreateSong](#popupcreatesongsong-callback--null)
  - [popupCreateText](#popupcreatetexttext-callback--null)
  - [popupCreateTheme](#popupcreatethemetheme-callback--null)
- [Classes](#classes)
  - [Lyrics](#lyrics)
  - [Text](#text)
  - [Theme](#theme)
  - [Background](#background)
  - [Slide Description](#slide-description)
  - [Item](#item)
  - [Group](#group)
  - [Song Arrangement](#song-arrangement)
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
  - [Translation Custom Settings](#translation-custom-settings)
  - [Translation Custom Settings Item](#translation-custom-settings-item)
  - [Styled Model](#styled-model)
  - [Initial Slide Settings](#initial-slide-settings)
  - [Copyright Settings](#copyright-settings)
  - [Image Presentation Settings](#image-presentation-settings)
  - [Non-Latin Alphabet Support Settings](#non-latin-alphabet-support-settings)
  - [Global Settings](#global-settings)
  - [AddItem](#additem)
  - [AddItemTitle](#additemtitle)
  - [AddItemSong](#additemsong)
  - [AddItemVerse](#additemverse)
  - [AddItemText](#additemtext)
  - [AddItemAudio](#additemaudio)
  - [AddItemVideo](#additemvideo)
  - [AddItemImage](#additemimage)
  - [AddItemFile](#additemfile)
  - [AddItemAutomaticPresentation](#additemautomaticpresentation)
  - [AddItemAnnouncement](#additemannouncement)
  - [AddItemCountdown](#additemcountdown)
  - [AddItemCountdownCommunicationPanel](#additemcountdowncommunicationpanel)
  - [AddItemPlainText](#additemplaintext)
  - [AddItemTextCommunicationPanel](#additemtextcommunicationpanel)
  - [AddItemAddItemScript](#additemadditemscript)
  - [AddItemAddItemAPI](#additemadditemapi)
  - [AddItemURI](#additemuri)
  - [AddItemGlobalAction](#additemglobalaction)
  - [SongInfo](#songinfo)
  - [TextInfo](#textinfo)
  - [VerseInfo](#verseinfo)
  - [AudioInfo](#audioinfo)
  - [VideoInfo](#videoinfo)
  - [ImageInfo](#imageinfo)
  - [FileInfo](#fileinfo)
  - [AutomaticPresentationInfo](#automaticpresentationinfo)
  - [AnnouncementInfo](#announcementinfo)
  - [SongSlideInfo](#songslideinfo)
  - [TextSlideInfo](#textslideinfo)
  - [PPTInfo](#pptinfo)
  - [PPTSlideInfo](#pptslideinfo)
  - [ThemeInfo](#themeinfo)
  - [BackgroundInfo](#backgroundinfo)
  - [TitleInfo](#titleinfo)
  - [WebcamInfo](#webcaminfo)
  - [CountdownInfo](#countdowninfo)
  - [AutomaticPresentationSlideInfo](#automaticpresentationslideinfo)
  - [PresentationModifierInfoInfo](#presentationmodifierinfoinfo)
  - [NewChatMessageInfo](#newchatmessageinfo)
  - [VersePresentationChangedInfo](#versepresentationchangedinfo)
  - [PlaylistChangedInfo](#playlistchangedinfo)
  - [FileModifiedInfo](#filemodifiedinfo)
  - [PlayerProgressInfo](#playerprogressinfo)


# General 
### global
- v2.24.0

Object &nbsp;| &nbsp;Utility class for reading and saving the corresponding data of: `getGlobal(key, default)` and `setGlobal(key, value)`<br>
However, using the JavaScript object itself as a handler.<br>
 <br>
```javascript
var v = h.global.abc;
//{{o mesmo que}}
h.getGlobal('abc');

h.global.abc = 'xyz';
//{{o mesmo que}}
h.setGlobal('abc', 'xyz');
```



---

### storage
- v2.24.0

Object &nbsp;| &nbsp;Utility class for reading and saving the corresponding data of: `store(key, value)` and `restore(key, default)`<br>
However, using the JavaScript object itself as a handler.<br>
 <br>
```javascript
var v = h.storage.abc;
//the same as
var v = h.restore('abc');

h.store.abc = 'xyz';
//the same as
h.store('abc', 'xyz');
```



---

### files
- v2.24.0

[FileUtils](https://github.com/holyrics/jslib/blob/main/doc/en/FileUtils.md) &nbsp;| &nbsp;Utility class for some file manipulation methods.



---

### uri
- v2.24.0

[URIUtils](https://github.com/holyrics/jslib/blob/main/doc/en/URIUtils.md) &nbsp;| &nbsp;Utility class to execute some actions via URI in the operating system, such as executing a streaming track



---

### image
- v2.24.0

[ImageUtils](https://github.com/holyrics/jslib/blob/main/doc/en/ImageUtils.md) &nbsp;| &nbsp;Utility class for images.<br>Alternative name: `img`



---

### stream
- v2.23.0

[Stream](https://github.com/holyrics/jslib/blob/main/doc/en/Stream.md) &nbsp;| &nbsp;Utility class for `stream`



---

### local
- v2.24.0

Object &nbsp;| &nbsp;Utility class to use the same syntax of `store(key, value)` and `restore(key, default)`, but the value is only available for the local device, meaning it is not shared in cloud synchronization.<br>
Alternative name: `device`<br>
 <br>
```javascript
h.local.store(key, value);
var v = h.local.restore(key);
```



---

### globalSettings
- v2.25.0

[GlobalSettings](#global-settings) &nbsp;| &nbsp;Utility class for reading and saving the corresponding data of: `hly('GetGlobalSettings', input)` and `hly('SetGlobalSettings', input)`<br>
However, using the JavaScript object itself as a handler.<br>
 <br>
Alternative name: `gs`
 <br>
```javascript
var v = h.globalSettings.show_favorite_bar_main_window;
//the same as
var data = h.hly('GetGlobalSettings', {
  filter: 'show_favorite_bar_main_window'
});
var r = data.show_favorite_bar_main_window;

h.globalSettings.show_favorite_bar_main_window = false;
//the same as
h.hly('SetGlobalSettings', {
  show_favorite_bar_main_window: false
});
```



---

### log(obj)
Display the information passed as a parameter in a log window (lower right corner of the screen, usually)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `obj` | _Object_ | Any object to be displayed in the log window |


_Method does not return value_

**Example:**

```javascript
h.log('log message');
```

---


### log(key = null, obj, args = null)
### log.add(key = null, obj, args = null)
- v2.20.0

Display the information passed as a parameter in a log window (lower right corner of the screen, usually)<br>
Use {%t} to display the current time.<br>
`h.logf('{%t} - {}', 'Test message');`.<br>
 <br>
Use the syntax `{i18n|...}` to use the translated message according to the translation table available in `jsc`.<br>
Example:<br>
`h.logf('{i18n|Example}');`<br>
`h.logf('{i18n|Test message} {i18n|Test message 2}');`<br>
`h.logf('{i18n|Test message} {i18n|Test message 2 {} with param}', ['param']);`<br>
 <br>
Variations:<br>
`{i18n,lc|Test message}` Force the display of text in lowercase<br>
`{i18n,uc|Test message}` Force the display of text in uppercase

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key/id of log management |
| `obj` | _Object_ | Any object to be displayed in the log window |
| `args` | _Array&lt;Object&gt; (optional)_ | Parameters for formatting a log message |


_Method does not return value_

**Example:**

```javascript
h.log('xyz', 'log message');

h.log('xyz', 'log message {} abc {}', ['value 1', 'value 2']);
//output:
//log message value 1 abc value 2

h.log('log message {} abc {}', ['value 1', 'value 2']);
//output:
//log message value 1 abc value 2
```

---


### logf(obj, args = null)
- v2.23.0

The same as `h.log(key, obj, ...args)`, but without needing to provide key

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `obj` | _Object_ | Any object to be displayed in the log window |
| `args` | _Array&lt;Object&gt; (optional)_ | Parameters for formatting a log message |


_Method does not return value_

**Example:**

```javascript
h.logf('log message');

h.logf('log message {} abc {}', 'value 1', 'value 2');
```

---


### logfp(obj, args = null)
### logpf(obj, args = null)
- v2.23.0

The same as `h.logf(key, obj, ...args)`, but complex objects will be displayed in 'pretty-print' format

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `obj` | _Object_ | Any object to be displayed in the log window |
| `args` | _Array&lt;Object&gt; (optional)_ | Parameters for formatting a log message |


_Method does not return value_

**Example:**

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

The same as `h.log(obj)`, but complex objects will be displayed in 'pretty-print' format

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `obj` | _Object_ | Any object to be displayed in the log window |


_Method does not return value_

**Example:**

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

Display the information passed as a parameter in a log window (lower right corner of the screen, usually)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key/id of log management |
| `obj` | _Object_ | Any object to be displayed in the log window |
| `args` | _Array&lt;Object&gt; (optional)_ | Parameters for formatting a log message |


_Method does not return value_

**Example:**

```javascript
h.log('xyz', 'log message');

h.log('xyz', 'log message {} abc {}', ['value 1', 'value 2']);
//output:
//log message value 1 abc value 2

h.log('log message {} abc {}', ['value 1', 'value 2']);
//output:
//log message value 1 abc value 2
```

---


### logt(obj)
- v2.24.0

The same as `h.log(obj)`, but adds the current time at the beginning of the log

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `obj` | _Object_ | Any object to be displayed in the log window |


_Method does not return value_

**Example:**

```javascript
h.logt("Example");
/* OUTPUT
19:30:00 | Example
*/
```

---


### log.setEnabled(key, enabled)
- v2.23.0

Enable/disable the display of logs from the key/id passed as a parameter. All keys/ids start disabled by default

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key/id of log management |
| `enabled` | _Boolean_ |  |


_Method does not return value_

**Example:**

```javascript
h.log.setEnabled('xyz', true);
```

---


### log.enable(key)
### log.disable(key)
- v2.20.0

Enable/disable the display of logs from the key/id passed as a parameter. All keys/ids start disabled by default

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key/id of log management |


_Method does not return value_

**Example:**

```javascript
h.log.enable('xyz');
h.log.disable('xyz');
```

---


### log.enableAll()
### log.disableAll()
- v2.20.0

Enable/disable the display of all logs



_Method does not return value_

**Example:**

```javascript
h.log.enableAll();
h.log.disableAll();
```

---


### log.isEnabled(key)
### log.isDisabled(key)
- v2.20.0

Checks if the visualization is enabled/disabled for the respective key/id

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key/id of log management |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

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

Enable/disable the display of key/id along with the message in the log window

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Boolean_ |  |


_Method does not return value_

**Example:**

```javascript
h.log.setShowLogKey(false);
```

---


### log.isShowLogKey()
- v2.20.0

Checks if the display of the key is activated



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
if (h.log.isShowLogKey()) {
    //...
}
```

---


### log.toggleEnabled(key)
### log.toggle(key)
- v2.23.0

Toggle the current value

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key/id of log management |


_Method does not return value_

**Example:**

```javascript
h.log.toggleEnabled('xyz');
```

---


### sleep(time)
Pause execution in X milliseconds as specified value

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `time` | _Number_ | Value in milliseconds. Minimum=0, Maximum=60000 |


_Method does not return value_

**Example:**

```javascript
h.sleep(200); //200ms
```

---


### base64Encode(input)
Encodes an array of bytes to base64 string

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | array of bytes or string |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | String in base64 format |


---


### base64Decode(str)
Decodes a string in base64 format

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `str` | _String_ | String in base64 |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;byte&gt;_ | Array of bytes decoded |


---


### base64DecodeAsString(str, charset = 'utf8')
- v2.21.0

Decodes a string in base64 format

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `str` | _String_ | String in base64 |
| `charset` | _String (optional)_ | Charset for conversion of decoded bytes |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Decoded String |


---


### hexEncode(input)
- v2.24.0

Encodes an array of bytes into a hexadecimal string

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | array of bytes or string |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | String in hexadecimal format |


---


### hexDecode(hex)
- v2.24.0

Decodes a string in hexadecimal format

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `hex` | _String_ | String in hexadecimal |


**Response:**

| Type  |
| :---: |
| _Array&lt;Byte&gt;_ | 


---


### hexDecodeAsString(hex, charset = 'utf-8')
- v2.24.0

Decodes a string in hexadecimal format

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `hex` | _String_ | String in hexadecimal |
| `charset` | _String (optional)_ | Charset for conversion of decoded bytes `Default: utf-8` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Decoded String |


---


### hexDecodeAsNumber(hex)
- v2.24.0

Decodes a string in hexadecimal format

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `hex` | _String_ | String in hexadecimal |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Decoded number |


---


### uuid()
- v2.23.0

UUID



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | UUID |


**Example:**

```javascript
var uuid = h.uuid();
```

---


### hash(hashName, data)
- v2.21.0

Returns the hash of the informed parameter

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `hashName` | _String_ | Can be: `MD5` `SHA-1` `SHA-256` `SHA-384` `SHA-512` |
| `data` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | hash |


**Example:**

```javascript
var hash = h.hash('SHA-512', "Example");
```

---


### hashBytes(hashName, data)
- v2.21.0

Returns the hash of the informed parameter

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `hashName` | _String_ | Can be: `MD5` `SHA-1` `SHA-256` `SHA-384` `SHA-512` |
| `data` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;byte&gt;_ | hash |


**Example:**

```javascript
var bytes = h.hashBytes('SHA-512', "Example");
```

---


### checksum(hashName, data)
- v2.21.0

Returns the **checksum** of the informed parameter

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `hashName` | _String_ | Can be: `ADLER-32` `CRC32` |
| `data` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | checksum |


**Example:**

```javascript
var crc32 = h.checksum('CRC32', "Example");
```

---


### md5(value)
MD5 hash in byte array

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;byte&gt;_ | MD5 hash |


---


### md5Str(value)
MD5 hash

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | MD5 hash |


---


### sha256(value)
Hash SHA-256 in byte array

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;byte&gt;_ | SHA-256 hash |


---


### sha256Str(value)
SHA-256 hash

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | SHA-256 hash |


---


### sha512(value)
- v2.20.0

SHA-512 hash in byte array

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;byte&gt;_ | SHA-512 hash |


---


### sha512Str(value)
- v2.20.0

SHA-512 hash

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be calculated. Can be string or byte array |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | SHA-512 hash |


---


### security(securityKey)
### sec(securityKey)
- v2.23.0

Class to perform encryption actions and store data protected with a password

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `securityKey` | _String_ | Security key |


**Response:**

| Type  | Description |
| :---: | ------------|
| _[SecurityUtils](#securityutils-methods)_ | SecurityUtils class object |


**Example:**

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

Convert an object to JSON

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `obj` | _Object_ |  |


**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

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

Convert an object to JSON in 'pretty-print' format

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `obj` | _Object_ |  |


**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

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
Get the operating system clipboard text



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Clipboard text |


**Example:**

```javascript
var val = h.getClipboard();
h.log('Clipboard text: ' + val);
```

---


### normalize(str)
Remove accent from string

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `str` | _String_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | String without accent |


**Example:**

```javascript
var r = h.normalize("ÁÉÍÓÚÇáéíóúç");
h.log('Text with accent removed: ' + r); //AEIOUCaeiouc
```

---


### store(key, value)
Saves an object to disk that can be retrieved even after restarting the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | key/id to save the object |
| `value` | _Object_ | Object to be saved. Versions prior to `2.23.0` are only compatible with objects of type `string` |


_Method does not return value_

**Example:**

```javascript
h.store('abc', 'Example');
```

---


### restore(key, default = null)
Retrieves the object saved on disk

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | key/id of the previously saved object |
| `default` | _Object (optional)_ | Default value returned if no previously saved object is found `v2.23.0+` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns the saved object or **default** if not found. Versions prior to `2.23.0` are only compatible with objects of type `string` |


**Example:**

```javascript
var r = h.restore('abc');
if (r == null) {
    h.log('Item abc not found');
} else {
    h.log('Item abc: ' + r);
}


var r = h.restore('xyz', {});
h.logfp('Item xyz: {}', r);
```

---


### setGlobal(key, value, ttl = 0)
Saves an object in memory that can be retrieved, but is valid only as long as the program is open. The method is shared with all scripts in the program.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Saved object key |
| `value` | _Object_ | Object to be saved in memory |
| `ttl` | _Number (optional)_ | Duration in seconds for the variable access to expire `v2.21.0+` |


_Method does not return value_

**Example:**

```javascript
h.setGlobal('xyz', 'Example');

//expires in 1 hour
h.setGlobal('xyz', 'Example', 3600);
```

---


### getGlobal(key, default = null)
Retrieves an object saved in memory. The method is shared with all scripts in the program.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key of object saved in memory |
| `default` | _Object (optional)_ | Default value if no previously saved value is found |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns the saved object or **default** if not found |


**Example:**

```javascript
var r = h.getGlobal('xyz');
if (r == null) {
    h.log('Item xyz not found');
} else {
    h.log('Item xyz: ' + r);
}

var r2 = h.getGlobal('xyz', 'default value');
h.log('Item xyz: ' + r2);
```

---


### setGlobalNext(key, values, ttl = 0)
- v2.21.0

It's the same as `setGlobal`, but the `values` parameter is a list of items, and the value that will be saved in `setGlobal` is the next item in the list (based on the current item) or the first item in the list (if the current item is null, or is the last item in the list, or does not exist in the list).

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Saved object key |
| `values` | _Object_ | Object, array, map or list with possible values |
| `ttl` | _Number_ | Duration in seconds for the variable access to expire |


_Method does not return value_

**Example:**

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

It's the same as `getGlobal` followed by `setGlobal`.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | object key/id |
| `default` | _Object (optional)_ | Default value if no previously saved value is found |
| `newValue` | _Object_ | Object to be saved in memory |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns the saved object or **default** if not found |


**Example:**

```javascript
var r = h.getGlobalAndSet('xyz', "New value");
```

---


### getGlobalAndSetNext(key, values)
- v2.21.0

It's the same as `getGlobal` followed by `setGlobalNext`.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Saved object key |
| `values` | _Object_ | Object, array, map or list with possible values |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns the saved object or **default** if not found |


**Example:**

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

It's the same as `setGlobalNext` followed by `getGlobal`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Saved object key |
| `values` | _Object_ | Object, array, map or list with possible values |


_Method does not return value_

**Example:**

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
Generate a random number

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `min` | _Number_ | minimum value |
| `max` | _Number_ | Maximum value |
| `keySafeRepeat` | _String (optional)_ | Can be used to avoid repeated number drawn in sequence |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Returns a random number from **min** to **max** |


**Example:**

```javascript
var r = h.random(0, 10);
h.log('Random number from 0 to 10: ' + r);
//The number drawn can be repeated
r = h.random(0, 10);
h.log('Random number from 0 to 10: ' + r);

//To avoid repetition:
var r = h.random(0, 10, 'xyz');
h.log('Random number from 0 to 10: ' + r);
//The number drawn will not be repeated
r = h.random(0, 10, 'xyz');
h.log('Random number from 0 to 10: ' + r);

//The do not repeat mechanic also works when the script is run again
//and not just in sequence executions as in the example above
```

---


### random(x, y, z)
- v2.21.0

Get a random value based on input values

Possible combinations:
(x = number)
Returns a random value from 0 to x

(x = number, y = number)
Returns a random value from x to y

(x = string)
Returns a random character from string x

(x = array)
Returns a random object from array x

(x = object)
Returns a random field from object x

It is possible to add an additional parameter of type `string` as an argument in the above calls to be used as 'keySafeRepeat' (to avoid a repeated value being drawn in sequence)
Example: (x = number, y = number, x = string)


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `x` | _Object_ |  |
| `y` | _Object (optional)_ |  |
| `z` | _Object (optional)_ |  |


**Response:**

| Type  |
| :---: |
| _Object_ | 


**Example:**

```javascript
var r = h.random(0, 10);
h.log('Random number from 0 to 10: ' + r);
//The number drawn can be repeated
r = h.random(0, 10);
h.log('Random number from 0 to 10: ' + r);

//To avoid repetition:
var r = h.random(0, 10, 'xyz');
h.log('Random number from 0 to 10: ' + r);
//The number drawn will not be repeated
r = h.random(0, 10, 'xyz');
h.log('Random number from 0 to 10: ' + r);

//The do not repeat mechanic also works when the script is run again
//and not just in sequence executions as in the example above

var r = h.random(10);
h.log('Random number from 0 to 10: ' + r);

var r = h.random("abcd");
h.log('Random character from the string abcd: ' + r);

var r = h.random([20, 25, 30]);

var r = h.random([20, 25, 30], 'xyz');
var r = h.random([20, 25, 30], 'xyz');
//Does not repeat the previously drawn value

var r = h.random(['z', 123, false]);
```

---


### startTimer(key = 'default')
Start a timer

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String (optional)_ | Timer key `Default: 'default'` |


_Method does not return value_

**Example:**

```javascript
h.startTimer('xyz');
h.sleep(2000); //2 seconds
var r = h.getTimer('xyz');
h.log('Elapsed time: ' + r); //Like 00:00:02

//is a global method, the value can be used in any other script using the same key
```

---


### getTimer(key = 'default')
Retrieves how much time has elapsed on a timer according to the **key** value. If the timer has not been started, the method will start the timer and return 00:00:00

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String (optional)_ | Timer key `Default: 'default'` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Elapsed time in format HH:MM:SS |


**Example:**

```javascript
var r = h.getTimer('xyz');
h.log('Elapsed time: ' + r);
```

---


### getTimerMillis(key)
- v2.21.0

Recovers how much time has elapsed (in milliseconds) on a timer according to the value **key**. If the timer has not been started, the method will start the timer and return 0

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Timer key |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Elapsed time in milliseconds |


---


### getTimerSeconds(key)
- v2.21.0

Recovers how much time has elapsed (in seconds) on a timer according to the value **key**. If the timer has not been started, the method will start the timer and return 0

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Timer key |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Elapsed time in seconds |


---


### startCountdown(key = 'default', seconds)
- v2.20.0

Start a countdown

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String (optional)_ | Key/id of the countdown `Default: 'default'` |
| `seconds` | _Number_ | Total duration of the countdown in seconds |


_Method does not return value_

**Example:**

```javascript
h.startCountdown('xyz', 300);
h.sleep(2000); //2 seconds
var r = h.getCountdown('xyz');
h.log('Remaining time: ' + r); //probably 00:04:58

//is a global method, the value can be used in any other script using the same key
```

---


### getCountdown(key = 'default')
- v2.20.0

Recovers how much time is left in a countdown according to the **key** value.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String (optional)_ | Key/id of the countdown `Default: 'default'` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Remaining time in the format HH:MM:SS (returns negative values after time limit) |


**Example:**

```javascript
var r = h.getCountdown('xyz');
h.log('Remaining time: ' + r);
```

---


### getCountdownMillis(key)
- v2.21.0

Recovers how much time is left in a countdown according to the **key** value.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key/id of the countdown |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Remaining time in milliseconds (returns negative values after time limit) |


---


### getCountdownSeconds(key)
- v2.21.0

Recovers how much time is left in a countdown according to the **key** value.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Key/id of the countdown |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Remaining time in seconds (returns negative values after time limit) |


---


### getPlaylistInfo()
Gets the currently selected playlist in the program



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | Playlist event type. Can be: temporary, service, event |
| `name` | _String_ | Event name |
| `datetime` | _String_ | Item date and time in format: YYYY-MM-DD HH:MM |


**Example:**

```javascript
var r = h.getPlaylistInfo();
h.log(r.name + ' - ' + r.datetime);
switch (r.type) {
    case 'temporary':
        h.log('Playlist is temporary');
        break;
    case 'service':
        h.log('The playlist is from a service');
        break;
    case 'event':
        h.log('The playlist is from an event');
        break;
}
```

---


### getPlayer()
Player class to get information and perform actions on the program's player



**Response:**

| Type  |
| :---: |
| _[Player](https://github.com/holyrics/jslib/blob/main/doc/en/Player.md)_ | 


**Example:**

```javascript
var r = h.getPlayer();
if (r.isPlaying()) {
    h.log('The player is running');
} else {
    h.log('The player is not running');
}

//change volume
r.setVolume(80);

//mute
r.setMute(true);

//stop current execution
r.stop();
```

---


### getAutomaticPresentationPlayer()
### getAPPlayer()
- v2.23.0

Class representing the program's automatic presentation player



**Response:**

| Type  |
| :---: |
| _[AutomaticPresentationPlayer](https://github.com/holyrics/jslib/blob/main/doc/en/AutomaticPresentationPlayer.md)_ | 


**Example:**

```javascript
var r = h.getAPPlayer();
if (r.isPlaying()) {
    h.logf('Total time: {} - Slide time: {}', r.getTime(), r.getSlide().getTime());
}
```

---


### scriptAction(id, input = null)
Executes the action of an existing **Script** item in the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | item id |
| `input` | _Object (optional)_ | Values that will be set for [Function Input](https://github.com/holyrics/Scripts/blob/main/i18n/en/FunctionInput.md) `v2.20.0+` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Returns **false** if the item is not found |


**Example:**

```javascript
var r = h.scriptAction('abcxyz');
if (r) {
    h.log('Action performed');
} else {
    h.log('Item abcxyz not found');
}

var r = h.scriptAction('abcxyz', {
    id_example_1: 'abc',
    id_example_2: 10
});
if (r) {
    h.log('Action performed');
} else {
    h.log('Item abcxyz not found');
}
```

---


### apiAction(id, input = null)
Executes the action of an existing API item in the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | item id |
| `input` | _Object (optional)_ | Values that will be set for [Function Input](https://github.com/holyrics/Scripts/blob/main/i18n/en/FunctionInput.md) `v2.20.0+` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Returns **false** if the item is not found |


**Example:**

```javascript
var r = h.apiAction('abcxyz');
if (r) {
    h.log('Action performed');
} else {
    h.log('Item abcxyz not found');
}

var r = h.apiAction('abcxyz', {
    id_example_1: 'abc',
    id_example_2: 10
});
if (r) {
    h.log('Action performed');
} else {
    h.log('Item abcxyz not found');
}
```

---


### apiRequest(id, raw)
Executes a request to the associated receiver and returns the receiver's response.<br>
From `v2.23.0` it is possible to pass the host or IP directly, but it is necessary to add the host/IP to the list of allowed requests.<br>
file menu > settings > advanced > javascript > settings > allowed requests

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | receiver id |
| `raw` | _Object_ | requisition data |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Request return or NULL for error/timeout |


**Example:**

```javascript
//It is possible to make a request directly to a receiver created
//For example:
//Assuming you have a receiver created to communicate with OBS Studio via websocket and the receiver ID is 'abcyxz'
//you can make a request as in the example below
var r = h.apiRequest('receiver_id', {
    'request-type': 'GetSourceActive',
    'sourceName': 'example'
});
h.log('Requisition response: ' + r);
var obj = JSON.parse(r);
if (obj.sourceActive) {
    h.log('The example source is active');
} else {
    h.log('The example source is not active');
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

//Parameters available for request [URL]
var r = h.apiRequest('receiver_id', {
    //type of request
    //GET, POST, PATCH, PUT, DELETE, UDP, TCP, WS_JSON, WS
    type: 'POST', /* optional */

    //parameter added to the end of the url defined in the receiver
    url_suffix: 'test.php?x=1&y=2&z=3', /* optional */
    
    //request header
    headers: { /* optional */
        Authorization: '1234'
    },
    
    //request body (except for GET type)
    //can be byte array for UDP and TCP
    //data: h.createByteBuffer().putString('example').toBytes(),
    data: "example",
    
    //request response encoding, utf-8 by default
    //response_data_type: "string;iso-8859-1",
    //response_data_type: "base64",
    response_data_type: "string;utf-8", /* optional */
    
    //Available for: UDP
    wait_for_response: true, /* optional */
    
    //Available for: UDP
    port: 1234, /* optional */
    
    //timeout ms - default: 5000 - UDP: 2000
    timeout: 5000 /* optional */
});

//-------------------------------------------------

//Parameters available for request [MIDI]
//Array
//[code, velocity, action, channel, note_off, sleep]
//code: 0~127
//velocity: 0~127
//action: (optional) note_on, control_change, program_change, polyphonic_key_pressure, channel_pressure, pitch_bend_change, midi_time_code, song_position_pointer, song_select, tune_request, timing_clock, start, continue, stop, active_sensing, system_reset
//channel: (optional) 0~15
//note_off: (optional) 0~127
//sleep: (optional) 0~300000 (millis)
var action = [30, 127, 'control_change'];
var r = h.apiRequest('receiver_id', action);

//Array<Array>
var actions = [
    [30, 127, 'control_change'],
    [32, 127, 'program_change']
];
var r = h.apiRequest('receiver_id', actions);

//Object
var action = {
    code: 30,
    velocity: 127,
    action: 'control_change'
};
var r = h.apiRequest('receiver_id', action);

//Array<Object>
var actions = [
    {
        code: 30,
        velocity: 127,
        action: 'control_change'
    }, {
        code: 32,
        velocity: 127,
        action: 'program_change'
    }
];
var r = h.apiRequest('receiver_id', actions);
```

---


### getApiRequestLastError()
- v2.19.0

Returns the error of the last apiRequest request performed.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Last request error or NULL if no error |


---


### apiRequestAsync(id, raw, callback = null)
- v2.19.0

Executes a request to the associated receiver asynchronously. The result can be accessed by creating an anonymous function as a callback.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | receiver id |
| `raw` | _Object_ | requisition data |
| `callback` | _Function (optional)_ | anonymous function used as request callback. function(response, error){} |


_Method does not return value_

**Example:**

```javascript
//works like apiRequest, but asynchronously
//
//wait for the return, it may take a while
//the next line is executed only when the request is completed
var r = h.apiRequest('abcxyz', {
    'request-type': 'GetSceneList'
});
//next line

//do not wait for the return
//the next line is executed right after
h.apiRequestAsync('abcxyz', {
    'request-type': 'GetSceneList'
}, function (response, error) {
    //request callback
});
//next line
```

---


### apiRequestEx(id, raw)
- v2.21.0

O mesmo que}} `apiRequest(id, raw)`, but throws an exception when an error occurs, instead of returning **null**

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | receiver id |
| `raw` | _Object_ | requisition data |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Request return |


---


### setTimeout(function, timeout, name = null)
- v2.19.0

Runs a function after a few milliseconds.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `function` | _Function_ | Function that will be executed |
| `timeout` | _Number_ | Time in milliseconds to wait until execution |
| `name` | _String (optional)_ | Item name. Compatible value for display in **JavaScript Monitor** `v2.23.0+` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Returns the task ID. You can use the ID to cancel the run. |


**Example:**

```javascript
var id = h.setTimeout(function () {
    //task that will run in 60 seconds
}, 60000);
```

---


### clearTimeout(id)
- v2.19.0

Cancels previously scheduled function execution.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _Function_ | ID returned from method **setTimeout** |


_Method does not return value_

**Example:**

```javascript
var id = h.setTimeout(function () {
    //task that will run in 60 seconds
}, 60000);

//cancel task execution
h.clearTimeout(id);
```

---


### setInterval(function, timeout, name = null)
- v2.19.0

Runs a function every X milliseconds. Use **clearInterval** to stop execution.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `function` | _Function_ | Function that will be executed |
| `timeout` | _Number_ | Interval in milliseconds between each run |
| `name` | _String (optional)_ | Item name. Compatible value for display in **JavaScript Monitor** `v2.23.0+` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Returns the task ID. You can use the ID to stop the execution. |


**Example:**

```javascript
var id = h.setInterval(function () {
    //task that will run every 15 seconds
}, 15000);
```

---


### clearInterval(id)
- v2.19.0

Cancels previously scheduled function execution.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _Function_ | ID returned from method **setInterval** |


_Method does not return value_

**Example:**

```javascript
var id = h.setInterval(function () {
    //task that will run every 15 seconds
}, 15000);

//stop execution
h.clearInterval(id);
```

---


### runAt(input)
- v2.24.0

Executes a function at a specified time.<br>
Works like a **setTimeout**, but without the need to calculate the time in milliseconds.<br>
The task is not persistent, meaning that upon restarting the program it does not remain scheduled.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Item ID |
| `input.name` | _String (optional)_ | Item name |
| `input.datetime` | _Object_ | Execution time.<br>Accepted formats: `HH:MM:SS` `HH:MM` `YYYY-MM-DD HH:MM` `YYYY-MM-DD HH:MM:SS` `YYYY/MM/DD HH:MM` `YYYY/MM/DD HH:MM:SS` `timestamp` |
| `input.action` | _Function_ | Action to be executed |
| `input.notification` | _Boolean (optional)_ | `true` to display a notification in the corner of the screen one minute before the task execution, allowing the user to cancel the execution |
| <br>Available if **notification=true** |  |  |
| `input.description` | _String (optional)_ | Description displayed in the notification |
| `input.icon` | _String (optional)_ | Icon displayed in the notification.<br>Uses the syntax of [Icon](https://github.com/holyrics/Scripts/blob/main/i18n/en/Icon.md). |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Returns the task ID. You can use the ID to cancel the run. `cancelRunAt(id)` |


**Example:**

```javascript
var id = runAt({
  name: '',
  datetime: '19:25',
  action: function() {
    //todo
  }
});

//h.cancelRunAt('id');
```

---


### cancelRunAt(id)
- v2.24.0

Cancels previously scheduled function execution.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _Function_ | ID returned from the **runAt** method |


_Method does not return value_

---


### getHostname()
- v2.19.0

Returns the device name.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Device name |


---


### getRuntimeEnvironment()
### getRE()
- v2.19.0

Returns the name of the currently defined runtime environment in the program settings.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Runtime environment name |


---


### setRuntimeEnvironment(name)
### setRE(name)
- v2.19.0

Change the current runtime environment.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Runtime environment name |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Return **true** or **item not found** |


---


### isRuntimeEnvironment(name)
### isRE(name)
- v2.19.0

Checks whether the current execution environment is the same as the one passed by parameter.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Runtime environment name |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Return **true** or **false** |


---


### getVersion()
- v2.20.0

Returns the current version of the program.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Version in the format: X.Y.Z |


**Example:**

```javascript
if (h.getVersion() == "2.20.0") {
    //...
}
```

---


### isMinimumVersion(version)
### isMinVersion(version)
- v2.20.0

Checks if the program version is equal to or higher than the one informed by parameter.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `version` | _String_ | Version in the format: X.Y.Z |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
if (h.isMinimumVersion('2.20.0')) {
    //The current version is equal to or greater than 2.20.0
}
```

---


### getDeviceID()
- v2.24.0

Returns the device ID. Useful for differentiating the device when cloud synchronization is enabled.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | `[a-zA-Z0-9]{12}` |


---


### getLanguage()
- v2.20.0

Returns the current language set in the program settings.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Language in ISO 639 two-letter format |


**Example:**

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

Checks if the current language set in the program settings is equal to the value passed by parameter.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `language` | _String_ | Language in ISO 639 two-letter format |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
if (h.isLanguage('pt')) {
    //...
}
```

---


### getUITheme()
- v2.20.0

Returns the current theme of the program interface.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | One of the following values: `DEFAULT` `DARK_SOFT` `DARK_MEDIUM` `DARK_STRONG` |


**Example:**

```javascript
if (h.getUITheme() == 'DEFAULT') {
    //...
}
```

---


### isUITheme(value)
- v2.20.0

Checks if the current theme of the interface is equal to the value passed by parameter.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Theme name |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
if (h.isUITheme('DARK_STRONG')) {
    //...
}
```

---


### getCommunityVersion()
- v2.23.0

Returns the current version of the JSCommunity library in the program.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Version in the format: X.Y.Z |


---


### isMinimumCommunityVersion(version)
### isMinCommunityVersion(version)
- v2.23.0

Checks if the version of the JSCommunity library in the program is equal to or greater than the one specified by parameter.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `version` | _String_ | Version in the format: X.Y.Z |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### getHolyricsPluginVersion()
- v2.24.0

Returns the current version of **Holyrics Plugin**



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Version in the format: y.m.d |


---


### isHolyricsPluginOpened()
- v2.24.0

Checks if the Holyrics Plugin is open



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### isHolyricsPluginStarted()
- v2.24.0

Checks if the Holyrics Plugin server is started



**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### format.secondsToHMS(seconds, separator = ':')
### secToHMS(seconds, separator)
- v2.20.0

Format a number of seconds as hour|minute|second.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `seconds` | _Number_ | Total amount of seconds |
| `separator` | _String (optional)_ | Separator `Default: ':'` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Formatted value |


**Example:**

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

Format a number of seconds as minute|second.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `seconds` | _Number_ | Total amount of seconds |
| `separator` | _String (optional)_ | Separator `Default: ':'` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Formatted value |


**Example:**

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

Format a number of minutes as hour|minute.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `minutes` | _Number_ | Total amount of minutes |
| `separator` | _String (optional)_ | Separator `Default: ':'` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Formatted value |


**Example:**

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

An alias for the default formatter in Java java.util.Formatter [Documentation](https://docs.oracle.com/javase/8/docs/api/java/util/Formatter.html)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `format` | _String_ |  |
| `params` | _Array&lt;Object&gt;_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Formatted value |


**Example:**

```javascript
var r = h.format.f("Example: %s, %.2f", ['abc', 100.1234]);
//r == Example: abc, 100,12
```

---


### format.rgbToHex(red, green, blue)
### format.rgbaToHex(red, green, blue, alpha)
- v2.23.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `red` | _Number_ | `0 ~ 255` |
| `green` | _Number_ | `0 ~ 255` |
| `blue` | _Number_ | `0 ~ 255` |
| `alpha` | _Number_ | `0 ~ 255` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Color in hexadecimal format. `RRGGBB` or `RRGGBBAA`<br>If `alpha = 255`, only `RRGGBB` will be returned |


**Example:**

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


### format.applyJSHighlightHTML(code)
- v2.24.0

Applies syntax formatting to a piece of JavaScript code for better visualization when displaying examples in the interface

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `code` | _String_ | JavaScript Code |


**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

```javascript
var code = "function example() {\n"
         + "  return 'abc';\n"
         + "}";
var r = h.format.applyJSHighlightHTML(code);
h.ok("<html>" + r);
```

---


### date.getSecondOfDay()
- v2.20.0

Returns the total amount of seconds of the day (hour * 3600 + minute * 60 + second)



**Response:**

| Type  |
| :---: |
| _Number_ | 


**Example:**

```javascript
var r = h.date.getSecondOfDay();
//00:00:00 = 0
//23:59:59 = 86399
```

---


### date.getSecondOfDay(hour, minute, second)
- v2.20.0

Returns the total amount of seconds of the day (hour * 3600 + minute * 60 + second)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `hour` | _Number_ |  |
| `minute` | _Number_ |  |
| `second` | _Number_ |  |


**Response:**

| Type  |
| :---: |
| _Number_ | 


**Example:**

```javascript
var r = h.date.getSecondOfDay(18, 30, 0);
```

---


### date.toMillis(value)
- v2.24.0

Converts a value to timestamp (in milliseconds)<br>
Accepted formats: `YYYY-MM-DD` `YYYY/MM/DD` `YYYY-MM-DD HH:MM:SS` `YYYY/MM/DD HH:MM:SS` `DD-MM-YYYY` `DD/MM/YYYY` `DD-MM-YYYY HH:MM:SS` `DD/MM/YYYY HH:MM:SS`<br>
Note: `:SS` is optional<br>
The current system TimeZone will be used as a basis to generate the Timestamp value<br>
May generate Exception

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ |  |


**Response:**

| Type  |
| :---: |
| _Number_ | 


**Example:**

```javascript
var timeMillis = h.date.toMillis('2024-12-16 19:30:00');
```

---


### date.getElapsedTime(unit, a, b)
- v2.24.0

Returns the difference between two dates. ´b - a´<br>
Accepted formats: `timestamp` `YYYY-MM-DD` `YYYY/MM/DD` `YYYY-MM-DD HH:MM:SS` `YYYY/MM/DD HH:MM:SS` `DD-MM-YYYY` `DD/MM/YYYY` `DD-MM-YYYY HH:MM:SS` `DD/MM/YYYY HH:MM:SS`<br>
Note: `:SS` is optional<br>
May generate Exception

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `unit` | _String_ | Can be: `millis` `seconds` `minutes` `hours` `days` |
| `a` | _String_ |  |
| `b` | _String_ |  |


**Response:**

| Type  |
| :---: |
| _Number_ | 


**Example:**

```javascript
var r = h.date.getElapsedTime('hours', '2024-12-16 15:00:00', '2024-12-16 19:30:00');
//r == 4
```

---


### date.format(format, date = null)
- v2.25.0

Format a date.<br>May generate Exception.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `format` | _String_ | Pattern [SimpleDateFormat](https://docs.oracle.com/javase/8/docs/api/java/text/SimpleDateFormat.html) |
| `date` | _Object (optional)_ | Can be:<br>Native JavaScript Date object or a timestamp number (compatible with seconds and milliseconds).<br>If the parameter is not declared, the current date and time on the system will be used. |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Formatted value |


**Example:**

```javascript
var r = h.date.format('yyyy-MM-dd', Date.now());
```

---


### date.get(format = null)
- v2.25.0

Gets the current date and time formatted.<br>May generate Exception.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `format` | _String (optional)_ | Pattern [SimpleDateFormat](https://docs.oracle.com/javase/8/docs/api/java/text/SimpleDateFormat.html) `Default: yyyy-MM-dd HH:mm:ss` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Formatted value |


---


### date.parse(format, value)
- v2.25.0

Converts a string to `Timestamp`.<br>May generate Exception.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `format` | _String_ | Pattern [SimpleDateFormat](https://docs.oracle.com/javase/8/docs/api/java/text/SimpleDateFormat.html) |
| `value` | _String_ | Pattern [SimpleDateFormat](https://docs.oracle.com/javase/8/docs/api/java/text/SimpleDateFormat.html) |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Timestamp |


**Example:**

```javascript
var r = h.date.parse('yyyy-MM-dd', '2025-03-16');
```

---


### csvToArray(csv)
- v2.21.0

Converts a CSV (string) into a two-dimensional array

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `csv` | _String_ | String in CSV format |


**Response:**

| Type  |
| :---: |
| _Array&lt;Object&gt;_ | 


**Example:**

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

Converts a string in XML format to a JavaScript object. May generate Exception.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `xml` | _String_ | String in XML format |


**Response:**

| Type  |
| :---: |
| _Object_ | 


**Example:**

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

Register a trigger for execution

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _[TriggerItem](#trigger-item)_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Returns the ID of the registered item (automatically generated if **input.id** is **null**) |


**Example:**

```javascript
var r = h.addTriggerListener({
    when: 'displaying',
    item: 'any_song',
    action: function (obj) {
        if (obj.title == 'Example') {
            //do action
        }
    },
    filter: {
        title: 'Song Title'
    }
});

var r = h.addTriggerListener({
    when: 'displaying',
    item: 'any_song',
    action: function (obj) {
        //do action
    },
    filter: {
        title: 'Example'
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

Remove a registered trigger

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Returns **true** for removed. Returns **false** for ID was not found |


**Example:**

```javascript
var r = h.removeTriggerListener('xyz');
```

---


### containsTriggerListener(id)
- v2.21.0

Checks if a trigger with the specific ID is already registered

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


---


### getTriggerListeners()
- v2.21.0

Returns the list of registered triggers



**Response:**

| Type  |
| :---: |
| _Array&lt;[TriggerItem](#trigger-item)&gt;_ | 


**Example:**

```javascript
var items = h.getTriggerListeners();
for (var i = 0; i < items.length; i++) {
    h.log("ID: " + items[i].id);
}
```

---


### addSysVar(name, function, cacheDelay = null)
- v2.23.0

Adds a system variable that can be used within the texts displayed by the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Item name |
| `function` | _Function_ | Function that will be executed to get the return and display the content in place of the variable declared in the presentation |
| `cacheDelay` | _Number (optional)_ | The duration (in milliseconds) that the returned value will be cached for reuse without invoking the `function` again.<br>`500 ~ 60000` `Default: 1000` `v2.25.0+` |


_Method does not return value_

**Example:**

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

Removes a system variable added by h.addSysVar(...)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Item name |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
h.removeSysVar('sum');
```

---


### getSysVar(value)
- v2.23.0

Get the current value of a system variable

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | System variable in the actual usage syntax. Example: `@js{sys_var_name}` |


**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

```javascript
var r = h.getSysVar("@js{sum(3, 4)}");
// r: 7
```

---


### applySysVar(value)
- v2.23.0

Convert all system variables in the passed value to the current value of the respective variable

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Text to be converted |


**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

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

Read a file from the program library (max=16mb)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `file` | _String_ | File name |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;byte&gt;_ | Byte array of the file |


**Example:**

```javascript
var r = h.readImage('file.jpg');
```

---


### readAudioAsBase64(file)
### readImageAsBase64(file)
### readVideoAsBase64(file)
### readFileAsBase64(file)
- v2.21.0

Read a file from the program library (max=16mb)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `file` | _String_ | File name |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | File bytes in base64 format |


**Example:**

```javascript
var r = h.readImageAsBase64('file.jpg');
```

---


### readFileAsText(file, charset = 'utf8')
- v2.21.0

Read a file from the program library (max=16mb)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `file` | _String_ | File name |
| `charset` | _String (optional)_ | File encoding |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | File content in text format |


**Example:**

```javascript
var r = h.readFileAsText('file.txt');
```

---


### isPathEquals(a, b)
- v2.21.0

Checks if the two paths are the same, ignoring case distinction for Windows and considering '\' and '/' as equal

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `a` | _String_ |  |
| `b` | _String (optional)_ |  |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

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

Convert a byte array to a string

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `bytes` | _Array&lt;byte&gt;_ | Byte array |
| `charset` | _String (optional)_ | Coding used `Default: UTF-8` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | String decodificada. The method generates an exception for invalid charset |


---


### stringToBytes(string, charset = 'UTF-8')
- v2.22.0

Converts a string to a byte array

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `string` | _String_ | Text that will be encoded |
| `charset` | _String (optional)_ | Coding used `Default: UTF-8` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Array&lt;byte&gt;_ | Byte array. The method generates an exception for invalid charset |


---


### trim(value, trim)
- v2.23.0

Removes characters from the beginning and end of a string

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Value to be edited |
| `trim` | _String_ | List of characters to be removed from the beginning and end of the value |


**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

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

Performs a replace on all occurrences of the string in JavaScript. The original method in JavaScript replaces only the first occurrence.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `search` | _String_ | Value to be searched |
| `replace` | _String_ | Replacement value |
| `subject` | _String_ | String to be searched and replaced |


**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

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

Removes all values within `<>` (inclusive)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Value to be edited |


**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

```javascript
var r = h.strRemoveTags("example <a> test</b>");
h.log(r);
// output
// example  test
```

---


### fixNonspacingMark(value)
### fixNonSpacingMark(value)
### fixNSM(value)
- v2.24.0

Normalizes characters of type `NonspacingMark (NSM)`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Value that will be normalized |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Normalized value |


**Example:**

```javascript
var str = "e\u0308";
var fixed = h.fixNonspacingMark(str);
//fixed = ё
```

---


### htmlExtractText(html, keepLineBreak = false)
- v2.23.0

Extract text from an HTML formatted snippet

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `html` | _String_ | Value to be edited |
| `keepLineBreak` | _Boolean (optional)_ | If **true**, line breaks `\n (char 10)` will be preserved `Default: false` |


**Response:**

| Type  |
| :---: |
| _String_ | 


**Example:**

```javascript
var html = "<b>Example</b>\n"
        + "Example - <span>Example</span>\n"
        + "<div>Example</div>";
var r = h.htmlExtractText(html);
/*
Example Example - Example
Example
*/

var r = h.htmlExtractText(html, true);
/*
Example
Example - Example
Example
*/
```

---


### exportTXT(text, settings = null)
- v2.22.0

Save content to a TXT file. May generate Exception.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `text` | _String_ | Text that will be saved |
| `settings` | _Object (optional)_ | Settings |
| `settings.name` | _String (optional)_ | File name `Default: YYYY-MM-DD_HH-MM-SS` |
| `settings.charset` | _String (optional)_ | Text encoding `Default: UTF-8` |


_Method does not return value_

**Example:**

```javascript
h.exportTXT("abc", {
    name: "txt filename"
});
```

---


### exportXLSX(data)
- v2.22.0

Save content to an XLSX spreadsheet. May generate Exception.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.name` | _String (optional)_ | File name `Default: YYYY-MM-DD_HH-MM-SS` |
| `data.sheets` | _Array&lt;Object&gt;_ | Tabs |
| `data.sheets.*.name` | _String_ | Tab name |
| `data.sheets.*.header` | _String_ | Header |
| `data.sheets.*.cols_name` | _Array&lt;String&gt;_ | Column titles |
| `data.sheets.*.grid` | _Array&lt;Array&lt;String&gt;&gt;_ | Tabs |


_Method does not return value_

**Example:**

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

Creates an object to store data in binary form.



**Response:**

| Type  |
| :---: |
| _[ByteBufferWriter](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferWriter.md)_ | 


**Example:**

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

Creates an object filled with bytes for reading in binary form.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `reader` | _Array&lt;byte&gt;_ | Byte array |


**Response:**

| Type  |
| :---: |
| _[ByteBufferReader](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferReader.md)_ | 


**Example:**

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

Creates a `stream` to facilitate list manipulations

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `obj` | _Object_ | Array or Object |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [Stream](https://github.com/holyrics/jslib/blob/main/doc/en/Stream.md) |


**Example:**

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

Creates a `stream` to facilitate list manipulations

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `obj` | _Array&lt;Number&gt;_ | Array of numbers |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [IntStream](https://github.com/holyrics/jslib/blob/main/doc/en/IntStream.md) |


**Example:**

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

Creates a `stream` to facilitate list manipulations

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `startInclusive` | _Number_ | Initial value (inclusive) |
| `endExclusive` | _Number_ | Upper limit (exclusive) |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [IntStream](https://github.com/holyrics/jslib/blob/main/doc/en/IntStream.md) |


**Example:**

```javascript
h.intStreamRange(0, 10); // 0...9
```

---


### intStreamRangeClosed(startInclusive, endInclusive)
- v2.23.0

Creates a `stream` to facilitate list manipulations

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `startInclusive` | _Number_ | Initial value (inclusive) |
| `endInclusive` | _Number_ | Upper limit (inclusive) |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | [IntStream](https://github.com/holyrics/jslib/blob/main/doc/en/IntStream.md) |


**Example:**

```javascript
h.intStreamRangeClosed(0, 10); // 0...10
```

---


### chat.sendMessage(message)
- v2.23.0

Send message to Holyrics chat.<br>
To use this action, you need to enable permission in the settings<br>`file menu > settings > advanced > javascript > settings > advanced permissions`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `message` | _String_ | Text message to send to the Holyrics chat |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Returns **false** if the message is not sent. For example, if the permission is not enabled. |


**Example:**

```javascript
h.chat.sendMessage("Hello");
```

---


### identifyVerseReferences(value, languageID = null)
- v2.23.0

Identifies possible biblical references in the provided text

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Text for identification |
| `languageID` | _String (optional)_ | Language ID of the book set.<br>If an ID is not provided, the list of books from the main Bible selected in the program will be used.<br>To get the list of available IDs, see: `h.getAvailableBibleBooks()` |


**Response:**

| Type  |
| :---: |
| _Array&lt;[VerseReferenceGroup](#verse-reference-group)&gt;_ | 


**Example:**

```javascript
var r = h.identifyVerseReferences("... ... Rm 12:2  Gn 1:1-3  Ps 23 ... ...");
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

Returns the list of available book sets in different languages



**Response:**

| Type  |
| :---: |
| _Array&lt;[BibleBookList](#bible-book-list)&gt;_ | 


**Example:**

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

Returns a set of Bible books

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `languageID` | _String_ | Language ID of the book set |


**Response:**

| Type  |
| :---: |
| _Array&lt;[BibleBookInfo](#bible-book-info)&gt;_ | 


**Example:**

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

Returns the information of a receiver or **null** if not found

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Receiver ID or name |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `type` | _String_ | Type of item |
| `name` | _String_ | Item name |


**Example:**

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



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ | Storage key used to save and retrieve the value of items.<br>`h.getGlobal(key, ...)`<br>`h.restore(key, ...)` |
| `fromStore` | _Boolean_ | **true** to retrieve the value also in `h.restore(key, ...)` `Default: true` |
| `inputs` | _Array&lt;[InputParam](https://github.com/holyrics/Scripts/blob/main/i18n/en/InputParam.md)&gt;_ | Object with previously stored values, where each key is the `id` of the respective `input`.<br>The value defined in `default_value` of each item will be returned if there is no previously stored value |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Object with previously stored values, where each key is the `id` of the respective `input`.<br>The value defined in `default_value` of each item will be returned if there is no previously stored value |


**Example:**

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

Creates a WebSocket connection. May generate Exception.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `receiver` | _String_ | Accepted values<br>Receiver ID or name<br>Host or destination IP, if added to the list of allowed requests<br>`file menu > settings > advanced > javascript > settings > allowed requests` |
| `cacheID` | _String (optional)_ | ID used as a value to obtain the existing connection, instead of creating a new one |
| `modelToCreate` | _Object (optional)_ | Actions used when creating a new connection |
| `modelToCreate.headers` | _Object (optional)_ |  |
| `modelToCreate.on_open` | _Function (optional)_ | Executed when the connection starts<br>`function(evt) { /* evt.source; evt.http_status; evt.http_status_message; */ }` |
| `modelToCreate.on_message` | _Function_ | Executed for each new message received<br>The `message` object is of the type:  string<br>`function(message) { ... }` |
| `modelToCreate.on_error` | _Function (optional)_ | Executed when an error occurs<br>`function(evt) { /* evt.source; evt.error; */ }` |
| `modelToCreate.on_close` | _Function (optional)_ | Executed when the connection is closed<br>`function(evt) { /* evt.source; evt.code; evt.reason; */ }` |
| `modelToCreate.loop` | _Function (optional)_ | Executed every 1 second while the connection is open<br>Useful for connections that need to send a 'ping' to keep the connection open<br>`function(evt) { /* evt.source; */ }` |


**Response:**

| Type  |
| :---: |
| _[WebSocketClient](https://github.com/holyrics/jslib/blob/main/doc/en/WebSocketClient.md)_ | 


**Example:**

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

Creates a TCP connection. May generate Exception.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `receiver` | _String_ | Accepted values<br>Receiver ID or name<br>Host or destination IP, if added to the list of allowed requests<br>`file menu > settings > advanced > javascript > settings > allowed requests` |
| `cacheID` | _String (optional)_ | ID used as a value to obtain the existing connection, instead of creating a new one |
| `modelToCreate` | _Object (optional)_ | Actions used when creating a new connection |
| `modelToCreate.on_message` | _Function_ | Executed for each new message received<br>The `message` object is of the type:  [ByteBufferReader](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferReader.md)<br>`function(message) { ... }` |
| `modelToCreate.on_close` | _Function (optional)_ | Executed when the connection is closed<br>`function(evt) { /* evt.source; */ }` |


**Response:**

| Type  |
| :---: |
| _[TCPClient](https://github.com/holyrics/jslib/blob/main/doc/en/TCPClient.md)_ | 


**Example:**

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


### process(file, input = null)
- v2.24.0

Starts a process in the operating system from a file in the program's library.<br>
Compatible with: `bat`  `exe`  `sh`<br>
The file (or extension) must be on the execution whitelist<br>
May generate Exception

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `file` | _String_ | File that will be executed. The file must be in the respective 'files' tab of the program's library (or in a subfolder). |
| `input` | _Object (optional)_ |  |
| `input.cli` | _Array&lt;String&gt;_ | Arguments that will be passed in the execution of the file |
| `input.on_message` | _Function_ | Executed for each new message received `stdout`<br>The `message` object is of the type:  [ByteBufferReader](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferReader.md)<br>`function(message) { ... }` |
| `input.on_error` | _Function_ | Executed for each new message received `stderr`<br>The `message` object is of the type:  [ByteBufferReader](https://github.com/holyrics/jslib/blob/main/doc/en/ByteBufferReader.md)<br>`function(message) { ... }` |
| `input.on_finish` | _Function_ | Executed when the process ends<br>`function(result) { }`<br>If `result` is a number, it is the exit code of the execution; if it is a `string`, it is the error message, for example, 'timeout' |
| `input.timeout` | _Number_ | Maximum time for process execution `Default: 5000` |


**Response:**

| Type  |
| :---: |
| _[Process](https://github.com/holyrics/jslib/blob/main/doc/en/Process.md)_ | 


**Example:**

```javascript
var p = h.process('filename.exe', {
  cli: ['param 1', 'param 2'],
  on_message: function(msg) {
    h.log(msg.readString());
  },
  on_error: function(msg) {
    h.log("error: " + msg.readString());
  },
  on_finish: function(code) {
    //todo
  },
  timeout: 10000
});
p.send('example');
p.await();
```

---


### executeCmdAndWait(file, cli = null, timeout = 5000)
- v2.24.0

Alternative request for `h.process(...)` using a more compact and direct approach

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `file` | _String_ | File that will be executed. The file must be in the respective 'files' tab of the program's library (or in a subfolder). |
| `cli` | _Array&lt;String&gt;_ | Arguments that will be passed in the execution of the file |
| `timeout` | _Number_ | Maximum time for process execution `Default: 5000` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Object_ |  |
| `data.status` | _Object_ | Can be: `ok` `error` |
| `data.data` | _Object_ | `data.code` Exit code or error message<br>`data.output` Full text received from the executed process `stdout`<br>`data.error` Full text received from the executed process `stderr` |
| `data.error` | _Object_ | Error message |


**Example:**

```javascript
var r = h.executeCmdAndWait('filename.exe', ['param 1', 'param 2'], 3000);
//r.status
//r.error //can be null
//r.data //can be null
//r.data.code
//r.data.output
//r.data.error
```

---


### triggerHotkey(id)
- v2.24.0

Executes the corresponding action available in the shortcut keys window.<br>
The list of actions is available at:  `menu ajuda > teclas de atalho`<br>
The action ID can be obtained by right-clicking on the action name in the respective **Action** column<br>
Observation: This method does not simulate pressing the shortcut key, it only executes the action based on the action id, regardless of the associated shortcut key.<br>


**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | `false` for ID not found |


**Example:**

```javascript
h.triggerHotkey('favorites_enable_disable');
```

---


### isAllowedExtensionToExecute(extension)
- v2.24.0

Checks if the extension is on the permission list for execution

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `extension` | _String_ |  |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
var r = h.isAllowedExtensionToExecute('exe');
```

---


### isAllowedFileToExecute(file)
- v2.24.0

Checks if a file from the files tab is on the permission list for execution

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `file` | _String_ | File name (including subfolder) |


**Response:**

| Type  |
| :---: |
| _Boolean_ | 


**Example:**

```javascript
var r = h.isAllowedFileToExecute('filename.exe');

var r = h.isAllowedFileToExecute('folder/filename.exe');
```

---


### getAvailableFontFamilyNames()
- v2.24.0

Returns the list of available sources in the system



**Response:**

| Type  |
| :---: |
| _Array&lt;String&gt;_ | 


---


### hlyOrThrow(action, input = null)
- v2.25.0

Alternative method for `hly(action, input)`, but it returns the `data` object directly and raises an exception if `status=error`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | Action name |
| `input` | _Object (optional)_ | Action parameters |


**Response:**

| Type  |
| :---: |
| _Object_ | 


**Example:**

```javascript
var data = h.hlyOrThrow('GetLyrics', { id: '123' });
//the same as
var r = h.hly('GetLyrics', { id: '123' });
var data = r.data;
//throws exception if r.status === 'error'
```

---


# Methods HLY 


All requests for hly(...) methods return a default object:
| Name | Type  | Description |
| ---- | :---: | ------------|
| `status` | _String_ | It might be *'ok'* or *'error'* |
| `error` | _String (optional)_ | Error message if status equals *error* |
| `data` | _Object (optional)_ | Response content if *status* equals *ok* |


---


### hly('GetLyrics', input)
### hly('GetSong', input)
Returns a song.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Song ID |
| `input.fields` | _String (optional)_ | Comma-separated field names. If this field is declared, only the specified fields will be returned `v2.24.0+` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _[Lyrics](#lyrics)_ | Music or NULL if not found |


**Example:**

```javascript
var r = h.hly('GetLyrics', {id: '123'});
if (r.data == null) {
    h.log('Item 123 not found');
} else {
    h.log('Item 123:');
    h.log(r.data);
}
```

---


### hly('GetSongs', input)
- v2.21.0

Returns the list of songs

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.fields` | _String (optional)_ | Comma-separated field names. If this field is declared, only the specified fields will be returned `v2.24.0+` |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Lyrics](#lyrics)&gt;_| 


**Example:**

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
Performs a search in the user's lyrics list

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _String_ | Filter |
| `input.text` | _String_ | Text to be searched |
| `input.title` | _Boolean (optional)_ |  `Default: true` |
| `input.artist` | _Boolean (optional)_ |  `Default: true` |
| `input.note` | _Boolean (optional)_ |  `Default: true` |
| `input.lyrics` | _Boolean (optional)_ |  `Default: false` |
| `input.group` | _String (optional)_ |  |
| `input.fields` | _String (optional)_ | Comma-separated field names. If this field is declared, only the specified fields will be returned `v2.24.0+` |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Lyrics](#lyrics)&gt;_| 


**Example:**

```javascript
var r = h.hly('SearchLyrics', {
    text: 'example',
    lyrics: true
});
if (r.data.length == 0) {
    h.log("No results found");
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
Starts a lyric show.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |
| `input.initial_index` | _Number (optional)_ | Initial index of the presentation `Default: 0` `v2.23.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowLyrics', {id: '123'});

//search for a song and execute the first result found
var r = h.hly('SearchLyrics', {
    text: 'song title'
});
if (r.data.length == 0) {
    h.log("Music not found");
} else {
    h.hly('ShowLyrics', {id: r.data[0].id});
}

//Alternate calls
h.showLyrics('123');
h.showSong('123');
```

---


### hly('GetText', input)
- v2.21.0

Returns a text.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Text ID |
| `input.fields` | _String (optional)_ | Comma-separated field names. If this field is declared, only the specified fields will be returned `v2.24.0+` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _[Text](#text)_ | Text or NULL if not found |


**Example:**

```javascript
var r = h.hly('GetText', {id: '123'});
if (r.data == null) {
    h.log('Item 123 not found');
} else {
    h.log('Item 123:');
    h.log(r.data);
}
```

---


### hly('GetTexts', input)
- v2.21.0

Returns the list of texts

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.fields` | _String (optional)_ | Comma-separated field names. If this field is declared, only the specified fields will be returned `v2.24.0+` |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Text](#text)&gt;_| 


**Example:**

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

Performs a search in the user's text list

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _String_ | Filter |
| `input.text` | _String_ | Text to be searched |
| `input.fields` | _String (optional)_ | Comma-separated field names. If this field is declared, only the specified fields will be returned `v2.24.0+` |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Lyrics](#lyrics)&gt;_| 


**Example:**

```javascript
var r = h.hly('SearchText', {
    text: '...'
});
if (r.data.length == 0) {
    h.log("Item not found");
} else {
    h.hly('ShowText', {id: r.data[0].id});
}
```

---


### hly('ShowText', input)
Starts a presentation of a text tab item.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |
| `input.initial_index` | _Number (optional)_ | Initial index of the presentation `Default: 0` `v2.23.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowText', {id: 'abc'});

//Alternate call
h.showText('abc');
```

---


### hly('ShowVerse', input)
Starts a Bible verse presentation.<br>Note: It is possible to display a maximum of 100 different verses in a single request.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object_ | **id**, **ids** or **references** |
| `input.id` | _String (optional)_ | To display a verse. Item ID in BBCCCVVV format.<br/>Example: '19023001' (book 19, chapter 023, verse 001) |
| `input.ids` | _Array&lt;String&gt; (optional)_ | To display a list of verses. List with the ID of each verse.<br/>Example: ['19023001', '43003016', '45012002'] |
| `input.references` | _String (optional)_ | References. Example: **John 3:16** or **Rm 12:2** or **Gn 1:1-3 Sl 23.1** |
| `input.version` | _String (optional)_ | Name or abbreviation of the translation used `v2.21.0+` |
| `input.quick_presentation` | _Boolean (optional)_ | `true` to display the verse through a quick presentation popup window.<br>Allows, for example, to start the presentation of a verse without ending the current presentation, returning to the current presentation when the verse presentation ends. `Default: false` `v2.24.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowVerse', {id: '19023001'});

h.hly('ShowVerse', {ids: ['19023001', '43003016', '45012002']});

h.hly('ShowVerse', {references: 'John 3:16'});

h.hly('ShowVerse', {
    references: 'Rm 12:2  Gn 1:1-3  Ps 23',
    version: 'en_kjv'
});

//Alternate call
h.showVerse('Rm 12:2  Gn 1:1-3  Ps 23');
```

---


### hly('GetAudios', input)
### hly('GetVideos', input)
### hly('GetImages', input)
### hly('GetFiles', input) `v2.21.0+`
- v2.19.0

Returns the list of files from the respective tab: audio, video, image, file

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.folder` | _String (optional)_ | Subfolder name to list files |
| `input.filter` | _String (optional)_ | Filter files by name |
| `input.include_metadata` | _Boolean (optional)_ | Add metadata to the response `Default: false` `v2.22.0+` |
| `input.include_thumbnail` | _Boolean (optional)_ | Add thumbnail to response (80x45) `Default: false` `v2.22.0+` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.name` | _String_ | Item name |
| `data.*.isDir` | _Boolean_ | Return **true** if it's a folder or **false** if it's a file. |
| `data.*.properties` | _Object_ | Map with the custom properties defined for the file `v2.24.0+` |
| <br>Available if **include_metadata=true** |  |  |
| `data.*.length` | _Number_ | File size (bytes). Available if **isDir=false** `v2.22.0+` |
| `data.*.modified_time` | _String_ | File modification date. Date and time format: YYYY-MM-DD HH:MM `v2.22.0+` |
| `data.*.modified_time_millis` | _String_ | File modification date. (timestamp) `v2.24.0+` |
| `data.*.duration_ms` | _Number_ | File duration. Available if the file is: audio or vídeo `v2.22.0+` |
| `data.*.width` | _Number_ | Width. Available if the file is: imagem or vídeo `v2.22.0+` |
| `data.*.height` | _Number_ | Height. Available if the file is: imagem or vídeo `v2.22.0+` |
| `data.*.position` | _String_ | Image adjustment. Available for images. Can be: `adjust` `extend` `fill` `v2.22.0+` |
| `data.*.blur` | _Boolean_ | Apply blur effect `v2.22.0+` |
| `data.*.transparent` | _Boolean_ | Display images with transparency `v2.22.0+` |
| `data.*.last_executed_time` | _String_ | Date of the last execution of the file. Date and time format: YYYY-MM-DD HH:MM `v2.24.0+` |
| `data.*.last_executed_time_millis` | _Number_ | Date of the last execution of the file. (timestamp) `v2.24.0+` |
| <br>Available if **include_thumbnail=true** |  |  |
| `data.*.thumbnail` | _String_ | Image in base64 format `v2.22.0+` |


**Example:**

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


### hly('GetAudio', input)
### hly('GetVideo', input)
### hly('GetImage', input)
### hly('GetFile', input)
- v2.24.0

Returns the data of a file from the list of files in the respective tab: audio, video, image, file

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.name` | _String_ | File name (including subfolder) |
| `input.include_metadata` | _Boolean (optional)_ | Add metadata to the response `Default: false` |
| `input.include_thumbnail` | _Boolean (optional)_ | Add thumbnail to response (80x45) `Default: false` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Object_ |  |
| `data.name` | _String_ | Item name |
| `data.isDir` | _Boolean_ | Return **true** if it's a folder or **false** if it's a file. |
| `data.properties` | _Object_ | Map with the custom information saved in the file |
| <br>Available if **include_metadata=true** |  |  |
| `data.length` | _Number_ | File size (bytes). Available if **isDir=false** |
| `data.modified_time` | _String_ | File modification date. Date and time format: YYYY-MM-DD HH:MM |
| `data.modified_time_millis` | _Number_ | File modification date. (timestamp) |
| `data.duration_ms` | _Number_ | File duration. Available if the file is: audio or vídeo |
| `data.width` | _Number_ | Width. Available if the file is: imagem or vídeo |
| `data.height` | _Number_ | Height. Available if the file is: imagem or vídeo |
| `data.position` | _String_ | Image adjustment. Available for images. Can be: `adjust` `extend` `fill` |
| `data.blur` | _Boolean_ | Apply blur effect |
| `data.transparent` | _Boolean_ | Display images with transparency |
| `data.last_executed_time` | _String_ | Date of the last execution of the file. Date and time format: YYYY-MM-DD HH:MM |
| `data.last_executed_time_millis` | _Number_ |  |
| <br>Available if **include_thumbnail=true** |  |  |
| `data.thumbnail` | _String_ | Image in base64 format |


**Example:**

```javascript
var r = h.hly('GetAudio', {
    name: 'audio.mp3'
});
```

---


### hly('SetAudioItemProperty', input)
### hly('SetVideoItemProperty', input)
### hly('SetImageItemProperty', input)
### hly('SetFileItemProperty', input)
- v2.24.0

Changes the custom information of a file

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.name` | _String_ | File name (including subfolder) |
| `input.properties` | _Object_ | Key/value map with the information that will be changed. The passed values will be MERGED with the existing values. That is, it is not necessary to send parameters that will not be changed (or removed). |


_Method does not return value_

**Example:**

```javascript
h.hly('SetAudioItemProperty', {
    name: 'audio.mp3',
    properties: {
        key: 'value 1',
        abc: 'value 2',
        example: 'value 3'
    }
});
```

---


### hly('PlayAudio', input)
Play an audio or a list of audios (folder)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | File or folder name. Example: **file.mp3** or **folder** or **folder/file.mp3** |
| `input.settings` | _[PlayMediaSettings](#play-media-settings) (optional)_ | Settings for media execution `v2.21.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('PlayAudio', {file: 'file.mp3'});
h.hly('PlayAudio', {file: 'folder'});
h.hly('PlayAudio', {
    file: 'folder/file.mp3',
    settings: {
        stop_time: "2:10",
        repeat: true
    }
});

//Alternate call
h.playAudio('file.mp3');

h.playAudio('file.mp3', {
    volume: 90,
    start_time: '30'
});

//throws exception for runtime error
h.playAudioEx('file.mp3');
```

---


### hly('PlayVideo', input)
Play a video or a list of videos (folder)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | File or folder name. Example: **file.mp4** or **folder** or **folder/file.mp4** |
| `input.settings` | _[PlayMediaSettings](#play-media-settings) (optional)_ | Settings for media execution `v2.21.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('PlayVideo', {file: 'file.mp4'});
h.hly('PlayVideo', {
    file: 'folder',
    settings: {
        shuffle: true
    }
});
h.hly('PlayVideo', {file: 'folder/file.mp4'});

//Alternate call
h.playVideo('file.mp4');

h.playVideo('file.mp4', {
    volume: 0,
    repeat: true
});

//throws exception for runtime error
h.playVideoEx('file.mp4');
```

---


### hly('ShowImage', input)
Displays an image or a list of images (folder)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | File or folder name. Example: **file.jpg** or **folder** or **folder/file.jpg** |
| `input.automatic` | _[Automatic](#automatic) (optional)_ | If informed, the presentation of the items will be automatic |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowImage', {file: 'file.jpg'});
h.hly('ShowImage', {file: 'folder'});
h.hly('ShowImage', {file: 'folder/file.jpg'});

h.hly('ShowImage', {
    file: 'folder',
    automatic: {
        seconds: 5,
        repeat: true
    }
});

//Alternate call
h.showImage('file.jpg');

//throws exception for runtime error
h.showImageEx('file.jpg');
```

---


### hly('ExecuteFile', input)
- v2.21.0

Executes a file. Only safe extensions or those added to the exception list.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | File name |


_Method does not return value_

**Example:**

```javascript
h.hly('ExecuteFile', {
    file: 'file.txt'
});

//Alternate call
h.executeFile("file.txt");

//throws exception for runtime error
h.executeFileEx('file.txt');
```

---


### hly('AudioExists', input)
### hly('VideoExists', input)
### hly('ImageExists', input)
### hly('FileExists', input)
- v2.21.0

Checks if there is a file with the informed name

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | File name |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Boolean_| 


**Example:**

```javascript
var r = h.hly('AudioExists', {file: 'audio.mp3'});
if (r.data) {
    //exists
}
h.hly('VideoExists', {file: 'video.mp4'});
h.hly('ImageExists', {file: 'image.jpg'});
h.hly('FileExists', {file: 'file.txt'});

//Alternate call
if (h.audioExists("audio.mp3")) {
    //exists
}
h.videoExists("video.mp4");
h.imageExists("image.jpg");
h.fileExists("file.txt");
```

---


### hly('ShowAnnouncement', input)
Displays an announcement or a list of announcements

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Announcement ID. Can be **all** to display all |
| `input.ids` | _Array&lt;String&gt; (optional)_ | List with the ID of each announcement |
| `input.name` | _String (optional)_ | Announcement name |
| `input.names` | _Array&lt;String&gt; (optional)_ | List with the name of each announcement |
| `input.automatic` | _[Automatic](#automatic) (optional)_ | If informed, the presentation of the items will be automatic |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowAnnouncement', {id: '123'});

h.hly('ShowAnnouncement', {
    names: ['Announcement 1', 'Announcement 2', 'Announcement 3'],
    automatic: {
        seconds: 10,
        repeat: true
    }
});
```

---


### hly('GetCustomMessages')
- v2.19.0

List of custom messages



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[CustomMessage](#custom-message)&gt;_| 


**Example:**

```javascript
var r = h.hly('GetCustomMessages');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('ShowCustomMessage', input)
- v2.19.0

Display a custom message. Note: A custom message is not displayed directly on the screen. a notification is created in the corner of the screen for the operator to accept and display.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.name` | _String_ | custom message name |
| `input.position_?` | _Object (optional)_ | Variable added at the specified position according to the value returned in **variables.*.position** of the CustomMessage class. |
| `input.params` | _Object (optional)_ | Alternative method. Key/value map where the key is the field name **variables.*.name** of the CustomMessage class. If necessary to add the same parameter, add `*_n` at the end of the name, starting at 2<br>Example: **input.params.name, input.params.name_2, input.params.name_3** `v2.21.0+` |
| `input.note` | _String_ | Extra information displayed in popup window for operator |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowCustomMessage', {
    name: 'name',
    position_15: 'Value 1',
    position_28: 'Value 2',
    note: 'Urgently'
});

h.hly('ShowCustomMessage', {
    name: 'name',
    params: {
        abc: 'Value 1',
        xyz: 'Value 2',
        aaa: 'Value 3',
        abc_2: 'Value 4'
    },
    note: 'Urgently'
});
```

---


### hly('ShowQuickPresentation', input)
Quick display of text

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String_ | Text that will be displayed [Styled Text](https://github.com/holyrics/Scripts/blob/main/i18n/en/StyledText.md) from v2.19.0<br>Optional if `slides` is declared |
| `input.slides` | _Array&lt;[QuickPresentationSlide](#quick-presentation-slide)&gt;_ | Alternative parameter for more complex presentations<br>Optional if `text` is declared `v2.23.0+` |
| `input.theme` | _[ThemeFilter](#theme-filter) (optional)_ | Filter selected theme for display |
| `input.custom_theme` | _[Theme](#theme) (optional)_ | Custom theme used to display the text `v2.21.0+` |
| `input.automatic` | _[Automatic](#automatic) (optional)_ | If informed, the presentation of the items will be automatic |
| `input.initial_index` | _Number (optional)_ | Initial index of the presentation `Default: 0` `v2.23.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('ShowQuickPresentation', {
    text: "Text to be displayed"
});

h.hly('ShowQuickPresentation', {
    text: "Slide 1\n\nSlide 2\n\nSlide 3",
    theme: {
        name: "Theme 3",
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
    text: "Text to be displayed",
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
            text: "Text to be displayed (1)",
            theme: {
                name: "Theme 1"
            }
        }, {
            text: "Text to be displayed (2)",
            duration: 20,
            translations: {
                "translation_name_1": "Example",
                "translation_name_2": "Example"
            }
        }, {
            text: "Text to be displayed (3)",
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
        name: "Theme"
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

Display a countdown on the public screen

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.time` | _String_ | HH:MM or MM:SS |
| `input.exact_time` | _Boolean (optional)_ | If **true**, `time` should be HH:MM (exact hour and minute). If **false**, `time` should be MM:SS (amount of minutes and seconds) `Default: false` |
| `input.text_before` | _String (optional)_ | Text displayed at the top of the countdown |
| `input.text_after` | _String (optional)_ | Text displayed at the bottom of the countdown |
| `input.zero_fill` | _Boolean (optional)_ | Fill in the 'minute' field with zero on the left `Default: false` |
| `input.hide_zero_minute` | _Boolean (optional)_ | Hide the display of minutes when it is zero `Default: false` `v2.25.0+` |
| `input.countdown_relative_size` | _Number (optional)_ | Relative size of the countdown `Default: 250` |
| `input.theme` | _[ThemeFilter](#theme-filter) (optional)_ | Filter selected theme for display `v2.21.0+` |
| `input.countdown_style` | _[FontSettings](#font-settings) (optional)_ | Custom font for countdown `v2.21.0+` |
| `input.custom_theme` | _[Theme](#theme) (optional)_ | Custom theme `v2.21.0+` |


_Method does not return value_

**Example:**

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

Start a multiple choice presentation

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.questions` | _Array&lt;[QuizQuestion](#quiz-question)&gt;_ | Questions to display |
| `input.settings` | _[QuizSettings](#quiz-settings)_ | Settings |


_Method does not return value_

**Example:**

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

Execute an action in a multiple choice presentation

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.action` | _String (optional)_ | One of the following values: `previous_slide`  `next_slide`  `previous_question`  `next_question`  `show_result`  `close` |
| `input.hide_alternative` | _Number (optional)_ | Hide an alternative. Starts at 1 |
| `input.select_alternative` | _Number (optional)_ | Select an alternative. Starts at 1 |
| `input.countdown` | _Number (optional)_ | Start a countdown. [1-120] |


_Method does not return value_

**Example:**

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

Returns the list of automatic presentations



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.name` | _String_ | File name. Example: **file.ap** |


**Example:**

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

Returns an automatic presentation

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | File name. Example: **file.ap** |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _[AutomaticPresentation](#automatic-presentation)_| 


**Example:**

```javascript
var r = h.hly('GetAutomaticPresentation', {file: 'file.ap'});
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

Play an automatic presentation item

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String_ | File name. Example: **file.ap** |
| `input.theme` | _Object (optional)_ | Filter selected theme for display |
| `input.theme.id` | _String (optional)_ | Theme ID |
| `input.theme.name` | _String (optional)_ | Theme name |
| `input.theme.edit` | _[Theme](#theme) (optional)_ | Settings to modify the selected Theme for display `v2.21.0+` |
| `input.custom_theme` | _[Theme](#theme) (optional)_ | Custom theme used to display the automatic presentation `v2.21.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('PlayAutomaticPresentation', {file: 'file.ap'});

h.hly('PlayAP', {file: 'file.ap'});

h.hly('PlayAP', {
    file: 'file.ap',
    theme: {
        name: "Theme 3"
    }
});

//Alternate calls
h.playAutomaticPresentation('file.ap');
h.playAP('file.ap');
```

---


### hly('GetAutomaticPresentationPlayerInfo')
### hly('GetAPPlayerInfo')
- v2.20.0

Returns the information of the automatic presentation on display



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.name` | _String_ | Item name |
| `data.playing` | _Boolean_ | Checks if the player is running |
| `data.time_ms` | _Number_ | Current media time in milliseconds |
| `data.volume` | _Number_ | Current player volume. Minimum=0, Maximum=100 |
| `data.mute` | _Boolean_ | Checks if the **mute** option is enabled |
| `data.duration_ms` | _Number_ | Total time in milliseconds `v2.21.0+` |


**Example:**

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

Perform actions in the player

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.action` | _String (optional)_ | Name of the action that will be performed on the player. play, pause, stop |
| `input.volume` | _Number (optional)_ | Change the volume of the player. Minimum=0, Maximum=100 |
| `input.mute` | _Boolean (optional)_ | Change the **mute** option |
| `input.time_ms` | _Boolean (optional)_ | Change the current media time in milliseconds |


_Method does not return value_

**Example:**

```javascript
h.hly('AutomaticPresentationPlayerAction', {
    action: 'play',
    volume: 80
});
```

---


### hly('GetMediaPlayerInfo')
Returns player information



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.name` | _String_ | Name of current media in player |
| `data.path` | _String_ | Full path of media in player |
| `data.relative_path` | _String_ | Relative path of the media in the player. Can be null. `v2.24.0+` |
| `data.playing` | _Boolean_ | Checks if the player is running |
| `data.duration_ms` | _Number_ | Total time in milliseconds |
| `data.time_ms` | _Number_ | Current media time in milliseconds |
| `data.time_elapsed` | _String_ | Elapsed time in format HH:MM:SS |
| `data.time_remaining` | _String_ | Remaining time in format HH:MM:SS |
| `data.volume` | _Number_ | Current player volume. Minimum=0, Maximum=100 |
| `data.mute` | _Boolean_ | Checks if the **mute** option is enabled |
| `data.repeat` | _Boolean_ | Checks if the **repeat** option is enabled |
| `data.execute_single` | _Boolean_ | Checks if the player is set to play only the current list item |
| `data.shuffle` | _Boolean_ | Checks if the **random** option is enabled |
| `data.fullscreen` | _Boolean_ | Checks if the **full screen** option is enabled |


**Example:**

```javascript
var r = h.hly('GetMediaPlayerInfo');
if (r.data.playing) {
    h.log('The player is running');
} else {
    h.log('The player is not running');
}
```

---


### hly('MediaPlayerAction', input)
- v2.19.0

Perform actions in the player

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.action` | _String (optional)_ | Name of the action that will be performed on the player. play, pause, stop, next, previous |
| `input.volume` | _Number (optional)_ | Change the volume of the player. Minimum=0, Maximum=100 |
| `input.mute` | _Boolean (optional)_ | Change the **mute** option |
| `input.repeat` | _Boolean (optional)_ | Change the **repeat** option |
| `input.shuffle` | _Boolean (optional)_ | Change the **random** option |
| `input.execute_single` | _Boolean (optional)_ | Change player setting to play only current list item |
| `input.fullscreen` | _Boolean (optional)_ | Change player **full screen** option |
| `input.time_ms` | _Boolean (optional)_ | Change the current media time in milliseconds `v2.20.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('MediaPlayerAction', {
    mute: false,
    repeat: true,
    volume: 80,
    action: 'play'
});

//change volume
h.hly('MediaPlayerAction', {volume: 80});

//mute
h.hly('MediaPlayerAction', {mute: true});

//stop current execution
h.hly('MediaPlayerAction', {action: 'stop'});
```

---


### hly('GetLyricsPlaylist')
### hly('GetSongPlaylist')
Lyrics playlist



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Lyrics](#lyrics)&gt;_| 


**Example:**

```javascript
var r = h.hly('GetLyricsPlaylist');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].title);
}
```

---


### hly('AddLyricsToPlaylist', input)
### hly('AddSongsToPlaylist', input)
Add song lyrics to playlist

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Lyrics ID |
| `input.ids` | _Array&lt;String&gt; (optional)_ | List with id of each lyics |
| `input.index` | _Number (optional)_ | Position in the list where the item will be added (starts at zero). Items are added to the end of the list by default. `Default: -1` |
| `input.media_playlist` | _Boolean (optional)_ | Add the lyrics to the media playlist `Default: false` |


_Method does not return value_

**Example:**

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
Remove lyrics from playlist

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Lyrics ID |
| `input.ids` | _Array&lt;String&gt; (optional)_ | List with id of each lyics |
| `input.index` | _Number (optional)_ | Position of the item in the list to be removed (starts at zero). |
| `input.indexes` | _Array&lt;Number&gt; (optional)_ | List with the position of each item in the list that will be removed. (Starts at zero) |


_Method does not return value_

**Example:**

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

Change a Lyrics Playlist Item

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.index` | _Number_ | Index of the item in the list |
| `input.song_id` | _String_ | New item |


_Method does not return value_

**Example:**

```javascript
h.hly('SetLyricsPlaylistItem', {
    index: 2,
    song_id: '123'
});
```

---


### hly('GetMediaPlaylist')
Media playlist



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Item](#item)&gt;_| 


**Example:**

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

Change a media playlist item

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.index` | _Number_ | Index of the item in the list |
| `input.item` | _[AddItem](#add-item)_ | New item |


_Method does not return value_

**Example:**

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
Play a media playlist item

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |


_Method does not return value_

**Example:**

```javascript
h.hly('MediaPlaylistAction', {id: 'abc'});

//Alternate calls
h.mediaPlaylistAction('abc');
h.mplAction('abc');
```

---


### hly('GetNextSongPlaylist')
- v2.22.0

Returns the next song in the playlist. Can be null



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _[Lyrics](#lyrics)_| 


**Example:**

```javascript
var r = h.hly('GetNextSongPlaylist');
```

---


### hly('GetNextMediaPlaylist')
- v2.22.0

Returns the next executable item from the media playlist. Can be null



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _[Item](#item)_| 


**Example:**

```javascript
var r = h.hly('GetNextMediaPlaylist');
```

---


### hly('ShowNextSongPlaylist')
- v2.22.0

Play the next song in the playlist



_Method does not return value_

**Example:**

```javascript
h.hly('ShowNextSongPlaylist');
```

---


### hly('ShowNextMediaPlaylist')
- v2.22.0

Plays the next item in the media playlist



_Method does not return value_

**Example:**

```javascript
h.hly('ShowNextMediaPlaylist');
```

---


### hly('GetPreviousSongPlaylist')
- v2.22.0

Returns the previous song in the playlist. Can be null



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _[Lyrics](#lyrics)_| 


**Example:**

```javascript
var r = h.hly('GetPreviousSongPlaylist');
```

---


### hly('GetPreviousMediaPlaylist')
- v2.22.0

Returns the previous executable item from the media playlist. Can be null



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _[Item](#item)_| 


**Example:**

```javascript
var r = h.hly('GetPreviousMediaPlaylist');
```

---


### hly('ShowPreviousSongPlaylist')
- v2.22.0

Play the previous song in the playlist



_Method does not return value_

**Example:**

```javascript
h.hly('ShowPreviousSongPlaylist');
```

---


### hly('ShowPreviousMediaPlaylist')
- v2.22.0

Plays the previous item in the media playlist



_Method does not return value_

**Example:**

```javascript
h.hly('ShowPreviousMediaPlaylist');
```

---


### hly('AddToPlaylist', input)
- v2.20.0

Add items to the media playlist

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.items` | _Array&lt;[AddItem](#add-item)&gt;_ | List with the items that will be added |
| `input.index` | _Number (optional)_ | Position in the list where the item will be added (starts at zero). Items are added to the end of the list by default. `Default: -1` |
| `input.ignore_duplicates` | _Boolean (optional)_ | Do not duplicate items when adding new items, that is, do not add an item if it is already on the list. `Default: false` |


_Method does not return value_

**Example:**

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
        name: 'Title',
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
        name: 'Title 2'
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
        name: 'Title 3'
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
Remove items from media playlist

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Item ID |
| `input.ids` | _Array&lt;String&gt; (optional)_ | List with id of each item |
| `input.index` | _Number (optional)_ | Position of the item in the list to be removed (starts at zero). |
| `input.indexes` | _Array&lt;Number&gt; (optional)_ | List with the position of each item in the list that will be removed. (Starts at zero) |


_Method does not return value_

**Example:**

```javascript
h.hly('RemoveFromMediaPlaylist', {id: 'abc'});

h.hly('RemoveFromMediaPlaylist', {ids: ['abc', 'xyz']});

h.hly('RemoveFromMediaPlaylist', {index: 3});

h.hly('RemoveFromMediaPlaylist', {indexes: [3, 4, 5]});
```

---


### hly('SetPlaylistItemDuration', input)
- v2.21.0

Change duration of an item in the media playlist.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Item ID |
| `input.index` | _Number (optional)_ | Item position in the list (starts at zero). |
| `input.duration` | _Number (optional)_ | Item duration (in seconds) |


_Method does not return value_

**Example:**

```javascript
h.hly('SetPlaylistItemDuration', {
    id: 'abc',
    duration: 300
});
```

---


### hly('GetSlideDescriptions')
- v2.21.0

List of available slide descriptions



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[SlideDescription](#slide-description)&gt;_| 


**Example:**

```javascript
var r = h.hly('GetSlideDescriptions');
for (var i = 0; i < r.data.length; i++) {
    var s = r.data[i];
    h.log("", "Name: {}, Tag: {}", [s.name, s.tag]);
}
```

---


### hly('GetFavorites')
Favorites bar items



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[FavoriteItem](#favorite-item)&gt;_| 


**Example:**

```javascript
var r = h.hly('GetFavorites');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('FavoriteAction', input)
Execute an item from the bookmarks bar

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |


_Method does not return value_

**Example:**

```javascript
h.hly('FavoriteAction', {id: 'abc'});

//Alternate calls
h.favoriteAction('abc');
h.favAction('abc');
```

---


### hly('GetApis')
- v2.21.0

Returns the list of APIs



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.id` | _String_ | Item ID |
| `data.*.name` | _String_ | Item name |


**Example:**

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

Returns the list of scripts



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.id` | _String_ | Item ID |
| `data.*.name` | _String_ | Item name |


**Example:**

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

Executes the action of an existing API item in the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |


_Method does not return value_

**Example:**

```javascript
var r = h.hly('ApiAction', {id: 'abcxyz'});

if (r.status == 'ok') {
    h.log('Action performed');
} else {
    h.log('Error: ' + r.error);
}
```

---


### hly('ScriptAction', input)
- v2.19.0

Executes the action of an existing **Script** item in the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID |


_Method does not return value_

**Example:**

```javascript
var r = h.hly('ScriptAction', {id: 'abcxyz'});

if (r.status == 'ok') {
    h.log('Action performed');
} else {
    h.log('Error: ' + r.error);
}
```

---


### hly('ApiRequest', input)
- v2.19.0

Executes a request to the associated receiver and returns the receiver's response.<br>
From `v2.23.0` it is possible to pass the host or IP directly, but it is necessary to add the host/IP to the list of allowed requests.<br>
file menu > settings > advanced > javascript > settings > allowed requests

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | receiver id |
| `input.raw` | _Object_ | requisition data |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Request return or NULL for error/timeout |


**Example:**

```javascript
//It is possible to make a request directly to a receiver created
//For example:
//Assuming you have a receiver created to communicate with OBS Studio via websocket and the receiver ID is 'abcyxz'
//you can make a request as in the example below
var r = h.hly('ApiRequest', {
    id: 'abcxyz',
    raw: {
        'request-type': 'GetSourceActive',
        'sourceName': 'example'
    }
});
if (r.status == 'ok') {
    h.log('Requisition response: ' + r.data);
    var obj = JSON.parse(r.data);
    if (obj.sourceActive) {
        h.log('The example source is active');
    } else {
        h.log('The example source is not active');
    }
} else {
    h.log('Error: ' + r.error);
}
```

---


### hly('GetCurrentPresentation', input)
- v2.19.0

Item currently being presented or **null** if no presentation is being displayed

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.include_slides` | _Boolean (optional)_ | Return the list of slides from the current presentation. Unavailable for verse presentation. `Default: false` `v2.21.0+` |
| `input.include_slide_comment` | _Boolean (optional)_ | Include comments (if any) in the slide text. Available if **include_slides=true**. `Default: false` `v2.21.0+` |
| `input.include_slide_preview` | _Boolean (optional)_ | Include slide preview image. Available if **include_slides=true**. `Default: false` `v2.21.0+` |
| `input.slide_preview_size` | _String (optional)_ | Preview size in WxH format (ex. 320x180). (max 640x360)<br>Available if **include_slide_preview=true** `Default: false` `v2.21.0+` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.id` | _String_ | Item ID |
| `data.type` | _String_ | Type of item. It can be: `song` `verse` `text` `audio` `image` `announcement` `automatic_presentation` `quick_presentation` |
| `data.name` | _String_ | Item name |
| `data.slide_number` | _Number_ | Starts at 1 `v2.20.0+` |
| `data.total_slides` | _Number_ | Total slides `v2.20.0+` |
| `data.slide_type` | _String_ | One of the following values: `default`  `wallpaper`  `blank`  `black`  `final_slide` `v2.20.0+` |
| `data.slides` | _Array&lt;[PresentationSlideInfo](#presentation-slide-info)&gt;_ | List with the slides of the current presentation. Available if **include_slides=true** `v2.21.0+` |


**Example:**

```javascript
var r = h.hly('GetCurrentPresentation');
if (r.data == null) {
    //there is no presentation currently showing
}

switch (r.data.type) {
    case 'song':
        //a song being performed
        break;
    case 'verse':
        //a verse being presented
        break;
}
```

---


### hly('CloseCurrentPresentation')
End current presentation



_Method does not return value_

**Example:**

```javascript
h.hly('CloseCurrentPresentation');
```

---


### hly('GetF8')
### hly('GetF9')
### hly('GetF10')
- v2.19.0

Returns the current state of the respective option **F8 (wallpaper), F9 (empty screen) or F10 (black screen)**



**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | **true** or **false** |


**Example:**

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

Changes the current state of the respective option **F8 (wallpaper), F9 (empty screen) or F10 (black screen)**

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.enable` | _Boolean_ | **true** or **false** |


_Method does not return value_

**Example:**

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

Changes the current state of the respective option **F8 (wallpaper), F9 (empty screen) or F10 (black screen)**



_Method does not return value_

**Example:**

```javascript
h.hly('ToggleF8');

h.hly('ToggleF9');

h.hly('ToggleF10');
```

---


### hly('ActionNext')
- v2.19.0

Performs a **next** command on the current presentation



_Method does not return value_

---


### hly('ActionPrevious')
- v2.19.0

Performs a **back** command on the current presentation



_Method does not return value_

---


### hly('ActionGoToIndex', input)
- v2.19.0

Changes the slide in view from the slide index

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.index` | _Number_ | Slide index in presentation (starts at zero) |


_Method does not return value_

**Example:**

```javascript
h.hly('ActionGoToIndex', {index: 3});
```

---


### hly('ActionGoToSlideDescription', input)
- v2.19.0

Changes the slide in view from the name of the slide description

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.name` | _String_ | Slide description name |


_Method does not return value_

**Example:**

```javascript
h.hly('ActionGoToSlideDescription', {name: 'Verse 1'});
```

---


### hly('GetCurrentBackground')
Returns the background of the currently displayed presentation.



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _[Background](#background)_ | Current background or NULL if no presentation is displayed |


**Example:**

```javascript
var r = h.hly('GetCurrentBackground');
if (r.data != null) {
    h.log('Current background ID: ' + r.data.id);
} else {
    h.log('There is no presentation on display');
}
```

---


### hly('GetCurrentTheme')
- v2.22.0

Returns the theme of the presentation currently displayed.



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _[Background](#background)_ | Current theme or NULL if there is no presentation displayed |


**Example:**

```javascript
var r = h.hly('GetCurrentTheme');
if (r.data != null) {
    h.log('Current theme ID: ' + r.data.id);
} else {
    h.log('There is no presentation on display');
}
```

---


### hly('GetBackgrounds', input)
List of themes and backgrounds

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object (optional)_ | Filter |
| `input.type` | _String (optional)_ | Can be: `theme` `my_video` `my_image` `video` `image` |
| `input.tag` | _String (optional)_ |  |
| `input.tags` | _Array&lt;String&gt; (optional)_ |  |
| `input.intersection` | _Boolean (optional)_ | If the **input.tags** field is populated with multiple items, the **input.intersection** option defines the type of junction. If **true**, the filter will only return items that contain **all** the informed tags, if **false**, the filter will return the items that have at least one tag of the informed tags `Default: false` |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Background](#background)&gt;_| 


**Example:**

```javascript
//all
var r = h.hly('GetBackgrounds', {});
for (var i = 0; i < r.data.length; i++) {
    var bg = r.data[i];
    h.log(bg.type + ": " + bg.name);
}

//only "My Videos" and tagged 'water' AND 'blue'
r = h.hly('GetBackgrounds', {
    type: 'my_video',
    tags: ['water', 'blue'],
    intersection: true
});
for (var i = 0; i < r.data.length; i++) {
    var bg = r.data[i];
    h.log(bg.name);
}
```

---


### hly('SetCurrentBackground', input)
Changes the background (or theme) of the current presentation. If more than one item is found according to the filters, random item will be chosen from the list

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _Object (optional)_ | Filter |
| `input.id` | _String (optional)_ | Theme or background ID |
| `input.name` | _String (optional)_ | Theme name or background |
| `input.type` | _String (optional)_ | Can be: `theme` `my_video` `my_image` `video` `image` |
| `input.tag` | _String (optional)_ |  |
| `input.tags` | _Array&lt;String&gt; (optional)_ |  |
| `input.intersection` | _Boolean (optional)_ | If the **input.tags** field is populated with multiple items, the **input.intersection** option defines the type of junction. If **true**, the filter will only return items that contain **all** the informed tags, if **false**, the filter will return the items that have at least one tag of the informed tags `Default: false` |
| `input.edit` | _[Theme](#theme) (optional)_ | Settings to modify the selected Theme for display `v2.21.0+` |
| `input.custom_theme` | _[Theme](#theme) (optional)_ | Custom theme `v2.21.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('SetCurrentBackground', {id: 'abc'});

h.hly('SetCurrentBackground', {name: 'xyz'});

//a video that is defined with the tag 'water'
h.hly('SetCurrentBackground', {
    type: 'my_video',
    tag: 'water'
});

//a video that is tagged 'water' OR tagged 'blue'
h.hly('SetCurrentBackground', {
    type: 'my_video',
    tags: ['water', 'blue']
});

//a video that is defined with the tag 'water' AND the tag 'blue'
h.hly('SetCurrentBackground', {
    type: 'my_video',
    tags: ['water', 'blue'],
    intersection: true
});

//a video that is tagged 'water' OR tagged 'blue'
//the selected theme will be modified to the 'Arial' font in italic
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

//change to a custom theme
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

Returns the thumbnail image of an item in the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Item ID |
| `input.ids` | _Array&lt;String&gt; (optional)_ | Item IDs |
| `input.type` | _String_ | Type of item. Can be: `video` `image` `announcement` `theme` `background` `api` `script` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.type` | _String_ | Type of item |
| `data.*.id` | _String_ | Item ID |
| `data.*.image` | _String_ | Image in base64 format |


**Example:**

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

Returns the information of the predominant color of a respective type of item.<br/>The returned array contains 8 indices, and each index corresponds to the section according to the following example image.<br/> <br/>![Color Map Example](https://holyrics.com.br/images/color_map_item_example.png)<br/>

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.type` | _String_ | One of the following values:<br/>**background** - um item de tema ou plano de fundo<br/>**presentation** - apresentação atual em exibição<br/>**image** - uma imagem da aba 'imagens'<br/>**video** - um vídeo da aba 'vídeos'<br/>**printscreen** - um printscreen atual de uma tela do sistema<br/> |
| `input.source` | _Object (optional)_ | The item according to the type informed:<br/>**background** - ID do tema ou plano de fundo<br/>**presentation** - não é necessário informar um valor, a apresentação da tela público será retornada<br/>**image** - o nome do arquivo da aba 'imagens'<br/>**video** - o nome do arquivo da aba 'vídeos'<br/>**printscreen** `opcional` -  the name of the screen (public, screen_2, screen_3, ...); o padrão é `public`<br/> |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.hex` | _String_ | Color in hexadecimal format |
| `data.*.red` | _Number_ | Red  `0 ~ 255` |
| `data.*.green` | _Number_ | Green  `0 ~ 255` |
| `data.*.blue` | _Number_ | Blue  `0 ~ 255` |


**Example:**

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

//Alternate calls
var arr = h.getColorMap('presentation');
var arr = h.getColorMap('video', 'filename.mp4');
```

---


### hly('GetAlert')
- v2.20.0

Returns alert message settings



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.text` | _String_ | Current alert text |
| `data.show` | _Boolean_ | Whether the alert display is enabled |


**Example:**

```javascript
var r = h.hly('GetAlert');
h.log(r.text);
```

---


### hly('SetAlert', input)
Change alert message settings

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String (optional)_ | Change alert text |
| `input.show` | _Boolean (optional)_ | Show/hide the alert |


_Method does not return value_

**Example:**

```javascript
h.hly('SetAlert', {
    text: "alert text",
    show: true
});

//remove
h.hly('SetAlert', {show: false});
```

---


### hly('GetCurrentSchedule', input)
Current schedule (selected in the main program window)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.include_lyrics_slides` | _Boolean (optional)_ |  `v2.24.0+` |
| `input.include_lyrics_history` | _Boolean (optional)_ |  `v2.24.0+` |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Schedule](#schedule)&gt;_| 


**Example:**

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
Returns the schedule list for a specific month

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.month` | _Number_ | Month (1-12) |
| `input.year` | _Number_ | Year |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Schedule](#schedule)&gt;_| 


**Example:**

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

Returns saved playlists



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.id` | _String_ | Item ID |
| `data.*.name` | _String_ | Item name |
| `data.*.items` | _Array&lt;[Item](#item)&gt;_ | Items saved in the list |


**Example:**

```javascript
var r = h.hly('GetSavedPlaylists');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('LoadSavedPlaylist', input)
- v2.19.0

Populates the media list of the currently selected playlist in the program with the given list

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.name` | _String_ | Saved playlist name |


_Method does not return value_

**Example:**

```javascript
var r = h.hly('LoadSavedPlaylist', {name: 'name'});
```

---


### hly('GetHistory', input)
"Music played" history

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Song lyric ID |
| `input.in_millis` | _Boolean (optional)_ | `true` to return the value in Timestamp `v2.24.0+` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;String&gt;_ | Date and time in format: YYYY-MM-DD HH:MM |


**Example:**

```javascript
var r = h.hly('GetHistory', {id: '123'});
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i]);
}
```

---


### hly('GetHistories', input)
History of all tags for "Music played"

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.in_millis` | _Boolean (optional)_ | `true` to return the value in Timestamp `v2.24.0+` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.music_id` | _String_ | Song ID |
| `data.*.history` | _Array&lt;String&gt;_ | Date and time in format: YYYY-MM-DD HH:MM |


**Example:**

```javascript
var r = h.hly('GetHistories');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].music_id);
    h.log(r.data[i].history);
}
```

---


### hly('GetNearestHistory', input)
- v2.24.0

Gets the date of the "Song played" history closest to a date and time passed as a parameter (or the current system date and time)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Song lyric ID |
| `input.datetime` | _String (optional)_ | Accepted formats: `timestamp` `YYYY-MM-DD` `YYYY/MM/DD` `YYYY-MM-DD HH:MM:SS` `YYYY/MM/DD HH:MM:SS` `DD-MM-YYYY` `DD/MM/YYYY` `DD-MM-YYYY HH:MM:SS` `DD/MM/YYYY HH:MM:SS` `Default: Date.now()` |
| `input.type` | _String (optional)_ | Search filter. Can be:<br>`any` any value closest to the specified date<br>`before_datetime` The closest value that is earlier than or equal to the specified date (value <= datetime)<br>`after_datetime` The closest value that is equal to or later than the specified date (value >= datetime) `Default: any` |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Object_ | Can be null |
| `data.datetime` | _String_ | Date and time in format: YYYY-MM-DD HH:MM |
| `data.datetime_millis` | _Number_ | Timestamp |


**Example:**

```javascript
var r = h.hly('GetNearestHistory', {
    id: '123'
});
//r //can be null
//r.datetime
//r.datetime_millis

var r = h.hly('GetNearestHistory', {
    id: '123',
    datetime: '2024-12-16',
    type: 'after_datetime'
});
```

---


### hly('GetSongGroup', input)
- v2.25.0

Music group

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.name` | _String_ |  |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _[Group](#group)_| 


**Example:**

```javascript
var r = h.hly('GetSongGroup', { name: 'name' });
r.data.songs.forEach(function(songID) {
    //todo
});
```

---


### hly('GetSongGroups')
- v2.24.0

List of music groups



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Group](#group)&gt;_| 


**Example:**

```javascript
var r = h.hly('GetSongGroups');
r.data.forEach(function(songGroup) {
    //todo
});
```

---


### hly('GetTeams')
- v2.22.0

Team list



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Team](#team)&gt;_| 


**Example:**

```javascript
var r = h.hly('GetTeams');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetMembers', input)
List of members

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.only_active` | _Boolean_ |  `Default: true` `v2.25.0+` |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Member](#member)&gt;_| 


**Example:**

```javascript
var r = h.hly('GetMembers');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetRoles', input)
List of functions

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.only_active` | _Boolean_ |  `Default: true` `v2.25.0+` |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Role](#role)&gt;_| 


**Example:**

```javascript
var r = h.hly('GetRoles');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetServices', input)
- v2.22.0

Service list

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.only_active` | _Boolean_ |  `Default: true` `v2.25.0+` |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Service](#service)&gt;_| 


**Example:**

```javascript
var r = h.hly('GetServices');
for (var i = 0; i < r.data.length; i++) {
    h.log(r.data[i].name);
}
```

---


### hly('GetEvents', input)
- v2.22.0

Event list

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.month` | _Number_ | Month (1-12) |
| `input.year` | _Number_ | Year |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Event](#event)&gt;_| 


**Example:**

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

Announcement

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Announcement ID |
| `input.name` | _String (optional)_ | Announcement name |


**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _[Announcement](#announcement)_| 


**Example:**

```javascript
var r = h.hly('GetAnnouncement', {
    id: '123'
});
h.log(r.data.name);
```

---


### hly('GetAnnouncements')
- v2.22.0

Announcement list



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[Announcement](#announcement)&gt;_| 


**Example:**

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
Current communication panel configuration



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.text` | _String_ | Current text |
| `data.show` | _Boolean_ | Whether the current text is displayed |
| `data.display_ahead` | _Boolean_ | Whether the *'display in front of all'* option is enabled |
| `data.alert_text` | _String_ | Current alert text |
| `data.alert_show` | _Boolean_ | Whether the alert display is enabled |
| `data.countdown_show` | _Boolean_ | If a countdown is on display |
| `data.countdown_time` | _Number_ | The current countdown time displayed (in seconds) |
| `data.stopwatch_show` | _Boolean_ | If a timer is on display `v2.20.0+` |
| `data.stopwatch_time` | _Number_ | The current time of the timer on display (in seconds) `v2.20.0+` |
| `data.theme` | _String_ | Theme ID `v2.20.0+` |
| `data.countdown_font_relative_size` | _Number_ | Relative size of the countdown `v2.20.0+` |
| `data.countdown_font_color` | _String_ | Color of the countdown font `v2.20.0+` |
| `data.stopwatch_font_color` | _String_ | Color of the stopwatch font `v2.20.0+` |
| `data.time_font_color` | _String_ | Color of the time font `v2.20.0+` |
| `data.display_clock_as_background` | _Boolean_ | Display clock as background `v2.20.0+` |
| `data.display_clock_on_alert` | _Boolean_ | Display clock in the alert `v2.20.0+` |
| `data.countdown_display_location` | _String_ | Location of the countdown or stopwatch display. `FULLSCREEN`  `FULLSCREEN_OR_ALERT`  `ALERT` `v2.20.0+` |
| `data.display_clock_with_countdown_fullscreen` | _Boolean_ | Display clock along with the countdown or stopwatch when displayed in full screen `v2.20.0+` |
| `data.display_vlc_player_remaining_time` | _Boolean_ | Display remaining time of the media playing in VLC Player `v2.20.0+` |
| `data.attention_icon_color` | _String_ | Icon color of the **Attention** button `v2.23.0+` |
| `data.attention_background_color` | _String_ | Background color of the **Attention** button icon `v2.23.0+` |
| `data.countdown_hide_zero_minute` | _Boolean_ | Hide the display of minutes when it is zero `v2.25.0+` |
| `data.countdown_hide_zero_hour` | _Boolean_ | Hide the display of hours when it is zero `v2.25.0+` |
| `data.stopwatch_hide_zero_minute` | _Boolean_ | Hide the display of minutes when it is zero `v2.25.0+` |
| `data.stopwatch_hide_zero_hour` | _Boolean_ | Hide the display of hours when it is zero `v2.25.0+` |


**Example:**

```javascript
var r = h.hly('GetCommunicationPanelInfo');
if (r.data.countdown_show) {
    h.log("Communication panel countdown is active");
    h.log(r.data.countdown_time + " seconds");
} else {
    h.log("Communication panel countdown is not active");
}
```

---


### hly('SetCommunicationPanelSettings', input)
### hly('SetCPSettings')
- v2.20.0

Change the current setting of the communication panel.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String_ | Current text |
| `input.show` | _Boolean_ | Display the current text |
| `input.display_ahead` | _Boolean_ | Option *'display ahead of everything'* |
| `input.theme` | _Object_ | ID or name of the default theme |
| `input.theme.id` | _String_ |  |
| `input.theme.name` | _String_ |  |
| `input.custom_theme` | _[Theme](#theme) (optional)_ | Custom theme `v2.21.0+` |
| `input.alert_text` | _String_ | Current alert text |
| `input.alert_show` | _Boolean_ | Enable the display of the alert |
| `input.countdown_font_relative_size` | _Number_ | Relative size of the countdown |
| `input.countdown_font_color` | _String_ | Color of the countdown font |
| `input.stopwatch_font_color` | _String_ | Color of the stopwatch font |
| `input.time_font_color` | _String_ | Color of the time font |
| `input.display_clock_as_background` | _Boolean_ | Display clock as background |
| `input.display_clock_on_alert` | _Boolean_ | Display clock in the alert |
| `input.countdown_display_location` | _String_ | Location of the countdown or stopwatch display. `FULLSCREEN`  `FULLSCREEN_OR_ALERT`  `ALERT` |
| `input.display_clock_with_countdown_fullscreen` | _Boolean_ | Display clock along with the countdown or stopwatch when displayed in full screen |
| `input.display_vlc_player_remaining_time` | _Boolean_ | Display remaining time of the media playing in VLC Player |
| `input.attention_icon_color` | _String_ | Icon color of the **Attention** button `v2.23.0+` |
| `input.attention_background_color` | _String_ | Background color of the **Attention** button icon `v2.23.0+` |
| `input.countdown_hide_zero_minute` | _Boolean_ | Hide the display of minutes when it is zero `v2.25.0+` |
| `input.countdown_hide_zero_hour` | _Boolean_ | Hide the display of hours when it is zero `v2.25.0+` |
| `input.stopwatch_hide_zero_minute` | _Boolean_ | Hide the display of minutes when it is zero `v2.25.0+` |
| `input.stopwatch_hide_zero_hour` | _Boolean_ | Hide the display of hours when it is zero `v2.25.0+` |


_Method does not return value_

**Example:**

```javascript
var r = h.hly('SetCommunicationPanelSettings', {
    display_clock_as_background: false,
    display_clock_on_alert: true
});
```

---


### hly('StartCountdownCommunicationPanel', input)
### hly('StartCountdownCP', input)
Starts a countdown on the communication panel

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.minutes` | _Number_ | Number of minutes |
| `input.seconds` | _Number_ | Number of seconds |
| `input.yellow_starts_at` | _Number (optional)_ | Value in seconds to define how long the countdown will be yellow from |
| `input.stop_at_zero` | _Boolean (optional)_ | Stop the countdown when it reaches zero `Default: false` |
| `input.text` | _String (optional)_ | Text for display. By default, the text is displayed before the numeric part. For special formatting, use the variable `@cp_countdown` in the middle of the text to indicate the location of the numeric part. `v2.24.0+` |
| `input.alert_text` | _String (optional)_ | Alternative text to be displayed when the display is in the alert. By default, the text is displayed before the numeric part. For special formatting, use the variable `@cp_countdown` in the middle of the text to indicate the location of the numeric part. `v2.24.0+` |


_Method does not return value_

**Example:**

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
Ends current communication panel countdown



_Method does not return value_

**Example:**

```javascript
h.hly('StopCountdownCommunicationPanel');
```

---


### hly('StartTimerCommunicationPanel', input)
### hly('StartTimerCP', input)
- v2.20.0

Start a stopwatch on the communication panel

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String (optional)_ | Text for display. By default, the text is displayed before the numeric part. For special formatting, use the variable `@cp_countdown` in the middle of the text to indicate the location of the numeric part. `v2.24.0+` |
| `input.alert_text` | _String (optional)_ | Alternative text to be displayed when the display is in the alert. By default, the text is displayed before the numeric part. For special formatting, use the variable `@cp_countdown` in the middle of the text to indicate the location of the numeric part. `v2.24.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('StartTimerCommunicationPanel');
h.hly('StartTimerCP');
```

---


### hly('StopTimerCommunicationPanel')
### hly('StopTimerCP')
- v2.20.0

End the current stopwatch of the communication panel



_Method does not return value_

**Example:**

```javascript
h.hly('StopTimerCommunicationPanel');
h.hly('StopTimerCP');
```

---


### hly('SetTextCommunicationPanel', input)
### hly('SetTextCP', input)
Change communication panel text

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String (optional)_ | Change the text of the communication panel. [Styled Text](https://github.com/holyrics/Scripts/blob/main/i18n/en/StyledText.md) from v2.19.0 |
| `input.show` | _Boolean (optional)_ | Show/hide the text |
| `input.display_ahead` | _Boolean (optional)_ | Change the *'display in front of all'* option |
| `input.theme` | _Object (optional)_ | ID or name of the Theme used to display the text `v2.21.0+` |
| `input.custom_theme` | _[Theme](#theme) (optional)_ | Custom theme to display the text `v2.21.0+` |


_Method does not return value_

**Example:**

```javascript
h.hly('SetTextCommunicationPanel', {
    text: "communication panel text",
    show: true,
    display_ahead: true
});

//remove
h.hly('SetTextCommunicationPanel', {show: false});
```

---


### hly('SetAlertCommunicationPanel', input)
### hly('SetAlertCP', input)
Change communication panel alert settings

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.text` | _String (optional)_ | Change alert text |
| `input.show` | _Boolean (optional)_ | Show/hide the alert |


_Method does not return value_

**Example:**

```javascript
h.hly('SetAlertCommunicationPanel', {
    text: "communication panel alert text",
    show: true
});

//remove
h.hly('SetAlertCommunicationPanel', {show: false});
```

---


### hly('CommunicationPanelCallAttention')
### hly('CPCallAttention')
- v2.20.0

Execute the 'call attention' option available in the communication panel



_Method does not return value_

**Example:**

```javascript
h.hly('CommunicationPanelCallAttention');
```

---


### hly('GetWallpaperSettings')
- v2.19.0

Wallpaper settings



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.image_base64` | _String_ | Wallpaper image in base 64 |
| `data.enabled` | _Boolean_ | Show wallpaper |
| `data.fill_color` | _String_ | Color in hexadecimal defined in the **fill** option. |
| `data.extend` | _Boolean_ | `deprecated` Replaced for `adjust_type`<br>Extend wallpaper |
| `data.adjust_type` | _String_ | Image adjustment: Can be: `ADJUST` `EXTEND` `FILL` `ADJUST_BLUR` `v2.22.0+` |
| `data.show_clock` | _Boolean_ | Show clock |
| `data.by_screen` | _Object_ | Independent configuration per screen `v2.23.0+` |
| `data.by_screen.default` | _[WallpaperSettings](#wallpaper-settings)_ | Default configuration `v2.23.0+` |
| `data.by_screen.public` | _[WallpaperSettings](#wallpaper-settings)_ | Custom configuration for the screen or **null** if using the default configuration `v2.23.0+` |
| `data.by_screen.screen_n` | _[WallpaperSettings](#wallpaper-settings)_ | n >= 2  `v2.23.0+` |


**Example:**

```javascript
var r = h.hly('GetWallpaperSettings');
h.log('Wallpaper enabled: ' + r.data.enabled);
```

---


### hly('SetWallpaperSettings', input)
- v2.19.0

Change wallpaper settings

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.file` | _String (optional)_ | File location in the **Images** tab |
| `input.enabled` | _Boolean (optional)_ | Show wallpaper |
| `input.fill_color` | _String (optional)_ | Color in hexadecimal defined in the **fill** option. **NULL** to disable |
| `input.extend` | _Boolean (optional)_ | `deprecated` Replaced for `adjust_type`<br>Extend wallpaper |
| `input.adjust_type` | _String_ | Image adjustment: Can be: `ADJUST` `EXTEND` `FILL` `ADJUST_BLUR` `v2.22.0+` |
| `input.show_clock` | _Boolean (optional)_ | Show clock |
| `input.by_screen` | _Object (optional)_ | Independent configuration per screen `v2.23.0+` |
| `input.by_screen.default` | _[WallpaperSettings](#wallpaper-settings) (optional)_ | Default configuration `v2.23.0+` |
| `input.by_screen.public` | _[WallpaperSettings](#wallpaper-settings) (optional)_ | Custom configuration for the screen or **null** if using the default configuration `v2.23.0+` |
| `input.by_screen.screen_n` | _[WallpaperSettings](#wallpaper-settings) (optional)_ | n >= 2 `v2.23.0+` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Return **true** or a list of errors that occurred |


**Example:**

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

List of display settings for each screen



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[DisplaySettings](#display-settings)&gt;_| 


**Example:**

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

Change a screen's display settings

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _[DisplaySettings](#display-settings)_ | New settings. Settings are individually optional. Fill in only the fields you want to change. |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Return **true** or a list of errors that occurred |


**Example:**

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

List of transition effect configuration



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `music` | _Array&lt;[TransitionEffectSettings](#transition-effect-settings)&gt;_ |  |
| `bible` | _Array&lt;[TransitionEffectSettings](#transition-effect-settings)&gt;_ |  |
| `image` | _Array&lt;[TransitionEffectSettings](#transition-effect-settings)&gt;_ |  |
| `announcement` | _Array&lt;[TransitionEffectSettings](#transition-effect-settings)&gt;_ |  |


**Example:**

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

Change the settings of a transition effect

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _Object_ | Item ID |
| `input.settings` | _[TransitionEffectSettings](#transition-effect-settings)_ | New settings. Settings are individually optional. Fill in only the fields you want to change. |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Return **true** or a list of errors that occurred |


**Example:**

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

`deprecated` Replaced for: hly('GetBibleVersionsV2')<br>Returns the list of available versions of the Bible, and also the associated shortcuts



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.key` | _String_ | Abbreviation of the version or the name of the shortcut, if it starts with '#shortcut ' |
| `data.*.title` | _String_ | Version name |
| `data.*.version` | _String (optional)_ | Abbreviation of the version. Available if the item is a shortcut, that is if 'key' starts with '#shortcut ' |
| `data.*.language` | _Object_ | Language `v2.24.0+` |
| `data.*.language.id` | _String_ | Item ID `v2.24.0+` |
| `data.*.language.iso` | _String_ | ISO 639 two-letter language code `v2.24.0+` |
| `data.*.language.name` | _String_ | Name in English `v2.24.0+` |
| `data.*.language.alt_name` | _String_ | Name in the language defined in `language`. Can be null. `v2.24.0+` |


**Example:**

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

Returns the list of available versions of the Bible, and also the associated shortcuts



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.key` | _String_ | Item ID |
| `data.*.version` | _String_ | Bible version ID |
| `data.*.title` | _String_ | Version name or shortcut name |
| `data.*.language` | _Object_ | Language `v2.24.0+` |
| `data.*.language.id` | _String_ | Item ID `v2.24.0+` |
| `data.*.language.iso` | _String_ | ISO 639 two-letter language code `v2.24.0+` |
| `data.*.language.name` | _String_ | Name in English `v2.24.0+` |
| `data.*.language.alt_name` | _String_ | Name in the language defined in `language`. Can be null. `v2.24.0+` |


**Example:**

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

Bible module settings



**Response:**

| Name | Type  |
| ---- | :---: |
| `data` | _Array&lt;[BibleSettings](#bible-settings)&gt;_| 


**Example:**

```javascript
var r = h.hly('GetBibleSettings');
h.log("Default version: " + r.data.tab_version_1);
```

---


### hly('SetBibleSettings', input)
- v2.21.0

Change the settings of the Bible module

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _[BibleSettings](#bible-settings)_ | New settings. Settings are individually optional. Fill in only the fields you want to change. |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Return **true** or a list of errors that occurred |


**Example:**

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

Presentation footer settings



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.rows` | _Number_ | Number of lines. `1 ~ 4` |
| `data.preview_mode` | _String_ | Accepted values: `text` `image` |
| `data.minimized` | _Boolean_ |  |


---


### hly('SetPresentationFooterSettings', input)
- v2.23.0

Change the presentation footer settings

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.rows` | _Number_ | Number of lines. `1 ~ 4` |
| `input.preview_mode` | _String_ | Accepted values: `text` `image` |
| `input.minimized` | _Boolean_ |  |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Return **true** or a list of errors that occurred |


**Example:**

```javascript
var r = h.hly('SetPresentationFooterSettings', {
    minimized: false,
    preview_mode: 'text',
    rows: 2
});
```

---


### hly('GetBpm')
Returns the current BPM value set in the program



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Current BPM value |


**Example:**

```javascript
var r = h.hly('GetBpm');
h.log('BPM: ' + r.data);
```

---


### hly('SetBpm', input)
Change the current BPM value of the program

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.bpm` | _Number_ | BPM value |


_Method does not return value_

**Example:**

```javascript
h.hly('SetBpm', {bpm: 80});
```

---


### hly('GetHue')
- v2.19.0

Returns the current hue value defined in the program



**Response:**

| Type  | Description |
| :---: | ------------|
| _Number_ | Current hue value. Minimum=0, Maximum=360. Returns **null** if disabled. |


**Example:**

```javascript
var r = h.hly('GetHue');
h.log('HUE: ' + r.data);
```

---


### hly('SetHue', input)
- v2.19.0

Changes the program's current hue value

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.hue` | _Number_ | Hue value. Minimum=0, Maximum=360 or **null** to disable. |


_Method does not return value_

**Example:**

```javascript
h.hly('SetHue', {hue: 250});

h.hly('SetHue', {hue: null});
```

---


### hly('GetRuntimeEnvironment')
### hly('GetRE')
- v2.19.0

Returns the name of the currently defined runtime environment in the program settings.



**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Runtime environment name |


**Example:**

```javascript
var r = h.hly('GetRuntimeEnvironment');
h.log('current runtime environment: ' + r.data);
```

---


### hly('SetRuntimeEnvironment', input)
### hly('SetRE', input)
- v2.19.0

Change the current runtime environment.

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.name` | _String_ | Runtime environment name |


_Method does not return value_

**Example:**

```javascript
h.hly('SetRuntimeEnvironment', {name: 'abc'});
```

---


### hly('SetLogo', input)
Change the settings for the program's *Logo* functionality (tools menu)

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.enable` | _Boolean (optional)_ | Enable/disable functionality |
| `input.hide` | _Boolean (optional)_ | Show/hide functionality |


_Method does not return value_

**Example:**

```javascript
h.hly('SetLogo', {enable: true});

h.hly('SetLogo', {hide: true});
```

---


### hly('GetSyncStatus')
- v2.19.0

Returns the current state of online synchronization via Google Drive™



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.enabled` | _Boolean_ | If sync is turned on |
| `data.started` | _Boolean_ | Whether synchronization has started (internet available for example) |
| `data.progress` | _Number_ | Sync progress from 0 to 100 |


---


### hly('GetInterfaceInput', input)
- v2.21.0

Returns the value of a field from the program interface

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID. Can be: <br>`main_lyrics_tab_search`<br>`main_text_tab_search`<br>`main_audio_tab_search`<br>`main_video_tab_search`<br>`main_image_tab_search`<br>`main_file_tab_search`<br>`main_automatic_presentation_tab_search`<br>`main_selected_theme` |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Item content |


**Example:**

```javascript
var r = h.hly('GetInterfaceInput', {
    id: 'main_lyrics_tab_search'
});
```

---


### hly('SetInterfaceInput', input)
- v2.21.0

Change the value of a field in the program interface

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Item ID. Can be: <br>`main_lyrics_tab_search`<br>`main_text_tab_search`<br>`main_audio_tab_search`<br>`main_video_tab_search`<br>`main_image_tab_search`<br>`main_file_tab_search`<br>`main_automatic_presentation_tab_search`<br>`main_selected_theme` |
| `input.value` | _String_ | New value |
| `input.focus` | _Boolean (optional)_ | Make the component receive system focus |


_Method does not return value_

**Example:**

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

Selects a verse in the Bible window

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String (optional)_ | Verse ID |
| `input.reference` | _String (optional)_ | Verse reference |


_Method does not return value_

**Example:**

```javascript
h.hly('SelectVerse', { id: '43003016' });
```

---


### hly('OpenDrawLots', input)
- v2.21.0

Opens the draw window from a list of items

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.items` | _Array&lt;String&gt;_ | List with the items to be drawn |


_Method does not return value_

**Example:**

```javascript
h.hly('OpenDrawLots', {
    items: ['exemplo 1', 'exemplo 2', 'exemplo 3']
});
```

---


### hly('GetMediaDuration', input)
- v2.21.0

Returns the duration of the media

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.type` | _String_ | Type of item. Can be: `video`, `audio`, `automatic_presentation` |
| `input.name` | _String_ | Item name |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.type` | _String_ |  |
| `data.name` | _String_ |  |
| `data.duration` | _Number_ | Duration in seconds |
| `data.duration_ms` | _Number_ | Duration in milliseconds |


**Example:**

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

Returns information about the version of the running program



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.version` | _String_ | Program version |
| `data.platform` | _String_ | Operational system. Can be: `win` `uni` `osx` |
| `data.platformDescription` | _String_ | Detailed operating system name |
| `data.baseDir` | _String_ |  `v2.24.0+` |
| `data.language` | _String_ |  `v2.24.0+` |
| `data.theme` | _String_ | One of the following values: `DEFAULT` `DARK_SOFT` `DARK_MEDIUM` `DARK_STRONG` `v2.24.0+` |
| `data.jscVersion` | _String_ | JS Community Version y.m.d `v2.24.0+` |


**Example:**

```javascript
var r = h.hly('GetVersion');
h.log(r.data.version);
h.log(r.data.plaftorm);
h.log(r.data.plaftormDescription);
```

---


### hly('GetRealTimeSongKey', input)
- v2.24.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Song ID |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.key` | _String_ | `C` `C#` `Db` `D` `D#` `Eb` `E` `F` `F#` `Gb` `G` `G#` `Ab` `A` `A#` `Bb` `B` `Cm` `C#m` `Dbm` `Dm` `D#m` `Ebm` `Em` `Fm` `F#m` `Gbm` `Gm` `G#m` `Abm` `Am` `A#m` `Bbm` `Bm` |


**Example:**

```javascript
var r = h.hly('GetRealTimeSongKey', {
    id: '123'
});
```

---


### hly('SetRealTimeSongKey', input)
- v2.24.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | Song ID |
| `input.key` | _String_ | `C` `C#` `Db` `D` `D#` `Eb` `E` `F` `F#` `Gb` `G` `G#` `Ab` `A` `A#` `Bb` `B` `Cm` `C#m` `Dbm` `Dm` `D#m` `Ebm` `Em` `Fm` `F#m` `Gbm` `Gm` `G#m` `Abm` `Am` `A#m` `Bbm` `Bm` |


_Method does not return value_

**Example:**

```javascript
h.hly('SetRealTimeSongKey', {
    id: '123',
    key: 'Em'
});
```

---


### hly('ActionNextQuickPresentation')
- v2.24.0





_Method does not return value_

---


### hly('ActionPreviousQuickPresentation')
- v2.24.0





_Method does not return value_

---


### hly('CloseCurrentQuickPresentation')
- v2.24.0





_Method does not return value_

---


### hly('GetCurrentQuickPresentation')
- v2.24.0





**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data.id` | _String_ | Current verse ID |
| `data.slide_number` | _Number_ | Starts at 1 |
| `data.total_slides` | _Number_ | Total verses |
| `data.slide_type` | _String_ | One of the following values: `default`  `wallpaper`  `blank`  `black`  `final_slide` |
| `data.slides` | _Array&lt;Object&gt;_ | List of verses from the current presentation |
| `data.slides.*.number` | _Number_ | Slide number. Starts at 1. |
| `data.slides.*.reference` | _String_ | Verse reference. Example: **John 3:16** |


---


### hly('GetTriggers')
- v2.24.0

Returns the list of saved triggers



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Array&lt;Object&gt;_ |  |
| `data.*.id` | _String_ | Item ID |
| `data.*.enabled` | _Boolean_ |  |
| `data.*.when` | _String_ | Can be: `displaying` `closing` `change` `event` |
| `data.*.type` | _String_ | Type of item. Can be:<br>**when=displaying**: `any_song` `any_text` `any_verse` `any_announcement` `any_audio` `any_video` `any_image` `any_automatic_presentation` `any_song_slide` `any_text_slide` `any_ppt_slide` `any_theme` `any_background` `any_title_subitem` `any_webcam` `any_audio_folder` `any_video_folder` `any_image_folder` `any_ppt` `any_countdown` `any_automatic_presentation_slide` `f8` `f9` `f10`<br><br>**when=closing**: `any_song` `any_text` `any_verse` `any_announcement` `any_audio` `any_video` `any_image` `any_automatic_presentation` `any_webcam` `any_audio_folder` `any_video_folder` `any_image_folder` `any_ppt` `f8` `f9` `f10`<br><br>**when=change**: `countdown_seconds_public` `countdown_seconds_communication_panel` `timer_seconds_communication_panel` `wallpaper` `wallpaper_service` `stage` `playlist` `bpm` `hue` `player_volume` `player_mute` `player_pause` `player_repeat` `player_list_or_single` `player_shuffle`<br><br>**when=event**: `new_message_chat` `verse_presentation_changed` `playlist_changed` `file_modified` `player_progress` |
| `data.*.item.title` | _String_ |  |
| `data.*.item.reference` | _Object_ |  |
| `data.*.receiver.type` | _String_ | Can be: `get` `post` `ws` `tcp` `udp` `midi` `javascript` `community` `multiple_actions` `obs_v4` `obs_v5` `lumikit` `vmix` `osc` `soundcraft` `ha` `ptz` `tbot` `openai` |
| `data.*.description` | _String_ |  |
| `data.*.tags` | _Array&lt;String&gt;_ |  |


**Example:**

```javascript
var items = h.hly('GetTriggers').data;
for (var i = 0; i < items.length; i++) {
    h.log("ID: " + items[i].id);
}
```

---


### hly('GetGlobalSettings', input)
- v2.25.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.filter` | _String (optional)_ | Name of the settings separated by comma |


**Response:**

| Type  |
| :---: |
| _[GlobalSettings](#global-settings)_ | 


**Example:**

```javascript
var r = h.hly('GetGlobalSettings', {
    filter: "show_favorite_bar_main_window,fade_in_out_duration"
});

h.log("show_favorite_bar_main_window: " + r.data.show_favorite_bar_main_window);
h.log("fade_in_out_duration: " + r.data.fade_in_out_duration);
```

---


### hly('SetGlobalSettings', input)
- v2.25.0



**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input` | _[GlobalSettings](#global-settings)_ |  |


**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `data` | _Object_ | Key/value pair with the result of the change of each item.<br>`true` if the value was successfully changed, or a `string` with the reason for the error. |


**Example:**

```javascript
var r = h.hly('SetGlobalSettings', {
    show_favorite_bar_main_window: true,
    fade_in_out_duration: 100
});

h.log(r.data.show_favorite_bar_main_window);
//output: true

h.log(r.data.fade_in_out_duration);
//output: "invalid value: 100"
```

---


### hly('GetStyledModels')
- v2.25.0





**Response:**

| Type  |
| :---: |
| _[StyledModel](#styled-model)_ | 


**Example:**

```javascript
var r = h.hly('GetStyledModels');
h.logp(r.data);
```

---


### hly('GetStyledModelsAsMap')
- v2.25.0





**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Key/value pair<br>`StyledModel#key : StyledModel#properties` |


**Example:**

```javascript
var r = h.hly('GetStyledModelsAsMap');
h.logp(r.data);
```

---


### hly('CreateItem', input)
- v2.25.0

Create a new item<br> <br>This action requires a [Holyrics Plan](https://holyrics.com.br/holyrics_plan.html) subscription to be executed<br>To use this action, you need to enable permission in the settings<br>`file menu > settings > advanced > javascript > settings > advanced permissions`<br>Or if you are using the implementation of a module, grant permission in the module settings and use the `hly` method of the **Module** class `module.hly(action, input)`<br> <br>The structure of the object passed as a parameter must be according to the table below<br><table><tr><td><p align="right">**Action**</p></td><td>Type</td></tr><tr><td><p align="right">CreateSong</p></td><td>[Lyrics](#lyrics)</td></tr><tr><td><p align="right">CreateText</p></td><td>[Text](#text)</td></tr><tr><td><p align="right">CreateTheme</p></td><td>[Theme](#theme)</td></tr><tr><td><p align="right">CreateTeam</p></td><td>[Team](#team)</td></tr><tr><td><p align="right">CreateRole</p></td><td>[Role](#role)</td></tr><tr><td><p align="right">CreateMember</p></td><td>[Member](#member)</td></tr><tr><td><p align="right">CreateEvent</p></td><td>[Event](#event)</td></tr><tr><td><p align="right">CreateSongGroup</p></td><td>[Group](#group)</td></tr></table>



**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns the created item |


**Example:**

```javascript
var r = h.hly('CreateSong', {
  title: "Title",
  artist: "Artist",
  author: "Author",
  slides: [
    {
      text: "Example",
      slide_description: "Verse 1",
      translations: {
          pt: 'Exemplo'
      }
    },
    {
      text: "Example",
      slide_description: "Chorus",
      translations: {
          pt: 'Exemplo'
      }
    },
    {
      text: "Example",
      slide_description: "Verse 2",
      translations: {
          pt: 'Exemplo'
      }
    }
  ],
  title_translations: {
    pt: 'Título'
  },
  order: "1,2,3,2,2",
  key: "G",
  bpm: 80,
  time_sig: "4/4"
});

h.log(r.data.id + ": " + r.data.title);
```

---


### hly('EditItem', input)
- v2.25.0

Edit an existing item<br> <br>This action requires a [Holyrics Plan](https://holyrics.com.br/holyrics_plan.html) subscription to be executed<br>To use this action, you need to enable permission in the settings<br>`file menu > settings > advanced > javascript > settings > advanced permissions`<br>Or if you are using the implementation of a module, grant permission in the module settings and use the `hly` method of the **Module** class `module.hly(action, input)`<br> <br>All parameters are optional except: `id`<br>Only the declared parameters will be changed that is, it is not necessary to provide the complete object to change just one parameter.<br>Parameters defined as `read-only` are not editable <br>The structure of the object passed as a parameter must be according to the table below<br><table><tr><td><p align="right">**Action**</p></td><td>Type</td></tr><tr><td><p align="right">EditSong</p></td><td>[Lyrics](#lyrics)</td></tr><tr><td><p align="right">EditText</p></td><td>[Text](#text)</td></tr><tr><td><p align="right">EditTheme</p></td><td>[Theme](#theme)</td></tr><tr><td><p align="right">EditTeam</p></td><td>[Team](#team)</td></tr><tr><td><p align="right">EditRole</p></td><td>[Role](#role)</td></tr><tr><td><p align="right">EditMember</p></td><td>[Member](#member)</td></tr><tr><td><p align="right">EditEvent</p></td><td>[Event](#event)</td></tr><tr><td><p align="right">EditSongGroup</p></td><td>[Group](#group)</td></tr></table>



_Method does not return value_

**Example:**

```javascript
h.hly('EditSong', {
    id: '123',
    title: 'New Title'
});

h.log("status: " + r.status);
```

---


### hly('DeleteItem', input)
- v2.25.0

Deletes an existing item<br> <br>This action requires a [Holyrics Plan](https://holyrics.com.br/holyrics_plan.html) subscription to be executed<br>To use this action, you need to enable permission in the settings<br>`file menu > settings > advanced > javascript > settings > advanced permissions`<br>Or if you are using the implementation of a module, grant permission in the module settings and use the `hly` method of the **Module** class `module.hly(action, input)`<br> <br>Provide the id of the respective item to remove it.<br> <br><table><tr><td><p align="right">**Action**</p></td></tr><tr><td><p align="right">DeleteSong</p></td></tr><tr><td><p align="right">DeleteText</p></td></tr><tr><td><p align="right">DeleteTheme</p></td></tr><tr><td><p align="right">DeleteTeam</p></td></tr><tr><td><p align="right">DeleteRole</p></td></tr><tr><td><p align="right">DeleteMember</p></td></tr><tr><td><p align="right">DeleteEvent</p></td></tr><tr><td><p align="right">DeleteSongGroup</p></td></tr></table>

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.id` | _String_ | ID of the respective item |


_Method does not return value_

**Example:**

```javascript
h.hly('DeleteSong', { id: '123' });
```

---


### hly('AddSongsToSongGroup', input)
- v2.25.0

Adiciona músicas a um grupo<br> <br>This action requires a [Holyrics Plan](https://holyrics.com.br/holyrics_plan.html) subscription to be executed<br>To use this action, you need to enable permission in the settings<br>`file menu > settings > advanced > javascript > settings > advanced permissions`<br>Or if you are using the implementation of a module, grant permission in the module settings and use the `hly` method of the **Module** class `module.hly(action, input)`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.group` | _String_ | Group name |
| `input.songs` | _String_ | List with the id of the songs separated by comma |


_Method does not return value_

**Example:**

```javascript
h.hly('AddSongsToSongGroup', {
    group: "Name",
    songs: "123,456"
});
```

---


### hly('RemoveSongsFromSongGroup', input)
- v2.25.0

Remove músicas de um grupo<br> <br>This action requires a [Holyrics Plan](https://holyrics.com.br/holyrics_plan.html) subscription to be executed<br>To use this action, you need to enable permission in the settings<br>`file menu > settings > advanced > javascript > settings > advanced permissions`<br>Or if you are using the implementation of a module, grant permission in the module settings and use the `hly` method of the **Module** class `module.hly(action, input)`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.group` | _String_ | Group name |
| `input.songs` | _String_ | List with the id of the songs separated by comma |


_Method does not return value_

**Example:**

```javascript
h.hly('RemoveSongsFromSongGroup', {
    group: "Name",
    songs: "123"
});
```

---


# SecurityUtils methods 
### encrypt(value)
### enc(value)
- v2.23.0

Encrypt a value `String`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _String_ | Value to be encrypted |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Value encrypted in Base64 |


**Example:**

```javascript
var b64 = h.sec('key').encrypt('Test');
// b64: rNFZfSWo/J+ggo11cxPNxg==
```

---


### decrypt(base64)
### dec(base64)
- v2.23.0

Decrypt a value `String`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `base64` | _String_ | Base64 value to be decrypted |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Decrypted value |


**Example:**

```javascript
var r = h.sec('key').decrypt('rNFZfSWo/J+ggo11cxPNxg==');
// r: Test
```

---


### encryptObj(value)
### encObj(value)
- v2.23.0

Encrypt a value `Object`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `value` | _Object_ | Value to be encrypted |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Value encrypted in Base64 |


**Example:**

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

Decrypt a value `Object`

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `base64` | _String_ | Base64 value to be decrypted |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Decrypted value |


**Example:**

```javascript
var val = h.sec('key').dec('nO2IFVws9KhnhxvQ3IBX2g==');
h.log(val);
// val: { a: 1, b: 2 }
```

---


### relativeMethods
- v2.23.0

All the following methods have the same documentation as the respective original method.
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




_Method does not return value_

**Example:**

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


# User input Methods 
### input(param, notification = false)
Display a window with input fields to receive information interactively

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `param` | _Object_ | Entries that will be requested in the interface. It can be a string or Array&lt;[InputParam](https://github.com/holyrics/Scripts/blob/main/i18n/en/InputParam.md)&gt;. If a string is passed, it will be the name of the item and the type of the item will be **string** |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | If only one item is passed as input, the value informed by the user will be returned (can be NULL). If multiple entries are requested, an object will be returned (can be NULL) where each value will be informed in the variable of its respective ID. |


**Example:**

```javascript
var r = h.input("Item name");
h.log("Reported value: " + r);

var param = [{type: 'password', name: 'Password'}];
var r = h.input(param);
h.log("Informed password: " + r);

var param = [
    {
        key: 'info',
        type: 'string',
        name: 'Information'
    }, {
        key: 'type',
        type: 'string',
        name: 'Type',
        allowed_values: ['Type 1', 'Type 2', 'Type 3']
    }
];
var r = h.input(param);
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Information: " + r.info);
    h.log("Type: " + r.type);
}

var param = [
    {
        key: 'message',
        type: 'textarea',
        name: 'Message'
    }, {
        key: 'seconds',
        type: 'number',
        name: 'Seconds',
        min: 30,
        max: 300,
        default_value: 60
    }
];
var r = h.input(param);
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Message: " + r.message);
    h.log("Seconds: " + r.seconds);
}
```

---


### settings(saveTo, saveToStore, data)
### settings(saveTo, data)
- v2.23.0

The same function as `h.input(...)`, but automatically saves the value in `setGlobal` and `store`, and also displays the current value saved previously.<br>The value will only be stored when clicking OK in the settings window

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `saveTo` | _String_ | Storage key used to save and retrieve the value of items.<br>`h.setGlobal(saveTo, ...)`<br>`h.getGlobal(saveTo, ...)`<br>`h.store(saveTo, ...)`<br>`h.restore(saveTo, ...)` |
| `saveToStore` | _Boolean_ | **true** to save the value also in `h.store(saveTo, ...)`, meaning the configuration remains saved even after restarting the program `Default: true` |
| `data` | _Object_ | Entries that will be requested in the interface. It can be a string or Array&lt;[InputParam](https://github.com/holyrics/Scripts/blob/main/i18n/en/InputParam.md)&gt;. If a string is passed, it will be the name of the item and the type of the item will be **string**.<br>`data` can be `saveTo` (storage key) if the `h.registerSettings(saveTo, ...)` or `h.loadSettings(saveTo, ...)` method was called previously |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | If only one item is passed as input, the value informed by the user will be returned (can be NULL). If multiple entries are requested, an object will be returned (can be NULL) where each value will be informed in the variable of its respective ID. |


**Example:**

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
Requests input in **textarea** format allowing multi-line text

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `title` | _String_ | Component name |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _String_ | Returns the text entered by the user (can be NULL) |


**Example:**

```javascript
var r = h.inputTextArea("Item name");
h.log("Reported value: " + r);

var r = h.inputTextArea("Item name", true); //notification
h.log("Reported value: " + r);
```

---


### itemChooser(title, items, notification = false)
Opens a window for selecting an item from a list of values

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `title` | _String_ | Window title |
| `items` | _Object_ | List of items that will be displayed in the list |
| `items.*.label` | _String (optional)_ | Name that will be displayed representing the item |
| `items.*.selected` | _Boolean (optional)_ | To set the item selected by default. v2.19.0+ |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns the item selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.itemChooser("Select an item", ["abc", "xyz", "123"]);
h.log("Selected item: " + r);

var r = h.itemChooser("Select a number", [1, 2, 3, 4, 5]);
h.log("Selected number: " + r);

var items = [
    {
        id: 1,
        type: 'test1',
        label: 'ABC'
    }, {
        id: 2,
        type: 'test2',
        label: 'XYZ',
        selected: true //selected by default
    }, {
        id: 3,
        type: 'test3',
        label: '123'
    }
];
var r = h.itemChooser("Select an item", items, true); //notification
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item");
    h.log("ID: " + r.id);
    h.log("Type: " + r.type);
    h.log("Name: " + r.label);
}

var arr1 = ['a', 'b', 'c'];
var arr2 = ['x', 'y', 'z'];
var arr3 = [1, 2, 3];
var items = [
    {source: arr1, label: 'List 1 (a, b, c)'},
    {source: arr2, label: 'List 2 (x, y, z)'},
    {source: arr3, label: 'List 3 (1, 2, 3)'}
];
var r = h.itemChooser("Select an item", items);
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.source);
}
```

---


### multipleItemChooser(title, items, notification = false)
- v2.19.0

Opens a window for selecting multiple items from a list of values

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `title` | _String_ | Window title |
| `items` | _Object_ | List of items that will be displayed in the list |
| `items.*.label` | _String (optional)_ | Name that will be displayed representing the item |
| `items.*.selected` | _Boolean (optional)_ | To define if the item will be selected by default. |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Object_ | Returns items selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.multipleItemChooser("select the items", ["abc", "xyz", "123"]);
h.log("Selected items: " + r);

var r = h.multipleItemChooser("select the numbers", [1, 2, 3, 4, 5]);
h.log("Selected numbers: " + r);

var items = [
    {
        id: 1,
        type: 'test1',
        label: 'ABC',
        selected: true //selected by default
    }, {
        id: 2,
        type: 'test2',
        label: 'XYZ'
    }, {
        id: 3,
        type: 'test3',
        label: '123',
        selected: true //selected by default
    }
];
var r = h.multipleItemChooser("select the items", items, true); //notification
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected items");
    for (var i = 0; i < r.length; i++) {
        h.log("ID: " + r[i].id);
        h.log("Type: " + r[i].type);
        h.log("Name: " + r[i].label);
    }
}
```

---


### confirm(msg, title = 'Confirm', notification = false)
- v2.19.0

Opens a confirmation window, displaying **OK** and **Cancel** buttons

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `msg` | _String_ | Message that will be displayed |
| `title` | _String_ | Window title |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Return **true** or **false** |


**Example:**

```javascript
if (h.confirm("Do task now?", "title")) {
    //ok
} else {
    //cancel
}
```

---


### yesNo(msg, title = 'Confirm', notification = false)
- v2.19.0

Opens a confirmation window, displaying **Yes** and **No** buttons

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `msg` | _String_ | Message that will be displayed |
| `title` | _String_ | Window title |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


**Response:**

| Type  | Description |
| :---: | ------------|
| _Boolean_ | Return **true** or **false** |


**Example:**

```javascript
if (h.yesNo("Do task now?", "title")) {
    //yes
} else {
    //no
}
```

---


### ok(msg, title = 'Confirm', notification = false)
- v2.24.0

Displays a message in a dialog window

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `msg` | _String_ | Message that will be displayed |
| `title` | _String_ | Window title |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


_Method does not return value_

**Example:**

```javascript
h.ok('Message', 'Info');
```

---


### error(msg, notification = false)
- v2.24.0

Displays an error message in a dialog window

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `msg` | _String_ | Message that will be displayed |
| `notification` | _Boolean (optional)_ | Display a notification instead of opening the window directly |


_Method does not return value_

**Example:**

```javascript
h.error('Error message');
```

---


### notification(msg, duration = 0)
### notificationError(msg, duration = 0)
### notificationWarning(msg, duration = 0)
- v2.19.0

Displays a notification in the corner of the screen

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `msg` | _String_ | Message that will be displayed |
| `duration` | _Number (optional)_ | Time for the notification to be automatically hidden. If the value is less than or equal to zero, the notification will not be automatically hidden. |


_Method does not return value_

**Example:**

```javascript
h.notification("Task accomplished");
```

---


### lyricsChooser()
### songChooser()
- v2.19.0

Opens a window to select a song



**Response:**

| Type  | Description |
| :---: | ------------|
| _[Lyrics](#lyrics)_ | Returns the item selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.lyricsChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.title);
}
```

---


### textChooser()
- v2.22.0

Opens a window for selecting a Text item



**Response:**

| Type  | Description |
| :---: | ------------|
| _[Text](#text)_ | Returns the item selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.textChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.title);
}
```

---


### themeChooser()
- v2.19.0

Opens a window to select a theme



**Response:**

| Type  | Description |
| :---: | ------------|
| _[Background](#background)_ | Returns the item selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.themeChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.name);
}
```

---


### imageChooser()
- v2.19.0

Opens a window to select an image



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Object_ | Returns the item selected by the user (can be NULL) |
| `*.id` | _String_ | Item ID |
| `*.name` | _String_ | Item name |
| `*.isDir` | _Boolean_ | Return **true** if it's a folder or **false** if it's a file. |


**Example:**

```javascript
var r = h.imageChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.name);
}
```

---


### audioChooser()
- v2.19.0

Opens a window to select an audio



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Object_ | Returns the item selected by the user (can be NULL) |
| `*.id` | _String_ | Item ID |
| `*.name` | _String_ | Item name |
| `*.isDir` | _Boolean_ | Return **true** if it's a folder or **false** if it's a file. |


**Example:**

```javascript
var r = h.audioChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.name);
}
```

---


### videoChooser()
- v2.19.0

Opens a window to select a video



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Object_ | Returns the item selected by the user (can be NULL) |
| `*.id` | _String_ | Item ID |
| `*.name` | _String_ | Item name |
| `*.isDir` | _Boolean_ | Return **true** if it's a folder or **false** if it's a file. |


**Example:**

```javascript
var r = h.videoChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.name);
}
```

---


### fileChooser()
- v2.24.0

Opens a window to select a file



**Response:**

| Name | Type  | Description |
| ---- | :---: | ------------|
|  | _Object_ | Returns the item selected by the user (can be NULL) |
| `*.id` | _String_ | Item ID |
| `*.name` | _String_ | Item name |
| `*.isDir` | _Boolean_ | Return **true** if it's a folder or **false** if it's a file. |


**Example:**

```javascript
var r = h.fileChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.name);
}
```

---


### backgroundChooser()
- v2.19.0

Opens a window to select a background



**Response:**

| Type  | Description |
| :---: | ------------|
| _[Background](#background)_ | Returns the item selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.backgroundChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.name);
}
```

---


### verseChooser()
- v2.24.0

Opens a window to select a verse



**Response:**

| Type  | Description |
| :---: | ------------|
| _[VerseReference](#verse-reference)_ | Returns the item selected by the user (can be NULL) |


**Example:**

```javascript
var r = h.verseChooser();
if (r == null) {
    h.log("Canceled");
} else {
    h.log("Selected item: " + r.reference);
}
```

---


### openWindow(name)
- v2.22.0

Open a program window

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Window name. Can be: `main` `bible` `communication_panel` `chat`<br> <br>**v2.23.0+**<br>`js_playground` `js_monitor_interval` `js_monitor_timeout` `js_monitor_run_at` `js_monitor_trigger` `js_monitor_global` `js_monitor_timer_and_countdown` <br> <br>**v2.24.0+**<br>`js_allowed_extensions` `js_allowed_files` |


_Method does not return value_

**Example:**

```javascript
h.openWindow('main');

h.openWindow('bible');
```

---


### repaint(id)
- v2.23.0

Forces the update of an interface component.<br>Currently available for: Favorites bar

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |


_Method does not return value_

**Example:**

```javascript
h.repaint('favorite_id');
```

---


### popupWorker(input)
- v2.24.0

Opens a progress popup for executing long tasks with feedback in the interface

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `input.title` | _String (optional)_ | Initial message of the progress popup |
| `input.cancelable` | _Boolean (optional)_ | `true` to allow the user to cancel the task `Default: false` |
| `input.action` | _Function_ | Action to be executed.<br>`function(evt) { /* */ }`<br>The `evt` object is of type [PopupWorkerUpdater](https://github.com/holyrics/jslib/blob/main/doc/en/PopupWorkerUpdater.md) |
| `input.callback` | _Function (optional)_ | Executed when finishing the execution of `action`.<br>`function(response, err) { /* */ }`<br>`response` is the object returned in the execution of `action`<br>`err` is the error message if the execution generated any `Exception` |
| `input.on_cancel` | _Function_ | Executed if the task is canceled |


_Method does not return value_

**Example:**

```javascript
h.popupWorker({
  title: 'Please wait',
  action: function(evt) {
    //evt.setProgress(0); //0~100
    //evt.setMessage("message");
    //evt.setLog("log");
    return null;
  },
  callback: function(response, err) {
    //callback action
  },
  //cancelable: false, //default false
  //on_cancel: function() {}
});
```

---


### popupCreateSong(song, callback = null)
- v2.24.0

Opens an editing window for creating new song lyrics<br>Note: It is not possible to open multiple editing windows simultaneously<br>May generate Exception

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `callback` | _Function (optional)_ | Executed when closing the editing window.<br>`function(id) { /* */ }`<br>`id` is the id of the saved item or `null` if the user closed the window without saving the item |
| `song` | _Object_ |  |
| `song.title` | _String_ | Song title |
| `song.lyrics` | _String_ | Song lyrics.<br>Optional if `paragraphs` is declared |
| `song.paragraphs` | _Array&lt;Object&gt;_ | Alternative parameter for more complex values.<br>Optional if `lyrics` is declared |
| `song.paragraphs.*.text` | _String_ | Paragraph text |
| `song.paragraphs.*.description` | _String (optional)_ | Description of the paragraph. chorus, verse, ... |
| `song.paragraphs.*.translations` | _Object (optional)_ | Translations for the slide.<br>Key/value pair. |
| `song.author` | _String (optional)_ | Music author |
| `song.artist` | _String (optional)_ | Music artist |
| `song.copyright` | _String (optional)_ | Music copyright |
| `song.note` | _String (optional)_ | Music annotation |
| `song.key` | _String (optional)_ | Tone of music.<br>Can be: `C` `C#` `Db` `D` `D#` `Eb` `E` `F` `F#` `Gb` `G` `G#` `Ab` `A` `A#` `Bb` `B` `Cm` `C#m` `Dbm` `Dm` `D#m` `Ebm` `Em` `Fm` `F#m` `Gbm` `Gm` `G#m` `Abm` `Am` `A#m` `Bbm` `Bm` |
| `song.bpm` | _Number (optional)_ | BPM of the song |
| `song.time_sig` | _String (optional)_ | Music time.<br>Can be: `2/2` `2/4` `3/4` `4/4` `5/4` `6/4` `3/8` `6/8` `7/8` `9/8` `12/8` |
| `song.streaming` | _Object_ | URI or ID of the streamings |
| `song.streaming.audio` | _Object_ | Audio |
| `song.streaming.audio.spotify` | _String_ |  |
| `song.streaming.audio.youtube` | _String_ |  |
| `song.streaming.audio.deezer` | _String_ |  |
| `song.streaming.backing_track` | _Object_ | Backing track |
| `song.streaming.backing_track.spotify` | _String_ |  |
| `song.streaming.backing_track.youtube` | _String_ |  |
| `song.streaming.backing_track.deezer` | _String_ |  |
| `song.extras` | _Object (optional)_ | Map of extra objects (added by the user)<br>Allowed only for already existing fields. |
| `song.title_translations` | _Object_ | Translations for the title slide.<br>Key/value pair. |


_Method does not return value_

**Example:**

```javascript
var song = {
    title: 'Title',
    artist: 'Artist',
    author: 'Author',
    lyrics: 'Slide 1\nSlide 1\n\nSlide 2\nSlide 2'
};
h.popupCreateSong(song, function(id) {
    if (id) {
        //The item has been saved
    } else {
        //The item has not been saved
    }
});
```

---


### popupCreateText(text, callback = null)
- v2.24.0

Opens an editing window for creating a new text presentation<br>Note: It is not possible to open multiple editing windows simultaneously<br>May generate Exception

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `callback` | _Function (optional)_ | Executed when closing the editing window.<br>`function(id) { /* */ }`<br>`id` is the id of the saved item or `null` if the user closed the window without saving the item |
| `text` | _Object_ |  |
| `text.title` | _String_ | Text title |
| `text.folder` | _String_ | Path of the location folder |
| `text` | _String_ | Presentation text.<br>Optional if `slides` is declared |
| `text.slides` | _Array&lt;Object&gt;_ | Alternative parameter for more complex values.<br>Optional if `lyrics` is declared |
| `text.slides.*.text` | _String_ | Paragraph text |
| `text.slides.*.translations` | _Object (optional)_ | Translations for the slide.<br>Key/value pair. |
| `text.extras` | _Object (optional)_ | Mapa de objetos extras (adicionados pelo usuário)<br>Allowed only for already existing fields. |


_Method does not return value_

**Example:**

```javascript
var text = {
    title: 'Title',
    text: 'Slide 1\nSlide 1\n\nSlide 2\nSlide 2'
};
h.popupCreateText(text, function(id) {
    if (id) {
        //The item has been saved
    } else {
        //The item has not been saved
    }
});
```

---


### popupCreateTheme(theme, callback = null)
- v2.24.0

Opens an editing window for creating a new theme<br>Note: It is not possible to open multiple editing windows simultaneously<br>May generate Exception

**Parameters:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `callback` | _Function (optional)_ | Executed when closing the editing window.<br>`function(id) { /* */ }`<br>`id` is the id of the saved item or `null` if the user closed the window without saving the item |
| `theme` | _[Theme](#theme)_ |  |


_Method does not return value_

**Example:**

```javascript
var theme = {
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
};
h.popupCreateTheme(theme, function(id) {
    if (id) {
        //The item has been saved
    } else {
        //The item has not been saved
    }
});
```

---


# Classes 
Complex classes used as a return in some methods
## Lyrics
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Song ID |
| `title` | _String_ | Song title |
| `artist` | _String_ | Music artist |
| `author` | _String_ | Music author |
| `note` | _String_ | Music annotation |
| `copyright` | _String_ | Music copyright |
| `slides` | _Array&lt;Object&gt;_ |  `v2.21.0+` |
| `slides.*.text` | _String_ | Slide text `v2.21.0+` |
| `slides.*.styled_text` | _String_ | Slide text with **styled** formatting (when available) `v2.24.0+` |
| `slides.*.slide_description` | _String_ | Slide description `v2.21.1+` |
| `slides.*.background_id` | _String_ | ID of the theme or background saved for the slide `v2.21.0+` |
| `slides.*.translations` | _Object_ | Translations for the slide.<br>Key/value pair. `v2.25.0+` |
| `formatting_type` | _String_ | `basic`  `styled`  `advanced`<br> <br>When using this object in creation or editing methods, if `formatting_type=basic` is used, the value of the variable `slides.*.text` will be used; otherwise, the value of the variable `slides.*.styled_text` will be used `Default: basic` `v2.25.0+` |
| `order` | _String_ | Order of slides (index from 1), separated by comma `v2.21.0+` |
| `arrangements` | _Array&lt;[SongArrangement](#song-arrangement)&gt;_ |  `v2.25.1+` |
| `title_translations` | _Object_ | Translations for the title slide.<br>Key/value pair. `v2.25.0+` |
| `key` | _String_ | Tone of music.<br>Can be: `C` `C#` `Db` `D` `D#` `Eb` `E` `F` `F#` `Gb` `G` `G#` `Ab` `A` `A#` `Bb` `B` `Cm` `C#m` `Dbm` `Dm` `D#m` `Ebm` `Em` `Fm` `F#m` `Gbm` `Gm` `G#m` `Abm` `Am` `A#m` `Bbm` `Bm` |
| `bpm` | _Number_ | BPM of the song |
| `time_sig` | _String_ | Music time.<br>Can be: `2/2` `2/4` `3/4` `4/4` `5/4` `6/4` `3/8` `6/8` `7/8` `9/8` `12/8` |
| `groups` | _Array&lt;[Group](#group)&gt;_ | Groups where music is added `read-only` |
| `linked_audio_file` | _String_ | Path of the audio file linked to the song `v2.22.0+` |
| `linked_backing_track_file` | _String_ | Path of the audio file (backing track) linked to the song `v2.22.0+` |
| `streaming` | _Object_ | URI or ID of the streamings `v2.22.0+` |
| `streaming.audio` | _Object_ | Audio `v2.22.0+` |
| `streaming.audio.spotify` | _String_ |  `v2.22.0+` |
| `streaming.audio.youtube` | _String_ |  `v2.22.0+` |
| `streaming.audio.deezer` | _String_ |  `v2.22.0+` |
| `streaming.backing_track` | _Object_ | Backing track `v2.22.0+` |
| `streaming.backing_track.spotify` | _String_ |  `v2.22.0+` |
| `streaming.backing_track.youtube` | _String_ |  `v2.22.0+` |
| `streaming.backing_track.deezer` | _String_ |  `v2.22.0+` |
| `midi` | _[Midi](#midi)_ | Item MIDI shortcut |
| `extras` | _Object_ | Map of extra objects (added by the user) `v2.21.0+` |
| `theme` | _String_ | Saved theme ID for the song `v2.25.0+` |
| `archived` | _Boolean_ | If the song is archived |
| `metadata.modified_time_millis` | _Number_ | File modification date. (timestamp) `v2.25.0+` `read-only` |
<details>
  <summary>See example</summary>

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
      "slide_description": "Verse 2",
      "background_id": null,
      "translations": null
    }
  ],
  "formatting_type": "basic",
  "order": "1,2,3,2,2",
  "title_translations": null,
  "key": "",
  "bpm": 0.0,
  "time_sig": "",
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
  "theme": null,
  "archived": false
}
```
</details>

## Text
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Text ID |
| `title` | _String_ | Text title |
| `folder` | _String_ | Path of the location folder |
| `theme` | _String_ | ID of the theme saved for the text |
| `slides` | _Array&lt;Object&gt;_ |  |
| `slides.*.text` | _String_ | Slide text |
| `slides.*.styled_text` | _String_ | Slide text with **styled** formatting (when available) `v2.24.0+` |
| `slides.*.background_id` | _String_ | ID of the theme or background saved for the slide |
| `slides.*.translations` | _Object_ | Translations for the slide.<br>Key/value pair. `v2.25.0+` |
| `formatting_type` | _String_ | `basic`  `styled`  `advanced`<br> <br>When using this object in creation or editing methods, if `formatting_type=basic` is used, the value of the variable `slides.*.text` will be used; otherwise, the value of the variable `slides.*.styled_text` will be used `Default: basic` `v2.25.0+` |
| `extras` | _Object_ | Map of extra objects (added by the user) `v2.24.0+` |
| `metadata.modified_time_millis` | _Number_ | File modification date. (timestamp) `v2.25.0+` `read-only` |
<details>
  <summary>See example</summary>

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
  ],
  "formatting_type": "basic"
}
```
</details>

## Theme
| Name | Type  | Description |
| ---- | :---: | ------------|
| `copy_from_id` | _String (optional)_ | ID of an existing Theme to use as initial copy when creating a new item |
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |
| <br>**background** |  | <br>Background |
| `background.type` | _String_ | Type of background. Can be: `color`  `my_video`  `my_image`  `video`  `image`  `pattern`  `transparent`  `image_file`  `video_file` |
| `background.id` | _String_ | <table><tr><td><p align="right">**Type**</p></td><td>Value</td></tr><tr><td><p align="right">color</p></td><td>Color in hexadecimal format</td></tr><tr><td><p align="right">my_video</p></td><td>Item ID</td></tr><tr><td><p align="right">my_image</p></td><td>Item ID</td></tr><tr><td><p align="right">video</p></td><td>Item ID</td></tr><tr><td><p align="right">image</p></td><td>Item ID</td></tr><tr><td><p align="right">pattern</p></td><td>Item ID</td></tr><tr><td><p align="right">transparent</p></td><td>"transparent"</td></tr><tr><td><p align="right">image_file</p></td><td>File name in the library</td></tr><tr><td><p align="right">video_file</p></td><td>File name in the library</td></tr></table> |
| `background.adjust_type` | _String_ | `fill` `extend` `adjust` `side_by_side` `center`<br>Available for: **type=my_image**, **type=image** |
| `background.opacity` | _Number_ | Opacity. `0 ~ 100` |
| `background.velocity` | _Number_ | Available for: **type=my_video**, **type=video**<br>`0.25 ~ 4.0` |
| `base_color` | _String_ | Color in hexadecimal format. Base color of the background when reducing opacity. |
| <br>**font** |  | <br>Source |
| `font.name` | _String_ | Font name |
| `font.bold` | _Boolean_ | Bold |
| `font.italic` | _Boolean_ | Italic |
| `font.size` | _Number_ | Size `0.0 ~ 0.4`<br>Value in percentage, based on the slide height. |
| `font.color` | _String_ | Color in hexadecimal format |
| `font.line_spacing` | _Number_ | Line spacing. `-0.5 ~ 1.0`<br>Value in percentage based on the line height. |
| `font.char_spacing` | _Number_ | Spacing between characters. `-40 ~ 120` |
| <br>**align** |  | <br>Alignment |
| `align.horizontal` | _String_ | `left`  `center`  `right`  `justify` |
| `align.vertical` | _String_ | `top`  `middle`  `bottom` |
| `align.margin.top` | _Number_ | `0 ~ 90` |
| `align.margin.right` | _Number_ | `0 ~ 90` |
| `align.margin.bottom` | _Number_ | `0 ~ 90` |
| `align.margin.left` | _Number_ | `0 ~ 90` |
| <br>**effect** |  | <br>Font effects |
| `effect.outline_color` | _String_ | Color in hexadecimal format |
| `effect.outline_weight` | _Number_ | `0.0 ~ 100.0` |
| `effect.brightness_color` | _String_ | Color in hexadecimal format |
| `effect.brightness_weight` | _Number_ | `0.0 ~ 100.0` |
| `effect.shadow_color` | _String_ | Color in hexadecimal format |
| `effect.shadow_x_weight` | _Number_ | `-100.0 ~ 100.0` |
| `effect.shadow_y_weight` | _Number_ | `-100.0 ~ 100.0` |
| `effect.blur` | _Boolean_ | Apply 'blur' effect on brightness and shadow |
| <br>**shape_fill** |  | <br>Background color |
| `shape_fill.type` | _String_ | `box`  `line`  `line_fill`  `theme_margin` |
| `shape_fill.enabled` | _Boolean_ |  |
| `shape_fill.color` | _String_ | Color in hexadecimal format (RGBA) |
| `shape_fill.margin.top` | _Number_ | `0 ~ 100` |
| `shape_fill.margin.right` | _Number_ | `0 ~ 100` |
| `shape_fill.margin.bottom` | _Number_ | `0 ~ 100` |
| `shape_fill.margin.left` | _Number_ | `0 ~ 100` |
| `shape_fill.corner` | _Number_ | `0 ~ 100` |
| <br>**shape_outline** |  | <br>Outline |
| `shape_outline.type` | _String_ | `box`  `line`  `line_fill`  `theme_margin` |
| `shape_outline.enabled` | _Boolean_ |  |
| `shape_outline.color` | _String_ | Color in hexadecimal format (RGBA) |
| `shape_outline.outline_thickness` | _Number_ | `0 ~ 25` |
| `shape_outline.margin.top` | _Number_ | `0 ~ 100` |
| `shape_outline.margin.right` | _Number_ | `0 ~ 100` |
| `shape_outline.margin.bottom` | _Number_ | `0 ~ 100` |
| `shape_outline.margin.left` | _Number_ | `0 ~ 100` |
| `shape_outline.corner` | _Number_ | `0 ~ 100` |
| <br>**comment** |  | <br>Comment |
| `comment.font_name` | _String_ | Font name |
| `comment.bold` | _Boolean_ | Bold |
| `comment.italic` | _Boolean_ | Italic |
| `comment.relative_size` | _Number_ | relative font size. `40 ~ 100` |
| `comment.color` | _String_ | Color in hexadecimal format |
| <br>**settings** |  | <br>Settings |
| `settings.uppercase` | _Boolean_ | Display the text in uppercase |
| `settings.line_break` | _String_ | Apply line break. `system`  `true`  `false`<br> `Default: system` |
| <br>**metadata** |  | <br> |
| `metadata.modified_time_millis` | _Number_ | File modification date. (timestamp) `v2.25.0+` `read-only` |
<details>
  <summary>See example</summary>

```json
{
  "id": "123",
  "name": "",
  "background": {
    "type": "color",
    "id": "212121",
    "opacity": 100
  },
  "base_color": "FFFFFF",
  "font": {
    "name": "CMG Sans",
    "bold": true,
    "italic": false,
    "size": 10.0,
    "color": "F5F5F5",
    "line_spacing": 0.3,
    "char_spacing": 0
  },
  "align": {
    "horizontal": "center",
    "vertical": "middle",
    "margin": {
      "top": 3.0,
      "right": 3.0,
      "bottom": 3.0,
      "left": 3.0
    }
  },
  "effect": {
    "outline_color": "404040",
    "outline_weight": 0.0,
    "brightness_color": "C0C0C0",
    "brightness_weight": 0.0,
    "shadow_color": "404040",
    "shadow_x_weight": 0.0,
    "shadow_y_weight": 0.0,
    "blur": true
  },
  "shape_fill": {
    "type": "box",
    "enabled": false,
    "color": "000000",
    "margin": {
      "top": 5.0,
      "right": 30.0,
      "bottom": 10.0,
      "left": 30.0
    },
    "corner": 0
  },
  "shape_outline": {
    "type": "box",
    "enabled": false,
    "color": "000000",
    "outline_thickness": 10,
    "margin": {
      "top": 5.0,
      "right": 30.0,
      "bottom": 10.0,
      "left": 30.0
    },
    "corner": 0
  },
  "comment": {
    "font_name": "Arial",
    "bold": false,
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
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `type` | _String_ | Type of item. Can be: `theme` `my_video` `my_image` `video` `image` |
| `name` | _String_ | Item name |
| `width` | _Number (optional)_ |  |
| `height` | _Number (optional)_ |  |
| `duration` | _Number (optional)_ | Duration in milliseconds |
| `tags` | _Array&lt;String&gt;_ | Item tag list |
| `bpm` | _Number_ | BPM value of item |
| `midi` | _[Midi](#midi) (optional)_ | Item MIDI shortcut |
<details>
  <summary>See example</summary>

```json
{
  "id": "10",
  "type": "video",
  "name": "Hexagons",
  "duration": "29050",
  "width": "1280",
  "height": "720",
  "bpm": 0.0
}
```
</details>

## Slide Description
| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Item name |
| `tag` | _String_ | Short name of the item |
| `aliases` | _Array&lt;String&gt;_ | List with alternative names |
| `font_color` | _String_ | Font color in hexadecimal format |
| `bg_color` | _String_ | Background color in hexadecimal format |
| `background` | _Number_ | ID of the custom background |
| `midi` | _[Midi](#midi) (optional)_ | Item MIDI shortcut |
<details>
  <summary>See example</summary>

```json
{
  "name": "Chorus",
  "tag": "C",
  "font_color": "FFFFFF",
  "bg_color": "000080",
  "background": null,
  "midi": null
}
```
</details>

## Item
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `type` | _String_ | Type of item. It can be: `title`  `song`  `verse`  `text`  `audio`  `video`  `image`  `file`  `announcement`  `automatic_presentation`  `countdown`  `countdown_cp`  `cp_text`  `plain_text`  `uri`  `global_action`  `api`  `script` |
| `name` | _String_ | Item name |

## Group
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID. (The same value as `name`). `v2.25.0+` |
| `name` | _String_ | Item name `read-only` |
| `songs` | _Array&lt;String&gt;_ | List of song IDs |
| `add_chorus_between_verses` | _Boolean_ |  `v2.25.0+` |
| `hide_in_interface` | _Boolean_ |  `v2.25.0+` |
| `metadata.modified_time_millis` | _Number_ | File modification date. (timestamp) `v2.25.0+` `read-only` |

## Song Arrangement
| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Item name |
| `sequence` | _String_ | Order of slides (index from 1), separated by comma |
| `collections` | _Array&lt;String&gt;_ |  |
<details>
  <summary>See example</summary>

```json
{
  "name": "",
  "sequence": "1,2,3,2,2"
}
```
</details>

## Announcement
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |
| `text` | _String_ | Announcement text |
| `archived` | _Boolean_ | If the item is archived |

## Midi
| Name | Type  | Description |
| ---- | :---: | ------------|
| `code` | _Number_ | MIDI code |
| `velocity` | _Number_ | Speed/intensity midi |
<details>
  <summary>See example</summary>

```json
{
  "code": 80,
  "velocity": 20
}
```
</details>

## Favorite Item
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |

## Service
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID `v2.25.0+` |
| `name` | _String_ | Item name |
| `disabled` | _Boolean_ | Returns **true** if the item is set to disabled `v2.25.0+` |
| `week` | _String_ | Week. Can be: `all` `first` `second` `third` `fourth` `last` |
| `day` | _String_ | Day of the week. Can be: `sun` `mon` `tue` `wed` `thu` `fri` `sat` |
| `hour` | _Number_ | Hour [0-23] |
| `minute` | _Number_ | Minute [0-59] |
| `type` | _String_ | Type of item. Can be: `service` `event` |
| `hide_week` | _Array&lt;String&gt;_ | List of hidden weeks. Available if `week=all` |
| `metadata.modified_time_millis` | _Number_ | File modification date. (timestamp) `v2.25.0+` `read-only` |

## Event
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID `v2.25.0+` |
| `name` | _String_ | Item name |
| `description` | _String_ | Item description `v2.25.0+` |
| `datetime` | _String_ | Date and time format: YYYY-MM-DD HH:MM |
| `datetime_millis` | _String_ | timestamp `v2.24.0+` `read-only` |
| `wallpaper` | _String_ | Relative path of the file used as the event wallpaper |
| `metadata.modified_time_millis` | _Number_ | File modification date. (timestamp) `v2.25.0+` `read-only` |
| `metadata.service` | _[Service](#service)_ | Regular service or event that gives rise to this event. It can be `null` if it is an individually created event. `v2.25.0+` `read-only` |

## Schedule
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | Playlist type. Can be: temporary, service, event |
| `name` | _String_ |  |
| `datetime` | _String_ | Date and time format: YYYY-MM-DD HH:MM |
| `lyrics_playlist` | _Array&lt;[Lyrics](#lyrics)&gt;_ | Lyrics list |
| `media_playlist` | _Array&lt;[Item](#item)&gt;_ | Media list |
| `responsible` | _[Member](#member)_ | Member defined as responsible for the event |
| `members` | _Array&lt;Object&gt;_ | List of members |
| `members.*.id` | _String_ | Member ID |
| `members.*.name` | _String_ | Name of the member |
| `members.*.scheduled` | _Boolean_ | Whether the integrand is scaled or defined for a function |
| `roles` | _Array&lt;Object&gt;_ | List of functions on the scale |
| `roles.*.id` | _String_ | Function ID |
| `roles.*.name` | _String_ | Function name |
| `roles.*.member` | _[Member](#member)_ | Member assigned to the role |
| `notes` | _String_ | Notes `v2.21.0+` |
| `metadata.modified_time_millis` | _Number_ | File modification date. (timestamp) `v2.25.0+` `read-only` |
| `metadata.event` | _[Event](#event)_ | Event that gives rise to this playlist. It can be `null` if `type=temporary`. `v2.25.0+` `read-only` |
<details>
  <summary>See example</summary>

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
  "notes": ""
}
```
</details>

## Team
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |
| `description` | _String_ | Item description |
| `metadata.modified_time_millis` | _Number_ | File modification date. (timestamp) `v2.25.0+` `read-only` |

## Member
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |
| `disabled` | _Boolean_ | Returns **true** if the item is set to disabled `v2.25.0+` |
| `skills` | _String_ | Skills |
| `roles` | _Array&lt;[Role](#role)&gt;_ | Roles |
| `metadata.modified_time_millis` | _Number_ | File modification date. (timestamp) `v2.25.0+` `read-only` |

## Role
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |
| `disabled` | _Boolean_ | Returns **true** if the item is set to disabled `v2.25.0+` |
| `team` | _[Team](#team)_ | Team |
| `metadata.modified_time_millis` | _Number_ | File modification date. (timestamp) `v2.25.0+` `read-only` |

## Automatic Presentation
| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Item name |
| `duration` | _Number_ | Duration in milliseconds |
| `starts_with` | _String_ | Accepted values: `title` `blank` |
| `song` | _[Lyrics](#lyrics)_ |  |
| `timeline` | _Array&lt;Object&gt;_ | Information about the start and duration of each slide in the presentation |
| `timeline.*.number` | _Number_ | number >= 0 |
| `timeline.*.start` | _Number_ | Start time of the presentation in milliseconds |
| `timeline.*.end` | _Number_ | End time of the presentation in milliseconds |
| `timeline.*.duration` | _Number_ | Duration in milliseconds |

## Automatic
| Name | Type  | Description |
| ---- | :---: | ------------|
| `seconds` | _Number_ | Time each item will be displayed |
| `repeat` | _Boolean_ | **true** to keep repeating the presentation (go back to the first item after the last one) |

## Presentation Slide Info
| Name | Type  | Description |
| ---- | :---: | ------------|
| `number` | _Number_ | Slide number (starts at 1) |
| `text` | _String_ | Slide text |
| `theme_id` | _String_ | Slide theme ID |
| `slide_description` | _String (optional)_ | Slide description name. Available if it is a music presentation. |
| `preview` | _String (optional)_ | Image in base64 format |

## Trigger Item
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String (optional)_ | Item ID |
| `when` | _String_ | `displaying` `closing` `change` `event` |
| `item` | _String_ | Type of item. Can be:<br>**when=displaying**: `any_song` `any_text` `any_verse` `any_announcement` `any_audio` `any_video` `any_image` `any_automatic_presentation` `any_song_slide` `any_text_slide` `any_ppt_slide` `any_theme` `any_background` `any_title_subitem` `any_webcam` `any_audio_folder` `any_video_folder` `any_image_folder` `any_ppt` `any_countdown` `any_automatic_presentation_slide` `f8` `f9` `f10`<br><br>**when=closing**: `any_song` `any_text` `any_verse` `any_announcement` `any_audio` `any_video` `any_image` `any_automatic_presentation` `any_webcam` `any_audio_folder` `any_video_folder` `any_image_folder` `any_ppt` `f8` `f9` `f10`<br><br>**when=change**: `countdown_seconds_public` `countdown_seconds_communication_panel` `timer_seconds_communication_panel` `wallpaper` `wallpaper_service` `stage` `playlist` `bpm` `hue` `player_volume` `player_mute` `player_pause` `player_repeat` `player_list_or_single` `player_shuffle`<br><br>**when=event**: `new_message_chat` `verse_presentation_changed` `playlist_changed` `file_modified` `player_progress` |
| `action` | _Function_ | Action to be executed.<br>`function(obj) { /*  */ }`<br>Content of `obj` according to the item type:<br>[`any_song`](https://github.com/holyrics/jslib/blob/main/README-en.md#songinfo)  [`any_text`](https://github.com/holyrics/jslib/blob/main/README-en.md#textinfo)  [`any_verse`](https://github.com/holyrics/jslib/blob/main/README-en.md#verseinfo)  [`any_announcement`](https://github.com/holyrics/jslib/blob/main/README-en.md#announcementinfo)  [`any_audio`](https://github.com/holyrics/jslib/blob/main/README-en.md#audioinfo)  [`any_video`](https://github.com/holyrics/jslib/blob/main/README-en.md#videoinfo)  [`any_image`](https://github.com/holyrics/jslib/blob/main/README-en.md#imageinfo)  [`any_automatic_presentation`](https://github.com/holyrics/jslib/blob/main/README-en.md#automaticpresentationinfo)  [`any_song_slide`](https://github.com/holyrics/jslib/blob/main/README-en.md#songslideinfo)  [`any_text_slide`](https://github.com/holyrics/jslib/blob/main/README-en.md#textslideinfo)  [`any_ppt_slide`](https://github.com/holyrics/jslib/blob/main/README-en.md#pptslideinfo)  [`any_theme`](https://github.com/holyrics/jslib/blob/main/README-en.md#themeinfo)  [`any_background`](https://github.com/holyrics/jslib/blob/main/README-en.md#backgroundinfo)  [`any_title_subitem`](https://github.com/holyrics/jslib/blob/main/README-en.md#titleinfo)  [`any_webcam`](https://github.com/holyrics/jslib/blob/main/README-en.md#webcaminfo)  [`any_audio_folder`](https://github.com/holyrics/jslib/blob/main/README-en.md#audioinfo)  [`any_video_folder`](https://github.com/holyrics/jslib/blob/main/README-en.md#videoinfo)  [`any_image_folder`](https://github.com/holyrics/jslib/blob/main/README-en.md#imageinfo)  [`any_ppt`](https://github.com/holyrics/jslib/blob/main/README-en.md#pptinfo)  [`any_countdown`](https://github.com/holyrics/jslib/blob/main/README-en.md#countdowninfo)  [`any_automatic_presentation_slide`](https://github.com/holyrics/jslib/blob/main/README-en.md#automaticpresentationslideinfo)  [`f8`](https://github.com/holyrics/jslib/blob/main/README-en.md#presentationmodifierinfoinfo)  [`f9`](https://github.com/holyrics/jslib/blob/main/README-en.md#presentationmodifierinfoinfo)  [`f10`](https://github.com/holyrics/jslib/blob/main/README-en.md#presentationmodifierinfoinfo)  [`new_message_chat`](https://github.com/holyrics/jslib/blob/main/README-en.md#newchatmessageinfo)  [`verse_presentation_changed`](https://github.com/holyrics/jslib/blob/main/README-en.md#versepresentationchangedinfo)  [`playlist_changed`](https://github.com/holyrics/jslib/blob/main/README-en.md#playlistchangedinfo)  [`file_modified`](https://github.com/holyrics/jslib/blob/main/README-en.md#filemodifiedinfo)  [`player_progress`](https://github.com/holyrics/jslib/blob/main/README-en.md#playerprogressinfo)<br><br>All items with **when=change** contain: `obj.id` `obj.name` `obj.old_value` `obj.new_value` |
| `name` | _String (optional)_ | Item name. Compatible value for display in **JavaScript Monitor** `v2.23.0+` |
| `filter` | _Object (optional)_ | Execute action only if the object that triggered the event matches the filter object `v2.24.0+` |
<details>
  <summary>See example</summary>

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
Settings for media execution

| Name | Type  | Description |
| ---- | :---: | ------------|
| `volume` | _Number_ | Change the volume of the player |
| `repeat` | _Boolean_ | Change the **repeat** option |
| `shuffle` | _Boolean_ | Change the **random** option |
| `start_time` | _String_ | Start time for execution in SS, MM:SS or HH:MM:SS format |
| `stop_time` | _String_ | End time for execution in SS, MM:SS or HH:MM:SS format |
<details>
  <summary>See example</summary>

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
Display settings

| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID. `public` `screen_2` `screen_3` `screen_?` `stream_image` `stream_html_1` `stream_html_2` `stream_html_3` |
| `name` | _String_ | Item name |
| `stage_view` | _[StageView](#stage-view)_ | Stage view settings. (Unavailable for public screen) |
| `slide_info` | _[SlideAdditionalInfo](#slide-additional-info)_ | Additional slide info |
| `slide_translation` | _String_ | translation name |
| `slide_translation_custom_settings` | _[TranslationCustomSettings](#translation-custom-settings)_ | Custom translation settings |
| `bible_version_tab` | _Number_ | Tab number (1, 2 or 3) of the Bible translation displayed on the screen, as translations are loaded in the Bible window |
| `margin` | _Object_ | Margins set in **Edit screen position** option. margin.top, margin.right, margin.bottom, margin.left |
| `area` | _[Rectangle](#rectangle)_ | Screen area with margins applied (if available) |
| `total_area` | _[Rectangle](#rectangle)_ | Total screen area on the system |
| `hide` | _Boolean_ | Hide screen |
| `show_items` | _Object_ | Defines the presentation types that will be displayed (only available for stream screens - image and html) |
| `show_items.lyrics` | _Boolean_ | Song lyrics |
| `show_items.text` | _Boolean_ | Text |
| `show_items.verse` | _Boolean_ | Verse |
| `show_items.image` | _Boolean_ | Image |
| `show_items.alert` | _Boolean_ | Alert |
| `show_items.announcement` | _Boolean_ | Announcement |
| `media_player.show` | _Boolean_ | Display VLC Player `v2.20.0+` |
| `media_player.margin` | _[Rectangle](#rectangle)_ | Margin for displaying videos by VLC Player `v2.20.0+` |
<details>
  <summary>See example</summary>

```json
{
  "id": "public",
  "name": "Público",
  "screen": "1920,0",
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
      "layout_text_row_1": "",
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
  "slide_translation_custom_settings": {
    "translation_1": {
      "name": "default",
      "style": "",
      "prefix": "",
      "suffix": ""
    },
    "translation_2": null,
    "translation_3": null,
    "translation_4": null,
    "merge": true,
    "uppercase": false,
    "blank_line_height": 40
  },
  "margin": {
    "top": 0.0,
    "right": 0.0,
    "bottom": 0.0,
    "left": 0.0
  },
  "area": {
    "x": 1920,
    "y": 0,
    "width": 1920,
    "height": 1080
  },
  "total_area": {
    "x": 1920,
    "y": 0,
    "width": 1920,
    "height": 1080
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
      "x": 1920,
      "y": 0,
      "width": 1920,
      "height": 1080
    }
  }
}
```
</details>

## Transition Effect Settings
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | Type of effect. Can be: `random` `fade` `slide` `accordion` `linear_fade` `zoom` `curtain` |
| `enabled` | _Boolean_ | Whether it is enabled or disabled |
| `duration` | _Number_ | Total duration of the transition (in milliseconds) `200 ~ 2400` |
| `only_area_within_margin` | _Number_ | Performs the transition effect only within the margin defined in the Theme. (Available only for text transition) |
| <br>**type=fade** |  |  |
| `merge` | _Object_ | Accepted values: true,&nbsp;false |
| `division_point` | _Object_ | Accepted values: min:&nbsp;10,&nbsp;max:&nbsp;100 |
| `increase_duration_blank_slides` | _Object_ | Accepted values: true,&nbsp;false |
| <br>**type=slide** |  |  |
| `direction` | _Object_ | Accepted values: random,&nbsp;left,&nbsp;up |
| `slide_move_type` | _Object_ | Accepted values: random,&nbsp;move_new,&nbsp;move_old,&nbsp;move_both |
| <br>**type=accordion** |  |  |
| `direction` | _Object_ | Accepted values: random,&nbsp;horizontal,&nbsp;vertical |
| <br>**type=linear_fade** |  |  |
| `direction` | _Object_ | Accepted values: random,&nbsp;horizontal,&nbsp;vertical,&nbsp;up,&nbsp;down,&nbsp;left,&nbsp;right |
| `distance` | _Object_ | Accepted values: min:&nbsp;5,&nbsp;max:&nbsp;90 |
| `fade` | _Object_ | Accepted values: min:&nbsp;2,&nbsp;max:&nbsp;90 |
| <br>**type=zoom** |  |  |
| `zoom_type` | _Object_ | Accepted values: random,&nbsp;increase,&nbsp;decrease |
| `directions` | _Object_ | Accepted values: {<br>&nbsp;&nbsp;top_left:&nbsp;boolean,<br>&nbsp;&nbsp;top_center:&nbsp;boolean,<br>&nbsp;&nbsp;top_right:&nbsp;boolean,<br>&nbsp;&nbsp;middle_left:&nbsp;boolean,<br>&nbsp;&nbsp;middle_center:&nbsp;boolean,<br>&nbsp;&nbsp;middle_right:&nbsp;boolean,<br>&nbsp;&nbsp;bottom_left:&nbsp;boolean,<br>&nbsp;&nbsp;bottom_center:&nbsp;boolean,<br>&nbsp;&nbsp;bottom_right:&nbsp;boolean<br>} |
| <br>**type=curtain** |  |  |
| `direction` | _Object_ | Accepted values: random,&nbsp;horizontal,&nbsp;vertical |
| `direction_lines` | _Object_ | Accepted values: random,&nbsp;down_right,&nbsp;up_left,&nbsp;alternate |
| `slide_move_type` | _Object_ | Accepted values: random,&nbsp;new,&nbsp;old,&nbsp;both |
| <br>**type=random** |  |  |
| `random_enabled_types` | _Object_ | Accepted values: {<br>&nbsp;&nbsp;fade:&nbsp;boolean,<br>&nbsp;&nbsp;slide:&nbsp;boolean,<br>&nbsp;&nbsp;accordion:&nbsp;boolean,<br>&nbsp;&nbsp;linear_fade:&nbsp;boolean,<br>&nbsp;&nbsp;zoom:&nbsp;boolean,<br>&nbsp;&nbsp;curtain:&nbsp;boolean<br>} |
<details>
  <summary>See example</summary>

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
| Name | Type  | Description |
| ---- | :---: | ------------|
| `tab_version_1` | _String_ | Bible version set in the first tab |
| `tab_version_2` | _String_ | Bible version set in the second tab |
| `tab_version_3` | _String_ | Bible version set in the third tab |
| `show_x_verses` | _Number_ | Number of verses displayed in the projection |
| `uppercase` | _Boolean_ | Display the verse text in uppercase |
| `show_only_reference` | _Boolean_ | Display only the verse reference |
| `show_two_versions` | _Boolean_ | `deprecated` Replaced for: `show_second_version` `show_third_version`<br>Display two versions. |
| `show_second_version` | _Boolean_ | Show second version `v2.22.0+` |
| `show_third_version` | _Boolean_ | Show third version `v2.22.0+` |
| `book_panel_type` | _String_ | Type of view of the books of the Bible `grid` `list` |
| `book_panel_order` | _String_ | Type of sorting of the books of the Bible |
| `book_panel_order_available_items` | _Array&lt;String&gt;_ |  |
| `multiple_verses_separator_type` | _String_ | Type of separation in the display of multiple verses. Can be: no_line_break, single_line_break, double_line_break |
| `multiple_versions_separator_type` | _String_ | Separation type in multiple version view. Can be: no_line_break, single_line_break, double_line_break `v2.22.0+` |
| `versification` | _Boolean_ | Apply verse mapping |
| `theme` | _Object_ | Display Theme ID for the different system screens |
| `theme.public` | _String_ |  |
| `theme.screen_n` | _String_ | n >= 2 |
<details>
  <summary>See example</summary>

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
    "automatic",
    "standard",
    "ru",
    "tyv"
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
| Name | Type  | Description |
| ---- | :---: | ------------|
| `font_name` | _String (optional)_ | Font name `Default: null` |
| `bold` | _Boolean (optional)_ | Bold `Default: null` |
| `italic` | _Boolean (optional)_ | Italic `Default: null` |
| `color` | _String (optional)_ | Color in hexadecimal `Default: null` |

## Stage View
| Name | Type  | Description |
| ---- | :---: | ------------|
| `enabled` | _Boolean_ | Stage view enabled |
| `preview_mode` | _String_ | Lyrics display mode. Available options:<br/>`CURRENT_SLIDE`<br>`FIRST_LINE_OF_THE_NEXT_SLIDE_WITH_SEPARATOR`<br>`FIRST_LINE_OF_THE_NEXT_SLIDE_WITHOUT_SEPARATOR`<br>`NEXT_SLIDE`<br>`CURRENT_AND_NEXT_SLIDE`<br>`ALL_SLIDES` |
| `uppercase` | _Boolean_ | Show in capital letters |
| `remove_line_break` | _Boolean_ | remove line break |
| `show_comment` | _Boolean_ | Show comments |
| `show_advanced_editor` | _Boolean_ | Show advanced editor |
| `show_communication_panel` | _Boolean_ | Show communication panel content |
| `show_next_image` | _Boolean_ | Display next image `v2.21.0+` |
| `custom_theme` | _String_ | Custom Theme ID used in presentations |
| `apply_custom_theme_to_bible` | _Boolean_ | Use custom theme in verses |
| `apply_custom_theme_to_text` | _Boolean_ | Use custom theme in texts |
| `apply_custom_theme_to_quick_presentation` | _Boolean_ | Use the custom theme in the **Quick Presentation** option `v2.21.0+` |
<details>
  <summary>See example</summary>

```json
{
  "enabled": false,
  "preview_mode": "FIRST_LINE_OF_THE_NEXT_SLIDE_WITH_SEPARATOR",
  "uppercase": false,
  "uppercase_mode": "text_and_comment",
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
| Name | Type  | Description |
| ---- | :---: | ------------|
| `info_1` | _Object_ |  |
| `info_1.show_page_count` | _Boolean_ | Show slide count |
| `info_1.show_slide_description` | _Boolean_ | Show slide description (chorus, i.e.) |
| `info_1.horizontal_align` | _String_ | Horizontal alignment of information on the slide. left, center, right |
| `info_1.vertical_align` | _String_ | Vertical alignment of information on the slide. top, bottom |
| `info_2` | _Object_ |  |
| `info_2.show` | _Boolean_ |  |
| `info_2.layout_row_1` | _String_ | Layout of the first line information **type=song** [Slide Additional Info Layout](#slide-additional-info-layout) |
| `info_2.layout_row_2` | _String (optional)_ | Layout of the second line information **type=song** [Slide Additional Info Layout](#slide-additional-info-layout) |
| `info_2.layout_text_row_1` | _String_ | Layout of the first line information **type=text** [Slide Additional Info Layout](#slide-additional-info-layout) `v2.24.0+` |
| `info_2.layout_text_row_2` | _String (optional)_ | Layout of the first line information **type=text** [Slide Additional Info Layout](#slide-additional-info-layout) `v2.24.0+` |
| `info_2.horizontal_align` | _String_ | Horizontal alignment of information on the slide. left, center, right |
| `info_2.vertical_align` | _String_ | Vertical alignment of information on the slide. top, bottom |
| `font` | _Object_ |  |
| `font.name` | _String_ | Font name. If it is **null**, it uses the theme's default font. |
| `font.bold` | _Boolean_ | Bold. If it is **null**, use the default theme setting |
| `font.italic` | _Boolean_ | Italid. If it is **null**, use the default theme setting |
| `font.color` | _String_ | Font color in hexadecimal. If it is **null**, use the theme's default font color |
| `height` | _Number_ | Height in percent of slide height `4 ~ 15` |
| `paint_theme_effect` | _String_ | Render text with theme outline, glow, and shadow effects, if available |
<details>
  <summary>See example</summary>

```json
{
  "info_1": {
    "show_page_count": false,
    "show_slide_description": false,
    "horizontal_align": "right",
    "vertical_align": "bottom"
  },
  "info_2": {
    "show": false,
    "layout_row_1": "<title>< (%author_or_artist%)>",
    "layout_text_row_1": "",
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
}
```
</details>

## Rectangle
| Name | Type  | Description |
| ---- | :---: | ------------|
| `x` | _Number_ |  |
| `y` | _Number_ |  |
| `width` | _Number_ |  |
| `height` | _Number_ |  |

## Custom Message
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Item name |
| `message_model` | _String_ | message without filling |
| `message_example` | _String_ | Example message with the name of the parameters filled in |
| `variables` | _Array&lt;[CustomMessageParam](#custom-message-param)&gt;_ | message parameters |
<details>
  <summary>See example</summary>

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
      "uppercase": false
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
| Name | Type  | Description |
| ---- | :---: | ------------|
| `position` | _Number_ | Parameter position in the message (in number of characters) |
| `name` | _String_ | Item name |
| `only_number` | _Boolean_ | Parameter accepts only numbers |
| `uppercase` | _Boolean_ | Parameter always displayed in uppercase |
| `suggestions` | _Array&lt;String&gt; (optional)_ | List with default values for the parameter |
<details>
  <summary>See example</summary>

```json
{
  "position": 0,
  "name": "",
  "only_number": false,
  "uppercase": false
}
```
</details>

## Quiz Question
| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | Item name `v2.24.0+` |
| `title` | _String_ | Question |
| `alternatives` | _Array&lt;String&gt;_ | Alternatives |
| `correct_alternative_number` | _Number (optional)_ | Number of the correct alternative. Starts at 1 `Default: 1` |
| `source` | _String (optional)_ | Answer font |
<details>
  <summary>See example</summary>

```json
{
  "name": "",
  "title": "...",
  "alternatives": [
    "Item 1",
    "Item 2",
    "Item 3"
  ],
  "correct_alternative_number": 2,
  "source": ""
}
```
</details>

## Quiz Settings
| Name | Type  | Description |
| ---- | :---: | ------------|
| `correct_answer_color_font` | _String (optional)_ | Font color for the correct answer |
| `correct_answer_color_background` | _String (optional)_ | Background color for the correct answer |
| `incorrect_answer_color_font` | _String (optional)_ | Font color for the incorrect answer |
| `incorrect_answer_color_background` | _String (optional)_ | Background color for the incorrect answer |
| `question_and_alternatives_different_slides` | _Boolean (optional)_ | Display the question and alternatives on separate slides `Default: false` |
| `display_alternatives_one_by_one` | _Boolean (optional)_ | Display the alternatives one by one `Default: true` |
| `alternative_char_type` | _String (optional)_ | Type of character to list the alternatives `number (1, 2, 3...)`  `alpha (A, B, C...)` `Default: 'alpha'` |
| `alternative_separator_char` | _String (optional)_ | Separator character. Allowed values:  ` `  `.`  `)`  `-`  `:` `Default: '.'` |
<details>
  <summary>See example</summary>

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
| Name | Type  | Description |
| ---- | :---: | ------------|
| `text` | _String_ | Slide text |
| `theme` | _[ThemeFilter](#theme-filter) (optional)_ | Filter selected theme for display |
| `custom_theme` | _[Theme](#theme) (optional)_ | Custom theme used to display the text |
| `translations` | _[Translations](#translations) (optional)_ |  |
| `duration` | _Number (optional)_ | Slide duration for use in automatic presentations |
<details>
  <summary>See example</summary>

```json
{
  "text": "text",
  "duration": 3,
  "translations": {
    "key1": "value1",
    "key2": "value2"
  },
  "theme": {
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
}
```
</details>

## Theme Filter
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String (optional)_ | Theme or background ID |
| `name` | _String (optional)_ | Theme name or background |
| `edit` | _[Theme](#theme) (optional)_ | Settings to modify the selected Theme for display |
<details>
  <summary>See example</summary>

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
Key/value pair

| Name | Type  | Description |
| ---- | :---: | ------------|
| `???` | _String_ | Translated value of the item, where the parameter name `???` is the name of the translation |
| `???` | _String_ |  |
| `...` | _String_ |  |
<details>
  <summary>See example</summary>

```json
{
  "key1": "value1",
  "key2": "value2"
}
```
</details>

## Wallpaper Settings
| Name | Type  | Description |
| ---- | :---: | ------------|
| `enabled` | _Boolean_ | Show wallpaper |
| `fill_color` | _String_ | Color in hexadecimal defined in the **fill** option. |
| `clock` | _[ClockSettings](#clock-settings)_ | Clock settings |
<details>
  <summary>See example</summary>

```json
{
  "enabled": null,
  "fill_color": null,
  "clock": {
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
}
```
</details>

## Clock Settings
| Name | Type  | Description |
| ---- | :---: | ------------|
| `enabled` | _Boolean_ |  |
| `font_name` | _String_ | Font name |
| `bold` | _Boolean_ | Bold |
| `italic` | _Boolean_ | Italic |
| `color` | _String_ | Color in hexadecimal format (RGBA) |
| `background` | _String_ | Color in hexadecimal format (RGBA) |
| `height` | _Number_ | Value in percentage based on the line height.<br>Accepted values: `6` `7` `8` `9` `10` `12` `14` `15` `16` `18` `20` `25` `30` `35` `40` |
| `position` | _Boolean_ | Accepted values: `top_left` `top_center` `top_right` `middle_left` `middle_center` `middle_right` `bottom_left` `bottom_center` `bottom_right` |
| `corner` | _Number_ | `0 ~ 100` |
<details>
  <summary>See example</summary>

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
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `name` | _String_ | Name in English |
| `language` | _String_ | ISO 639 two-letter language code `v2.24.0+` |
| `alt_name` | _String_ | Name in the language defined in `language`. Can be null. `v2.24.0+` |
<details>
  <summary>See example</summary>

```json
{
  "id": "en",
  "name": "English",
  "language": "en",
  "alt_name": "English"
}
```
</details>

## Bible Book Info
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Book ID `01 ~ 66` |
| `name` | _String_ | Book name |
| `abbrev` | _String_ | Book abbreviation |
| `usfx_code` | _String_ |  `v2.24.0+` |
<details>
  <summary>See example</summary>

```json
{
  "id": "01",
  "name": "Genesis",
  "abbrev": "Gn"
}
```
</details>

## Verse Reference Group
| Name | Type  | Description |
| ---- | :---: | ------------|
| `reference` | _String_ | References. Example: **John 3:16** or **Rm 12:2** or **Gn 1:1-3 Sl 23.1** |
| `ids` | _Array&lt;String&gt;_ | Example:  ['19023001', '43003016', '45012002'] |
| `verses` | _Array&lt;[VerseReference](#verse-reference)&gt;_ | Detailed list of references |
<details>
  <summary>See example</summary>

```json
{
  "reference": "Ps 23.1-2",
  "ids": [
    "19023001",
    "19023002"
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
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Item ID |
| `book` | _Number_ | Book ID `1 ~ 66` |
| `chapter` | _Number_ | Chapter |
| `verse` | _Number_ | Verse |
| `reference` | _String_ |  |
<details>
  <summary>See example</summary>

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

## Translation Custom Settings
Custom translation settings

| Name | Type  | Description |
| ---- | :---: | ------------|
| `translation_1` | _[TranslationCustomSettingsItem](#translation-custom-settings-item)_ |  |
| `translation_2` | _[TranslationCustomSettingsItem](#translation-custom-settings-item)_ |  |
| `translation_3` | _[TranslationCustomSettingsItem](#translation-custom-settings-item)_ |  |
| `translation_4` | _[TranslationCustomSettingsItem](#translation-custom-settings-item)_ |  |
| `merge` | _Boolean_ |  |
| `uppercase` | _Boolean_ |  |
| `blank_line_height` | _Number_ | `0 ~ 100` |
<details>
  <summary>See example</summary>

```json
{
  "translation_1": {
    "name": "default",
    "style": "",
    "prefix": "",
    "suffix": ""
  },
  "translation_2": null,
  "translation_3": null,
  "translation_4": null,
  "merge": false,
  "uppercase": false,
  "blank_line_height": 0
}
```
</details>

## Translation Custom Settings Item
Custom translation settings (item)

| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ | translation name. Use 'default' to use the original text. |
| `style` | _String_ | Custom text formatting. [Styled Text](https://github.com/holyrics/Scripts/blob/main/i18n/en/StyledText.md) |
| `prefix` | _String_ | Text added at the beginning of each line |
| `suffix` | _String_ | Text added at the end of each line |
<details>
  <summary>See example</summary>

```json
{
  "name": "default",
  "style": "",
  "prefix": "",
  "suffix": ""
}
```
</details>

## Styled Model
| Name | Type  | Description |
| ---- | :---: | ------------|
| `key` | _String_ |  |
| `properties` | _Object_ | Key/value pair |
<details>
  <summary>See example</summary>

```json
{
  "key": "title",
  "properties": {
    "b": "true",
    "size": "120"
  }
}
```
</details>

## Initial Slide Settings
| Name | Type  | Description |
| ---- | :---: | ------------|
| `display_mode` | _String_ | Accepted values: `title_author` `title_author_or_artist` `title` `title_artist` `blank` `remove` |
| `uppercase` | _Boolean_ |  |
| `automatic_line_break` | _Boolean_ |  |
| `underlined_title` | _Boolean_ |  |
| `title_font_relative_size` | _Number_ | `40 ~ 160` |
| `author_or_artist_font_relative_size` | _Number_ | `40 ~ 160` |
| `keep_ratio` | _Boolean_ |  |
| `remove_final_slide` | _Boolean_ |  |
<details>
  <summary>See example</summary>

```json
{
  "display_mode": "title_author_or_artist",
  "uppercase": false,
  "automatic_line_break": true,
  "underlined_title": true,
  "title_font_relative_size": 130,
  "author_or_artist_font_relative_size": 110,
  "keep_ratio": true,
  "remove_final_slide": false
}
```
</details>

## Copyright Settings
| Name | Type  | Description |
| ---- | :---: | ------------|
| `display_mode` | _String_ | Accepted values: `disabled` `first_slide` `all_slides` `last_slide` `display_for_x_seconds` |
| `seconds` | _String_ | Available if `display_mode=display_for_x_seconds`<br>Accepted values: `5` `10` `15` `20` `30` `60` `120` |
| `layout` | _String_ | Accepted values: `t,a` `t;a` `t,a;c` `t;a;c` |
| `font.name` | _String_ | Font name |
| `font.bold` | _String_ | Bold |
| `font.italic` | _String_ | Italic |
| `font.color` | _String_ | Color in hexadecimal format |
| `line_height` | _Number_ | `2.0 ~ 10.0` |
| `align` | _String_ | Accepted values: `left` `center` `right` |
| `opaticy` | _Number_ | `30 ~ 100` |
| `position` | _String_ | Accepted values: `top_left` `top_center` `top_right` `bottom_left` `bottom_center` `bottom_right` |
<details>
  <summary>See example</summary>

```json
{
  "display_mode": "all_slides",
  "layout": "t;a;c",
  "font": {
    "name": "Arial",
    "bold": true,
    "italic": true,
    "color": "FFFF00"
  },
  "line_height": 3.0,
  "align": "left",
  "opacity": 70,
  "position": "top_left"
}
```
</details>

## Image Presentation Settings
| Name | Type  | Description |
| ---- | :---: | ------------|
| `adjust_type` | _String_ | `adjust` `extend` |
| `blur` | _Object_ | Used only if: `adjust_type=adjust` |
| `blur.enabled` | _Boolean_ |  |
| `blur.radius` | _Number_ | `1 ~ 20` |
| `blur.times` | _Number_ | `1 ~ 10` |
| `blur.opacity` | _Number_ | `10 ~ 100` |
<details>
  <summary>See example</summary>

```json
{
  "adjust_type": "adjust",
  "blur": {
    "enabled": true,
    "radius": 8,
    "times": 5,
    "opacity": 70
  }
}
```
</details>

## Non-Latin Alphabet Support Settings
| Name | Type  | Description |
| ---- | :---: | ------------|
| `enabled` | _Boolean_ |  |
| `font_or_script` | _String_ | `system` `lucida_sans` `arial_unicode_ms` `nirmala_ui` `arabic` `armenian` `bengali` `bopomofo` `cyrillic` `devanagari` `georgian` `gujarati` `gurmukhi` `han` `hebrew` `hiragana` `kannada` `katakana` `malayalam` `meetei_mayek` `ol_chiki` `oriya` `sinhala` `tamil` `telugu` `thai` |
<details>
  <summary>See example</summary>

```json
{
  "enabled": false,
  "font_or_script": "system"
}
```
</details>

## Global Settings
| Name | Type  | Description |
| ---- | :---: | ------------|
| `fade_in_out_enabled` | _Boolean_ |  |
| `fade_in_out_duration` | _Number_ | `200 ~ 1200` |
| `show_history_main_window` | _Boolean_ |  |
| `show_favorite_bar_main_window` | _Boolean_ |  |
| `show_favorite_bar_bible_window` | _Boolean_ |  |
| `show_module_bar_main_window` | _Boolean_ |  |
| `show_module_bar_bible_window` | _Boolean_ |  |
| `show_automatic_presentation_tab_main_window` | _Boolean_ |  |
| `text_editor_font_name` | _String_ |  |
| `show_comment_main_window` | _Boolean_ |  |
| `show_comment_presentation_footer` | _Boolean_ |  |
| `show_comment_app` | _Boolean_ |  |
| `initial_slide` | _[InitialSlideSettings](#initial-slide-settings)_ |  |
| `copyright` | _Object_ | Key/value pair<br>key: `public` `screen_2` `screen_3` `screen_?` `stream_image`<br>valor: [CopyrightSettings](#copyright-settings) |
| `image_presentation` | _[ImagePresentationSettings](#image-presentation-settings)_ |  |
| `black_screen_color` | _String_ | Color in hexadecimal format |
| `swap_f5` | _Boolean_ |  |
| `stage_view_modifier_enabled` | _Boolean_ |  |
| `disable_modifier_automatically` | _Boolean_ |  |
| `automatic_presentation_theme_chooser` | _Boolean_ |  |
| `automatic_presentation_execution_delay` | _String_ | Accepted values: `0` `1000` `1500` `2000` `2500` `3000` |
| `skip_slide_transition_if_equals` | _Boolean_ |  |
| `non_latin_alphabet_support` | _[NonLatinAlphabetSupportSettings](#non-latin-alphabet-support-settings)_ |  |
| `public_screen_expand_width` | _Number_ | `0 ~ 3840` |
| `public_screen_rounded_border` | _Boolean_ |  |
| `public_screen_rounded_border_size` | _Number_ | `0 ~ 540` |
| `display_custom_formatting_enabled` | _Boolean_ |  |
| `display_custom_background_enabled` | _Boolean_ |  |
| `display_advanced_editor_enabled` | _Boolean_ |  |
| `advanced_editor_block_line_break` | _Boolean_ |  |
| `slide_description_repeat_description_for_sequence` | _Boolean_ |  |
| `standardize_automatic_line_break` | _Boolean_ |  |
| `allow_main_window_and_bible_window_simultaneously` | _Boolean_ |  |
| `preferential_arrangement_collection` | _String_ |  |
<details>
  <summary>See example</summary>

```json
{
  "fade_in_out_enabled": true,
  "fade_in_out_duration": 500,
  "show_history_main_window": true,
  "show_favorite_bar_main_window": true,
  "show_favorite_bar_bible_window": false,
  "show_module_bar_main_window": false,
  "show_module_bar_bible_window": false,
  "show_automatic_presentation_tab_main_window": false,
  "text_editor_font_name": "Lucida Sans Unicode",
  "show_comment_main_window": false,
  "show_comment_presentation_footer": true,
  "show_comment_app": true,
  "initial_slide": {
    "display_mode": "title_author_or_artist",
    "uppercase": false,
    "automatic_line_break": true,
    "underlined_title": true,
    "title_font_relative_size": 130,
    "author_or_artist_font_relative_size": 110,
    "keep_ratio": true,
    "remove_final_slide": false
  },
  "copyright": {
    "display_mode": "all_slides",
    "layout": "t;a;c",
    "font": {
      "name": "Arial",
      "bold": true,
      "italic": true,
      "color": "FFFF00"
    },
    "line_height": 3.0,
    "align": "left",
    "opacity": 70,
    "position": "top_left"
  },
  "image_presentation": {
    "adjust_type": "adjust",
    "blur": {
      "enabled": true,
      "radius": 8,
      "times": 5,
      "opacity": 70
    }
  },
  "black_screen_color": "1E1E1E",
  "swap_f5": false,
  "stage_view_modifier_enabled": true,
  "disable_modifier_automatically": true,
  "automatic_presentation_theme_chooser": true,
  "automatic_presentation_execution_delay": 0,
  "skip_slide_transition_if_equals": false,
  "non_latin_alphabet_support": {
    "enabled": false,
    "font_or_script": "system"
  },
  "public_screen_expand_width": 0,
  "public_screen_rounded_border": false,
  "public_screen_rounded_border_size": 100,
  "display_custom_formatting_enabled": true,
  "display_custom_background_enabled": true,
  "display_advanced_editor_enabled": true,
  "advanced_editor_block_line_break": true,
  "slide_description_repeat_description_for_sequence": true,
  "standardize_automatic_line_break": false,
  "allow_main_window_and_bible_window_simultaneously": false,
  "preferential_arrangement_collection": ""
}
```
</details>

## AddItem
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | Type of item. It can be: `title`  `song`  `verse`  `text`  `audio`  `video`  `image`  `file`  `announcement`  `automatic_presentation`  `countdown`  `countdown_cp`  `cp_text`  `plain_text`  `uri`  `global_action`  `api`  `script` |

## AddItemTitle
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | title |
| `name` | _String_ | Item name |
| `background_color` | _String (optional)_ | Background color in hexadecimal, example: 000080 |
| `collapsed` | _Boolean (optional)_ |  `Default: false` |
<details>
  <summary>See example</summary>

```json
{
  "type": "title",
  "name": "Example",
  "background_color": "0000FF",
  "collapsed": false
}
```
</details>

## AddItemSong
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | song |
| `id` | _String_ | Item ID |
<details>
  <summary>See example</summary>

```json
{
  "type": "song",
  "id": "123"
}
```
</details>

## AddItemVerse
**id**, **ids** or **references**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | verse |
| `id` | _String (optional)_ | To display a verse. Item ID in BBCCCVVV format.<br/>Example: '19023001' (book 19, chapter 023, verse 001) |
| `ids` | _Array&lt;String&gt; (optional)_ | To display a list of verses. List with the ID of each verse.<br/>Example: ['19023001', '43003016', '45012002'] |
| `references` | _String (optional)_ | References. Example: **John 3:16** or **Rm 12:2** or **Gn 1:1-3 Sl 23.1** |
| `version` | _String (optional)_ | Name or abbreviation of the translation used `v2.21.0+` |
<details>
  <summary>See example</summary>

```json
{
  "type": "verse",
  "references": "Ps 23.1-6 Rm 12.2",
  "version": "en_kjv"
}
```
</details>

## AddItemText
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | text |
| `id` | _String_ | Item ID |
<details>
  <summary>See example</summary>

```json
{
  "type": "text",
  "id": "xyz"
}
```
</details>

## AddItemAudio
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | audio |
| `name` | _String_ | File name |
| `settings` | _[PlayMediaSettings](#play-media-settings) (optional)_ | Settings for media execution `v2.21.0+` |
<details>
  <summary>See example</summary>

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
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | video |
| `name` | _String_ | File name |
| `settings` | _[PlayMediaSettings](#play-media-settings) (optional)_ | Settings for media execution `v2.21.0+` |
<details>
  <summary>See example</summary>

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
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | image |
| `name` | _String_ | File name |
<details>
  <summary>See example</summary>

```json
{
  "type": "image",
  "name": "file.ext"
}
```
</details>

## AddItemFile
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | file |
| `name` | _String_ | File name |
<details>
  <summary>See example</summary>

```json
{
  "type": "file",
  "name": "file.ext"
}
```
</details>

## AddItemAutomaticPresentation
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | automatic_presentation |
| `name` | _String_ | File name |
<details>
  <summary>See example</summary>

```json
{
  "type": "automatic_presentation",
  "name": "filename.ap"
}
```
</details>

## AddItemAnnouncement
**id**, **ids**, **name** or **names**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | announcement |
| `id` | _String (optional)_ | Announcement ID. Can be **all** to display all |
| `ids` | _Array&lt;String&gt; (optional)_ | List with the ID of each announcement |
| `name` | _String (optional)_ | Announcement name |
| `names` | _Array&lt;String&gt; (optional)_ | List with the name of each announcement |
| `automatic` | _[Automatic](#automatic) (optional)_ | If informed, the presentation of the items will be automatic |
<details>
  <summary>See example</summary>

```json
{
  "type": "announcement",
  "names": [
    "Anúncio 1",
    "Anúncio 2",
    "Anúncio 3"
  ],
  "automatic": {
    "seconds": 10,
    "repeat": true
  }
}
```
</details>

## AddItemCountdown
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | countdown |
| `time` | _String_ | HH:MM or MM:SS |
| `exact_time` | _Boolean (optional)_ | If **true**, `time` should be HH:MM (exact hour and minute). If **false**, `time` should be MM:SS (amount of minutes and seconds) `Default: false` |
| `text_before` | _String (optional)_ | Text displayed at the top of the countdown |
| `text_after` | _String (optional)_ | Text displayed at the bottom of the countdown |
| `zero_fill` | _Boolean (optional)_ | Fill in the 'minute' field with zero on the left `Default: false` |
| `hide_zero_minute` | _Boolean (optional)_ | Hide the display of minutes when it is zero `Default: false` `v2.25.0+` |
| `countdown_relative_size` | _Number (optional)_ | Relative size of the countdown `Default: 250` |
| `theme` | _[ThemeFilter](#theme-filter) (optional)_ | Filter selected theme for display `v2.21.0+` |
| `countdown_style` | _[FontSettings](#font-settings) (optional)_ | Custom font for countdown `v2.21.0+` |
<details>
  <summary>See example</summary>

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
  },
  "hide_zero_minute": false
}
```
</details>

## AddItemCountdownCommunicationPanel
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | countdown_cp |
| `minutes` | _Number_ | Number of minutes |
| `seconds` | _Number_ | Number of seconds |
| `stop_at_zero` | _Boolean (optional)_ | Stop the countdown when it reaches zero `Default: false` |
| `description` | _String_ | Item description |
<details>
  <summary>See example</summary>

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

## AddItemPlainText
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | plain_text |
| `name` | _String_ | Item name |
| `text` | _String_ | Text |
<details>
  <summary>See example</summary>

```json
{
  "type": "plain_text",
  "name": "",
  "text": "Example"
}
```
</details>

## AddItemTextCommunicationPanel
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | cp_text |
| `name` | _String_ | Item name |
| `text` | _String_ | Text |
| `display_ahead` | _Boolean (optional)_ | Change the *'display in front of all'* option |
<details>
  <summary>See example</summary>

```json
{
  "type": "cp_text",
  "name": "",
  "text": "Example",
  "display_ahead": false
}
```
</details>

## AddItemAddItemScript
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | script |
| `id` | _String_ | Item ID |
| `description` | _String_ | Item description |
| `inputs` | _Object (optional)_ | Default value for [Function Input](https://github.com/holyrics/Scripts/blob/main/i18n/en/FunctionInput.md) |
<details>
  <summary>See example</summary>

```json
{
  "type": "script",
  "id": "xyz",
  "description": "",
  "inputs": {
    "message": "Example",
    "duration": 30
  }
}
```
</details>

## AddItemAddItemAPI
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | api |
| `id` | _String_ | Item ID |
| `description` | _String_ | Item description |
| `inputs` | _Object (optional)_ | Default value for [Function Input](https://github.com/holyrics/Scripts/blob/main/i18n/en/FunctionInput.md) |
<details>
  <summary>See example</summary>

```json
{
  "type": "api",
  "id": "xyz",
  "description": "",
  "inputs": {
    "message": "Example",
    "duration": 30
  }
}
```
</details>

## AddItemURI
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | uri |
| `title` | _String_ | Item title |
| `uri_type` | _String_ | Can be: `spotify` `youtube` `deezer` |
| `value` | _String_ | URI |
<details>
  <summary>See example</summary>

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
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | global_action |
| `action` | _String_ | Can be: `slide_exit` `vlc_stop` `vlc_stop_fade_out` |

## SongInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Song ID |
| `title` | _String_ | Song title |
| `artist` | _String_ | Music artist |
| `author` | _String_ | Music author |
| `note` | _String_ | Music annotation |
| `copyright` | _String_ | Music copyright |
| `key` | _String_ | Tone of music.<br>Can be: `C` `C#` `Db` `D` `D#` `Eb` `E` `F` `F#` `Gb` `G` `G#` `Ab` `A` `A#` `Bb` `B` `Cm` `C#m` `Dbm` `Dm` `D#m` `Ebm` `Em` `Fm` `F#m` `Gbm` `Gm` `G#m` `Abm` `Am` `A#m` `Bbm` `Bm` |
| `bpm` | _Number_ | BPM of the song |
| `time_sig` | _String_ | Music time.<br>Can be: `2/2` `2/4` `3/4` `4/4` `5/4` `6/4` `3/8` `6/8` `7/8` `9/8` `12/8` |
<details>
  <summary>See example</summary>

```json
{
  "id": "0",
  "title": "",
  "artist": "",
  "author": "",
  "note": "",
  "copyright": "",
  "key": "",
  "bpm": 0.0,
  "time_sig": ""
}
```
</details>

## TextInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Text ID |
| `title` | _String_ | Text title |
<details>
  <summary>See example</summary>

```json
{
  "id": "",
  "title": ""
}
```
</details>

## VerseInfo
<details>
  <summary>See example</summary>

```json
{}
```
</details>

## AudioInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `file_name` | _String_ |  |
| `file_fullname` | _String_ |  |
| `file_relative_path` | _String_ |  |
| `file_path` | _String_ |  |
| `is_dir` | _Boolean_ |  |
| `extension` | _String_ |  |
| `properties` | _Object_ |  |
<details>
  <summary>See example</summary>

```json
{
  "file_name": "file.mp3",
  "file_fullname": "folder\\file.mp3",
  "file_relative_path": "audio\\folder\\file.mp3",
  "file_path": "C:\\Holyrics\\Holyrics\\files\\media\\audio\\folder\\file.mp3",
  "is_dir": false,
  "extension": "mp3"
}
```
</details>

## VideoInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `file_name` | _String_ |  |
| `file_fullname` | _String_ |  |
| `file_relative_path` | _String_ |  |
| `file_path` | _String_ |  |
| `is_dir` | _Boolean_ |  |
| `extension` | _String_ |  |
| `properties` | _Object_ |  |
<details>
  <summary>See example</summary>

```json
{
  "file_name": "file.mp4",
  "file_fullname": "folder\\file.mp4",
  "file_relative_path": "video\\folder\\file.mp4",
  "file_path": "C:\\Holyrics\\Holyrics\\files\\media\\video\\folder\\file.mp4",
  "is_dir": false,
  "extension": "mp4"
}
```
</details>

## ImageInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `file_name` | _String_ |  |
| `file_fullname` | _String_ |  |
| `file_relative_path` | _String_ |  |
| `file_path` | _String_ |  |
| `is_dir` | _Boolean_ |  |
| `extension` | _String_ |  |
| `properties` | _Object_ |  |
<details>
  <summary>See example</summary>

```json
{
  "file_name": "file.jpg",
  "file_fullname": "folder\\file.jpg",
  "file_relative_path": "image\\folder\\file.jpg",
  "file_path": "C:\\Holyrics\\Holyrics\\files\\media\\image\\folder\\file.jpg",
  "is_dir": false,
  "extension": "jpg"
}
```
</details>

## FileInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `file_name` | _String_ |  |
| `file_fullname` | _String_ |  |
| `file_relative_path` | _String_ |  |
| `file_path` | _String_ |  |
| `is_dir` | _Boolean_ |  |
| `extension` | _String_ |  |
| `properties` | _Object_ |  |
<details>
  <summary>See example</summary>

```json
{
  "file_name": "file.txt",
  "file_fullname": "folder\\file.txt",
  "file_relative_path": "file\\folder\\file.txt",
  "file_path": "C:\\Holyrics\\Holyrics\\files\\media\\file\\folder\\file.txt",
  "is_dir": false,
  "extension": "txt"
}
```
</details>

## AutomaticPresentationInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ |  |
<details>
  <summary>See example</summary>

```json
{
  "name": "name"
}
```
</details>

## AnnouncementInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _Number_ |  |
| `name` | _String_ |  |
<details>
  <summary>See example</summary>

```json
{
  "id": 0,
  "name": "name"
}
```
</details>

## SongSlideInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Song ID |
| `slide_index` | _Number_ |  |
| `slide_total` | _Number_ |  |
| `slide_description` | _String_ |  |
| `slide_show_index` | _Number_ |  |
| `slide_show_total` | _Number_ |  |
| `title` | _String_ | Song title |
| `artist` | _String_ | Music artist |
| `author` | _String_ | Music author |
| `note` | _String_ | Music annotation |
| `copyright` | _String_ | Music copyright |
| `key` | _String_ | Tone of music.<br>Can be: `C` `C#` `Db` `D` `D#` `Eb` `E` `F` `F#` `Gb` `G` `G#` `Ab` `A` `A#` `Bb` `B` `Cm` `C#m` `Dbm` `Dm` `D#m` `Ebm` `Em` `Fm` `F#m` `Gbm` `Gm` `G#m` `Abm` `Am` `A#m` `Bbm` `Bm` |
| `bpm` | _Number_ | BPM of the song |
| `time_sig` | _String_ | Music time.<br>Can be: `2/2` `2/4` `3/4` `4/4` `5/4` `6/4` `3/8` `6/8` `7/8` `9/8` `12/8` |
| `text` | _String_ |  |
| `comment` | _String_ |  |
| `extra` | _String_ |  |
<details>
  <summary>See example</summary>

```json
{
  "id": "0",
  "slide_index": 2,
  "slide_total": 8,
  "slide_description": "",
  "slide_show_index": 2,
  "slide_show_total": 12,
  "title": "",
  "artist": "",
  "author": "",
  "note": "",
  "copyright": "",
  "key": "",
  "bpm": 0.0,
  "time_sig": "",
  "text": "",
  "comment": "",
  "extra": ""
}
```
</details>

## TextSlideInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ | Text ID |
| `title` | _String_ | Text title |
| `text` | _String_ |  |
| `comment` | _String_ |  |
| `folder` | _String_ |  |
| `slide_index` | _String_ |  |
| `slide_total` | _String_ |  |
<details>
  <summary>See example</summary>

```json
{
  "id": "",
  "title": "",
  "text": "",
  "comment": "",
  "folder": "",
  "slide_index": 2,
  "slide_total": 8
}
```
</details>

## PPTInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `file_name` | _String_ |  |
| `file_fullname` | _String_ |  |
| `file_relative_path` | _String_ |  |
| `file_path` | _String_ |  |
| `is_dir` | _Boolean_ |  |
| `extension` | _String_ |  |
| `properties` | _Object_ |  |
<details>
  <summary>See example</summary>

```json
{
  "file_name": "file.txt",
  "file_fullname": "folder\\file.txt",
  "file_relative_path": "file\\folder\\file.txt",
  "file_path": "C:\\Holyrics\\Holyrics\\files\\media\\file\\folder\\file.txt",
  "is_dir": false,
  "extension": "txt"
}
```
</details>

## PPTSlideInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `file_name` | _String_ |  |
| `slide_number` | _Number_ |  |
| `slide_total` | _Number_ |  |
<details>
  <summary>See example</summary>

```json
{
  "file_name": "name",
  "slide_number": 1,
  "slide_total": 10
}
```
</details>

## ThemeInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _Number_ |  |
| `name` | _String_ |  |
| `from_user_list` | _Boolean_ |  |
| `tags` | _String_ |  |
| `bpm` | _String_ |  |
<details>
  <summary>See example</summary>

```json
{
  "id": 0,
  "name": "name",
  "from_user_list": true,
  "tags": "",
  "bpm": "0"
}
```
</details>

## BackgroundInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | `THEME` `MY_VIDEO` `MY_IMAGE` `VIDEO` `IMAGE` |
| `id` | _Number_ |  |
| `name` | _String_ |  |
| `from_user_list` | _Boolean_ |  |
| `tags` | _String_ |  |
| `bpm` | _String_ |  |
| `color_map` | _Array&lt;Object&gt;_ |  |
| `color_map.*.hex` | _String_ | Color in hexadecimal format |
| `color_map.*.red` | _Number_ | Red  `0 ~ 255` |
| `color_map.*.green` | _Number_ | Green  `0 ~ 255` |
| `color_map.*.blue` | _Number_ | Blue  `0 ~ 255` |
<details>
  <summary>See example</summary>

```json
{
  "type": "MY_VIDEO",
  "id": 0,
  "name": "name",
  "from_user_list": true,
  "tags": "",
  "bpm": "0",
  "color_map": [
    {
      "hex": "000000",
      "red": 0,
      "green": 0,
      "blue": 0
    },
    {
      "hex": "000000",
      "red": 0,
      "green": 0,
      "blue": 0
    },
    {
      "hex": "000000",
      "red": 0,
      "green": 0,
      "blue": 0
    },
    {
      "hex": "000000",
      "red": 0,
      "green": 0,
      "blue": 0
    },
    {
      "hex": "000000",
      "red": 0,
      "green": 0,
      "blue": 0
    },
    {
      "hex": "000000",
      "red": 0,
      "green": 0,
      "blue": 0
    },
    {
      "hex": "000000",
      "red": 0,
      "green": 0,
      "blue": 0
    },
    {
      "hex": "000000",
      "red": 0,
      "green": 0,
      "blue": 0
    }
  ]
}
```
</details>

## TitleInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `title` | _String_ |  |
| `subitem` | _Object_ |  |
| `subitem_index` | _Number_ |  |
| `playlist_index` | _Number_ |  |
<details>
  <summary>See example</summary>

```json
{
  "title": "",
  "subitem_index": -1,
  "playlist_index": -1
}
```
</details>

## WebcamInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `name` | _String_ |  |
| `fps` | _Number_ |  |
| `width` | _Number_ |  |
| `height` | _Number_ |  |
| `mute` | _Boolean_ |  |
| `aspect_ratio` | _String_ |  |
<details>
  <summary>See example</summary>

```json
{
  "name": "name",
  "fps": 30.0,
  "width": 1280,
  "height": 720,
  "mute": false,
  "aspect_ratio": "1:1"
}
```
</details>

## CountdownInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `time` | _String_ |  |
| `exact_time` | _Boolean_ |  |
| `text_before` | _String_ |  |
| `text_after` | _String_ |  |
| `zero_fill` | _Boolean_ |  |
| `countdown_relative_size` | _Number_ |  |
| `hide_zero_minute` | _Boolean_ |  |
<details>
  <summary>See example</summary>

```json
{
  "time": "",
  "exact_time": false,
  "text_before": "",
  "text_after": "",
  "zero_fill": false,
  "countdown_relative_size": 0,
  "hide_zero_minute": false
}
```
</details>

## AutomaticPresentationSlideInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ |  |
| `slide_index` | _Number_ |  |
<details>
  <summary>See example</summary>

```json
{
  "id": "filename.ap",
  "slide_index": 2
}
```
</details>

## PresentationModifierInfoInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `type` | _String_ | `WALLPAPER` `BLANK_SCREEN` `BLACK_SCREEN` |
| `name` | _String_ | Item name |
| `shortcut` | _String_ | `F8` `F9` `F10` |
| `presentation_type` | _String_ | `SONG` `TEXT` `VERSE` `ANY_ITEM` |
| `state` | _Boolean_ |  |
<details>
  <summary>See example</summary>

```json
{
  "type": "BLANK_SCREEN",
  "name": "Blank Screen",
  "shortcut": "F9",
  "presentation_type": "SONG",
  "state": false
}
```
</details>

## NewChatMessageInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ |  |
| `datetime` | _Number_ |  |
| `user_id` | _String_ |  |
| `name` | _String_ |  |
| `message` | _String_ |  |
<details>
  <summary>See example</summary>

```json
{
  "id": "1742142790725",
  "datetime": 1742142790725,
  "user_id": "-1qfe9t8wtrsb6p5",
  "name": "example",
  "message": "example"
}
```
</details>

## VersePresentationChangedInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `id` | _String_ |  |
| `book` | _Number_ |  |
| `chapter` | _Number_ |  |
| `verse` | _Number_ |  |
| `reference` | _String_ |  |
<details>
  <summary>See example</summary>

```json
{
  "id": "01001001",
  "book": 1,
  "chapter": 1,
  "verse": 1,
  "reference": "Gn 1:1"
}
```
</details>

## PlaylistChangedInfo
<details>
  <summary>See example</summary>

```json
{}
```
</details>

## FileModifiedInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `media_type` | _String_ |  |
| `action` | _String_ |  |
| `name` | _String_ |  |
| `is_dir` | _Boolean_ |  |
<details>
  <summary>See example</summary>

```json
{
  "media_type": "image",
  "action": "created",
  "name": "image.jpg",
  "is_dir": false
}
```
</details>

## PlayerProgressInfo
| Name | Type  | Description |
| ---- | :---: | ------------|
| `time` | _Number_ |  |
| `total` | _Number_ |  |
<details>
  <summary>See example</summary>

```json
{
  "time": 0,
  "total": 60000
}
```
</details>

# Slide Additional Info Layout
Type between the characters **< >** the texts you want to display
<br/>
And type inside **% %** the name of the field you want to use
<br/>
Example:

`<%title%>< (%author%)>`
<br/>
Turns into: **Title (Author)**
<br/>
But if the **author** field is not available, only **Title** will be displayed, not **Title ()**
<br/>

`<%title%>< - %author%>`
<br/>
Turns into: **Title - Author**
<br/>
But if the **author** field is not available, only **Title** will be displayed, not **Title -**
<br/>

It is also possible to use the **extra** fields created by the user for the songs, for example:
<br/>
If there is an extra field called **Year**, it can be used like this:
<br/>
`<title>< - %author%><, %Year%>`
<br/>
Turns into: **Title - Author, 2023**
