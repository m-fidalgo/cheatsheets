<h1 align="center">Alocação Dinâmica</h1>

<h3>Biblioteca stdio.h</h3>
<li><b>void * malloc(size_t size)</b>: aloca size bytes, retornando o endereço do início do bloco ou NULL em caso de erro</li>
<li><b>void * calloc(size_t n, size_t size)</b>: aloca n itens de sizebytes</li>
<li><b>void * realloc(void *ptr, size_t size)</b>: aloca size bytes (tamanho novo), copiando o conteúdo de ptr para o novo bloco</li>
<li><b>void free(void *ptr)</b>: libera o bloco alocado indicado por ptr</li>
