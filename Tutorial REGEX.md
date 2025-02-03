
### Tutorial REGEX

Texto como exemplo: “número do empenho: 1566/2025 Valor do empenho: R$ 150,00 Data do empenho: 02/01/2025” 

Nesse trecho temos duas informações importantíssimas para o formulário (data e número) e uma (valor) que pode ser mapeada para futura utilização num formulário por exemplo; 

Para mapear, vamos utilizar uma pesquisa genérica chamada expressão regular. Por exemplo, se pesquisarmos o texto “número do empenho: 1566/2025” no Word, ele encontrará o texto e o destacará. Isso é uma pesquisa direta, pois sabemos o valor exato a ser encontrado. Agora, como podemos fazer essa pesquisa de forma que ela seja dinâmica e encontre qualquer número, independentemente do valor?

Para deixar dinâmico a captura desse texto vamos criar um molde de pesquisa utilizando a expressão regular: 

Antes vamos conhecer algumas palavras chaves para utilizar na pesquisa; 

\d : captura um único número de 0-9; exemplo "abc123def456", pesquisando com esse termo vai localizar apenas o primeiro numero ou seja o valor "1"

\d+ : captura uma cadeia de números de 0-9, pelo menos um número é necessário para a pesquisa funcionar;  pesquisando com esse termo vai localizar a primeira cadeia de números ou seja vai capturar o valor "123";

Nesse início vemos que a letra d dessa palavra chave “\d” se refere a um grupo de decimais, existem outros grupos como “\w” word (letras), “\s” space (espaço comum, tabulação, quebra de página), veja no final mais palavras chaves; 

Agora vamos desenvolver uma pesquisa dinâmica com essas palavras chaves em cima da pesquisa direta que trabalhamos acima: "número do empenho: 1566/2025";

vamos convencionar que apenas queremos que o número 1566 seja dinamico na pesquisa, assim vamos preservar uma estrura para a pesquisa e trocar apenas o número 1566 pela palavra chave de números decimais \d "número do empenho: \d+/2025", pense nisso como uma ordem dada ao sistema assim: (localize o texto  "número do empenho: " seguido de números e seguido do texto "/2025"!).

Nesse exemplo fizemos uma pesquisa dinamica para o número 1566, agora vamos ao passo seguinte, que é riar a captura utilizando e dar um nome ao valor: 

Vamos definir que o número 1566/2025 vai ser o número do anexo no SEI que preenchemos ao anexar um arquivo.

até então temos a nossa pesquisa "número do empenho: \d+/2025", a informação que é útil para nós é o número do anexo "\d+/2025";

obs. na extensão a chave do valor que preenche o número do anexo é a "numeroAnexo"

Para capturar essa informação da pesquisa montada vamos circular ela com esse molde: “`(?<chave>informação a ser capturada)`” e ela ficará assim "número do empenho: `(?<numeroAnexo>\d+/2025)`"

com isso criamos a primeira captura para definir o número do anexo;



#### Palavras Chaves de Pesquisa com Regex (JavaScript)

Aqui estão algumas palavras chaves de pesquisa utilizando expressões regulares compatíveis com JavaScript:

- `\d` : Captura um único dígito (0-9).

- `\d+` : Captura uma sequência de um ou mais dígitos.

- `\w` : Captura um caractere alfanumérico (letras e números) ou underscore (_).

- `\w+` : Captura uma sequência de um ou mais caracteres alfanuméricos ou underscores.

- `\s` : Captura qualquer caractere de espaço em branco (espaço, tabulação, quebra de linha).

- `\S` : Captura qualquer caractere que não seja espaço em branco.

- `.` : Captura qualquer caractere, exceto quebras de linha.

- `.*` : Captura zero ou mais ocorrências de qualquer caractere, exceto quebras de linha.

- `^` : Indica o início de uma linha.

- `$` : Indica o final de uma linha.

- `\b` : Captura uma borda de palavra (início ou fim de uma palavra).

- `\B` : Captura uma posição que não seja uma borda de palavra.

- `[abc]` : Captura qualquer caractere dentro dos colchetes. Por exemplo, `[abc]` captura 'a', 'b', ou 'c'.

- `[a-z]` : Captura qualquer caractere de 'a' a 'z'.

- `[A-Z]` : Captura qualquer caractere de 'A' a 'Z'.

- `[0-9]` : Captura qualquer dígito de '0' a '9'.

- `[a-zA-Z0-9]` : Captura qualquer caractere alfanumérico.

