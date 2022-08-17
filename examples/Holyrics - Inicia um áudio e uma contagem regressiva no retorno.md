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
