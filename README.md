# Estudo de Caso — Sistema Interno de Monitoramento e Análise de Licitações

Este repositório apresenta um estudo de caso técnico, anonimizado e simplificado, baseado na minha participação em um sistema interno voltado ao monitoramento, organização e análise de licitações.

O objetivo deste material não é divulgar o projeto original, seu código-fonte ou regras internas, mas registrar os principais conceitos técnicos, desafios e aprendizados obtidos durante minha durante minha participação no desenvolvimento do sistema.

## Objetivo do repositório

Este estudo de caso foi criado como parte do meu portfólio profissional, com o objetivo de demonstrar contato prático com problemas comuns em aplicações web reais, como:

* Separação entre frontend, backend e banco de dados;
* Consumo e criação de APIs REST;
* Controle de autenticação e autorização;
* RBAC e permissões por perfil de usuário;
* Dashboards e indicadores;
* Filtros avançados e paginação;
* Relatórios e organização de dados;
* Integração com serviços externos;
* Manutenção de funcionalidades existentes;
* Boas práticas de confidencialidade em projetos internos.

## Contexto do projeto

O sistema tinha como finalidade apoiar o acompanhamento e a análise de licitações, permitindo que diferentes perfis de usuários acessassem informações, indicadores, relatórios e funcionalidades de acordo com seu nível de permissão.

De forma geral, a aplicação envolvia:

* Listagens de licitações;
* Filtros por diferentes critérios;
* Dashboards com indicadores;
* Relatórios;
* Regras de acesso por perfil de usuário;
* Integração entre frontend, backend e banco de dados;
* Consumo de serviços externos;
* Manutenção e evolução de funcionalidades já existentes.

As regras reais de negócio, dados internos, nomes de clientes e detalhes específicos do sistema foram omitidos ou generalizados por confidencialidade.

## Escopo da minha participação

Minha atuação esteve relacionada ao desenvolvimento e manutenção de funcionalidades da aplicação, principalmente em pontos como:

* Telas e componentes no frontend;
* Consumo de APIs REST;
* Ajustes e evolução de filtros;
* Dashboards e indicadores;
* Relatórios;
* Renderização condicional conforme perfil do usuário;
* Controle de permissões;
* Integração entre frontend, backend e banco de dados;
* Correção de bugs e melhoria da experiência do usuário;
* Compreensão e manutenção de código existente.

Este repositório não representa a autoria integral do sistema original. Ele documenta, de forma profissional e anonimizada, conceitos, fluxos e desafios técnicos relacionados à minha atuação e ao meu aprendizado durante a participação no projeto.

## Confidencialidade

Este repositório não contém:

* Código-fonte proprietário;
* Dados reais;
* Telas internas;
* Nomes de clientes;
* Credenciais;
* Consultas reais do sistema;
* Estrutura real completa do banco de dados;
* Regras específicas de negócio;
* Informações sensíveis da empresa ou de usuários.

Todos os exemplos, fluxos e descrições foram generalizados com fins educacionais e profissionais.

## Tecnologias e conceitos abordados

O estudo de caso envolve tecnologias e conceitos como:

### Frontend

* React;
* TypeScript;
* Consumo de APIs REST;
* Componentização;
* Renderização condicional;
* Estados de carregamento, erro e ausência de dados;
* Organização de telas e melhoria da experiência do usuário.

### Backend

* Node.js;
* Express;
* APIs REST;
* Rotas e controllers;
* Middlewares;
* Autenticação;
* Autorização;
* RBAC;
* Tratamento de erros;
* Padronização de respostas.

### Banco de dados

* Supabase;
* PostgreSQL;
* SQL;
* Views;
* Relacionamentos;
* Filtros;
* Ordenação;
* Paginação;
* Escopo de dados por usuário;
* Organização de dados para dashboards e relatórios.

### Configurações e integrações

* Docker;
* dotenv;
* CORS;
* Zod;
* Resend;
* OpenAI API;
* Variáveis de ambiente;
* Validação de dados;
* Integração com serviços externos;
* Envio de e-mails transacionais;
* Cuidados com credenciais e informações sensíveis.

