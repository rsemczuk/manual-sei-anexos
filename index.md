# Sumário

- [VISÃO GERAL](#visão-geral)
- [O QUE IRÁ APRENDER](#o-que-irá-aprender)
- [PARAMETRIZANDO ARQUIVOS E DOCUMENTOS](#parametrizando-arquivos-e-documentos)
    - [Conhecendo Regex e como utilizar para extrair os dados](#conhecendo-regex-e-como-utilizar-para-extrair-os-dados)
    - [Tutorial REGEX](#tutorial-regex)
    - [Palavras Chaves de Pesquisa com Regex (JavaScript)](#palavras-chaves-de-pesquisa-com-regex-javascript)
    - [Escapando Caracteres Especiais em Regex](#escapando-caracteres-especiais-em-regex)
    - [Guia Completo de Expressões Regulares](#guia-completo-de-expressões-regulares)
    - [Utilizando Grupos para Captura Nomeada](#utilizando-grupos-para-captura-nomeada)
- [CRIANDO CONFIGURAÇÕES](#criando-configurações)
    - [Anexar utilizando - REGEX](#anexar-utilizando---regex)
    - [Anexar PDF](#anexar-pdf)
    - [Formulários](#formulários)
    - [Processos](#processos)
    - [Processos relacionados](#processos-relacionados)
    - [Descrição do processo](#descrição-do-processo)
    - [E-mail](#e-mail)
- [OUTRAS FUNÇÕES](#outras-funções)
- [Disponibilizando acesso externo em lote a um documento/processo](#disponibilizando-acesso-externo-em-lote-a-um-documentoprocesso)
- [Verificando ciência de servidores a um determinado processo](#verificando-ciência-de-servidores-a-um-determinado-processo)
- [Utilizando a barra de pesquisa e filtros](#utilizando-a-barra-de-pesquisa-e-filtros)
- [Ativando alerta de blocos de assinatura disponibilizados para o setor](#ativando-alerta-de-blocos-de-assinatura-disponibilizados-para-o-setor)
- [Utilizando a caixa de se seleção para copiar dados](#utilizando-a-caixa-de-se-seleção-para-copiar-dados)
- [Ativando funções da extensão](#ativando-funções-da-extensão)


# VISÃO GERAL 

A extensão “SEI-ANEXOS” apresenta uma série de ferramentas desenvolvidas para aumentar e padronizar a produtividade no ambiente de produção do Sistema Eletrônico de Informações (SEI). 

O seu funcionamento se baseia em parametrizar os dados dos documentos (doc, xls, xlsx, pdf, txt, csv, etc.) para utilizá-los na automatização de funções como: anexar, preencher formulário, preencher Email etc. 

Com isso, o objetivo é elevar os procedimentos realizados no SEI a outro nível, garantindo eficiência e consistência nas atividades diárias. Por meio da implementação dessas ferramentas para parametrizar os dados e como utilizar, espero ensinar o básico para que possa utilizar a extensão a fim de padronizar documentos e consequentemente, aprimorar a qualidade do serviço prestado. 

Você terá liberdade para adotar as melhores práticas que considerar para o seu setor do SEI, alinhando as necessidades específicas dos usuários do SEI. 

 

# O QUE IRÁ APRENDER 



Parametrizar arquivos e documentos para extrair dados; 


- utilizar a Função "Inserir Anexo(s)"



- inserir formulários;

- criar processo SEI;

- gerar processo relacionado;

- reescrever a descrição do processo;

- enviar e-mail;

 

Utilizar outras funções como: 

- disponibilizar acesso externo em lote a um documento/processo;

- verificar ciência de servidores a um determinado processo;

- utilizar a barra de pesquisa e filtros de processos e organizar a tabela;

- ativar/desativar alerta de blocos de assinatura disponibilizados para o setor;

- utilizar a caixa de seleção para copiar dados;

- desativar/ativar funções da extensão;

 

# FUNÇÃO INSERIR ANEXOS
    
os anexos podem ser inseridos através do botão "Anexar arquivo(s)"

![FUNÇÃO INSERIR ANEXOS](gifs/botao_anexar.png)

ou arrastando diretamente na arvore

![FUNÇÃO INSERIR ANEXOS](gifs/arrastar_anexo.gif)


Essa operação de anexar tem as seguintes funções nativas que podem ser aproveitadas;

1- se o arquivo iniciar com "fatura 123" por padrão o tipo do documento externo será "fatura" e o número será "123", esse é um exemplo, isso se existir fatura como documento externo, caso não exista ela tentará selecionar anexo ou anexos se também existir.

2- é possívem incluir essas chaves abaixo no nome do arquivo para alterar propriedades do anexo

- ".caa" altera o tipo de conferência para "Cópia Autenticada Administrativamente"
- ".cac" altera o tipo de conferência para "Cópia Autenticada por Cartório"
- ".cs" altera o tipo de conferência para "Cópia Simples"
- ".do" altera o tipo de conferência para "Documento Original"
- ".ip" altera o acesso para restrito e seleciona "Informacao pessoal"
- ".28-01-2025" altera a data do documento externo para 28/01/2025
escreva o nome de um arquivo como "fatura 123.caa.ip.25-01-2025" e faça um teste para ver o comportamento


![FUNÇÃO INSERIR ANEXOS](gifs/teste_fatura_keys.png)

como resultado o anexo vai ter os seguintes valores preenchidos:

1. Tipo do Documento: Fatura
2. Data do Documento: 20/01/2028
3. Número: 123
4. Formato: Digitalizado nesta Unidade
5. Tipo de Conferência: Cópia Autenticada Administrativamente
6. Nível de Acesso: Restrito => Informação Pessoal (Art. 31 da Lei nº 12.527/2011)


Essa é a função basica, confira a seguir as funções avançadas para anexar, criar formulários e gerar processos inteiros em 1 click (modo de falar, mas dois ou três resolvem).



   
 
# PARAMETRIZANDO ARQUIVOS E DOCUMENTOS 

Parametrizar dados utilizando expressões regulares - REGEX; 

Aprender como trabalhar com Regex Essa crucial crucial para utilizar 100% do que a extensão pode oferecer.

Outra forma de mapear é exclusiva de arquivos PDF onde as informações venham na mesma posição, veja em [Anexar PDF](#anexar-pdf) essa forma de mapear.


 

## Conhecendo Regex e como utilizar para extrair os dados 


Se já está habituado com REGEX, basta utilizar os grupos nominados "`(?<nomeDaVariavel>...)`" e lembrar que essas variaveis abaixo são essenciais no preenchimento da tela anexo:

- numeroAnexo (preenche o número)

- nomeArvore (preenche o nome na arvore)

- data (preenche a data)

- observacoes (preenche observações da unidade)

As utilizações serão feitas no nome do arquivo ou no texto dele ou ambos, conforme vai ser 

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



 

# CRIANDO CONFIGURAÇÕES 

 

## Anexar utilizando - REGEX

### Objetivo:

- anexar usando somente o nome do arquivo para seleção automática do tipo de anexo;

- coletar dados a partir do texto do arquivo (data, numeroAnexo, nomeArvore, observacoes, outras informações que possam ser utilizadas no preenchimento de formulários, descrição do processo, e-mail etc.)

Observações: 

A coleta de dados vai ocorre em duas situações:

A primeira é quando usar diretamente o botão "Anexar arquivo(s) (também dropando o arquivo na arvore dos documentos);

Caso não tenha um arquivo de nota fiscal para seguir, utilize esse arquivo de modelo: [Modelo NF](arquivos/NF%202718.pdf)



![Anexar](gifs/anexar.gif)


A segunda é quando ele já foi inserido e é marcado a caixa de seleção, se tiver alguma configuração compatível a extensão vai ler o arquivo e extrair os dados.


![Anexar](gifs/selecionar_documento.gif)


### Passo a passo - Primeira fase

Vamos definir o que vai a extensão vai executar:

temos o arquivo que abreviamos Nota fiscal pra NF seguido do número dela ("NF 2718.pdf") e queremos que a extensão insira e selecione "Nota Fiscal" e defina "2718" como número do anexo;

Vamos começar: 

Abra Extensão

![Abrir Extensão](gifs/abrir_extensao.gif)

Entre em Configurar Anexo

![Entrar em Configurar Anexos](gifs/entrar_configurar_anexos.gif)

Crie um novo anexo

![Novo Anexo](gifs/novo_anexo.gif)

na aba "Propriedades e diretrizes de seleção do anexo" voce vai conseguir criar o regex para executar no nome do arquivo que vai identificar qual nome de anexo ele vai usar ao ser carregado no SEI;

Preencha os campos:

- nome: usar uma informação curta para você identificar a configuração para editar, nesse caso vamos usar "Nota Fiscal";

- Anotação/Descrição: informações úteis do anexo, instruções de como gerar o arquivo e assim por diante, vamos deixar essa informação para definir essa configuração: "Seleciona nota fiscal em documentos iniciados com NF";

- Agora configure o campo "Regex" e "Anexo selecionado" para que o regex selecione o anexo desejado dessa forma:

vamos montar o regex para fazer a identificação e capturar o a variavel "numeroAnexo"
"`^NF (?<numeroAnexo>\d+\-\d{4}).pdf$" => "Nota fiscal`";

    ^: Indica o início da string. O nome do arquivo deve começar com "NF".

    NF: Literalmente corresponde aos caracteres "NF".

    (espaço): Corresponde a um espaço após "NF".

    (?<numeroAnexo>\d+\-\d{4}): Este é um grupo nomeado chamado numeroAnexo.

        \d+: Corresponde a um ou mais dígitos.

        \-: Corresponde ao caractere hífen "-".

        \d{4}: Corresponde exatamente a quatro dígitos.

    .pdf: Corresponde literalmente aos caracteres ".pdf".

    $: Indica o final da string. O nome do arquivo deve terminar com ".pdf".

    Portanto, o regex completo ^NF (?<numeroAnexo>\d+\-\d{4}).pdf$ corresponde a um nome de arquivo que:

    Começa com "NF".

    Seguido por um espaço.

    Seguido por um número (um ou mais dígitos), um hífen e exatamente quatro dígitos.

    Termina com ".pdf".

    Quando um nome de arquivo corresponde a esse padrão, ele será classificado como "Nota fiscal".

Dessa forma pode-se criar quantas configurações quiser, porem tem que tomar cuidado para que a uma configuração corresponda com o padrão de outra e entrem em conflito

seguindo uma abordagem menos exigente, que copia tudo depois de NF até o primeiro ponto:

"`^NF (?<numeroAnexo>[^\.]+)`" => "Nota fiscal";

    ^: Este símbolo indica o início da string. Significa que a string deve começar com o padrão que segue.

    NF: Este é um texto literal que deve aparecer exatamente como está. Então, a string deve começar com "NF".

    (espaço): Um espaço literal. A string deve ter um espaço após "NF".

    (?<numeroAnexo>[^\.]+): Este é um grupo de captura nomeado. Vamos detalhar cada parte:

    (?<numeroAnexo>...): Define um grupo de captura nomeado chamado numeroAnexo. Isso permite que você acesse o valor capturado por este grupo pelo nome numeroAnexo.

    [^\.]+: Um conjunto de caracteres negados. [^\.] significa "qualquer caractere exceto um ponto (.)". O + indica que deve haver um ou mais desses caracteres.

    Portanto, o regex completo ^NF (?<numeroAnexo>[^\.]+) corresponde a uma string que:

    Começa com "NF"

    Seguido por um espaço

    Seguido por um ou mais caracteres que não sejam um ponto (.), que são capturados no grupo nomeado numeroAnexo.

    Exemplo de correspondência:

    Para a string "NF 12345", o grupo numeroAnexo capturaria "12345".

    Para a string "NF ABCD", o grupo numeroAnexo capturaria "ABCD".

Essa regex é usada para identificar strings que começam com "NF " e capturar o texto que segue, até encontrar um ponto (se houver).

Anexo que será ser selecionado: ser o regex corresponder será selecionado o anexo escolhido aqui, (é possível selecionar vários porem selecionará o primeiro que existir no SEI).

Diferenciar maiúsculas/minúsculas: marque caso queira que 'NF' seja diferente de "nf" no seu regex, nesse caso vamos deixar desmarcado para aceitar tando NF quanto outras variações como nf, Nf ou nF.


salve e está feito seu primeiro atalho automático, teste nomeando um arquivo "NF 12345" ou "NF 12345-2025" dependendo da sua escolha

### Passo a passo - Segunda fase

Agora que configuramos a primeira aba ("Propriedades e diretrizes de seleção do anexo") vamos criar as propriedades que faltaram, como a data da nota fiscal além de capturar informações pra utilização na criação de um formulário:


Agora abra a aba "Capturas extras - REGEX" para configurar parametrizar alguns dados;

- marque Ler texto do arquivo

- Baixe o arquivo "NF 2718.pdf" e abra ele na extensão para usar como teste;


![Capturas extras - REGEX](gifs/anexar_1_selecionar.gif)


Agora com o texto carregado vamos localizar essa informação no texto para parametrizar o "nome", o "cpf/cnpf" e a "data":

![Capturas extras - REGEX](gifs/nota_data_nome.png)

```
...
NOME / RAZÃO SOCIAL	CNPJ / CPF	DATA DA EMISSÃO
FULANO DE TAL	000.000.00-00	22/05/2024
...

``` 

agora vamos criar uma captura em branco:


![Capturas extras - REGEX](gifs/capturas_extras_regex.gif)


vamos criar um regex para capturar as 3 informações

vamos manter a primeira linha como um identificador para a segunda linha, assim o regex ficará assim:

obs. não é possível visualizar facilmente mas "NOME / RAZÃO SOCIAL",  "CNPJ / CPF" e "DATA DA EMISSÃO" estão sendo separados por uma tabulação e não por um espaço simple e o mesmo ocorre na linha 2 que estão os valores que pretendemos capturar, assim podemos substituir a tabulação pelo caracter "\t",
vamos fazer as substituições

```
NOME / RAZÃO SOCIAL\tCNPJ / CPF\tDATA DA EMISSÃO
FULANO DE TAL\t000.000.00-00\t22/05/2024
```

feito isso vamos criar as capturas:

```
NOME / RAZÃO SOCIAL\tCNPJ / CPF\tDATA DA EMISSÃO
(?<nome>[^\t]+)\t(?<cpfCnpj>[^\t]+)\t(?<data>.+)
```

obs. o texto gerado do arquivo pdf mantém separado por tabulação "\t" textos distantes que ficam na mesma linha, por isso é interessante memorizar essa lógica de regex "`(?<nome>[^\t]+)\t`" pois pode ser bem útil para parametrizar textos linhas de tabelas ou um texto que a linha anterior são os titulos e a linha seguinte são os valores.


agora vamos substituir a quebra de linha pelo seu caracter "\n"

```
NOME / RAZÃO SOCIAL\tCNPJ / CPF\tDATA DA EMISSÃO\n(?<nome>[^\t]+)\t(?<cpfCnpj>[^\t]+)\t(?<data>.+)
```

agora que terminamos o regex para capturar as informações e vamos inserir na captura em branco que criamos e preencha o nome:

![Capturas extras - REGEX](gifs/preencher_captura_branco.gif)


agora vamos repetir o processo e criar para capturar o número da nota:
texto que identifica a nota
```
Nº. 000.002.718
```

```
^Nº. [0\.]*(?<numeroAnexo>[1-9][0-9\.]*)
```

1. `^`: Indica o início da linha. Isso garante que a correspondência ocorra apenas se o padrão estiver no começo da linha. (**marque a opção multlinha para que isso funcione**).
2. `Nº. `: Corresponde literalmente ao texto "Nº. " (com um espaço após o ponto). Este é o prefixo que identifica o número da nota.
3. `[0\.]*`: Corresponde a zero ou mais ocorrências de '0' ou '.'. Isso permite que o número da nota tenha zeros à esquerda e pontos como separadores.
4. `(?<numeroAnexo>[1-9][0-9\.]*)`: Esta é uma captura nomeada chamada `numeroAnexo`.
   - `[1-9]`: Corresponde a qualquer dígito de 1 a 9. Isso garante que o número não comece com zero.
   - `[0-9\.]*`: Corresponde a zero ou mais ocorrências de qualquer dígito (0-9) ou ponto ('.'). Isso permite capturar o restante do número da nota, que pode incluir pontos como separadores.



com isso temos as propriedades nome, cpfCnpj, data e numeroAnexo capturadas do texto do arquivo, abra a aba "Valores carregados" e confira se essas propriedades carregaram com os valores corretamente.

![Capturas extras - REGEX](gifs/valores_carregados.gif)

feito isso agora é só salvar

vamos agora configurar um formulário e usar essas informações capturadas

e veja também outra forma de capturar essas informações em "Anexar PDF"



## Anexar PDF

## Formulários 


Muitos formulários que trabalhamos são como esse abaixo, eles vem quase prontos onde temos que apenas adicionar uma ou outra informação para que fique pronto.

![Abrir Formularios](gifs/formulario_inicial.png)

Nesse caso temos que adicionar o número da nota fiscal e o link na parte destacada "Nota(s) Fiscal(is) nº ___ , (link)", portanto vamos definir que essa é a primeira forma de trabalhar com formulário, onde alteramos o "Documento do sistema" conforme nossa necessidade;

A segunda forma é utilizar um "Texto padrão" para substituir o corpo principal da mensagem e deixa-lo conforme nossa necessidade, mas esse método se restringe apenas ao corpo, geralmente cabeçalhos e rodapes não são possíveis utilizar o texto padrão;

A terceira forma de traballhar com formulário é criar um modelo a partir do original e utilizar o seu número, essa forma permite personalizar tanto o cabeçalho quanto o rodapé;

Obs. ao trabalhar com a primeira forma é possível editar tanto o cabeçalho quanto o rodapé, mas desde que esteja liberado pois a maioria dos formulários só deixam disponível alterar o corpo da mensagem.

Dicas. 
 1. criando uma biblioteca de modelos com texto padrão ficará restrito apenas a sua unidade;
 2. criando uma biblioteca de modelos a partir de um processo SEI, assinando os modelos e deixando público eles ficarão disponíveis para outras unidades;
 3. criando uma biblioteca de modelos a partir de um processo SEI, deixar os modelos sem assinatura fará com que os modelos fiquem disponíveis apenas para a unidade atual, mas permitirá fazer alterações;
 4. trabalhando com o "Documento do sistema" será mais trabalhoso, mas não terá as restrições acima.

Vamos aproveitar o trabalho que fizemos para parametrizar a nota fiscal 2718 feita no menu "Anexar utilizando - REGEX" e vamos trabalhar com a primeira forma, utilizar o "Documento do sistema" e fazer as edições pontualmente;

Vou utilizar o formuário "Contratos: Recebimento do Objeto", fique a vontade para utilizar outro caso não exista e assim seguir o tutorial.
 
### Passo 1 - Abra a tela de formulários e crie um novo formulário:

 ![Abrir Formularios](gifs/abrir_formularios.gif)

No campo: "Nome da configuração" Insira um nome para a configuração do Formulário, vou utilizar o prório nome do formulário: "Contratos: Recebimento do Objeto"


### Passo 2 - Na aba "informações basicas" preencha
- Formulário: selecione um formulário ("Contratos: Recebimento do Objeto");
- Nome na arvore: preencha caso queira deixar uma informação extra no nome do formulário; normalmente deixo vazio mas vou deixar com a lista de nota selecionadas para verem o resultado "`[[LISTA_POR_EXTENSO_REDUZIDA_SEM_LINK]]`"
- Nível de acesso: selecione o nível de acesso;
- Observações: preencha caso queira incluir observações no formulário; normalmente deixo vazio mas vamos adicionar um texto para ver o resultado "`criado por: [[NOME_USUARIO]], documento: [[nomeCompleto]], [[cpfCnpj]], [[nome]]`"
- Selecione entre "Documento do sistema" ou "Número modelo" ou "Texto padrão"; nesse caso deixe marcado "Documento do sistema";

### Passo 3 - Na aba "informações da extensão" preencha:

- Descreva o que o formulário faz para quando o mouse estiver em cima: Escreva "recebimento do Objeto:\n\t selecione pelo menos uma nota fiscal para gerar o formulário"
- Selecione quais documentos selecionados que ativará esse formulário: Escolha o anexo que você quer que o formulário aparece, no meu caso vou escolher "Nota Fiscal"
- Selecione a quantidade mínima de anexos para ativar o formulário: se o seu formulário precisar de mais de um tipo de anexo coloque a quantidade aqui, ele irá bloquear a inserção do formulário se não atingir essa quantidade mínima; mas vou deixar 0;
- Adicione uma cor para o botão;
- Filtrar anexos que serão usados na sua edição; por exemplo na arvore tenho 2 anexos, um boleto e uma nota fiscal, no formulários temos disponíveis algumas listas de anexos selecionados como `[[LISTA_POR_EXTENSO_REDUZIDA]]`, se adicionarmos essa lista no texto que vamos substituir a frente "`Nota(s) Fiscal(is) nº ___ , (link)`" assim "`Nota(s) Fiscal(is) [[LISTA_POR_EXTENSO_COMPLETA]]`" vamos ter o boleto como intruso nessa lista, a lista ficará assim "`Nota(s) Fiscal(is) Nota Fiscal 2.718 (1423422) e Boleto 4654 (1423436)`", para que isso não ocorra insira apenas a "Nota Fiscal" nesse filtro;
- Atalho gerar formulário - defina se essa configuração se ativará ou não, padrão é ativar; deixe ativado
- Sempre mostrar formulário - marque se quiser que o atalho fique sempre ativo;deixe desativado pois o intuito do formulário aparecer somente quando selecionarmos a nota fiscal;

### Passo 4 - Agora entre na aba "Pesquisar, substituir, remover ou adicionar texto no modelo":

 ![Abrir Formularios](gifs/pesquisar_substituir.png)

 Utilize o botão "Adicionar substituição/acão" na coluna da esquerda para criar quantas substituições precisar, por enquando vamos realizar somente uma substituição

 1. no campo "Texto para Procurar" adicione o texto que queremos substituir `Nota(s) Fiscal(is) nº ___ , (link)`
 2. no campo "Ação" selecione "`Substituir apenas o texto encontrado`"
 3. no campo "Substituir por" adicione o texto que substuirá o valor inicial, vamos usar uma das listas de objetos selecionados para trazer o nome do anexo e o link, nesse caso vamos usar "`[[LISTA_POR_EXTENSO_COMPLETA]]`", assim o texto "`Nota(s) Fiscal(is) [[LISTA_POR_EXTENSO_COMPLETA]]`"
 4. tem opção de alterar o esli do paragrafo, nesse caso vamos selecinar o que da espaçamento na primeira linha "Texto_Justificado_Recuo_Primeira_Linha";


Agora salve a configuração 

 ![Abrir Formularios](gifs/novo_salvar.png)

"Contratos: Recebimento do Objeto"

















## Processos 

 

## Processos relacionados 

 

## Descrição do processo 

 

## E-mail 

 

# OUTRAS FUNÇÕES 

 

# Disponibilizando acesso externo em lote a um documento/processo 

 

# Verificando ciência de servidores a um determinado processo 

 

# Utilizando a barra de pesquisa e filtros 

 

# Ativando alerta de blocos de assinatura disponibilizados para o setor 

 

# Utilizando a caixa de se seleção para copiar dados 

 

# Ativando funções da extensão 

 

 

 