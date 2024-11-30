## Tipos de Prompting

---
### Chain-of-Thought (CoT) Prompting
- CoT significa raciocínio em várias etapas.
- Este método avalia extensivamente prompts que incluem etapas intermediárias, gerando resultados surpreendentes.

![img07](https://github.com/user-attachments/assets/2f9cb719-c4e6-49b0-914d-0f5f59448dd4)

> Exemplo:<br>
> Pergunta: "Quanto é 17 vezes 3?"<br>
> Resposta CoT: "10 vezes 3 é igual a 30.<br> 7 vezes 3 é igual a 21.<br> 30 + 21 é 51."

---
### Least-to-Most Prompting
- Técnica que resolve problemas complexos dividindo-os em partes menores e abordando cada uma de maneira sequencial.

![img08](https://github.com/user-attachments/assets/96bdd127-3a75-4ece-ab0e-e1d00839be25)

> Exemplo:<br>
> Pergunta: "Qual é a área de um triângulo com base 10 e altura 5?"<br>
> Least-to-Most: A fórmula é base x altura / 2. Inserindo os valores para calcular a área, temos (10 x 5 / 2 = 25).

---
### Few-Shot Prompting
- Apresenta ao modelo alguns exemplos representativos no prompt antes de solicitar a resposta.
- Útil para ajustar o contexto sem ajustar os pesos do modelo.

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
**Não importa se você treina um modelo do zero ou utiliza ajustes via prompts, o que realmente faz a diferença são as etapas intermediárias no raciocínio.**

A chave está nos **passos-intermediários**.  

> Observe que o método CoT e o Least-to-Most são muito semelhantes, pois ambos utilizam etapas intermediárias. 
