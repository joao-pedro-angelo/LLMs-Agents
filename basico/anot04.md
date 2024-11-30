# Pense passo a passo

> É possível gerar respostas passo a passo sem usar nenhuma entrada do tipo "pense passo a passo" ou sem exemplos?

A capacidade de responder de maneira passo a passo está intimamente ligada a como o modelo foi treinado
e ao tipo de dados usados em seu treinamento.

Se os LLMs forem treinados usando grandes volumes de dados que incluem explicações detalhadas ou etapas intermediárias no raciocínio,
eles terão maior probabilidade de reproduzir esse comportamento durante a inferência.

Os prompts como "pense passo a passo" são úteis para ajustar o comportamento durante a inferência,
especialmente se o treinamento inicial não priorizou etapas intermediárias.
Esses prompts ajudam o modelo a ativar padrões latentes que incentivam respostas mais detalhadas.

---
# Artigo: CoT without Prompting

![image](https://github.com/user-attachments/assets/0d4f143c-0e13-4dfc-88e5-4923c4b761bd)

![image](https://github.com/user-attachments/assets/e8213287-3d0a-4b18-8929-7d3c3b5c011f)

