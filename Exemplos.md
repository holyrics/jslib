# Holyrics - Inicia um áudio e uma contagem regressiva no retorno
Exemplo de como iniciar a execução de um fundo musical e uma contagem regressiva para ser exibida na tela de retorno.


```javascript
function foo() {
    //lista padrão com a possível duração (em minutos) da contagem regressiva
    var arr = [15, 20, 25, 30, 40, 45, 60, 90];
    for (var i in arr) {
        arr[i] = {
            label: arr[i] + " minutos",
            minutes: arr[i]
        };
    }
    
    //exibe uma janela para selecionar a duração da contagem regressiva
    var selected = h.itemChooser('Contagem regressiva', arr);
    if (selected == null) {
        //cancelado pelo usuário
        return;
    }

    //executa o arquivo 'fundo musical.mp3' da pasta de áudio
    h.playAudio('fundo musical.mp3');

    //exemplo caso tenha uma pasta com vários áudios e queira executar um aleatoriamente
    /*
     var player = h.getPlayer();
     player.setShuffle(true);
     h.playAudio('fundo musical'); //nome da pasta
    */

    //inicia a contagem regressiva na tela de retorno, com a quantidade de minutos selecionada
    h.hly('StartCountdownCommunicationPanel', {
        minutes: selected.minutes,
        yellow_starts_at: 30 //segundos
    });
}

```

# Holyrics - Adicionar música na lista de reprodução utilizando o texto da área de transferência
Exemplo para copiar o texto da área de transferência, pesquisar cada linha e adicionar a música encontrada na lista de reprodução


```javascript
function foo() {
    //exemplo para limpar a lista de reprodução atual
    /*
     var indexes = [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15];
     h.hly('RemoveFromLyricsPlaylist', {'indexes': indexes});
     */

    var clipboard = h.getClipboard();
    var arr = clipboard.split("\n");
    for (var k in arr) {
        var text = arr[k];
        if (text.trim() == '' || text.trim().startsWith('//')) { //desconsiderar valores vazios
            continue;
        }
        var json = h.hly('SearchSong', {'text': text});
        if (json.data.length == 0) {
            h.log("Item não encontrado: " + text);
        } else if (json.data.length == 1) {
            h.hly('AddLyricsToPlaylist', {'id': json.data[0].id});
        } else {
            //caso encontre mais de um resultado
            //vai exibir uma janela para o usuário escolher um item criando a propriedade 'label'
            //pois é ela que será exibida na lista como nome do item
            json.data.forEach(function(m) {m.label = m.title + " (" + m.artist + ")";});
            var r = h.itemChooser(text + " - Múltiplos itens encontrados", json.data);
            if (r != null) {
                h.hly('AddLyricsToPlaylist', {'id': r.id});
            }
        }
    }
}
```

# OBS - Listar e alterar cena (ws v4)
Exemplo de como realizar uma requisição direta ao obs para obter a lista de cenas disponíveis, exibir a lista para o usuário escolher uma cena e alterar para a cena selecionada

(para websocket versão 4)


```javascript
function foo() {
    //considerando que você tenha um receptor criado para comunicação com o OBS
    //utilize o nome que você deu ao receptor, ou o ID do receptor
    var idOrName = 'xyz';

    //realiza uma requisição direta ao obs para obter a lista de cenas disponíveis
    var r = h.apiRequest(idOrName, {
        'request-type': 'GetSceneList'
    });
    if (r == null) {
        //pode ser: obs studio fechado, webservice desativado, ip incorreto, senha incorreta, etc
        h.log('Erro ao obter lista de cenas');
        return;
    }
    var json = JSON.parse(r);
    if (json.scenes.length == 0) {
        h.log('Nenhuma cena encontrada');
        return;
    }

    //cria um array com somente o nome da cena
    var scenes = [];
    for (var i = 0; i < json.scenes.length; i++) {
        scenes.push(json.scenes[i].name);
    }
    
    //exibe uma janela para selecionar uma cena, exibindo a lista de todas as cenas
    var selectedScene = h.itemChooser('Selecione uma cena', scenes);
    if (selectedScene == null) {
        //cancelado pelo usuário
        return;
    }
    
    //realiza uma requisição direta ao obs para alterar a cena atual
    //passando o nome da cena selecionada anteriormente como parâmetro
    h.apiRequest(idOrName, {
        'request-type': 'SetCurrentScene',
        'scene-name': selectedScene
    });
}

```

# OBS - Listar e alterar cena (ws v5)
Exemplo de como realizar uma requisição direta ao obs para obter a lista de cenas disponíveis, exibir a lista para o usuário escolher uma cena e alterar para a cena selecionada

(para websocket versão 5)


```javascript
function foo() {
    //considerando que você tenha um receptor criado para comunicação com o OBS
    //utilize o nome que você deu ao receptor, ou o ID do receptor
    var idOrName = 'xyz';

    //realiza uma requisição direta ao obs para obter a lista de cenas disponíveis
    var r = h.apiRequest(idOrName, {
        'op': 6,
        'd': {
            'requestType': 'GetSceneList'
        }
    });
    if (r == null) {
        //pode ser: obs studio fechado, webservice desativado, ip incorreto, senha incorreta, etc
        h.log('Erro ao obter lista de cenas');
        return;
    }
    var json = JSON.parse(r);
    json = json.d.responseData;
    if (json.scenes.length == 0) {
        h.log('Nenhuma cena encontrada');
        return;
    }

    //cria um array com somente o nome da cena
    //(o FOR obtém o array em forma decrescente pois o retorno do websocket da v5 vem na ordem contrária exibida na lista do OBS)
    var scenes = [];
    for (var i = json.scenes.length - 1; i >= 0; i--) {
        scenes.push(json.scenes[i].sceneName);
    }

    //exibe uma janela para selecionar uma cena, exibindo a lista de todas as cenas
    var selectedScene = h.itemChooser('Selecione uma cena', scenes);
    if (selectedScene == null) {
        //cancelado pelo usuário
        return;
    }

    //realiza uma requisição direta ao obs para alterar a cena atual
    //passando o nome da cena selecionada anteriormente como parâmetro
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
