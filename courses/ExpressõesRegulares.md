# Curso Expressões Regulares
## Alura

Uma expressão regular, ou Regex, são padrões utilizados para identificar determinadas combinações ou cadeias de caracteres em uma string. Ela faz parte do dia a dia de todos os programadores e administradores de infra. Por meio dela, podemos validar a entrada de usuários ou encontrar alguma informação em logs, documentação ou saída de comando. O mais legal é que as regex são escritas independentes de uma linguagem, como JavaScript ou C#. As expressões são definidas em sua própria linguagem formal e uma vez aprendida, podemos aplicar o conhecimento dentro da linguagem de nossa preferência.
Regex, ou expressões regulares, é uma linguagem para encontrar padrões de texto.
Sendo uma linguagem independente, existem interpretadores para a maioria das plataformas de desenvolvimento, como JavaScript, C#, Python ou Ruby.
Uma classe de caracteres predefinida é \d, que significa qualquer dígito.
Existem vários meta-char, como . ou *.
-----------------------------------------------------------------------------------------------------
Funções da RegEx:
A) Extraindo seções específicas de uma arquivo de texto
B) Validação de formatação de, por exemplo, e-mail ou telefone
C) Análise de arquivos de texto e extração de dados para, por exemplo, gravar no banco de dados
D) Substituindo os valores de um texto para limpar, reformatar ou alterar o conteúdo
http://aurelio.net/regex/guia/metacaracteres.html
EXEMPLO:
O nosso alvo é: 15.123.321/8883-22
Vamos analisar o nosso CNPJ por partes.
A primeira parte possui dois números e o "ponto", portanto: \d{2}\.
A segunda e terceira parte possuem três números, separado por "ponto", portanto: \d{3}\.\d{3}
Após disso, há uma barra que deve ser escapada: \/
Após à barra, vem quatro números e os dois dígitos verificadores: \d{4}\-\d{2}
Uma resposta correta é: \d{2}\.\d{3}\.\d{3}\/\d{4}\-\d{2}
-----------------------------------------------------------------------------------------------------
EXEMPLO: NUMERO IP:
\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}
-----------------------------------------------------------------------------------------------------
EX:
\d{3}[.-]?\d{3}[.-]?\d{3}[.-]?\d{2}
[ ] representa uma classe de caracteres, um conjunto de caracteres que pode aparecer
? significa que pode ou nao aparecer, é o mesmo que dizer [0,1] é um quantifier
-----------------------------------------------------------------------------------------------------
QUANTIFIERS -
? - zero ou uma vez
* - zero ou mais vezes
+ - uma ou mais vezes (positivo)
{n} - exatamente n vezes
{n, } - no minimo n vezes
{n,m} - no minimo n+1 vezese no maximo m vezes
Por fim, não podemos esquecer de mencionar a classe de word char. Um word char é apresentado com \w e é um atalho para [A-Za-z0-9_].
-----------------------------------------------------------------------------------------------------
EXEMPLO:
[0123]?\d\s+de\s+[A-Z][a-zç]{1,8}\s+de\s+[12]\d{3}
( dá match em : 21 de Maio de 1993 )
o \s selecione um white space e o mais após significa mais de um espaço em branco.
[a-z] seleciona o alfabeto, mas não inclui os caracteres ç por exemplo
3:35
-----------------------------------------------------------------------------------------------------
ANCORAS:
Existem âncoras predefinidas que selecionam uma posição dentro do alvo.
\b é uma âncora que seleciona um word boundary, isso é o início ou fim da palavra.
^ é uma âncora que seleciona o início da string alvo.
$ é uma âncora que seleciona o fim do alvo.
inpt: aaa aaaaa aaa aaaa
\baaa\b irá retornar APENAS OS "aaa" sem nada dos lados
-----------------------------------------------------------------------------------------------------
EXEMPLO:
^\d{3}\.\d{3}\.\d{3}-\d{2}$
String compatvel: 111.111.111-11
Como foi visto no capítulo, o circunflexo (^) é uma âncora e garante que na string nada deve vir antes, por isso a string CPF: 111.111.111-11 não é compatível, pois antes do número do CPF há o trecho CPF:. Já o $ é o contrário, nada na string deve vir depois, por isso a string 111.111.111-11 é o número do meu CPF também não é compatível, pois depois do número do CPF há o trecho é o número do meu CPF
\Bpor\B --> SELECIONA TODAS AS SILABAS "por" q estao dentro de uma palavra
\Bpor\b --> SELECIONA TODAS AS PALAVRAS EXATAMENTE "por"
3:35
-----------------------------------------------------------------------------------------------------
([0123]?\d)\s+(?:de\s+)?([A-Z][a-zç]{1,8})\s+(?:de\s+)?([12]\d{3})
- () serve para agrupar determinadas pates da regEx, com isso, vc pode por exemplo tornar determinado grupo opcional
- cria grupos para a expressao regular, o ?: ira fazer com que o grupo nao seja capturado pelo interpretador
----------------------------------------------------------------------------------------------------
EXEMPLO:
ReGex pra capturar APENAS os NOMES antes do @ dos emails que terminar com caelum.com.br OU alura.com.br.
([a-z.]{4,14}[a-z\d])@(?:caelum.com.br|alura.com.br)
super.mario@caelum.com.br extrai super.mario
----------------------------------------------------------------------------------------------------
GRUPOS
Declaramos um grupo com ().
Podemos ter grupos e subgrupos.
Um grupo é retornado na hora de executar, são úteis para selecionar uma parte do match.
Através do ?:, dizemos que não queremos ver esse grupo na resposta
3:35
----------------------------------------------------------------------------------------------------
EXEMPLO:
<h2 id="regex" class="form">Expressões regulares não são tão difíceis.</h2>
<(h1|h2).+?>([\w\sõãí.]+)<\/\1> nesse fim, estamos referenciando o NUMERO DO grupo.
irá voltar:
<h2 id="regex" class="form">Expressões regulares não são tão difíceis.</h2> ||| h2 ||| Expressões regulares não são tão difíceis.
----------------------------------------------------------------------------------------------------
NEGAÇÕES:
O \W é a non-word char, ou seja tudo que não é um word char. \W é um atalho para [^\w].
A classe \D, por sua vez, é um non-digit, ou seja, \D é um atalho para [^\d]
EX:
Z171PZ7AZ23PZ7819AZ78GZ1AZ99IZ34O
[^Z\d]
Resultado: P || A || P || A || G || A || I || O
Aprendemos que quantifiers são gananciosos por padrão e que podemos utilizar um ? logo após o quantifier, deixando-o preguiçoso. Também aprendemos como podemos referenciar o texto de um grupo dentro da regex, aonde n é o número do grupo.
3:36
----------------------------------------------------------------------------------------------------
RegEx no Javascript:
No mundo JavaScript, temos duas formas de construir uma expressão regular. A primeira é usada através da classe RegExp, como já vimos no nosso script:
ex:
<html>
<script>
var alvo = '11a22b33c';
var exp = /(\d\d)(\w)/g;
var resultado = exp.exec(alvo);
console.log(resultado);
console.log(exp.lastIndex);
</script>
</html>
