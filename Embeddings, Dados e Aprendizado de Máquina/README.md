# Embeddings, Processamento de Texto, Dados e Aprendizado de Máquina

# 1. Introdução Geral

A aula apresenta os principais fundamentos utilizados em sistemas modernos de Inteligência Artificial.

Os tópicos abordados incluem:

- embeddings;
- processamento de texto;
- tipos de dados;
- bancos vetoriais;
- rotulagem;
- aprendizado de máquina.

O objetivo é mostrar como dados são transformados em representações matemáticas para que modelos consigam:

- entender conteúdo;
- comparar significados;
- buscar informações;
- gerar respostas.

---

# 2. Embeddings

## O que são embeddings

Embeddings são representações numéricas de informações dentro de um espaço vetorial.

Eles convertem conteúdos como:

- texto;
- imagens;
- áudio;
- vídeos;

em vetores matemáticos.

## Objetivo principal

Permitir que computadores comparem significados utilizando matemática.

### Ideia principal

Conteúdos semanticamente parecidos ficam próximos no espaço vetorial.

Exemplo:

- “gato” fica próximo de “cão”;
- “carro” fica distante de “gato”.

## Aplicações

- busca semântica;
- recomendação;
- sistemas RAG;
- IA conversacional;
- classificação;
- IA Generativa.

---

# 3. Embedding de Texto

Embedding de texto transforma palavras, frases ou documentos em vetores numéricos.

## O que ele representa

- significado;
- contexto;
- relações semânticas;
- similaridade entre palavras.

### Exemplo

Texto:

```text
"banco financeiro"
```

Pode virar:

```text
[0.21, -0.45, 0.88, 0.13, ...]
```

## Aplicações

- chatbots;
- busca inteligente;
- recomendação;
- clustering;
- classificação textual.

---

# 4. Embedding de Imagem

Embedding de imagem transforma imagens em vetores matemáticos.

## O que é analisado

- formas;
- texturas;
- padrões;
- cores;
- objetos.

## Objetivo

Permitir comparação de imagens semelhantes.

## Aplicações

- reconhecimento visual;
- busca por imagem;
- moderação;
- visão computacional.

---

# 5. Embedding Multimodal

O embedding multimodal trabalha com diferentes tipos de dados no mesmo espaço vetorial.

## Modalidades possíveis

- texto;
- imagem;
- áudio;
- vídeo.

## Principal vantagem

Permitir comparação entre formatos diferentes.

### Exemplo

Uma imagem de praia pode ficar próxima do texto:

```text
"praia ao pôr do sol"
```

## Aplicações

- busca cruzada;
- recomendação multimodal;
- sistemas multimídia.

---

# 6. Geração Multimodal

A geração multimodal utiliza IA para criar conteúdos novos.

## Funcionamento

Recebe uma modalidade e gera outra.

### Exemplos

- texto → imagem;
- imagem → descrição;
- áudio → texto.

## Aplicações

- geração de imagens;
- legendas automáticas;
- criação de vídeos;
- IA criativa.

---

# 7. Diferença entre Embedding e Geração Multimodal

| Embedding Multimodal | Geração Multimodal |
|---|---|
| Compara conteúdos | Cria conteúdos |
| Mede similaridade | Gera novas saídas |
| Usa vetores | Usa IA generativa |

---

# 8. Processamento de Texto

Antes de compreender linguagem, modelos precisam processar o texto.

Esse processamento transforma palavras em representações manipuláveis matematicamente.

---

# 9. Tokenização

Tokenização é o processo de dividir texto em partes menores chamadas tokens.

## Tokens podem ser

- palavras;
- sílabas;
- caracteres;
- partes de palavras.

### Exemplo

Texto:

```text
"O gato dorme na cama"
```

Tokens:

```text
"O" | "gato" | "dorme" | "na" | "cama"
```

## Importância

É a primeira etapa do processamento de linguagem natural.

A forma como o texto é tokenizado impacta diretamente:

- desempenho;
- custo;
- qualidade da IA.

---

# 10. Bag-of-Words (BoW)

Bag-of-Words é uma técnica clássica de representação textual.

## Funcionamento

Conta quantas vezes cada palavra aparece.

### Características

- ignora ordem das palavras;
- ignora contexto;
- transforma texto em números.

### Exemplo

Texto:

```text
"o gato dorme na cama, o gato adora a casa"
```

Representação:

| Palavra | Frequência |
|---|---|
| gato | 2 |
| cama | 1 |
| dorme | 1 |
| casa | 1 |

## Vantagens

- simples;
- rápido;
- eficiente em problemas básicos.

## Limitações

- perde contexto;
- perde significado semântico;
- não entende relações entre palavras.

---

# 11. Contagem de Frequência

Conta quantas vezes cada palavra aparece em um texto.

## Objetivos

- identificar temas principais;
- transformar texto em dados numéricos;
- apoiar modelos estatísticos.

### Exemplo

| Palavra | Frequência |
|---|---|
| modelo | 5 |
| dados | 4 |
| treina | 3 |
| vetor | 2 |

