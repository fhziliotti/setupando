# Curso Performance Web 1
## Alura

1) Utilizar GULP (task para minificar todos os js, css, html) com o uglify para minificar o CSS, JS e HTML do site.
Criar uma cópia da pasta original do sistema chamada DIST.
Tem como minificar no server side com o PHP, basta procurar no google.

2) Servidor e GZIP, tem como habilitar o GZIP no servidor para enviar os arquivos compactados. Basta alterar os comandos de um arquivo de configurações do servidor, procurar no google.
Conversar com a galera que cuida do Servidor, geralmente o pessoal da Infraestrutura para habilitar o Gzip.

3) Usar SVGS ao invés de JPEG, por ser mais rápido

4) PARA VERIFICAR AS MUDANÇAS NO TAMANHO DOS ARQUIVOS , BASTA IR no --INSPECIONAR NA PARTE DO NETWORK

5) IMAGENS REPRESENTAM 2/3 do tamanho de nossas paginas web.
OTIMIZAR IMAGENS, FERRAMENTA ONLINE KRAKEN.IO - otimiza a imagem usando o Loosly e o LossLess (sem perda). Esse segundo ira retirar os metadados da imagem(informações inbutidas e que sao desnecessárias na hora de mostrar, a imagem terá a MESMA qualidade) tem o TINYPNG.com.
OTIMIZAR SVG - SVGOMG - https://jakearchibald.github.io/svgomg/
O arquivo da imagem precisa ser lido na memória, gastando RAM. Um problema se o usuário tiver pouca RAM, como no mobile.
O browser precisa redimensionar a imagem na hora de exibi-la e isso pode ser custoso, sobretudo em cenários com dispositivos de baixo poder de processamento, como celulares.
TEM COMO AUTOMATIZAR COM O GULP TAMBEM, INSTALANDO FERRAMENTAS DE OTIMIZACAO E CRIANDO A TASK NO GULP
O melhor formato para fotos hoje na Web. Foi pensado pra isso. Há outros menos usados como WEBP e JPEG2000 que seriam bons também.

6) Como vimos na aula, o Chrome DevTools nos permite analisar muitas coisas da performance do site. Faça isso agora, abrindo a aba Network e navegando para o site otimizado. Algumas coisas para observar, como vimos na aula:
a) O waterfall dos requests. Mostrando a sequência se requisições, o tempo de espera de cada um, o tempo de resposta do servidor, o tempo de download de cada recurso.
b) O número de conexões simultâneas, que limita a quantidade de requests em paralelo. (no Chrome são 6)
c) O número total de requests embaixo e o tamanho final da página.

7) REMOVER DEPENDENCIAS DO PROJETO: exemplo, se eu uso JQUERY apenas como facilitador (seletor jquery), será mesmo que vale a pena gastar a requisição que geralmente atrapalha o carregamento da pagina?

8) Deploy no Google App Engine - é um servidor gratuito do google que serve para você subir seu site, ele ja faz varias otimizações padrões e tem suporte ao HTTP2

9) Software que analisa a performance do site
a- PageSpeed Insights
b- WebPageTest - mais completo, mostra graficos que facilitam o entendimento

10) 
server {
listen 2020;
root /Users/alura/performance-web/site/;
}
server {
listen 3030;
root /Users/alura/performance-web/dist/;
gzip on;
gzip_types text/css application/javascript image/svg+xml;
}

11) Concatenação do CSS (se você divide seus css em componentes, você exigira muitos requests e isso nao é legal, o bom sera apenas um request com todos os components em um arquivo só)
Diminuir o número de requests faz com que as coisas baixem mais rapidamente no HTTP 1. Temos menos concorrência nas parcas 6 conexões disponíveis, logo recursos tem que esperar menos para serem baixados. De bônus, o GZIP funciona muito bem em recursos texto concatenados com bastante repetição, como CSS.
USAR O Gulp com useref. -ferramenta de build:
```css
<!-- build:css assets/css/estilos.css -->
<link rel="stylesheet" href="assets/css/reset.css">
....
<!-- endbuild -->
```
Coloca isso no arquivo html, e ao rodar o comando no gulp ele salva todos os css entre a tag build e 'COSPE' na pasta que você quer, alem disso modifica a parte do LINK do html para apenas um arquivo.
OBS: PRA FAZER ISSO, VOCE DEVE TER EM MENTE QUE PODE ATRAPALHAR O ESQUEMA DE CACHEAR OS ARQUIVOS, se você mudar apenas uma linha de codigo, o browser do usuario vai baixar todo o arquivo novamente, antes ele iria baixar apenas o arquivo que foi modificado.

12) SPRITES - é uma tecnica para diminuir a quantidade de requests do seu site
você ira concatenar as imagens em uma única imagem, e na hora de apresentálas, você modifica o background-position via CSS.
O google usa isso e é bem eficaz.
Você deve usar o ImageMagic (software que facilita a concatenação/edição via linha de comando), ou senao usar o photoshop/coreldraw
Sprites em png é alterando o background position
Sprites em SVG você concatena os SVGS em um unico arquivo, dando um ID para cada Symbol dentro da tag SVG, no arquivo HTML, ao inves de usar a tag img, você usa a tag SVG e passa o arquivo concatenado com parametro e no fim , basta passar #id-do-symbol.
TEM COMO AUTOMATIZAR usando o svg-sprite , ou fazendo na ferramenta do designer mesmo, criando os simbolos no editor visual.
obs: ténica de usar <symbol> é muito útil mas não funciona em todos os navegadores. Em especial, IEs mais antigos. Mas, para isso, podemos usar um polyfill.
Uma bem famosa é a svg4everybody. Basta adicionar um script simples na página e chamar svg4everybody(). Deixei isso pronto no projeto já em assets/js/svg4everybody.js.

