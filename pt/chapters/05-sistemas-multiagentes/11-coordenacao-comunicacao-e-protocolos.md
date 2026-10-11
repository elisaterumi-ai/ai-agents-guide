# Coordenação, comunicação e protocolos

## Por que coordenar?

Em um sistema multiagente, cada agente pode produzir resultados parciais. 

A coordenação determina como as tarefas são distribuídas, como as saídas são reunidas e como conflitos ou falhas são tratados.

Sem coordenação explícita, agentes podem repetir atividades, trabalhar com versões diferentes de informações ou produzir resultados incompatíveis.

## Distribuição de tarefas

A arquitetura precisa definir:

- quem atribui cada tarefa;
- quais entradas cada agente recebe;
- qual formato de saída é esperado;
- quais dependências existem entre tarefas;
- como lidar com atrasos e falhas;
- quem é responsável por validar o resultado final.

Um coordenador pode distribuir tarefas e reunir respostas. Em outros sistemas, o fluxo pode ser predefinido e cada agente executar apenas uma etapa.

## Comunicação

A comunicação deve ser estruturada o suficiente para que os agentes compreendam as mensagens. 

É útil explicitar o objetivo da mensagem, os dados necessários, o resultado esperado e eventuais limitações. Formatos e contratos claros reduzem ambiguidades.

## Interoperabilidade e protocolos

Protocolos definem convenções para que sistemas diferentes troquem informações ou solicitem capacidades. 

Ao escolher um protocolo, verifique sua finalidade, maturidade, compatibilidade, requisitos de segurança e suporte real nas ferramentas utilizadas.

Protocolos e padrões do ecossistema evoluem; detalhes de implementação devem ser conferidos na documentação oficial atualizada. 

Não se deve presumir que agentes de plataformas diferentes consigam colaborar automaticamente.

> A padronização facilita a integração, mas o funcionamento do conjunto ainda depende de como esses elementos são configurados e utilizados.

### MCP: acesso a ferramentas e contexto

O **Model Context Protocol**, ou MCP, padroniza a forma como aplicações de IA se conectam a ferramentas e fontes de contexto externas.

Uma integração pode disponibilizar recursos como consulta a documentos, acesso a registros ou operações sobre um serviço. 

A aplicação utiliza essas capacidades para fornecer informações ao modelo ou executar ações necessárias à tarefa.

Na arquitetura do MCP, a aplicação host utiliza clientes para se comunicar com servidores que disponibilizam essas capacidades. 

Um servidor pode expor ferramentas, recursos de contexto e prompts reutilizáveis.

O protocolo facilita a comunicação, mas a aplicação continua responsável por decidir o que disponibilizar ao agente e quais operações estão autorizadas.

✨ Leia mais sobre MCP: 

- [MCP: O Protocolo Aberto da Anthropic que Está Conectando IAs ao Mundo Real
](https://elisaterumi.substack.com/p/mcp-o-protocolo-aberto-da-anthropic)
- [MCP na Prática: Como criar seu próprio servidor localmente](https://elisaterumi.substack.com/p/mcp-na-pratica-como-criar-seu-proprio)
- [Como acessei dados da NASA usando MCP e linguagem natural](https://elisaterumi.substack.com/p/como-acessei-dados-da-nasa-usando)
- [Como usar MCP para acessar dados do governo brasileiro (passo a passo)](https://elisaterumi.substack.com/p/como-usar-mcp-para-acessar-dados)
- [Criando um MCP Server para buscar Jogos da Copa](https://elisaterumi.substack.com/p/criando-um-mcp-server-para-buscar)

### A2A: comunicação entre agentes

O **Agent2Agent**, ou A2A, tem como foco a comunicação entre agentes independentes. 

Ele permite descrever capacidades e organizar a troca de solicitações, mensagens e resultados de tarefas.

Considere um assistente corporativo que precisa organizar uma viagem. 

Em vez de realizar todas as atividades internamente, ele pode encaminhar uma solicitação a um agente especializado nesse serviço e acompanhar o resultado.

Essa interação precisa preservar as condições do pedido. Informações como destino, período, orçamento e ações autorizadas continuam sendo necessárias para que a tarefa seja executada adequadamente.

✨ Leia mais: [A2A e MCP : O Futuro da Comunicação entre Agentes de IA](https://elisaterumi.substack.com/p/a2a-e-mcp-o-futuro-da-comunicacao)

### Como os protocolos se complementam

Uma aplicação pode utilizar A2A para delegar uma tarefa a outro agente. 

Esse agente, por sua vez, pode acessar ferramentas e dados por meio de MCP ou de integrações diretas com APIs.

Os protocolos atendem, portanto, a relações diferentes: 

> MCP conecta aplicações a ferramentas e contexto; A2A organiza a comunicação entre agentes.

Isso não significa que toda arquitetura precise utilizar os dois. 

Um agente simples pode funcionar com integrações diretas, e um sistema multiagente pode ter sua coordenação inteiramente dentro da aplicação.

✨ Leia mais:

- [Arquitetura de agentes de IA: 6 protocolos que você precisa conhecer](https://elisaterumi.substack.com/p/arquitetura-de-agentes-de-ia-6-protocolos)
- [Agent Plugins: o próximo padrão que pode simplificar o desenvolvimento de agentes de IA](https://elisaterumi.substack.com/p/agent-plugins-o-proximo-padrao-que)

## Tratamento de falhas

Uma arquitetura robusta deve prever:

- respostas ausentes ou inválidas;
- agentes que excedem o tempo limite;
- divergências entre resultados;
- repetição controlada de operações;
- limites de chamadas e custo;
- registro da origem de cada resultado;
- mecanismos de escalonamento para revisão humana.

## Segurança entre agentes

Cada agente deve receber somente os dados e as permissões necessários à sua função. Mensagens de outro agente devem ser tratadas como entradas que podem conter erros ou instruções inadequadas; a confiança não deve ser automática.

## Como avaliar a coordenação

Observe se a arquitetura reduz o tempo total, melhora a qualidade ou aumenta a cobertura da tarefa. Compare esses benefícios com o custo adicional, a latência e a complexidade de depuração.

## Conceitos-chave

- Coordenação organiza dependências, tarefas e resultados.
- Contratos de entrada e saída reduzem ambiguidades.
- Protocolos favorecem interoperabilidade, mas não eliminam a necessidade de integração.
- Permissões e validação devem ser aplicadas a cada agente.

## Para refletir

1. Como identificar qual agente produziu uma informação incorreta?
2. Que regras ajudam a evitar ciclos de comunicação intermináveis?
3. Como limitar os dados que cada agente pode acessar?

## Próximo passo

Leia [Avaliação e observabilidade](../06-seguranca-e-governanca/12-avaliacao-e-observabilidade.md).