- `[^abc]` : Captura qualquer caractere que não seja 'a', 'b', ou 'c'.

- `[^a-z]` : Captura qualquer caractere que não esteja entre 'a' e 'z'.

- `[^A-Z]` : Captura qualquer caractere que não esteja entre 'A' e 'Z'.

- `[^0-9]` : Captura qualquer caractere que não seja um dígito de '0' a '9'.

- `[^a-zA-Z0-9]` : Captura qualquer caractere que não seja alfanumérico.




Exemplos de uso:

- Capturar um número de telefone no formato (43) 99456-7890:

    ```regex

    (?<telefone>\(\d{2}\) \d{5}-\d{4})

```

- Capturar um endereço de email:

```regex

(?<email>[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,})

```

- Capturar uma data no formato DD/MM/YYYY:

```regex

(?<data>\d{2}/\d{2}/\d{4})

```

- Capturar um CPF no formato 123.456.789-00:

    ```regex

    (?<CPF>\d{3}\.\d{3}\.\d{3}-\d{2})

    ```

- Capturar um CNPJ no formato 12.345.678/0001-00:

    ```regex

    (?<CNPJ>\d{2}\.\d{3}\.\d{3}/\d{4}-\d{2})

    ```

lembrando que sempre que possível utilize parte do texto que vem antes ou depois, caso esses sejam úteis para determinar com precisão o valor que vai capturar, por exemplo:

- Capturar um CNPJ no formato 12.345.678/0001-00:

    ```regex

    CNPJ: (?<CNPJ>\d{2}\.\d{3}\.\d{3}/\d{4}-\d{2})

    ```

se o CNPJ sempre vier com "CNPJ: " antes do número, procure utilizar esse texto antes a seu favor.

#### Escapando Caracteres Especiais em Regex

Em expressões regulares, alguns caracteres têm significados especiais e precisam ser escapados com uma barra invertida (`\`) para serem usados literalmente. Aqui estão alguns exemplos:

- `\[` : Escapa o caractere de colchete esquerdo `[`.

- `\]` : Escapa o caractere de colchete direito `]`.

- `\(` : Escapa o caractere de parêntese esquerdo `(`.

- `\)` : Escapa o caractere de parêntese direito `)`.

- `\{` : Escapa o caractere de chave esquerda `{`.

- `\}` : Escapa o caractere de chave direita `}`.

- `\.` : Escapa o ponto `.`.

- `\*` : Escapa o asterisco `*`.

- `\+` : Escapa o sinal de mais `+`.

- `\?` : Escapa o ponto de interrogação `?`.

- `\\` : Escapa a barra invertida `\`.

- `\|` : Escapa a barra vertical `|`.

- `\^` : Escapa o acento circunflexo `^`.

- `\$` : Escapa o cifrão `$`.

Exemplo de uso:

- Para capturar um texto que contém colchetes, como `[exemplo]`:

    ```regex

    \[exemplo\]

    ```

Esses caracteres especiais precisam ser escapados para serem interpretados literalmente em uma expressão regular.

#### Guia Completo de Expressões Regulares

Para um guia completo e detalhado sobre expressões regulares, você pode consultar o seguinte link:

[Guia Completo de Expressões Regulares (MDN Web Docs)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Regular_Expressions)

Este guia fornece uma visão abrangente sobre o uso de expressões regulares em JavaScript, incluindo exemplos práticos e explicações detalhadas.


#### Utilizando Grupos para Captura Nomeada

O foco principal ao trabalhar com expressões regulares na extensão é a utilização de grupos para capturar informações específicas de forma nomeada.

Por exemplo, considere a expressão regular `(?<chave>\d\w[a-z]+)`. Aqui está o que cada parte faz:

- `(?<chave>...)` : Define um grupo de captura nomeada chamado `chave`.

- `\d` : Captura um único dígito (0-9).

- `\w` : Captura um caractere alfanumérico (letras e números) ou underscore (_).

- `[a-z]+` : Captura uma sequência de um ou mais caracteres de 'a' a 'z'.

Essa expressão regular captura um dígito seguido por um caractere alfanumérico e uma sequência de letras minúsculas, e armazena o resultado no grupo nomeado `chave`.

Vamos aplicar isso em um exemplo prático. Suponha que queremos capturar um número de identificação seguido por uma palavra:

Texto: "ID123abc"

Expressão Regular: `ID(?<id>\d\w[a-z]+)`

Aplicando a expressão regular ao texto, o grupo nomeado `id` capturará "123abc".
