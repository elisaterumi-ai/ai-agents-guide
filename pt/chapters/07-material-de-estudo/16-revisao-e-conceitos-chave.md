# Revisão e conceitos-chave

Este módulo reúne perguntas e sínteses para revisar os fundamentos apresentados no repositório.

## 1. Fundamentos

Um agente é um sistema orientado a objetivos que pode interpretar uma tarefa, planejar ações, utilizar ferramentas e avaliar resultados. Um LLM pode fazer parte desse sistema, mas não representa necessariamente toda a arquitetura.

**Perguntas**

1. O que diferencia um agente de um sistema que apenas responde a uma pergunta?
2. Em quais situações uma automação determinística é mais adequada?
3. Por que autonomia deve ser limitada conforme o risco?

## 2. Arquitetura

Modelos, instruções, contexto, memória, ferramentas, bases de conhecimento, orquestração e controles podem colaborar na execução. A composição deve refletir as necessidades reais do problema.

**Perguntas**

1. Qual é a função do contexto?
2. Como memória e histórico se diferenciam conceitualmente?
3. Por que as ferramentas precisam de permissões explícitas?

## 3. Raciocínio e execução

O agente pode alternar entre planejamento, ação, observação e nova decisão. A execução deve ter critérios de sucesso e condições de parada.

**Perguntas**

1. Por que observar o resultado de uma ferramenta é essencial?
2. Que riscos surgem de ciclos sem limites?
3. Quando uma etapa de verificação adicional é útil?

## 4. Construção

A implementação começa pela definição do problema e dos critérios de avaliação. Frameworks podem facilitar o desenvolvimento, mas não substituem decisões de arquitetura, testes e controles.

**Perguntas**

1. O que deve ser definido antes de escolher um framework?
2. Como avaliar se um agente realmente concluiu a tarefa?
3. Quais métricas devem ser acompanhadas além da qualidade da resposta?

## 5. Sistemas multiagentes

Múltiplos agentes podem dividir tarefas e especializar responsabilidades, mas a comunicação e a coordenação aumentam a complexidade.

**Perguntas**

1. Que benefícios justificariam vários agentes em vez de um único?
2. Como definir responsabilidades e interfaces entre agentes?
3. Como limitar a propagação de erros entre etapas?

## 6. Segurança e governança

Agentes devem operar dentro de permissões definidas, com validação, registros, supervisão proporcional ao risco e responsabilidades claras.

**Perguntas**

1. Quais ações exigem aprovação humana?
2. Por que guardrails precisam de controles técnicos?
3. Como equilibrar observabilidade e proteção de dados?

## Exercício de síntese

Escolha uma tarefa que você conhece e descreva, em poucas linhas:

1. O objetivo que o sistema deveria alcançar.
2. Se uma automação tradicional, um assistente ou um agente seria mais adequado.
3. Quais informações e ferramentas seriam necessárias.
4. Como o sistema verificaria se atingiu o objetivo.
5. Quais limites, riscos e condições de parada precisariam ser definidos.
6. Como a qualidade seria avaliada após a implementação.

## Mensagem final 🚀

- Comece pelo problema, não pela tecnologia.
- Utilize a arquitetura mais simples que atenda aos requisitos.
- Separe a geração de uma resposta da execução real de uma ação.
- Defina permissões, critérios de sucesso e condições de parada.
- Avalie qualidade, segurança, custo e latência em conjunto.
- Trate observabilidade, supervisão e governança como partes do sistema.

## Referência

Material didático baseado em [Introdução aos Agentes de IA: Fundamentos, Arquiteturas e Aplicações](https://elisaterumi.substack.com/perks/d9de5a19-3de0-4bf2-8692-eaf58dc1abd7).
