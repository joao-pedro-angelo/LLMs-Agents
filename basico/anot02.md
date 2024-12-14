## Tipos de Prompting

> Engenharia de Prompting é a prática de criar e otimizar instruções para guiar modelos de inteligência artificial (IA) a gerar respostas relevantes e precisas.<br><br>
> Existem tipos específicos de prompting. 

---
### Chain-of-Thought (CoT) e Least-to-Most
- CoT significa raciocínio em várias etapas.
- Este método avalia prompts que incluem etapas intermediárias, gerando resultados surpreendentes.
- Least-to-Most divide o problema em partes independentes, mais fáceis e resolve o problema todo de forma incremental, em partes.
- Observe que o método CoT e o Least-to-Most são muito semelhantes, pois ambos utilizam etapas intermediárias. 

![image](https://github.com/user-attachments/assets/4e3afe61-9afa-483c-bab6-fdc1839d8d89)

> Exemplo:<br>
> Pergunta: "Quanto é 17 vezes 3?"<br>
> Resposta CoT: "10 vezes 3 é igual a 30.<br> 7 vezes 3 é igual a 21.<br> 30 + 21 é 51."

---
### Few-Shot Prompting
- Apresenta ao modelo alguns exemplos representativos no prompt antes de solicitar a resposta.
- Útil para ajustar o contexto sem modificar o modelo.

> Exemplo:<br>
> Pergunta: "Sabendo que cat significa gato, qual o significado de apple?<br>
> Resposta few-shot: "maçã".

---
### Zero-Shot Prompting
- O modelo resolve a tarefa diretamente sem exemplos prévios no prompt.
- Baseia-se no conhecimento geral e no contexto implícito.

> Exemplo:<br>
> Pergunta: "Qual é a capital da França?"<br>
> Resposta Zero-Shot: "A capital da França é Paris."

---
### Role-Playing Prompting
- O modelo é colocado em um "papel" ou "persona" para realizar uma tarefa específica.

> Exemplo: "Imagine que você é um professor de matemática. Explique o teorema de Pitágoras."

---
