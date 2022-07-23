# Projeto2-Arduino, Robô capaz de desviar de obstáculos e de seguir linhas.
Projeto feito para disciplina "Eletrônica para Computação" com o professor Eduardo do Valle Simões

<img src="./imagens_robo/robo_frente.jpeg">

## Lista de componentes:
* **[Arduino Uno](https://www.wjcomponentes.com.br/arduino-uno-r3?parceiro=6298&gclid=Cj0KCQjwlemWBhDUARIsAFp1rLXXRjnmUf28JuTs7vJEahyzHQNulgMpKd_8ZTKi6LKbq0MQoYi6lK8aAly3EALw_wcB)**;
* **[Arduino Shield Sensor v5](https://www.wjcomponentes.com.br/sensores/shield-sensor-v5?parceiro=6298&gclid=Cj0KCQjwlemWBhDUARIsAFp1rLWyl2DaFC4bJrkin5tWJDtAEjEgp5JKVKMJHvIxLU2Wn70tp_T1jD0aAjr1EALw_wcB)**;
* **[Sensor Ultrassônico](https://www.baudaeletronica.com.br/modulo-de-sensor-ultrassonico-hc-sr04.html?gclid=Cj0KCQjwlemWBhDUARIsAFp1rLVdvVXiuTmYQeKTRq5vNrWMnUuh9OBFf7pbaAqXgq4sLdiVYzUZDXMaAhtGEALw_wcB)**;
* **[3x Sensores infravermelhos de segue linha](https://produto.mercadolivre.com.br/MLB-2161686373-modulo-sensor-seguir-linha-line-tracking-arduino-pic-ky-033-_JM?matt_tool=40343894&matt_word=&matt_source=google&matt_campaign_id=14303413655&matt_ad_group_id=133855953276&matt_match_type=&matt_network=g&matt_device=c&matt_creative=584156655519&matt_keyword=&matt_ad_position=&matt_ad_type=pla&matt_merchant_id=465009696&matt_product_id=MLB2161686373&matt_product_partition_id=1413191055026&matt_target_id=aud-659781599642:pla-1413191055026&gclid=Cj0KCQjwlemWBhDUARIsAFp1rLVtqBApBzplaJBIRardUfLW_B7QpCGPbIMmKj-heDXRZsj137ykEkAaAk7NEALw_wcB)**;
* **[Servo Motor](https://www.eletrogate.com/micro-servo-9g-sg90-towerpro?utm_source=Site&utm_medium=GoogleMerchant&utm_campaign=GoogleMerchant&gclid=Cj0KCQjwlemWBhDUARIsAFp1rLUaxegc2wQdypo5-ttqysj68LCmrH2FXbZtPZ08DoJO0zcGDVi-wysaAmtqEALw_wcB)**;
* **[4x Motores DC](https://www.baudaeletronica.com.br/kit-motor-dc-roda-para-robo.html?gclid=Cj0KCQjwlemWBhDUARIsAFp1rLW00mB4nPtRBvkEDu-Pbi6jc4--7_sxdB1tPdlnvmO11zAOBty6vgkaArnEEALw_wcB)**;
* **[Ponte H](https://www.multcomercial.com.br/driver-motor-ponte-h-l298n-gc-37.html)**;
* **[2x Pilhas Recarregáveis de 3.7V](https://produto.mercadolivre.com.br/MLB-1970377770-bateria-li-ion-18650-6800mah-37v-recarregavel-original-_JM?matt_tool=56291529&matt_word=&matt_source=google&matt_campaign_id=14303413604&matt_ad_group_id=133074303519&matt_match_type=&matt_network=g&matt_device=c&matt_creative=584156655498&matt_keyword=&matt_ad_position=&matt_ad_type=pla&matt_merchant_id=563396324&matt_product_id=MLB1970377770&matt_product_partition_id=1413191054866&matt_target_id=aud-1396166235996:pla-1413191054866&gclid=Cj0KCQjwlemWBhDUARIsAFp1rLWpznwBvGwj6Ps4IEn81zq5ro9gGK0JZ8o83N7dHybLRSwkV-9QbZ4aAt4DEALw_wcB)**.

OBS: Os links são apenas para ajudar na compra, mas o grupo não garante a procedência dessas lojas. 

## Componentes:
<h3>Esse aqui é o Arduino Uno Shield Sensor v5. Usamos ele para conectar no arduino uno e facilitar as conexões dos dados nas entradas e saídas.</h3>
<img src="./imagens_robo/robo_arduino.jpeg"> 

<h3>Essa é a ponte H. Por meio dela, conseguimos controlar os dois motores e fazer o carrinho se mover</h3>
<img src="./imagens_robo/robo_ponteH.jpeg">

<h3>Esses 3 são os sensores infravermelhos de segue linha, eles funcionam com o princípio de que a co preta reflete a luz infravermelha de maneira diferente da branca, assim o carro consegue detectar uma linha preta no chão, por exemplo, e com a programação certa segui-la</h3>
<img src="./imagens_robo/robo_baixo.jpeg">

<h3>Esses são os sensores ultrassônicos do robô(com umas folhinhas de papel para parecer o Wall-E). Elas emitem um sinal sonoro e por meio do tempo que esse sinal leva para retornar calculam a distância até um certo objeto. Por meio delas, por exemplo, conseguimos fazer o carro detectar um obstáculo e desviar de direção<p></h3>
<img src="./imagens_robo/sonar.jpg">

<h3>Aqui é a fonte de alimentação do nosso projeto, utilizamos duas pilhas de 3.7V para conseguir alimentar o sonar a ponte H o arduino e os sensores infravermelhos.<p></h3>
<img src="./imagens_robo/robo_bateria.jpeg">



## Diagrama:
<img src="./imagens_robo/robo_diagrama_esquematico.jpg">
<img src="./imagens_robo/robo_diagrama_tabela.jpeg">

## Vídeo de funcionamento:

https://youtu.be/LGvDf1pJzMQ

## Códigos usados

#### Cógido para seguir linha (arquivo segue_linha)

      #include <Servo.h>
      Servo myservo;

      
      /* definir leitor de linha */
      #define LT1 digitalRead(11)
      #define LT2 digitalRead(4)
      #define LT3 digitalRead(2)


      /* definir pinos de saida de controle logico */
      int in1=9;
      int in2=8;
      int in3=7;
      int in4=6;
      
      /* definir pinos de saida de habilitacao de canal */
      int ENA=12;
      int ENB=5;
      
      /* funcao de movimento para frente */
      void _mForward()
      { 
        digitalWrite(ENA,HIGH);
        digitalWrite(ENB,HIGH);
        digitalWrite(in1,LOW);//digital output
        digitalWrite(in2,HIGH);
        digitalWrite(in3,HIGH);
        digitalWrite(in4,LOW);
        Serial.println("Forward");
      }
      /* funcao de curva para a esquerda */
      void _mleft()
      {
        digitalWrite(ENA,HIGH);
        digitalWrite(ENB,HIGH);
        digitalWrite(in1,LOW);
        digitalWrite(in2,HIGH);
        digitalWrite(in3,LOW);
        digitalWrite(in4,HIGH);
        Serial.println("Left");
      }
      /* funcao de curva para a direita */
      void _mright()
      {
        digitalWrite(ENA,HIGH);
        digitalWrite(ENB,HIGH);
        digitalWrite(in1,HIGH);
        digitalWrite(in2,LOW);
        digitalWrite(in3,HIGH);
        digitalWrite(in4,LOW);
        Serial.println("Right");
      }
      
      void setup() {
        /* Abre a porta serial e define a taxa de transmissao para 9600 */
        Serial.begin(9600);
        
        /* Configura os pinos declarando como saida */
        pinMode(in1,OUTPUT);
        pinMode(in2,OUTPUT);
        pinMode(in3,OUTPUT);
        pinMode(in4,OUTPUT);
        pinMode(ENA,OUTPUT);
        pinMode(ENB,OUTPUT);
        
        
        /* indica qual entrada do arduino sera usada */
        /* o servo apenas esta sendo usado nesse codigo a fim de que o robo "olhe" para a direcao para a qual esta andando */
        myservo.attach(3);  
      }
      
      void loop() {
        /* anda para frente quando e retornado sinal do sensor central */
        if(LT2){
          myservo.write(90);
          _mForward();
        }
        /* anda para a esquerda quando e retornado sinal do sensor da esquerda */
        else if(LT1) { 
          myservo.write(120);
          _mleft();                            
        }   
        /* anda para a direita quando e retornado sinal do sensor da direita */
        else if(LT3) {
          myservo.write(60);
          _mright();
        }
      }
      
#### Código para desviar de obstáculos (arquivo desvia_de_obstaculos)

      #include <Servo.h>
      Servo myservo;
      
      /* definir pinos de saida de controle logico */
      int Echo = A5;  
      int Trig = A4; 
      int in1=9;
      int in2=8;
      int in3=7;
      int in4=6;
      
      /* definir pinos de saida de habilitacao de canal */
      int ENA=12;
      int ENB=5;
      
      /* inteiro que define a velocidade do motor */
      /* para uso do ABS, altere as funcoes digitalWrite() dos pinos ENA e ENB nas funcoes de movimento para analogWrite() e troque HIGH pela variavel ABS */
      int ABS = 150;
      
      /* inicializa as entradas como zero */
      int rightDistance = 0,leftDistance = 0,middleDistance = 0;
      
      /* funcao de movimento para frente */
      void _mForward()
      { 
        digitalWrite(ENA,HIGH);
        digitalWrite(ENB,HIGH);
        digitalWrite(in1,LOW);//digital output
        digitalWrite(in2,HIGH);
        digitalWrite(in3,HIGH);
        digitalWrite(in4,LOW);
        Serial.println("Forward");
      }
      
      /* funcao de movimento para tras */
      void _mBack()
      {
        digitalWrite(ENA,HIGH);
        digitalWrite(ENB,HIGH);
        digitalWrite(in1,HIGH);
        digitalWrite(in2,LOW);
        digitalWrite(in3,LOW);
        digitalWrite(in4,HIGH);
        Serial.println("Back");
      }
      
      /* funcao de curva para a esquerda */
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
      
      /* funcao de curva para a direita */
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
      
      /* funcao de interromper movimento */
      void _mStop()
      {
        digitalWrite(ENA,LOW);
        digitalWrite(ENB,LOW);
        Serial.println("Stop!");
      }
      
      /* funcao que retorna, em centimetros, a distancia lida pelo sonar */
      int Distance_test()   
      {
        digitalWrite(Trig, LOW);   
        delayMicroseconds(2);
        digitalWrite(Trig, HIGH);  
        delayMicroseconds(10);
        digitalWrite(Trig, LOW);
        delayMicroseconds(2);   
        long duracao = pulseIn(Echo, HIGH, 150000L);  
        int Fdistance= duracao * 0.034 / 2;
        delay(25);       
        return Fdistance;
      }  
      
      
      void setup() {
        /* Abre a porta serial e define a taxa de transmissao para 9600 */
        Serial.begin(9600); 
        
        /* Configura os pinos declarando como saida */
        pinMode(Echo, INPUT);    
        pinMode(Trig, OUTPUT); 
        pinMode(in1,OUTPUT);
        pinMode(in2,OUTPUT);
        pinMode(in3,OUTPUT);
        pinMode(in4,OUTPUT);
        pinMode(ENA,OUTPUT);
        pinMode(ENB,OUTPUT);
        
        /* indica qual entrada do arduino sera usada */
        myservo.attach(3);
        
        _mStop();  
      }
      
      void loop() {
          myservo.write(90);
          delay(500); 
          middleDistance = Distance_test();
          #ifdef send
          #endif

          /* encontra obstaculo na frente */
          if(middleDistance < 60)
          {    
            /* le distancia da direita */
            _mStop();
            delay(500);                         
            myservo.write(20); //10°-180°          
            delay(1000);      
            rightDistance = Distance_test();

            #ifdef send
            #endif
            
            /* le distancia da esquerda */
            delay(500);
            myservo.write(90);              
            delay(1000);                                                  
            myservo.write(170);              
            delay(1000); 
            leftDistance = Distance_test();

            #ifdef send
            #endif

            delay(500);
            myservo.write(90);              
            delay(1000);
            
            /* caso sejam encontrados obstaculos na frente, na direita e atras: movimento para tras */
            if(rightDistance<20 && leftDistance < 20)  
            {
              _mBack();
              delay(1000);
              _mStop();
             }
             
             /* ostaculo na frente e na esquerda: movimento para a direita */
             else if(leftDistance< 20)
             {
              _mright();
              delay(1000);
              _mStop();
             }
             
             /* obstaculo na frente e na direita: movimento para a esquerda */
             else if(rightDistance<20)
             {
              _mleft();
              delay(1000);
              _mStop();
             }
             
             /* obstaculo apenas na frente: da uma re e faz um movimento para a esquerda */
             else
             {
              _mBack();
              delay(500);
              _mleft();
              delay(500);
              _mStop();
             }
          }  
          
          /* movimento para a frente ate encontrar um obstaculo */
          else
          {
            _mForward();                     
          }
      }

## Alunos:

Artur De Vlieger Lima

Calebe Damas Nogueira

Gabriel Sousa Santos de Almeida

