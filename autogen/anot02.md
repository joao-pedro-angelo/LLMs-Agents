# AutoGen

> O AutoGen é uma estrutura de conversação multiagente que permite que você crie rapidamente vários agentes com
diferentes funções.

> Seus agentes também podem revisar, criticar e melhorar os resultados do seu trabalho.

![img01](https://github.com/user-attachments/assets/f13dab33-8f7e-4535-a431-148cf33dbe43)

No AutoGen, um agente é uma entidade que pode agir em nome da intenção humana,
enviar mensagens, receber mensagens, executar ações, gerar respostas e interagir com outros agentes.

O AutoGen tem uma classe interna chamada "agente conversável",
que unifica diferentes tipos de agentes na mesma abstração de programação.
Ele vem com muitas funcionalidades internas.

Você pode ligar e desligar cada componente e personalizá-lo para atender às necessidades do seu aplicativo.

---
## Exemplo em Código

```python
# Importando o framework AutoGen
from autogen import ConversableAgent

# Configuração do modelo de linguagem (usando GPT)
llm_config = {
    "model": "gpt-3.5-turbo",  # Modelo escolhido
    "api_key": "SUA_API_KEY",  # Substitua pela sua chave da OpenAI
}

# Criação do agente Cathy
cathy = ConversableAgent(
    name="Cathy",
    llm_config=llm_config,
    system_message="Você é Cathy, uma comediante de stand-up que adora trocadilhos."
)

# Criação do agente Joe
joe = ConversableAgent(
    name="Joe",
    llm_config=llm_config,
    system_message="Você é Joe, um comediante sarcástico que adora piadas secas."
)

# Iniciando a conversa (Joe começa com uma mensagem inicial)
conversation_result = joe.start_chat(
    recipient_agent=cathy,  # Agente que vai responder
    message="Por que o frango atravessou a rua?",
    max_turns=2  # Número máximo de turnos
)

# Exibindo a conversa
for i, turn in enumerate(conversation_result["messages"]):
    role = turn["role"]
    content = turn["content"]
    print(f"Turno {i + 1} - {role}: {content}")

# Calculando e mostrando o uso de tokens
token_usage = conversation_result["usage"]
print("\nResumo do uso de tokens:")
print(f"Tokens de prompt: {token_usage['prompt_tokens']}")
print(f"Tokens de resposta: {token_usage['completion_tokens']}")
print(f"Total de tokens: {token_usage['total_tokens']}")

```
