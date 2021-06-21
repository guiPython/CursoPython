### Sintaxe

Antes de qualquer coisa vamos apresentar a sintaxe das funções lambda:

1-) Criar uma expressão lambda para verificar paridade de um numero:

```python
fParidade = lambda numero: "PAR" if numero % 2 == 0 else "IMPAR"
```

NOTE QUE: Ao utilizarmos a palavra reservada **lambda** devemos nomea-la atribuindo-a para uma variável no exemplo acima nomeamos-a **fParidade**, logo após a palavra reservada devemos escrever os parâmetros da função, ou seja, nossa função lambda acima é uma função que tem somente um parâmetro chamado **numero**, após dizermos os parâmetros definimos a função depois do caractere **'' : ''** , no exemplo acima utilizamos uma estrutura condicional para definir o retorno, quando utilizamos um condicional em uma expressão **lambda** devemos primeiro escrever o retorno para a condição verdadeira, em seguida a condição com **if** e por fim a palavra reservada **else** e o retorno se falsa.

2-) Criar uma expressão lambda que tenha dois parâmetros **x** e **y** e retorne **x**^**y** :

```python
fPotencia = lambda x,y : x ** y
```

Acima temos uma expressão **lambda** com mais de um parâmetro, teoricamente podemos definir quantos parâmetros quisermos, mas perceba que o intuito desta sintaxe é definir funções simples sem precisar usar uma definição mais verbosa como **def**.

Bom com essa pequena introdução acima vamos reescrever o exercício das matrizes somente com expressões lambda, vamos ver na pratica quando utiliza-las e quando não.

### Quando não utilizar?

1-) Vamos supor que você precisa criar um programa em Python que faça operações básicas com matrizes ambas N x N. Antes de sair escrevendo seu código vamos pensar nas coisas que precisamos fazer para que o algoritmo funcione:

-   Ler Matrizes e armazena-las
-   Escrever o código para as operações (Soma/Subtração)
-   Escrever o código para apresentar o resultado

SHOW ME THE CODE KKK:

```python
LerLinha = lambda : list(map(lambda elemento: int(elemento) ,input().strip().split()))

LerMatriz = lambda qtdLinhas: list(map(lambda matriz: list(map(lambda linha: linha,LerLinha())),range(qtdLinhas)))

SomaMatrizes = lambda m1,m2: list(map(lambda x: list(map(lambda y: m1[x][y] + m2[x][y], range(len(m1[0])))),range(len(m1))))

SubtraiMatrizes = lambda m1,m2: list(map(lambda x: list(map(lambda y: m1[x][y] - m2[x][y], range(len(m1[0])))),range(len(m1))))

ApresentaMatriz = lambda matriz: [print(*linha,sep=" ") for linha in matriz]

def main():
    qtdLinhas = int(input("Digite o numero de Linhas da Matriz: "))
    print('\nMATRIZ 1:')
    m1 = LerMatriz(qtdLinhas)
    print('\nMATRIZ 2:')
    m2 = LerMatriz(qtdLinhas)

    print('\nSOMA DE MATRIZES:')
    ApresentaMatriz(SomaMatrizes(m1,m2))

    print('\nSUBTRAÇÃO DE MATRIZES:')
    ApresentaMatriz(SubtraiMatrizes(m1,m2))

main()
```

Não se assunte se você não entendeu o código acima, ele é um exemplo de abuso do uso de expressões **lambda**, o primeiro questionamento que você deve fazer ao escrever um código é se ele é legível, olhando para o código acima é muito difícil entender oque cada função faz sem realizar a leitura de seus nomes, outro problema é a composição de expressões **lambda**, assim como a definição de funções dentro de funções é uma pratica ruim a composição de **lambdas** também é, a conclusão é que devemos ter bom senso ao tentar reduzir as linhas de nosso programa, devemos sempre nos preocupar com a **legibilidade** e **simplicidade** da nossa solução, e por fim a documentação vimos que quando utilizamos a palavra reservada **def** podemos usar um comentário com 3 aspas duplas para dar uma noção aos outros programadores sobre o funcionamento do nosso método além disso vimos que podemos explicitar os tipos dos parâmetros e retorno de nossas funções, ambas as operações não são possíveis com a a sintaxe **lambda**.

**_“Qualquer tolo consegue escrever código que um computador entenda. Bons programadores escrevem código que humanos possam entender.”_**

**Martin Fowler**

### Quando utilizar ?

Agora vamos ver casos de uso para **lambda functions** que fazem sentido.

1-) Faça uma função de filtro que receba um array e pegue somente numeros pares:

```python

filtro = lambda numero: True if numero % 2 == 0 else False

''' Vamos aplicar esse filtro '''

pares = filter(filtro,[1,2,3,4])

print(*pares, sep=" ")

```

2-) Faça uma função que dado um valor n retorne o enésimo elemento da sequencia de Fibonacci:

```python

fibonacci = lambda n: 1/(5**0.5) * ( ( (1+5**0.5)/2 )**n - ( (1-5**0.5)/2 )**n )

n = int(input("Insira n: "))

print(fibonacci(n))

```
