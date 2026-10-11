# Arquitetura e frameworks

## Da ideia à implementação

Construir um agente começa pela definição do problema, não pela escolha de um framework. 

A arquitetura deve esclarecer o objetivo, os dados disponíveis, as ações permitidas, os critérios de conclusão e os riscos envolvidos.

## Etapas de projeto

1. **Definir o objetivo:** descreva o resultado esperado e como será avaliado.
2. **Delimitar o escopo:** especifique o que o agente pode e não pode fazer.
3. **Escolher o modelo:** considere qualidade, latência, custo, privacidade e requisitos de implantação.
4. **Definir contexto e conhecimento:** identifique documentos, memória e fontes necessários.
5. **Selecionar ferramentas:** ofereça somente operações úteis e autorizadas.
6. **Desenhar a orquestração:** estabeleça sequência, condições de repetição e critérios de parada.
7. **Adicionar controles:** implemente validação, permissões, registros e aprovação humana quando necessária.
8. **Avaliar e iterar:** teste casos comuns, limites, falhas e situações adversas.

## O papel dos frameworks

Frameworks para agentes podem facilitar a integração com modelos, ferramentas, memória, fluxos de execução e observabilidade. 

Eles oferecem abstrações e componentes reutilizáveis, mas não substituem decisões de arquitetura nem garantem segurança ou qualidade.

Ao avaliar um framework, considere:

- compatibilidade com modelos e provedores;
- facilidade para integrar ferramentas;
- controle explícito do fluxo de execução;
- suporte a testes e observabilidade;
- tratamento de erros e limites;
- manutenção, documentação e comunidade;
- requisitos de implantação, privacidade e custo.

Como o ecossistema evolui rapidamente, verifique a documentação oficial e a situação atual do projeto antes de escolher uma tecnologia.

## Alguns frameworks, SDKs e plataformas para conhecer

- **[LangChain](https://docs.langchain.com/oss/python/langchain/overview):** oferece componentes para construir agentes e integrar modelos de linguagem, ferramentas e fontes de dados.

- **[LangGraph](https://docs.langchain.com/oss/python/langgraph/overview):** permite organizar a execução em grafos, com controle de estado, persistência e participação humana em diferentes etapas.

- **[CrewAI](https://docs.crewai.com/):** facilita a criação de equipes de agentes, com divisão de responsabilidades e coordenação de tarefas e fluxos de trabalho.

- **[OpenAI Agents SDK](https://openai.github.io/openai-agents-python/):** oferece recursos para construir agentes com ferramentas, transferência de tarefas entre agentes, guardrails e acompanhamento da execução.

- **[LlamaIndex](https://developers.llamaindex.ai/python/framework/):** reúne recursos para conectar aplicações de IA a dados e documentos, incluindo recuperação de informações, RAG e agentes.

- **[n8n](https://n8n.partnerlinks.io/agentai):** permite criar workflows e integrar agentes de IA por meio de uma interface visual, conectando modelos, ferramentas e serviços.

### ✨ Para aprofundar e experimentar

Quer conhecer melhor essas ferramentas e acompanhar exemplos práticos? Nos artigos abaixo, explico os conceitos e mostro como construir na prática aplicações com IA.

**LangChain**

- [Tudo o que você precisa saber sobre LangChain antes de começar um projeto com IA](https://elisaterumi.substack.com/p/tudo-o-que-voce-precisa-saber-sobre)
- [Criando Chatbots com RAG usando LangChain](https://elisaterumi.substack.com/p/criando-chatbots-com-rag-usando-langchain)
- [Chatbots com Memória usando LangChain](https://elisaterumi.substack.com/p/chatbots-com-memoria-usando-langchain)
- [Agentes com LangChain: Quando a IA Precisa Tomar Decisões](https://elisaterumi.substack.com/p/agentes-com-langchain-quando-a-ia)
- [LangChain com MCP: Conectando ferramentas com flexibilidade e interoperabilidade](https://elisaterumi.substack.com/p/langchain-com-mcp-conectando-ferramentas)
- [Chatbot com LangChain e Streamlit: Criando uma interface conversacional](https://elisaterumi.substack.com/p/chatbot-com-langchain-e-streamlit)

**n8n**

- [Introdução ao n8n: Criando um atendente virtual com IA](https://elisaterumi.substack.com/p/introducao-ao-n8n-criando-um-atendente)

## Começar simples

Nem todo agente precisa de uma arquitetura complexa ou de múltiplos agentes. 

Um fluxo explícito com um modelo, poucas ferramentas e condições claras de parada pode ser mais fácil de testar e manter.

Adicione componentes quando houver uma necessidade identificável, como recuperação de documentos, memória persistente ou coordenação entre especialistas.

## Checklist antes de colocar em uso

- O objetivo pode ser testado?
- Os acessos são mínimos e adequados?
- As ações irreversíveis exigem confirmação?
- Há limites de custo, tempo e iterações?
- Os erros podem ser detectados e tratados?
- Existe registro suficiente para investigar problemas?
- O sistema foi avaliado em exemplos representativos e adversos?

## Conceitos-chave

- Comece pelo problema e pelos critérios de sucesso.
- Framework é meio de implementação, não solução automática.
- A arquitetura precisa tornar permissões e condições de parada explícitas.
- Simplicidade pode melhorar manutenção, custo e previsibilidade.

## Para refletir

1. Que requisitos deveriam ser definidos antes de escolher um framework?
2. Quando vale adicionar memória ou mais ferramentas?
3. Como evitar que um protótipo inseguro chegue à produção?

## Próximo passo

Veja um fluxo ilustrativo em [Exemplo de agente na prática](09-exemplo-de-agente-na-pratica.md).
