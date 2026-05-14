# Técnicas de Machine Learning

# 1. Introdução Geral

A aula apresenta os fundamentos das principais técnicas de Machine Learning.

Os conteúdos abordados são:

- regressão;
- classificação;
- clustering.

O foco principal é compreender:
- quando usar cada técnica;
- como elas funcionam;
- quais problemas resolvem.

---

# 2. O que é Machine Learning

Machine Learning (ML) é uma área da Inteligência Artificial em que computadores aprendem padrões a partir de dados.

## Ideia principal

Em vez de programar regras manualmente:
- o modelo aprende automaticamente analisando exemplos.

## Fluxo básico

```text
Dados históricos
↓
Treinamento do modelo
↓
Previsão ou decisão
```

## Por que isso é importante

Permite resolver problemas complexos onde criar regras manualmente seria inviável.

### Exemplos

- prever preços;
- detectar fraude;
- recomendar conteúdo;
- segmentar clientes.

---

# 3. Machine Learning na Nuvem

A computação em nuvem facilitou o uso de ML em larga escala.

## Principais vantagens

### Escalabilidade

A nuvem fornece:
- GPUs;
- CPUs;
- armazenamento;
- processamento sob demanda.

---

### Serviços Gerenciados

Provedores cloud oferecem ferramentas prontas para:
- treinamento;
- deploy;
- monitoramento;
- inferência.

---

### Democratização

Mesmo profissionais sem grande experiência em ciência de dados conseguem utilizar ML através de APIs e serviços prontos.

---

# 4. As Três Grandes Famílias do Machine Learning

A aula divide ML em três grandes categorias.

| Família | Pergunta principal | Objetivo |
|---|---|---|
| Regressão | Quanto? | Prever valores numéricos |
| Classificação | Qual categoria? | Prever rótulos |
| Clustering | Quem se parece com quem? | Descobrir grupos |

---

# 5. Regressão

## O que é regressão

Regressão é uma técnica usada para prever valores numéricos contínuos.

## Características

- saída numérica;
- previsão de quantidades;
- relação entre variáveis de entrada e saída.

## Exemplos

- preço de imóveis;
- demanda de produtos;
- consumo de energia;
- tempo de entrega.

---

# 6. Regressão Linear

## Ideia central

Encontrar a melhor linha reta que representa os dados.

## Funcionamento

O modelo:
- observa os dados;
- tenta minimizar o erro;
- ajusta os pesos das variáveis.

## Objetivo matemático

Encontrar uma reta que fique o mais próxima possível dos pontos reais.

### Representação


::contentReference[oaicite:0]{index=0}


Onde:
- `m` = inclinação da reta;
- `b` = intercepto.

---

# 7. Intuição da Regressão Linear

## Passos

1. observar padrão dos dados;
2. traçar a melhor reta;
3. usar a reta para prever novos valores.

## Exemplo

Entrada:
- área do imóvel.

Saída:
- preço estimado.

Quanto maior a área:
- maior tende a ser o preço.

---

# 8. Vantagens da Regressão Linear

## Pontos fortes

- simples;
- rápida;
- fácil de interpretar;
- baixo custo computacional.

## Limitações

Funciona melhor quando:
- a relação entre variáveis é linear.

Pode falhar em:
- padrões complexos;
- relações condicionais.

---

# 9. Árvores de Decisão

## Ideia central

Tomar decisões em sequência usando perguntas.

## Estrutura

A árvore possui:

- nós;
- ramos;
- folhas.

### Funcionamento

Cada pergunta divide os dados em grupos menores e mais homogêneos.

---

# 10. Exemplo de Árvore de Decisão

```text
Área > 100m²?
├── Não → R$ 250k
└── Sim
    ├── Tem garagem?
    │   ├── Não → R$ 520k
    │   └── Sim → R$ 700k
```

---

# 11. Vantagens das Árvores

## Pontos positivos

- capturam relações não-lineares;
- interpretáveis visualmente;
- funcionam bem com regras condicionais.

## Limitações

Podem:
- decorar demais os dados;
- sofrer overfitting.

---

# 12. Regressão Linear vs Árvores de Decisão

| Regressão Linear | Árvores de Decisão |
|---|---|
| Relações lineares | Relações não-lineares |
| Fácil interpretação matemática | Fácil interpretação visual |
| Mais simples | Mais flexível |
| Menos eficaz em padrões complexos | Melhor em regras condicionais |

---

# 13. Classificação

## O que é classificação

Classificação prevê categorias ou rótulos.

## Diferença para regressão

| Regressão | Classificação |
|---|---|
| Prevê números | Prevê categorias |

---

# 14. Exemplos de Classificação

- spam ou não spam;
- fraude ou não fraude;
- tipo de produto;
- sentimento positivo ou negativo.

---

# 15. Classificação Binária

## Definição

Existem apenas duas classes possíveis.

### Exemplos

- fraude / não fraude;
- spam / não spam;
- aprovado / reprovado.

---

# 16. Funcionamento da Classificação Binária

O modelo:
1. calcula probabilidade;
2. compara com um limiar;
3. decide a classe final.

---

# 17. Limiar de Decisão

## O que é

Valor usado para decidir entre:
- classe positiva;
- classe negativa.

### Exemplo

Se:
```text
Probabilidade > 0.5
```

Então:
```text
Classe positiva
```

---

# 18. Ajuste do Limiar

