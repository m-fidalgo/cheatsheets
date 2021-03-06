<h1 align="center">Pseudo-classes</h1>

<h3>Elementos Filhos</h3>
<li><b>:first-child</b> primeiro filho do elemento pai</li>
<li><b>:first-of-type</b> primeiro elemento de seu tipo entre os filhos do elemento pai</li>
<li><b>:last-child</b> último filho do elemento pai</li>
<li><b>:last-of-type</b> último elemento de seu tipo entre os filhos do elemento pai</li>
<li><b>:nth-child(num)</b> o elemento s1 deve ser o num-ésimo filho de seu pai</li>
<li><b>:nth-last-child(num)</b> começa a contar a partir do último</li>
<li><b>:nth-of-type(num)</b> o num-ésimo filho de seu pai, de seu tipo</li>
<li><b>:nth-last-of-type(num)</b> começa a contar a partir do último, considerando apenas elementos do seu tipo</li>
<li><b>:empty</b> elementos sem filhos (outros elementos ou texto)</li>
<li><b>:only-child</b> elementos sem irmãos</li>
<li><b>:only-of-type</b> elementos sem irmãos do mesmo tipo</li>

<h3>Links e Foco</h3>
<li><b>:hover</b> o mouse está em cima do elemento</li>
<li><b>:focus</b> quando o elemento recebe foco: o usuário seleciona o elemento com o teclado/mouse</li>
<li><b>:link</b> regras para links não visitados</li>
<li><b>:visited</b> regras para links já visitados</li>
<li><b>:active</b> regras para enquanto o link está sendo clicado (links ativos). Para funcionar corretamente deve vir depois de outros seletores relacionados a links</li>

<h3>Elementos de Formulários</h3>
<li><b>:checked</b> quando o radio/checkbox/option está selecionado</li>
<li><b>:default</b> elementos que são o default num grupo de elementos semelhantes</li>
<li><b>:disabled</b> elementos desativados</li>
<li><b>:enabled</b> elementos ativados</li>
<li><b>:in-range</b> elementos input cujo conteúdo está dentro do limite estabelecido pelos atributos min e max do input</li>
<li><b>:out-of-range</b> elementos input cujo conteúdo está fora do limite</li>
<li><b>:invalid</b> elementos input/form cujo conteúdo não é válido</li>
<li><b>:valid</b> oposto de :invalid</li>
<li><b>:optional</b> elementos input/select/textarea sem o atributo required</li>
<li><b>:required</b> oposto de :optional</li>
<li><b>:read-only</b> elementos input/textarea que não podem ser editados pelo usuário</li>
<li><b>:read-write</b> elementos input/textarea que podem ser editados pelo usuário</li>

<h3>Outros</h3>
<li><b>:not(s2)</b> aplica em todo s1 que não é s2</li>
<li><b>:fullscreen</b> elementos em tela cheia</li>
<li><b>:target</b> o elemento alvo com o id que está na url</li>

