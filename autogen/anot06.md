# Tools

Aqui temos um exemplo mais complexo que demonstra como usar ferramentas (tools) no AutoGen.

Neste exemplo, criaremos um sistema multi-agente onde:

1. Um agente coleta dados sobre um problema de saúde relatado por um usuário.<br>
2. Outro agente realiza pesquisas online para encontrar possíveis causas ou tratamentos usando uma ferramenta de busca.<br>
3. Um terceiro agente valida as informações encontradas, usando lógica para avaliar sua relevância e confiabilidade.

--- 
## Exemplo

```python
from autogen import AssistantAgent, Tool, Conversation

# Definição de uma ferramenta para buscar informações na web
class WebSearchTool(Tool):
    def __init__(self):
        super().__init__(name="WebSearch", description="Faz pesquisas na internet para encontrar informações relevantes.")
    
    def run(self, query):
        # Simulação de uma pesquisa (poderia integrar com uma API como Google ou Bing)
        print(f"[WebSearchTool] Executando busca para: {query}")
        # Retornando um exemplo fictício de resultado
        return f"Resultados da pesquisa para '{query}': 1) Causa A, 2) Causa B, 3) Tratamento recomendado C."

# Criação da ferramenta
web_search_tool = WebSearchTool()

# Definição dos agentes
# Agente 1: Coleta informações do cliente
info_agent = AssistantAgent(
    name="InfoAgent",
    system_message="Você é um especialista em saúde, sua tarefa é coletar detalhes sobre sintomas e problemas relatados.",
    human_input_mode="always"  # Recebe entradas do usuário
)

# Agente 2: Pesquisa informações
search_agent = AssistantAgent(
    name="SearchAgent",
    system_message="Você é um assistente que pesquisa informações de saúde online. Use a ferramenta de busca.",
    tools=[web_search_tool],  # Associa a ferramenta ao agente
    human_input_mode="never"  # Este agente não interage diretamente com o usuário
)

# Agente 3: Avalia a relevância dos resultados
validator_agent = AssistantAgent(
    name="ValidatorAgent",
    system_message="Você é um crítico especializado que avalia a relevância e a confiabilidade das informações fornecidas.",
    human_input_mode="never"  # Não interage diretamente com o usuário
)

# Simulação de fluxo de trabalho
def main():
    # Passo 1: InfoAgent coleta dados do cliente
    user_input = "Estou sentindo dores de cabeça frequentes e náuseas. O que pode estar causando isso?"
    print(f"[InfoAgent] Cliente relatou: {user_input}")
    
    # Passo 2: SearchAgent pesquisa informações
    search_query = f"Possíveis causas e tratamentos para: {user_input}"
    search_result = search_agent.start_chat(
        recipient_agent=None, 
        message=f"Pesquise sobre: {search_query}",
        max_turns=1
    )
    
    # O resultado simulado seria:
    search_result = web_search_tool.run(search_query)  # Usando a ferramenta de busca
    print(f"[SearchAgent] Resultados encontrados: {search_result}")
    
    # Passo 3: ValidatorAgent avalia as informações
    validator_input = f"Analise a relevância dos seguintes resultados: {search_result}"
    validation_result = validator_agent.start_chat(
        recipient_agent=None, 
        message=validator_input, 
        max_turns=1
    )
    # Simulando a validação
    validation_result = "Os resultados 1 e 3 são relevantes, o resultado 2 é irrelevante."
    print(f"[ValidatorAgent] Avaliação: {validation_result}")

# Execução
main()
```

---
## Explicação do Código

### Ferramenta (Tool):
O **WebSearchTool** é uma simulação de uma ferramenta que faz pesquisas online.

Integra-se ao agente SearchAgent, permitindo que ele realize pesquisas sem intervenção humana.

---
### Agentes:
**InfoAgent**: Interage com o usuário para coletar informações iniciais.<br>

**SearchAgent**: Usa a ferramenta WebSearchTool para pesquisar soluções ou causas.<br>

**ValidatorAgent**: Analisa os resultados da pesquisa e avalia sua qualidade.

---
### Fluxo de Trabalho:
O **usuário** fornece sintomas para o **InfoAgent**.

O **SearchAgent** usa a ferramenta para pesquisar soluções baseadas nos sintomas.

O **ValidatorAgent** revisa os resultados e oferece uma crítica construtiva.
