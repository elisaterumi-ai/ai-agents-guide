# Exemplo de agente na prática

## Cenário

Imagine um agente que ajuda uma equipe a responder perguntas sobre um conjunto de documentos internos. O objetivo é produzir respostas fundamentadas nas fontes disponíveis, sinalizando quando não há evidências suficientes.

Este exemplo é conceitual: não descreve uma implementação específica nem garante que qualquer agente terá essas capacidades sem integração e configuração.

## Objetivo e limites

**Objetivo:** responder à pergunta usando documentos autorizados e indicar as fontes consultadas.

**Limites:** não acessar documentos fora do escopo, não inventar referências e não divulgar dados que o usuário não tem permissão para consultar. Se a evidência for insuficiente, o agente deve informar a limitação ou pedir esclarecimento.

## Componentes possíveis

- Um LLM para interpretar a pergunta e redigir a resposta.
- Um prompt de sistema com instruções e limites.
- Um mecanismo de recuperação de documentos.
- Uma ferramenta para consultar o repositório autorizado.
- Uma camada de orquestração para coordenar as etapas.
- Controles de acesso, registros e avaliação.

## Fluxo de execução

1. **Receber a pergunta:** identificar o que a pessoa deseja saber.
2. **Verificar o escopo:** confirmar que a consulta está dentro das permissões disponíveis.
3. **Recuperar fontes:** buscar trechos relevantes nos documentos autorizados.
4. **Avaliar a evidência:** verificar se os resultados são suficientes e pertinentes.
5. **Produzir a resposta:** sintetizar o conteúdo com referências às fontes recuperadas.
6. **Validar:** verificar se as afirmações estão apoiadas nos documentos e se informações sensíveis foram protegidas.
7. **Encerrar ou pedir ajuda:** responder, pedir esclarecimento ou encaminhar para revisão humana.

## Possíveis falhas

- A busca não encontra o documento relevante.
- Os documentos estão desatualizados ou contraditórios.
- O modelo interpreta incorretamente um trecho.
- O usuário pede conteúdo fora de suas permissões.
- A ferramenta falha ou demora.

O sistema deve prever respostas para essas situações. Por exemplo, pode informar que não encontrou evidência suficiente em vez de preencher a lacuna com uma suposição.

## Como avaliar

Crie um conjunto representativo de perguntas e defina critérios como:

- correção factual;
- correspondência entre resposta e fontes;
- qualidade das referências;
- tratamento adequado de perguntas sem resposta;
- respeito às permissões;
- latência e custo;
- comportamento diante de instruções maliciosas ou ambíguas.

A avaliação deve combinar métricas apropriadas, inspeção de exemplos e, quando necessário, revisão humana.

## Variações

Se a tarefa exigir atualização de dados, o agente pode consultar uma fonte autorizada em tempo real. Se envolver uma ação com consequências externas, como enviar uma mensagem ou alterar um registro, essa operação deve ter validações e uma política clara de aprovação.

## Conceitos-chave

- Um caso de uso precisa de objetivo, escopo e critérios de conclusão.
- Ferramentas devem ser autorizadas e ter falhas previstas.
- Respostas precisam ser fundamentadas nas fontes disponíveis.
- Avaliação e segurança fazem parte da arquitetura, não são etapas opcionais no final.

## Para refletir

1. Como o agente deveria responder quando não encontra evidência suficiente?
2. Quais controles são necessários para proteger documentos internos?
3. Como testar se as referências realmente sustentam a resposta?

## Próximo passo

Leia [Fundamentos de sistemas multiagentes](../05-sistemas-multiagentes/10-fundamentos-de-sistemas-multiagentes.md).
