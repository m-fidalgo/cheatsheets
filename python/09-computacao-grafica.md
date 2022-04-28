<h1 align="center">Computação Gráfica</h1>
<p align="center"><a href="#gerar">Geração de Linhas e Circunferências</a></p>
<br />

<h2 align="center" id="gerar">Geração de Linhas e Circunferências</h2>
<p align="center"><a href="#tela">Tela</a> | <a href="#primitiva-linha">Classe para Primitiva de Linha</a></p>


<h3 id="tela">Tela</h3>
<p>Classe para gerenciar a tela</p>
<p>Todos os métodos dentro de <b>class Screen(object):</b></p>
<p>Bibliotecas</p>

```
import pygame
import numpy as np
from copy import copy
```

<p>Construtor</p>

```
  def __init__(self, title, bgColor, width, height):
    self.title = title                                 # título da janela
    self.bgColor = bgColor                             # cor de fundo
    self.width = width                                 # largura da janela
    self.height = height                               # altura da janela
    self.screen = pygame.display.set_mode(self.size()) # define o tamanho da tela
    pygame.display.set_caption(self.title)             # define o título da janela
```
<p>Executar o pipeline gráfico</p>

```
  def run(self, obj):
    while True:  # laço principal
      # captura eventos
      for event in pygame.event.get(): 
        # Captura evento de clicar em botão para fechar
        if event.type == pygame.QUIT:
            return pygame.quit()
      
      # preencha a tela com a cor de fundo
      self.screen.fill(self.bgColor)
      
      # gera o desenho
      obj.draw(self);
      
      # aplica o antialiasing
      self.meanFilter()
      
      # atualiza a tela 
      pygame.display.update()
 ```
 <p>Métodos Úteis</p>
 
 ```       
  # retorna um vetor com o tamanho da tela
  def size(self):
    return (self.width, self.height)
    
  # modifica um pixel na tela com a cor desejada
  def setPixel(self, x, y, color):
    self.screen.set_at((x, y), color)
```
<p>Filtro da Média (Antialising)</p>

```
  def meanFilter(self):
    # Captura a matrix da tela
    frameBuffer2 = pygame.PixelArray(self.screen)
    
    frameBuffer = pygame.surfarray.array3d(self.screen)
    #print(frameBuffer)
    
    mask = np.ones((3, 3)) * 1/9 
    #print(mask)
    
    temp = np.zeros((3))
            
    for i in range(1, self.width - 1):
      for j in range(1, self.height - 1):    
        subI = frameBuffer[i-1:i+2,j-1:j+2, 0]
        temp[0] = np.sum(np.multiply(subI, mask))
        #display(temp)
        
        subI = frameBuffer[i-1:i+2,j-1:j+2, 1]
        temp[1] = np.sum(np.multiply(subI, mask))
        #display(temp)
        
        subI = frameBuffer[i-1:i+2,j-1:j+2, 2]
        temp[2] = np.sum(np.multiply(subI, mask))
        #display(temp)
        
        #temp = np.zeros((3))
        
        #for k in range(-1,2):
        #    for l in range(-1,2):
        #        for b in range(3):
        #            temp[b] = temp[b] + frameBuffer[i + k][j + l][b] * mask[k + 1][l + 1]
                
        #print(pygame.Color(int(temp[0]), int(temp[1]), int(temp[2]), 255))
                
        self.setPixel(i, j, pygame.Color(int(temp[0]), int(temp[1]), int(temp[2]), 255));
        #frameBuffer2[i][j] = pygame.Color(int(temp[0]), int(temp[1]), int(temp[2]), 255);
```

<h3 id="primitiva-linha">Classe para Primitiva de Linha</h3>
<p>Tudo dentro de <b>class Line(object):</b></p>
<p>Construtor</p>

```
  def __init__(self, x1, y1, x2, y2, color):
    self.x1 = x1       # coordenada x do primeiro ponto
    self.x2 = x2       # coordenada x do segundo ponto
    self.y1 = y1       # coordenada y do primeiro ponto
    self.y2 = y2       # coordenada y do segundo ponto
    self.color = color # cor do objeto
```
<p>Renderizar a linha desejada</p>

```
  def draw(self, screen):
    self.dda(screen)
```
<p>Algoritmo DDA</p>

```
  def dda(self, screen):      
    # Definição e Inicialização de Variáveis locais
    dx, dy, k = 0, 0, 0
    x_inc, y_inc = 0.0, 0.0
    x, y = 0.0, 0.0

    # Define os deslocamentos nas direções x e y
    dx = self.x2 - self.x1
    dy = self.y2 - self.y1

    # Define qual a direção de incremento fixo
    if abs(dx) > abs(dy):
      iter = abs(dx)
    else:
      iter = abs(dy)
    
    # Define os incrementos para cada direção
    x_inc = dx/iter
    y_inc = dy/iter

    # Define o ponto inicial
    x = self.x1
    y = self.y1

    # Desenha o ponto inicial na tela
    screen.setPixel(round(x), round(y), self.color)

    # Geração e renderização dos pontos seguintes da linha
    for k in range(iter):
      # Gera o próximo ponto
      x = x + x_inc
      y = y + y_inc
      
      # Desenha o ponto
      screen.setPixel(round(x), round(y), self.color)
          
```
<p>Algoritmo Bresenham</p>

```
def bresenham(self, screen):
    # Definição e inicialização de variáveis locais
    dx, dy, d = 0, 0, 0
    incrE, incrNE = 0, 0
    x, y, xFinal = 0, 0, 0
    
    # Define os deslocamentos absolutos nas direções x e y
    dx = abs(self.x2 - self.x1)
    dy = abs(self.y2 - self.y1)
    
    # Define o d de teste inicial
    d = 2 * dy - dx
    
    # Define os incrementos nas direções x e y
    incrE = 2 * dy
    incrNE = 2 * (dy - dx)
    
    # Troca a ordem dos pontos em caso de segundo ponto à esquerda de primeiro ponto
    if self.x1 > self.x2:
      x = self.x2
      y = self.y2
      xFinal = self.x1
    else:
      x = self.x1
      y = self.y1
      xFinal = self.x2
    
    # Desenha o ponto inicial na tela
    screen.setPixel(x, y, self.color)
    
    # Gera e renderiza os pontos seguintes da linha
    while x < xFinal:
      # Gera o próximo ponto
      x = x + 1
      
      if d < 0:
        d = d + incrE
      else:
        y = y + 1
        d = d + incrNE
      
      # Desenha o próximo ponto
      screen.setPixel(x, y, self.color)
```

