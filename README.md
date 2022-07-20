# Projeto2-Arduino, Robô capaz de desviar de obstáculos e de desviar de linhas.
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

<h3>Esses 3 são os sensores infravermelhos d segue linha, eles funcionam com o princípio de que a co preta reflete a luz infravermelha de maneira diferente da branca, assim o carro consegue detectar uma linha preta no chão, por exemplo, e com a programação certa segui-la</h3>
<img src="./imagens_robo/robo_baixo.jpeg">

<h3>Esses são os sensores ultrassônicos do robô(com umas folhinahs de papel para parecer o Wall-E). Elas emitem um sinal sonoro e por meio do tempo que esse sinal leva para retornar calculam a distância até um certo objeto. Por meio delas, por exemplo, conseguimos fazer o carro detectar um obstáculo e desviar de direção<p></h3>
<img src="./imagens_robo/sonar.jpeg">

<h3>Aqui é a fonte de alimentação do nosso projeto, utilizamos duas pilhas de 3.7V para conseguir alimentar o sonar a ponte H o arduino e os sensores infravermelhos.<p></h3>
<img src="./imagens_robo/robo_bateria.jpeg">



## Diagrama:

## Vídeo de funcionamento:

## Códigos usados:

'''
//www.elegoo.com
//2016.09.12
#include <Servo.h>
Servo myservo;


#define LT1 digitalRead(11)
#define LT2 digitalRead(4)
#define LT3 digitalRead(2)


/*define logic control output pin*/
int in1=9;
int in2=8;
int in3=7;
int in4=6;
/*define channel enable output pins*/
int ENA=12;
int ENB=5;
/*define forward function*/
void _mForward()
{ 
  digitalWrite(ENA,10);
  digitalWrite(ENB,10);
  digitalWrite(in1,LOW);//digital output
  digitalWrite(in2,HIGH);
  digitalWrite(in3,HIGH);
  digitalWrite(in4,LOW);
  Serial.println("Forward");
}
/*define back function*/
void _mBack()
{
  digitalWrite(ENA,10);
  digitalWrite(ENB,10);
  digitalWrite(in1,HIGH);
  digitalWrite(in2,LOW);
  digitalWrite(in3,LOW);
  digitalWrite(in4,HIGH);
  Serial.println("Back");
}
/*define left function*/
void _mleft()
{
  digitalWrite(ENA,10);
  digitalWrite(ENB,10);
  digitalWrite(in1,LOW);
  digitalWrite(in2,HIGH);
  digitalWrite(in3,LOW);
  digitalWrite(in4,HIGH);
  Serial.println("Left");
}
/*define right function*/
void _mright()
{
  digitalWrite(ENA,10);
  digitalWrite(ENB,10);
  digitalWrite(in1,HIGH);
  digitalWrite(in2,LOW);
  digitalWrite(in3,HIGH);
  digitalWrite(in4,LOW);
  Serial.println("Right");
}
/*put your setup code here, to run once*/
void setup() {
 Serial.begin(9600); //Open the serial port and set the baud rate to 9600
/*Set the defined pins to the output*/
  pinMode(in1,OUTPUT);
  pinMode(in2,OUTPUT);
  pinMode(in3,OUTPUT);
  pinMode(in4,OUTPUT);
  pinMode(ENA,OUTPUT);
  pinMode(ENB,OUTPUT);
  
  myservo.attach(3);  
}
/*put your main code here, to run repeatedly*/
void loop() {
/*delay(3000);
_mForward();
delay(1000);
_mBack();
delay(1000);
_mleft();
delay(1000);
_mright();
delay(1000);*/
  if(LT2){
    myservo.write(90);
    _mForward();
  }
  else if(LT1) { 
    myservo.write(120);
    _mleft();                            
  }   
  else if(LT3) {
    myservo.write(60);
    _mright();
  }
}
'''

## Alunos:

Artur De Vlieger Lima

Calebe Damas Nogueira

Gabriel Souza Santos de Almeida

