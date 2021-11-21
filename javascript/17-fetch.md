<h1 align="center">Fetch</h1>

<h3>Sobre</h3>
<p>Modo do ES6 de fazer requisições</p>
<p>Retorna uma Promise, que retorna um objeto response com a resposta do servidor</p>
<p>Apenas o 1º parâmetro é obrigatório</p>

<h3>Exemplo</h3>

```
fetch('enderecoRequisicao', {
        method: 'GET',
        headers: {'Content-Type': 'application/json'}
     })
     .then(response => response.json());
```
