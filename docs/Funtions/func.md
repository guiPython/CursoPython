As funções são como pequenas abstrações mais genéricas no seu código, i.e podemos definir partes menores de nosso algoritmo nomeá-las e parametriza-las, se você já utilizou alguma biblioteca em Python deve ter percebido essa sintaxe **len(array) **, a função **len() ** é nativa da linguagem e retorna o comprimento de uma string, array etc.

As funções nativas de uma linguagem são funções que não precisam ser definidas pelo programador como a própria função **len()** , entretanto o programador pode definir suas funções, veremos isso nos exemplos a seguir, antes disso é importante entender o porque utilizar funções e como elas podem te ajudar a estruturar melhor seu código e evitar a repetição dele.

1-) Vamos supor que você precisa criar um programa em Python que faça operações básicas com matrizes ambas N x N. Antes de sair escrevendo seu código vamos pensar nas coisas que precisamos fazer para que o algoritmo funcione:

-   Ler Matrizes e armazena-las
-   Escrever o código para as operações (Soma/Subtração)
-   Escrever o código para apresentar o resultado

### Código sem utilizar funções

```python
numeroDeLinhas = int(input('Insira o numero de Linhas das Matrizes: '))
matriz1 = []
matriz2 = []
resultado = []
aux = 0

'Leitura Da Matriz e Armazenamento'
while aux < 2:
    print(f'\nInsira a Matriz {aux + 1}:')
    for i in range(numeroDeLinhas):
        linha = [int(x) for x in input().strip().split()]
        if aux == 0:
            matriz1.append(linha)
        elif aux == 1:
            matriz2.append(linha)
    aux += 1

'Desvio de Fluxo e Definições de Operações'
operacao = int(input('\n1- Somar || 2-Subtrair: '))

'Definição da Soma'
if operacao == 1:
    resultado = [[matriz1[i][j] + matriz2[i][j]
                 for j in range(len(matriz1[i]))] for i in range(len(matriz1))]

'Definição da Subtração'
elif operacao == 2:
    resultado = [[matriz1[i][j] - matriz2[i][j]
                 for j in range(len(matriz1[i]))] for i in range(len(matriz1))]

'Apresentação do Resultado'
print('\nRESULTADO:')
for linha in resultado:
    print(*linha,sep=' ')


```

O programa acima foi construído sem a utilização das funções, independente se o algoritmo funciona devemos ter cuidado ao programar nossos algoritmos, o exemplo acima não permite o reuso do código, a lógica esta espalhada e não sabemos ao certo oque cada parte do código faz sem que seja realizado um teste de mesa ou a leitura do código.

DICA: Se você precisa comentar o seu código para entender o seu funcionamento considere reescrever ou revisar o mesmo.

Algumas mudanças podem deixar o código mais legível, nomes de variáveis e definição de funções são uma delas, vamos escrever o algoritmo utilizando as funções.

Primeiramente devemos entender o uso da palavra reservada **def**, quando utilizamos esta palavra em nosso código estamos dizendo ao interpretador que vamos escrever uma função, logo após a palavra **def**, nomeamos nossa função e parametrizamos ela, portanto **def main()** é a definição de nossa função principal, é importante entender que a função **main** é especial no nosso código, ela que comandara a execução do nosso programa como veremos no exemplo abaixo:

### Sintaxe Das Funções

```python
def main():
	print('Ola mundo')
main()
```

NOTE QUE: O código acima define a função main e chama a mesma para ser executada.

```python
def ParOuImpar(numero: int) -> str:
    if(numero % 2 == 0): return "PAR"
    return "IMPAR"

def main():
    numero = int(input("Digite um numero para indentificar sua Paridade: "))
    print(f'{numero} é {ParOuImpar(numero)}')
main()

```

NOTE QUE: **ParOuImpar ** é uma função que tem um parâmetro do tipo inteiro e retorna uma string.

```python
def ParOuImpar(numero):
    if(numero % 2 == 0) return "PAR"
	return "IMPAR"

def main():
    numero = int(input("Digite um numero para indentificar sua Paridade: "))
    print(f'{numero} é {ParOuImpar(numero)}')
main()
```

Acima podemos ver que a sintaxe usada na definição de **ParOuImpar** é diferente, entretanto semanticamente não temos diferenças, devemos levar em conta que escrever código é menos trabalhoso que ler, compreender e explicar, logo utilizar a sintaxe mais verbosa dizendo o tipo dos parâmetros e de retorno é interessante pois serve como "documentação" para outros programadores que utilizaram seu código, outras linguagens de programação obrigam a especificação dos tipos então considere utilizar a especificação de tipo se pretende programar em outras linguagens.

### Código utilizando funções

```python

'Nesta função estamos utilizando a sintaxe mais verbosa onde dizemos qual o tipo de retorno e do parametro'

def LerMatriz(qtdLinhas: int) -> list(list(int)):
   """Le um Matriz de Inteiros"""
   matriz = []
   print("Insira as Linhas da Matriz:")
   for i in range(qtdLinhas):
       linha = [int(x) for x in input().strip().split()]
       matriz.append(linha)
   return matriz

def SomaMatrizes(m1: list(list(int)), m2: list(list(int))) -> list(list(int)):
   """Soma duas Matrizes de Inteiros"""
   return [[m1[i][j] + m2[i][j] for j in range(len(m1[0]))] for i in range(len(m1))]

'Nesta função estamos utilizando a sintaxe menos verbosa onde não especificamos os tipos dos parametros e retorno'

def SubtracaoMatrizes(m1,m2):
   """Subtrai duas Matrizes de Inteiros"""
   return [[m1[i][j] - m2[i][j] for j in range(len(m1[0]))] for i in range(len(m1))]

def ApresentaMatriz(m: list(list(int))) -> None:
   """Apresenta uma Matriz de Inteiros"""
   for linha in m: print(*linha,sep=" ")

'Como dito anteriormente temos a função main que controla a execução do programa'

def main():
   qtdLinhas = int(input("Digite o numero de linhas das Matrizes: "))
   print('\nMATRIZ 1:')
   m1 = LerMatriz(qtdLinhas)
   print('\nMATRIZ 2:')
   m2 = LerMatriz(qtdLinhas)

   print('\nSOMA DE MATRIZES:')
   ApresentaMatriz(SomaMatrizes(m1,m2))

'Assim chamamos uma função main'
main()

```

NOTE QUE: Escrevemos comentários com 3 aspas duplas abaixo das definições, isso permite que programadores que vão utilizar nosso métodos leiam e compreendam seu funcionamento, além disso se você for um programador legal e explicitar os tipos de parâmetros e retorno essas informações também aparecem nessa pequena documentação, mas atenção essa documentação deve ser sempre sucinta e objetiva.
