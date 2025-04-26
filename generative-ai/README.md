
# Projeto: Construção de um Pipeline RAG com LLM Databricks

## Visão Geral
Neste projeto, desenvolvi um **pipeline completo** de **Geração Aumentada por Recuperação (RAG)** utilizando **Databricks**, **Python**, **Google Colab** e **bancos vetoriais**.

O objetivo foi integrar **IA Generativa** com mecanismos de **recuperação de dados**, aumentando a **precisão**, a **atualização** e a **confiabilidade** das respostas geradas por modelos de linguagem (LLMs).

---

## Objetivos
- Implementar um **pipeline RAG** de ponta a ponta.
- Utilizar **Databricks LLM** para geração de respostas.
- Usar **Web Scraping** para ingestão de dados externos.
- Criar um **banco vetorial** para buscas semânticas.
- Orquestrar a consulta, recuperação e geração de informações atualizadas.

---

## Estrutura do Projeto

### 1. Configuração de Ambiente
Instalação dos pacotes essenciais:  
- `databricks-langchain`, `langchain_milvus`, `langchain-huggingface`, `sentence-transformers`, `beautifulsoup4`, `databricks-cli`, entre outros.

O ambiente foi preparado no **Google Colab** para rápida execução e compatibilidade.

### 2. Configuração de Credenciais
- Variáveis de ambiente para conectar ao **Databricks** via token seguro.

### 3. Extração de Dados
- Utilização do `WebBaseLoader` para capturar conteúdo atualizado de fontes web (ex.: **MIT Sloan Review Brasil**).
- Aplicação de **Text Splitting** para segmentar o conteúdo em pequenos chunks.

### 4. Embeddings
- Carregamento do modelo de embeddings **BAAI/bge-small-en-v1.5** do **HuggingFace**.
- Conversão de textos em vetores numéricos para posterior recuperação semântica.

### 5. Banco de Dados Vetorial
- Implementação do **Milvus** como banco vetorial local.
- Indexação e armazenamento dos embeddings para buscas rápidas.

### 6. Conexão com LLM do Databricks
- Configuração do endpoint **databricks-dbrx-instruct**.
- Limitação controlada de `max_tokens` para respostas otimizadas.

### 7. Construção do Prompt Template
- Definição de um **prompt seguro e direcionado**.
- Garantia de que a IA só responderá com informações baseadas no contexto recuperado.

### 8. Construção do RAG Chain
- Integração entre **retriever**, **prompt** e **LLM** usando LangChain.
- Fluxo de dados totalmente encadeado, passando pela recuperação, formatação, prompting e geração.

### 9. Execução Final
- Interface simples via terminal para perguntas em tempo real.
- Pipeline executando a consulta RAG de ponta a ponta.

---

## Desafios Enfrentados
- **Gerenciamento de dependências** para garantir compatibilidade no ambiente Colab.
- **Tokenização correta** das entradas para evitar erros no modelo LLM.
- **Ajuste do tamanho dos chunks** para maximizar o aproveitamento sem estourar o limite de tokens.
- **Criação manual de índices vetoriais** para otimizar a busca no Milvus local.
- **Tratamento de exceções** na comunicação entre o pipeline e o endpoint Databricks.

---

## Tecnologias Utilizadas
- **Python** (LangChain, HuggingFace, Milvus)
- **Databricks** (ChatDatabricks Endpoint)
- **Google Colab**
- **Milvus** (Banco Vetorial)
- **BeautifulSoup4** (Web Scraping)
- **LangChain Framework** (Orquestração)

---

## Benefícios do Pipeline
- **Atualização Contínua**: Capta dados web em tempo real sem necessidade de retreinar o modelo.
- **Confiabilidade**: Baseia as respostas em fontes verificáveis externas.
- **Personalização**: Pode ser adaptado para diversos domínios (jurídico, saúde, financeiro, etc).

---

## Próximos Passos
- Automatizar ingestão contínua de fontes web.
- Substituir Milvus local por **Milvus Cloud** ou **Pinecone** para escalar a solução.
- Implementar cache inteligente para reduzir latência de resposta.
- Testar variações de prompt engineering para diferentes níveis de formalidade nas respostas.

---

## Contato
Davi Leyendecker  
📧 d.leyendecker@ymail.com
