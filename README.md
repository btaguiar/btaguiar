# Bruno Aguiar

**AI Engineer** · São Paulo

Todo dia às 9h40 um agente meu abre as vagas novas de AI Engineer no LinkedIn, lê a descrição inteira de cada uma, extrai as skills exigidas e pontua o fit contra o meu perfil. Dez minutos antes, outro já publicou a newsletter do dia em [olhonomundo.com.br](https://olhonomundo.com.br).

Nenhum dos dois me pede nada. É isso que eu construo: sistemas de agentes que rodam sozinhos em produção, e que falham de forma visível quando falham.

## No ar

### Cortex

27 agentes em Python, mais de 40 jobs agendados, 1.950 testes. Roda numa VPS sob systemd, sem ninguém olhando.

- Newsletter diária em dois passos: um modelo monta a estrutura, outro escreve a narrativa. Separar as duas coisas cortou alucinação e deixou o texto em português puro.
- O agente de vagas abre cada vaga nova, extrai as skills com vocabulário determinístico, sem gastar LLM onde regra resolve, e só então usa uma chamada de modelo para pontuar o fit.
- Provedor de LLM tem fallback em cadeia. Fonte desligada por política fica atrás de kill-switch, com o código intacto: desligar não é apagar.
- Quando o túnel de coleta cai, o job falha rápido e com motivo, em vez de subir um browser sem sessão e queimar meia hora em timeout.

Espelho público, defasado, porque a produção é privada: [cortex-multi-agent](https://github.com/btaguiar/cortex-multi-agent)

### [olhonomundo.com.br](https://olhonomundo.com.br)

Portal em Next.js que transforma cada newsletter do Cortex em matérias navegáveis, com categorização por tópico e foto escolhida pelo assunto da matéria. O conteúdo é gerado pelo pipeline; o site só publica.

## Em construção

### [pauta](https://github.com/btaguiar/pauta)

`LangGraph` `FastAPI` `pgvector` `Python`

Briefings analíticos multi-agente: supervisor → pesquisa → análise → crítica → redação, com humano no meio e streaming por SSE. O smoke test da demo e do stream roda no CI a cada mudança.

### [grifo](https://github.com/btaguiar/grifo)

`RAG` `Qdrant` `Reranker` `Python`

Assistente de dúvidas para cursos que responde só com o material oficial e cita módulo, aula e minuto. Quando a resposta não está no material, ele diz que não sabe em vez de inventar.

## Stack

| | |
|---|---|
| **LLM e agentes** | LangChain · LangGraph · CrewAI · Claude · GLM · OpenAI · RAG · Prompt Engineering · Fine-tuning |
| **Dados e recuperação** | PostgreSQL · pgvector · Qdrant · ChromaDB · Redis · SQL |
| **Backend e infra** | Python · FastAPI · Docker · AWS · systemd · Git |
| **ML** | Scikit-learn · XGBoost · LightGBM · Pandas · NumPy |
| **Front** | Next.js · TypeScript · Tailwind |

## Outros repositórios

**[BRMP](https://github.com/btaguiar/BRMP-Brazilian-Match-Prediction)**: previsão de resultados do Brasileirão com validação temporal e modelos calibrados.

**[SCS](https://github.com/btaguiar/SCS-Analise-Performance-360)**: análise multivariada de performance em Python, com ROI médio de 1.645% e CPA mínimo de R$ 126.

**[BK-DEP](https://github.com/btaguiar/BK_DEP_Otimiza-o_de_Convers-o)**: modelagem bayesiana de conversão, com 30% de redução no CPA.

## Formação

**Tecnólogo em Inteligência Artificial**, em andamento (2025-2027)

**FAPCOM**: bacharelado em Rádio, TV e Comunicação Digital (2014-2017)

## Contato

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Bruno%20Aguiar-0077B5?style=flat&logo=linkedin)](https://www.linkedin.com/in/bruno-aguiar-ai-engineer/)

bruno.aguiarsp@outlook.com
