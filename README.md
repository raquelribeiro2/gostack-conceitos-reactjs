# 🚀 Bootcamp GoStack 2020 - Projeto NodeJS

## Executar projeto do repositório

- Abra a pasta no editor de código de sua preferência e execute o comando ``` yarn ``` ou ``` npm install ``` para instalar as dependências. 
- Os testes podem ser feitos logo após iniciar o servidor com o comando ``` yarn start ```

# Conteúdo aprendido neste módulo

## Conceitos ReactJS

## O que é React?

- **Biblioteca para construção de interfaces;**
    - Pode ser utilizado em web, mobile, interfaces de realidade virtual.

- **Utilizado para construção de Single-Page Applications (SPA);**
    - É uma forma de construir aplicações no frontend.
    - Anteriormente, quando não existia o conceito de SPA com libs tratando os dados no front-end, tinha o back-end e pra cada rota que o back-end acessava, ele retornava um conteúdo HTML.
    - O que mudou com a construção dos SPAs, é que o back-end só retorna JSON e o front-end controla as rotas e também a parte de consumir esses dados e mostrar pro usuário. Então as páginas na aplicação não precisam ser rotas no back-end.
    - No back-end só são feitas as rotas de criar, listar, editar e deletar recursos, enquanto que as rotas de página de contato, dashboard, listagem de usuários, por exemplo, ficam no front-end, ou seja, todo o roteamento da nossa aplicação fica no front-end e é aí que entra o conceito de SPA, pois é tudo em uma única página.
    - Você deve estar se perguntando: Como assim?
    - A página nunca recarrega, ela fica na mesma página e então temos várias formas de roteamento para alternar entre uma página e outra sem recarregar todo o browser, o que gera muita performance e usabilidade.

- **Pode ser chamado de framework?**
    - Sim. O React sozinho é uma lib, porém quando analisamos o ecossistema do React, como por exemplo, ReactJS para Web, React Native para Mobile, React Redux, entre outras ferramentas. Então quando nos referimos a todo o ecossistema do React, podemos sim chamá-lo de framework, pois é um conjunto de ferramentas que facilita o desenvolvimento das interfaces.

- **Tudo fica dentro do JavaScript;**
    - O CSS fica dentro do Javascript, porém continua com a sintaxe do CSS;
    - As imagens ficam dentro do Javascript;

    ```jsx
    import React from 'react';

    // Importando o arquivo CSS, o Webpack entenderá que se trata de um código CSS
    // Após importar esse arquivo, ele o jogará dentro do HTML automaticamente
    import './button.css';
    import icon from './button.png'

    // Função que retorna um código HTML diretamente
    // Sintaxe JSX
    function Button() {
    	return (
    		<button>
    			<img src={icon} />
    		</button>
    	);
    } 
    ```

- **React / ReactJS / React Native**

    - **React**
        - Refere-se à biblioteca de construção de interfaces e componentização.
        - É utilizada tanto no ReactJS quanto no React Native;

    - **ReactJS**
        - Refere-se ao comportamento do React no browser;
        - Junção da biblioteca React com a blbioteca React DOM (controla a DOM, a árvore de elementos do browser) = ReactJS.

    - **React Native**
        - Soma da biblioteca React com a biblioteca que lida com elementos nativos = React Native.

## Vantagens

- Organização do código;
    - Componentização.
        - Consiste em dividir partes da tela/código em componentes que, sozinhos tem funcionalidades específicas.
        - A aplicação completa também é um componente, pode ser chamado de App, por exemplo.
        - Deve-se criar um novo componente quando se consegue isolar a lógica de um componente sem que interfira no restante do código da aplicação.
        - Podemos pensar na estrutura de um componente sendo um conjunto de código de lógica, estruturação (HTML) e estilização (CSS).

- Divisão de responsabilidades;
    - Back-end: Regra de Negócio;
    - Front-end: Interface.

- Uma API, múltiplos clientes: Web e Mobile, por exemplo.
- Programação declarativa.

## JSX

- Basicamente é a junção de Javascript com XML.
- É usado para escrever HTML dentro do Javascript.
- Com React podemos criar nossos próprios elementos HTML.

```jsx
// Podemos criar uma função Button
function Button() {
	return (
		<button type="button">
			<span class="icon"></span>
		</button>
	);
}

// E usar esse componente que acabamos de criar na função abaixo
function Header () {
	return <Button />
}
```

