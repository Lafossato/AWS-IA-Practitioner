# Resumo Completo — Métricas de Regressão, PDPs e Infraestrutura AWS para IA

# 1. Introdução Geral

A aula aborda três grandes temas:

- métricas de regressão;
- explicabilidade de modelos;
- infraestrutura AWS para treinamento e inferência de IA.

Os tópicos principais incluem:

- MSE;
- RMSE;
- R²;
- PDPs;
- EC2 Trainium;
- EC2 Inferentia.

---

# 2. Métricas de Regressão

Em modelos de regressão:
- o objetivo é prever valores numéricos.

Exemplos:
- preço;
- temperatura;
- demanda;
- tempo.

## Problema principal

O modelo sempre gera erros.

Erro:

```text
valor previsto − valor real
```

Como existem vários erros:
- precisamos resumir todos em métricas.

As principais métricas são:
- MSE;
- RMSE;
- R².

:contentReference[oaicite:0]{index=0}

---

# 3. MSE — Mean Squared Error

## Definição

MSE significa:

```text
Mean Squared Error
```

ou:

```text
Erro Quadrático Médio
```

## Objetivo

Calcular a média dos erros ao quadrado.

### Fórmula

:contentReference[oaicite:1]{index=1}

Onde:
- `yᵢ` = valor real;
- `ŷᵢ` = valor previsto.

---

# 4. Características do MSE

## Sempre positivo

O quadrado elimina sinais negativos.

---

## Sensível a outliers

Erros grandes recebem peso muito maior.

Exemplo:

```text
Erro = 10
→ 10² = 100
```

---

## Unidade ao quadrado

Se a variável estiver em:
```text
reais
```

o MSE fica em:
```text
reais²
```

Isso dificulta interpretação prática.

---

## Comparação entre modelos

Muito útil para:
- comparar modelos;
- otimização matemática.

:contentReference[oaicite:2]{index=2}

---

# 5. RMSE — Root Mean Squared Error

## Definição

RMSE significa:

```text
Root Mean Squared Error
```

ou:

```text
Raiz do Erro Quadrático Médio
```

## Relação com MSE

É simplesmente:
- a raiz quadrada do MSE.

### Fórmula

:contentReference[oaicite:3]{index=3}

:contentReference[oaicite:4]{index=4}

---

# 6. Vantagens do RMSE

## Mesma unidade dos dados

Se a variável estiver em:
```text
reais
```

o RMSE também estará em:
```text
reais
```

---

## Mais interpretável

Permite leitura intuitiva:

```text
"Em média, o modelo erra cerca de X unidades."
```

---

## Ainda sensível a outliers

Como deriva do MSE:
- continua penalizando erros grandes.

:contentReference[oaicite:5]{index=5}

---

# 7. MSE vs RMSE

| MSE | RMSE |
|---|---|
| Erro ao quadrado | Raiz do erro |
| Unidade ao quadrado | Unidade original |
| Mais técnico | Mais interpretável |
| Muito usado em otimização | Muito usado em relatórios |

## Ideia principal

Os dois contam a mesma história:
- RMSE apenas traduz o erro para uma escala mais intuitiva.

:contentReference[oaicite:6]{index=6}

---

# 8. R² — Coeficiente de Determinação

## Definição

O R² mede:
- quanto da variabilidade dos dados o modelo consegue explicar.

### Ideia principal

Não mede erro diretamente.

Ele mede:
```text
poder explicativo
```

:contentReference[oaicite:7]{index=7}

---

# 9. Interpretação do R²

## Valor = 1

Modelo perfeito.

Explica:
```text
100% da variabilidade
```

---

## Valor = 0

Não explica nada.

Equivale a:
```text
prever sempre a média
```

---

## Valor < 0

Modelo pior que simplesmente usar a média.

---

## Regra geral

Quanto mais próximo de 1:
- melhor o ajuste do modelo.

:contentReference[oaicite:8]{index=8}

---

# 10. Limitações do R²

## Problemas importantes

### R² alto não garante modelo bom

O modelo pode:
- decorar os dados;
- falhar em produção.

---

## Pode ser inflado

Adicionar muitas variáveis:
- pode aumentar artificialmente o R².

---

## Não substitui RMSE

Boa prática:
- usar RMSE + R² juntos.

:contentReference[oaicite:9]{index=9}

---

# 11. Comparação Geral das Métricas

| Métrica | Mede | Unidade | Sensível a outliers |
|---|---|---|---|
| MSE | Erro ao quadrado | Ao quadrado | Sim |
| RMSE | Erro médio típico | Mesma unidade | Sim |
| R² | Poder explicativo | Sem unidade | Indiretamente |

## Boa prática profissional

Relatar:
- RMSE;
- R²;

em conjunto.

:contentReference[oaicite:10]{index=10}

---

# 12. PDPs — Partial Dependence Plots

## Definição

PDP significa:

```text
Partial Dependence Plot
```

ou:

```text
Gráfico de Dependência Parcial
```

## Objetivo

Explicar como uma variável influencia a previsão do modelo.

---

# 13. Por que PDPs são importantes

Métricas mostram:
```text
quanto o modelo erra
```

PDPs mostram:
```text
por que ele toma decisões
```

