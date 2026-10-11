# LLMs, prompts, memória e contexto

## O papel do LLM

Um Modelo de Linguagem de Grande Escala (LLM) processa linguagem e gera saídas a partir da entrada e do contexto recebido. 

Em um agente, pode contribuir para interpretar objetivos, avaliar opções e propor a próxima ação. 

O modelo não executa automaticamente qualquer operação externa: isso depende das ferramentas e do mecanismo de execução do sistema.

## Prompts e instruções

O prompt de sistema descreve o papel esperado do agente, seus objetivos e restrições. Instruções úteis tendem a ser explícitas sobre:

- a tarefa e o resultado esperado;
- as fontes que podem ser utilizadas;
- as ações permitidas e proibidas;
- quando solicitar esclarecimento;
- quando interromper a execução;
- como comunicar incertezas e resultados.

Prompts ajudam a orientar o comportamento, mas não devem ser a única barreira de segurança. 

Permissões, validações e limites precisam ser aplicados também na camada técnica.

## Contexto

Contexto é o conjunto de informações disponibilizadas ao modelo para uma etapa da execução. 

Pode incluir a solicitação atual, instruções, histórico relevante, resultados de ferramentas e trechos recuperados de documentos.

Contexto excessivo ou irrelevante pode aumentar custos e dificultar a seleção das informações importantes. 

Por isso, a construção do contexto deve priorizar relevância, atualidade e confiabilidade.

✨ Leia mais: [O que todo engenheiro de IA deveria saber sobre Engenharia de Contexto](https://elisaterumi.substack.com/p/o-que-todo-engenheiro-de-ia-deveria)

## Memória

Memória permite manter informações úteis além de uma única etapa. Dependendo da arquitetura, pode ser:

- **De curto prazo:** informações necessárias durante a interação ou tarefa atual.
- **Persistente:** informações que precisam estar disponíveis em interações futuras.

Memória não é sinônimo de histórico completo. 

O sistema deve definir quais dados merecem ser guardados, como podem ser corrigidos ou apagados, quem pode acessá-los e por quanto tempo serão mantidos.

## Como esses elementos se relacionam

O LLM interpreta a entrada usando o contexto disponível e as instruções. 

Se o agente precisar de informações adicionais, a orquestração pode recuperar documentos ou chamar uma ferramenta. O resultado pode ser incluído no contexto para orientar uma nova decisão.

## Limitações importantes

- Modelos podem produzir informações incorretas ou sem suporte suficiente.
- Instruções ambíguas podem gerar comportamento inconsistente.
- Informações antigas na memória podem induzir decisões inadequadas.
- Dados sensíveis exigem proteção e regras de retenção.
- Uma resposta convincente não comprova que a tarefa foi executada corretamente.

## Boas práticas

1. Defina instruções claras e verificáveis.
2. Forneça apenas o contexto necessário.
3. Diferencie fatos recuperados de inferências do modelo.
4. Valide saídas antes de ações relevantes.
5. Trate a memória como um recurso governado, não como armazenamento ilimitado.
6. Teste o comportamento com entradas ambíguas e situações adversas.

## Conceitos-chave

- O LLM contribui para a interpretação e a decisão.
- Prompt e contexto têm funções diferentes, mas complementares.
- Memória pode manter informações entre etapas ou interações.
- Nenhum desses elementos elimina a necessidade de validação e segurança.

## Para refletir

1. Que informações devem estar no contexto de uma tarefa?
2. Quando a memória persistente é útil — e quando pode ser arriscada?
3. Por que um prompt não deve ser considerado um mecanismo de segurança suficiente?

## Próximo passo

Leia [Ferramentas, bases de conhecimento e orquestração](05-ferramentas-bases-de-conhecimento-e-orquestracao.md).
