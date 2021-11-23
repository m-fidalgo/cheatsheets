<h1 align="center">Funções</h1>

<h3>Funções em Comum</h3>
<li><b>CONCAT(str1, ..., str2)</b>: unir strings</li>
<li><b>LOWER(str)</b> e <b>UPPER(str)</b></li>
<li><b>REPLACE(strOriginal, strTrocar, strNova)</b></li>
<li><b>SUBSTRING(strOriginal, pos, tamanho)</b>: pega a substring de tamanho a partir de pos</li>
<li><b>COALESCE(valores)</b>: retorna o primeiro não nulo</li>

<h3>Funções de Agregação</h3>
<li><b>MIN(col)</b> e <b>MAX(col)</b></li>
<li><b>SUM(col)</b>: soma todos os valores</li>
<li><b>COUNT(col)</b>: conta as ocorrências</li>
<li><b>AVG(col)</b>: faz a média aritmética dos valores</li>

<h3>MySQL</h3>
<li><b>SOUNDEX(string)</b>: comparação fonética</li>
<li><b>CURDATE()</b>: data atual</li>
<li><b>NOW()</b>: data e hora atual</li>
<li><b>TIMESTAMPDIFF(unidadeTempo, dataInicial, dataFinal)</b>: </li>

<h3>SQLServer</h3>
<li><b>GETDATE()</b>: data e hora atuais</li>
<li><b>SYSDATETIME()</b>: hora no formato datetime2 do sistema</li>
<li><b>CURRENT_TIMESTAMP()</b>: timestamp do sistema</li>
<li><b>DATEDIFF(unidadeTempo, dataInicial, dataFinal)</b></li>
<li><b>CAST(col AS tipo)</b> ou <b>CONVERT(col AS tipo)</b></li>
<li><b>ISNULL(col, retorno)</b>: se for null, dá o retorno</li>
<li><b>YEAR, MONTH, DAY(col)</b>: pega essa unidade de tempo da data</li>
<li><b>DATEFROMPARTS(dia, mes, ano)</b>: retorna no formato de data</li>
<li><b>DATEPART(unidade, campo)</b>: retorna a unidade de tempo da data passada</li>
<li><b>ABS(valor)</b>: valor positivo absoluto</li>
<li><b>LOG10(valor)</b></li>
<li><b>PI()</b></li>
<li><b>RAND()</b>: número aleatório entre 0 e 1</li>

<h3>PostgreSQL</h3>
<li><b>NOW()</b> ou <b>CURRENT_TIMESTAMP</b>: data e hora atual</li>

<h3>Oracle</h3>
<li><b>LENGTH(string)</b></li>
<li><b>TRIM(string)</b>: remove espaços em branco nas bordas</li>
<li><b>POSITION(sequencia IN sequenciaBusca)</b>: retorna a posição inicial de uma sequência de caracteres em outra</li>
<li><b>TO_DATE(data, formato)</b>: formata a data nesse formato para o padrão oracle</li>
<li><b>TO_CHAR(dataOracle, formato)</b>: formata a data no padrão oracle para esse formato</li>
<li><b>CURRENT_DATE</b> e <b>CURRENT_TIMESTAMP</b>: data/data e hora atual</li>
<li><b>SYSDATE</b>: data e hora do sistema</li>
<li><b>MONTHS_BETWEEN(dataInicial, dataFinal)</b></li>