## Estrutura da documentação

A documentação está organizada em arquivos separados, cada um abordando um aspecto específico do estudo de caso.

```txt
docs/
├── arquitetura.md
├── rbac-e-permissoes.md
├── dashboard-e-relatorios.md
├── desafios-tecnicos.md
└── aprendizados.md
```

## Documentos

### Arquitetura geral

Arquivo: [`docs/arquitetura.md`](docs/arquitetura.md)

Apresenta uma visão geral da estrutura da aplicação, abordando a separação entre frontend, backend e banco de dados, além do fluxo simplificado de uma requisição.

Principais temas:

* Estrutura full stack;
* Responsabilidades do frontend;
* Responsabilidades do backend;
* Papel do banco de dados;
* Fluxo de requisições;
* Controle de acesso em camadas;
* Benefícios da separação de responsabilidades.

### RBAC e permissões

Arquivo: [`docs/rbac-e-permissoes.md`](docs/rbac-e-permissoes.md)

Explica, de forma conceitual, o controle de acesso por perfil de usuário utilizado no sistema.

Principais temas:

* Autenticação;
* Autorização;
* RBAC;
* Papéis e permissões;
* Contexto do usuário;
* Middlewares;
* Validação no backend;
* Renderização condicional no frontend;
* Escopo de dados por usuário.

### Dashboard e relatórios

Arquivo: [`docs/dashboard-e-relatorios.md`](docs/dashboard-e-relatorios.md)

Aborda os conceitos relacionados à organização e exibição de dados em dashboards, indicadores, filtros e relatórios.

Principais temas:

* Indicadores;
* Filtros;
* Paginação;
* Organização de dados;
* Relatórios;
* Consistência entre dashboard, listagens e relatórios;
* Relação entre dados, permissões e experiência do usuário.

### Desafios técnicos

Arquivo: [`docs/desafios-tecnicos.md`](docs/desafios-tecnicos.md)

Reúne os principais desafios técnicos observados e trabalhados durante o projeto.

Principais temas:

* Separação entre frontend, backend e banco de dados;
* Migração de consultas diretas no frontend para endpoints centralizados no backend;
* Controle de permissões;
* Escopo de dados por usuário;
* Filtros avançados;
* Consistência entre telas;
* Integrações externas;
* Manutenção de funcionalidades existentes;
* Experiência do usuário em sistemas internos.

### Aprendizados

Arquivo: [`docs/aprendizados.md`](docs/aprendizados.md)

Consolida os principais aprendizados técnicos e profissionais obtidos durante minha participação no projeto.

Principais temas:

* Aplicações reais vão além de CRUDs;
* Importância da separação de responsabilidades;
* Backend como camada de segurança e organização;
* Diferença entre autenticação e autorização;
* Uso de RBAC;
* Filtros, dashboards e relatórios;
* Manutenção de código existente;
* Confidencialidade em projetos internos;
* Experiência do usuário em sistemas com regras complexas.

## Principais aprendizados consolidados

A participação nesse projeto contribuiu para minha evolução como desenvolvedor full stack júnior, principalmente por aproximar meus estudos de um contexto real de produto.

Entre os principais aprendizados estão:

* Separação entre frontend, backend e banco;
* Centralização de regras sensíveis no backend;
* Autenticação, autorização e RBAC;
* Filtros, dashboards e relatórios com escopo de dados;
* Manutenção de código existente;
* Confidencialidade em projetos internos.

## Considerações finais

Este case demonstra meu contato com uma aplicação web em contexto profissional, envolvendo frontend, backend, banco de dados, permissões, dashboards, relatórios e manutenção de funcionalidades existentes.

Mais do que listar tecnologias, o objetivo deste repositório é mostrar minha evolução na compreensão de sistemas web reais, regras de negócio, organização de código, segurança, experiência do usuário e colaboração em ambiente profissional.

## Autor

Gabriel Custódio Loureiro

* GitHub: [github.com/gabrielcustodio](https://github.com/gabrielcustodio)
* LinkedIn: [linkedin.com/in/gabrielcustodioloureiro](https://www.linkedin.com/in/gabrielcustodioloureiro/)