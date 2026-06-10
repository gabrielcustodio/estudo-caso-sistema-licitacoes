# Arquitetura Geral

Este documento apresenta uma visão geral, anonimizada e simplificada, da arquitetura de um sistema interno de monitoramento e análise de licitações no qual participei durante minha experiência como estagiário de desenvolvimento web.

O objetivo deste material não é documentar a arquitetura completa do sistema original, mas registrar os principais conceitos, fluxos e decisões técnicas com os quais trabalhei, estudei e tive contato durante o desenvolvimento e manutenção de funcionalidades.

Por confidencialidade, detalhes internos, código-fonte, nomes de clientes, regras específicas de negócio, estrutura real do banco de dados e telas do sistema foram omitidos ou generalizados.

## Escopo da minha participação

Minha atuação esteve relacionada ao desenvolvimento e manutenção de funcionalidades da aplicação, com foco em telas, consumo de APIs, filtros, dashboards, relatórios, regras de exibição por perfil de usuário e integração entre frontend, backend e banco de dados.

Este documento não representa a autoria integral da arquitetura do sistema, mas sim uma síntese dos conceitos técnicos com os quais trabalhei, estudei e tive contato durante minha participação no projeto.

## Visão geral

A aplicação seguia uma estrutura full stack, com separação entre frontend, backend e banco de dados.

De forma simplificada, o fluxo pode ser representado assim:

```txt
Usuário
  ↓
Frontend Web
  ↓
API / Backend
  ↓
Banco de Dados Relacional
```

Essa separação permitia organizar melhor as responsabilidades da aplicação, centralizar regras de negócio no backend e controlar o acesso aos dados de acordo com o perfil do usuário.

## Frontend

O frontend era responsável pela interface com o usuário, exibição de dados e consumo das informações fornecidas pela API.

Durante minha participação, atuei em funcionalidades relacionadas a:

* Exibição e organização de telas da aplicação;
* Consumo de APIs REST;
* Renderização de listas e detalhes;
* Aplicação de filtros;
* Exibição de dashboards e indicadores;
* Ajustes de interface e experiência do usuário;
* Renderização condicional de elementos conforme o perfil do usuário.

Tecnologias e conceitos relacionados:

* React;
* TypeScript;
* Componentização;
* Consumo de APIs;
* Organização de estados;
* Renderização condicional;
* Experiência do usuário.

## Backend

O backend funcionava como camada intermediária entre o frontend e o banco de dados. Essa camada era responsável por organizar rotas, aplicar regras de negócio, validar permissões e retornar dados ao frontend de forma estruturada.

Durante o projeto, aprofundei meus conhecimentos e participei de funcionalidades relacionadas a:

* APIs REST;
* Rotas e controllers;
* Middlewares;
* Autenticação;
* Autorização;
* Controle de permissões por perfil;
* Filtros e paginação;
* Integração com banco de dados;
* Tratamento de erros;
* Padronização de respostas.

Tecnologias e conceitos relacionados:

* Node.js;
* Express;
* SQL;
* Supabase/PostgreSQL;
* Zod;
* CORS;
* dotenv;
* RBAC;
* Docker.

## Integrações e configurações auxiliares

Além das camadas principais da aplicação, o projeto também envolvia integrações e configurações auxiliares importantes para o funcionamento do sistema.

Entre os pontos estudados ou utilizados estavam:

* Configuração de variáveis de ambiente com dotenv;
* Ajustes de CORS para comunicação entre frontend e backend;
* Validação de dados com Zod;
* Integração com serviços externos;
* Envio de e-mails transacionais com serviço externo, como Resend;
* Contato com integração de serviços de IA via API, como OpenAI API, utilizando chamadas externas para apoiar fluxos específicos do sistema.

Esses pontos reforçaram a importância de configurar corretamente o ambiente, validar dados de entrada, proteger informações sensíveis e organizar integrações externas de forma segura e reutilizável.

## Banco de dados

O banco de dados relacional era utilizado para armazenar informações relacionadas a usuários, clientes, licitações, permissões, logs e dados utilizados em dashboards e relatórios.

Por confidencialidade, este estudo de caso não apresenta a estrutura real das tabelas, nomes internos, relacionamentos completos ou dados do sistema original.

Durante minha participação, trabalhei e aprofundei conhecimentos em conceitos como:

* Consultas SQL;
* Relacionamentos entre entidades;
* Filtros;
* Ordenação;
* Paginação;
* Views;
* Escopo de dados por usuário;
* Organização de dados para dashboards e relatórios.

## Fluxo simplificado de uma requisição

Um fluxo comum da aplicação podia ser entendido da seguinte forma:

```txt
1. O usuário acessa uma tela no frontend
2. O frontend envia uma requisição para a API
3. O backend valida a autenticação
4. O backend identifica o contexto do usuário
5. O backend verifica permissões
6. O backend consulta o banco de dados
7. Os dados são filtrados conforme o perfil do usuário
8. A API retorna uma resposta ao frontend
9. O frontend exibe as informações na interface
```

## Controle de acesso

Um dos pontos importantes da arquitetura era o controle de acesso por perfil de usuário.

A aplicação precisava diferenciar usuários com permissões administrativas de usuários com acesso mais restrito. Com isso, algumas telas, filtros, ações e dados eram liberados ou bloqueados conforme o perfil.

Esse controle envolvia dois níveis:

* No frontend, elementos visuais podiam ser ocultados para melhorar a experiência do usuário;
* No backend, as permissões precisavam ser validadas antes de qualquer retorno de dados sensíveis.

Esse ponto reforçou a importância de não depender apenas do frontend para segurança, mantendo as validações principais na API.

## Benefícios da separação em camadas

A separação entre frontend, backend e banco de dados trouxe benefícios como:

* Melhor organização das responsabilidades;
* Maior controle sobre regras de negócio;
* Mais segurança no acesso aos dados;
* Facilidade para aplicar permissões;
* Reaproveitamento de endpoints;
* Melhor manutenção do código;
* Maior clareza na evolução de funcionalidades.

## Aprendizados

Esse contato com a arquitetura do projeto contribuiu para meu aprendizado em:

* Estruturação de aplicações full stack;
* Integração entre frontend e backend;
* Consumo e criação de APIs REST;
* Controle de acesso por perfil;
* Organização de filtros e paginação;
* Uso de banco de dados relacional;
* Separação de responsabilidades;
* Desenvolvimento de funcionalidades em contexto de sistema real.

## Observação

Este documento é uma representação simplificada e anonimizada, criada apenas para fins de portfólio e estudo. Nenhuma informação sensível, código proprietário ou dado real do sistema original é divulgado.