:contentReference[oaicite:11]{index=11}

---

# 14. O que PDPs respondem

Pergunta principal:

```text
"Como esta variável influencia a previsão?"
```

Eles mostram:
- efeito médio de uma variável;
- impacto sobre a previsão final.

:contentReference[oaicite:12]{index=12}

---

# 15. Como PDPs Funcionam

## Passo 1

Escolher uma variável.

---

## Passo 2

Variar os valores dessa variável.

---

## Passo 3

Gerar previsões mantendo o restante fixo.

---

## Passo 4

Calcular média das previsões.

---

## Resultado

Uma curva explicando o efeito médio da variável.

:contentReference[oaicite:13]{index=13}

---

# 16. Interpretação dos PDPs

## Eixo X

Valores da variável.

---

## Eixo Y

Impacto médio na previsão.

---

# 17. Formato das Curvas

## Curva crescente

Aumentar variável:
- aumenta previsão.

---

## Curva decrescente

Aumentar variável:
- reduz previsão.

---

## Curva plana

Variável possui:
- pouco impacto.

---

## Curvas não lineares

Mostram:
- comportamentos complexos.

:contentReference[oaicite:14]{index=14}

---

# 18. Aplicações dos PDPs

## Explicabilidade

Tornar modelos compreensíveis.

---

## Diagnóstico

Detectar:
- vieses;
- comportamentos inesperados.

---

## Comunicação

Facilitar explicação para áreas de negócio.

---

## Governança

Ajudar:
- auditoria;
- compliance;
- transparência.

:contentReference[oaicite:15]{index=15}

---

# 19. EC2 Trainium e Inferentia

A :contentReference[oaicite:16]{index=16} oferece famílias específicas de instâncias EC2 para IA.

As duas principais são:

| Família | Objetivo |
|---|---|
| Trainium | Treinamento |
| Inferentia | Inferência |

:contentReference[oaicite:17]{index=17}

---

# 20. EC2 Trainium

## Objetivo

Treinar modelos de IA.

## Características

- chip AWS Trainium;
- otimizado para deep learning;
- cargas longas e intensivas;
- treinamento em larga escala.

---

# 21. Casos de Uso do Trainium

## Aplicações

- LLMs;
- visão computacional;
- NLP;
- IA Generativa.

## Benefício principal

Redução de custo de treinamento.

:contentReference[oaicite:18]{index=18}

---

# 22. EC2 Inferentia

## Objetivo

Executar inferência de modelos já treinados.

## Características

- chip AWS Inferentia;
- baixa latência;
- alto volume;
- custo reduzido por previsão.

:contentReference[oaicite:19]{index=19}

---

# 23. Casos de Uso do Inferentia

## Aplicações

- APIs de IA;
- chatbots;
- previsões em produção;
- sistemas em tempo real.

## Benefícios

- menor custo de inferência;
- maior velocidade;
- baixa latência.

:contentReference[oaicite:20]{index=20}

---

# 24. Trainium vs Inferentia

| Trainium | Inferentia |
|---|---|
| Treinamento | Inferência |
| Deep learning pesado | Uso do modelo pronto |
| Cargas longas | Baixa latência |
| Foco em aprendizado | Foco em previsões |

## Regra prática

```text
Trainium → aprender
Inferentia → servir
```

:contentReference[oaicite:21]{index=21}

---

# 25. Pergunta da Aula — Instância EC2

## Cenário

Instituição deseja:
- treinar LLM;
- reduzir impacto ambiental;
- otimizar treinamento.

## Resposta correta

```text
(C) Amazon EC2 série Trn
```

## Motivo

Trainium foi criado especificamente para:
- treinamento eficiente;
- redução de custo;
- workloads pesadas de IA.

:contentReference[oaicite:22]{index=22}

---

# 26. Pergunta da Aula — Explicabilidade

## Cenário

Universidade precisa:
- transparência;
- explicabilidade;
- relatório compreensível.

## Resposta correta

```text
(B) Gráficos de dependência parcial (PDPs)
```

## Motivo

PDPs explicam:
- como variáveis influenciam previsões.

:contentReference[oaicite:23]{index=23}

---

# 27. Principais Aprendizados

## MSE

Mede erro quadrático.

---

## RMSE

Mede erro médio interpretável.

---

## R²

Mede poder explicativo.

---

## PDPs

Explicam comportamento do modelo.

---

## Trainium

Infraestrutura otimizada para:
- treinamento.

---

## Inferentia

Infraestrutura otimizada para:
- inferência.

:contentReference[oaicite:24]{index=24}

---

# 28. Conclusão Geral

A aula mostra três pilares fundamentais da IA moderna:

## Métricas

Avaliam:
- qualidade;
- erro;
- capacidade explicativa.

---

## Explicabilidade

Ajuda humanos a:
- entender decisões;
- confiar nos modelos.

---

## Infraestrutura

Permite:
- escalar treinamento;
- otimizar inferência;
- reduzir custos.

Fluxo geral:

```text
Dados
↓
Treinamento (Trainium)
↓
Avaliação (MSE/RMSE/R²)
↓
Explicabilidade (PDPs)
↓
Inferência (Inferentia)
```
