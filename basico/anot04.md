# Pense passo a passo

> É possível gerar respostas passo a passo sem usar nenhuma entrada do tipo "pense passo a passo" ou sem exemplos?

A capacidade de responder de maneira passo a passo está intimamente ligada a como o modelo foi treinado
e aos tipos de dados usados em seu treinamento.

Se os LLMs forem treinados usando grandes volumes de dados que incluem explicações detalhadas ou etapas intermediárias no raciocínio,
eles terão maior probabilidade de reproduzir esse comportamento durante a inferência.

Os prompts como "pense passo a passo" são úteis para ajustar o comportamento durante a inferência,
especialmente se o treinamento inicial não priorizou etapas intermediárias.

---
# Artigo: CoT without Prompting

![image](https://github.com/user-attachments/assets/0d4f143c-0e13-4dfc-88e5-4923c4b761bd)

![image](https://github.com/user-attachments/assets/e8213287-3d0a-4b18-8929-7d3c3b5c011f)

O artigo **"Chain-of-Thought Reasoning Without Prompting"**, de Xuezhi Wang e Denny Zhou, apresenta uma abordagem inovadora para explorar as capacidades de raciocínio em LLMs sem depender de técnicas de prompting específicas, como few-shot ou CoT.

No artigo discutido, os autores introduzem uma variação no processo de decoding para extrair caminhos de raciocínio passo a passo (CoT) sem usar prompts específicos.

Alterando métodos como top-k decoding, eles observam que os modelos frequentemente geram raciocínios intermediários (CoT) já presentes nas distribuições de probabilidade, mas que podem ser ignorados em abordagens convencionais, como greedy decoding.

---
# Contribuições

#### Eliminação de Prompting manual
- Em vez de construir prompts manuais para induzir o raciocínio em etapas (CoT), os autores propõem alterar o processo de decoding para acessar as habilidades de raciocínio intrínsecas do modelo.

#### Alterações no Decoding
- A abordagem substitui o greedy decoding (que seleciona a sequência de maior probabilidade em cada etapa) pelo uso de top-k decoding.
-  Isso permite explorar sequências alternativas que frequentemente contêm caminhos de raciocínio do tipo CoT.

#### Raciocínio Intrínseco
- Os resultados sugerem que os modelos de linguagem têm raciocínio intrínseco que pode ser extraído ao ajustar o processo de geração de texto, sem a necessidade de exemplos explícitos ou engenharia de prompts.

---
![image](https://github.com/user-attachments/assets/30b66e55-ada6-4945-ae25-c6bf617dba90)

![image](https://github.com/user-attachments/assets/57ba763e-459c-4e36-83fb-752592f4a527)

- Cada linha representa uma resposta gerada pelo modelo com base no processo de decodificação exploratório (usando top-k decoding).
- Algumas respostas são completas e apresentam raciocínio intermediário (Chain-of-Thought, como na linha 6), enquanto outras são respostas diretas (Even. na linha 2 ou Odd. na linha 3).
- As probabilidades indicam o nível de confiança que o modelo atribuiu à resposta durante o processo de decodificação.

- Na linha 6, o modelo fornece uma resposta completa: "Cage nasceu em 1964, um ano par". Esta resposta apresenta um raciocínio detalhado e obteve a maior probabilidade (0.978), indicando que o raciocínio intermediário reforça a confiança do modelo.
- Respostas mais diretas (linhas 2 e 3) ou menos elaboradas têm probabilidades menores.

