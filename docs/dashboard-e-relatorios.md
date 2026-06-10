# Dashboard e Relatórios

Este documento apresenta uma visão geral, anonimizada e simplificada, dos conceitos relacionados a dashboards, indicadores, filtros e relatórios trabalhados em um sistema interno de monitoramento e análise de licitações.

O objetivo não é expor telas reais, regras específicas de negócio ou dados internos do sistema, mas registrar os principais conceitos técnicos e funcionais com os quais trabalhei, estudei e tive contato durante minha participação no projeto.

Por confidencialidade, nomes de clientes, métricas reais, consultas específicas, telas internas, regras de negócio e dados sensíveis foram omitidos ou generalizados.

## Escopo da minha participação

Minha atuação esteve relacionada ao desenvolvimento, manutenção e melhoria de funcionalidades envolvendo visualização de dados, filtros, dashboards, relatórios e integração entre frontend, backend e banco de dados.

Durante o projeto, trabalhei com telas e fluxos que dependiam de dados organizados, consumo de APIs, aplicação de filtros, renderização de indicadores, controle de permissões e apresentação das informações de forma clara para diferentes perfis de usuário.

Este documento não representa a autoria integral dos módulos de dashboard e relatórios, mas sim uma síntese dos conceitos técnicos que pratiquei, estudei e acompanhei durante minha participação.

## Objetivo dos dashboards

Os dashboards tinham como objetivo apresentar informações resumidas e indicadores relevantes para facilitar o acompanhamento das licitações.

Em vez de depender apenas de listagens extensas, os dashboards permitiam uma visão mais rápida sobre o volume de dados, status, relevância, desempenho de processamento e alertas importantes.

De forma geral, um dashboard precisava responder perguntas como:

* Quantos registros existem em determinado período?
* Qual a distribuição dos dados por status?
* Existem oportunidades classificadas como relevantes?
* Há erros ou alertas que precisam de atenção?
* Como os dados variam ao longo do tempo?
* Quais informações devem ser exibidas para cada perfil de usuário?

## Organização dos dados

Para que o dashboard fosse útil, os dados precisavam ser tratados e organizados antes de serem exibidos na interface.

Esse processo envolvia conceitos como:

* Consultas ao banco de dados;
* Filtros por período;
* Filtros por cliente ou contexto do usuário;
* Agrupamentos;
* Contagens;
* Cálculo de totais;
* Classificações por status;
* Organização dos dados em formatos adequados para o frontend.

De forma simplificada:

```txt
Banco de Dados
  ↓
Consultas e filtros
  ↓
Agregações e organização dos dados
  ↓
API / Backend
  ↓
Frontend
  ↓
Cards, gráficos, tabelas e indicadores
```

## Indicadores e métricas

Durante o projeto, trabalhei e estudei conceitos relacionados à exibição de métricas e indicadores no frontend.

Entre os tipos de informações que um dashboard poderia apresentar estavam:

* Total de registros encontrados;
* Dados por período;
* Distribuição por status;
* Distribuição por relevância;
* Indicadores de aptidão ou classificação;
* Alertas operacionais;
* Informações relacionadas ao processamento de dados;
* Métricas de acompanhamento e desempenho.

Os nomes e regras reais dos indicadores foram generalizados por confidencialidade.

## Filtros

Os filtros eram uma parte importante da experiência do usuário, pois permitiam refinar os dados exibidos nas listagens, dashboards e relatórios.

Entre os conceitos praticados ou estudados estavam:

* Filtros por período;
* Filtros por status;
* Filtros por relevância;
* Filtros por cliente ou contexto permitido;
* Busca textual;
* Paginação;
* Ordenação;
* Combinação de múltiplos filtros;
* Sincronização entre frontend e backend.

Um ponto importante foi entender que filtros não devem ser tratados apenas no frontend. Em sistemas com muitos dados, permissões e regras de negócio, os filtros precisam ser aplicados principalmente no backend e no banco de dados.

## Relação entre filtros e permissões

Os filtros também precisavam respeitar o perfil do usuário.

Usuários com permissões administrativas poderiam acessar filtros mais amplos, enquanto usuários com acesso restrito deveriam visualizar apenas informações relacionadas ao próprio contexto.

Exemplo conceitual:

```txt
Usuário administrativo
  → Pode acessar dados em escopo mais amplo
  → Pode utilizar filtros globais

Usuário restrito
  → Visualiza apenas dados permitidos
  → Não deve alternar para contextos não autorizados
```

Esse ponto reforçou a importância de unir regras de interface, validação no backend e filtragem correta no banco de dados.

## Relatórios

Os relatórios tinham como objetivo organizar informações de forma mais estruturada para consulta, análise ou exportação.

