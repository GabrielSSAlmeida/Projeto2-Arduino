# Projeto2-Arduino, Robô capaz de desviar de obstáculos e de seguir linhas.
Projeto feito para disciplina "Eletrônica para Computação" com o professor Eduardo do Valle Simões

<img src="./imagens_robo/robo_frente.jpeg">

## Lista de componentes:
* **Arduino Uno**;
* **Arduino Shield Sensor v5**;
* **Sensor Ultrassônico**;
* **3x Sensores infravermelhos de segue linha**;
* **Servo Motor**;
* **4x Motores DC**;
* **Ponte H**;
* **2x Pilhas Recarregáveis de 3.7V**.

## Componentes:
<h3>Esse aqui é o Arduino Uno Shield Sensor v5. Usamos ele para conectar no arduino uno e facilitar as conexões dos dados nas entradas e saídas.</h3>
<img src="./imagens_robo/robo_arduino.jpeg"> 

<h3>Essa é a ponte H. Por meio dela, conseguimos controlar os dois motores e fazer o carrinho se mover</h3>
<img src="./imagens_robo/robo_ponteH.jpeg">

<h3>Esses 3 são os sensores infravermelhos de segue linha, eles funcionam com o princípio de que a co preta reflete a luz infravermelha de maneira diferente da branca, assim o carro consegue detectar uma linha preta no chão, por exemplo, e com a programação certa segui-la</h3>
<img src="./imagens_robo/robo_baixo.jpeg">

<h3>Esses são os sensores ultrassônicos do robô(com umas folhinhas de papel para parecer o Wall-E). Elas emitem um sinal sonoro e por meio do tempo que esse sinal leva para retornar calculam a distância até um certo objeto. Por meio delas, por exemplo, conseguimos fazer o carro detectar um obstáculo e desviar de direção<p></h3>
<img src="./imagens_robo/sonar.jpeg">

<h3>Aqui é a fonte de alimentação do nosso projeto, utilizamos duas pilhas de 3.7V para conseguir alimentar o sonar a ponte H o arduino e os sensores infravermelhos.<p></h3>
<img src="./imagens_robo/robo_bateria.jpeg">



## Diagrama:
<img src="./imagens_robo/robo_diagrama_esquematico.jpeg">
<img src="./imagens_robo/robo_diagrama_tabela.jpeg">

## Vídeo de funcionamento:

## Códigos usados estão nos arquivos segue_linha e desvia_de_obstaculos

## Alunos:

Artur De Vlieger Lima

Calebe Damas Nogueira

Gabriel Souza Santos de Almeida

