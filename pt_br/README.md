# Uma Introdução ao Elm

**Elm é uma linguagem funcional que compila para JavaScript.** Ele concorre com projetos como React sendo uma ferramenta para criar sites e aplicações web. Elm tem uma forte ênfase em simplicidade, facilidade de uso e ferramental de qualidade.

Este guia irá:

  - Te ensinar o básico de como programar em Elm.
  - Te mostrar como fazer aplicações interativas com a *Elm Architecture*(Arquitetura Elm).
  - Enfatizar princípios e padrões que difundem para programação em qualquer linguagem.
  
Ao fim, eu espero que não apenas você seja capaz de criar grandes aplicações web em Elm, como também entenda as principais idéias e padrões que fazem Elm agradável de usar.

Se você está em cima do muro, posso garantir que se você der uma chance ao Elm e fizer um projeto com ele, você acabará escrevendo códigos React e Javascript de uma forma melhor. As idéias se transferem facilmente.


## Um Exemplo Rápido

Claro que *eu* acho Elm bom, então veja você mesmo.

Aqui tem [um simples contador](http://elm-lang.org/examples/buttons). Se você olhar o código, ele apenas deixa você incrementar e decrementar o contador:

```elm
import Html exposing (Html, button, div, text)
import Html.Events exposing (onClick)

main =
  Html.beginnerProgram { model = 0, view = view, update = update }

type Msg = Increment | Decrement

update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1

view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (toString model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]
```

Note que as funções `update` e `view` são completamente desacopladas.Você descreve seu HTML de forma declarativa e o Elm cuida de mexer no DOM.


## Por que uma linguagem *funcional*?

Esqueça o que você tem ouvido sobre programação funcional. Palavras esquisitas, idéias estranhas, ferramental ruim. Elm é sobre:

  - Sem 'runtime errors' na prática. Sem `null`. Sem '`undefined` is not a function'.
  - Mensagens de erro amigáveis que ajudam você a adicionar 'features' rapidamente.
  - Código bem arquitetado que *continua* bem arquitetado conforme sua aplicação cresce.
  - Versionamento semântico aplicado automaticamente a todos os pacotes Elm.
  
Nenhuma combinação de bibliotecas JS pode te oferecer isto, porém tudo isso vem de graça e fácil no Elm. Agora estas coisas legais são possíveis *apenas* por que Elm baseia-se em 40+ anos de trabalho em linguagens funcionais tipadas. Então Elm é uma linguagem funcional por que os benefícios práticos valem algumas horas que você gastará lendo este guia.

Eu tenho colocado uma grande ênfase em fazer Elm fácil de aprender e usar, tudo que peço é que você dê uma chance ao Elm e veja o que pensa. Espero que seja uma grande surpresa!
