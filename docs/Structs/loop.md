### While

<style>.justify {text-align: justify;text-justify: inter-word;}</style>

<p class="justify">O loop While é uma estrutura de repetição muito simples e funcional, sua vantagem é de suportar varias condições destintas simultaneamente, entretanto este loop precisa de variáveis de controle para que o algoritmo não entre em loop infinito.</p>

```python
y = 3
x = 0

while x < y:
	print(f'X eh menor que Y. {x} < {y}')
	x += 1

```

NOTE QUE: O loop do exemplo acima realiza 2 iterações, ele é um exemplo de um loop **while** com uma condição.

```python
z = 7
y = 5
x = 0
while x < y and y < z:
	print(f'X eh menor que Y e Y eh menor que Z')
	x += 1
	y += 1

```

NOTE QUE: O loop do exemplo acima realiza 2 iterações, ele é um exemplo de um loop **while** com mais de uma condição.

### For Loop

<p class="justify">O loop For é uma estrutura de repetição bem interessante em Python, a sua vantagem em relação ao loop <b>while</b> é que não precisa da declaração de uma variável de controle e sua sintaxe é bastante simples e versátil.</p>

```python
inicio = 1
'O inicio é incluido'
final = 10
'O final não é incluido'
incremento = 5
'O incremento que vamos fazer para chegar no final'

for x in range(inicio,final,incremento):
	print(f'{x} ')
```

<p class="justify">Podemos ver que a estrutura de repetição <b>for</b> é bem simples de entender, ela utiliza uma palavra <b>in</b> reservada e uma função <b>range()</b>, ou seja, semanticamente estamos dizendo <b>"para x no intervalo [ início , final - 1] pulando x de incremento em incremento"</b> faça alguma coisa. No caso do exemplo acima o laço vai iterar duas vezes vamos esquematizar:</p>

```python
for x in range(3,20,2):
	print(f'{x} ')
```

Bom o código acima demonstra a definição de um loop for que só escreve no console os números ímpares até 19, a função **range()** pode gerar um tanto intervalo crescente quanto decrescente, vejamos um exemplo a seguir de um **loop** decrescente que imprime no console somente os números pares do intervalo:

```python
for x in range(20,3,-2):
    print(f'{x}')
```

NOTE QUE: Passamos o parâmetro de incremento como negativo, caso contrario o intervalo não será gerado e não vamos iterar no **loop**.

<p class="justify">Existe ainda uma ultima maneira de utilizar a função <b>range()</b> no loop <b>for</b>, passando somente um <b>int</b> como parâmetro o intervalo gerado vai de 0 até uma unidade anterior ao parâmetro com incremento unitário:</p>

```python
for x in range(3):
    print(f'{x}')
```
