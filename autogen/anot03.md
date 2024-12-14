# Chats Sequenciais e Integração de Clientes

> Você criará uma sequência de tarefas entre vários agentes,
que colaboram para fornecer uma experiência de integração do cliente para um produto.

---
## Teoria

![img01](https://github.com/user-attachments/assets/c6dffbc3-de71-4191-88df-7e357296fd12)<br>
Vamos considerar um cenário de integração de clientes.
Neste cenário, um procedimento típico é primeiro coletar algumas informações do cliente e então se envolver com o cliente
com base nas informações coletadas.

Com isso em mente, é uma boa ideia decompor esta tarefa de integração do cliente em três subtarefas,
incluindo coleta de informações, pesquisa de interesse e engajamento do cliente.

![img02](https://github.com/user-attachments/assets/f80245a5-53da-4cb8-b673-b945bcdaa043)<br>

---
## Import

![image](https://github.com/user-attachments/assets/80bcf827-4eba-4eef-8008-8af2c3e8276d)<br>
Então aqui, usaremos a classe de agente conversável do AutoGen para criar os agentes.
Vamos primeiro importar esse agente conversável do AutoGen.

---
## Primeiro Agente

![img03](https://github.com/user-attachments/assets/8375607c-2afe-4aa0-bb03-d8419af9a942)<br>
O primeiro agente é o que pede informações pessoais.

Definimos a mensagem do sistema como um agente de integração do cliente e demos instruções detalhadas do contexto.

Definimos o modo de entrada humana como "never" porque estamos usando um LLM para gerar a resposta deste agente.

---
## Segundo Agente

![img04](https://github.com/user-attachments/assets/f3d13978-5c70-4d7f-adc6-9e2604a00ce5)<br>
Similarmente, vamos criar outro agente de integração que peça preferência de tópico.

Podemos perceber o que queremos alcançar ao definir a mensagem do sistema.

A mensagem do sistema é definida para perguntar os interesses do cliente.

Usamos "never" como modo de entrada humana, pois estamos usando um LLM para apoiar este agente conversável.

---
## Terceiro Agente

![img05](https://github.com/user-attachments/assets/60ebaba9-1191-4337-8308-3dfd75e03e52)<br>
Outro agente que queremos criar é o agente de engajamento do cliente que fornecepiadas ou histórias interessantes com base nas informações pessoais do cliente.

E, novamente, damos instruções detalhadas sobre o comportamento desse agente de engajamento definindo
a mensagem de sistema adequada.

---
## Quarto Agente

![img06](https://github.com/user-attachments/assets/fa667b17-6221-4c8e-b56f-e1ca1505801e)<br>
Agora, em seguida, devemos definir um agente proxy para atuar como um proxy para o cliente real.

Observe que aqui estamos definindo o modo de entrada humana como always. 

Para que esse agente proxy sempre possa solicitar entrada humana do cliente real.

---
## Chat

![img07](https://github.com/user-attachments/assets/58312ad9-ac64-4d76-b183-6b989a7ddcf1)

Então, com esses agentes construídos, agora podemos criar um chat sequencial para finalizar o processo de integração.

Neste exemplo específico, cada chat é efetivamente um chat de dois agentes entre um agente de integração específico
e um agente proxy personalizado em cada chat.

Em cada chat, o remetente envia uma mensagem inicial ao destinatário para iniciar a conversa e, em seguida,
eles terão uma conversa de ida e volta até que o máximo de turnos seja atingido ou a mensagem de encerramento seja recebida.

Estamos definindo o máximo de turnos para dois, para que eles possam ter no máximo dois turnos de conversa.

Além disso, no cenário de chat sequencial, as tarefas, normalmente dependem umas das outras.

Neste caso, queremos usar o método summary.
Neste exemplo, estamos usando reflection com o método summary.

Adicionamos ainda um prompt summary como uma forma de instruir o modelo de linguagem sobre como fazer o resumo.

No segundo chat, estamos fazendo coisas semelhantes.

Neste segundo chat, o remetente é o agente de preferência de tópico de integração.
E o destinatário é um agente proxy do cliente.

E no terceiro chat, temos um chat entre o agente proxy do cliente e o agente de engajamento do cliente.

---
## Execução

![image](https://github.com/user-attachments/assets/dd7b146e-8414-442c-821d-033b2f7ec281)<br>
![image](https://github.com/user-attachments/assets/aec7d06d-b9c2-4e65-9a1b-9ffa1a5d5be7)<br>
Neste exemplo, você atuará como o cliente. E quando for solicitado a responder, você deve digitar sua resposta.

Você pode ver que estamos iniciando nosso primeiro bate-papo, que é entre o agente de informações pessoais
de integração e o agente de proxy do cliente.

![image](https://github.com/user-attachments/assets/eaf0f67c-96be-465d-9611-d2cbe28187ed)<br>
E aqui você pode ver que estamos iniciando um novo bate-papo,
que é a segunda sessão de bate-papo entre o agente de preferência de tópico e o agente de proxy do cliente.

![image](https://github.com/user-attachments/assets/ccaa1816-73aa-4fbd-a725-1f53548a741c)<br>
Esta é a mensagem do agente de engajamento do cliente.

---
## Dados extras

![image](https://github.com/user-attachments/assets/a223a22a-2488-40cf-ac1b-cbc13064f14b)
