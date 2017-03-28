> **Nota:** Se você não quiser instalar ainda, você pode acompanhar esse guia com o [editor online](http://elm-lang.org/try) e o [REPL online](http://elmrepl.cuberoot.in/).

# Instalação

* Mac &mdash; [instalador][mac]
* Windows &mdash; [instalador][win]
* Anywhere &mdash; [instalador npm ][npm] ou [gerar a partir do source][build]

[mac]: http://install.elm-lang.org/Elm-Platform-0.18.pkg
[win]: http://install.elm-lang.org/Elm-Platform-0.18.exe
[npm]: https://www.npmjs.com/package/elm
[build]: https://github.com/elm-lang/elm-platform

Após instalar por qualquer uma dessas rotas, você terá disponíveis as seguintes ferramentas em linha de comando:

- [`elm-repl`](#elm-repl) &mdash; brinque com expressões em Elm
- [`elm-reactor`](#elm-reactor) &mdash; coloque rapidamente um projeto pra rodar
- [`elm-make`](#elm-make) &mdash; compile código Elm diretamente
- [`elm-package`](#elm-package) &mdash; faça download de pacotes

Veremos com mais detalhes como cada uma delas funciona assim que configurarmos seu editor!

> **Tira-dúvidas:** O jeito mais rápido de aprender *qualquer coisa* é conversando com o pessoal da comunidade Elm. Somos amigáveis e estamos sempre felizes em ajudar!  Então, se você estiver empacado em alguma etapa da instalação ou encontrar alguma coisa estranha, viste o [Elm Slack](http://elmlang.herokuapp.com/) e faça uma pergunta. Na verdade, se você encontrar alguma coisa confusa em qualquer situação enquanto estiver aprendendo ou usando Elm, apareça e nos pergunte sobre isso. Você poderá economizar horas. Apenas venha e pergunte!


## Configure seu Editor

Usar Elm é muito mais legal quando você tem um editor de código para te ajudar. Existem plugins de Elm disponíveis para pelo menos os seguintes editores:

  * [Atom](https://atom.io/packages/language-elm)
  * [Brackets](https://github.com/lepinay/elm-brackets)
  * [Emacs](https://github.com/jcollard/elm-mode)
  * [IntelliJ](https://github.com/durkiewicz/elm-plugin)
  * [Light Table](https://github.com/rundis/elm-light)
  * [Sublime Text](https://packagecontrol.io/packages/Elm%20Language%20Support)
  * [Vim](https://github.com/lambdatoast/elm.vim)
  * [VS Code](https://github.com/sbrink/vscode-elm)

Se você não tem nenhum editor ainda, o [Sublime Text](https://www.sublimetext.com/) é uma boa pedida para começar!

Você também deveria tentar utilizar o [elm-format][] que deixa o seu código bem mais bonito!

[elm-format]: https://github.com/avh4/elm-format


## As ferramentas em linha de comando

Então, instalamos o Elm e ele nos deu `elm-repl`, `elm-reactor`, `elm-make`, e `elm-package`. Mas o que exatamente tudo isso faz?

### elm-repl

[`elm-repl`](https://github.com/elm-lang/elm-repl) permite que você brinque com as expressões em Elm

```bash
$ elm-repl
---- elm-repl 0.18.0 -----------------------------------------------------------
 :help for help, :exit to exit, more at <https://github.com/elm-lang/elm-repl>
--------------------------------------------------------------------------------
> 1 / 2
0.5 : Float
> List.length [1,2,3,4]
4 : Int
> String.reverse "stressed"
"desserts" : String
> :exit
$
```

Nós usaremos o `elm-repl` na próxima seção &ldquo;Core da Linguagem&rdquo;. Você pode ler mais sobre como ele funciona [aqui](https://github.com/elm-lang/elm-repl/blob/master/README.md).

> **Nota:** `elm-repl` funciona compilando código para JavaScript, então certifique-se de ter o [Node.js](http://nodejs.org/) instalado, pois ele será utilizado para avaliar o código.


### elm-reactor

[`elm-reactor`](https://github.com/elm-lang/elm-reactor) te ajuda a montar seus projetos em Elm sem precisar ficar mexendo demais com a linha de comando. Você simplesmente executa ele na raiz de seu projeto, assim:

```bash
git clone https://github.com/evancz/elm-architecture-tutorial.git
cd elm-architecture-tutorial
elm-reactor
```
Ele vai iniciar um servidor em [`http://localhost:8000`](http://localhost:8000). Você pode navegar por quaisquer arquivos Elm e ver como eles são. Dê uma olhada em `examples/01-button.elm`.

**Flags importantes:**

- `--port` te deixa escolher uma porta diferente da porta 8000. Ou seja, você pode escrever
  `elm-reactor --port=8123` para fazer as coisas rodarem em `http://localhost:8123`.
- `--address` te deixa substituir `localhost` por algum outro endereço. Por exemplo, você talvez queira utilizar `elm-reactor --address=0.0.0.0` se quiser testar um programa em Elm em um disposivo móvel conectado à sua rede local.

## elm-make

[`elm-make`](https://github.com/elm-lang/elm-make) monta os projetos em Elm. Ele pode compilar código Elm para HTML ou JavaScript. É a maneira mais genérica de compilar código Elm, ou seja, caso seu projeto se torne muito avançado para o `elm-reactor`, você vai preferir utilizar `elm-make` diretamente.


Digamos que você queira compilar `Main.elm` para um arquivo HTML chamado `main.html`. Você rodaria este comando:

```bash
elm-make Main.elm --output=main.html
```

**Flags importantes:**

- `--warn` imprime alertas para melhorar a qualidade do código

### elm-package

[`elm-package`](https://github.com/elm-lang/elm-package) faz downloads e publica pacotes de nosso [catálogo de pacotes](http://package.elm-lang.org/). À medida que membros da comunidade resolvem os problemas [de um jeito legal](http://package.elm-lang.org/help/design-guidelines), eles compartilham seus códigos no catálogo de pacotes para qualquer um utilizar!

Digamos que você queira utilizar [`elm-lang/http`][http] e [`NoRedInk/elm-decode-pipeline`][pipe] para fazer requisições  HTTP para um servidor e transformar o JSON de resposta em valores Elm. Você escreveria:

[http]: http://package.elm-lang.org/packages/elm-lang/http/latest
[pipe]: http://package.elm-lang.org/packages/NoRedInk/elm-decode-pipeline/latest

```bash
elm-package install elm-lang/http
elm-package install NoRedInk/elm-decode-pipeline
```

This will add the dependencies to your `elm-package.json` file that describes your project. (Or create it if you do not have one yet!) More information about all this [here](https://github.com/elm-lang/elm-package)!

Isso irá adicionar as dependências a seu arquivo `elm-package.json`, que descreve seu projeto, ou irá criá-lo caso não tenha um ainda! Mais informações sobre tudo isso [aqui](https://github.com/elm-lang/elm-package)!


**Comandos importantes:**

- `install`: instala as dependências em `elm-package.json`
- `publish`: publica sua biblioteca no Elm Package Catalog (catálogo de pacotes do Elm)
- `bump`: incrementa os números de versão baseados em modificações na API
- `diff`: verifica a diferença entre duas APIs
