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

Primeiramente, precisamos detalhar todo os processos condizentes com a porta. O processo será o seguinte: Existirá uma sequência de 4 alavancas (entradas 1, 2, 3, e 4), uma placa de pressão (entrada 5), e uma a porta (saída). Ao pressionar a placa, a porta abrirá somente se: a primeira alavanca estiver ligada; a segunda estiver desligada; a terceira estiver ligada, e a quarta desligada. No caso, a senha seria 1010, onde cada algorismo representa a sua respectiva alavanca da esquerda para a direita.

Traduzindo para o contexto de circuitos digitais, isso significa que a saída (porta) será positiva (aberta) quando as entradas 1, 3 e 5 forem positivas e as entradas 2 e 4 forem negativas. A tabela verdade desse circuito seria:

Linha | Entrada 1 | Entradas 2 | Entrada 3 | Entrada 4 | Entrada 5 | Saida
----------|----------|------------|-----------|-----------|-----------|------
1 | 0 | 0 | 0 | 0 | 0 | 0
2 | 0 | 0 | 0 | 0 | 1 | 0
3 | 0 | 0 | 0 | 1 | 0 | 0
4 | 0 | 0 | 0 | 1 | 1 | 0
5 | 0 | 0 | 1 | 0 | 0 | 0
6 | 0 | 0 | 1 | 0 | 1 | 0 
7 | 0 | 0 | 1 | 1 | 0 | 0
8 | 0 | 0 | 1 | 1 | 1 | 0
9 | 0 | 1 | 0 | 0 | 0 | 0
10 | 0 | 1 | 0 | 0 | 1 | 0
11 | 0 | 1 | 0 | 1 | 0 | 0
12 | 0 | 1 | 0 | 1 | 1 | 0
13 | 0 | 1 | 1 | 0 | 0 | 0
14 | 0 | 1 | 1 | 0 | 1 | 0
15 | 0 | 1 | 1 | 1 | 0 | 0
16 | 0 | 1 | 1 | 1 | 1 | 0
17 | 1 | 0 | 0 | 0 | 0 | 0
18 | 1 | 0 | 0 | 0 | 1 | 0
19 | 1 | 0 | 0 | 1 | 0 | 0
20 | 1 | 0 | 0 | 1 | 1 | 0
21 | 1 | 0 | 1 | 0 | 0 | 0
22 | 1 | 0 | 1 | 0 | 1 | 1
23 | 1 | 0 | 1 | 1 | 0 | 0
24 | 1 | 0 | 1 | 1 | 1 | 0
25 | 1 | 1 | 0 | 0 | 0 | 0
26 | 1 | 1 | 0 | 0 | 1 | 0
27 | 1 | 1 | 0 | 1 | 0 | 0
28 | 1 | 1 | 0 | 1 | 1 | 0
29 | 1 | 1 | 1 | 0 | 0 | 0
30 | 1 | 1 | 1 | 0 | 1 | 0
31 | 1 | 1 | 1 | 1 | 0 | 0
32 | 1 | 1 | 1 | 1 | 1 | 0

Como podemos perceber, apenas as entradas da linha 22 fará com que a saída seja positiva. A expressão booleana da linha 22 é A

![Expressão Booleana](images/expr_bool_project.jpeg)