## Programação Imperativa X Programação Declarativa

### Imperativo

```jsx
const notificacoes = 0;

function montaBadge(num) {
	if (notificacoes === 0 && num > 0) {
		// Adiciona badge
		// container.appendChild(badge) ...
	}

	if (notificações !=  0 && num > o) {
		// Apenas muda o número
		// badge.innerHTML = num ...
	}

	if (notificacoes != 0 && num === 0) {
		// Remove badge
		// container.removeChild(badge)
	}
}
```

### Declarativo

- Na programação declarativa (React), não se dá os passos para o browser montar a Badge, como no caso da imperativa, mas sim, as condições para mostrar ou não um elemento ou outro.

```jsx
// Não comparamos com o estado anterior

function Badge({ num }) {
	return (
		<div id="container">
			{ num > 0 && <div id="badge">{num}</div> }
			<span class="icon"></span>
		</div>
	);
}
```

## Babel / Webpack

### Babel

- O browser não entende o código React;
- O Babel converte o código JS de uma forma que o browser entenda;
    - Ele pega funcionalidades que o browser ainda não entende, por exemplo, o import/export.

### Webpack

- Possui várias funções:
    - Criação do bundle, arquivo que contém todo código Javascript da aplicação.
        - Ele pega todo o código Javascript compilado pelo Babel e transforma em um único código que é consumido pela aplicação.
    - Ensinar ao Javascript como importar arquivos CSS, imagens, etc.
    - Live reload com Webpack Dev Server.
        - Toda vez que um código Javascript é alterado, automaticamente é dado um refresh na aplicação, ou seja, o browser atualizar com as alterações realizadas.
        
## Configurando o Babel

- No terminal, na pasta do projeto execute:

```jsx
$ yarn init -y
```

- Este comando irá criar o arquivo *package.json* dentro de seu projeto.
- Para instalar as libs do React e React Dom, abra seu projeto no Visual Studio Code e execute:

```jsx
$ yarn add react react-dom
```

- Agora já podemos instalar o Babel e Webpack, para isso, execute:

```jsx
$ yarn add @babel/core @babel/preset-env @babel/preset-react webpack webpack-cli
```

- Feito isso, deve-se criar um arquivo, na raiz do projeto, chamado de **babel.config.js** e adicionar:

```jsx
module.exports = {
  presets: [
    '@babel/preset-env',
    '@babel/preset-react'
  ]
}
```

- É adicionado também um pacote que é usado como interface de linha de comando, para ser utilizado no terminal.
- Para adicioná-lo, execute:

```jsx
$ yarn add @babel/cli 
```

- Para utilizá-lo, execute:

```jsx
$ yarn babel src/index.js --out-file public/bundle.js

// src/index.js: caminho até o arquivo raiz;
// --out-file: flag que indica para onde deve ir o arquivo transpilado (convertido)
// public/bundle.js: caminho para o arquivo onde ficam as informações convertidas
```

- O arquivo convertido ficará com a seguinte sintaxe:

```jsx
"use strict";

var soma = function soma(a, b) {
  return a + b;
};

console.log(soma(1, 3));
```

- Para testar, vá até sua pasta do arquivo pelos seus Arquivos e dê dois cliques no arquivo index.html, para que ele seja aberto no browser.
- Coloque para inspecionar elemento → Console, o resultado da soma deve aparecer.

## Configurando o Webpack

- Agora deve-se instalar o babel-loader e criar um arquivo, na raiz do projeto, chamado de **webpack.config.js** e adicionar:

```jsx
$ yarn add babel-loader
```

```jsx
const path = require('path');

module.exports = {
// Arquivo raiz
  entry: path.resolve(__dirname, 'src', 'index.js'),
// Arquivo onde ficam as informações transpiladas
  output: {
    path: path.resolve(__dirname, 'public'),
    filename: 'bundle.js'
  },
  module: {
    rules: [
      {
// Basicamente estou dizendo
        test: /\.js$/, // Se tiver um arquivo com extensão .js
        exclude: /node_modules/, // e este arquivo não estiver em node_modules
        use: {
          loader: 'babel-loader', // converta ele usando babel
        }
      }
    ]
  }
}
```

- Para executar basta rodar o comando:

```jsx
$ yarn webpack --mode development 
```

- Feito isso, a conversão estará no mesmo arquivo bundle.js, com muitas outras instruções necessárias para que a conversão seja feita.

