# Regressão linear: técnicas avançadas de modelagem

## Introdução

Anotações feitas durante o segundo curso de regressão linear. Tópicos abordados:

- [Transformações de variáveis](./curso-4.md#transformações-de-variáveis)
    - [Aplicação de logaritmo](./curso-4.md#aplicação-de-logaritmo)
- [Regressão linear com StatsModels](./curso-4.md#regressão-linear-com-statsmodels)
    - [Modelos log linear](./curso-4.md#modelos-log-linear)
    - [Criando e treinando o modelo com StatsModels](./curso-4.md#criando-e-treinando-o-modelo-com-statsmodels)
        - [Teste F](./curso-4.md#teste-f)
        - [Teste T](./curso-4.md#teste-t)

## Transformações de variáveis

Quando o conjunto de dados, principalmente a variável dependente não seguir uma distribuição normal e for [assimétrico](./curso-1.md#relação-entre-média-mediana-e-moda) é necessário realizar algumas transformações nessa variável antes da regressão para fazê-la se aproximar de uma distribuição normal.

Essas transformações são necessárias pois testes paramétricos assumem que as amostras foram retiradas de uma população com distribuição de probabilidade conhecida e, em sua maiora, normal.

### Aplicação de logaritmo

Uma forma comum de fazer essa transformação é utilizar ao invés de as variáveis em si, o logaritmo delas, o logaritmo acaba juntando as medidas de valores mais altos tornando-as menos dispersas, isso faz com que a assimetria à direita seja resolvida.

## Regressão linear com StatsModels

O [statsmodels](https://www.statsmodels.org/stable/index.html) é uma biblioteca escrita em python que busca fornecer ao programador diversas classes e funções para estimar modelos estatísticos, além de exploração estatística de dados e condução de testes estatísticos.

### Modelos log linear

Como mencionado na seção de [tranformação](./curso-4.md#aplicação-de-logaritmo) em conjuntos assimétricos é comum utilizar uma transformação logaritmíca. Nesses casos a regressão linear deixa de ser um modelo linear e passa a ser um modelo log linear. Assim, um modelo que poderia ser descrito da forma:

\\[ Y_i = \\beta_1 X_{2i}^{\\beta_2}X_{3i}^{\\beta_3}eU{u_i} \\]

Passa a ser descrito por:

\\[ ln Y_i = ln \\beta_1 + \\beta_2 ln X_{2i} + \\beta_3 ln X_{3i} + u_i\\]

### Criando e treinando o modelo com StatsModels

Para treinar um modelo, a biblioteca statsmodels precisa que seja adicionada uma coluna ao conjunto de dados, esta coluna deve possuir um valor constante igual a 1 e serve para a soma do último termo da equação acima. Considerando que a variável x_treino seja o conjunto de treino (sem a constante) e y_treino seja a variável dependente de treino, o trecho de código abaixo cria e treina um modelo linear do statsmodels.

```python
import statsmodels.api as sm
x_treino = sm.add_constant(x_treino)
modelo = sm.OLS(y_treino, x_treino, hasconst=True).fit()
print(modelo.summary())
```

O método `modelo.summary()` chamado ao final do código acima mostra diversas estatísticas do modelo treinado, inclusive algumas vistas no [curso anterior](./curso-3.md#r2), outros valores importantes que essa função traz serão discutidos abaixo.

#### Teste F
Trata-se de um teste de significância dos parâmetros do modelo em conjunto. Caso a probabilidade do teste f seja maior do 0,05, ou 5% a hipotese nula não pode ser rejeitada, implicando em uma regressão ruim;

#### Teste T
Similar ao teste f, porém para cada variável individualmente. Ele verifica se a variável é relevante, valores de probabilidade menores do que 5% indicam uma relevância, valores maiores do que isso indicam que a hipotese nula não pode ser rejeitada, trata-se de uma variável ruim para a regreessão
