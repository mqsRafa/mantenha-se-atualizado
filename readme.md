# 📰 Sistema Multiagente de Notícias com Gemini e Google ADK

Um projeto de demonstração utilizando a biblioteca Google ADK e o modelo Gemini para buscar, filtrar e resumir notícias relevantes com base na localização do usuário, empregando um sistema de múltiplos agentes de Inteligência Artificial.

## ✨ Sobre o Projeto

Este projeto exemplifica o poder dos sistemas multiagente baseados em IA. Ao invés de um único modelo tentando realizar todas as tarefas, dividimos o trabalho entre agentes especializados, cada um focado em uma parte específica do processo: buscar informações, curar o conteúdo e apresentá-lo de forma acessível.

A ideia é simular um pequeno fluxo de trabalho jornalístico automatizado, onde a notícia é primeiramente encontrada, depois avaliada por relevância e, por fim, "traduzida" para uma linguagem simples para o consumidor final.

## 🚀 Funcionalidades

* **Entrada Localizada:** O usuário informa sua cidade como ponto de partida.
* **Busca Abrangente:** O Agente 1 busca notícias relevantes da última semana em três níveis:
    * Local (sua cidade)
    * Nacional (o país da sua cidade)
    * Global (notícias de destaque mundial)
* **Curadoria Inteligente:** O Agente 2, atuando como um "editor", analisa os links encontrados e seleciona as notícias mais relevantes e urgentes (considerando títulos e snippets).
* **Resumo Simplificado:** O Agente 3 recebe as notícias selecionadas e as explica de forma clara e concisa, facilitando a compreensão pelo usuário.

## 🛠️ Tecnologias Utilizadas

* **Google Colab:** Ambiente de desenvolvimento baseado em nuvem.
* **Google AI SDK (google-genai):** Biblioteca para interagir com os modelos Gemini.
* **Google ADK (google-adk):** Framework para construção de sistemas multiagente.
* **Google Gemini:** Modelo de linguagem grande utilizado pelos agentes.
* **Google Search Tool:** Ferramenta utilizada pelo Agente 1 e Agente 2 para realizar buscas na web.
* **Python:** Linguagem de programação principal.

## 🚦 Como Configurar e Executar

1.  **Pré-requisitos:**
    * Uma Conta Google com acesso ao Google Colab.
    * Uma chave de API válida para o Google Gemini. Você pode obtê-la no [Google AI Studio](https://aistudio.google.com/).

2.  **Abrir no Google Colab:**
    * Crie um novo Notebook no Google Colab.
    * Copie e cole o código do notebook (disponível no arquivo `.ipynb` ou o código gerado anteriormente) nas células do Colab.

3.  **Configurar a API Key:**
    * No Google Colab, clique no ícone de chave (Secrets) no menu lateral esquerdo.
    * Clique em `+ New secret`.
    * No campo `Name`, digite `GOOGLE_API_KEY`.
    * No campo `Value`, cole a sua chave de API do Google Gemini.
    * Certifique-se de que a opção "Notebook access" esteja ativada para este secret.

4.  **Instalar Dependências:**
    * Execute a primeira célula do notebook que contém `%pip -q install google-genai google-adk`.

5.  **Executar o Notebook:**
    * Execute as células do notebook sequencialmente.
    * Quando solicitado, digite o nome da sua cidade e do país.
    * Observe a execução de cada agente e o resultado final com as notícias resumidas.

## 💡 Como Funciona (Visão Geral)

O sistema opera em um fluxo linear:

```mermaid
graph LR
    A[Usuário fornece Cidade/País] --> B(Agente 1: Buscador de Notícias)
    B --> C(Agente 2: Especialista em Jornalismo)
    C --> D(Agente 3: Explicador Simples)
    D --> E[Exibição do Resumo para o Usuário]

    B -- Utiliza --> F(Google Search Tool)
    C -- Pode utilizar --> F