```jsx
/******/ (function(modules) { // webpackBootstrap
/******/ 	// The module cache
/******/ 	var installedModules = {};
/******/
/******/ 	// The require function
/******/ 	function __webpack_require__(moduleId) {
/******/
/******/ 		// Check if module is in cache
/******/ 		if(installedModules[moduleId]) {
/******/ 			return installedModules[moduleId].exports;
/******/ 		}
/******/ 		// Create a new module (and put it into the cache)
/******/ 		var module = installedModules[moduleId] = {
/******/ 			i: moduleId,
/******/ 			l: false,
/******/ 			exports: {}
/******/ 		};
/******/
/******/ 		// Execute the module function
/******/ 		modules[moduleId].call(module.exports, module, module.exports, __webpack_require__);
/******/
/******/ 		// Flag the module as loaded
/******/ 		module.l = true;
/******/
/******/ 		// Return the exports of the module
/******/ 		return module.exports;
/******/ 	}
/******/
/******/
/******/ 	// expose the modules object (__webpack_modules__)
/******/ 	__webpack_require__.m = modules;
/******/
/******/ 	// expose the module cache
/******/ 	__webpack_require__.c = installedModules;
/******/
/******/ 	// define getter function for harmony exports
/******/ 	__webpack_require__.d = function(exports, name, getter) {
/******/ 		if(!__webpack_require__.o(exports, name)) {
/******/ 			Object.defineProperty(exports, name, { enumerable: true, get: getter });
/******/ 		}
/******/ 	};
/******/
/******/ 	// define __esModule on exports
/******/ 	__webpack_require__.r = function(exports) {
/******/ 		if(typeof Symbol !== 'undefined' && Symbol.toStringTag) {
/******/ 			Object.defineProperty(exports, Symbol.toStringTag, { value: 'Module' });
/******/ 		}
/******/ 		Object.defineProperty(exports, '__esModule', { value: true });
/******/ 	};
/******/
/******/ 	// create a fake namespace object
/******/ 	// mode & 1: value is a module id, require it
/******/ 	// mode & 2: merge all properties of value into the ns
/******/ 	// mode & 4: return value when already ns object
/******/ 	// mode & 8|1: behave like require
/******/ 	__webpack_require__.t = function(value, mode) {
/******/ 		if(mode & 1) value = __webpack_require__(value);
/******/ 		if(mode & 8) return value;
/******/ 		if((mode & 4) && typeof value === 'object' && value && value.__esModule) return value;
/******/ 		var ns = Object.create(null);
/******/ 		__webpack_require__.r(ns);
/******/ 		Object.defineProperty(ns, 'default', { enumerable: true, value: value });
/******/ 		if(mode & 2 && typeof value != 'string') for(var key in value) __webpack_require__.d(ns, key, function(key) { return value[key]; }.bind(null, key));
/******/ 		return ns;
/******/ 	};
/******/
/******/ 	// getDefaultExport function for compatibility with non-harmony modules
/******/ 	__webpack_require__.n = function(module) {
/******/ 		var getter = module && module.__esModule ?
/******/ 			function getDefault() { return module['default']; } :
/******/ 			function getModuleExports() { return module; };
/******/ 		__webpack_require__.d(getter, 'a', getter);
/******/ 		return getter;
/******/ 	};
/******/
/******/ 	// Object.prototype.hasOwnProperty.call
/******/ 	__webpack_require__.o = function(object, property) { return Object.prototype.hasOwnProperty.call(object, property); };
/******/
/******/ 	// __webpack_public_path__
/******/ 	__webpack_require__.p = "";
/******/
/******/
/******/ 	// Load entry module and return exports
/******/ 	return __webpack_require__(__webpack_require__.s = "./src/index.js");
/******/ })
/************************************************************************/
/******/ ({

/***/ "./src/index.js":
/*!**********************!*\
  !*** ./src/index.js ***!
  \**********************/
/*! no static exports found */
/***/ (function(module, exports) {

eval("var soma = function soma(a, b) {\n  return a + b;\n};\n\nconsole.log(soma(1, 3));\n\n//# sourceURL=webpack:///./src/index.js?");

/***/ })

/******/ });
```

- Por último, instalar um pacote que dá reload no browser, para isso, execute:

```jsx
$ yarn add webpack-dev-server -D
```

- No arquivo **webpack.config.js**, deve ser adicionada a instrução que indica onde estão seus arquivos public:

