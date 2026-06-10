# Desafios Técnicos

Este documento apresenta uma visão geral, anonimizada e simplificada, dos principais desafios técnicos observados, estudados e trabalhados durante minha participação em um sistema interno de monitoramento e análise de licitações.

O objetivo não é expor problemas internos específicos, código-fonte, regras de negócio ou dados reais, mas registrar os tipos de desafios encontrados em uma aplicação full stack com autenticação, permissões, dashboards, relatórios, filtros e integração entre frontend, backend e banco de dados.

Por confidencialidade, nomes de clientes, detalhes internos, telas reais, consultas específicas, credenciais, dados sensíveis e regras proprietárias foram omitidos ou generalizados.

## Escopo da minha participação

Minha atuação esteve relacionada ao desenvolvimento e manutenção de funcionalidades da aplicação, principalmente em telas, consumo de APIs, filtros, dashboards, relatórios, permissões por perfil de usuário e integração entre frontend, backend e banco de dados.

Este documento não representa a autoria integral das soluções técnicas do sistema, mas sim uma síntese dos desafios com os quais trabalhei, estudei, acompanhei ou aprofundei conhecimentos durante minha participação no projeto.

## 1. Separação entre frontend, backend e banco de dados

Um dos principais desafios em uma aplicação full stack é definir corretamente a responsabilidade de cada camada.

No contexto do projeto, era importante entender quais regras deveriam ficar no frontend, quais deveriam ser centralizadas no backend e quais deveriam ser resolvidas por meio de consultas ao banco de dados.

Essa separação era especialmente importante em pontos como:

* Controle de permissões;
* Aplicação de filtros;
* Organização de dados para dashboards;
* Exibição de informações por perfil de usuário;
* Tratamento de erros;
* Padronização das respostas da API.

Um exemplo prático desse desafio foi a transição de algumas consultas diretas feitas pelo frontend para endpoints centralizados no backend. Essa mudança ajudou a organizar melhor permissões, filtros, escopo de dados e padronização das respostas da API.

Um aprendizado importante foi perceber que o frontend deve melhorar a experiência do usuário, mas regras sensíveis, como permissões e escopo de dados, precisam ser validadas no backend.

## 2. Migração de consultas diretas para uma API centralizada

Um dos pontos importantes observados durante o projeto foi a necessidade de reduzir consultas diretas realizadas pelo frontend ao banco de dados por meio do cliente Supabase.

Em uma fase anterior da aplicação, algumas telas consumiam dados diretamente no frontend. Com a evolução do sistema e a necessidade de aplicar regras mais consistentes de permissão, filtros e escopo por usuário, tornou-se importante centralizar esse acesso no backend.

Essa mudança trouxe benefícios como:

* Maior controle sobre regras de negócio;
* Validação de permissões antes do retorno dos dados;
* Redução da exposição de regras sensíveis no frontend;
* Padronização das respostas da API;
* Melhor organização dos filtros e paginação;
* Maior consistência entre dashboard, listagens e relatórios;
* Facilidade para reutilizar endpoints em diferentes telas.

De forma simplificada, o fluxo evoluiu de:

```txt
Frontend
  ↓
Consulta direta ao Supabase
  ↓
Banco de dados
```

Para:

```txt
Frontend
  ↓
API / Backend
  ↓
Validação de autenticação e permissões
  ↓
Consulta ao banco de dados
  ↓
Resposta padronizada para o frontend
```

Esse processo reforçou a importância de centralizar regras sensíveis no backend e tratar o frontend principalmente como camada de interface e consumo de dados.

## 3. Controle de permissões por perfil de usuário

O sistema precisava atender usuários com diferentes níveis de acesso. Isso exigia cuidado para que cada perfil visualizasse apenas as informações e funcionalidades permitidas.

Esse desafio envolvia dois pontos principais:

* Adaptar a interface conforme o perfil do usuário;
* Garantir que o backend validasse permissões antes de retornar dados ou permitir ações.