Durante o projeto, trabalhei e acompanhei fluxos relacionados à preparação e exibição de dados para relatórios, considerando aspectos como:

* Seleção de campos relevantes;
* Organização das colunas;
* Aplicação de filtros;
* Respeito às permissões do usuário;
* Padronização das informações exibidas;
* Clareza na leitura dos dados;
* Preparação para exportação ou visualização.

A geração de relatórios exigia atenção para que os dados exibidos estivessem consistentes com os filtros aplicados e com o perfil do usuário autenticado.

## Fluxo simplificado de geração de relatório

De forma conceitual, o fluxo de um relatório podia ser entendido assim:

```txt
1. Usuário acessa a tela de relatório
2. Usuário seleciona ou mantém filtros
3. Frontend envia parâmetros para a API
4. Backend valida autenticação e permissões
5. Backend aplica escopo do usuário
6. Banco de dados retorna os registros filtrados
7. Backend organiza os dados em formato padronizado
8. Frontend exibe ou disponibiliza o relatório
```

## Frontend dos dashboards e relatórios

No frontend, os principais desafios estavam relacionados à organização visual das informações e à clareza da interface.

Entre os conceitos trabalhados ou estudados estavam:

* Organização de cards de indicadores;
* Exibição de tabelas;
* Renderização condicional por perfil de usuário;
* Estados de carregamento;
* Estados de erro;
* Mensagens de vazio;
* Atualização de dados após aplicação de filtros;
* Consumo de endpoints específicos;
* Melhoria da experiência do usuário.

Um dashboard eficiente não depende apenas de dados corretos. Ele também precisa apresentar essas informações de forma clara, objetiva e útil para quem está usando o sistema.

## Backend dos dashboards e relatórios

No backend, os dashboards e relatórios dependiam de endpoints capazes de buscar, filtrar e organizar informações do banco de dados.

Entre os conceitos envolvidos estavam:

* Criação e manutenção de rotas;
* Aplicação de filtros recebidos do frontend;
* Validação de permissões;
* Consulta ao banco de dados;
* Agregação de dados;
* Paginação;
* Padronização das respostas;
* Tratamento de erros;
* Retorno de dados em formato adequado para a interface.

Esse fluxo reforçou a importância de centralizar regras sensíveis no backend, principalmente quando os dados exibidos dependem do perfil do usuário.

## Banco de dados e consultas

Os dashboards e relatórios dependiam diretamente da qualidade das consultas ao banco de dados.

Durante o projeto, aprofundei conhecimentos em conceitos como:

* Consultas SQL;
* Filtros com múltiplos critérios;
* Ordenação;
* Paginação;
* Relacionamentos entre tabelas;
* Views;
* Dados agregados;
* Contagens;
* Organização de informações para exibição.

A estrutura das consultas reais e das tabelas foi omitida por confidencialidade.

## Desafios técnicos

Alguns desafios comuns nesse tipo de funcionalidade incluem:

* Garantir que os filtros sejam aplicados corretamente;
* Evitar divergência entre dados do dashboard e dados das listagens;
* Respeitar permissões e escopo do usuário;
* Organizar respostas da API em formatos fáceis de consumir;
* Lidar com estados de carregamento, erro e ausência de dados;
* Manter clareza visual mesmo com grande volume de informações;
* Evitar duplicação de regras entre frontend e backend;
* Garantir consistência entre relatórios, dashboards e filtros.

## Tecnologias e conceitos relacionados

Durante o projeto, trabalhei, estudei ou tive contato com os seguintes conceitos e tecnologias relacionados a dashboards e relatórios:

* React;
* TypeScript;
* Node.js;
* Express;
* Supabase;
* PostgreSQL;
* SQL;
* APIs REST;
* Filtros;
* Paginação;
* Views;
* Dashboards;
* Relatórios;
* Autenticação;
* Autorização;
* RBAC;
* Renderização condicional;
* Tratamento de erros;
* Organização de dados para interface.

## Aprendizados

O contato com dashboards e relatórios foi importante para aprofundar meu entendimento sobre:

* Como transformar dados do banco em informações úteis para o usuário;
* Como estruturar endpoints para telas com filtros e indicadores;
* Como aplicar permissões em dados exibidos na interface;
* Como dashboards dependem de regras bem organizadas no backend;
* Como relatórios exigem consistência entre filtros, dados e permissões;
* Como melhorar a experiência do usuário em telas com grande volume de informação;
* Como pensar em sistemas web além de CRUDs simples.

## Observação

Este documento é uma representação simplificada e anonimizada, criada apenas para fins de portfólio e estudo. Nenhuma informação sensível, código proprietário, tela real, dado interno ou regra específica do sistema original é divulgada.
