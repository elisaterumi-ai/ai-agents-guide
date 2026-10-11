# Ferramentas, bases de conhecimento e orquestração

## Por que esses componentes importam?

Um agente precisa interagir com sistemas e informações para realizar tarefas que vão além da geração de texto. 

> Ferramentas, bases de conhecimento e orquestração ajudam a transformar uma intenção em um processo executável.

## Ferramentas

Ferramentas são interfaces para operações externas, como consultar uma API, pesquisar dados, acessar um sistema ou executar uma ação autorizada. 

O modelo pode sugerir o uso de uma ferramenta, mas a aplicação é responsável por verificar os parâmetros, aplicar permissões e executar a operação.

Uma ferramenta bem projetada deve ter uma finalidade clara, entradas definidas, saídas compreensíveis e permissões mínimas. 

É por meio dessas integrações que o agente consegue transformar uma decisão em uma ação, como verificar a disponibilidade de um produto ou registrar um compromisso na agenda.

> Lembre-se: Ações com consequências relevantes podem exigir confirmação humana.

### Como uma ferramenta é utilizada

A aplicação disponibiliza ferramentas com descrições sobre suas funções e os dados necessários para utilizá-las. 

Com base no objetivo e no contexto, o modelo pode selecionar uma dessas ferramentas e informar os argumentos da chamada.

A aplicação valida a solicitação, executa a operação e devolve o resultado. Esse retorno passa a fazer parte das informações disponíveis para a próxima decisão do agente.

Por isso, a descrição de uma ferramenta precisa ser clara. 

O sistema deve conseguir distinguir, por exemplo, uma operação que apenas consulta um pedido de outra que cancela esse pedido.

### Lidando com erros

Ferramentas podem falhar, receber parâmetros inválidos ou retornar informações incompletas. 

O agente precisa reconhecer essas situações para decidir se deve tentar novamente, buscar uma alternativa ou informar que a tarefa está bloqueada.

Em operações que modificam dados, repetir uma chamada exige cuidado. Se a criação de um evento não retornar uma resposta, isso não significa necessariamente que o evento deixou de ser criado. 

Antes de repetir a operação, a aplicação deve verificar o estado para evitar duplicações.

Da mesma forma, uma resposta da ferramenta precisa ser interpretada dentro de seu contexto. 

Uma falha na consulta de estoque não permite concluir que o produto está indisponível; significa que essa informação não foi obtida.

## Bases de conhecimento e RAG

Os LLMs são treinados com grandes volumes de dados, mas o conhecimento adquirido nesse processo possui limitações. 

Ele pode estar desatualizado e não necessariamente inclui documentos privados ou informações específicas de uma organização.

Quando uma tarefa depende desses dados, a aplicação precisa consultar fontes externas. Elas podem ser documentos, bancos de dados, APIs ou sistemas corporativos.

### O que é RAG?

**RAG**, de *Retrieval-Augmented Generation*, é uma abordagem que combina recuperação de informações com geração de respostas.

Em vez de depender apenas do conhecimento do modelo, a aplicação busca conteúdo relevante em uma fonte externa e o fornece como contexto. 

O modelo utiliza essas informações para elaborar a resposta.

Imagine um assistente que responde perguntas sobre políticas internas. Ao receber uma dúvida sobre reembolso, ele pode recuperar os trechos relacionados ao assunto e utilizá-los para explicar as regras. 

Dessa forma, a resposta passa a ter como apoio os documentos da organização.

✨ Leia mais sobre RAG:

- [Criando Chatbots com RAG usando LangChain](https://elisaterumi.substack.com/p/criando-chatbots-com-rag-usando-langchain)
- [Qwen3 Embedding: Um novo marco para busca semântica e RAG](https://elisaterumi.substack.com/p/qwen3-embedding-um-novo-marco-para)
- [RAG Multimodal na Prática com Modelos Open-source](https://elisaterumi.substack.com/p/rag-multimodal-na-pratica-com-modelos)
- [Como Construir seu Próprio RAG Local com conteúdos da Wikipedia e LEANN](https://elisaterumi.substack.com/p/como-construir-seu-proprio-rag-local)

### Como a recuperação funciona

Os documentos precisam estar organizados de maneira que permita localizar o conteúdo relevante. 

Uma abordagem comum é dividir o material em trechos e utilizar representações vetoriais para buscar conteúdos semanticamente próximos da pergunta.

Também é possível utilizar busca por palavras-chave ou combinar diferentes estratégias. 

A escolha depende do tipo de informação e das necessidades da aplicação.

A qualidade da resposta depende tanto da recuperação quanto da geração. 

Se a busca retornar um trecho incompleto ou uma versão antiga do documento, o modelo poderá produzir uma resposta inadequada. Por isso, origem, atualização e permissões de acesso às fontes precisam ser consideradas.

### O que muda no RAG agêntico?

Em um fluxo RAG predefinido, a aplicação estabelece como a consulta será feita e como os resultados serão utilizados. No **RAG agêntico**, o agente pode decidir parte dessa estratégia durante a execução.

Ele pode escolher entre fontes, reformular uma consulta ou realizar uma nova busca ao perceber que as informações disponíveis ainda não são suficientes.

Por exemplo, ao investigar uma regra de reembolso, o agente pode consultar primeiro a política geral e depois buscar uma orientação específica para viagens internacionais. 

A segunda consulta surge da necessidade identificada durante a tarefa.

Essa flexibilidade pode ajudar em perguntas que exigem várias consultas, mas também aumenta o número de decisões, o custo e o tempo de execução.

✨ Leia mais aqui: [Você sabe a diferença entre RAG e Agentic RAG?](https://elisaterumi.substack.com/p/voce-sabe-a-diferenca-entre-rag-e)

### Conhecimento externo também precisa ser avaliado

RAG pode melhorar a fundamentação das respostas, mas não elimina alucinações. 

O modelo ainda pode interpretar um trecho incorretamente ou produzir uma conclusão que não é sustentada pelas fontes.

Por isso, é importante verificar se o conteúdo recuperado responde à pergunta e se a resposta final respeita as informações encontradas. 

Quando a evidência for insuficiente, o sistema deve reconhecer essa limitação.

## Orquestração

A orquestração controla o fluxo de execução. 

Pode determinar quando chamar o modelo, quando utilizar uma ferramenta, como tratar erros, quantas iterações permitir e em quais condições encerrar a tarefa.

Sem limites claros, um agente pode repetir chamadas desnecessárias, aumentar custos ou não concluir a execução. 

Condições de parada e caminhos de recuperação são parte importante do projeto.

## Exemplo de fluxo

1. Receber o objetivo do usuário.
2. Identificar quais informações faltam.
3. Recuperar documentos ou consultar uma ferramenta autorizada.
4. Interpretar o resultado e decidir se outra ação é necessária.
5. Validar o resultado e verificar os critérios de conclusão.
6. Responder, pedir esclarecimento ou encaminhar para revisão humana.

Esse é um exemplo ilustrativo, não uma sequência obrigatória para todos os agentes.

## Controles essenciais

- Restringir ferramentas às operações necessárias.
- Validar entradas e saídas.
- Tratar falhas e respostas inesperadas.
- Definir limites de tempo, custo e número de etapas.
- Registrar ações relevantes sem expor dados desnecessários.
- Solicitar aprovação antes de operações sensíveis.

## Conceitos-chave

- Ferramentas permitem agir sobre sistemas externos.
- Bases de conhecimento oferecem informações para consulta.
- RAG recupera conteúdo para enriquecer o contexto, mas não garante correção.
- Orquestração coordena etapas e condições de parada.
- Permissões e validações precisam ser aplicadas fora do modelo.

## Para refletir

1. Qual a diferença entre recuperar uma informação e executar uma ação?
2. O que pode acontecer se um agente não tiver condições de parada?
3. Quais ferramentas deveriam exigir aprovação antes da execução?

## Próximo passo

Avance para [Ciclo de raciocínio e execução](../03-padroes-de-raciocinio/06-ciclo-de-raciocinio-e-execucao.md).
