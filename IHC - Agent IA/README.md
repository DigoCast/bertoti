# Agente Inteligente de Análise de Produtos
Um assistente especializado em pesquisa e análise de produtos, desenvolvido para:

🔍 Buscar preços em múltiplas lojas (via SerpAPI)

🤖 Responder naturalmente a perguntas sobre produtos e preços

📊 Analisar pontos fortes e fracos com base em especificações técnicas e avaliações (ainda nao implementado)

💡 Comparar produtos e recomendar a melhor opção por custo-benefício (ainda nao implementado)


## Tecnologias Utilizadas
Python + Ollama (modelo Qwen2.5)

SerpAPI (integração com Google Shopping)

Arquitetura de agentes modulares (tools/prompts)

Gradio (interface web)

### Funcionalidades Chave
- ✅ Pesquisa de preços em tempo real
- ✅ Análise técnica e de reviews
- ✅ Comparativo com produtos similares
- ✅ Respostas formatadas e organizadas

Exemplo de uso: "Analise o iPhone 15 Pro com preços e compare com o Samsung S24"
## Passos para executar
### Crie o ambiente virtual

```bash
python -m venv venv
venv\Scripts\activate     # Windows
```

### Instale as dependencias

```bash
pip install -r requirements.txt
```

### Instale o Ollama localmente e rode o comando 
```bash
ollama pull qwen2.5:3b
```

### Inicie o agente
```bash
python app.py
```