![image](https://github.com/user-attachments/assets/016abac0-40cf-4d0f-ad73-d21986b7dc27)

![image](https://github.com/user-attachments/assets/90769ff2-0680-48e2-a2ae-1596991e5815)

![image](https://github.com/user-attachments/assets/c1746247-719c-4d73-90e3-afe7f602a2d0)

---
## O que o LLM faz em decoding

O modelo, ao decodificar, tenta encontrar a sequência mais provável considerando tanto o caminho de raciocínio (reasoning path)
quanto a resposta final (final answer), dados o problema (problem). Em termos matemáticos:

arg max 𝑃(reasoning path, final answer | problem)

Isso significa que o LLM avalia a probabilidade conjunta de produzir tanto os passos intermediários quanto a resposta final
para um dado problema.

---
## O que queremos

Em vez de priorizar o caminho de raciocínio junto com a resposta final, o objetivo é maximizar diretamente a probabilidade
da resposta final correta, considerando o problema. Isso é representado como:

arg max 𝑃(final answer | problem)

Durante o raciocínio, um LLM pode gerar passos intermediários desnecessários ou errados,
que impactam negativamente na resposta final.
Ao eliminar a dependência do reasoning path, o modelo pode potencialmente melhorar sua precisão.

Esse conceito está diretamente relacionado à ideia de raciocínio sem prompting, usando estratégias como top-k decoding,
onde caminhos de raciocínio alternativos são explorados para melhorar o desempenho em tarefas complexas.

---
## Como calcular P(final answer | problem)

![image](https://github.com/user-attachments/assets/74172358-7809-4283-95f4-d595c9049a1b)

![image](https://github.com/user-attachments/assets/4f9b76ba-0cdc-4438-9f61-0aa2685e0586)

O texto destaca que amostragem (sampling) é o método utilizado para estimar essa soma,
já que é computacionalmente inviável explorar todos os caminhos de raciocínio possíveis diretamente.
