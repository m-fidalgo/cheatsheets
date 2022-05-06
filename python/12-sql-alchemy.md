<h1 align="center">SQL Alchemy ORM</h1>

<h3>Sobre</h3>
<p>Framework ORM (object-relational mapping): mitiga a impedância objeto-relacional</p>
<p>Instalar com pip (sqlalchemy)</p>

<h3>Criar conexão</h3>

```
engine = create_engine(f"mysql://{user}:{password}@{host}:{port}/{db}")
```
<h3>Entidades</h3>
<p>De modo declarativo</p>

```
from sqlalchemy import Column, Integer, String
from sqlalchemy.ext.declarative import declarative_base

Base = declarative_base()

class NomeTabela(Base):
  __tablename__ = 'nome'
  id = Column(Integer, primary_key=True)
  nome = Column(String(200), nullable=false)
  
  def __repr__(self):
    return "item %s %s", %(self.id, self.nome)
    
Base.metadata.create_all(engine)
```
<p>Com Schemas</p>

```
nomeTab = Table('nome', metadata,
  Column('id', Integer, primary_key=True),
  Column('nome', String(200), nullable=False)
)
```
<h3>Tabelas com Relacionamentos</h3>
<p>Importar relationship de sqlalchemy.orm</p>
<p>Depois dos campos</p>

```
outro_id = Column(Integer, ForeignKey('outraTab.id'), nullable=False)
```
<p>Nas duas tabelas</p>

```
outro = relationship("ClasseOutraTab", back_populates="essaTab")
```
<p>Tabelas auxiliares de relacionamentos</p>

```
aux = Table('aux', Base.metadata,
  Column('tab1_id', Integer, ForeignKey('tab1.id')),
  Column('tab2_id', Integer, ForeignKey('tab2.id'))
)
```
<p>Nas duas tabelas: <b>outro = relationship('ClasseOutraTab', secondary='aux', back_populates='essaTab')</b></p>

<h3>Sessões</h3>
<p>Estabelecer comunicações com o banco: consultas são salvas num mapa de identidade e alterações são retidas até o commit ou rollback</p>

```
connection = self.connect()
Session = SessionMaker()
Session.configure(bind=connection)
session = Session()
```
<p>Inserir: <b>session.add(elemento)</b></p>
<p>Update</p>

```
session.query(NomeClasseTab).filter(classeTab.id == id).update({'nome' = nome, 'tel' = tel})
```
<p>O update também pode ser feito ao pegar o elemento desse id e alterar os campos</p>
<p>Delete</p>

```
item = session.query(NomeClasseTab).filter(ClasseTab.id == id).one()
session.delete(item)
```
<p>Listar</p>

```
items = session.query(NomeClasseTab).all()
```
<p>Ordenar: asc ou desc</p>

```
session.query(NomeClasseTab).filter(condição).order_by(NomeClasseTab.campo.asc()).all()
```
<h3>Eager e Lazy Loading</h3>
<p>Lazy: carrega as entidades de forma que uma nova consulta é feita a cada relacionamento (problema n+1)</p>
<p>Eager: carrega todas as classes relacionadas numa mesma query: importa-se joinedload de sqlalchemy.orm</p>

```
items = session.query(Tabela).options(joinedload(Tabela.items)).all()
```
<h3>Cascade</h3>
<p>Excluir todas as entidades da relação na exclusão: cascade='delete' como último argumento de relationship</p>
