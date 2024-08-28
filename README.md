Aluno: Rafael - 17100155
"Implementar soft shadow e explicar a diferença de como seria a implementação usando ray-marching."

Neste trabalho utilizei o código fornecido em https://webgl2fundamentals.org/webgl/lessons/webgl-shadows.html que aplica Shadow Mapping e modifiquei de hard shadows para soft shadows.

Nesta implementação foi produzida uma depth texture a partir da perspectiva da luz para mapeamento das sombras e então foi adicionada a técnica de Percentage Closer Filtering (PCF) para aplicar uma suavização nas sombras, amostrando a profundidade ao redor da coordenada projetada no mapa de sombras e calculando uma média para decidir o valor final da sombra nesse local.

A técnica de ray-marching é uma técnica que exige mais processamento, mas permite produzir efeitos de combreamento e volumetria mais complexos.
Consiste em traçar um raio através da cena e percorrê-lo ("marchando" ao longo dele) calculando a cor e iluminação em cada ponto.
Esta técnica trata a cena como uma função contínua que pode ser consultada em qualquer ponto do espaço.
Para implementá-lo no atual código seria necessário modificar o Fragment Shader para iterar ao longo de um raio e usar outra lógica de cálculo de sombra para obter valores de densidade e interação com objetos da cena.
Em resumo, seria necessário lançar um raio a partir da câmera através de cada pixel na tela (o que torna o ray-marching um derivado de ray-tracing), depois o algoritmo deve avançar por cada raio em determinados passos e calcular a densidade ou interação com objeto em cada um.
Baseado no valor de cada passo, é calculado então a sombra, luz e cor daquele ponto no espaço. Cada raio termina quando atinge seu comprimento máximo ou quando encontra um objeto muito denso.

Ray-marching pode ser utilizado em aplicações que trabalham com efeitos volumétricos (nuvens, neblina e fumaça), sombras e iluminação de efeitos volumétricos e em cenários dinâmicos utilizando geometria implícita.
Porém, assim como o ray-tracing, possui um custo maior de processamento que aumenta exponencialmente conforme a quantidade de passos aplicados em cada raio.
