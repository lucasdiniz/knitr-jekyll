---
layout: post
title: "A melhor de todas as séries"
published: true 
tags: [htmlwidgets, r]
output: hmtl_notebook
---





 Para responder as perguntas abaixo precisaremos apenas de alguns dos dados que temos disponíveis sobre as séries, os mais essenciais para as visualizações e interpretações aqui apresentadas são:
  
  1 - _season_: Variável numérica discreta que representa o número da temporada da série em questão. No nosso caso esta assume apenas os valores 1, 2 e 3. Uma vez que nenhuma das séries analisadas possui mais de três temporadas.
  
  2 - _UserRating_: Variável numérica contínua que representa a pontuação de um episódio obtida através das avaliações dos usuários. Pode assumir valores entre 0 e 10.
  
  3 - season_ep: Variável numérica discreta que representa o número do episódio referente a uma certa temporada. Pode assumir valores a partir de 1 até o número de episódios da temporada. (Creio que seja seguro afirmar que esse valor dificilmente passará de 30 pra qualquer série)


## __Pergunta 1:__ Qual das séries escolhidas é a mais "constante"? (Ou seja, a qualidade de seus episódios varia menos)  

  Para responder essa pergunta, vamos observar a evolução do *rating* dos episódios ao longo dos episodios de cada temporada. E utilizando métricas de agrupamento dos dados (tais como distância inter-quartil e desvio padrão) poderemos achar a resposta, uma vez que é esperado que uma série com qualidade mais constante tenha notas bem próximas para os seus episódios. 

<img src="/figure/source/lab1/2017-05-29-a-melhor-serie/unnamed-chunk-2-1.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="1280px" />

```
## [1] "Desvio Padrão = 0.501 e Distância inter-quartil = 0.550"
```


<img src="/figure/source/lab1/2017-05-29-a-melhor-serie/unnamed-chunk-3-1.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="1280px" />

```
## [1] "Desvio Padrão = 0.253 e Distância inter-quartil = 0.275"
```


<img src="/figure/source/lab1/2017-05-29-a-melhor-serie/unnamed-chunk-4-1.png" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" width="1280px" />

```
## [1] "Desvio Padrão = 0.514 e Distância inter-quartil = 0.500"
```



<img src="/figure/source/lab1/2017-05-29-a-melhor-serie/unnamed-chunk-5-1.png" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" width="1280px" />

```
## [1] "Desvio Padrão = 0.413 e Distância inter-quartil = 0.600"
```
#### Resposta para a pergunta 1:

Basta olhar os gráficos para perceber que __Stranger Things__ é, de longe, a série que mantém a qualidade mais constante, com apenas __0.8__ pontos de diferença entre a classificação de seu melhor e de seu pior episódio, valor muito inferior às outras séries. Caso isso não seja convicente o suficiente, podemos checar as métricas de agrupamento e verificar que os valores obtidos para Stranger Things são praticamente a metade dos valores obtidos para as outras séries. Utilizando as mesmas visualizações e interpretações utilizadas para responder a pergunta 1, poderiamos também responder uma das outras perguntas propostas no checkpoint 3: __#Levando em consideração o melhor/pior episódio de cada série, qual seria a série mais "inconstante"? (Que a qualidade dos episódios mais varia.)__

#### Resposta para a pergunta adicional:

Temos Black Mirror, 13 Reasons Why e Sense 8 com resultados semelhantes nas métricas de agrupamento, entretanto, levando em consideração o melhor/pior episódio, __Sense 8__ é a série que apresenta a maior variação, com uma diferença de __2.2__ pontos entre o seu pior e o seu melhor episódio.


## __Pergunta 2:__ Quais séries ficaram melhores ao longo das temporadas? 

Utilizando as mesmas visualizações usadas na pergunta 1 seria possível concluir a olho nu que existe sim uma tendência dos episódios ficarem melhores nos finais das temporadas. Contudo, para ter certeza do que estamos vendo, podemos realizar um cálculo simples da média das notas dos episódios na primeira metade da temporada e comparar com a média dos episódios da metade final. Vale notar que mesmo que tenhamos valores extremos (muito inferiores ou muito superiores aos demais) que influenciem na média, o intuito é que esses valores de fato influenciem no resultado uma vez que queremos comparar as duas metades de cada temporada como um todo.


__Sense 8__

```
## Media da primeira metade da temporada 1 de Sense 8: 8.28 
## Media da segunda metade da temporada 1 de Sense 8: 8.92
```

```
## Media da primeira metade da temporada 2 de Sense 8: 9.06 
## Media da segunda metade da temporada 2 de Sense 8: 9.33
```


__Stranger Things__

```
## Media da primeira metade da temporada 1 de Stranger Things: 8.78 
## Media da segunda metade da temporada 1 de Stranger Things: 9.03
```


__Black Mirror__


```
## Media da primeira metade da temporada 1 de Black Mirror: 8.10 
## Media da segunda metade da temporada 1 de Black Mirror: 8.50
```

```
## Media da primeira metade da temporada 2 de Black Mirror: 8.20 
## Media da segunda metade da temporada 2 de Black Mirror: 8.05
```

```
## Media da primeira metade da temporada 3 de Black Mirror: 8.33 
## Media da segunda metade da temporada 3 de Black Mirror: 8.47
```

__13 Reasons Why__

```
## Media da primeira metade da temporada 1 de 13 Reasons Why: 8.17 
## Media da segunda metade da temporada 1 de 13 Reasons Why: 8.62
```

### Resposta para a pergunta 2:
  
  Por fim, as médias descobertas apenas evidenciam o que já desconfiavamos antes, existem sim uma tendência das séries ficarem melhores no final das temporadas. __Nas séries aqui analisadas, todas elas ficaram melhores no final das temporadas__ houve apenas um caso na segunda temporada da série Black Mirror em que a metade final da série teve média menor que a metade inicial. Entretanto, esse é um caso especial pois a temporada possui apenas 4 episódios e na metade final desta mesma segunda temporada estão ambos o melhor e o pior episódios de toda a série. Portanto, este único caso que fugiu ao padrão não representa o todo, a maioria. Com os dados das médias obtidos anteriormente, seria possível ainda responder a pergunta adicional: __#Qual a melhor série dentre as escolhidas?__
  
  
### Resposta para a pergunta adicional:

  Levando em consideração apenas a classificação média por temporada, __poderiamos concluir que Stranger Things apresenta a melhor média e portanto é a melhor série__. Contudo, os números mostram que, apesar de ter uma média geral menor, a segunda temporada de Sense8 consegue ser melhor que a única temporada de Stranger Things. Portanto, opinião e gosto pessoal também têm um peso importante nessa resposta.
  
