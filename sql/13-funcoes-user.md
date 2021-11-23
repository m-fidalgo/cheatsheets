<h1 align="center">Funções do Usuário</h1>

<h3>MySQL</h3>

```
DELIMITER : DELIMITER $$
CREATE FUNCTION nome([parametros]) RETURNS tipo instruções
$$ DELIMITER

DROP FUNCTION nome;
```
<p>Função: uso de delimiter para ser possível usar ; dentro da função</p>
<p>Parâmetros: param tipo</p>
<p>Variáveis</p>

```
DECLARE nome tipo;
SET nome = valor;
SELECT ? INTO nome FROM tabela ... ;
```
<h3>SQLServer</h3>

```
CREATE FUNCTION nome
(@param tipo) RETURNS tipo
AS BEGIN
  instruções
  RETURN
END;

SCHEMA.nome();
DROP FUNCTION nome;
```
<p>Pode retornar tabelas: RETURNS TABLE AS RETURN tabela</p>
<p>Variáveis</p>

```
DECLARE @nome tipo;
SET @nome = valor;
```
<h3>PostgreSQL</h3>

```
CREATE [OR REPLACE] FUNCTION
[schema.]nome (param tipo classificaçãoParam)
RETURNS tipoRetornno AS
$$
DECLARE variáveis
BEGIN instruções END
$$
LANGUAGE linguagem
classificaçãoFunção;
```
<p>Classificação do Parâmetro: IN, OUT, INOUT, VARIADIC</p>
<p>Classificação da Função: VOLATILE (pode modificar valores do BD, não necessariamente retorna o mesmo valor com os mesmos parâmetros), STABLE (não modifica valores, dá o mesmo valor para os mesmos parâmetros, otimizada), IMMUTABLE (como STABLE, não otimizada)</p>
<p>Linguagem: SQL, C, PLPGSQL</p>

<h3>Oracle</h3>

```
CREATE FUNCTION nome (param tipo) RETURN tipoRet IS var tipoVar
BEGIN instruções END;

nomePacote.nomeFunção(param);
```
