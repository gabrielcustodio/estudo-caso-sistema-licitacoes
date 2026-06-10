# Aprendizados

Este documento apresenta uma síntese dos principais aprendizados técnicos e profissionais desenvolvidos durante minha participação em um sistema interno de monitoramento e análise de licitações.

O objetivo não é expor detalhes internos do projeto, mas registrar os conhecimentos adquiridos ao trabalhar em funcionalidades relacionadas a frontend, backend, banco de dados, permissões, dashboards, relatórios, filtros e manutenção de uma aplicação em contexto real.

Este documento faz parte de um estudo de caso anonimizado. Detalhes internos, dados reais e regras específicas foram omitidos.

## 1. Aplicações reais exigem mais do que CRUD

Um dos principais aprendizados foi perceber que uma aplicação real vai muito além de operações básicas de cadastro, listagem, edição e exclusão.

No contexto do projeto, as funcionalidades envolviam regras de permissão, filtros, relatórios, dashboards, integração com banco de dados, diferentes perfis de usuário, tratamento de erros e preocupação com a experiência de uso.

Isso reforçou a importância de pensar em sistemas web de forma mais ampla, considerando:

* Quem está usando a aplicação;
* Quais dados esse usuário pode acessar;
* Como as informações devem ser filtradas;
* Como apresentar dados de forma clara;
* Como evitar inconsistências entre telas;
* Como manter o sistema evolutivo e organizado.

## 2. Separação de responsabilidades é essencial

Outro aprendizado importante foi entender melhor a separação entre frontend, backend e banco de dados.

O frontend deve ser responsável pela interface, interação com o usuário e consumo das APIs. O backend deve centralizar regras de negócio, permissões, validações e organização das respostas. O banco de dados deve armazenar e permitir a consulta eficiente das informações.

Essa separação ficou ainda mais clara ao observar a migração de consultas diretas feitas pelo frontend para endpoints centralizados no backend.

Esse processo reforçou que regras sensíveis, como permissões e escopo de dados, não devem depender apenas da interface.

## 3. O backend é uma camada importante de segurança e organização

Durante o projeto, aprofundei meus conhecimentos sobre o papel do backend em uma aplicação full stack.

O backend não serve apenas para buscar dados no banco. Ele também é responsável por:

* Validar autenticação;
* Verificar permissões;
* Aplicar regras de escopo;
* Organizar filtros;
* Padronizar respostas;
* Tratar erros;
* Proteger dados sensíveis;
* Integrar serviços externos;
* Reduzir a exposição de regras internas no frontend.

Esse aprendizado foi importante para entender por que uma API bem organizada melhora a segurança, a manutenção e a evolução do sistema.

## 4. Autenticação e autorização são conceitos diferentes

Um ponto importante foi compreender melhor a diferença entre autenticação e autorização.

Autenticação está relacionada a identificar quem é o usuário.

Autorização está relacionada a definir o que esse usuário pode acessar ou executar.

Esse conceito foi essencial para entender sistemas com diferentes perfis de usuário, permissões e escopo de dados.

Um usuário autenticado não deve ter acesso automático a todas as funcionalidades. Cada ação ou dado sensível precisa respeitar regras de permissão definidas no sistema.

## 5. RBAC ajuda a organizar sistemas multiusuário

O contato com controle de permissões baseado em papéis ajudou a entender melhor como sistemas multiusuário podem ser organizados.

Com RBAC, permissões são associadas a papéis, e usuários recebem esses papéis conforme seu nível de acesso.

Esse modelo facilita a manutenção porque evita criar regras isoladas para cada usuário e permite organizar o acesso de forma mais previsível.

Os principais aprendizados relacionados a RBAC foram:

* Diferenciar papéis e permissões;
* Entender o contexto do usuário autenticado;
* Aplicar permissões no backend;
* Adaptar a interface conforme o perfil;
* Filtrar dados de acordo com o escopo permitido;
* Evitar depender apenas do frontend para segurança.

## 6. Filtros e paginação exigem alinhamento entre camadas

Trabalhar com filtros e paginação em telas com muitos dados ajudou a entender a importância do alinhamento entre frontend, backend e banco de dados.

O frontend precisa enviar os parâmetros corretamente.
O backend precisa interpretar, validar e aplicar esses parâmetros.
O banco de dados precisa retornar os dados de forma consistente.

Esse tipo de funcionalidade exige atenção porque pequenos erros podem gerar inconsistência nos resultados, filtros que não funcionam corretamente ou diferenças entre dashboard, listagem e relatório.

## 7. Dashboards dependem da organização dos dados

