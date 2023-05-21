# Flappy-Bird-com-Inteligência-Artificial 

Este aplicativo consiste em uma cópia do jogo Flappy Bird construído usando PyGame no qual o usuário tem a oportunidade de competir com uma IA.

O jogador controla um pássaro que deve desviar de todos os obstáculos para não morrer,
sendo estes: tubos (um dos quais de baixo e outro de cima),
o chão e o teto.
O pássaro é afetado pela gravidade e a única ação que o usuário pode realizar é para clicar para fazê-lo pular na tentativa de permanecer vivo.
O objetivo do jogo que criamos é derrotar o computador neste jogo. 

O projeto começou com a ideia desse video:
 [tutorial](https://www.youtube.com/watch?v=UZg49z76cLw).

## Treinando o passaro com a IA. 

### Diagrama de classe para treinamento:

![Arquitetura](https://github.com/TUIASI-AC-enaki/flappy-bird-with-ai/blob/main/documentation/architecture.png)

### Modelo da Inteligência Artificial

Para IA, usamos uma rede neural com 4 neurônios na camada de entrada (3 entradas e um bias) e um único neurônio de saída que descreve se deve ou não pressionar a tela para fazer o pássaro pular.

![Modelo de IA](https://github.com/TUIASI-AC-enaki/flappy-bird-with-ai/blob/main/documentation/neuron.png)

* __Bias__ - O neurônio de polarização.
* __H_bird__- A altura atual do pássaro em jogo.
* __H_bottom_pipe__ - A altura na qual o próximo tubo inferior está localizado.
* __H_top_pipe__ - A altura na qual o próximo tubo superior está localizado..


### Notas:

* Para treinamento foi utilizado o algoritmo genético, com 90% de chance de cruzamento, 20% de chance de mutação, número máximo de gerações 200.000.
* Como função de seleção tomamos um segmento aleatório composto por 50% dos indivíduos após o que os cruzamos chegamos no máximo ao tamanho da população infantil igual
ao inicial. Fazemos mutações e mantemos apenas os melhores indivíduos.
* Como função de fitness usamos a distância que um pássaro percorre até atingir um obstáculo.
* Quando a evolução é interrompida, ou todos os pássaros AI estão mortos, seus pesos e outras informações (gerações vivas, gerações ancestrais, pontuação média por todas as gerações vivas) são colocadas no arquivo training.json

## GUI

### Treinamento

Existem 2 botões:
* Start Evolution - comece a treinar usando os dados de training.json
* Stop Evolution - pare de treinar e atualize o training.json

Para iniciar o treinamento, execute o arquivo `training.py`.

### Jogo

Para iniciar o jogo, execute o arquivo `game.py. 

