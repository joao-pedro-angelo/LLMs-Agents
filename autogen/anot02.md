# AutoGen

> O AutoGen é uma estrutura de conversação multiagente que permite que você crie rapidamente vários agentes com
diferentes funções, tarefas de persona e recursos para implementar aplicativos de IA complexos.

> Um sistema multiagente pode agilizar esse processo permitindo que você crie e contrate agentes que trabalhem para você.
> Seus agentes também podem revisar, criticar e melhorar os resultados.

![img01](https://github.com/user-attachments/assets/f13dab33-8f7e-4535-a431-148cf33dbe43)

No AutoGen, um agente é uma entidade que pode agir em nome da intenção humana,
enviar mensagens, receber mensagens, executar ações, gerar respostas e interagir com outros agentes.

O AutoGen tem uma classe de agente interna chamada "agente conversável",
que unifica diferentes tipos de agentes na mesma abstração de programação.
Ele vem com muitas funcionalidades internas. Por exemplo, você pode usar uma lista de configurações LLm
para gerar respostas, ou podemos fazer execução de código ou execução de função e ferramenta.
Ele também fornece um componente para manter o humano no loop e verificar se há interrupção da resposta.
Você pode ligar e desligar cada componente e personalizá-lo para atender às necessidades do seu aplicativo.
Usando esses diferentes recursos. Você pode criar agentes de diferentes funções usando a interface segura.

---
## Exemplo 01
![img02](https://github.com/user-attachments/assets/10c9fc31-ba28-4ce3-8316-9fddc5509dd3)

A imagem acima mostra um exemplo de uso do framework AutoGen para criar e interagir com um agente conversacional básico.
A ideia central é a configuração e o uso de um agente chamado ConversableAgent,
que utiliza um modelo de linguagem como backend (neste caso, especificado no llm_config como gpt-3.5).

![img03](https://github.com/user-attachments/assets/694eb437-12f9-49a8-b7af-f5695b5b96df)<br>
![img04](https://github.com/user-attachments/assets/bc99b95b-90b0-429b-b90e-09b462990b66)

---
## Conversa entre Agentes

Faremos um exemplo de comédia stand-up.
Queremos criar um aplicativo onde comediantes stand-up conversem entre si.

Então o primeiro agente que criaremos é um agente conversável chamado Cathy.
Neste caso, damos a ele uma mensagem do sistema para que o agente saiba que seu nome é Cathy e seu contexto.
![img05](https://github.com/user-attachments/assets/a7357086-b414-48f0-b657-cde9d89c8be1)

Vamos criar outro agente conversável chamado Joe e dar uma mensagem ao sistema.
Então isso dá uma instrução mais específica sobre como continuar a conversa.
![img06](https://github.com/user-attachments/assets/2dbe8c11-d6b8-4503-a01e-3d6097607647)

Certo, então temos dois comediantes.
Agora estamos pronto para colocá-los para trabalhar e criar uma conversa.
Iniciamos a conversa chamando a função de iniciar um bate-papo de um dos agentes.

![img07](https://github.com/user-attachments/assets/cf9157c2-e707-402e-bef9-dc1960f5c48d)

Por exemplo, se quisermos que Joe inicie a conversa, chamaremos a função de iniciar bate-papo de Joe.
Definiremos o destinatário como Cathy e daremos a ele a mensagem inicial.
Definimos o máximo de turnos para 2, temos dois turnos de conversas e então terminamos.

![img08](https://github.com/user-attachments/assets/26079f98-064d-4499-862b-7c5b153dd506)

E depois desses dois turnos, a conversa parou.

---
## Outros comandos

Após a conversa, nós podemos vê-la novamente na tela com o comando abaixo.
![img09](https://github.com/user-attachments/assets/9ecb3076-8114-4185-8170-e198ce57dbb2)

E você também pode inspecionar o uso do token no resultado do chat.
Chamaremos a função de custo do resultado do chat.
Veremos que estamos usando o modelo turbo GPT-3.5 mais barato.
Consumimos 97 tokens de conclusão e 219 tokens de prompt.
E o total de tokens é 316.
E o custo do código é essa quantia em dólares.
![img10](https://github.com/user-attachments/assets/d20bc6bd-b5da-4372-a809-704a1d9dea6b)

Então, em geral, poderíamos definir a conversa de diferentes maneiras.
Você também poderia verificar o resumo chamando a função de resumo do resultado do chat.
Então, por padrão, estamos usando a última mensagem como o resumo do resultado do chat.
![img11](https://github.com/user-attachments/assets/d417b5ea-dc36-45d4-9af4-32391ce2eca4)

E você pode dar um prompt de resumo. 
Então o que acontece é que depois que a conversa termina, chamaremos o LLM com este prompt.
E o modelo refletirá na conversa e produzirá um novo resumo.
![img12](https://github.com/user-attachments/assets/3a6782db-d306-4023-96b5-7ef95ca67d21)

E quando você não sabe o número certo de turnos antes que a conversa termine? O que você pode fazer?<br>
Poderíamos mudar a condição de término fornecendo uma configuração adicional chamada "is terminate message".
Esta é uma função booleana.
Então ela pega uma mensagem como entrada e retorna true ou false.
![img13](https://github.com/user-attachments/assets/428aa8a1-36c0-4d48-945a-e66fd8205810)

Preservando o estado do Agente:
![img14](https://github.com/user-attachments/assets/14ac9553-9067-4469-a0b7-126fe095881a)

---
> Esta é uma demonstração muito básica de conversa entre agentes.
