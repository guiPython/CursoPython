As matrizes são estruturas bem versáteis em Python elas funcionam exatamente da mesma maneira que as listas, por definição elas são listas de listas, ou seja teremos dois índices para o acesso de um elemento, o primeiro refere-se a linha e o segundo a coluna que queremos acessar, vamos ver como declarar uma matriz em Python e preenche-la.

1-) Lendo uma matriz:

```python
matriz = []
numLinhas = int(input('Digite o numero de linhas da matriz: '))
for indice in range(numLinhas):
    linha = [int(x) for x in input("Digite os valores da Linha: ").strip().split()]
    matriz[indice] = linha

print(f'O primeiro elemento da primeira linha é {matriz[0][0]}')
```

NOTE QUE: O acesso do elemento como dissemos é feito por dois índices, e ambos iniciam com valor 0, como dito matrizes são listas de listas.

2-) Percorrendo a boa e velha matriz:

```python
matriz = [[1,2,3,4],[5,6,7,8]]
for linha in range(len(matriz)):
    for coluna in range(len(matriz[linha])):
        print(f'O elemento da posição [{linha}][{coluna}] = {matriz[linha][coluna]}')
```

Temos acima um loop aninhado, ou seja, para cada repetição do primeiro loop teremos n repetições, isso funciona para percorrer as matrizes pois note que para cada linhas temos n repetições relativas a quantidade de colunas daquela linha, existe um outra maneira mais tranquila de percorrer sem usar os índices veja:

```python
matriz = [[1,2,3,4],[5,6,7,8]]
for linha in matriz:
    for elemento in linha:
        print(elemento)
```

##### Exercícios:

1-) Percorrer somente a coluna desejada pelo usuário:

```python
coluna = int(input('Digite o numero da coluna: ')) - 1
matriz = [[1,2,3,4],[5,6,7,8]]
for linha in matriz:
    print(f'{matriz.index(linha) + 1} elemento da {coluna} coluna é {linha[coluna]}')
```

NOTE QUE: Houve um decremento unitário no valor da coluna justamente pelo índice iniciar em 0, ou seja, a segunda coluna é acessada pelo valor de índice 1.

2-) Percorrer somente a diagonal principal:

```python
matriz = [[1,2],[3,4]]
for linha in matriz:
    index = matriz.index(linha)
    print(f'{index + 1} elemento da diagonal principal é {linha[index]}')
```

3-) Percorrer somente a diagonal secundaria:

```python
matriz = [[1,2],[3,4]]
for linha in matriz:
    index = matriz.index(linha)
    linha = linha[::-1]
    print(f'{index + 1} elemento da diagonal secundaria é {linha[index]}')
```

Ou ainda podemos gerar uma outra solução:

```python
matriz = [[1,2],[3,4]]
for linha in matriz:
    index = matriz.index(linha)
    print(f'{index + 1} elemento da diagonal secundaria é {linha[len(linha)-1]}')
```

Bom não tem muito segredo em trabalhar com matrizes uma vez que estamos trabalhando com as listas ainda, vamos ver uma situação mais prática sobre as matrizes simulando uma base de dados, claramente vamos cair em vetores com tipos de dados diferentes que são uma má pratica, entretanto para simular um banco de dados por hora basta, veremos mais tarde como resolver isso com outro tipo de dados.

Imagine que você carrega em memória uma tabela de um banco de dados relativa as vendas e você precisa extrair alguns dados dessa tabela.

Por simplicidade uma venda tem as seguintes características:

-   Nome do Cliente;
-   Nome do Vendedor;
-   Nome do produto;
-   Quantidade do produto;
-   Valor do produto;

Queremos saber qual o cliente que mais compra, qual o produto que mais vende e qual o vendedor com a maior média no valor da venda.

```python
tabelaVendas = [['Cliente','Vendedor','Produto','Qtd','Valor']]
tabelaVendas[1] = ['Valter','Alex','Papel-A4',576,25.90]
tabelaVendas[2] = ['Valter','Anderson','Borracha',120,2.95]
tabelaVendas[3] = ['Thales','Alex','Papel-A4',180,25.90]
tabelaVendas[3] = ['Thales','Anderson','Borracha',590,2.95]
```

Percebam que acima definimos uma tabela com cabeçalho, vamos utilizar essa base de dados para resolver esse problema com matrizes.

```python
'Cliente que mais compra'
clientes = [venda[0] if venda[0] not in clientes for venda in tabelaVendas[1::]]
info = []
for cliente in clientes:
    totalVendas = 0
    for venda in tabelaVendas:
        if(venda[0] == cliente):
            totalVendas += venda[4] * venda[3]
    info.append([cliente,totalVendas])
```

NOTE QUE: Semanticamente esse código não fica legível temos os chamados números mágicos, eles são os índices de nossas colunas, por exemplo sem olhar o cabeçalho seria praticamente impossível sabermos oque a primeira coluna da matriz significa, esse problema será resolvido com nossa próxima estrutura de dados, outro ponto é sobre nossa lista de clientes existe uma estrutura de dados mais adequada para armazenar os clientes que veremos depois chamada **set**.