## Limiar baixo

- mais sensível;
- detecta mais positivos;
- gera mais falsos positivos.

---

## Limiar alto

- mais conservador;
- reduz alarmes falsos;
- pode perder casos importantes.

---

# 19. Classificação Multiclasse

## Definição

O modelo escolhe entre três ou mais categorias.

## Funcionamento

Calcula probabilidade para cada classe.

Exemplo:

| Classe | Probabilidade |
|---|---|
| A | 65% |
| B | 20% |
| C | 10% |
| D | 5% |

O modelo escolhe:
```text
Classe A
```

---

# 20. Exemplos de Multiclasse

- idioma do texto;
- categoria de produto;
- reconhecimento de objetos;
- classificação de tickets.

---

# 21. K-NN (K-Nearest Neighbors)

## Ideia central

O modelo observa os vizinhos mais próximos.

## Funcionamento

1. calcula distância;
2. encontra os K vizinhos mais próximos;
3. escolhe a classe mais frequente.

---

# 22. Exemplo do K-NN

```text
Novo ponto
↓
Observa vizinhos próximos
↓
Maioria dos vizinhos = classe final
```

---

# 23. Importância do K

## K pequeno

- muito sensível;
- sofre com ruído.

---

## K grande

- perde sensibilidade local;
- tende para classe majoritária.

---

## K equilibrado

Melhor equilíbrio entre:
- precisão;
- estabilidade.

---

# 24. XGBoost

## Ideia central

Combinar várias árvores de decisão para criar um modelo mais forte.

## Funcionamento

1. treina uma árvore;
2. identifica erros;
3. nova árvore corrige erros;
4. processo se repete.

---

# 25. Boosting

O aprendizado ocorre em sequência.

```text
Árvore 1
↓
Corrige erros
↓
Árvore 2
↓
Corrige erros
↓
Árvore 3
↓
Modelo final
```

---

# 26. Vantagens do XGBoost

## Pontos fortes

- alta precisão;
- muito usado no mercado;
- excelente para dados tabulares;
- robusto;
- funciona em:
  - regressão;
  - classificação.

---

# 27. Ranking com XGBoost

## Objetivo

Aprender a ordenar itens por relevância.

## Aplicações

- buscadores;
- e-commerce;
- sistemas de recomendação;
- CRM.

---

# 28. Exemplo de Ranking

Busca:
```text
"tênis para corrida"
```

Resultado:

| Produto | Relevância |
|---|---|
| Tênis corrida | 9.2 |
| Tênis esportivo | 7.5 |
| Tênis casual | 5.1 |

---

# 29. Clustering

## O que é clustering

Clustering é uma técnica não supervisionada.

## Objetivo

Encontrar grupos naturais nos dados.

## Pergunta principal

```text
Quem se parece com quem?
```

---

# 30. Características do Clustering

## Diferença principal

Não existem rótulos.

O algoritmo:
- descobre padrões sozinho.

---

# 31. Aplicações do Clustering

- segmentação de clientes;
- agrupamento de produtos;
- detecção de padrões;
- análise de comportamento;
- detecção de anomalias.

---

# 32. K-Means

## Ideia central

Dividir os dados em K grupos.

## Objetivo

Pontos do mesmo grupo:
- devem ser parecidos.

Pontos de grupos diferentes:
- devem ser diferentes.

---

# 33. Centróides

Cada grupo possui um ponto central chamado centróide.

## Funcionamento

Cada observação:
- pertence ao centróide mais próximo.

---

# 34. Funcionamento do K-Means

## Passo a passo

1. escolher K;
2. posicionar centróides;
3. atribuir pontos;
4. recalcular centróides;
5. repetir até estabilizar.

---

# 35. Importância do K

O valor de K influencia diretamente:
- quantidade de grupos;
- qualidade do clustering.

---

# 36. Cuidados com K-Means

## Limitações

- sensível à escala dos dados;
- depende da escolha de K;
- funciona melhor com grupos regulares.

---

# 37. Comparação Geral das Técnicas

| Técnica | Tipo | Objetivo | Exemplo |
|---|---|---|---|
| Regressão | Supervisionado | Prever número | Preço |
| Classificação | Supervisionado | Prever categoria | Spam |
| Clustering | Não supervisionado | Descobrir grupos | Segmentação |

---

# 38. Como Escolher a Técnica Correta

## Precisa prever número?

Use:
- regressão.

---

## Precisa prever categoria?

Use:
- classificação.

---

## Precisa descobrir grupos?

Use:
- clustering.

---

# 39. Principais Aprendizados

## Machine Learning aprende padrões

O modelo aprende com dados, não com regras fixas.

---

## Existem três famílias principais

- regressão;
- classificação;
- clustering.

---

## A escolha depende do problema

A técnica correta depende:
- do tipo de saída;
- da existência de rótulos;
- da complexidade dos dados.

---

# 40. Conclusão Geral

A aula apresenta os principais fundamentos das técnicas clássicas de Machine Learning.

Resumo da evolução:

```text
Dados
↓
Treinamento
↓
Modelo aprende padrões
↓
Previsão / Classificação / Agrupamento
```

As técnicas estudadas formam a base de muitos sistemas modernos de IA utilizados em:

- recomendação;
- previsão;
- detecção de fraude;
- segmentação;
- buscadores;
- análise de dados;
- automação inteligente.