```jsx
const path = require('path');

module.exports = {
  entry: path.resolve(__dirname, 'src', 'index.js'),
  output: {
    path: path.resolve(__dirname, 'public'),
    filename: 'bundle.js'
  },
// Adicionar essa instrução
  devServer: {
    contentBase: path.resolve(__dirname, 'public'),
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
        }
      }
    ]
  }
}
```

- Depois execute o comando:

```jsx
$ yarn webpack-dev-server --mode development
```

- Ele fará a mesma função do comando anterior, porém conseguirá identificar as alterações feitas no código e irá atualizar o browser automaticamente.

## Componentização

- O exemplo abaixo demonstra o conceito de JSX:
    - Arquivo index.js:

```jsx
import React from 'react';
import { render } from 'react-dom';

// Quero renderizar o h1 dentro da div com id="app", em index.html
render(<h1>Hello World</h1>, document.getElementById('app'))
```

- Neste exemplo já podemos entender o conceito de componentização:
    - É criado um arquivo dentro de src, chamado App.js (componentes são sempre com primeira letra maiúscula).

    ```jsx
    import React from 'react';

    function App() {
      return <h1>Hello World</h1>;
    }

    export default App;
    ```

    - No arquivo index.js ficará da seguinte forma:

    ```jsx
    import React from 'react';
    import { render } from 'react-dom';

    // importação do componente criado anteriormente
    import App from './App';

    // utilização do componente
    render(<App />, document.getElementById('app'));
    ```

    - O conceito da componentização consiste em criar algo para ser usado várias vezes;
    - O conceito de fragment consiste na criação de um conteiner para envolver dois ou mais componentes, sem reproduzir efeito visual na página do browser, o que pode facilitar na estilização posteriormente.

    ```jsx
    import React from 'react';

    import Header from './components/Header';

    function App() {
      return (
    // fragment são os sinais <> vazios, sem especificação, por exemplo <div>
    // abertura da tag
        <>
          <Header />
          <Header />
        </>
    // fechamento da tag
      );
    }

    export default App;
    ```
    
## Propriedades

- São as informações que podem ser passadas de um componente pai para um componente filho.

```jsx
import React from 'react';

import Header from './components/Header';

// Componente pai (App)
function App() {
  return (
// Componente filho (Header)
// Propriedade title
    <>
      <Header title="Homepage" />
      <Header title="Projects" />
    </>
  );
}

export default App;
```

- Quando um atributo é aplicado no componente no React, chamamos de propriedade.
- Para acessar o atributo, deve-se passar as propriedades na função Header, por exemplo, e acessá-los através da variável {props.title}.

```jsx
import React from 'react';

export default function Header(props) {
  return (
    <header>
      <h1>{props.title}</h1>
    </header>
  )
}
```

- Ou ainda pode-se também fazer a desestruturação de props e passar apenas o title:

```jsx
import React from 'react';

export default function Header({ title }) {
  return (
    <header>
      <h1>{title}</h1>
    </header>
  )
}
```

- Existe uma propriedade que vem em todos os componentes do React, chamada *children*.
- Para usar esse exemplo, vamos colocar conteúdo dentro da tag Header, como se fosse um menu.
- Children é todo o conteúdo que a tag recebeu.
- Em App.js o código ficará da seguinte maneira.

```jsx
import React from 'react';

import Header from './components/Header';

function App() {
  return (
    <>
      <Header title="Homepage">
// Children
        <ul>
          <li>Homepage</li>
          <li>Projects</li>
        </ul>
      </Header>
      <Header title="Projects">
        <ul>
          <li>Homepage</li>
          <li>Projects</li>
          <li>Login</li>
        </ul>
      </Header>
    </>
  );
}

export default App;
```

- E no arquivo de Header.js, adicionaremos a propriedade *children*.

```jsx
import React from 'react';

export default function Header({ title, children }) {
  return (
    <header>
      <h1>{title}</h1>

      {children}
    </header>
  )
}
```

## Estado e Imutabilidade

### Estado

- Armazenar e manipular alguma informação dentro do componente App, como por exemplo, uma listagem de projetos

```jsx
import React from 'react';

import Header from './components/Header';

function App() {
  const projects = ['Desenvolvimento de app', 'Front-end web'];

  return (
    <>
      <Header title="Projects" />
// O map percorre o array de projects e retorna informações de HTML
// Para cada projeto, irei exibir um projeto no HTML
      <ul>
        {projects.map(project => <li key={project}>{project}</li>)}
      </ul>
    </>
  );
}

export default App;
```

