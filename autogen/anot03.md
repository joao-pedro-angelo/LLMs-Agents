# Chats Sequenciais e Integração de Clientes

> Você criará uma sequência de tarefas entre vários agentes,
que colaboram para fornecer uma experiência de integração do cliente para um produto.

---
## Teoria

![img01](https://github.com/user-attachments/assets/c6dffbc3-de71-4191-88df-7e357296fd12)<br>
Vamos considerar um cenário de integração de clientes.
Neste cenário, um procedimento típico é primeiro coletar algumas informações do cliente e então se envolver com o cliente
com base nas informações coletadas.

Com isso em mente, é uma boa ideia decompor esta tarefa de integração do cliente em três subtarefas,
incluindo coleta de informações, pesquisa de interesse e engajamento do cliente.

![img02](https://github.com/user-attachments/assets/f80245a5-53da-4cb8-b673-b945bcdaa043)<br>

---
## Exemplo em Código

```python
from autogen import ConversableAgent

# Configuração do modelo de linguagem
llm_config = {
    "model": "gpt-3.5-turbo",  # Modelo LLM
    "api_key": "SUA_API_KEY",  # Substitua pela sua chave
}

# Criando o agente cliente
cliente_agent = ConversableAgent(
    name="ClienteAgent",
    llm_config=llm_config,
    system_message="Você é um agente amigável que entrevista clientes para entender seus gostos musicais.",
    accept_user_input="always"  # Este agente sempre aceita entradas do usuário
)

# Criando o agente sugeridor
sugeridor_agent = ConversableAgent(
    name="SugeridorAgent",
    llm_config=llm_config,
    system_message="Você é um especialista musical que sugere músicas com base nos gostos fornecidos pelo ClienteAgent.",
    accept_user_input="never"  # Este agente não interage diretamente com o usuário
)

# Criando o agente crítico
critico_agent = ConversableAgent(
    name="CriticoAgent",
    llm_config=llm_config,
    system_message="Você é um crítico musical rigoroso que avalia as sugestões fornecidas pelo SugeridorAgent.",
    accept_user_input="never"  # Este agente não interage diretamente com o usuário
)

# Passo 1: ClienteAgent inicia a conversa com o cliente
# Durante a execução, o AutoGen aguarda a entrada do usuário.
# Essa entrada é registrada no objeto de resposta, que é retornado pelo método start_chat e armazenado em cliente_resposta
cliente_resposta = cliente_agent.start_chat(
    recipient_agent=None,
    message="Olá! Quais são os seus gêneros musicais favoritos?",
    max_turns=2  # Máximo de 2 turnos para coletar informações do cliente
)

# Exibindo a interação com o cliente
print("Interação com o cliente:")
for msg in cliente_resposta["messages"]:
    print(f"{msg['role']}: {msg['content']}")

# Passo 2: SugeridorAgent analisa os dados coletados e sugere músicas
preferencias_cliente = cliente_resposta["messages"][-1]["content"]  # Obtendo a última resposta do cliente
sugestoes_resposta = sugeridor_agent.start_chat(
    recipient_agent=None,
    message=f"Baseado nas preferências musicais: {preferencias_cliente}, sugira músicas apropriadas.",
    max_turns=1  # Apenas uma interação
)

# Exibindo as sugestões de músicas
print("\nSugestões de músicas:")
for msg in sugestoes_resposta["messages"]:
    print(f"{msg['role']}: {msg['content']}")

# Passo 3: CriticoAgent avalia as sugestões
sugestoes = sugestoes_resposta["messages"][-1]["content"]  # Pegando a última resposta
critica_resposta = critico_agent.start_chat(
    recipient_agent=None,
    message=f"As sugestões foram: {sugestoes}. Por favor, avalie e melhore se necessário.",
    max_turns=1  # Apenas uma interação
)

# Exibindo as críticas e melhorias
print("\nCríticas e melhorias:")
for msg in critica_resposta["messages"]:
    print(f"{msg['role']}: {msg['content']}")
```

