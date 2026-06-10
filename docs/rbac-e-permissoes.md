# RBAC e Controle de Permissões

Este documento apresenta uma visão geral, anonimizada e simplificada, dos conceitos de autenticação, autorização e controle de permissões por perfil de usuário trabalhados em um sistema interno de monitoramento e análise de licitações.

O objetivo não é expor a implementação real do sistema, mas registrar os principais conceitos técnicos com os quais trabalhei, estudei e tive contato durante minha participação no projeto.

Por confidencialidade, nomes reais de tabelas, regras específicas de negócio, código-fonte, permissões internas e dados sensíveis foram omitidos ou generalizados.

## Escopo da minha participação

Minha atuação esteve relacionada ao desenvolvimento e manutenção de funcionalidades que dependiam do perfil do usuário, incluindo regras de exibição no frontend, consumo de dados filtrados pela API, ajustes em permissões, validação de acesso a telas e compreensão do fluxo entre autenticação, contexto do usuário e autorização no backend.

Este documento não representa a autoria integral do modelo de permissões do sistema, mas sim uma síntese dos conceitos aplicados, estudados e observados durante minha participação no projeto.

## Conceito de RBAC

RBAC significa Role-Based Access Control, ou Controle de Acesso Baseado em Papéis.

Nesse modelo, o acesso às funcionalidades do sistema não é definido diretamente para cada usuário de forma isolada. Em vez disso, o usuário recebe um ou mais papéis, e cada papel possui um conjunto de permissões.

De forma simplificada:

```txt
Usuário
  ↓
Papéis
  ↓
Permissões
  ↓
Acesso a funcionalidades e dados
```

Esse modelo ajuda a organizar sistemas com diferentes tipos de usuários, principalmente quando existem áreas administrativas, clientes, operadores internos ou usuários com acesso limitado.

## Problema que o controle de permissões ajudava a resolver

O sistema precisava atender usuários com diferentes níveis de acesso.

Alguns usuários poderiam visualizar informações mais amplas, acessar dashboards administrativos, consultar logs e aplicar filtros globais. Outros usuários deveriam acessar apenas informações relacionadas ao próprio contexto.

Esse tipo de controle era importante para:

* Proteger dados sensíveis;
* Evitar acesso indevido a informações de outros clientes;
* Separar funcionalidades administrativas de funcionalidades comuns;
* Exibir apenas telas e ações compatíveis com o perfil do usuário;
* Garantir que a validação de acesso acontecesse no backend;
* Melhorar a experiência do usuário ao ocultar opções indisponíveis.

## Fluxo simplificado de autenticação e autorização

Um fluxo comum de acesso podia ser entendido da seguinte forma:

```txt
1. O usuário realiza login na aplicação
2. O frontend obtém os dados básicos do usuário autenticado
3. O backend valida a autenticação
4. O backend carrega o contexto do usuário
5. O sistema identifica papéis e permissões disponíveis
6. A rota verifica se o usuário possui permissão para a ação solicitada
7. Os dados são filtrados conforme o escopo permitido
8. A resposta é enviada ao frontend
9. A interface exibe apenas as informações compatíveis com o perfil do usuário
```

## Separação entre autenticação e autorização

Durante o projeto, um ponto importante foi entender a diferença entre autenticação e autorização.

A autenticação responde à pergunta:

```txt
Quem é o usuário?
```

Já a autorização responde à pergunta:

```txt
O que esse usuário pode acessar ou executar?
```

Essa separação é importante porque um usuário autenticado não deve necessariamente ter acesso a todas as áreas do sistema. Depois de confirmar a identidade do usuário, ainda é necessário verificar suas permissões.

## Contexto do usuário

Um conceito importante no controle de permissões era o carregamento do contexto do usuário.

Esse contexto reunia informações necessárias para que o sistema entendesse o nível de acesso do usuário autenticado, como:

* Identificação do usuário;
* E-mail ou dados básicos do perfil;
* Papéis associados;
* Permissões disponíveis;
* Escopo de dados permitido;
* Clientes ou entidades relacionadas ao usuário.

De forma simplificada:

```txt
Usuário autenticado
  ↓
Contexto do usuário
  ↓
Papéis, permissões e escopo
  ↓
Acesso permitido ou bloqueado
```

Esse contexto era utilizado tanto para liberar ou bloquear ações quanto para filtrar dados retornados pela API.

## Middlewares e validação de acesso

No backend, o controle de acesso podia ser organizado com middlewares.

De forma conceitual, o fluxo seguia uma estrutura parecida com:

```txt
Requisição
  ↓
Middleware de autenticação
  ↓
Carregamento do contexto do usuário
  ↓
Validação de permissão
  ↓
Controller ou regra da rota
  ↓
Resposta da API
```

