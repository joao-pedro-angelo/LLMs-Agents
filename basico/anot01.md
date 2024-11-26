## LLM - Definição

![00img](https://github.com/user-attachments/assets/ab14f1b6-8f8b-4a86-af2b-99049c1e586c)

LLM significa large language model, um modelo de aprendizado de máquina que pode executar tarefas de processamento de linguagem natural (NLP).
LLMs são treinados em grandes quantidades de dados de texto para aprender relações estatísticas e prever a próxima palavra ou frase em uma sequência.

Os LLMs geralmente são baseados em arquiteturas de aprendizado profundo, como o Transformer, desenvolvido pelo Google em 2017.
Embora os LLMs tenham a capacidade de entender e gerar linguagem humana, eles também podem herdar vieses e imprecisões dos dados nos quais são treinados.

---
## Etapas da Criação de LLMs

1. **Training (Treinamento)**<br>
O treinamento é a primeira e mais ampla etapa na construção de um LLM.<br>
Objetivo: Ensinar ao modelo os padrões gerais da linguagem.

2. **Fine-Tuning (Ajuste Fino)**<br>
O fine-tuning é uma etapa posterior ao treinamento, onde o modelo pré-treinado é ajustado para aplicações específicas.<br>
Objetivo: Adaptar o modelo para tarefas especializadas ou contextos específicos.

3. **Prompting**<br>
O prompting é uma abordagem leve e não envolve re-treinar o modelo.<br>
Você pode pensar no prompting como uma forma de "conversa" entre o usuário e o modelo.<br>
O objetivo do prompting é orientar o modelo a gerar respostas mais precisas e relevantes.

---
## Agents - Definição

Os agentes LLM são sistemas avançados de IA projetados para criar textos complexos que precisam de raciocínio sequencial. 

![image](https://github.com/user-attachments/assets/d950a0fd-581f-4944-a3e6-fc2fa74fd128)

Agentes LLM operam em ambientes diversos, sãomuito flexíveis. 
Por exemplo, navegando na web e APIs online. Eles podem sentir o ambiente por meio de diferentes tipos de entradas.

---
## Colaboração entre Múltiplos Agentes

A colaboração entre agentes permite a divisão de trabalho para resolver tarefas complexas.

![01img](https://github.com/user-attachments/assets/94c664af-d6ef-4b52-869c-644aa408f0ac)

Agentes não interagem apenas com o ambiente, mas também entre si, o que aumenta a eficiência e permite soluções colaborativas.

Esse fluxo de trabalho facilita:
- Decomposição de tarefas;
- Alocação de subtarefas para módulos especializados;
- Colaboração em projetos.

---
### "AI deve ser capaz de aprender com apenas alguns exemplos, como os humanos normalmente fazem" — Denny Zhou

O que falta no aprendizado de máquina (ML)?
- Reasoning (raciocínio).
- Humanos conseguem aprender com poucos exemplos porque conseguem raciocinar.

![02img](https://github.com/user-attachments/assets/a8e60d93-d66e-42f9-9953-068577284224)

- Para um humano, resolver problemas como o ilustrado na imagem acima é fácil.
- Para máquinas, problemas simples como esse exigem enormes quantidades de dados e ainda assim não garantem 100% de precisão.

---
## Estratégias de Melhoria de LLMs - Tipos de Prompting

#### Chain-of-Thought (CoT) Prompting
- CoT significa raciocínio em várias etapas.
- Este método avalia extensivamente prompts que incluem etapas intermediárias, gerando resultados surpreendentes.
- Não importa se você treina um modelo do zero ou utiliza ajustes via prompts, o que realmente faz a diferença são as etapas intermediárias no raciocínio.

![img07](https://github.com/user-attachments/assets/2f9cb719-c4e6-49b0-914d-0f5f59448dd4)

#### Least-to-Most Prompting
- Técnica que resolve problemas complexos dividindo-os em partes menores e abordando cada uma de maneira sequencial.

![img08](https://github.com/user-attachments/assets/96bdd127-3a75-4ece-ab0e-e1d00839be25)

A chave está nos **passos-intermediários**.  