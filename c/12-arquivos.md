<h1 align="center">Arquivos</h1>

<h3>Declaração</h3>

```
FILE *file;
```
<h3>Abrindo Arquivo</h3>

```
file = fopen(caminho, modo);
```
<p>Modos</p>
<li><b>r</b>: abre arquivo já existente para leitura</li>
<li><b>w</b>: cria arquivo vazio para escrita (se já existir, apaga e cria outro)</li>
<li><b>a</b>: cria/abre arquivo, adicionando conteúdo</li>
<li>Sufixo <b>+</b>: permite leitura e escrita</li>
<li>Sufixos <b>t</b> e <b>b</b>: modo texto(padrão) e binário</li>

<h3>Fechando Arquivos</h3>

```
fclose(file);
```
<h3>Leitura e Escrita</h3>
<li>Básica: lê/escreve n conjuntos de nBytes, sendo var a variável que recebe a leitura/fornece o conteúdo a ser escrito</li>

```
fread(&var, nBytes, n, file);
fwrite(&var, nBytes, n, file);
```
<li>Caracteres: retorna o caracter lido/escreve o caracter ch</li>

```
ch = fgetc(file);
fputc(ch, file);
```
<li>Formatadas: semelhante a scanf/printf</li>

```
fscanf(file, formatação, variáveis);
fprintf(file, formatação, variáveis);
```
<li>Strings: o n considera o caracter de fim de string</li>

```
fgets(string, n, file);
fputs(string, file);
```
<h3>Fim de Arquivo</h3>
<p>Caracter de fim de arquivo: EOF</p>
<p>Função feof: retorna verdadeiro se o EOF já foi lido</p>

```
feof(file);
```
<h3>Seeking</h3>
<p>Ação de mover o ponteiro do arquivo por suas posições</p>
<p>O fseek move o ponteiro n posições a partir da constante</p>
<p>Constantes: <b>SEEK_SET</b> (0, início do arquivo), <b>SEEK_CUR</b> (1, posição atual), <b>SEEK_END</b> (2, fim do arquivo)</p>
<p>O rewind volta ao começo do arquivo</p>

```
fseek(file, n, CTE);
rewind(file);
```
<h3>Outras Funções</h3>

```
fflush(file);
remove(file);
ftell(file);
```
<li><b>fflush</b>: descarrega o buffer, assegurando que os dados sejam gravados</li>
<li><b>remove</b>: apaga o arquivo</li>
<li><b>ftell</b>: retorna um long que indica o número de bytes do começo do arquivo até a posição atual</li>
