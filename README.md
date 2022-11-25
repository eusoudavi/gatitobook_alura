# Curso de Angula - GatitoBook

_Node v18.12.1_

_[Angular CLI](https://angular.io/cli)_

### Back-end

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

**Esse repositório já foi iniciado com o Angular instalado**

Neste curso, utilizaremos os poderosos recursos do Angular. Podemos deixar a nossa experiência de desenvolvimento ainda melhor com alguns recursos do VS Code.

Você pode instalar esse [pacote de extensões](https://marketplace.visualstudio.com/items?itemName=johnpapa.angular-essentials&wt.mc_id=angularessentials-github-jopapa) específicas para o desenvolvimento de aplicações Angular.

Usaremos também o formatador de código [Prettier](https://prettier.io/). Para utilizá-lo com as regras do typescript de maneira harmoniosa, siga os seguintes passos:

1. Instale no nosso projeto utilizando o comando:

```
npm install --save-dev prettier
```

2. Instale os seguintes pacotes de desenvolvimento:

```
npm install --save-dev tslint-config-prettier
npm install --save-dev tslint-plugin-prettier
```

3. No arquivo `tslint.json`, coloque a seguinte configuração no atributo `extends`:

```
"extends": ["tslint:recommended", "tslint-plugin-prettier", "tslint-config-prettier"]
```

4. No Vs Code, utilize o comando `Ctrl+Shift+P`, selecione a opção _“Format Document”_ e, em seguida, selecione Prettier como formarter.

### Instalação das bibliotecas para o CSS

Vamos utilizar duas bibliotecas nesse projeto. Na pasta do projeto `./angula_formularios-main/gatitobook` vamos instalar essas bibliotecas com o comando

```
npm i bootstrap font-awesome
```

Para utilizarmos essas biblioteca, vamos no arquivo `angular.json` e acrescentamos nas configurações de _style_ as seguintes informações:

```
"./node_modules/bootstrap/dist/css/bootstrap.min.css",
"./node_modules/font-awesome/css/font-awesome.css"
```
