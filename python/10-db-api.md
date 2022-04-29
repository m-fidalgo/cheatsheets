<h1 align="center">Db API</h1>

<h3>Sobre</h3>
<p>Interface que padroniza o uso de bibliotecas de banco de dados</p>
<p>Alterar a versão da API: <b>MySQLdb.apilevel = '1.0'</b></p>

<h3>Criar Conexão</h3>

```
import MySQLdb

db = MySQLdb.connect(user='root', passwd='senha', db='nomeBanco', host='localhost', port=3306)
db.close()
```
<h3>Cursores</h3>
<p>Um cursor por banco</p>

```
cursor = db.cursor()
```
<p>Select</p>
<ul>
  <li><b>.execute(select)</b> exemplo .execute('SELECT campos FROM tabela WHERE condição')</li>
  <li><b>.fetchall()</b> percorre e retorna todos os resultados do último select feito pelo cursor (retorna uma tupla de tuplas)</li>
  <li><b>.fetchone()</b> retorna o primeiro registro da última consulta (tupla)</li>
  <li><b>.fetchmany(n)</b> retorna os n primeiros registros</li>
</ul>
<p>Insert: <b>.execute(insert)</b> exemplo .execute('INSERT into tabela(campos) VALUES(values)'</p>
<p>Recuperar id do último registro: <b>id = cursor.lastrowid()</b></p>
<p>Update: <b>.execute(update)</b></p>
<p>Delete: <b>.execute(delete)</b></p>

<h3>Alterações</h3>
<p>Devem ser commitadas</p>
<p>Pode-se passar <b>autocommit=True</b> no connect</p>

<h3>Transações</h3>

```
try:
  db.begin()
  # operações
  db.commit()
except:
  db.rollback()
```
<h3>Consultas parametrizadas</h3>
<p>Configuração global paramstyle: determina o tipo de parâmetros que são aceitos nas consultas -> <b>MySQLdb.paramstyle = formato</b>, sendo formato = 'format' (formato ASIC) ou 'pyformat'</p>
<ul>
  <li><b>.execute('query campo =%s', (valor, ))</b></li>
  <li><b>.execute('query campo =%(chave)s', ({chave: valor}))</b></li>
</ul>
<p>Parâmetros múltiplos: <b>.executemany('query campo =%s campo =%s', ('a1', 'b1'), ('a2', 'b2'))</b></p>