## Aplicações

- TF-IDF;
- busca textual;
- classificação;
- NLP clássico.

---

# 12. Janela de Contexto

A janela de contexto define quantos tokens o modelo consegue enxergar ao mesmo tempo.

## Inclui

- prompt do usuário;
- resposta do modelo.

## Características

- janela maior → mais contexto;
- janela maior → maior custo computacional.

## Analogia

Funciona como a memória de curto prazo da IA.

## Problema

Quando o texto excede a janela:
- partes podem ser truncadas;
- informações podem ser perdidas.

---

# 13. Intervalos (Chunks)

Intervalos são divisões menores de documentos grandes.

## Objetivo

Fazer conteúdos extensos caberem na janela de contexto.

### Exemplo

```text
Documento longo
↓
Intervalo 1
Intervalo 2
Intervalo 3
```

## Aplicações

- RAG;
- busca semântica;
- indexação vetorial;
- chat com documentos.

---

# 14. Tipos de Dados

Os dados podem ser classificados em:

- estruturados;
- não estruturados.

---

# 15. Dados Estruturados

Dados organizados em tabelas.

## Características

- linhas e colunas;
- formato fixo;
- fáceis de consultar.

## Ferramenta principal

SQL.

## Exemplos

- planilhas;
- bancos relacionais;
- ERPs.

## Vantagens

- validação simples;
- fácil auditoria;
- processamento rápido.

---

# 16. Dados Não Estruturados

Não possuem formato tabular fixo.

## Exemplos

- textos;
- imagens;
- vídeos;
- áudios;
- e-mails.

## Características

- representam a maioria dos dados do mundo;
- mais difíceis de processar;
- exigem embeddings e IA.

---

# 17. Por que isso importa para IA

## Dados estruturados

- funcionam bem com SQL;
- modelos clássicos lidam melhor com eles.

## Dados não estruturados

- exigem embeddings;
- usam busca semântica;
- funcionam melhor em IA Generativa.

## Armazenamento

| Tipo | Onde guardar |
|---|---|
| Estruturados | Bancos relacionais |
| Não estruturados | Data lakes e objetos |

---

# 18. Bancos de Dados Vetoriais

Bancos vetoriais armazenam embeddings.

## Funções principais

- indexar vetores;
- buscar similaridade;
- encontrar conteúdos semanticamente próximos.

## Aplicações

- busca semântica;
- recomendação;
- RAG;
- IA conversacional.

---

# 19. Busca por Similaridade

A consulta ocorre comparando vetores matemáticos.

## Funcionamento

O sistema procura vetores mais próximos da consulta.

### Exemplo

Consulta:
```text
"gatos dormindo"
```

O banco retorna conteúdos semanticamente parecidos.

---

# 20. Aurora PostgreSQL com pgvector

O pgvector é uma extensão do PostgreSQL que adiciona suporte vetorial.

## Características

- armazena embeddings;
- faz consultas vetoriais;
- utiliza SQL.

## Vantagem principal

Combina:
- dados relacionais;
- dados vetoriais;

no mesmo banco.

## Benefícios

- menor complexidade;
- menos infraestrutura;
- integração simples.

---

# 21. Rotulagem de Dados

Rotulagem é o processo de associar respostas corretas aos dados.

## Exemplo

Imagem:
```text
foto de gato
```

Rótulo:
```text
"gato"
```

## Importância

Os rótulos são o material de aprendizado dos modelos supervisionados.

---

# 22. Dados Rotulados

Possuem respostas corretas associadas.

## Características

- usados em aprendizado supervisionado;
- alta qualidade;
- exigem revisão humana.

## Problemas

- caros;
- demorados;
- difíceis de produzir em grande escala.

---

# 23. Dados Não Rotulados

Possuem apenas entradas.

## Características

- abundantes;
- baratos;
- usados em aprendizado não supervisionado.

## Objetivo

Permitir que o modelo descubra padrões sozinho.

---

# 24. Amazon SageMaker Ground Truth

Serviço da AWS para rotulagem de dados em escala.

## Recursos

- rotulagem de:
  - imagens;
  - textos;
  - vídeos.

## Funcionalidades

- automação;
- governança;
- qualidade;
- trabalho humano integrado.

## Objetivo

Reduzir:
- custo;
- tempo;
- esforço de preparação de datasets.

---

# 25. Amazon Mechanical Turk

Plataforma da AWS de trabalho humano sob demanda.

## Objetivo

Executar tarefas difíceis para máquinas.

## Exemplos

- rotulagem;
- validação;
- revisão;
- curadoria.

## Características

- pagamento por tarefa;
- escalabilidade;
- integração com SageMaker.

---

# 26. Tipos de Aprendizado de Máquina

Existem cinco principais tipos de aprendizado:

1. supervisionado;
2. não supervisionado;
3. por reforço;
4. federado;
5. por transferência.

---

# 27. Aprendizado Supervisionado

