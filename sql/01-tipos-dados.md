<h1 align="center">Tipos de Dados</h1>

<h3>MySQL</h3>
<li>Bit/Bool</li>
<li>TinyInt, SmallInt, MediumInt, Integer/Int, BigInt</li>
<li>Float, Real, Double</li>
<li>Decimal(M,D) ou Dec(M,D): precisão M e escala D</li>
<li>Date, DateTime, TimeStamp, Time (HH:MM:SS), Year</li>
<li>Char(n), Varchar(n): n ou n+1 bytes</li>
<li>TinyText ou TinyBlob, Text ou Blob, LongText ou LongBlob</li>
<li>Enum(val1, ..., valN), Set(val1, ..., valN): o set permite escolher nenhum ou vários</li>
<li>Serial: BigInt com as restrições NOT NULL, AUTO_INCREMENT, UNSIGNED, UNIQUE</li>

<h3>SQLServer</h3>
<li>SmallInt, Int, BigInt</li>
<li>Float(n), Real</li>
<li>Numeric(precisão, escala) e Decimal(precisão, escala)</li>
<li>Date (DD/MM/AAAA), Time(n): n é a precisão em segundos (hh:mm:ss[.nnnn]), DateTime2(n): date + time, DateTimeOffset(n): DateTime2 com fuso horário ([+|-] hh:mm)</li>
<li>Char(n) e nchar(n), Varchar(n) e nvarchar(n)</li>
<li>Money</li><li>Binary(n), Varbinary(n): fixo e variável</li>
<li>Image</li>

<h3>PostgreSQL</h3>
<li>SmallInt, Integer, BigInt</li>
<li>Numeric(precisão, escala) e Decimal(precisão, escala)</li>
<li>Real, DoublePrecision</li>
<li>Interval</li>
<li>Date</li>
<li>Time[(p)] [with|without timezone]</li>
<li>TimeStamp[(p)] [with|without timezone]: data e hora</li>
<li>Character Varying(n), Varchar(n), Character(n), Char(n): comprimento com limite, variável e fixo</li>
<li>Text: comprimento variável sem limite</li>
<li>Money</li>
<li>Serial: inteiro com auto-incremento, BigSerial</li>
<li>Boolean</li>
<li>Bytea</li>
<li>Enum: CREATE TYPE [schema.]nome AS ENUM (valores); o tipo da coluna será [schema.]nome</li>

<h3>Oracle</h3>
<li>Number(precisão, escala)</li>
<li>Binary_float e Binary_double</li>
<li>Date: data e data+hora, sem suporte para frações de segundo</li>
<li>Timestamp: aceita frações de segundo, [with timezone] armazena fuso horário</li>
<li>Char(n) e Varchar(n), nchar(n) e nvarchar(n)</li>
<li>Clob e nclob: binário para sequências grandes de caracteres</li>
<li>Blob: objeto binário</li>
<li>BFile: localizador, binários num local externo</li>