Outro aprendizado importante foi perceber que dashboards não são apenas elementos visuais.

Antes dos dados chegarem ao frontend, é necessário organizar informações, aplicar filtros, calcular totais, agrupar registros e formatar respostas de forma adequada para a interface.

Um dashboard útil depende de:

* Consultas bem estruturadas;
* Regras consistentes de permissão;
* Dados organizados no backend;
* Indicadores relevantes;
* Boa apresentação visual;
* Clareza para o usuário final.

Esse ponto ajudou a entender melhor a relação entre banco de dados, API e experiência de usuário.

## 8. Relatórios precisam de consistência

Os relatórios exigiam atenção especial porque precisavam respeitar filtros, permissões e organização dos dados.

Um relatório inconsistente pode gerar decisões erradas ou dificultar a análise do usuário.

Durante o projeto, aprofundei o entendimento sobre a importância de:

* Selecionar campos relevantes;
* Padronizar dados exibidos;
* Respeitar o perfil do usuário;
* Aplicar os mesmos filtros usados nas telas;
* Organizar informações de forma clara;
* Garantir que os dados exibidos estejam coerentes com o contexto da aplicação.

## 9. Tratamento de erros melhora a experiência do usuário

Em aplicações reais, erros e estados inesperados fazem parte do funcionamento do sistema.

Por isso, foi importante observar e trabalhar com estados como:

* Carregamento;
* Falha na requisição;
* Ausência de dados;
* Filtros sem resultado;
* Permissão insuficiente;
* Respostas inesperadas da API.

Esse aprendizado reforçou que uma boa experiência não depende apenas de telas bonitas, mas também de mensagens claras, comportamento previsível e tratamento adequado de problemas.

## 10. Manutenção de código existente exige cuidado

Trabalhar em um sistema já existente é diferente de iniciar um projeto do zero.

Antes de alterar uma funcionalidade, é necessário entender o fluxo, as dependências, as regras já implementadas e os possíveis impactos da mudança.

Esse processo ajudou a desenvolver mais cuidado com:

* Leitura de código existente;
* Entendimento de contexto antes de alterar;
* Correção de bugs sem criar efeitos colaterais;
* Respeito à estrutura do projeto;
* Evolução incremental;
* Testes manuais e validação de cenários;
* Comunicação com o time.

## 11. Integrações externas exigem atenção à segurança

O projeto também envolvia contato com integrações e configurações auxiliares, como variáveis de ambiente, CORS, validação de dados, envio de e-mails e serviços externos.

Esses pontos reforçaram a importância de proteger credenciais, validar entradas, tratar falhas de comunicação e separar configurações sensíveis do código.

Entre os aprendizados relacionados estavam:

* Uso de variáveis de ambiente;
* Configuração de CORS;
* Validação de dados com Zod;
* Cuidados com chamadas para serviços externos;
* Tratamento de falhas em integrações;
* Proteção de informações sensíveis.

## 12. Experiência do usuário também faz parte do desenvolvimento

Mesmo em sistemas internos, a experiência do usuário é importante.

Telas com muitos dados, filtros e permissões podem se tornar difíceis de usar se não forem bem organizadas.

Durante o projeto, aprofundei minha percepção sobre:

* Clareza visual;
* Organização de informações por prioridade;
* Mensagens de erro e vazio;
* Facilidade no uso de filtros;
* Exibição condicional de ações;
* Consistência entre telas;
* Redução de informações desnecessárias;
* Adaptação da interface ao perfil do usuário.

Esse aprendizado foi importante para enxergar o desenvolvimento web como uma combinação entre código, regras de negócio e experiência de uso.

## 13. Confidencialidade faz parte da postura profissional

Por se tratar de um sistema interno, um aprendizado importante foi entender que nem todo projeto pode ser divulgado com código, telas ou dados reais.

Mesmo assim, é possível apresentar aprendizados técnicos de forma profissional, preservando a confidencialidade da empresa, dos clientes e das regras internas.

Esse case foi estruturado com esse cuidado: explicar conceitos e desafios técnicos sem expor informações sensíveis.

## Conclusão

A participação nesse projeto contribuiu para minha evolução como desenvolvedor full stack júnior, principalmente por aproximar meus estudos de um contexto real de produto.

O contato com autenticação, permissões, dashboards, relatórios, filtros, banco de dados e manutenção de funcionalidades existentes me ajudou a entender melhor como aplicações web são organizadas e evoluídas em ambiente profissional.

Mais do que praticar tecnologias isoladas, esse projeto reforçou a importância de compreender arquitetura, regras de negócio, segurança, experiência do usuário e colaboração em equipe.