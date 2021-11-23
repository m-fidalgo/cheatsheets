<h1 align="center">Strings</h1>

<h3>Declaração</h3>
<p>O tamanho deve considerar o caracter de fim de string '\0'</p>

```
char nome[tamanho];
char nome[] = "conteudo";
char *nome = "conteudo";
```
<h3>Ler String</h3>
<p>O scanf para a leitura quando o espaço é pressionado</p>

```
scanf(" %s", nome);
gets(nome);
```
<h3>Biblioteca ctype.h</h3>
<p>Funções para trabalhar com caracteres</p>
<li>int isdigit(int c)</li>
<li>int isalpha(int c)</li>
<li>int isalnum(int c)</li>
<li>int islower(int c)</li>
<li>int isupper(int c)</li>
<li>int tolower(int c)</li>
<li>int toupper(int c)</li>

<h3>Biblioteca string.h</h3>
<li><b>char * strcpy(char *s1, const char *s2)</b>: copia s2 em s1</li>
<li><b>char * strncpy(char *s1, const char *s2, size_t n)</b>: copia os n primeiros caracteres de s2 em s1</li>
<li><b>char * strcat(char *s1, const char *s2)</b>: copia s2 no final de s1</li>
<li><b>char * strncat(char *s1, const char *s2, size_t n)</b>: copia os n primeiros caracteres de s2 no final de s1</li>
<li><b>int strcmp(const char *s1, const char *s2)</b>: compara s1 e s2, retornando 0 se s1=s2, <0 se s1<s2 e >0 se s1>s2</li>
<li><b>int strncmp(const char *s1, const char *s2, size_t n)</b>: compara os n primeiros caracteres de s1 e s2</li>
<li><b>size_t strlen(const char *s)</b>: retorna o tamanho de s (desconsiderando \0)</li>
<li><b>char * strchr(const char *s, int c)</b>: retorna um ponteiro para a primeira ocorrência de c em s (ou NULL)</li>
<li><b>char * strstr(const char *s2, const char *s2)</b>: retorna um ponteiro para a primeira ocorrência de s2 em s1 (ou NULL)</li>
<li><b>char * strtok(char *s1, const char *s2)</b>: separa em tokens</li>

<h3>Biblioteca stdlib.h</h3>
<li><b>double atof(const char *s)</b>: converte a string em double</li>
<li><b>int atoi(const char *s)</b>: converte a string em int</li>
<li><b>long atol(const char *s)</b>: converte a string em long int</li>
