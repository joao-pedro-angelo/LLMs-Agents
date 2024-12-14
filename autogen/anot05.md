# Conectar AutoGen com LLM

> O AutoGen é uma estrutura projetada para facilitar a construção e orquestração de sistemas multiagentes
> que se comunicam entre si usando Large Language Models (LLMs).<br><br>
> O GPT, como o GPT-4 da OpenAI, é um exemplo de LLM que pode ser integrado ao AutoGen para que os agentes
> gerem e troquem respostas.

---
## Integração entre o AutoGen e o GPT

O AutoGen serve como uma camada intermediária entre o GPT e a aplicação que você está desenvolvendo.

Para isso, ele utiliza a API do GPT, como as fornecidas pela OpenAI, permitindo que os agentes façam chamadas para o
modelo de linguagem.

**API KEY**: Para usar o GPT, você precisa de uma chave válida fornecida pela OpenAI.

**Configuração do Modelo**: O AutoGen permite configurar parâmetros como o modelo específico ("gpt-4" ou "gpt-3.5-turbo")
e limites como temperatura e tokens máximos.

---
## Exemplo em Código

```python
from autogen import ConversableAgent

# Configuração do GPT
llm_config = {
    "model": "gpt-4",  # Ou "gpt-3.5-turbo"
    "api_key": "SUA_API_KEY",  # Substitua pela sua chave da OpenAI
}

# Criação de um agente conectado ao GPT
agent = ConversableAgent(
    name="meu_agente",
    llm_config=llm_config,
    system_message="Você é um assistente que responde de forma clara e detalhada."
)

# Gerar uma resposta usando o agente
response = agent.generate_reply(
    messages=[{"role": "user", "content": "Explique os benefícios da prática de exercícios físicos."}]
)
print(response["content"])
```

---
## Fluxo da Comunicação

**1. Input do Usuário**: O usuário envia uma mensagem para o agente.

**2. Chamada da API**: O AutoGen transmite essa mensagem para o modelo GPT por meio da API da OpenAI.

**3. Resposta do GPT**: O GPT gera uma resposta com base no input e nos parâmetros configurados.

**4. Resposta ao Usuário**: O AutoGen formata e retorna a resposta ao agente ou diretamente ao usuário.