Apenas ocultar botões, menus ou filtros no frontend não seria suficiente. O backend também precisava validar permissões, aplicar escopo de dados e bloquear acessos indevidos.

Esse ponto reforçou a importância de conceitos como:

* Autenticação;
* Autorização;
* RBAC;
* Middlewares;
* Contexto do usuário;
* Escopo de dados;
* Renderização condicional no frontend.

## 4. Escopo de dados por usuário

Além de liberar ou bloquear funcionalidades, era necessário garantir que os dados retornados fossem compatíveis com o perfil do usuário.

Em sistemas com múltiplos clientes ou contextos, dois usuários podem acessar a mesma tela, mas visualizar conjuntos diferentes de dados.

Exemplo conceitual:

```txt
Usuário administrativo
  → Pode visualizar informações em escopo mais amplo

Usuário restrito
  → Visualiza apenas informações associadas ao próprio contexto
```

Esse tipo de regra impacta diretamente:

* Listagens;
* Dashboards;
* Relatórios;
* Filtros;
* Telas de detalhe;
* Logs e informações administrativas.

Um dos aprendizados foi entender que permissões não envolvem apenas acesso a telas, mas também o controle sobre quais dados podem ser consultados.

## 5. Filtros avançados e paginação

Outro desafio importante estava relacionado à construção de telas com grande volume de dados.

Listagens de licitações exigem filtros bem organizados para que o usuário consiga encontrar informações relevantes com rapidez.

Entre os pontos envolvidos estavam:

* Filtros por período;
* Filtros por status;
* Filtros por relevância;
* Busca textual;
* Filtros por cliente ou contexto permitido;
* Ordenação;
* Paginação;
* Combinação de múltiplos filtros.

Esse tipo de funcionalidade exige alinhamento entre frontend, backend e banco de dados.

O frontend precisa enviar corretamente os parâmetros.
O backend precisa validar, interpretar e aplicar os filtros.
O banco de dados precisa retornar os dados de forma consistente e eficiente.

## 6. Consistência entre dashboard, listagens e relatórios

Dashboards, listagens e relatórios muitas vezes utilizam dados parecidos, mas apresentados de formas diferentes.

Um desafio importante era manter consistência entre essas visões.

Por exemplo:

* O dashboard pode exibir totais e indicadores;
* A listagem pode exibir registros detalhados;
* O relatório pode organizar dados para consulta ou exportação.

Se os filtros ou regras de permissão forem aplicados de forma diferente em cada ponto, os dados podem ficar inconsistentes.

Esse desafio reforçou a importância de:

* Padronizar regras no backend;
* Reutilizar lógica sempre que possível;
* Aplicar filtros de forma consistente;
* Garantir que permissões sejam respeitadas em todas as telas;
* Testar diferentes cenários de usuário.

## 7. Organização de dados para dashboards

Dashboards exigem mais do que apenas buscar registros no banco. Muitas vezes é necessário organizar dados em formatos próprios para cards, gráficos, tabelas ou indicadores.

Esse processo pode envolver:

* Contagens;
* Agrupamentos;
* Cálculos;
* Filtros por período;
* Classificações por status;
* Organização de séries temporais;
* Separação de indicadores por perfil de usuário.

Um aprendizado importante foi entender que dashboards dependem bastante da qualidade das consultas e da organização da resposta da API.

A interface fica mais simples quando o backend já retorna os dados em um formato adequado para exibição.

## 8. Tratamento de erros e estados da interface

Em uma aplicação real, nem sempre os dados carregam corretamente. Por isso, as telas precisam lidar com diferentes estados.

Entre os estados importantes estavam:

* Carregamento;
* Erro;
* Ausência de dados;
* Dados filtrados sem resultado;
* Permissão insuficiente;
* Respostas inesperadas da API.

Esses estados impactam diretamente a experiência do usuário.

Um sistema interno precisa informar claramente o que está acontecendo, evitando telas quebradas, mensagens genéricas ou comportamentos confusos.

