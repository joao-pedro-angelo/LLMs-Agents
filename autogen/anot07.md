# Cálculo de Custo de Tokens

O cálculo de custo é importante em sistemas que utilizam modelos de linguagem como o GPT, pois o número de tokens
consumidos pode impactar os custos operacionais, especialmente quando se lida com grandes volumes de texto.

---
## Exemplo em Código

```python
from autogen import AssistantAgent, Conversation

# Criando os agentes
info_agent = AssistantAgent(
    name="InfoAgent",
    system_message="Este agente coleta informações sobre os sintomas do cliente.",
    human_input_mode="always"  # O agente coleta entradas do usuário
)

response_agent = AssistantAgent(
    name="ResponseAgent",
    system_message="Este agente gera uma resposta sobre os sintomas e calcula o custo em tokens.",
    human_input_mode="never"  # Este agente não interage diretamente com o usuário
)

# Função principal para processar a conversa e calcular o custo
def main():
    # Passo 1: O InfoAgent coleta informações do cliente
    user_input = "Estou com dor de cabeça e febre."
    print(f"[InfoAgent] Cliente relatou: {user_input}")
    
    # Passo 2: O ResponseAgent gera uma resposta baseada nos sintomas fornecidos
    response_message = f"Com base nos sintomas de {user_input}, o possível diagnóstico pode ser: gripe ou resfriado."
    print(f"[ResponseAgent] Resposta gerada: {response_message}")

    # Passo 3: Criar a conversa entre os dois agentes
    conversation = Conversation()
    conversation.add_message(info_agent, user_input)
    conversation.add_message(response_agent, response_message)

    # Passo 4: Obter o custo em tokens da conversa
    token_usage = conversation.get_token_usage()  # Usando a função interna para obter o custo em tokens
    print(f"[Token Usage] Tokens usados na conversa: {token_usage['total_tokens']}")
    print(f"[Token Usage] Tokens usados no prompt: {token_usage['prompt_tokens']}")
    print(f"[Token Usage] Tokens usados na resposta: {token_usage['completion_tokens']}")

# Executando o código
main()
```

---
## Sobre Tokens e Custo

O custo dos tokens é uma consideração importante ao usar modelos de linguagem como o GPT.

No exemplo acima, o custo dos tokens é estimado de forma simplificada, assumindo que cada palavra é equivalente
a um token (embora, na prática, o modelo GPT possa usar uma divisão diferente de palavras e tokens).

A OpenAI cobra por token processado, e esse custo pode variar dependendo do modelo de linguagem e do volume de tokens
consumidos.
