<h1 align="center">Views</h1>

<h3>Sobre</h3>
<p>Views (virtual tables) são objetos baseados em declarações select, pertencendo ao banco e retornando esse resultado</p>
<p>Podem ser atualizadas se não tiverem funções agregadas, join ou DISTINCT</p>
<p>Views normais executam o select quando invocadas, views materializadas armazenam esse resultado</p>

```
SELECT * FROM nomeView;
DROP VIEW nomeView;
```

<h3>MySQL</h3>

```
CREATE [OR REPLACE] [ALGORITHM = algType] VIEW nomeView [(colunas)] AS selectStatement [WITH [CASCADED | LOCAL] CHECK OPTION];
```
<p>O algType define qual algoritmo interno deve ser usado para processar a view quando ela for invocada. Pode ser UNDEFINED (cláusula em branco), MERGE ou TEMPTABLE</p>
<p>As colunas permitem sobrescrever o nome das colunas do select</p>
<p>WITH CHECK OPTION: todas as declarações que tentarem modificar dados de uma view serão revisadas para checar se respeitam o WHERE do select</p>
<p>Com a criação de uma view surge um arquivo .frm no diretório do banco</p>

<h3>SQLServer</h3>

```
CREATE VIEW nomeView AS selectStatement;
```
<h3>PostgreSQL</h3>

```
CREATE [OR REPLACE] [TEMP | TEMPORARY] VIEW nomeView (colunas) AS selectStatement;
```
<h3>Oracle</h3>
<p>Views normais</p>

```
CREATE VIEW nomeView AS selectStatement;
```
<p>Views materializadas</p>

```
CREATE MATERIALIZED VIEW nomeView AS selectStatement
BUILD IMMEDIATE | DEFERRED
REFRESH FAST | COMPLETE | FORCE
ON COMMIT | DEMAND
ENABLE | DISABLE QUERY REWRITE;
```
<p>Build: dados persistidos imediatamente ou ao chamar manualmente</p>
<p>Refresh: update rápido da view (modifica apenas as linhas modificadas), completo (refaz o arquivo) ou forçado (tenta o fast, se não conseguir, faz o completo)</p>
<p>Query Rewrite: se ativado, faz com que outros select usem a view ao identificar que eles tentam pegar os mesmos valores</p>
