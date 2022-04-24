<h1 align="center">Básico</h1>

<h3>Tipos de Dados</h3>
<p>int, str, bool, list, dict, file</p>

<h3>Variáveis</h3>
<p>Surgem na atribuição de valor</p>
<p>Atribuição: <b>nome = valor</b></p>
<p>Atribuição Múltipla: <b>nome1, nome2 = valor1, valor2</b></p>
<p>Ver o tipo: <b>type(var)</b></p>

<h3>Virtual Environment</h3>
<p>Criar</p>

```
python -m venv .venv
```
<p>Ativar</p>

```
.\.venv\Scripts\activate
```
<p>Desativar: <b>deactivate</b></p>

<h3>Entrada de Dados</h3>
<p>Enter como quebra, salva como string</p>

```
var = input("Mensagem: ")
var1, var2 = input().split()
varInt = int(input())
```
<h3>Saída de dados</h3>

```
print(var1, ..., varn)
print("msg", var, "msg")
print(f"msg {var} msg")
```
<h3>Operadores Aritméticos</h3>
<p>+, -, *, /, ** (exponenciação), // (parte inteira da divisão), % (módulo)</p>

<h3>Estruturas Condicionais</h3>

```
if condição:
  código
elif condição:
  código
else:
  código
```
<h3>Estruturas de Repetição</h3>
<p>While</p>

```
while condição:
  código
else:
  código
```
<p>For</p>

```
for varRef in sequencia:
  código
```
<p>O else pode ser adicionado em ambos, definindo um bloco de código executado imediatamente após o fim do loop</p>
<p>O break encerra o loop (não executa o else)</p>
<p>O continue pula para a próxima iteração</p>

<h3>Pip</h3>
<p>Gerenciamento de pacotes</p>

```
pip install pacote
```
