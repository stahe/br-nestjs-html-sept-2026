# Criando uma aplicação web com o framework NestJS

📖 **Leia o tutorial: [https://stahe.github.io/br-nestjs-html-sept-2026/](https://stahe.github.io/br-nestjs-html-sept-2026/)**

Este curso ensina a construir uma aplicação web **MVC** com o framework [NestJS](https://nestjs.com): uma aplicação cujas páginas HTML são geradas **pelo servidor** com a engine de views Handlebars, sem framework JavaScript no cliente.

Ele segue a progressão do curso [Introdução ao ASP.NET MVC por meio de exemplos](https://stahe.github.io/br-aspnetmvc-nov-2013/) (2013), adaptada ao ecossistema Node.js/TypeScript:

| ASP.NET MVC (2013) | NestJS (2026) |
|---|---|
| C#, controllers, actions | TypeScript, `@Controller`, `@Get`, `@Post` |
| views Razor, `_Layout.cshtml` | views Handlebars, `layout.hbs` |
| `[Required]`, `ModelState.IsValid` | class-validator, validação de formulários |
| sessão, `TempData` | cookies, token JWT, mensagens flash |
| filtros, `[Authorize]` | middleware, guards, interceptors, `@Roles` |
| Entity Framework | TypeORM + MySQL |

## A abordagem: muitos exemplos curtos, depois um estudo de caso

O curso se baseia em **28 projetos curtos**, cada um focado em um único conceito. Você pode executá-los e modificá-los. Todos os exemplos compartilham um único `npm install`.

| Capítulo | Conteúdo | Exemplos |
|---|---|---|
| Controllers, actions, roteamento | rotas, respostas, redirecionamentos, módulos, injeção de dependência | 01–06 |
| O modelo da action | parâmetros, conversão, validação, formulários POST, pipes | 07–12 |
| A view e seu template | Handlebars, templates, partials, helpers, formulários, validação, Post/Redirect/Get, diálogo de confirmação | 13–21 |
| Internacionalização | Uma aplicação em francês e inglês | 22 |
| Escopos de dados | Aplicação, requisição, cliente | 23 |
| O ciclo de vida da requisição | middleware, guard, interceptor, pipe, filtro de exceção | 24 |
| Autenticação e autorização | JWT em um cookie, papéis, CAPTCHA, limitação de taxa (rate limiting) | 25 a 27 |
| Arquitetura em camadas | web / lógica de negócio / DAO com TypeORM, transações, bloqueio otimista | 28 |

Cada exemplo é apresentado com seu código completo e comentários linha a linha. O curso também mostra os resultados em tempo de execução: capturas de tela do navegador, respostas HTTP brutas obtidas com `curl` e logs do servidor.

## O estudo de caso: RdvMedecins

O estudo de caso é uma aplicação completa de **agendamento de consultas em um consultório médico**. Ela é composta por cerca de sessenta arquivos, e **todos** eles são listados e comentados. Reúne todos os conceitos abordados nos capítulos anteriores.

- **Três papéis:**
  - `ADMIN` gerencia médicos e clientes;
  - `DOCTOR` agenda e cancela consultas;
  - `USER` é o paciente: agenda consultas para si mesmo e gerencia sua conta.
- **Regras de negócio:**
  - nenhuma consulta no passado;
  - apenas uma consulta futura por paciente;
  - nenhum nome duplicado, graças a restrições de unicidade nomeadas;
  - Um bloqueio otimista impede a sobrescrita de um registro que foi modificado nesse meio tempo por outro usuário.
- **Privacidade:** Um paciente nunca vê os nomes de outros pacientes. Esse nome nem sequer é enviado ao seu navegador.
- **Segurança:**
  - token JWT em um cookie `httpOnly` / `sameSite`;
  - senhas com hash bcrypt;
  - CAPTCHA e bloqueio temporário após várias tentativas de login malsucedidas;
  - criação de conta protegida por um "código de acesso" de uso único.
- **Uma interface bilíngue** (francês/inglês), construída com Bootstrap 5.
- **Aprimoramento progressivo:** A aplicação funciona inteiramente sem JavaScript. Um pequeno script apenas acrescenta um diálogo de confirmação que pode ser navegado pelo teclado.

## Tecnologias

NestJS 10 · TypeScript 5 · Express · Handlebars (hbs) · class-validator / class-transformer · TypeORM · MySQL 8 / MariaDB · Passport JWT · bcrypt · svg-captcha · Bootstrap 5

## Pré-requisitos

- Conhecimento básico de TypeScript (ou JavaScript), HTML e do protocolo HTTP.
- Node.js 20 ou superior, Visual Studio Code e um servidor MySQL (por exemplo, o Laragon no Windows). As instruções de instalação são fornecidas nos apêndices do curso.

## Autor

Este curso, seus exemplos e seu estudo de caso foram escritos por **Claude**, a IA da [Anthropic](https://www.anthropic.com) (setembro de 2026).
