# 📈 Investimentos - Intelligent Assistant

> **Democratizando o acesso a dados estratégicos de investimento através de Inteligência Artificial Generativa.**

## 💡 O Conceito
Uma empresa de investimentos lida diariamente com dois tipos críticos de informação que não conversam entre si:
1.  **Regras e Estratégias (Não-Estruturado):** Documentos PDF com políticas de conformidade, teses de investimento e sugestões de alocação.
2.  **Dados de Mercado (Estruturado):** Bancos de dados com histórico de cotações (ex: Bitcoin/Cripto), volumes e transações.

O problema tradicional é que para cruzar esses dados, um analista precisa ler 50 páginas de um PDF e depois pedir para um programador fazer uma consulta SQL no banco.

**Este projeto resolve isso criando um Cérebro Digital Unificado.**
Através de uma interface de chat simples, consultores e gestores podem fazer perguntas em linguagem natural tanto sobre as **regras da casa** quanto sobre os **números do mercado**.

---

## 🚀 Funcionalidades (Módulos)

O sistema opera com uma lógica de **"Workflow Determinístico"** (Human-in-the-Loop). O usuário seleciona o contexto desejado para garantir precisão máxima:

### 1. 📜 Consultor de Normas (RAG)
* **Fonte de Dados:** Documentos internos (PDFs de Política de Investimentos e Sugestões).
* **O que faz:** Lê, interpreta e cita as regras da empresa.
* **Exemplos de Perguntas:**
    * *"Qual é a exposição máxima permitida em criptoativos segundo a política?"*
    * *"Quais são as sugestões de investimento para perfil conservador?"*
* **Tecnologia:** Busca Vetorial (ChromaDB) para encontrar o parágrafo exato e LLM para gerar a resposta.

### 2. 📊 Analista de Bitcoin (SQL Agent)
* **Fonte de Dados:** Banco de dados PostgresSQL hospedado no Supabase com histórico de Bitcoin.
* **O que faz:** Transforma perguntas em código SQL, executa no banco e explica o resultado.
* **Exemplos de Perguntas:**
    * *"Qual foi o maior preço do Bitcoin em 2023?"*
    * *"Qual a média de volume de negociação nos finais de semana?"*
* **Tecnologia:** Agente Autônomo do Groq (llama-3.3-70b-versatile) que entende a estrutura das tabelas e escreve queries complexas sozinho.

---

## 🛠️ Arquitetura Técnica

Este projeto segue uma arquitetura **"Best of Breed"** (Melhor ferramenta para cada função), otimizada para custo zero e alta performance.

### O Cérebro Dividido
Para evitar custos elevados e latência, dividimos as responsabilidades da IA:
* **Raciocínio & Resposta (Groq + Llama 3):** Usamos a infraestrutura da Groq (LPUs) rodando o modelo `Llama-3.3-70b`. Ele é responsável por escrever os textos e gerar os códigos SQL com velocidade quase instantânea.
* **Memória Semântica (Google Gemini):** Usamos a API do Google (`text-embedding-004`) exclusivamente para gerar os *embeddings* (a representação matemática) dos textos, garantindo alta qualidade na busca vetorial.

### Stack Tecnológica
* **Linguagem:** Python 3.10+
* **Orquestração:** LangChain (LCEL & Agents)
* **Interface:** Streamlit
* **Banco Vetorial:** ChromaDB (Persistente)
* **Banco Relacional:** PostgreSQL (Dados de Bitcoin)
* **Observabilidade:** LangSmith (Rastreamento de tokens e latência)

---

## ⚙️ Instalação e Configuração

### Pré-requisitos
* Python instalado.
* Uma instância PostgreSQL com os dados de Bitcoin carregados.
* Chaves de API (Groq, Google AI Studio e LangSmith).
