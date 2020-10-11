# emoji_initialization_issue
[English](#english) below.</br>
Um caso-exemplo (mínimo, completo e verificável) em [Flutter](https://github.com/flutter) para demonstrar um bug da implementação do SDK. Cada branch relata um workaround sugerido.

Descrição do bug: Alguns emojis são formados por dois caracteres unicode. Esses quando são exibidos em um [Text Widget](https://api.flutter.dev/flutter/widgets/Text-class.html) no estado inicial logo após a compilação, tem sua renderização errada (mostra apenas o primeiro caracter). Após mudar o texto exibido, e mudar de volta, o bug não ocorre. Hot-restart ou Hot-reload não faz o bug ocorrer novamente, apenas uma nova compilação.

Esse bug foi perguntado primeiramente [aqui](https://stackoverflow.com/questions/59081353/text-widget-with-wrong-emoji-on-initialization-in-flutter). Na ausência de uma resposta, foi aberta essa [issue](https://github.com/flutter/flutter/issues/45947) no repositório oficial, onde foi explicado e constatado que trata-se de um bug. Foram sugeridas soluções (denominadas workarounds). Maiores explicações e detalhes podem ser encontrados nos links. Em suma, as sugestões foram:

 - Instanciar um parágrafo que utiliza uma fonte que possui o emoji para forçar o pré-cache desta.
 - Enumerar uma fonte de emojis no atributo "fontFamilyFallback" ou "fontFamily" do TextStyle. (Não consegui fazer funcionar sem a utilização de algum pacote de terceiros que incluem fontes personalizadas.)


## Descrição das branches


- master: Exemplo onde o bug ocorre
- workaround1: Criação de um parágrafo para pré-cache.
- workaround2: Adição de uma fonte de fallback.

### English
--- 

A minimal reproducible example, written in [Flutter](https://github.com/flutter) to show a implementation bug of the SDK. Each branch shows a suggested workaround.

Description: A few emoji are formed by two Unicode characters. When shown in a [Text Widget](https://api.flutter.dev/flutter/widgets/Text-class.html) in the first state after compilation, they are wrongly rendered (Only first character is shown). After changing the text and changing it back, the bug won't happen anymore. Hot-restarting and hot-reloading won't make the bug happen again. Only a fresh new build.

This problem was first asked [here](https://stackoverflow.com/questions/59081353/text-widget-with-wrong-emoji-on-initialization-in-flutter). Without answers, this [issue](https://github.com/flutter/flutter/issues/45947) was open in the official repo, where it was explained and stated that it's indeed a bug. A few solutions were suggested. For more info, check the links above. The suggestions were:

- Instantiate a paragraph using a font that contains the emoji to force the pre-cache of the font.
- Enumarate a different font in the "fontFamilyFallback" or "fontFamily" of the TextStyle. I couldn't make this work without the use of a third-part package with custom fonts.
