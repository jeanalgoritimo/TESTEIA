Dashboard Inteligente de Clientes







Protótipo de um Dashboard de Gestão de Clientes desenvolvido com HTML, CSS, Bootstrap 5 e JavaScript. O projeto demonstra como a Inteligência Artificial pode auxiliar no preenchimento de formulários, reduzir tarefas repetitivas e manter o usuário no controle da validação dos dados.

Este repositório possui finalidade educacional e demonstra uma prova de conceito. Os clientes utilizados são fictícios e os dados permanecem somente na memória do navegador.

Funcionalidades

Dashboard responsivo e moderno;

Indicadores de total de clientes, clientes VIP, ativos e preenchidos via IA;

Pesquisa por nome, CPF ou e-mail;

Filtros por categoria e status;

Cadastro de clientes em modal;

Máscaras para CPF, telefone e CEP;

Preenchimento assistido por IA a partir de uma descrição em linguagem natural;

Categorias VIP, Regular e Prospect;

Status Ativo, Inativo e Pendente;

Exclusão de clientes com confirmação;

Atualização automática da tabela e dos indicadores;

Proteção contra injeção de HTML na renderização dos dados.

Demonstração do fluxo

O usuário acessa o dashboard e seleciona Novo Cliente.

No modal, informa uma descrição, como Cliente VIP de São Paulo.

O frontend envia a solicitação para um backend seguro.

A IA devolve os dados do cliente em formato JSON.

O formulário é preenchido automaticamente.

O usuário revisa, altera o que for necessário e confirma o cadastro.

A tabela e os indicadores são atualizados.

Arquitetura recomendada

flowchart LR
    A[Frontend HTML] -->|POST /api/clientes/gerar| B[Backend seguro]
    B -->|Chave protegida| C[OpenAI API]
    C -->|JSON estruturado| B
    B -->|Dados do cliente| A

O navegador não deve acessar diretamente a API da OpenAI. A chave precisa permanecer no servidor, configurada por variável de ambiente ou serviço de gerenciamento de segredos.

No arquivo seguro, o frontend chama apenas o endpoint interno:

const API_ENDPOINT = "http://localhost:5000/api/clientes/gerar";

const response = await fetch(API_ENDPOINT, {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ prompt: promptUser })
});

Tecnologias

Tecnologia

Utilização

HTML5

Estrutura da página, formulário, tabela e modal

CSS3

Identidade visual, cartões, sombras e responsividade

Bootstrap 5.3

Grid, componentes, formulário e modal

Bootstrap Icons

Ícones da interface

JavaScript

Estado, filtros, máscaras, renderização e requisições HTTP

OpenAI API

Geração estruturada dos dados no backend

Estrutura atual

TESTEIA/
├── dashboard.html
├── Dashboard de Clientes.pdf
└── README.md

dashboard.html: interface principal do protótipo;

Dashboard de Clientes.pdf: tutorial completo do projeto;

README.md: apresentação e instruções do repositório.

Como executar o frontend

Opção 1: Visual Studio Code

Clone o repositório:

git clone https://github.com/jeanalgoritimo/TESTEIA.git

Entre na pasta:

cd TESTEIA

Abra o projeto no Visual Studio Code:

code .

Instale a extensão Live Server.

Clique com o botão direito em dashboard.html e selecione Open with Live Server.

Opção 2: abrir diretamente

Também é possível abrir dashboard.html no navegador. Entretanto, chamadas HTTP para um backend podem exigir que o frontend seja servido por um servidor local por causa das políticas de CORS.

Integração com IA

Para que o botão Preencher com IA funcione, é necessário disponibilizar um backend no endereço:

http://localhost:5000/api/clientes/gerar

O endpoint deve receber:

{
  "prompt": "Cliente VIP de São Paulo"
}

E retornar um objeto semelhante a:

{
  "nome": "Cliente Demonstrativo",
  "cpf": "123.456.789-09",
  "email": "cliente@example.com",
  "telefone": "(11) 98765-4321",
  "cep": "01001-000",
  "logradouro": "Praça da Sé",
  "numero": "100",
  "bairro": "Sé",
  "cidade": "São Paulo",
  "estado": "SP",
  "categoria": "VIP",
  "status": "Ativo"
}

Segurança

Antes de publicar ou executar o projeto:

Nunca coloque uma chave real no HTML ou JavaScript;

Nunca envie chaves para o GitHub, mesmo em repositórios privados;

Não salve credenciais no localStorage do navegador;

Use a variável de ambiente OPENAI_API_KEY somente no backend;

Inclua .env, secrets.json e configurações locais no .gitignore;

Caso uma chave tenha sido exposta, revogue-a imediatamente;

Não utilize dados pessoais reais em demonstrações públicas;

Em produção, adicione autenticação, autorização, validação, rate limiting, logs seguros e monitoramento de custos.

Persistência dos dados

Nesta versão, os clientes são armazenados em um array JavaScript. Por isso, os dados são apagados ao atualizar a página.

Para uma aplicação real, o projeto pode evoluir para:

ASP.NET Core Web API;

Entity Framework Core;

SQL Server, PostgreSQL ou Azure SQL;

Autenticação com Microsoft Entra ID;

Auditoria e histórico de alterações;

Adequação à LGPD;

Validações no servidor;

Observabilidade e controle de consumo da IA.

Tutorial completo

A explicação detalhada, com imagens e trechos de código, está disponível em:

Abrir o tutorial em PDF

Roadmap

Interface responsiva;

Cadastro em modal;

Pesquisa e filtros;

Indicadores dinâmicos;

Preparação do frontend para integração segura;

Backend ASP.NET Core;

Integração segura com a OpenAI;

Persistência em banco de dados;

Edição de clientes;

Autenticação e controle de acesso;

Testes automatizados;

Deploy em ambiente de nuvem.

Objetivo do projeto

Este exemplo busca demonstrar que a IA pode ser incorporada a sistemas corporativos de forma prática e responsável. A tecnologia auxilia no trabalho repetitivo, enquanto o usuário continua responsável pela revisão e confirmação das informações.

Autor

Jean Paiva da Silva

Desenvolvedor de Software com experiência em .NET, C#, APIs, sistemas corporativos, integrações, cloud e modernização de aplicações, em transição e especialização para Engenharia de Inteligência Artificial.

LinkedIn

GitHub
