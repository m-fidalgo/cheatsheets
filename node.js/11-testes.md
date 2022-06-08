<h1 align="center">Testes</h1>
<p align="center"><a href="#jest">Jest</a> | <a href="#jasmine">Jasmine</a></p>

<h2 align="center" id="jest">Jest</h2>

<h3>Configurar</h3>
<p>Instalar jest (-D) e iniciar: <b>npx jest --init</b> -> Y, node, N, Y</p>
<p>O arquivo jest.config.js foi criado: criar a pasta tests e, dentro dela, as pastas unit e integration</p>
<p>Testes são nomeados no modelo nomeCoisaTestada.spec.js</p>

<h3>Testes de Integração</h3>
<p>Deve-se configurar um BD específico para os testes: no knexfile.js, copiar e colar development, mudando para test e trocando filename por test.sqlite</p>
<p>Instalar cross-env: em package.json, mudar scripts>test: <b>"cross-env NODE_ENV=test jest --runInBand"</b></p>
<p>Em connection.js, mudar as consts config e connection</p>

```
const config = process.env.NODE_ENV == 'test' ? configs.test : configs.development
const connection = knex(config)
```
<p>Em tests>integration, criar nome.spec.js e instalar supertest (-D). Criar server.js, renomear index.js para app.js e em package.json, script>start, mudar de index para server.js. Em app.js, apagar e add <b>module.exports = app</b></p>
<p>Em server.js, importar app e adicionar <b>app.listen(3333)</b></p>
<p>Em nome.spec.js, importar app, supertest e connection.js</p>
<p>Exemplo - user.spec.js</p>

```
describe('user', () => {
  // antes dos testes
  beforeAll(async () => {
    // desfazer migrations: limpar BD teste
    await connection.migrate.rollback();
    // executar as migrations
    await connection.migrate.latest();
  });
  
  // após todos os testes
  afterAll(async () => {
    // destruir a conexão com o BD
    await connection.destroy();
  });
})
```
<p>Teste para insert na tabela</p>

```
it('should be able to create a new user', async () => {
  const resp = await request(app)
    .post('/user')
    .send({email: 'test@ex.com', phone: '111111111', password: 'teste'});
    
  expect(resp.status).toBe(200);
  expect(resp.body).toHaveProperty('id');
});
```
<p>Teste para listagem</p>

```
it('should be able list all users', async () => {
  const resp = await request(app).get('/user');
  const response = [{id: 1, email: 'test@ex.com', phone: '111111111', password: 'teste'}];
  expect(resp.status).toBe(200);
  expect(resp.body).toEqual(response);
});
```

<h2 align="center" id="jasmine">Jasmine</h2>

<h3>Configurar</h3>
<p>Instalar jasmine (-g). O comando <b>jasmine init</b> cria o diretório spec (dentro dele ficarão os arquivos de teste: nome.spec.js) e, dentro dele, o diretório support, onde estará o arquivo de configurações jasmine.json. O comando <b>jasmine</b> executa os testes, e <b>nodemon --exec jasmine</b> faz com que eles sejam executados a cada alterção de código</p>

<h3>Funções</h3>
<p><b>describe()</b> define algum componente da aplicação, iniciando uma suíte de testes (podem ser aninhados)</p>
<p><b>it()</b> especificação (spec). Recebe uma descrição do que o código deve fazer e uma função de teste</p>
<p>Exemplo</p>

```
const funcaoTestada = require(funcao);

describe('Função Testada', function() {
  it('has to print teste', function() {
    const text = funcaoTestada();
    expect(text).toEqual('teste');
  });
})
```
<h3>Matchers</h3>
<ul>
  <li><b>toBe</b> verifica se são o mesmo objeto</li>
  <li><b>toBeTruthy / toBeFalsy</b> verdadeiro ou falso. 0, null, false, "", NaN e undefined são considerados falsos</li>
  <li><b>toEqual</b> se o conteúdo é igual</li>
  <li><b>not</b> inverte outro matcher</li>
  <li><b>toContain</b> se o elemento está presente em outro</li>
  <li><b>toBeDefined / toBeUndefined</b> se o elemento está definido</li>
  <li><b>toBeNull / toBeNan</b> se é null ou NaN</li>
  <li><b>toBeGreaterThan / toBeLessThan</b> maior ou menor</li>
  <li><b>toBeCloseTo</b> passa-se um número e uma quantia de precisão de casas decimais</li>
  <li><b>toMatch</b> verifica o valor com regex</li>
  <li><b>toThrow</b> se a função retorna erro</li>
