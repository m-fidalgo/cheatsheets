<h1 align="center">Armazenamento de Dados</h1>

<h3>Local Storage</h3>
<p>Dados compartilhados entre todas as guias e janelas da mesma origem</p>
<p>Os dados não expiram, permanecendo após o fechamento do navegador e reboot do SO</p>
<p>Limita o tamanho dos dados que podem ser armazenados, devem ser em string</p>

```
// Guardar um valor
localStorage.setItem('nome', valor);

// Resgatar um valor
localStorage.getItem('nome');

// Remover um valor
localStorage.removeItem('nome');

// Limpar todos os valores:
localStorage.clear();
```
<h3>Session Storage</h3>
<p>Existe apenas no contexto da guia atual</p>
<p>Os dados sobrevivem o reload da guia, mas são perdidos ao fechar o navegador</p>

```
// Guardar um valor
sessionStorage.setItem('nome', valor);

// Resgatar um valor
sessionStorage.getItem('nome');

// Remover um valor
sessionStorage.removeItem('nome');

// Limpar todos os valores:
sessionStorage.clear();
```
