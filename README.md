Cookenu
Labenu | Full-Stack Web Development Bootcamp


Cookenu

GitHub top language GitHub language count Repository size GitHub last commit


Escopo do Projeto
De manhã, você acordou, tomou uma bela xícara de café, verificou sua caixa de email e viu que tinha mais uma proposta de Freela. Freela vem de Freelancer, que é um trabalhador autônomo que sempre trabalha em projetos diferentes. Dessa vez, um cliente deseja te pagar muito bem para implementar o Cookenu.

Esse produto nada mais é do que uma rede social, na qual os usuários podem dividir informações relevantes sobre comidas e receitas que tenham experimentado. Ela possui todas as funcionalidades mais comuns em redes sociais:

Cadastro:

Como o projeto está no início, o usuário só precisa informar: o id, e-mail, nome a sua senha para realizar o cadastro. A senha tem uma regra: ela deve conter, no mínimo, 6 carácteres.
Login:

Como o projeto está no início, o usuário só precisa informar: o id, e-mail, nome a sua senha para realizar o cadastro. A senha tem uma regra: ela deve conter, no mínimo, 6 carácteres.
Informações do próprio perfil:

A partir do token de autenticação fornecido no login, o usuário deve ser capaz de ver as suas informações não sensíveis salvas no banco (vulgo, id e email)
Criar receitas:

O usuário deve poder criar uma receita. A receita deve ter os seguintes atributos: título, descrição/modo de preparo e data de criação
Seguir usuário:

Um usuário deve poder seguir outros usuários. Para isso, ele deve fornecer o id do usuário que deseja seguir. Atente-se que essa funcionalidade se assemelha ao do instagram: um usuário seguir outro, não significa que "esse outro" está seguindo o primeiro.
Feed:

Um usuário deve poder visualizar as receitas criadas pelos usuários que ele segue. As receitas devem estar ordenadas pela data de criação.
Linguagens
Typescript
SQL
Tecnologias/Ferramentas
Git
Typescript
Node.js
MVC
Programação Orientada a Objeto
MySQL
Postman
O que a plataforma é capaz de fazer 🏁
🏆 Fornecer uma aplicação backend para um sistema de rede social voltada para o ambiente culinário

🏆 Coletar, verificar, armazenar os dados em banco de dados próprio para o sistema

🏆 Criar, ler, atualizar e deletar (CRUD) dados da aplicação.

Linguagens e libs utilizadas 📚
Typescript: versão 3.8.3
bcryptjs: versão 5.0.1 @types/2.4.2
dotenv: versão 8.2.0
express: versão 4.17.0 @types/4.17.0
jsonwebtoken: versão 8.5.1 @types/8.3.9
knex: versão 0.21.1 @types/0.16.1
moment: versão 2.25.3
mysql: versão 2.18.1
uuid: versão 8.0.0 @types/7.0.3
Conhecimentos adquiridos durante o projeto 🎓
Criação de projetos node com npm.init
Tranpilação de TS em JS
Integração com banco de dados externo e uso de variáveis de ambiente
Requisições HTTP / API Rest
Sistema de Autenticação e Autorização
Criptografia e geração de tokens de informações sensíveis
Como rodar a aplicação ▶️
No terminal, clone o projeto:

git clone https://github.com/danilomourelle/Cookenu.git
Navegue para dentro da raiz do projeto

cd Cookenu
Instale as dependências

npm i
Crie um arquivo .env com as configurções do seu bando de dados (preferencialmente MySQL, caso deseje utilizar outro, adaptações no código e dependências serão necessárias)

DB_HOST = seu_endereço_host
DB_USER = seu_usuário
DB_PASSWORD = sua_sehna
DB_DATABASE_NAME = seu_banco_de_dados
JWT_KEY = chave_para_jwt
JWT_EXPIRE_TIME = tempo_expiração (exemplo: 15 minutes)
BCRYPT_COST = cost_encriptação (idealmente um valor minimo de 12)
Execute a aplicação

npm start
Você poderá utilizar os endpoints através de um cliente HTTP (ex. Postman) tendo o endereço localhost:3003 como URL base para as requisições. Para informações de cada endpoint disponível conferir a documentação

Projeto inicialmente desenvolvido em 18/05/2020 neste Repo em parceria com:

Eloísa Fagundes
ADICIONAL
Querys realizadas paras as criações de tabelas utilizando o MySQL Workbench
Tabela Usuário

CREATE TABLE User (
  id varchar(255) PRIMARY KEY,
  email varchar(255) UNIQUE NOT NULL,
  password varchar(255) NOT NULL,
  role varchar(255) NOT NULL DEFAULT 'normal',
  name varchar(255) NOT NULL,
)
Tabela de Receitas

CREATE TABLE Recipes (
  id varchar(255) PRIMARY KEY,
  title varchar(255) UNIQUE NOT NULL,
  description text NOT NULL,
  created_at bigint(20) NOT NULL,
  creator_user_id varchar(255) NOT NULL,
  FOREIGN KEY (creator_user_id) REFERENCES User (id)
)
Tabela de Relação entre Usuários

CREATE TABLE UserFollowConnection (
  followed_id varchar(255) NOT NULL,
  follower_id varchar(255) NOT NULL,
  FOREIGN KEY (followed_id) REFERENCES User (id),
  FOREIGN KEY (follower_id) REFERENCES User (id)
)
