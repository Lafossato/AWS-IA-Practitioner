# Resumo Completo — Tipos de Inferência e Métricas de Performance de Modelos

# 1. Introdução Geral

A aula apresenta os principais conceitos sobre:

- tipos de inferência;
- métricas de performance de modelos de Machine Learning;
- avaliação técnica e de negócio.

O objetivo é compreender:
- como modelos são utilizados em produção;
- como escolher a estratégia correta de inferência;
- como medir qualidade e impacto do modelo.

---

# 2. O que é Inferência

Inferência é o uso de um modelo já treinado para gerar previsões utilizando novos dados.

## Fluxo geral

```text
Treinamento
↓
Modelo treinado
↓
Inferência
↓
Previsão
```

## Importância

A forma de servir o modelo impacta:

- latência;
- custo;
- escalabilidade;
- experiência do usuário;
- arquitetura da solução.

---

# 3. Principais Tipos de Inferência

Existem quatro principais abordagens:

| Tipo | Característica principal |
|---|---|
| Lote (Batch) | Processa grandes volumes juntos |
| Tempo Real | Resposta imediata |
| Assíncrona | Processa em segundo plano |
| Serverless | Sem gerenciar servidores |

---

# 4. Inferência em Lote (Batch)

## Definição

Processa grandes volumes de dados de uma só vez.

## Características

- execução planejada;
- não exige resposta imediata;
- resultados gravados em:
  - arquivos;
  - bancos;
  - armazenamento.

## Recursos

Os recursos computacionais:
- são criados apenas durante o job.

## Vantagem principal

Menor custo por previsão.

---

# 5. Quando usar Inferência em Lote

## Cenários ideais

- relatórios;
- scoring noturno;
- análises periódicas;
- grandes conjuntos de dados históricos.

## Exemplo

```text
Milhões de transações processadas toda madrugada.
```

---

# 6. Inferência em Tempo Real

## Definição

Responde imediatamente a cada requisição.

## Características

- baixa latência;
- respostas em milissegundos;
- endpoint sempre disponível.

## Infraestrutura

A capacidade precisa ser dimensionada para:
- picos de uso;
- disponibilidade contínua.

## Consequência

Maior custo operacional.

---

# 7. Quando usar Tempo Real

## Aplicações

- apps interativos;
- detecção de fraude online;
- recomendação instantânea;
- chatbots.

## Exemplo

```text
Aprovação imediata de cartão de crédito.
```

---

# 8. Batch vs Tempo Real

| Critério | Batch | Tempo Real |
|---|---|---|
| Latência | Alta | Baixa |
| Volume | Grande | Individual |
| Custo | Menor | Maior |
| Disponibilidade | Periódica | Contínua |
| Uso típico | Relatórios | Apps interativos |

---

# 9. Inferência Assíncrona

## Definição

A requisição é enviada e processada em segundo plano.

## Funcionamento

```text
Cliente envia requisição
↓
Processamento ocorre sem bloquear
↓
Resultado é entregue depois
```

## Características

- aceita payloads grandes;
- suporta inferências longas;
- equilíbrio entre custo e latência.

---

# 10. Quando usar Inferência Assíncrona

## Cenários ideais

- arquivos grandes;
- processamento longo;
- cliente pode esperar alguns minutos.

## Exemplo

```text
Processamento de vídeos, PDFs ou grandes arquivos de imagem.
```

---

# 11. Inferência Serverless

## Definição

O usuário não gerencia servidores.

## Características

- escalabilidade automática;
- cobrança apenas pelo uso;
- infraestrutura totalmente gerenciada.

## Vantagem principal

Redução da complexidade operacional.

---

# 12. Quando usar Serverless

## Ideal para

- cargas imprevisíveis;
- tráfego variável;
- aplicações com baixo volume.

## Benefícios

- menos custo ocioso;
- implantação simples;
- gerenciamento reduzido.

---

# 13. SageMaker Serverless Inference

## O que é

Serviço gerenciado do :contentReference[oaicite:0]{index=0} para servir modelos sem provisionar infraestrutura.

## Características

- inicialização automática;
- escala automática;
- sem custo quando o endpoint está parado.

## Melhor cenário

Workloads:
- imprevisíveis;
- intermitentes;
- de baixo tráfego.

---

# 14. Como Escolher o Tipo de Inferência

| Cenário | Melhor opção |
|---|---|
| Grandes volumes históricos | Batch |
| Resposta instantânea | Tempo real |
| Arquivos grandes e demora alta | Assíncrona |
| Baixo volume e tráfego variável | Serverless |

---

# 15. Métricas de Performance

Após treinar um modelo, é necessário avaliar sua qualidade.

## Objetivos

- medir desempenho;
- identificar erros;
- validar uso em produção;
- avaliar impacto real.

---

# 16. Importância das Métricas

Cada métrica responde uma pergunta diferente.

## Exemplo

- o modelo acerta muito?
- ele erra casos importantes?
- gera muitos alarmes falsos?
- o negócio ganha valor?

---

# 17. Matriz de Confusão

A matriz de confusão organiza os acertos e erros de classificação.

## Estrutura

| | Previsto Positivo | Previsto Negativo |
|---|---|---|
| Real Positivo | VP | FN |
| Real Negativo | FP | VN |

---

# 18. Componentes da Matriz

## VP — Verdadeiro Positivo

O modelo acertou um caso positivo.

---

## VN — Verdadeiro Negativo

O modelo acertou um caso negativo.

---

## FP — Falso Positivo

O modelo marcou positivo quando era negativo.

### Exemplo

