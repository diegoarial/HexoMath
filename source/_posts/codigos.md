---
title: Códigos
---

Estes foram os códigos utilizados para a resolução das atividades deste bimestre, eles foram programados na linguagem Python.

Método de Newton:

``` bash
def metodoNewton():
    quant_pontos = int(input('Quantidade de pontos: '))
    pontos, f_pontos = [], []
    tabela = []

    for i in range(quant_pontos):
        ponto = float(input('x%d = ' % i))
        f_ponto = float(input('f(x%d) = ' % i))
        pontos.append(ponto)
        f_pontos.append(f_ponto)
    tabela.append(f_pontos)

    passo = 1
    for n in range(quant_pontos - 1):
        ordem = []
        for m in range(len(tabela[n]) - 1):
            dif_dividida = (tabela[n][m + 1] -
                            tabela[n][m]) / (pontos[m + passo] - pontos[m])
            ordem.append(dif_dividida)
        tabela.append(ordem)
        passo += 1

    for k in range(len(tabela)):
        print('Ordem %d:' % k, tabela[k])
    print()

    x = float(input('Ponto x a ser estimado: '))
    resultado = tabela[0][0]
    produto = 1.0
    for i in range(1, quant_pontos):
        produto *= (x - pontos[i - 1])
        resultado += tabela[i][0] * produto

    print(f'Valor estimado de f({x}) é: {resultado}')


metodoNewton()
```

Método de Lagrange:

``` bash
def metodoLagrange():
  quant_pontos = int(input('Quantidade de pontos: '))
  pontos, f_pontos = [], []

  for i in range(quant_pontos):
      ponto = float(input('x%d = ' % i))
      f_ponto = float(input('f(x%d) = ' % i))
      pontos.append(ponto)
      f_pontos.append(f_ponto)

  x = float(input('Ponto x a ser estimado: '))
  coeficientes = []

  for indice in range(quant_pontos):
      L = 1
      for j in range(quant_pontos):
          if indice != j:
              L *= (x - pontos[j]) / (pontos[indice] - pontos[j])
      coeficientes.append(L)

  pn = 0
  for i in range(quant_pontos):
      pn += f_pontos[i] * coeficientes[i]

  print(f'Valor estimado de f({x}) é: {pn}')

metodoLagrange()
```