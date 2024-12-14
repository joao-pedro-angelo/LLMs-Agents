# Agentes IA

> O texto abaixo foi retirado da palestra: https://youtu.be/OOdtmCMSOo4

---
## O que são Agentes?

Agentes são entidades autônomas que percebem o ambiente ao seu redor, processam informações e executam ações.

Um agente é, de forma abstrata, qualquer sistema que:

1. **Percebe seu ambiente**: Essa percepção é feita por meio de sensores, seja em hardware (ex.: câmeras, microfones) ou software (ex.: análise de dados, textos, imagens).

2. **Processa informações**: O agente usa um mecanismo de decisão, que pode envolver lógica, aprendizado de máquina, heurísticas ou outras formas de computação, para escolher as ações mais adequadas.

3. **Age no ambiente**: Através de atuadores (físicos ou virtuais), ele executa as ações que impactam o ambiente. Exemplos incluem enviar comandos, alterar estados de sistemas ou fornecer respostas.

---
## Como serão as futuras aplicações de IA?
![img01](https://github.com/user-attachments/assets/8e97798e-ee89-4513-9b49-1bbdf15d9224)

A partir de 2022, vimos o enorme poder dos modelos de linguagem e de outros modelos generativos.

Hoje em dia, as novas técnicas ultrapassaram um limite que nos permite pensar em aplicações mais criativas e níveis mais avançados de capacidades de IA.

Então, o que vem a seguir? Qual é a melhor forma de aproveitar essas técnicas de IA?

A partir do início do ano passado, começamos a pensar nessas questões e fizemos várias apostas técnicas ao longo do caminho.

A mais importante delas foi a crença de que as futuras aplicações de IA podem ser agentes. Esses agentes seriam uma nova maneira de os humanos interagirem com o mundo digital, ajudando-nos a executar tarefas mais complexas e atingindo níveis mais altos de complexidade.

Naquela época, muitas pessoas ainda duvidavam se os agentes seriam uma ideia viável.

Mas, com o tempo, estamos vendo cada vez mais confirmações e evidências. 

Por exemplo, no início deste ano (2024), um artigo publicado pela Berkeley discutiu como estamos observando uma mudança de sistemas simples baseados em modelos de linguagem para a construção de sistemas de IA mais complexos.

---
## Aplicações dos Agentes IA
![img02](https://github.com/user-attachments/assets/33519650-3af3-486d-8ea8-9b16e3ebf089)

Se pensarmos em exemplos de agentes, notamos que a construção de agentes IA, como assistentes pessoais, bots autônomos ou agentes para jogos, não é uma ideia nova.

O que é novo, no entanto, é que, com o poder das novas técnicas de IA e dos modelos de linguagem,
somos capazes de construir essas aplicações de forma muito mais fácil e poderosa.

Ao mesmo tempo, estamos vendo aplicações completamente novas, como agentes científicos que podem fazer descobertas automáticas, agentes web que automatizam navegação e execução de tarefas na web, e agentes capazes de construir software do início ao fim.

---
## Principais benefícios dos Agentes
![img03](https://github.com/user-attachments/assets/d2fe599d-6bcd-4a64-9667-920c87af4f1e)

---
## Exemplo prático
![img04](https://github.com/user-attachments/assets/82b8a754-45c3-4a7e-8021-55ceffb875f5)

Vamos analisar um exemplo específico relacionado à otimização da cadeia de suprimentos na nuvem.

Ele permite que usuários respondam a perguntas como:
"E se alterarmos as restrições de envio? Como isso afetaria meus custos operacionais?"

Essa é uma pergunta difícil, que não pode ser respondida apenas com o GPT, porque a IA precisa entender os dados e restrições específicas do usuário.

Nesse caso, usamos o AutoGen para criar três agentes que resolvem essa questão de forma eficiente: **commander, writer e safeguard**.

1. Inicialmente, o **usuário envia a pergunta**, que é **recebida pelo commander**.
2. Antes de responder, o **commander pausa a conversa atual e inicia um "chat aninhado" com o writer**.
3. O **writer**, que usa um modelo de linguagem como backend, **analisa a pergunta** e **sugere um código Python** que pode ser usado para resolver o problema.
4. O **commander verifica o código com o safeguard**, que valida se o código é seguro.
5. Caso seja seguro, o **commander executa o código**.

![img05](https://github.com/user-attachments/assets/74b33eaa-a589-4eb2-968e-6f308c994507)

Este é um exemplo simples de como usar múltiplos agentes e etapas para concluir uma tarefa.

Em geral, podem surgir problemas, como códigos inseguros ou erros de execução. Nesses casos, o commander retornaria ao writer para corrigir o código.

---
## Perspectiva da programação
![img06](https://github.com/user-attachments/assets/defe60a6-3d0b-4546-81d3-2d9b58f99466)

Como eles constroem um programa desse tipo?
O método é bem diferente dos programas tradicionais. Os passos incluem:

**1. Criar os agentes** (como writer, safeguard, commander e user).
**2. Definir os padrões de interação entre os agentes** (por exemplo, dois chats aninhados para o commander).
**3. Iniciar a conversa com o agente inicial**.

Todo o restante acontece automaticamente. O framework gerencia os passos, os chats aninhados e retorna o resultado final.

---
## Orquestração Multi-Agente
![img08](https://github.com/user-attachments/assets/82059f24-b9ea-4742-8170-573b2c762826)

Um benefício imediato é a capacidade de usar múltiplos agentes para construir aplicações complexas de IA.

Para isso, é necessário considerar diferentes padrões de interação entre os agentes. Por exemplo:

1. Em alguns casos, o desenvolvedor pode preferir um fluxo de trabalho estático, onde cada etapa é claramente definida.
2. Em outros, é desejável dar mais autonomia aos agentes, permitindo fluxos de trabalho dinâmicos.
3. Há também o equilíbrio entre usar linguagem natural para instruir os agentes ou linguagem de programação para maior controle.
4. Outro ponto importante é o compartilhamento de dados entre os agentes.

---
## Frameworks

![img10](https://github.com/user-attachments/assets/52a5e2ce-b884-45ea-ba6b-bb48d66554ba)

---
## Agentes e AutoGen

No caso de frameworks como o AutoGen, os agentes são entidades especializadas que colaboram, cada um com responsabilidades distintas, para resolver tarefas complexas.

A ideia central é orquestrar **múltiplos agentes com papéis específicos**, como:

1. **Commander**: Coordena as interações.
2. **Writer**: Gera soluções (como códigos ou textos).
3. **Safeguard**: Realiza validações.
