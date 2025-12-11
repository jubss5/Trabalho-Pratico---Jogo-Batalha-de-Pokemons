# Trabalho-Pratico---Jogo-Batalha-de-Pokemons

O objetivo do programa é simular uma batalha Pokémon por turnos entre dois treinadores. O sistema calcula o dano causado (ajustado por tipo e atributos) até que um time seja completamente derrotado, determinando o vencedor da simulação.

No trabalho prático de desenvolvimento do jogo Pokémon, realizei a implementação de um programa em linguagem C para fazer uma batalha simples entre dois treinadores, ou seja, os jogadores, cada um com seus Pokémons. O programa consiste em simular uma batalha entre Pokémons, assim como no jogo, dado que cada jogador possui de 1 a N Pokémons, e cada um deles possui alguns atributos que serão utilizados na lógica da batalha. Esses atributos são: nome do Pokémon, ataque, que é a quantidade de poder ofensivo que ele possui; defesa, que é sua capacidade defensiva; vida, que representa o quanto de saúde ele tem; e, por fim, o tipo de Pokémon, que pode ser fogo, água, pedra, gelo ou elétrico. Esses tipos são utilizados para calcular o impacto do ataque do Pokémon que está atacando no momento.
A lógica da batalha consiste em um sistema de turnos entre o jogador 1 e o jogador 2. O jogador atacante utiliza seu poder de ataque contra o poder de defesa do inimigo. Se o valor de ataque for maior que o de defesa, subtrai-se da vida do oponente a diferença entre eles. Caso contrário, é subtraído apenas 1 ponto de vida.
No entanto, para realizar o ataque, é necessário calcular o dano com base na relação de tipos dos Pokémons, que será explicada na descrição do algoritmo. Basicamente, trata-se de aumentar o ataque em 20 por cento ou reduzir em 20 por cento, dependendo dessa relação.
Por fim, caso um Pokémon seja derrotado, o próximo Pokémon do time é enviado para a batalha, e o duelo continua até que todos os Pokémons de um dos jogadores sejam derrotados.
A entrada do programa consiste na leitura de um arquivo .txt em que a primeira linha contém dois números, N e M, que representam, respectivamente, o número de Pokémons do jogador 1 e do jogador 2. As linhas seguintes contêm os atributos mencionados anteriormente, na ordem em que foram citados. O programa deve retornar o que foi lido do arquivo e o resultado da batalha, indicando qual jogador venceu, quais Pokémons sobreviveram e quais foram derrotados.
Portanto, o código tem por objetivo determinar qual dos dois treinadores é o vencedor ao derrotar toda a equipe adversária.

Exemplo de Execução:
Input: 
3 2 
Squirtle 10 15 15 agua 
Vulpix 15 15 15 fogo 
Onix 5 20 20 pedra 
Golem 20 5 10 pedra 
Charmander 20 15 12 fogo

Processo:
O programa começa lendo os Pokémons do arquivo e formando as equipes: o Jogador 1 fica com Squirtle, Vulpix e Onix, e o Jogador 2 fica com Golem e Charmander. A simulação segue em turnos, aplicando o dano, calculando a eficácia dos ataques e fazendo o arredondamento dos valores quando necessário.

A simulação por turnos é controlada pela função batalha. Os índices ativos, indj1 e indj2, começam em 0, representando que Squirtle e Golem são os primeiros Pokémons a entrar na batalha.

Na primeira batalha, no turno 1, Squirtle ataca Golem. O ataque de Squirtle, que é do tipo água, contra Golem, que é do tipo pedra, resulta em uma relação neutra (1.0x). O dano é calculado e aplicado, mas Golem sobrevive.

No turno 2, Golem ataca Squirtle. O ataque de Golem, do tipo pedra, contra Squirtle, do tipo água, também resulta em uma relação neutra (1.0x). Squirtle sobrevive e a batalha continua. Após vários turnos trocando golpes, Squirtle derrota Golem. Golem é derrotado e Charmander, que está no índice 1, entra em campo pelo jogador 2. O Pokémon Golem é então registrado na lista de derrotados do jogador 2.

Na batalha 2, no turno 1, Squirtle ataca Charmander. O ataque de Squirtle, do tipo água, contra Charmander, do tipo fogo, resulta em uma relação de vantagem (1.2x). O ataque é aumentado, mas a defesa de Charmander é alta o bastante para que, em muitos turnos, apenas o dano mínimo de 1 seja aplicado.

No turno 2, Charmander ataca Squirtle. O ataque de Charmander, do tipo fogo, contra Squirtle, do tipo água, é pouco efetivo (0.8x). Mesmo assim, Charmander consegue causar dano aos poucos e reduzir a vida de Squirtle. Após uma batalha longa, Charmander derrota Squirtle. Squirtle é derrotado, Vulpix, que está no índice 1, entra em campo pelo jogador 1, e Squirtle é registrado na lista de derrotados do jogador 1.

Na última batalha, Vulpix ataca Charmander. O ataque de Vulpix, do tipo fogo, contra Charmander, também do tipo fogo, resulta em uma relação neutra (1.0x). No último golpe, Vulpix derrota Charmander. Charmander é derrotado e o Jogador 2 fica sem Pokémons ativos. Com isso, indj2 avança para 2, que é igual a M, e o loop da batalha se encerra.

Por fim, o programa verifica o estado dos Pokémons ativos. Como pokes_ativosj1 é maior que zero e o jogador 2 não possui mais Pokémons disponíveis, a função imp_resultado declara o vencedor. O Jogador 1 é anunciado como vencedor, pois ainda tem 2 Pokémons ativos, Vulpix e Onix. A função também imprime os Pokémons derrotados e o resumo das batalhas.

Output:
Squirtle venceu Golem 
Charmander venceu Squirtle 
Vulpix venceu Charmander 
Jogador 1 venceu 
Pokemon sobreviventes: 
Vulpix 
Onix 
Pokemon derrotados: 
Squirtle Golem Charmander