Aprende utilizando dados rotulados.

## Objetivo

Mapear:

```text
entrada → resposta correta
```

## Aplicações

- classificação;
- regressão;
- spam;
- previsão.

## Exemplos

- detectar fraude;
- prever preços;
- identificar imagens.

---

# 28. Aprendizado Não Supervisionado

Aprende sem respostas corretas.

## Objetivo

Encontrar padrões ocultos.

## Aplicações

- clustering;
- segmentação;
- anomalias;
- redução de dimensionalidade.

---

# 29. Aprendizado por Reforço

Aprende por tentativa e erro.

## Funcionamento

- agente executa ações;
- recebe recompensas;
- ajusta estratégias.

## Aplicações

- jogos;
- robótica;
- otimização;
- automação.

---

# 30. Aprendizado Federado

Treinamento distribuído sem mover os dados.

## Características

- dados permanecem locais;
- privacidade preservada;
- apenas atualizações são compartilhadas.

## Aplicações

- saúde;
- bancos;
- celulares;
- IoT.

---

# 31. Aprendizado por Transferência

Reaproveita modelos já treinados.

## Objetivo

Evitar criar modelos do zero.

## Benefícios

- menor custo;
- menos tempo;
- aproveitamento de conhecimento prévio.

## Aplicações

- NLP;
- visão computacional;
- modelos fundacionais.

---

# 32. Comparativo dos Tipos de Aprendizado

| Tipo | Dados usados | Como aprende | Aplicações |
|---|---|---|---|
| Supervisionado | Rotulados | Aprende respostas corretas | Classificação |
| Não supervisionado | Não rotulados | Descobre padrões | Clustering |
| Reforço | Interação | Tentativa e erro | Jogos |
| Federado | Distribuídos | Sem centralizar dados | Privacidade |
| Transferência | Modelo pré-treinado | Reaproveita conhecimento | Fine-tuning |

---

# 33. Pipeline Geral da IA

Fluxo geral:

```text
Dados
↓
Pré-processamento
↓
Tokenização
↓
Embeddings
↓
Banco vetorial
↓
Treinamento
↓
Inferência
↓
Resposta ao usuário
```

---

# 34. Recapitulando Conceitos Importantes

## Embeddings

Transformam significado em vetores.

---

## Geração Multimodal

Cria conteúdos novos usando múltiplas modalidades.

---

## Janela de Contexto

Define quanto texto o modelo consegue analisar.

---

## Intervalos

Dividem documentos grandes em partes menores.

---

## pgvector

Permite vetores dentro do PostgreSQL.

---

## Ground Truth

Ferramenta de rotulagem gerenciada da AWS.

---

## Mechanical Turk

Plataforma humana sob demanda para tarefas de IA.

---

## Federado vs Transferência

| Federado | Transferência |
|---|---|
| Preserva privacidade | Reaproveita conhecimento |
| Dados ficam locais | Usa modelos pré-treinados |

---

# 35. Perguntas e Respostas da Aula

## Pergunta 1

### Cenário

Dados genéticos não rotulados precisam ser agrupados para encontrar padrões.

### Resposta correta

```text
(B) Aprendizagem não supervisionada
```

### Motivo

O problema envolve:
- dados sem rótulos;
- descoberta de padrões;
- clustering.

---

## Pergunta 2

### Cenário

Assistente virtual melhora com feedback dos usuários.

### Resposta correta

```text
(D) Aprendizado por reforço com recompensas
```

### Motivo

O sistema aprende utilizando:
- recompensas;
- avaliações;
- feedback contínuo.

---

## Pergunta 3

### Cenário

Deseja reutilizar modelos já treinados.

### Resposta correta

```text
(A) Aprendizado por transferência
```

### Motivo

A técnica reaproveita conhecimento prévio.

---

## Pergunta 4

### Cenário

Quantidade máxima de informações em um prompt no Amazon Bedrock.

### Resposta correta

```text
(C) Janela de Contexto
```

### Motivo

A janela define quantos tokens o modelo consegue processar.

---

## Pergunta 5

### Cenário

Sistema analisa texto e imagens simultaneamente.

### Resposta correta

```text
(C) Modelo de incorporação multimodal
```

### Motivo

O modelo trabalha múltiplas modalidades no mesmo espaço vetorial.

---

## Pergunta 6

### Cenário

Definição de tokens.

### Resposta correta

```text
(A) Unidades básicas de entrada e saída
```

### Motivo

Tokens são as menores unidades processadas pelo modelo.

---

# Conclusão Geral

A aula mostra toda a base de funcionamento da IA moderna.

Fluxo principal:

1. dados são coletados;
2. textos são tokenizados;
3. conteúdos viram embeddings;
4. embeddings são armazenados em bancos vetoriais;
5. modelos aprendem padrões;
6. IA responde ou gera conteúdo.

Esses conceitos sustentam:

- chatbots;
- IA Generativa;
- sistemas RAG;
- recomendação;
- busca semântica;
- IA multimodal;
- visão computacional.