## 9. Integração com serviços externos

O projeto também envolvia integrações e configurações auxiliares importantes, como envio de e-mails, consumo de APIs externas, configuração de ambiente e validação de dados.

Entre os pontos estudados ou utilizados estavam:

* Variáveis de ambiente com dotenv;
* Configuração de CORS;
* Validação de dados com Zod;
* Integração com serviços externos;
* Envio de e-mails transacionais com serviço externo, como Resend;
* Contato com integração de serviços de IA via API, como OpenAI API.

Esse tipo de integração exige atenção a:

* Segurança de credenciais;
* Tratamento de erros;
* Validação de entradas;
* Organização de chamadas externas;
* Separação entre configuração e regra de negócio;
* Proteção de informações sensíveis.

## 10. Manutenção e evolução de funcionalidades existentes

Um desafio comum em sistemas reais é trabalhar em funcionalidades já existentes.

Diferente de um projeto criado do zero, sistemas internos podem ter regras, fluxos e decisões técnicas anteriores que precisam ser respeitados.

Durante o projeto, isso envolveu atenção a pontos como:

* Entender o fluxo antes de alterar;
* Evitar quebrar funcionalidades existentes;
* Manter consistência visual e técnica;
* Corrigir bugs sem gerar efeitos colaterais;
* Ler código existente;
* Adaptar novas funcionalidades à estrutura do projeto;
* Trabalhar de forma incremental.

Esse tipo de experiência foi importante para entender melhor como funciona a manutenção de sistemas em contexto profissional.

## 11. Clareza na experiência do usuário

Além da parte técnica, também havia desafios relacionados à apresentação das informações.

Sistemas com muitos dados, filtros e permissões podem se tornar difíceis de usar se a interface não for clara.

Alguns pontos importantes eram:

* Organizar informações por prioridade;
* Evitar excesso de dados na tela;
* Exibir mensagens claras;
* Facilitar o uso de filtros;
* Adaptar a interface ao perfil do usuário;
* Tornar dashboards e relatórios mais compreensíveis;
* Evitar ações indisponíveis para determinados perfis.

Esse desafio reforçou a importância de pensar em desenvolvimento web não apenas como código, mas também como experiência de uso.

## Tecnologias e conceitos relacionados

Durante o projeto, trabalhei, estudei ou tive contato com os seguintes conceitos e tecnologias relacionados aos desafios técnicos:

* React;
* TypeScript;
* Node.js;
* Express;
* Supabase;
* PostgreSQL;
* SQL;
* APIs REST;
* Docker;
* Zod;
* CORS;
* dotenv;
* Resend;
* OpenAI API;
* Autenticação;
* Autorização;
* RBAC;
* Middlewares;
* Filtros;
* Paginação;
* Dashboards;
* Relatórios;
* Tratamento de erros;
* Renderização condicional;
* Escopo de dados por usuário;
* Integração com serviços externos.

## Principais aprendizados

Os desafios técnicos observados e trabalhados durante o projeto contribuíram para meu desenvolvimento em pontos como:

* Entender melhor a separação de responsabilidades em aplicações full stack;
* Perceber a importância de centralizar regras sensíveis no backend;
* Aplicar conceitos de autenticação, autorização e RBAC;
* Trabalhar com filtros e paginação em telas com muitos dados;
* Compreender como dashboards e relatórios dependem de dados bem estruturados;
* Valorizar tratamento de erros e estados de interface;
* Entender a importância da confidencialidade em projetos internos;
* Melhorar a leitura e manutenção de código existente;
* Pensar em experiência do usuário em sistemas com regras complexas;
* Enxergar aplicações web além de CRUDs simples.

## Observação

Este documento é uma representação simplificada e anonimizada, criada apenas para fins de portfólio e estudo. Nenhuma informação sensível, código proprietário, tela real, dado interno ou regra específica do sistema original é divulgada.
