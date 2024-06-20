## Tutorial passo a passo: Como iniciar um site com VitePress

Já ouviu falar da ferramenta VitePress? Bem, VitePress nada mais é que uma ferramenta de geração de sites estáticos projetada para construção mais rápida de sites centrados em conteúdo. Resumindo, o VitePress pega seu conteúdo fonte escrito em Markdown, aplica um tema a ele e gera páginas HTML estáticas que podem ser facilmente implantadas em qualquer lugar.

## Qual a vantagem de usar o VitePress?
Diferente de outros SSGs (da sigla em inglês Static Site Generator ou gerador de site estático), onde cada navegação gera um recarregamento de página completo, um site gerado pelo VitePress serve HTML estático na visita inicial, mas se torna uma Aplicação de Página Única (SPA/Sigle Page Application) para navegação subsequente dentro do site.

## que será abordado
Neste tutorial, vou trazer uma série de conteúdos passo a passo de como criar um site VitePress. Nesse primeiro momento, vamos começar inicializando a aplicação e criando um conteúdo Markdown para ser renderizado em HTML na máquina local.

## O que vamos fazer
- Iniciar um projeto em Node.js para dar início ao projeto
- Criar via CLI o arquivo `package.json` para gerenciamento de dependências
- Instalar via CLI as dependências do VitePress
- Inicializar via CLI o assistente de instalação do VitePress, que ajuda a construir um projeto básico

## Tecnologias usadas:
- [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [NodeJs](https://nodejs.org/en/download)
- [VSCode](https://code.visualstudio.com/download)
- Gerenciador de pacotes `npm` que vem por padrão com Node.js.

## Mão na massa
1. Primeiro, crie um diretório no local de sua preferência e abra o VSCode.
2. Abra o terminal na raiz do projeto e escreva ``` npm init ```. Será gerado o arquivo `package.json`.
3. Em seguida, continue no diretório raiz no terminal e coloque `npm add -D vitepress`. Espere a instalação ser concluída, pode demorar um pouco dependendo da máquina.
4. Agora vamos iniciar o assistente de instalação com `npx vitepress init`. Você terá que responder algumas perguntas:

```
┌  Welcome to VitePress!
│
◇  Where should VitePress initialize the config?
│  ./
│
◇  Site title:
│  My Awesome Project
│
◇  Site description:
│  A VitePress Site
│
◆  Theme:
│  ● Default Theme (Out of the box, good-looking docs)
│  ○ Default Theme + Customization
│  ○ Custom Theme
└
```

Se você estiver construindo um site VitePress individual, você pode desenvolver seu site no diretório atual (`./`). Entretanto, se você está instalando VitePress em um projeto existente juntamente com outro código-fonte, é recomendado construir o site em um diretório aninhado (ex., `./docs`) para que esteja separado do resto do seu projeto.

Vamos assumir que sua escolha foi desenvolver o projeto em "./" (`./seudiretorio`). A estrutura de arquivos deve ficar assim:

```
.
├─ /seudiretorio
│  ├─ .vitepress
│  │  └─ config.js
│  ├─ api-examples.md
│  ├─ markdown-examples.md
│  └─ index.md
└─ package.json
```

Até aqui deve ter também injetado os seguintes scripts npm no seu `package.json`:

```
{
 
  "scripts": {
    "docs:dev": "vitepress dev docs",
    "docs:build": "vitepress build docs",
    "docs:preview": "vitepress preview docs"
  },

}
```

O script `docs:dev` iniciará um servidor de desenvolvimento local com atualizações instantâneas. Rode-o com o seguinte comando:
```
npm run docs:dev
``` 

Em vez de scripts npm, você também pode invocar VitePress diretamente com:
```
npx vitepress dev docs
```
### Uma sitação rápida sobre a diferença entre npm e npx
- `npm` é usado principalmente para instalar, remover e gerenciar pacotes de Node.js.
Ele armazena informações sobre os pacotes instalados no arquivo package.json.
Resumindo, ele faz a intalação previamente dos pacotes e os gerencia.

- `npx` é uma ferramenta projetada para ajudar a executar pacotes de Node.js
  sem a necessidade de instalação prévia. Ele pode executar pacotes que estão
  no node_modules, globalmente instalados, ou mesmo baixar temporariamente um pacote para executá-lo.

Tendo isso explicado, temos que no nosso contexto é interessane o uso do comando `npm run docs:dev` 
já temos configurado o script no package.json que nos facilita rodar a aplicação com npm.


O servidor de desenvolvimento deve estar rodando em http://localhost:5173.
Visite a URL no seu navegador para ver o seu novo site em ação!

Podemos ver que é gerado um layout padrão, mas nesse momento, não vamos nos aprofundar na esturura do sistema. O que devemos saber é que o arquivo `config.js`
permite que você personalize vários aspectos do seu site VitePress. Mas como dissemos antes não vamos entrar em detalhes para não gerar confusão.
O arquivo `index.md` é a porta de entrada da aplicação quando acessar a url correspondente, vamos deixa-lo do jeito que está. Vamos usa-lo como exemplo
para o que podemos fazer com vitepress.

Para continuarmos, na raiz do projeto, vamos criar um arquivo `about.md`. Este nome poderia ser qualquer um, mas aqui vamos escolher este. Este é um arquivo Markdown,
o VitePress será inteligente o bastante para ler este arquivo e transformá-lo em HTML quando acessarmos a URL http://localhost:5173/about.

Neste momento, podemos fazer algo simples e demonstrativo para observar a facilidade de trabalhar com o VitePress.
Vamos criar um conteúdo simples em Markdown e veremos que, no final, o VitePress será capaz de transformá-lo em HTML.

Dentro do arquivo `about.md` pode colocar por exemplo:

```
# Bem-vindo ao Meu Portfólio
Este é meu portfólio, venho mostrar aqui os meus projetos que venho trabalhando ao longo de etc...

## Projetos Destacados

### Projeto 1: E-commerce 

Este é um projeto E-commmerce que uni simplicidade e objetivo em um unico local...

[Veja no GitHub](https://github.com/seugithub)

### Projeto 2: Aplicatico escolar

Neste aplicativo é possível gerenciar uma escolha de forma prática e consistente facilitando...

[Veja no GitHub](https://github.com/seugithub)

## Sobre Mim

Sou apaixonado por desenvolvimento de software e adoro criar soluções inovadoras para problemas complexos. Tenho experiência com etc...

[Saiba mais](/sobre)

## Contato

Sinta-se à vontade para entrar em contato comigo através de [LinkedIn](https://www.linkedin.com/seuLinkedin) ou [Email](mailto:seuemail@gmail.com).

```
Vamos então rodar o comando `npm run docs:dev` e acessar a URL [`localhost:5173/about`](http://localhost:5173/about). Atente-se ao recurso “about” que é o nome do seu arquivo Markdown.

Podemos ver que ao acessar a URL, uma página HTML foi gerada. Mas como podemos saber que realmente é uma página HTML? Simples, ao inspecionar a página, vemos que todo o conteúdo está em HTML.
Nesta aula não vamos nos atentar a estilização então podemos pausar aqui. Explore um pouco a estrutura e se desafie a criar algo que seja interessante para você.

Pronto! Agora você está com seu ambiente de desenvolvimento pronto para criar conteúdos com VitePress. No próximo tutorial, vamos explorar como personalizar e adicionar novos conteúdos ao site.
