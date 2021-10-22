# Descrição do Projeto em Minecraft

O projeto desse artigo consiste em automatizar um processo simples do contidiano dos jogadores de Minecraft: entrar e sair de uma casa com a porta trancada por senha. Se fossemos realizar esse processo manualmente no Minecraft, o fluxo de procedimentos seria:

- Destrancar a porta, atráves de uma sequência de alavancas específicas;
- Abrir a porta, mudando diretamente seu estado de "Fechado" para "Aberto;
- Entrar na casa;
- Fechar a porta, mundando diretamente seu estado de "Aberto" para "Fechado";
- Verificar se está de noite ou de dia, atráves da ausência ou presença de iluminação provida do sol;
- Se estiver de noite, acender a lâmpada manualmente através de uma alavanca.

Para sair de uma casa no Minecraft, o processo seria o contrário:

- Se lâmpada estiver acesa, apaga-la atráves de uma alavanca;
- Abrir a porta, mudando diretamente seu estado de "Fechado" para "Aberto;
- Sair da casa;
- Fechar a porta, mudando diretamente seu estado de "Aberto" para "Fechado";
- Trancar a porta.

Todos esse processos podem ser automatizados atráves do circuitos de redstone, que podem ser formulados atráves dos circuitos digitais. A seguir, veremos todos os componentes lógicos para formular o circuito.

# Descrição dos Componentes Lógicos

Como foi visto, para formulação do circuito digital, primeiramente precisamos pensar no problema em que queremos resolver. Para melhorar o entendimento do circuito, dividiremo-os em 2 circuitos menores: o que diz respeito a porta, e o da lâmpada. Começaremos com circuito de destrancar e abrir a porta a seguir.

## Circuito da Porta

Primeiramente, precisamos detalhar todo os processos condizentes com a porta. O processo será o seguinte: Existirá uma sequência de 4 alavancas (entradas 1, 2, 3, e 4), uma placa de pressão (entrada P), e uma a porta (saída S). Ao pressionar a placa, a porta abrirá somente se: a primeira alavanca estiver ligada; a segunda estiver desligada; a terceira estiver ligada, e a quarta desligada. No caso, a senha seria 1010, onde cada algorismo representa a sua respectiva alavanca da esquerda para a direita.

Traduzindo para o contexto de circuitos digitais, isso significa que o circuito terá dois AND: o primeiro com as entradas E1, E2, E3, E4 (alavancas) e a saída T; e o segundo terá, como entradas, a saída T e a P (placa), e, como saída, o S (porta). A tabela verdade desse circuito seria:

##### Primeiro `AND`
Linha | Entrada 1 | Entradas 2 | Entrada 3 | Entrada 4 | Saída T
----------|----------|------------|-----------|-----------|------
1 | 0 | 0 | 0 | 0 | 0
2 | 0 | 0 | 0 | 1 | 0
3 | 0 | 0 | 1 | 0 | 0
4 | 0 | 0 | 1 | 1 | 0
5 | 0 | 1 | 0 | 0 | 0
6 | 0 | 1 | 0 | 1 | 0
7 | 0 | 1 | 1 | 0 | 0
8 | 0 | 1 | 1 | 1 | 0
9 | 1 | 0 | 0 | 0 | 0 
10 | 1 | 0 | 0 | 1 | 0 
11 | 1 | 0 | 1 | 0 | 1
12 | 1 | 0 | 1 | 1 | 0
13 | 1 | 1 | 0 | 0 | 0
14 | 1 | 1 | 0 | 1 | 0
15 | 1 | 1 | 1 | 0 | 0
16 | 1 | 1 | 1 | 1 | 0

Como podemos perceber, apenas as entradas da linha 22 fará com que a saída seja positiva. A expressão booleana da linha 22 é:

![Expressão Booleana](images/expr_bool_project.jpeg)

Para montar o circuito, basta apenas levar em consideração os 0 da linha 22, que deve ficar com as entradas com um inversor (`NOT`). Quanto ao segundo `AND`, ele terá a saída T e a entrada P como entradas. Isso significa que, ao pisar na placa (entrada fica positiva), a porta só irá abrir se a saída T for positiva, ou seja, so irá abrir se a senha for colocada corretamente. Portanto, o circuito referente à porta ficará da seguinte forma:

![Circuito Senha](images/circuito_senha.jpeg)

Agora que temos o circuito, basta apenas passarmos para circuito de Redstone do Minecraft. O circuito de Redstone da porta ficará da seguinte forma:

![Circuito Redstone Senha](images/circuito_redstone_senha.gif)

## Circuito da lâmpada

Agora veremos a segunda parte do circuito: o circuito da lÂmpada. O processo de acender a lâmpada é o seguinte: quando o jogador entrar na casa, vai depara-se com uma outra placa de pressão (entrada Y) que será responsável por acender a lâmpada (saída L), que por sua vez so irá acender se, no momento em que o jogador pisar na placa, estiver de noite. Para isso, será necessário uma entrada que esteja em sicronia com o período do dia (entrada N), ou seja, durante o dia essa entrada precisa estar em 0, e mudar para 1 caso esteja de noite. No Minecraft, tal entrada seria a ferramenta Painel Solar no modo Noturno.

Além disso, a lâmpada deve apagar, caso o jogador pise novamente na placa para sair da casa, o que implica que precisaremos fazer o uso de um Flip-Flop D com o ~Q sendo a entrada D e a placa de pressão como o clock, nos permitindo alternar o estado da saída L (lâmpada) toda vez que pisarmos na placa (ver imagem abaixo).

![FF D](images/ff_d.jpeg)

Dito isso, a lâmpada so irá acender caso a placa (Y) for 1, e a entrada condicional (N) for 1, ou seja, é preciso adicionar uma porta `AND` que o L (lâmpada) como saída. O circuito da lâmpada seria:

![Circuito da Lâmpada](images/circ_lamp.jpeg)

No minecraft, o circuito de Redstone correspondente seria:

![Circuito da Lâmpada Redstone](images/circ_lamp_reds.gif)

# Circuito de Redstone Completo

Com o circuito da porta e o da lâmpada já formulados, precisamos efetuar a integração dos circuitos. Para isso precisamos traçar o que os dois circuitos tem em comum. Na descrição do projeto, a placa de pressão interna à casa, além de acender a lâmpada, também abre a porta. Como ambas as placas abrem a porta, isso significa que qualquer uma das duas que forem pressionadas e estiverem de acordo com os seus critérios, a porta deverá abrir.

No contexto de circuitos, precisaremos utilizar a porta lógica `OR` que tem como entradas a saída do circuito da porta (saída P) e a placa de pressão interna (entrada Y). Então, o circuito completo do projeto ficará da seguinte forma:

![Circuito Projeto](images/circ_projeto_completo.jpeg)

No minecraft, o circuito de Redstone correspondende é:

![Circuito Projeto Redstone](images/circ_reds_projeto_completo.gif) 

# Projeto Completo no Minecraft

A seguir, iremos disponibilizar o link para download do Projeto funcionando dentro do Minecraft. Para você utilizar o mundo é necessário baixar o arquivo `.zip`, extrair o arquivo zipado. Após isso, com o Minecraft já instalado, copie a pasta extraída e cole na pasta `.minecraft` no seu computador. Pronto, entre no jogo e estará o mundo salvo para você utilizar!
