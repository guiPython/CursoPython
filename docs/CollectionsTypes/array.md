<div>
<p>Agora vamos apresentar a estrutura de dados chamada lista, este tipo de estrutura permite armazenar valor de um mesmo tipo de maneira ordenada, no geral coleções de dados são estruturas muito tranquilas de trabalhar em Python, a linguagem implementa muitas funções nativas e tem uma sintaxe bem versátil para trabalhar com listas. Em linguagens de tipo estático a definição de array é diferente da de lista, um array aloca um espaço de memória contigo e fixo isso significa que uma vez declarado um array nestas linguagens ele vai ocupar aquele espaço na memória até o final da execução do programa ou até um <b>"coletor de lixo"</b> ser acionado, enquanto as listas são estruturas dinâmicas no sentido de alocação de memória, podemos adicionar e remover valores dela sem problemas, em Python você não vai ter essa diferenciação, portanto vamos considerar por praticidade que arrays e listas são as mesmas entidades.</p>

<p>NOTA: Python permite que você tenha uma lista com itens de tipo diferentes, mas é importante dizer que você <b>deve</b> sempre querer trabalhar com coleções de somente um tipo de dados, isso evita muitos <b>bugs</b> no seu código e é uma boa prática em programação, se você esta ciente disso e prefere utilizar essa <b>"vantagem"</b> da linguagem use-a com cuidado.</p>
</div>

### Declaração de uma Lista:

```python
lista = []
lista = [1,2,3]
lista = ['1', 'a', 'b']
```

NOTE QUE: As declarações feitas acima seguem uma restrição imposta em nossa definição, é uma coleção de elementos ordenados e do mesmo tipo.

Para entendermos melhor as lista é importante saber que elas são estruturas indexadas, ou seja, cada elemento da lista tem uma posição especifica nela que sempre começa no valor 0 e termina no valor n -1 , onde n é o numero de elementos que temos na lista.

### Acesso aos elementos:

```python
lista = [1,2,3,4]
print(lista[0]) 'Escreve no console o valor 1'
print(lista[1]) 'Escreve no console o valor 2'

print(lista[209]) 'Retorna um erro kkkkk'
```

NOTE QUE: O erro ao escrever o item de posição 209 no console já era esperado pois como dito anteriormente só temos acesso ao índice de valor n-1, onde n é o numero de itens da lista.

### Adição Unitária e de Coleções:

```python
lista = []
lista.append(1) 'Adiciona na posição 0 da lista o valor 1'
lista.append(2) 'Adiciona na posição 1 da lista o valor 2'

lista.insert(3,2) 'Adiciona na posição 2 da lista o valor 3'

lista[3] = 4 'Adiciona na posição 3 da lista o valor 4'

lista.extend([5,6])
'Adiciona na posição 4 e 5 respectivamente os valores 5,6'

lista_2 = [7,8,9,10]

lista += lista_2
'Concatena a lista com a lista_2, mesmo efeito de extend'

lista_2 *= 2
'Extende a lista com a própria lista, ou seja, lista_2 = [7,8,9,10,7,8,9,10]''
```

### Remoção Unitária e de Coleções:

```python
lista = [1,2,3,4,5]

ultimo = lista.pop() 'Remove e retorna o ultimo item da lista, ou seja, lista = [1,2,3,4] e ultimo = 5'

lista.remove(2) 'Remove a primeira ocorrencia do valor 2 da lista caso ele exista'
```

### Propriedades e outras funções de Listas:

```python
lista = ["123","456"]
comprimentoDaLista = len(lista)

lista.reverse()
'O ultimos elementos da lista se tornam seus primeiros, ou seja, lista = ["456", "123"]'

lista.sort()
'Ordena os elementos da lista de acordo com o tipo dos elementos, strings alfabeticamente, { int, float } crescente'

lista.sort(reverse=True)
'Ordena os elementos da lista em ordem decrescente de acordo com a implementação do tipo dos elementos'

```

### Percorrendo Listas:

Bom como já passamos pelos Loops vamos ver como utiliza-los para percorrer nossas listas, podemos também realizar operações enquanto percorremos elas, veremos os exemplos abaixo:

```python
lista = [1,2,3,4,5]
for indice in range(len(lista)):
    print(lista[indice])

```

Okay o algoritmo acima é bem simples, ele só escreve no console os elementos da nossa lista, vamos ver exemplos um pouco mais complexos, aplicando filtros, e até mesmo gerando listas de maneira mais simples.

### Geração e Filtragem de Listas:

1-) Gerando uma Lista de 0 até n - 1 sem restrição:

```python
[ x for x in range(0,int(input("Digite o limite da lista: ")))]
```

2-) Gerando uma lista de 0 até n -1 somente com os valores pares:

```python
[ x for x in range(0,int(input("Digite o limite da lista: "))) if x % 2 == 0]
```

3-) Gerando uma lista de 0 até n-1 pegando os valores ímpares e elevando-os ao quadrado e os elementos pares multiplicados pelo seu sucessor:

```python
[x**2 if x % 2 != 0 else x * (x+1) for x in range(0, int(input("Digite o limite da lista: ")))]
```

<div class = "justify">
<p>Os exemplos acima podem sofrer modificações de acordo com suas necessidades, essa sintaxe é muito poderosa e basicamente permite quaisquer operações com os dados durante a geração da lista, aliada com as funções temos uma ferramenta muito poderosa, mas vamos com calma.</p>

<p>Bom vimos nos 3 exemplos acima que gerar listas em Python é super simples, entretanto se já tivermos nossa base de dados armazenada em uma lista em Python como podemos apenas filtra-lá de maneira simples, nos exemplos abaixo vamos simular isso.</p>
</div>
1-) Temos uma lista de frutas e queremos filtrar para pegar apenas frutas que o nome comece com uma determinada letra:

```python
frutas = ["maçã","pera","morango","uva","abacate","laranja","mamão"]

letra = input("Digite a letra: ")

'list comprehension'
frutasFiltrada = [fruta for fruta in frutas if fruta[0] == letra]
```