- Para que o usuário consiga adicionar mais projetos, podemos criar um botão:

```jsx
import React from 'react';

import Header from './components/Header';

function App() {
  const projects = ['Desenvolvimento de app', 'Front-end web'];

// Sempre que estou lidando com ações do usuário, começo o nome da função com Handle
	function handleAddProject() {
// Para adicionar um novo projeto ao array de projects, basta dar um push no array
// Para que não sejam criados projetos duplicados, passo a função Date.now, o que fará
// passar a data juntamento com o título do projeto
		projects.push(`Novo Projeto ${Date.now()}`);
// Para verificar se os projetos estão sendo adicionados ao array
		console.log(projects);
	}

  return (
    <>
      <Header title="Projects" />

      <ul>
        {projects.map(project => <li key={project}>{project}</li>)}
      </ul>
// Quando o usuário clicar no botão, é preciso disparar uma ação, por isso
// É adicionado um ouvidor de eventos, chamado onClick, ou seja, ele vai ouvir quando
// o usuário clicar no botão e é passada uma função (handleAddProject) para adicionar
// um novo item dentro do projeto, dentro do componente App
      <button type="button" onClick={handleAddProject}></button>
    </>
  );
}

export default App;
```

- Quando adicionado pelo browser, pode-se ver pelo console a adição do "Novo Projeto" juntamente com o time stamp em que foi criado.
- Para que o conceito de estado seja utilizado e as alterações sejam feitas na tela em tempo real, é preciso adicionar a função *useState*.

### Imutabilidade

- Para o conceito de imutabilidade não podemos mutar as variáveis, ou seja, incluir ou excluir informações, e sim recriar as informações com o novo valor.
- O método *push* não respeita a imutabilidade, pois ele altera o valor original do array projects, ou seja, não cria um novo array com essa nova informação.
- No React devemos evitar funções que alteram o valor original. Devemos usar funções que vão gerar novos valores.

```jsx
import React, { useState } from 'react';

import Header from './components/Header';

function App() {
// useState retorna um array com duas posições
// 1. Variável com seu valor inicial (projects)
// 2. Função para atualizarmos esse valor (setProjects) 
  const [projects, setProjects] = useState(['Desenvolvimento de app', 'Front-end web']);

  function handleAddProject() {
// É criado então uma nova informação (novo array), copiado tudo o que já tem dentro
// de projects (... projects) e adicionado o novo projeto
    setProjects([... projects, `Novo Projeto ${Date.now()}`]);
  }

  return (
    <>
      <Header title="Projects" />

      <ul>
        {projects.map(project => <li key={project}>{project}</li>)}
      </ul>

      <button type="button" onClick={handleAddProject}>Adicionar projeto</button>
    </>
  );
}

export default App;
```

- Desta forma, quando for adicionado um novo projeto, a resposta aparecerá em tela também.

## Importando CSS e Imagens

### CSS

- Para adicionar estilo à nossa página, é necessária a adição de novos pacotes loaders, por isso, execute o comando abaixo:

```jsx
$ yarn add style-loader css-loader
```

- Agora é necessária a adição de uma nova regra em nossas configurações Webpack, ficando da seguinte forma:

```jsx
const path = require('path');

module.exports = {
  entry: path.resolve(__dirname, 'src', 'index.js'),
  output: {
    path: path.resolve(__dirname, 'public'),
    filename: 'bundle.js'
  },
  devServer: {
    contentBase: path.resolve(__dirname, 'public'),
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
        }
      },
      {
        test: /\.css$/,
				exclude: /node_modules/,
        use: [
// Pega o CSS que foi interpretado pelo css-loader e injeta dentro do HTML
          { loader: 'style-loader' },
// Lê e interpreta as importações que tem dentro dos arquivos CSS, inclusive imagens
          { loader: 'css-loader' },
        ]
      }
    ]
  }
}
```

- Agora basta criar um arquivo App.css com o seguinte conteúdo:

```jsx
* {
  margin: 0;
  padding: 0;
  outline: 0;
  box-sizing: border-box;
}

body {
  background: #f5f5f5;
  font: 14px sans-serif;
  color: #333333;
}
```

- E importá-lo no App.js, que o Webpack se encarregará de converter o que for necessário:

```jsx
import './App.css';
```

### Imagens

