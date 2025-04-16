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
