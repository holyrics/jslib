# Holyrics - Starts an audio and countdown on return
Example of how to start playing a background music and a countdown to be displayed on the return screen.


```javascript
function foo() {
    //default list with possible duration (in minutes) of the countdown
    var arr = [15, 20, 25, 30, 40, 45, 60, 90];
    for (var i in arr) {
        arr[i] = {
            label: arr[i] + " minutes",
            minutes: arr[i]
        };
    }
    
    //displays a window to select the countdown duration
    var selected = h.itemChooser('Countdown', arr);
    if (selected == null) {
        //canceled by user
        return;
    }

    //plays the 'musical background.mp3' file from the audio folder
    h.playAudio('musical background.mp3');

    //example if you have a folder with several audios and you want to play one randomly
    /*
     var player = h.getPlayer();
     player.setShuffle(true);
     h.playAudio('musical background'); //file name
    */

    //starts the countdown on the return screen, with the number of minutes selected
    h.hly('StartCountdownCommunicationPanel', {
        minutes: selected.minutes,
        yellow_starts_at: 30 //seconds
    });
}

```

# Holyrics - Add music to playlist using clipboard text
Example to copy text from clipboard, search each line and add found song to playlist


```javascript
function foo() {
    //example to clear current playlist
    /*
     var indexes = [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15];
     h.hly('RemoveFromLyricsPlaylist', {'indexes': indexes});
     */

    var clipboard = h.getClipboard();
var arr = clipboard.split("\n");
for (var k in arr) {
    var text = arr[k];
    if (text.trim() == '' || text.trim().startsWith('//'))

        }

        var json = h.hly('SearchSong', {'text': text});
        if (json.data.length == 0) {
            h.log("Item not found: " + text);
        } else if (json.data.length == 1) {
            h.hly('AddLyricsToPlaylist', {'id': json.data[0].id});
        } else {
            //If found more than one result
            //will display a window for the user to choose an item by creating the 'label' property
            //because it will be displayed in the list as the item name
            json.data.forEach(function(m) {m.label = m.title + " (" + m.artist + ")";});
            var r = h.itemChooser(text + " - Multiple items found", json.data);
            if (r != null) {
                h.hly('AddLyricsToPlaylist', {'id': r.id});
            }
        }
    }
}
```

# OBS - List and change scene (ws v4)
Example of how to make a direct request to obs to obtain the list of available scenes, display the list for the user to choose a scene and change to the selected scene

(for websocket version 4)


```javascript
function foo() {
    //assuming you have a receiver created to communicate with OBS
    //use the name you gave the receiver, or the receiver ID
    var idOrName = 'xyz';

    //makes a direct request to obs to obtain the list of available scenes
    var r = h.apiRequest(idOrName, {
        'request-type': 'GetSceneList'
    });
    if (r == null) {
        //can be: obs studio closed, webservice disabled, incorrect ip, incorrect password, etc.
        h.log('Error getting scene list');
        return;
    }
    var json = JSON.parse(r);
    if (json.scenes.length == 0) {
        h.log('No scene found');
        return;
    }

    //create an array with only the scene name
    var scenes = [];
    for (var i = 0; i < json.scenes.length; i++) {
        scenes.push(json.scenes[i].name);
    }
    
    //displays a window for selecting a scene, displaying the list of all scenes
    var selectedScene = h.itemChooser('Select a scene', scenes);
    if (selectedScene == null) {
        //canceled by user
        return;
    }
    
    //makes a direct request to obs to change the current scene
    //passing the name of the previously selected scene as a parameter
    h.apiRequest(idOrName, {
        'request-type': 'SetCurrentScene',
        'scene-name': selectedScene
    });
}

```

# NOTE - List and change scene (ws v5)
Example of how to make a direct request to obs to obtain the list of available scenes, display the list for the user to choose a scene and change to the selected scene

(for websocket version 5)


```javascript
function foo() {
    //assuming you have a receiver created to communicate with OBS
    //use the name you gave the receiver, or the receiver ID
    var idOrName = 'xyz';

    //makes a direct request to obs to obtain the list of available scenes
    var r = h.apiRequest(idOrName, {
        'op': 6,
        'd': {
            'requestType': 'GetSceneList'
        }
    });
    if (r == null) {
        //can be: obs studio closed, webservice disabled, incorrect ip, incorrect password, etc.
        h.log('Error getting scene list');
        return;
    }
    var json = JSON.parse(r);
    json = json.d.responseData;
    if (json.scenes.length == 0) {
        h.log('No scene found');
        return;
    }

    //create an array with only the scene name
    //(FOR gets the array in descending form because the return from the v5 websocket comes in the opposite order displayed in the OBS list)
    var scenes = [];
    for (var i = json.scenes.length - 1; i >= 0; i--) {
        scenes.push(json.scenes[i].sceneName);
    }

    //displays a window for selecting a scene, displaying the list of all scenes
    var selectedScene = h.itemChooser('Select a scene', scenes);
    if (selectedScene == null) {
        //canceled by user
        return;
    }

    //makes a direct request to obs to change the current scene
    //passing the name of the previously selected scene as a parameter
    h.apiRequest(idOrName, {
        op: 6,
        d: {
            'requestType': 'SetCurrentProgramScene',
            'requestData': {
                'sceneName': selectedScene
            }
        }
    });
}

```