- Deve-se executar o comando abaixo para instalar um novo pacote de loader, para que seja possível carregar arquivos dentro da aplicação:

```jsx
$ yarn add file-loader
```

- Feito isso, deve-se fazer uma nova configuração dentro de Webpack:

```jsx
const path = require('path');

module.exports = {
  entry: path.resolve(__dirname, 'src', 'index.js'),
  output: {
    path: path.resolve(__dirname, 'public'),
    filename: 'bundle.js'
  },
  devServer: {
    contentBase: path.resolve(__dirname, 'public'),
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
        }
      },
      {
        test: /\.css$/,
        exclude: /node_modules/,
        use: [
          { loader: 'style-loader' },
          { loader: 'css-loader' },
        ]
      },
      {
        test: /.*\.(gif|png|jpe?g)$/i,
        use: {
          loader: 'file-loader',
        }
      }
    ]
  }
}
```

- Agora basta importar a imagem dentro do arquivo App.js:

```jsx
import backgroundImage from './assets/background.jpeg';
```

## Listando Projetos da API

### Axios

- Chegamos na parte que iremos conectar a API do back-end com a o front-end.
- Para isso, inicie o servidor do back-end, entrando na pasta do projeto e executando:

```jsx
$ yarn dev
```

- Crie alguns projetos pelo Insomnia, pois nosso front-end ainda não tem essa funcionalidade.
- Agora instale o pacote *axios*, responsável por fazer a conexão entre as duas APIs:

```jsx
$ yarn add axios
```

- Agora crie uma pasta dentro de *src* chamada *services*, e dentro de *services* crie um arquivo *api.js*.
- A pasta services pode ser utilizada como a pasta que vai armazenar qualquer tipo de arquivo que vai fornecer a comunicação com algum serviço externo.

```jsx
import axios from 'axios';

// Criação de uma instância do axios
const api = axios.create({
  baseURL: 'htto://localhost:3333'
});

export default api;
```

- Agora basta importar o arquivo *api* para dentro de *App.js:*

```jsx
import api from './services/api';
```

- Assim que o componente App for exibido em tela, preciso carregar as informações de projetos que estão contidas na API.
- Iremos utilizar a função useEffect, que serve para disparar funções sempre que tivermos alguma informação alterada ou simplesmente disparar a função assim que o componente for exibido em tela.

```jsx
import React, { useState, useEffect } from 'react';
import api from './services/api';

import './App.css';
import backgroundImage from './assets/background.jpeg';

import Header from './components/Header';

function App() {
  const [projects, setProjects] = useState(['Desenvolvimento mobile', 'Front-end web']);

// O useEffect recebe dois parâmetros:
// 1. Qual função eu desejo disparar
// 2. Quando eu quero disparar.
  useEffect(() => {
// método get
// quando o api.get('projects') retornar uma resposta, o then vai disponibilizar a
// seguinte resposta

	api.get('projects').then(response => {
		console.log(response);
	});

// Se eu desejo que essa função seja disparada toda vez que houver uma alteração
// em projects, eu coloco [projects].

// Se eu quiser que ela seja disparada somente uma vez, assim que meu componente
// for mostrado em tela, eu deixo o array vazio.

// Este array é conhecido como array de dependências. Nele iremos incluir
// principalmente as variáveis que utilizamos dentro da primeira função, pois
// obrigatoriamente e bem provavelmente, se estivermos usando alguma variável
// dentro dessa função, quer dizer que quando essa variável alterar, você quer
// executar essa função novamente.

// O array ficará vazio, pois eu quero que a função seja disparada somente quando o
// componente for exibido em tela e dentro dela buscaremos nossos dados da API
 }, []);

  function handleAddProject() {

    setProjects([...projects, `Novo Projeto ${Date.now()}`]);
  }

  return (
    <>
      <Header title="Projects" />

      <img width={300} src={backgroundImage} />

      <ul>
        {projects.map(project => <li key={project}>{project}</li>)}
      </ul>

      <button type="button" onClick={handleAddProject}>Adicionar projeto</button>
    </>
  );
}

export default App;
```

- No Console aparece a informação de Data, que é o que usaremos para preencher os meus projetos (setProjects).

