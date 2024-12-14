## LLMs como Pensadores Analógicos

Ao resolver um problema, sempre nos beneficiamos de problemas resolvidos anteriormente, usando seu resultado ou seu método,
ou da experiência que adquirimos ao resolvê-los.

![image](https://github.com/user-attachments/assets/9ad5af68-e0eb-41e6-90b1-417ccf4adfc6)

O artigo **"Large Language Models as Analogical Reasoners"**, apresentado no ICLR 2024,
propõe o conceito de **"analogical prompting"** como uma nova abordagem para melhorar o raciocínio de 
modelos de linguagem como GPTs.

A ideia central é inspirada no raciocínio analógico humano,
no qual experiências passadas são usadas para resolver novos problemas.

> Gerar de forma adaptativa exemplos e conhecimentos relevantes, em vez de usar um conjunto fixo de exemplos.

---
## Detalhes principais:

#### Analogical Prompting:
- Em vez de depender de exemplos, os modelos geram automaticamente exemplares relevantes para um problema antes de resolvê-lo.
- Exemplares e conhecimentos contextuais são gerados pelo próprio modelo, sem a necessidade de dados externos ou de rotulagem manual, o que aumenta a adaptabilidade e a conveniência.

#### Comparação com outros métodos:
- Essa abordagem supera o "zero-shot prompting" e o "few-shot", em tarefas que requerem raciocínio, como resolução de problemas matemáticos e geração de código.
- Também oferece vantagens sobre métodos baseados em recuperação de dados externos, sendo mais eficiente e flexível.

#### Casos de uso e experimentos:
- Testes foram realizados em resolução de problemas matemáticos e de geração de código (como Codeforces). Os resultados mostraram maior precisão em comparação com métodos tradicionais, especialmente em tarefas complexas.

#### Abordagem integrada:
- Além de exemplares, o método permite que os modelos gerem conhecimentos mais amplos ("self-generated knowledge"), melhorando o desempenho em problemas desafiadores, como programação competitiva.