13) Comandos que automatizam tudo que foi aprendido no curso
```bash
gulp imagemin
gulp minify
gulp useref
```
14) INLINE DE RECURSOS (as vezes , quando queremos que algo seja priorizado na hora de carregar a pagina, escrevemos o arquivo inline, ao invés de criar um request separado da index)
Podemos fazer isso com Javascripts com poucas linhas, com SVGS como logo do site. Para isso, podemos dar ctrl C ctrl V no arquivos mesmo, ou podemos usar um plugin do GULP, e colocar a tag "inline" no codigo HTML, quando rodamos o codigo do gulp, quando o programa encontra esse tag inline, ela copia o codigo do arquivo que seria baixado e coloca no html.

15) TAMANHO IDEAL DO ARQUIVO HTML é
14KB gzipados, incluindo os headers da resposta. É o tamanho aproximado de 10 segmentos TCP, o padrão da janela inicial de novas conexões em servidores modernos.

16) Requests paralelos, por padrão o HTTP1 disponibiliza apenas 6 conexões simultaneas
Você deve ter ouro dominio e fazer com que seu site importe os arquivos deste outro dominio.
Desse modo, os requests do seu site nao briga com apenas as 6 conexões padrões
Além de carregar mais rápido, pode até gerar uma economia de bytes ao evitar o envio de cookies do domínio principal.
Segundo subdomínio
Se você tiver um domínio próprio, pode usá-lo para espelhar os arquivos do nosso site.
Se estiver usando o Google App Engine como sugeri antes no curso, é muito fácil ter novos subdomínios. Inclusive, quando fazemos deploy da versão padrão da nossa app, já é possível acessá-la em dois hostnames diferentes:
obs: Estudos já mostraram que 2 ou 3 hostnames diferentes é o número ideal. Muitos hostnames paralelos podem causar congestionamento na rede e atrasar o browser. Mas sempre vale testar caso a caso. Às vezes nem compensa ter nenhum hostname a mais.

17) Cache com Expires, serve para você falar para os headers do browser os arquivos do projeto que você quer que seja cacheado(Web cache é um armazenamento temporário no disco rígido de páginas web, imagens e outros documentos e ficheiros utilizando técnicas de cache para reduzir o uso largura de banda disponível, aumentar a velocidade do acesso, entre outras vantagens.)
Você deve analisar o que não muda ou qual a constancia de alterações dos arquivos do seu site e informar para o navegador, desse modo, os usuarios que visitam seu site mais de 1 vez, sentirão um carregamento muito mais rápido da pagina, pois os seus browsers armazenam boa parte do projeto no proprio browser.
OBS: colocar cache com tempo alto pode ferrar seu site:
Um cuidado antes de habilitarmos o cache alto no servidor é de garantir que as URLs são únicas e mudarão quando fizermos alterações no site. Fazemos isso adicionando algum tipo de controle de versão no nome do arquivo (um número, ou um timestamp, ou um hash do conteúdo).
Esse processo pode ser manual mas temos o plugin do gulp que já faz isso automaticamente, colocando um hash gerado a partir do conteúdo de cada arquivo.
Nosso gulpfile já foi configurado para isso. Basta rodar: gulp revreplace que todas as tasks anteriores serão rodadas além das novas que fazem as revisões dos arquivos.
Observe o conteúdo gerado e veja como CSS, JS e imagens foram renomeadas.
Importante: renomear os arquivos é um processo destrutivo. Isso quer dizer que não dá pra rodar o revreplace duas vezes. Se precisar rodá-lo novamente, apague o dist, e rode o copy, minify, useref e aí o revreplace de novo.
exemplo no google app Engine:
```
application: seu_id_aqui
runtime: php55
api_version: 1
version: web
handlers:
- url: /
static_files: index.html
upload: index.html
- url: /assets
static_dir: assets
expiration: 365d
Exemplo do NGINX:
server {
listen 3030;
root /Users/alura/performance-web/dist;
gzip on;
gzip_types text/css application/javascript image/svg+xml;
location /assets {
expires 1y;
add_header Cache-Control public;
}
}```

## FINALIZANDO:
A PERFORMANCE ESTA DIRETAMENTE RELACIONADA COM O UX, POIS VOCE TEM QUE DEIXAR A PAGINA INICIAL DO PROJETO CARREGAR RAPIDAMENTE E PASSA A SENSAÇÃO DO USUARIO.
CASO 1: MUDANDO A COR DE FUNDO DE AZUL PARA BRANCO, DA A SENSAÇÃO DE CARREGAMENTO MAIS RAPIDO PRO USUARIO, MESMO QUE O TEMPO DE CARREGAMENTO SEJA O MESMO POR EXEMPLO
