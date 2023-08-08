# Estatística com python: probabilidade e amostragem
 
## Introdução

 Anotações feitas durante o curso de análise estatística utilizando linguagem python. Tópicos abordados:

- [Distribuição binomial](./curso-2.md#distribuição-binomial)
    - [Experimento binomial](./curso-2.md#experimento-binomial)
    - [Medidas importantes](./curso-2.md#medidas-importantes)
- [Distribuição de Poisson](./curso-2.md#distribuição-de-poisson)
    - [Experimento Poisson](./curso-2.md#experimento-binomial)
    - [Medidas importantes](./curso-2.md#medidas-importantes-1)
- [Distribuição normal](./curso-2.md#distribuição-normal)
- [Técnicas de amostragem](./curso-2.md#técnicas-de-amostragem)
    - [População](./curso-2.md#população)
    - [Amostra](./curso-2.md#amostra)
- [Nível e intervalo de confiança](./curso-2.md#nível-e-intervalo-de-confiaça)
    - [Teorema do limite central](./curso-2.md#teorema-do-limite-central)
    - [Nível de confiança e significância](./curso-2.md#nível-de-confiaça-e-significância)
    - [Erro inferêncial](./curso-2.md#erro-inferencial)
    - [Intervalo de confiança](./curso-2.md#intervalo-de-confiança)
- [Calculando o tamanho da amostra](./curso-2.md#calculando-o-tamanho-da-amostra)
    - [População infinita](./curso-2.md#população-infinita)
    - [População finita](./curso-2.md#população-finita)

## Distribuição binomial

Uma distribuição binomial é caracterizada por eventos com duas classificações, mutuamente excludentes e que formam todo o espaço amostral. Um exemplo disso é o lançamento de uma moeda. Normalmente essa distribuição é utilizada quando se envolve o conceito de __sucesso__ ou __fracasso__.

A equação abaixo mostra a [função massa de probabilidade](https://pt.wikipedia.org/wiki/Fun%C3%A7%C3%A3o_massa_de_probabilidade) dessa distribuição, sendo \\( n \\) o número de eventos estudados, \\( k \\) o número de sucessos \\( p \\) a probabilidade de sucesso e \\(  q = (1 - p)\\) a probabilidade de fracasso.

\\[ P(k) = \binom{n}{k} p^kq^{n-k} \\]

### Experimento binomial

Um experimento é binomial quando possuí as características listadas abaixo:

- Realização de \\( n \\) ensaios __identicos__;
- Os ensaios são __independentes__;
- Somente dois resultados são possíveis;
- A probabilidade dos eventos não se modificam de ensaio para ensaio

### Medidas importantes

\\[  \\mu = n \times p\\]

\\[  \\sigma = \sqrt{n \times p \times q}\\]

## Distribuição de Poisson

A distribuição de Poisson é utilizada para medir o número de ocorrências de um evento em um intervalo fixo de tempo dado uma média de ocorrências por unidade de tempo e independente de quando ocorreu o último evento. Essa distribuição é definida matematicamente pela fórmula abaixo sendo \\( k \\) o número de eventos no intervalo desejado e \\( \\lambda \\) é o número esperado de ocorrências num intervalo de tempo, por exemplo, se um evento ocorre a cada 5 minutos e queremos o número de eventos em 20 minutos, utilizamos \\( \\lambda = \frac{20}{5} = 4 \\).

\\[  P(k) = \dfrac{e^{-\\mu}\\mu^k}{k!}\\]

### Experimento Poisson

Um experimento é de Poisson quando possuí as características listadas abaixo:

- A probabilidade de ocorrência é a mesma em todo o intervalo de tempo observado;
- O número de ocorrências em determinado intervalo é independente do número de ocorrênciasem outros intervalos;
- A probabilidade de uma ocorrência é a mesma em intervalos de igual comprimento

### Medidas importantes

\\[ \\mu = \\lambda \\]

\\[ \\sigma = \sqrt{\\mu} \\]

## Distribuição normal

A distribuição normal é a mais importante de todas. Ela é uma distribuição de uma variável aleatória continua e apresenta um formato de sino sendo simétrica em relação à sua média.

Características:

- É simétrica em torno da média;
- A área soba a curva corresponde à 1 ou 100%;
- As medidas de tendência central (média, moda e mediana) apresentam o mesmo valor;
- Os extremos da curva tendem ao infinito em ambas as direções, jamais tocando o eixo \\( x \\);
- O desvio padrão define o achatamento e largura da distribuição;
- A distribuição é definida pela média e desvio padrão
- A probabilidade é sepre igual à área sob a curva delimitada pelos limites inferior e superios.

\\[ f(s) = \dfrac{1}{\sqrt{2 \\pi \\sigma}} e^{\frac{1}{2}\left( \frac{x - \\mu}{\\sigma}\right)^2}\\]

\\[ P(L_i < z < L_S>) = \int_{L_i}{L_s} \dfrac{1}{\sqrt{2 \\pi \\sigma}} e^{\frac{1}{2}\left( \frac{x - \\mu}{\\sigma}\right)^2}dx\\]

Devido à dificuldade de se resolver a integral da equação acima, é comum utilizar tabelas padronizadas para encontrar as probabilidades. Para utilizar essa tabela é necessário transformar a variável estudada em uma variável padronizada \\( Z \\):

\\[ Z = \dfrac{x - \\mu}{\\sigma}\\]

Isso faz com que a média da variável se torne nula e o seu desvio padrão se torne 1.

## Técnicas de amostragem

### População

Uma população é o conjunto de __todos__ os elementos de interesse de um estudo. Elas são divididas em duas categorias:

- Populações finitas: permitem a contagem de seus elementos;
- Populações infinitas: não permitem a contagem de seus elementos

### Amostra

Uma amostra é um conjunto __representativo__ de uma população, ou seja é um subconjunto de uma população.


## Nível e intervalo de confiaça

### Teorema do limite central

Trata-se de um dos mais importantes teoremas da estatística. Ele afirma que, conforme o tamanho da amostra é aumentado a distribuição das médias amostrais se aproxima de uma distribuição com média igual à média da população e desvio padrão igual ao da variável original dividido pela raiz quadrada do tamanho da amostra. 

\\[ \\mu_{\overline{x}} = \\mu \\]
\\[ \\sigma_{\overline{x}} = \frac{\\sigma}{\sqrt{n}} \\]

### Nível de confiaça e significância

O nível de confiança \\( z = ( 1 - \\alpha )\\) é a probabilidade de acerto de uma dada estimativa. De forma complementar, o nível de significância \\( \\alpha \\) é a probabilidade de erro da estimativa.

O nível de confiança representa a confiabilidade de um resultado estar dentro de um determinado intervalo. É comum em uma pesquisa fixar esse valor à 95%, nesse caso assume-se que há uma probabilidade de 95% dos resultados da pesquisa representarem bem a realidade, ou seja, estarem corretos.

Para se obter o nível de confiança de uma estimativa deve se calcular a área sob a curva normal como mostra a figura abaixo.

![Figura representativa do nível de confiança e nível de significância. Trata-se de um gráfico contendo uma distribuição normal com uma área centrada na origem e limitada por -Z e Z no eixo x, esta área está denominada nível de confiânça e marcada como 1 - alfa. As áreas não hachuradas estão denominadas como nível de significância e cada uma delas possuem a marcação de alfa dividido por 2.](./assets/curso-2/confianca-significancia.png)

### Erro inferencial

Este erro é definido como a multiplicação do desvio padrão das médias amostrais pelo nível de confiança de um dado processo.

\\[  e  = z \frac{\\sigma}{\sqrt{n}}\\]


### Intervalo de confiança

Para calcular um intervalo de confiança é necessário primeiramente definir um nível de confiança. Como dito anteriormente, usualmente o nível de confiança utilizado é de 95%, desta forma o intervalo de confiança é para um nível de confiança de 95%, ou seja, a variável estimada tem 95% de probabilidade de estar dentro do intervalo calculado, trata-se de uma estimativa intervalar.

\\[  \\mu = \overline{x} \pm z \frac{\\sigma}{\sqrt{n}} \\]

\\[  \\mu = \overline{x} \pm z \frac{s}{\sqrt{n}} \\]

## Calculando o tamanho da amostra

### População infinita

Dado um intervalo de confiança desejado é possível obter, a partir das equações de intervalo de confiança, o tamanho ideal de uma amostra. Para isso basta isolar o fator \\( n \\) nas equações do intervalo de confiança:

\\[ n = \left( z \frac{\\sigma}{e}\right)^2 \\]

\\[ n = \left( z \frac{s}{e}\right)^2 \\]

- O desvio padrão e o erro devem estar na mesma medida
- Quando o erro for representado em percentual, este percentual deve ser baseado na média

### População finita

Quando tratamos de variáveis quantitativas em uma população __finita__ as fórmulas mudam um pouco devido à adição de um fator de correção. Esse fator é necessário pois precisamos relativizar o tamanho da amostra em relação ao tamanho da população, assim o novo parâmetro \\( N \\) representa o tamanho da população.

\\[ n = \frac{z^2\\sigma^2N}{z^2\\sigma^2 + e^2(N - 1)} \\]
\\[ n = \frac{z^2s^2N}{z^2s^2 + e^2(N - 1)} \\]