</ul>

<h3>Before e After</h3>
<p><b>beforeEach</b> e <b>afterEach</b>: executar algo antes/depois de cada spec</p>
<p><b>beforeAll</b> e <b>afterAll</b>: executar algo antes/depois da execução de todos os specs</p>

<h3>Ignorar Specs e Suítes</h3>
<p>Colocar um * antes de describe/it</p>

<h3>Criar Matcher</h3>

```
const myMatchers = {
  nomeMatcher: function(util, customEqualityTesters) {
    return {
      compare: function(actual, expected) {
        var result = {};
        result.pass = // condição para passar no teste
        
        if(!result.pass)
          result.message = // mensagem de erro
          
        return result
      }
    }
  }
}
```
<p>Definir matchers criados</p>

```
beforeEach(function() {
  jasmine.addMatchers(myMatchers);
})
```
<h3>Comparar tipos de valores</h3>
<p>Exemplo</p>

```
expect(whatever).toEqual(jasmine.any(Boolean))
```
<h3>Spies</h3>
<p>Permitem verificar pedaços de código, modificar funções, rastrear suas chamadas e parâmetros</p>
<p>Função / objeto que substitui parte do código</p>
<p>Só existe no bloco em que foi declarado (removido depois)</p>
<p>Não retorna nada quando substitui uma função</p>
<p>Exemplo base</p>

```
class Calculator {
  sum(n1, n2) {
    return n1 + n2;
  }
}

class Person {
  randomCalc(calculator) {
    var n1, n2;
    return `${calculator.sum(n1, n2)}`;
  }
}

describe('Person', function() {
  it('uses the calculator to sum', function() {
    var calculator = new Calculator();
    var person = new Person();
    
    // testes
  }); 
});
```
<p>Testar se a função existente está sendo usada</p>

```
// substitui sum por um spy
spyOn(calculator, 'sum');
person.randomCalc(calculator);
expect(calculator.sum).toHaveBeenCalled();
```
<p>Ver se a função foi chamada com certo parâmetro</p>

```
spyOn(person, 'randomCalc');
person.randomCalc(calculator);
expect(person.randomCalc).toHaveBeenCalledWith(calculator);
```
<p>Manter o retorno da função original</p>

```
spyOn(person, 'randomCalc').and.callThrough();
var result = person.randomCalc(calculator);
```
<p>Retornar um valor definido</p>

```
spyOn(person, 'randomCalc').and.returnValue(valor);
var result = person.randomCalc(calculator);
```
<p>Alterar o código a ser executado por uma função</p>

```
const fakeFunction = function() {
  return 'teste';
}

spyOn(person, 'randomCalc').and.callFake(fakeFunction);
```
<p>Spy para uma função que não existe</p>

```
it('uses the calculator do divide', function() {
  var calculator = new Calculator();
  var person = new Person();
  
  person.randomDivision = jasmine.createSpy('div spy');
  person.randomDivision(calculator);
  expect(person.randomDivision).toHaveBeenCalled();
});
```
<p>Objetos spy</p>

```
var tape;

beforeEach(function() {
  tape = jasmine.createSpyObj('tape', ['play', 'pause', 'stop', 'rewind']);
  tape.play();
  tape.rewind();
});
```
<p>Outras propriedades</p>
<ul>
  <li><b>.calls.any()</b> false se o spy não foi chamado</li>
  <li><b>.calls.count()</b> número de vezes que o spy foi chamado</li>
  <li><b>.calls.argsFor(index)</b> parâmetros passados, por index</li>
  <li><b>.calls.allArgs()</b> todos os parâmetros passados</li>
  <li><b>.calls.all()</b> conexto (this) + parâmetros passados pelas chamadas</li>
  <li><b>.calls.mostRecent()</b> contexto e parâmetros da chamada mais recente</li>
  <li><b>.calls.first()</b> conexto e parâmetros da primeira chamada</li>
  <li><b>.calls.reset()</b> limpa os dados armazenados no spy</li>
</ul>

<h3>Testes assíncronos</h3>
<p>Colocar o código assíncrono dentro de beforeEach</p>

```
beforeEach(function(done) {
  myAsyncFunc().then(done)
});
```