```text
Transação legítima marcada como fraude.
```

---

## FN — Falso Negativo

O modelo marcou negativo quando era positivo.

### Exemplo

```text
Fraude real não detectada.
```

---

# 19. Acurácia

## Definição

Proporção total de acertos.

## Fórmula

:contentReference[oaicite:1]{index=1}

## Características

- visão geral do modelo;
- simples de interpretar.

## Problema

Pode ser enganosa em classes desbalanceadas.

---

# 20. Classes Desbalanceadas

## Exemplo

```text
99% das transações são legítimas.
```

Um modelo que sempre responde:
```text
"não fraude"
```

teria:
```text
99% de acurácia
```

mesmo sendo inútil.

---

# 21. Precisão

## Definição

Dos exemplos previstos como positivos:
- quantos realmente eram positivos.

## Fórmula

:contentReference[oaicite:2]{index=2}

## Objetivo principal

Reduzir falsos positivos.

---

# 22. Quando Precisão é Importante

## Exemplos

- detecção de fraude;
- spam;
- bloqueios automáticos.

## Problema evitado

```text
Acusar algo errado como positivo.
```

---

# 23. Recall (Sensibilidade)

## Definição

Dos positivos reais:
- quantos o modelo encontrou.

## Fórmula

:contentReference[oaicite:3]{index=3}

## Objetivo principal

Reduzir falsos negativos.

---

# 24. Quando Recall é Importante

## Exemplos

- diagnóstico médico;
- fraude;
- segurança.

## Problema evitado

```text
Deixar passar casos críticos.
```

---

# 25. Precisão vs Recall

| Precisão | Recall |
|---|---|
| Evita falsos positivos | Evita falsos negativos |
| Foco em qualidade do positivo | Foco em encontrar positivos |

---

# 26. F1 Score

## Definição

Combina Precisão e Recall.

## Objetivo

Encontrar equilíbrio entre:
- falsos positivos;
- falsos negativos.

## Característica

Utiliza média harmônica.

## Melhor cenário

Problemas com:
- classes desbalanceadas.

---

# 27. AUC (Area Under the Curve)

## Definição

Mede a capacidade do modelo distinguir classes.

## Características

- avalia vários limiares;
- independente de threshold específico.

## Interpretação

| Valor | Qualidade |
|---|---|
| 0.90 – 1.00 | Excelente |
| 0.80 – 0.90 | Bom |
| 0.70 – 0.80 | Razoável |
| 0.50 – 0.70 | Fraco |
| ≈ 0.50 | Aleatório |

---

# 28. MAE (Mean Absolute Error)

## Definição

Métrica utilizada em regressão.

## Objetivo

Medir o erro médio absoluto entre:
- valor previsto;
- valor real.

## Interpretação

```text
"Em média, quanto a previsão erra."
```

---

# 29. Características do MAE

## Vantagens

- fácil interpretação;
- mesma unidade do problema;
- simples de comunicar.

## Aplicações

- previsão de preço;
- temperatura;
- demanda;
- tempo.

---

# 30. Métricas Técnicas vs Negócio

Um modelo tecnicamente bom:
- não garante valor real.

É necessário avaliar:
- ROI;
- custo;
- impacto.

---

# 31. ROI (Retorno sobre Investimento)

## Objetivo

Comparar:
- ganho gerado;
- custo do modelo.

## Fórmula conceitual

```text
Lucro obtido ÷ custo do projeto
```

---

# 32. Custo Operacional

Inclui:

- treinamento;
- inferência;
- armazenamento;
- manutenção;
- infraestrutura.

---

# 33. Impacto no Negócio

## Mede efeitos reais

- receita;
- conversão;
- churn;
- eficiência;
- produtividade.

---

# 34. Escolha Correta de Métricas

| Problema | Métrica importante |
|---|---|
| Fraude | Recall |
| Spam | Precisão |
| Classes balanceadas | Acurácia |
| Classes desbalanceadas | F1 |
| Regressão | MAE |

---

# 35. Pergunta 1 da Aula

## Cenário

Históricos médicos enormes e sem necessidade imediata.

## Resposta correta

```text
(C) Transformação em lote
```

## Motivo

- grandes volumes;
- processamento planejado;
- sem urgência.

---

# 36. Pergunta 2 da Aula

## Cenário

Arquivos de até 1 GB e processamento de 1 hora com feedback rápido.

## Resposta correta

```text
(C) Inferência assíncrona
```

## Motivo

- payload grande;
- inferência longa;
- cliente pode aguardar;
- não exige milissegundos.

---

# 37. Resumo Final dos Tipos de Inferência

| Tipo | Melhor uso |
|---|---|
| Batch | Grandes volumes offline |
| Tempo Real | Resposta imediata |
| Assíncrona | Processamento longo |
| Serverless | Carga variável |

---

# 38. Resumo Final das Métricas

| Métrica | Mede |
|---|---|
| Acurácia | Total de acertos |
| Precisão | Qualidade dos positivos |
| Recall | Quantos positivos encontrou |
| F1 | Equilíbrio geral |
| AUC | Separação entre classes |
| MAE | Erro médio absoluto |

---

# 39. Conclusão Geral

A aula mostra dois pilares fundamentais da IA em produção:

## Inferência

Define:
- como o modelo atende usuários;
- custo;
- escalabilidade;
- latência.

## Métricas

Permitem:
- medir qualidade;
- identificar erros;
- avaliar impacto real.

A principal ideia é:

```text
Um modelo bom não é apenas preciso.
Ele também precisa ser útil, eficiente e gerar valor para o negócio.
```
