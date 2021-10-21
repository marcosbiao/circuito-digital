# Circuitos combinacionais

Ao combinar as portas lógicas que vimos até aqui, podemos criar muitos tipos diferentes de circuitos que nos ajudam a resolver muitos problemas. Esses circuitos tem a seguinte característica, a saída do circuito em um determinado momento, depende apenas das entradas nesses mesmo momento. Ou seja, esses circuitos não dependem de entradas/saidas que foram obtidas no passado, nem de algum tipo de memória. Esses circuitos são conhecidos como circuitos combinacionais. Isto porque a saída depende apenas das combinações das entradas em um determinado instante.

Veremos nesse capítulo como criar circuitos combinacionais que resolvam algum problema real.

## Projetando Circuitos Lógicos Combinacionais

Existem diversas técninas para projetar um circuito combinacional para resolver um problema específico, algumas técnicas são simples e podemos fazer manualmente, algumas outras são feitas com a ajuda de programas de computador. Algumas possuem princípios básicos necessários para fazer a análise e criação do circuito.

Um dos principíos básicos, é a criação de uma tabela verdade que descreva o resultado do nosso circuito, com isso podemos pensar combinações de portas lógicas que satisfaçam essa tabela. 

Além disso, existe um padrão de circuitos que eventualmente aparece enquanto estamos projetando o nosso circuito, esse padrão é conhecido como "Soma-de-Produtos", veremos esse padrão a seguir, e depois, veremos como projetar um circuito que esteja utilizando esse padrão.

### Soma-de-Produtos

Um circuito está na forma de soma-de-produtos quando todas as entradas do circuito estão conectadas a portas `AND` e o resultado dessas portas estão conectadas em uma porta `OR`, essa porta `OR` pode ter diversas entradas, dependendo apenas da quantidade de portas `AND` que irão se conectar a esse `OR`. Além disso, as entradas do circuito podem ou não estar conectadas a um inversor. Veja um exemplo de circuito que está no formato soma-de-produtos:

![Soma de produtos](images/soma-de-produtos_1.png)

Neste circuito, perceba que todas as saidas dos `AND` estão conectados ao `OR` e todas as entrdas então conectadas ao `AND`, e que também é possivel que uma entrada esteja invertida, como é o caso da entrada `A`. Veja como seria a representação algébrica desse circuito:

![Soma de produtos - Algebrica](images/soma-de-produtos_2.png)

Nesse caso,`R` representa a saída do circuito. Perceba que a representação algébrica do circuito é uma soma de produtos, por esse motivo que esse formato possue o nome de soma-de-produtos

### Exemplo de circuito utilizando a soma de produtos

# Circuito para travar porta em minecraft