Essa organização ajuda a separar responsabilidades:

* Um middleware verifica se o usuário está autenticado;
* Outro carrega as informações necessárias sobre o usuário;
* Outro valida se o usuário possui a permissão exigida;
* A rota executa a regra de negócio somente se o acesso for permitido.

## Exemplo conceitual de perfis

A aplicação precisava diferenciar perfis com diferentes níveis de acesso.

Um exemplo conceitual seria:

```txt
Perfil administrativo
  - Acesso a dashboards mais amplos
  - Acesso a filtros por cliente
  - Acesso a logs administrativos
  - Visualização de dados em escopo mais amplo

Perfil cliente
  - Acesso limitado ao próprio contexto
  - Sem acesso a logs administrativos
  - Sem filtro para alternar entre clientes
  - Visualização apenas dos dados permitidos
```

Esse exemplo é generalizado e não representa regras internas específicas do sistema original.

## Controle no frontend

O frontend também participava da experiência de controle de acesso, principalmente para adaptar a interface conforme o perfil do usuário.

Entre os pontos trabalhados ou estudados estavam:

* Ocultar menus não permitidos;
* Evitar exibir filtros incompatíveis com o perfil do usuário;
* Renderizar componentes condicionalmente;
* Adaptar dashboards conforme o escopo permitido;
* Melhorar a navegação para diferentes tipos de usuário;
* Evitar que o usuário tente executar ações indisponíveis.

Um exemplo conceitual:

```txt
Se o usuário possui perfil administrativo:
  Exibir filtros globais e opções administrativas

Se o usuário possui perfil restrito:
  Exibir apenas dados e ações compatíveis com seu contexto
```

## Validação no backend

Apesar de o frontend adaptar a interface, a validação principal precisava acontecer no backend.

Esse foi um ponto importante de aprendizado: esconder um botão ou menu no frontend melhora a experiência do usuário, mas não é suficiente para garantir segurança.

O backend precisava validar permissões antes de:

* Retornar dados sensíveis;
* Permitir ações administrativas;
* Aplicar filtros globais;
* Acessar logs;
* Atualizar informações;
* Executar operações restritas.

Essa separação reforça uma boa prática importante: regras sensíveis de autorização devem ser validadas na API, não apenas na interface.

## Escopo de dados por usuário

Além de permitir ou bloquear funcionalidades, o controle de acesso também precisava considerar o escopo dos dados.

Isso significa que dois usuários poderiam acessar a mesma tela, mas visualizar conjuntos diferentes de informações.

Exemplo conceitual:

```txt
Usuário administrativo:
  Pode visualizar dados de múltiplos contextos

Usuário restrito:
  Pode visualizar apenas dados associados ao seu próprio contexto
```

Esse tipo de filtragem era importante em listagens, dashboards, relatórios e telas de detalhe.

## Cuidados importantes

Durante o contato com esse tipo de controle, alguns cuidados se destacaram:

* Não depender apenas do frontend para segurança;
* Validar permissões no backend;
* Filtrar dados conforme o usuário autenticado;
* Evitar retornar informações sensíveis para usuários sem permissão;
* Padronizar nomes de permissões;
* Centralizar regras de acesso sempre que possível;
* Testar cenários com diferentes perfis;
* Evitar duplicação de lógica entre telas;
* Garantir que mudanças no perfil do usuário reflitam corretamente na interface.

## Tecnologias e conceitos relacionados

Durante o projeto, trabalhei, estudei ou tive contato com os seguintes conceitos e tecnologias relacionados ao controle de acesso:

* Autenticação;
* Autorização;
* RBAC;
* Middlewares;
* APIs REST;
* React;
* TypeScript;
* Node.js;
* Express;
* Supabase;
* PostgreSQL;
* SQL;
* Renderização condicional;
* Escopo de dados por usuário;
* Controle de permissões por perfil;
* Segurança em APIs.

## Aprendizados

O contato com esse fluxo de permissões foi importante para aprofundar meu entendimento sobre:

* A diferença entre autenticação e autorização;
* A importância de validar permissões no backend;
* Como adaptar interfaces conforme o perfil do usuário;
* Como organizar regras de acesso em sistemas multiusuário;
* Como filtrar dados de acordo com o escopo permitido;
* Como middlewares ajudam a separar responsabilidades;
* Como RBAC contribui para a manutenção e evolução de sistemas internos;
* Como pensar em segurança e experiência do usuário ao mesmo tempo.

## Observação

Este documento é uma representação simplificada e anonimizada, criada apenas para fins de portfólio e estudo. Nenhuma informação sensível, código proprietário, dado real ou regra interna específica do sistema original é divulgada.
