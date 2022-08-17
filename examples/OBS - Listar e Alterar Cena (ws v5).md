# OBS - Listar e Alterar Cena (ws v5)
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
