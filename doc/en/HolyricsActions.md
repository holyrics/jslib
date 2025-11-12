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
_No parameters are required_

---


### player_pause
_No parameters are required_

---


### player_stop
_No parameters are required_

---


### player_skip_previous
_No parameters are required_

---


### player_skip_next
_No parameters are required_

---


### player_mute
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### player_repeat
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### player_execute_list
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### player_fullscreen
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### player_shuffle
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### player_toggle_play_pause
_No parameters are required_

---


### player_toggle_play_stop
_No parameters are required_

---


### player_settings_volume
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `volume` | _Number_ | Volume `0 ~ 100` |


---


### player_settings_display_secondary_screens
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `screen` | _String_ | `screen_2` `screen_3` `screen_4` `screen_5` `screen_6` |
| `action` | _String_ | `toggle` `on` `off` |


---


### presentation_next
_No parameters are required_

---


### presentation_previous
_No parameters are required_

---


### presentation_close
_No parameters are required_

---


### presentation_f8
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### presentation_f9
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### presentation_f10
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### presentation_go_to_index
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `index` | _Number_ | Slide index |


---


### presentation_go_to_slide_description
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `slide_description` | _String_ | Slide description |


---


### presentation_set_background
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `background` | _String_ | Background |
| `when` | _String_ | `now` `changing_slides` |


---


### presentation_playlist_show_next_media
_No parameters are required_

---


### presentation_playlist_show_next_song
_No parameters are required_

---


### presentation_playlist_show_previous_media
_No parameters are required_

---


### presentation_playlist_show_previous_song
_No parameters are required_

---


### settings_open_window_settings
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `tab` | _String_ | `general` `layout` `display` `wallpaper` `several` `public_screen` `api_server` `advanced` |


---


### settings_open_window_display_settings
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `tab` | _String_ | `public` `screen_2` `screen_3` `screen_4` `screen_5` `screen_6` `stream_image` `stream_html_1` `stream_html_2` `stream_html_3` |


---


### settings_open_window_bible_settings
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `tab` | _String_ | `general` `verse_description` `show_version` `alternate_reading` `theme` |


---


### settings_settings_display_wallpaper
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_settings_display_clock
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_settings_display_logo
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_display_settings_hide_screen
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `screen` | _String_ | `public` `screen_2` `screen_3` `screen_4` `screen_5` `screen_6` |
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_bible_settings_display_only_reference
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_bible_settings_display_second_version
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_bible_settings_display_third_version
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_trigger_pause_for_tag
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `tag` | _String_ | Tag |
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_trigger_pause_for_receiver
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `receiver` | _String_ | Receiver |
| `action` | _String_ | `toggle` `on` `off` |


---


### settings_javascript_boolean_state
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `state_id` | _String_ | State (ID) |
| `action` | _String_ | `toggle` `on` `off` |


---


### interface_open_window_holyrics
_No parameters are required_

---


### interface_open_window_bible
_No parameters are required_

---


### interface_open_window_quick_presentation
_No parameters are required_

---


### interface_open_window_countdown
_No parameters are required_

---


### interface_open_window_announcements
_No parameters are required_

---


### interface_open_window_scheduled_tasks
_No parameters are required_

---


### interface_open_window_multiple_choice
_No parameters are required_

---


### interface_open_window_draw_lots
_No parameters are required_

---


### interface_open_window_logo
_No parameters are required_

---


### interface_open_window_scoreboard
_No parameters are required_

---


### interface_open_window_cp
_No parameters are required_

---


### interface_open_window_chat
_No parameters are required_

---


### interface_open_window_countdown_cp
_No parameters are required_

---


### interface_open_window_js_playground
_No parameters are required_

---


### interface_open_window_modules
_No parameters are required_

---


### interface_open_window_triggers
_No parameters are required_

---


### interface_open_window_scripts
_No parameters are required_

---


### interface_open_window_apis
_No parameters are required_

---


### interface_open_window_context_actions
_No parameters are required_

---


### interface_open_window_rules
_No parameters are required_

---


### interface_open_window_midi
_No parameters are required_

---


### interface_open_window_receivers
_No parameters are required_

---


### interface_open_window_telegram_questions
_No parameters are required_

---


### interface_open_window_telegram_poll
_No parameters are required_

---


### interface_open_window_telegram_files
_No parameters are required_

---


### interface_select_item_song
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `music` | _String_ | Item |


---


### interface_select_item_text
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `text` | _String_ | Item |


---


### interface_select_folder_text
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `text_folder` | _String_ | Folder |


---


### interface_select_item_audio
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `audio` | _String_ | Folder |


---


### interface_select_item_video
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `video` | _String_ | Folder |


---


### interface_select_item_image
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `image` | _String_ | Folder |


---


### interface_select_item_file
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `file` | _String_ | Folder |


---


### interface_select_item_custom_message
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `custom_message` | _String_ | Item |


---


### interface_select_item_automatic_presentation
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `automatic_presentation` | _String_ | Item |


---


### interface_select_playlist_tab_song
_No parameters are required_

---


### interface_select_playlist_tab_media
_No parameters are required_

---


### interface_select_playlist_tab_schedule
_No parameters are required_

---


### interface_select_playlist_tab_notes
_No parameters are required_

---


### interface_open_folder_audio
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `audio_folder` | _String_ | Folder |


---


### interface_open_folder_video
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `video_folder` | _String_ | Folder |


---


### interface_open_folder_image
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `image_folder` | _String_ | Folder |


---


### interface_open_folder_file
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `file_folder` | _String_ | Folder |


---


### interface_playlist_expand_collapse_title
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `action` | _String_ | `toggle` `on` `off` |
| `title` | _String_ | Title<br>Use the empty (blank) field to perform the action on all titles |


---


### interface_playlist_load_saved_list
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `model_id` | _String_ | List |
| `mode` | _String_ | `replace` `merge` |


---


### interface_bible_change_version
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `tab` | _Number_ | Tab `1 ~ 3` |
| `version` | _String_ | Version |


---


### interface_bible_set_displayed_verses
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `quantity` | _Number_ | Quantity `1 ~ 20` |


---


### interface_bible_split_long_verses
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `chars` | _String_ | `0` `50` `60` `70` `80` `90` `100` `120` `140` `150` `160` `180` `200` `225` `250` `275` `300` |


---


### interface_bible_select_verse
**Settings:**

| Name | Type  | Description |
| ---- | :---: | ------------|
| `verse` | _String_ | Verse<br>`BBCCCVVV` Example `43003016` (Jo 3.16) |


---
