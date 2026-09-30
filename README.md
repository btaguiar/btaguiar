# Bruno Aguiar

**AI Engineer** · São Paulo

Todo dia às 9h40 um agente meu abre as vagas novas de AI Engineer no LinkedIn, lê a descrição inteira de cada uma, extrai as skills exigidas e pontua o fit contra o meu perfil. Dez minutos antes, outro já publicou a newsletter do dia em [olhonomundo.com.br](https://olhonomundo.com.br).

Nenhum dos dois me pede nada. É isso que eu construo: sistemas de agentes que rodam sozinhos em produção, e que falham de forma visível quando falham.

Tenho uma regra em todos os projetos: nenhum número no README sem um eval que o reproduza. O LLM extrai, explica e redige; quem decide o número é modelo, regra ou SQL que eu consigo testar.

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

### [pme-risk](https://github.com/btaguiar/pme-risk) · [demo](https://pme-risk-demo.web.app)

`BigQuery ML` `Gemini` `FastAPI` `Cloud Run`

Laudo de risco de crédito para PMEs brasileiras. Um modelo em BigQuery ML calcula a probabilidade de inadimplência; agentes extraem o pedido em português, conferem o CNPJ na Receita e redigem o laudo; um analista aprova ou rejeita antes de ele valer.

- O LLM não tem permissão para mexer na PD. Um juiz determinístico, sem LLM, confere se cada número do laudo bate com o pedido ou com o modelo: 99,9% de fidedignidade.
- Extração com F1 de 0,99 e 100% de recusa correta fora de escopo, num golden set de 80 pedidos.
- Achei um vazamento na base da SBA: o prazo do empréstimo é regravado depois do calote e carrega o desfecho. Tirei a feature e um teste impede que ela volte, mesmo custando AUC.
- O multi-agente só ficou porque venceu o baseline de chamada única na métrica que importava.

### [grifo](https://github.com/btaguiar/grifo) · [demo](https://grifo-one.vercel.app)

`RAG` `Qdrant` `Reranker` `Pydantic` `Python`

Assistente de dúvidas para cursos que responde só com o material oficial e cita módulo, aula e o minuto do vídeo, com o nome de quem fala. Quando a resposta não está no material, recusa: 11 de 11 recusas corretas. O juiz de alucinação foi calibrado contra rótulos humanos (κ = 0,905) antes de eu confiar no 0% que ele deu.

### [quimera](https://github.com/btaguiar/quimera) · [demo](https://quimera-leads.web.app)

`Gemini` `Embeddings` `BigQuery` `Cloud Run` `React`

Transforma um pedido em português ("clínicas odontológicas abertas há mais de 2 anos em Santo André") numa lista ranqueada de empresas do cadastro público de CNPJ.

- O LLM nunca escreve SQL: ele só preenche um schema de filtros, e a consulta é parametrizada e minha.
- Toda consulta tem teto de custo. Materializei os 27,8 milhões de estabelecimentos ativos numa tabela particionada, e o pedido caiu de ~13 GB para 33–250 MB.
- Avaliado em 10.000 pedidos sintéticos com gabarito gerado por template, nunca por LLM: 92% dos casos 100% corretos e 100% de recusa em pedido de dado pessoal.

## Em construção

### [pauta](https://github.com/btaguiar/pauta)

`LangGraph` `FastAPI` `PostgreSQL` `Python`

Briefings analíticos multi-agente: supervisor → pesquisa → análise → crítica → redação, com humano no meio e orçamento de tokens. O CI sobe um Postgres, mata o processo com `kill()` no meio da run e prova que ela retoma do checkpoint em outro processo.

## Stack

| | |
|---|---|
| **LLM e agentes** | LangGraph · LangChain · CrewAI · Claude · Gemini · GLM · OpenAI · RAG · Evals · Structured output |
| **Dados e recuperação** | BigQuery · PostgreSQL · pgvector · Qdrant · ChromaDB · Redis · SQL |
| **Backend e infra** | Python · FastAPI · Docker · GCP (Cloud Run, Vertex AI) · AWS · systemd · GitHub Actions |
| **ML** | BigQuery ML · Scikit-learn · XGBoost · LightGBM · Pandas · NumPy |
| **Front** | Next.js · React · TypeScript · Tailwind |

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
