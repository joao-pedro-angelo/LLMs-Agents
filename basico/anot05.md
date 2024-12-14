# Processo de Decoding

> **Decoding** é a etapa final da geração de texto em modelos como o GPT. 

Após o modelo calcular as probabilidades para cada token (palavra, símbolo ou caractere) com base em seu contexto,
o decoding decide quais tokens serão escolhidos para formar a resposta.

---
## Principais métodos de Decoding

#### Greedy Decoding
- Seleciona o token com maior probabilidade em cada passo.
- É um método simples, mas pode perder melhores respostas globais, já que busca apenas a "melhor decisão local".
- Problema: Pode levar a saídas previsíveis ou sem criatividade.

#### Beam Search
- Explora várias sequências candidatas ao mesmo tempo (os "beams") e seleciona a sequência mais provável ao final.
- Vantagem: Mais robusto para encontrar respostas globais ótimas.
- Problema: É mais caro computacionalmente e pode gerar respostas genéricas.

#### Top-k Sampling
- Restringe as escolhas apenas aos k-tokens mais prováveis, reduzindo a probabilidade de escolher palavras menos relevantes.
- Vantagem: Permite maior variabilidade enquanto mantém relevância.

#### Nucleus Sampling (Top-p Sampling)
- Escolhe os tokens com base em uma probabilidade cumulativa (p).
- Por exemplo, ao configurar p = 0.9, só considerará os tokens que, juntos, somam 90% da probabilidade total.
- Vantagem: Balanceia variabilidade e precisão, oferecendo respostas mais criativas e naturais.

#### Temperature Scaling
- Ajusta a distribuição de probabilidades antes da escolha, controlando a "aleatoriedade" das respostas.
- Exemplo: Valores menores de temperatura (ex.: 0.2) tornam as respostas mais determinísticas, enquanto valores maiores (ex.: 1.0) tornam as respostas mais variadas.

