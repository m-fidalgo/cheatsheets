<h1 align="center">Stored Procedures</h1>

<h3>Sobre</h3>
<p>Procedimentos pré-compilados armazenados no servidor chamados de forma explícit para executar alguma lógica de manipulação de dados</h3>

<h3>Cursores</h3>
<p>Percorrer linhas de forma a analisar cada registro separadamente, sempre vinculados a uma consulta: navega nos registros retornados</p>
<p>Declarados após as variáveis</p>

<h3>MySQL</h3>
<p>Procedures</p>
  
```
CREATE PROCEDURE nomeProc ([params]) [características] [BEGIN] corpo; [END]
CALL nomeProc();
```
<li>Parâmetros: IN, OUT ou INOUT. Pode-se criar automaticamente parâmetros out com @nome</li>
<p>Cursores</p>

```
DECLARE nomeCursor CURSOR FOR select
OPEN nomeCursor

//associar uma variável a cada coluna da linha atual do cursor
FETCH [[NEXT] FROM] nomeCursor INTO @var1, @var2...

//uso de handler: lidar com erros - ver se não tem mais linhas
DECLARE CONTINUE HANDLER FOR NOT FOUND SET var = valor;

CLOSE nomeCursor
```
<h3>SQLServer</h3>
<p>Procedures</p>

```
CREATE PROCEDURE nomeProc
[@param tipo [=valor]] [OUTPUT]
AS comandos

EXECUTE schema.nomeProc  p1, p2;
```
<p>Cursores</p>

```
DECLARE nomeCursor CURSOR [LOCAL | GLOBAL] [FORWARD_ONLY | SCROLL]
tipo [READ_ONLY | SCROLL_LOCKS | OPTIMISTIC] [TYPE_WARNING] FOR select

OPEN nomeCursor
FETCH NEXT | FIRST | LAST | PRIOR cursor INTO @var...
UPDATE cursor SET col=valor WHERE CURRENT OF cursor
CLOSE nomeCursor
DEALLOCATE nomeCursor
```
<li>Static - dados no tempdb, não podem ser alterados. Forward-only (a linha só pode ser acessada uma vez) ou scrollable (navegação para qualquer direção)</li>
<li>Keyset: só as colunas necessárias para identificar a tupla no tempdb. Dados updatable ou read-only, forward-only ou scrollable</li>
<li>Dynamic: a consulta é feita toda vez que é invocado - não são armazenados. As alterações são refletidas no cursor e na tabela</li>
<li>Fast-forward: dados no tempdb, é forward-only e read-only. Se a consulta retorna text, ntext ou image (ou tem top), é convertido em keyset. Se a tabela tem triggers, é convertido em static</li>

<h3>Oracle</h3>
<p>Procedure</p>

```
//header do pkg
PROCEDURE nome

//body do pkg
PROCEDURE nome IS BEGIN instruções END;

//procedure
CREATE [OR REPLACE] PROCEDURE [schema.]nome (param tipo)
IS | AS
  cte CONSTANT tipo:= valor;
  var tipo;
  var tipo NOT NULL := valor;
BEGIN instruções END nome;
```
<p>Cursores</p>

```
DECLARE nomeCursor FOR select;
OPEN nomeCursor;
FETCH [[NEXT] FROM] nome INTO vars;
CLOSE nomeCursor;
```
<li>Critério de saída de loops: nome%NOTFOUND</li>
  
  
  
  
  
