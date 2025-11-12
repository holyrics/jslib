# Holyrics Actions

---

  - [player_play](#playerplay)
  - [player_pause](#playerpause)
  - [player_stop](#playerstop)
  - [player_skip_previous](#playerskipprevious)
  - [player_skip_next](#playerskipnext)
  - [player_mute](#playermute)
  - [player_repeat](#playerrepeat)
  - [player_execute_list](#playerexecutelist)
  - [player_fullscreen](#playerfullscreen)
  - [player_shuffle](#playershuffle)
  - [player_toggle_play_pause](#playertoggleplaypause)
  - [player_toggle_play_stop](#playertoggleplaystop)
  - [player_settings_volume](#playersettingsvolume)
  - [player_settings_display_secondary_screens](#playersettingsdisplaysecondaryscreens)
  - [presentation_next](#presentationnext)
  - [presentation_previous](#presentationprevious)
  - [presentation_close](#presentationclose)
  - [presentation_f8](#presentationf8)
  - [presentation_f9](#presentationf9)
  - [presentation_f10](#presentationf10)
  - [presentation_go_to_index](#presentationgotoindex)
  - [presentation_go_to_slide_description](#presentationgotoslidedescription)
  - [presentation_set_background](#presentationsetbackground)
  - [presentation_playlist_show_next_media](#presentationplaylistshownextmedia)
  - [presentation_playlist_show_next_song](#presentationplaylistshownextsong)
  - [presentation_playlist_show_previous_media](#presentationplaylistshowpreviousmedia)
  - [presentation_playlist_show_previous_song](#presentationplaylistshowprevioussong)
  - [settings_open_window_settings](#settingsopenwindowsettings)
  - [settings_open_window_display_settings](#settingsopenwindowdisplaysettings)
  - [settings_open_window_bible_settings](#settingsopenwindowbiblesettings)
  - [settings_settings_display_wallpaper](#settingssettingsdisplaywallpaper)
  - [settings_settings_display_clock](#settingssettingsdisplayclock)
  - [settings_settings_display_logo](#settingssettingsdisplaylogo)
  - [settings_display_settings_hide_screen](#settingsdisplaysettingshidescreen)
  - [settings_bible_settings_display_only_reference](#settingsbiblesettingsdisplayonlyreference)
  - [settings_bible_settings_display_second_version](#settingsbiblesettingsdisplaysecondversion)
  - [settings_bible_settings_display_third_version](#settingsbiblesettingsdisplaythirdversion)
  - [settings_trigger_pause_for_tag](#settingstriggerpausefortag)
  - [settings_trigger_pause_for_receiver](#settingstriggerpauseforreceiver)
  - [settings_javascript_boolean_state](#settingsjavascriptbooleanstate)
  - [interface_open_window_holyrics](#interfaceopenwindowholyrics)
  - [interface_open_window_bible](#interfaceopenwindowbible)
  - [interface_open_window_quick_presentation](#interfaceopenwindowquickpresentation)
  - [interface_open_window_countdown](#interfaceopenwindowcountdown)
  - [interface_open_window_announcements](#interfaceopenwindowannouncements)
  - [interface_open_window_scheduled_tasks](#interfaceopenwindowscheduledtasks)
  - [interface_open_window_multiple_choice](#interfaceopenwindowmultiplechoice)
  - [interface_open_window_draw_lots](#interfaceopenwindowdrawlots)
  - [interface_open_window_logo](#interfaceopenwindowlogo)
  - [interface_open_window_scoreboard](#interfaceopenwindowscoreboard)
  - [interface_open_window_cp](#interfaceopenwindowcp)
  - [interface_open_window_chat](#interfaceopenwindowchat)
  - [interface_open_window_countdown_cp](#interfaceopenwindowcountdowncp)
  - [interface_open_window_js_playground](#interfaceopenwindowjsplayground)
  - [interface_open_window_modules](#interfaceopenwindowmodules)
  - [interface_open_window_triggers](#interfaceopenwindowtriggers)
  - [interface_open_window_scripts](#interfaceopenwindowscripts)
  - [interface_open_window_apis](#interfaceopenwindowapis)
  - [interface_open_window_context_actions](#interfaceopenwindowcontextactions)
  - [interface_open_window_rules](#interfaceopenwindowrules)
  - [interface_open_window_midi](#interfaceopenwindowmidi)
  - [interface_open_window_receivers](#interfaceopenwindowreceivers)
  - [interface_open_window_telegram_questions](#interfaceopenwindowtelegramquestions)
  - [interface_open_window_telegram_poll](#interfaceopenwindowtelegrampoll)
  - [interface_open_window_telegram_files](#interfaceopenwindowtelegramfiles)
  - [interface_select_item_song](#interfaceselectitemsong)
  - [interface_select_item_text](#interfaceselectitemtext)
  - [interface_select_folder_text](#interfaceselectfoldertext)
  - [interface_select_item_audio](#interfaceselectitemaudio)
  - [interface_select_item_video](#interfaceselectitemvideo)
  - [interface_select_item_image](#interfaceselectitemimage)
  - [interface_select_item_file](#interfaceselectitemfile)
  - [interface_select_item_custom_message](#interfaceselectitemcustommessage)
  - [interface_select_item_automatic_presentation](#interfaceselectitemautomaticpresentation)
  - [interface_select_playlist_tab_song](#interfaceselectplaylisttabsong)
  - [interface_select_playlist_tab_media](#interfaceselectplaylisttabmedia)
  - [interface_select_playlist_tab_schedule](#interfaceselectplaylisttabschedule)
  - [interface_select_playlist_tab_notes](#interfaceselectplaylisttabnotes)
  - [interface_open_folder_audio](#interfaceopenfolderaudio)
  - [interface_open_folder_video](#interfaceopenfoldervideo)
  - [interface_open_folder_image](#interfaceopenfolderimage)
  - [interface_open_folder_file](#interfaceopenfolderfile)
  - [interface_playlist_expand_collapse_title](#interfaceplaylistexpandcollapsetitle)
  - [interface_playlist_load_saved_list](#interfaceplaylistloadsavedlist)
  - [interface_bible_change_version](#interfacebiblechangeversion)
  - [interface_bible_set_displayed_verses](#interfacebiblesetdisplayedverses)
  - [interface_bible_split_long_verses](#interfacebiblesplitlongverses)
  - [interface_bible_select_verse](#interfacebibleselectverse)


### player_play
_Nenhum parâmetro é necessário_

---


### player_pause
_Nenhum parâmetro é necessário_

---


### player_stop
_Nenhum parâmetro é necessário_

---


### player_skip_previous
_Nenhum parâmetro é necessário_

---


### player_skip_next
_Nenhum parâmetro é necessário_

---


### player_mute
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### player_repeat
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### player_execute_list
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### player_fullscreen
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### player_shuffle
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### player_toggle_play_pause
_Nenhum parâmetro é necessário_

---


### player_toggle_play_stop
_Nenhum parâmetro é necessário_

---


### player_settings_volume
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `volume` | _Number_ | Volume `0 ~ 100` |


---


### player_settings_display_secondary_screens
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `screen` | _String_ | `screen_2` `screen_3` `screen_4` `screen_5` `screen_6` |
| `action` | _String_ | `toggle` `on` `off` |


---


### presentation_next
_Nenhum parâmetro é necessário_

---


### presentation_previous
_Nenhum parâmetro é necessário_

---


### presentation_close
_Nenhum parâmetro é necessário_

---


### presentation_f8
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### presentation_f9
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### presentation_f10
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### presentation_go_to_index
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `index` | _Number_ | Índice do slide |


---


### presentation_go_to_slide_description
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `slide_description` | _String_ | Descrição do slide |


---


### presentation_set_background
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `background` | _String_ | Plano de Fundo |
| `when` | _String_ | `now` `changing_slides` |


---


### presentation_playlist_show_next_media
_Nenhum parâmetro é necessário_

---


### presentation_playlist_show_next_song
_Nenhum parâmetro é necessário_

---


### presentation_playlist_show_previous_media
_Nenhum parâmetro é necessário_

---


### presentation_playlist_show_previous_song
_Nenhum parâmetro é necessário_

---


### settings_open_window_settings
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `tab` | _String_ | `general` `layout` `display` `wallpaper` `several` `public_screen` `api_server` `advanced` |


---


### settings_open_window_display_settings
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `tab` | _String_ | `public` `screen_2` `screen_3` `screen_4` `screen_5` `screen_6` `stream_image` `stream_html_1` `stream_html_2` `stream_html_3` |


---


### settings_open_window_bible_settings
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `tab` | _String_ | `general` `verse_description` `show_version` `alternate_reading` `theme` |


---


### settings_settings_display_wallpaper
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_settings_display_clock
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_settings_display_logo
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_display_settings_hide_screen
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `screen` | _String_ | `public` `screen_2` `screen_3` `screen_4` `screen_5` `screen_6` |
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_bible_settings_display_only_reference
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_bible_settings_display_second_version
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_bible_settings_display_third_version
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_trigger_pause_for_tag
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `tag` | _String_ | Tag |
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_trigger_pause_for_receiver
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `receiver` | _String_ | Receptor |
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_javascript_boolean_state
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `state_id` | _String_ | Estado (ID) |
| `action` | _String_ | `toggle` `on` `off` |


---


### interface_open_window_holyrics
_Nenhum parâmetro é necessário_

---


### interface_open_window_bible
_Nenhum parâmetro é necessário_

---


### interface_open_window_quick_presentation
_Nenhum parâmetro é necessário_

---


### interface_open_window_countdown
_Nenhum parâmetro é necessário_

---


### interface_open_window_announcements
_Nenhum parâmetro é necessário_

---


### interface_open_window_scheduled_tasks
_Nenhum parâmetro é necessário_

---


### interface_open_window_multiple_choice
_Nenhum parâmetro é necessário_

---


### interface_open_window_draw_lots
_Nenhum parâmetro é necessário_

---


### interface_open_window_logo
_Nenhum parâmetro é necessário_

---


### interface_open_window_scoreboard
_Nenhum parâmetro é necessário_

---


### interface_open_window_cp
_Nenhum parâmetro é necessário_

---


### interface_open_window_chat
_Nenhum parâmetro é necessário_

---


### interface_open_window_countdown_cp
_Nenhum parâmetro é necessário_

---


### interface_open_window_js_playground
_Nenhum parâmetro é necessário_

---


### interface_open_window_modules
_Nenhum parâmetro é necessário_

---


### interface_open_window_triggers
_Nenhum parâmetro é necessário_

---


### interface_open_window_scripts
_Nenhum parâmetro é necessário_

---


### interface_open_window_apis
_Nenhum parâmetro é necessário_

---


### interface_open_window_context_actions
_Nenhum parâmetro é necessário_

---


### interface_open_window_rules
_Nenhum parâmetro é necessário_

---


### interface_open_window_midi
_Nenhum parâmetro é necessário_

---


### interface_open_window_receivers
_Nenhum parâmetro é necessário_

---


### interface_open_window_telegram_questions
_Nenhum parâmetro é necessário_

---


### interface_open_window_telegram_poll
_Nenhum parâmetro é necessário_

---


### interface_open_window_telegram_files
_Nenhum parâmetro é necessário_

---


### interface_select_item_song
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `music` | _String_ | Item |


---


### interface_select_item_text
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `text` | _String_ | Item |


---


### interface_select_folder_text
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `text_folder` | _String_ | Pasta |


---


### interface_select_item_audio
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `audio` | _String_ | Pasta |


---


### interface_select_item_video
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `video` | _String_ | Pasta |


---


### interface_select_item_image
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `image` | _String_ | Pasta |


---


### interface_select_item_file
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `file` | _String_ | Pasta |


---


### interface_select_item_custom_message
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `custom_message` | _String_ | Item |


---


### interface_select_item_automatic_presentation
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `automatic_presentation` | _String_ | Item |


---


### interface_select_playlist_tab_song
_Nenhum parâmetro é necessário_

---


### interface_select_playlist_tab_media
_Nenhum parâmetro é necessário_

---


### interface_select_playlist_tab_schedule
_Nenhum parâmetro é necessário_

---


### interface_select_playlist_tab_notes
_Nenhum parâmetro é necessário_

---


### interface_open_folder_audio
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `audio_folder` | _String_ | Pasta |


---


### interface_open_folder_video
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `video_folder` | _String_ | Pasta |


---


### interface_open_folder_image
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `image_folder` | _String_ | Pasta |


---


### interface_open_folder_file
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `file_folder` | _String_ | Pasta |


---


### interface_playlist_expand_collapse_title
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |
| `title` | _String_ | Título<br>Utilize o campo vazio (em branco) para executar a ação em todos os títulos |


---


### interface_playlist_load_saved_list
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `model_id` | _String_ | Lista |
| `mode` | _String_ | `replace` `merge` |


---


### interface_bible_change_version
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `tab` | _Number_ | Aba `1 ~ 3` |
| `version` | _String_ | Versão |


---


### interface_bible_set_displayed_verses
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `quantity` | _Number_ | Quantidade `1 ~ 20` |


---


### interface_bible_split_long_verses
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `chars` | _String_ | `0` `50` `60` `70` `80` `90` `100` `120` `140` `150` `160` `180` `200` `225` `250` `275` `300` |


---


### interface_bible_select_verse
**Settings:**

| Nome | Tipo  | Descrição |
| ---- | :---: | ------------|
| `verse` | _String_ | Versículo<br>`BBCCCVVV` Exemplo `43003016` (Jo 3.16) |


---
