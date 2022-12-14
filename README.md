# Curso de Angula - GatitoBook

## Versionamento do projeto

_Node v18.12.1_ .

_[Angular CLI](https://angular.io/cli)_

### Back end

No curso será utilizado a API que já está disponível na pasta `.\angular_formularios-main\api`.

O pacote fornecido pelo curso pode ter problemas para instalar alguns módulos, como o `sqlite3` e o `multer`. Assim, quando for executar a instalação, podemos seguir os comando (com as respectivas dependências comentadas)

```powershell
npm install
npm install sqlite3
npm install multer
```

#### Iniciar o servidor

Para iniciar o servidor, utilizar o comando `npm star`.

O servidor será iniciado na porta `localhost:3000`.

## Inicio do Projeto

### Instalação do Angular

Execute o comando `ng new gatitobook --strict` no terminal. Observe se o terminal está aberto na pasta onde deseja executar o projeto.

**Esse repositório já foi iniciado com o Angular instalado** .

Neste curso, utilizaremos os poderosos recursos do Angular. Podemos deixar a nossa experiência de desenvolvimento ainda melhor com alguns recursos do VS Code.

Você pode instalar esse [pacote de extensões](https://marketplace.visualstudio.com/items?itemName=johnpapa.angular-essentials&wt.mc_id=angularessentials-github-jopapa) específicas para o desenvolvimento de aplicações Angular.

Usaremos também o formatador de código [Prettier](https://prettier.io/). Para utilizá-lo com as regras do typescript de maneira harmoniosa, siga os seguintes passos:

1. Instale no nosso projeto utilizando o comando:

```powershell
npm install --save-dev prettier
```

2. Instale os seguintes pacotes de desenvolvimento:

```powershell
npm install --save-dev tslint-config-prettier
npm install --save-dev tslint-plugin-prettier
```

3. No arquivo `tslint.json`, coloque a seguinte configuração no atributo `extends`:

```powershell
"extends": ["tslint:recommended", "tslint-plugin-prettier", "tslint-config-prettier"]
```

4. No Vs Code, utilize o comando `Ctrl+Shift+P`, selecione a opção _“Format Document”_ e, em seguida, selecione Prettier como formarter.

### Instalação das bibliotecas para o CSS

Vamos utilizar duas bibliotecas nesse projeto. Na pasta do projeto `./angula_formularios-main/gatitobook` vamos instalar essas bibliotecas com o comando

```powershell
npm i bootstrap font-awesome
```

Para utilizarmos essas biblioteca, vamos no arquivo `angular.json` e acrescentamos nas configurações de _style_ as seguintes informações:

```powershell
"./node_modules/bootstrap/dist/css/bootstrap.min.css",
"./node_modules/font-awesome/css/font-awesome.css"
```

### Criando feature module

Com o comando abaixo, criamos os módulos principais do front

```powershell
ng generate module home --routing
```

Com o comando abaixo, criamos os componentes do Angular para o nosso projeto:

```powershell
ng generate component home
```

Dessa forma, criamos uma estrutura dentro da pasta `./gatitobook/src/app/home` para desenvolvermos a página home da nossa aplicação.

Primeiramente foi criado os arquivos `home-routing.module.ts` onde tem as rotas do nosso projeto e o arquivo `home.module.ts`, que foi alterado quando criamos o componente do projeto, pois o componente precisa ser declarado no módulo.

Depois, foi criado os componentes de CSS, HTML, TS e .SPEC.TS (para elaboração dos testes).

## Ajuste de rotas - Lazy Loading

Para que tenhamos o carregamento das páginas, apenas quando necessário, retiramos a importação do módulo do arquivo `app.module.ts`. Além disso, modificamos o `app.component.html` para indicar que o acesso a página Home, por exemplo, será feita através de uma roda.

Como o objetivo é criar uma rota para a página home, no arquivo `app-routing.ts`, criamos a indicação da rota:

```typescript
const routes: Routes = [
  {
    path: '',
    pathMatch: 'full',
    redirectTo: 'home'
  },
  {
    path: 'home',
    loadChildren: () => import('./home/home.module').then((moduloRecebido) => moduloRecebido.HomeModule)
  }
];
```

Dessa forma, para acessar a página home, será criada uma rota exclusiva pra essa página. Consequentemente, precisamos criar as rotas da componente Home no arquivo `home-routing.module.ts`.

## Página de Login

Para gerarmos o componente da página de Login, podemos executar o comando: `ng generate component home/login` ou `ng g c home/login`.

Dessa forma já é criado o componente e atualizado o `home.module.ts` com a declaração desse novo componente.

### Autenticação

Em Ângular, o local correto para inidicar as regras de negócio é na classe de serviço.

Assim, vamos criar primeiro o módulo de autenticação com o comando `ng generate module autenticacao`. Agora podemos criar a service com o comando `ng generate service autenticacao/autenticacao`.

Na service, vamos criar um método que irá fazer um POST ao back-end com um JSON contendo usuário e senha.

### Redirecionanemnto de rotas

Quando houver sucesso no login, queremos que o usuário seja orientado por uma rota onde ele acesse uma o módulo de animais.
Para isso, injetamos no `login.component.ts` o elemento `private router: Router`.

## Manipulando token JWT

Quando fazemos o login em uma página construída pelo Angular, é enviado um token chamado JWT. Esse token pode ser encontrado através da aba _Network_ do prompt de comando do navegador.

Na página [jwt.io](https://jwt.io/), é possível fazer o debug do token.

Para manipularmos o token enviado no momento do login, precisamos instalar uma biblioteca auxiliar através do comando `npm install jwt-decode`.

Com o comando `ng generate service autenticacao/token`, vamos criar um serviço para manipular os tokens.

## Rota de Guarda

O Angula cli tem uma ferramenta para proteger as rotas que os usuários farão através da página, impedindo, por exemplo, que determinado usuário, sem se autenticar previamente, entre em uma página restrita ou, se determinado usuário executar o logout dentro de uma página restrita, seja redirecionado para fora do ambiente restrito.

Para isso, utilizamos o comando `ng generate guard autenticacao/autenticacao` para que o Angular cli crie os arquivos necessários. Como estamos trabalhando com o Lazy loading, vamos utilizar a opção CanLoad, quando for feita a geração da guarda.