```jsx
import React, { useState, useEffect } from 'react';
import api from './services/api';

import './App.css';
import backgroundImage from './assets/background.jpeg';

import Header from './components/Header';

function App() {
// Devemos também, iniciar nossos projetos com o array vazio, pois agora, nosso
// back-end retorna um objeto, com id, title e owner
// Devo inicializar meu estado com uma informação do mesmo tipo que a informação
// que irei armazenar nas variáveis (projects, set Projects)
 const [projects, setProjects] = useState([]);

  useEffect(() => {
    api.get('projects').then(response => {
      setProjects(response.data);
    })
  }, []);

  function handleAddProject() {

    setProjects([...projects, `Novo Projeto ${Date.now()}`]);
  }

  return (
    <>
      <Header title="Projects" />

      <img width={300} src={backgroundImage} />

      <ul>
        {projects.map(project => <li key={project.id}>{project.ti}</li>)}
      </ul>

      <button type="button" onClick={handleAddProject}>Adicionar projeto</button>
    </>
  );
}

export default App;
```

- *project.title*: preciso que retorne apenas o valor do title, pois não conseguirá listar o valor inteiro de project.
- *project.id*: informação única dentro de cada projeto

### Cors

- Sempre que o front-end vai se conectar com o back-end, temos algumas técnicas de segurança no back-end para evitar que front-ends que não são da nossa aplicação possam fazer requisições e obter esses dados .
- Vamos adicionar um comando no projeto do back-end para que o front-end consiga acessar o back-end sem que ele seja barrado pela segurança.
- Para isso, abra a pasta do projeto no Visual Studio Code e instalar um módulo chamado *Cors*:

```jsx
$ yarn add cors
```

- Agora dentro do arquivo *index.js* devemos importar o *cors*, e adicionar a linha seguinte, logo abaixo da criação do app:

```jsx
const express = require('express');
const cors = require('cors');
const { uuid, isUuid } = require('uuidv4');

const app = express();

// Adicionar essa linha
// Dentro do cors podemos passar uma configuração falando qual é a origem/endereço
// do nosso front-end que terá acesso às informações do nosso back-end
app.use(cors()); 
app.use(express.json());

const projects = [];

function logRequests(req, res, next) {
  const { method, url } = req;

  const logLabel = `[${method.toUpperCase()}] ${url}`;
  
  console.log('1');
  console.time(logLabel);

  next();

  console.log('2');
  console.timeEnd(logLabel);
}

function validateProjectId(req, res, next) {
  const { id } = req.params;

  if (!isUuid(id)) {
    return res.status(400).json({ error: 'Invalid project ID.' });
  }

  return next();
}

app.use(logRequests);
app.use('/projects/:id', validateProjectId);

app.get('/projects', (req, res) => {
  console.log('3');

  const { title } = req.query;

  const results = title
    ? projects.filter(project => project.title.includes(title))
    : projects;

  return res.json(results);
});

app.post('/projects', (req, res) => {
  const { title, owner } = req.body;

  const project = { id: uuid(), title, owner };

  projects.push(project);

  return res.json(project);
})

app.put('/projects/:id', (req, res) => {
  const { id } = req.params;
  const { title, owner } = req.body;

  const projectIndex = projects.findIndex(project => project.id === id);

  if (projectIndex < 0) {
    return res.status(400).json({ error: 'Project not found' });
  }

  const project = {
    id,
    title,
    owner,
  }

  return res.json(project);
})

app.delete('/projects/:id', (req, res) => {
  const { id } = req.params;

  const projectIndex = projects.findIndex(project => project.id === id);

  if (projectIndex < 0) {
    return res.status(400).json({ error: 'Project not found' });
  }

  projects.splice(projectIndex, 1);

  return res.status(204).send();
})

app.listen(3333, () => {
  console.log('Back-end started!')
});
```

- Em ambiente de desenvolvimento não é preciso passar tais configurações, porém quando estivermos em ambiente de produção, será necessário informar qual o endereço do front-end:

```jsx
app.use(cors({
	origin: 'http://localhost:3000'
})); 
```

## Cadastrando Projetos

- Para poder utilizar async/await dentro do projeto, é necessário instalar um plugin do babel para que ele consiga interpretar:

```jsx
$ yarn add @babel/plugin-transform-runtime -D
```

- Deve-se adicionar dentro da função handleAddProject as instruções para criação de projeto pelo front-end:

```jsx
async function handleAddProject() {
    const response = await api.post('projects', {
      title: `Novo Projeto ${Date.now()}`,
      owner: 'Raquel Rodrigues',
    });

    const project = response.data;

    setProjects([...projects, project]);
  }
```
