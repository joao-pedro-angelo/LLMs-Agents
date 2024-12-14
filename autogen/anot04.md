# Reflection - Reflexão

> O processo de Reflection é uma estratégia que envolve agentes analisando suas próprias saídas,
> para melhorar a qualidade e precisão das respostas geradas.

![image](https://github.com/user-attachments/assets/8ad1c98d-cf6d-400b-87b5-d563d529bf40)

---
## O significado de "Reflection"

No contexto do AutoGen e de sistemas multiagentes, o termo "reflection" se refere a "refletir no sentido de 
pensar sobre ou analisar criticamente alguma coisa" e não no sentido físico de desvio de direção, como em óptica ou física.

Refletir é um processo cognitivo em que um agente analisa uma saída, resposta ou comportamento anterior, identifica problemas,
inconsistências ou melhorias, e sugere ajustes.

O objetivo é aprimorar a qualidade da resposta ou do raciocínio, criando um ciclo de aprendizado e iteração entre agentes.

Esse processo muitas vezes é feito através de agentes que assumem diferentes papéis, como "gerador" e "crítico",
onde o crítico oferece feedback e sugestões para o gerador.

---
## Exemplo em Código

```python
from autogen import ConversableAgent

# Configuração do modelo de linguagem (utilizando OpenAI GPT como exemplo)
llm_config = {
    "model": "gpt-4",
    "api_key": "YOUR_OPENAI_API_KEY",  # Substitua pela sua chave API
}

# Criação do agente Writer (Escritor) que gera a resposta inicial
writer = ConversableAgent(
    name="WriterAgent",
    llm_config=llm_config,
    system_message="Você é um agente responsável por gerar uma resposta inicial para uma pergunta."
)

# Criação do agente Critic (Crítico) que reflete sobre a resposta inicial
critic = ConversableAgent(
    name="CriticAgent",
    llm_config=llm_config,
    system_message="Você é um agente crítico. Seu trabalho é refletir sobre a resposta do WriterAgent, identificar problemas e sugerir melhorias."
)

# Pergunta inicial feita pelo usuário
user_question = "Explique o que é inteligência artificial em poucas palavras."

# Passo 1: O WriterAgent gera a resposta inicial
writer_reply = writer.generate_reply(messages=[{"role": "user", "content": user_question}])
print("Resposta Inicial do WriterAgent:")
print(writer_reply)

# Passo 2: O CriticAgent reflete sobre a resposta gerada pelo WriterAgent
critic_reply = critic.generate_reply(messages=[
    {"role": "user", "content": f"Avalie a seguinte resposta: '{writer_reply}'. Identifique problemas e sugira melhorias."}
])
print("\nCrítica do CriticAgent:")
print(critic_reply)

# Passo 3: O WriterAgent ajusta a resposta com base na crítica
writer_improved_reply = writer.generate_reply(messages=[
    {"role": "user", "content": f"Melhore a resposta original '{writer_reply}' com base na crítica: '{critic_reply}'."}
])
print("\nResposta Melhorada do WriterAgent:")
print(writer_improved_reply)

```

---
## Automatizar a Reflexão

```python
from autogen import ConversableAgent, UserProxyAgent

# Configuração do modelo
llm_config = {"model": "gpt-4", "api_key": "SUA_API_KEY"}

# Definir os agentes
writer = ConversableAgent(
    name="writer",
    llm_config=llm_config,
    system_message="Você é um gerador de conteúdo que escreve respostas baseadas em instruções do usuário."
)

critic = ConversableAgent(
    name="critic",
    llm_config=llm_config,
    system_message="Você é um crítico que analisa a resposta e sugere melhorias para torná-la mais clara e precisa."
)

controller = UserProxyAgent(
    name="controller",
    code_execution_config={"use_docker": False},
)

# Orquestrar o fluxo entre writer e critic
def auto_feedback_loop(prompt, max_iterations=3):
    iteration = 0
    current_response = None

    while iteration < max_iterations:
        iteration += 1
        print(f"\n### Iteração {iteration} ###")

        # Writer gera a resposta
        response = writer.generate_reply(messages=[{"role": "user", "content": prompt}])
        print(f"Writer: {response['content']}")

        # Critic analisa e dá feedback
        feedback = critic.generate_reply(
            messages=[{"role": "user", "content": f"Analise a seguinte resposta: '{response['content']}' e sugira melhorias."}]
        )
        print(f"Critic: {feedback['content']}")

        # Writer ajusta a resposta com base no feedback
        prompt = f"Resposta original: '{response['content']}'. Feedback: '{feedback['content']}'. Agora ajuste a resposta para aplicar as melhorias sugeridas."

        current_response = response['content']

    return current_response

# Executar o loop
final_output = auto_feedback_loop("Escreva um texto sobre os benefícios da prática de exercícios físicos.", max_iterations=2)
print("\n### Resposta Final ###")
print(final_output)

```
