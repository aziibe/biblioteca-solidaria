# Páginas do Site

## Catálogo de Livros (`catalogo.html`)

Esta é a página de **catálogo de livros** da aplicação _Biblioteca Solidária_, onde os usuários podem visualizar os livros disponíveis para doação. A interface permite aplicar filtros por gênero e faixa etária.

### Funcionalidades

- Listagem dinâmica dos livros disponíveis no sistema.
- Filtros por gênero (`category`) e faixa etária (`classification`).
- Cada card contém:
  - Capa do livro (imagem genérica)
  - Título, autor, gênero e classificação
  - Status de disponibilidade
  - Botão “Solicitar” que leva para a página de detalhes com ID na URL

## Página de Informações do Livro (`info-livro.html`)

Essa página faz parte do projeto **Biblioteca Solidária** e exibe os detalhes de um livro específico, permitindo que o usuário visualize informações completas e, se estiver logado, solicite o livro para retirada.

### Funcionalidades

- Busca os detalhes de um livro através do ID passado na URL (`?id=18`)
- Exibe as informações do livro como título, autor, descrição, categoria, status, dados do doador e ponto de coleta
- Exibe botões para solicitar o livro.
- Redireciona para a página de login se o usuário clicar em "Solicitar Livro" sem estar autenticado.

## Página de Login e Cadastro (`login.html`)

Esta página HTML oferece a interface de **login** e **cadastro de usuários** para o projeto _Biblioteca Solidária_. Ela se comunica com uma API REST construída com Django Rest Framework, realizando requisições `POST` para autenticação e criação de novos usuários.

## Página de Solicitações (`solicitacoes.html`)

Este módulo é responsável por exibir e gerenciar as solicitações de empréstimo de livros dentro da aplicação Biblioteca Solidária.

### A interface é dividida em duas abas principais:

- **Solicitações Feitas:** livros solicitados pelo usuário logado.

- **Solicitações Recebidas:** pedidos feitos por outros usuários para os livros doados pelo usuário atual.

### Funcionalidades principais:

- Exibição dinâmica de solicitações com base no status (pendente, aguardando retirada, etc).

- Botões de ação para cancelar, aprovar ou confirmar retirada das solicitações, com chamadas para a API via fetch.

- Autenticação baseada em token JWT armazenado no localStorage.

- Alternância intuitiva entre as guias com navegação fluida.

- Feedback visual por meio de estilos e mensagens de alerta.

## Página Meus Livros (`meus-livros.html`)

Página "Meus Livros" — Biblioteca Solidária
Esta página permite que usuários autenticados visualizem, filtrem e acessem detalhes dos livros que cadastraram na plataforma Biblioteca Solidária. A interface é dinâmica e interativa, com opções de filtro por gênero, faixa etária e status de disponibilidade.

### Principais Funcionalidades:

- Listagem dinâmica de livros cadastrados pelo usuário.

- Filtros aplicáveis por:

  - Gênero (Ficção, Fantasia, Horror, etc.)
  - Faixa etária (Livre, 10+, 13+, etc.)
  - Status (Disponível/Indisponível)

- Cards visuais dos livros com informações essenciais (título, autor, gênero, classificação, status).

- Botão para adicionar novo livro, destacado no início da lista.

- Integração com API (/api/my-books/) via token JWT armazenado no localStorage.

- Redirecionamento para tela de detalhes com botão de ação.

- Controle de navegação com base no login do usuário.

## Página Adicionar Livros (`adicionar-livro.html`)

Esta página permite que usuários autenticados registrem novos livros na plataforma Biblioteca Solidária.

### Requisitos de Acesso:

O usuário deve estar logado (verificação via accessToken no localStorage).

### Principais Funcionalidades:

- Formulário de cadastro com os seguintes campos:

  - Título
  - Autor
  - Descrição
  - Categoria (Ex: Ficção Científica, Romance, etc.)
  - Classificação Etária (Ex: Livre, 13+, 18+...)

- Ponto de Coleta (populado dinamicamente via API)

### Ao enviar:

Os dados são enviados via POST para o endpoint:
POST `/api/my-books/`

Token JWT é usado no cabeçalho Authorization.

Se bem-sucedido, o usuário é redirecionado para a página de detalhes do livro recém-adicionado.

### Funcionalidades adicionais:

- Botão Cancelar redireciona para `meus-livros.html`.

- Botão Sair limpa o token e redireciona para `login.html`.

### Integração com Backend

Endpoints consumidos:

- GET `/api/pickup-points/` → Lista os pontos de coleta.

- POST `/api/my-books/` → Registra o novo livro com ponto de coleta associado.

## Página Editar Livros (`editar-livro.html`)

Permite que o usuário autenticado edite as informações de um livro já cadastrado em seu acervo pessoal.

### Requisitos de Acesso

O usuário precisa estar logado (accessToken no localStorage).

### Principais Funcionalidades:

- Ao carregar a página, os dados do livro (via ID na URL) são buscados na API e populam os campos:

  - Título
  - Autor
  - Descrição
  - Categoria
  - Classificação Etária

- O formulário permite ao usuário modificar os dados e enviar as alterações.

### Requisição PATCH para:

- PATCH `/api/my-books/{id}/`

## Página Editar Livros (`editar-perfil.html`)

Permite que o usuário logado atualize suas informações pessoais e de endereço.

### Requisitos de Acesso

- Acesso apenas para usuários autenticados (accessToken no localStorage).

### Principais Funcionalidades

Carrega automaticamente os dados atuais do usuário via: GET `/api/users/{userId}/`

Permite editar:

- Nome
- E-mail
- Senha
- Data de nascimento
- Telefone
- Endereço completo (rua, número, cidade e CEP)

Envia atualizações parciais com: PATCH `/api/users/{userId}/`

### Extras:

Só os campos preenchidos são enviados (evita sobrescrita indesejada).

Validações simples no front-end (ex: campos obrigatórios como senha).

Botão Cancelar retorna para perfil.html.

## Página Perfil do Usuário (`perfil.html`)

Exibe os dados do perfil do usuário logado e um histórico de livros doados.

### Acesso Restrito

Necessário accessToken no localStorage.

### Principais Funcionalidades:

Carrega dados do usuário autenticado via: GET `/api/users/{userId}/`

Exibe:

- Nome

-E-mail

-Data de nascimento

-Telefone

-Endereço completo

- Botão de atalho para editar perfil (editar-perfil.html).

### Histórico de Doações

Lista estática (mockada) de livros doados pelo usuário com seus respectivos status. (Não implementado no momento, atualização futura)
