### Numéricos

Semelhante à outras linguagens, Python apresenta tipo inteiro e de ponto flutuante:

```python
x = 8
print (x, type(x))
```

#### Operações

```python
print (x + 3)   # Adição;
print (x - 3)   # Subtração;
print (x * 3)   # Multiplicação;
print (x ** 3)  # Exponenciação;
```

```python
x += 1
print (x)
x *= 2
print (x)
```

```python
y = x / 2
print (type(y))
print (y, y + 1, y * 2, y ** 2)
```

Veja que Python não tem operadores de incremento e decremento unitário (x++)

> Exercícios

    1-) Programe as formulas de juros simples e composto.
        *Taxa de 1% ao ano , periodo de 2 anos e capital de $1000.

```python

    '''Juros Simples'''
    Montante = 1000 * (1 + 1/100 * 2)

    '''Juros Compostos'''
    Montante = 1000 * (1 + 1/100)**2

```

### Booleanos

### Strings
