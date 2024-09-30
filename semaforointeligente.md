# Semáforo inteligente

## Introdução

  Este projeto tem a função de automatizar os semáforos de duas vias de sentidos opostos e facilitar a travessia de pedestres nas faixas das vias em horários de pico ou não. O projeto consiste em:
  
  - 2 semáforos com LEDs vermelho, amarelo e verde para as vias dos carros.
  - 2 semáforos com LEDs vermelho e verde, com sensosr de distância/proximidade (50cm) para os pedestres atravessarem na faixa da via.

  Os sinais das vias dos carros permanecem sempre com LED verde ligado, assim que um pedestre se aproxima da faixa de pedestre, o sensor do semáforo da faixa vai detectar a presença. Fazendo com que os sinais dos carros acionem o LED vermelho e os carros parem.Os pedestres tem 15 segundos para atravessar a faixa. Logo após esse tempo, se o sensor não detectar mais nada, o sinal da faixa acende o LED vermelho, enquanto o sinal da via acende o LED verde.


## Materiais utilizados
  - 1 arduino uno
  - 4 LEDs vermelhos
  - 2 LEDs amarelos
  - 4 LEDs verdes
  - 1 sensor de distância
  - 10 resistores de 1K Ohm
  - 

## Explicação do código

int ledverm1=6;
int ledverm2=7; 
int ledverm3=3;//semaf. pedestre
int ledverm4=10;//semaf. pedestre
int ledverde1=4;
int ledverde2=9;
int ledverde3=2; //semaf. pedestre
int ledverde4=11; //semaf. pedestre
int ledamarelo1=5;
int ledamarelo2=8;
int sensoresquerdo=12;
int sensordireito=13;

void setup()
{
  pinMode(ledverm1,OUTPUT);
  pinMode(ledverm2,OUTPUT);
  pinMode(ledverm3,OUTPUT);
  pinMode(ledverm4,OUTPUT);
  pinMode(ledverde1,OUTPUT);
  pinMode(ledverde2,OUTPUT);
  pinMode(ledverde3,OUTPUT);
  pinMode(ledverde4,OUTPUT);
  pinMode(ledamarelo1,OUTPUT);
  pinMode(ledamarelo2,OUTPUT);
  
  pinMode(sensoresquerdo,INPUT);
  pinMode(sensordireito,INPUT);
}

void loop()
{
  
  // SE UM PEDESTRE CHEGAR DO LADO DIREITO
  // CALCULAR A DISTANCIA DELE EM CM
  int cmd = 0.01723 * direito(sensordireito,sensordireito);
  // SE UM PEDESTRE CHEGAR DO LADO ESQUERDO
  // CALCULAR A DISTANCIA DELE EM CM
  int cme = 0.01723 * esquerdo(sensoresquerdo,sensoresquerdo);
  
  // SE PEDESTRE SE APROXIMAR MENOS DE 1 METRO DO SENSOR ESQUEDO OU DIREITO
  if(cmd<100 || cme<100){ 
  	// DESLIGAR OS LEDS VERDES DO CARRO
    digitalWrite(ledverde1,LOW);
    digitalWrite(ledverde2,LOW);
    // LIGAR OS LEDS AMARELOS DO CARRO
    digitalWrite(ledamarelo1,HIGH);
    digitalWrite(ledamarelo2,HIGH);
    delay(5000);
    //DESLIGAR OS LEDS AMARELOS DO CARRO
    digitalWrite(ledamarelo1,LOW);
    digitalWrite(ledamarelo2,LOW);
    //LIGAR OS LEDS VERMELHOS DO CARRO
    digitalWrite(ledverm1,HIGH);
    digitalWrite(ledverm2,HIGH);
    //DESLIGAR OS LEDS VERMELHOS DO PEDESTRE
    digitalWrite(ledverm3,LOW);
    digitalWrite(ledverm4,LOW);
    //LIGAR OS LEDS VERDES DO PEDESTRE
    digitalWrite(ledverde3,HIGH);
    digitalWrite(ledverde4,HIGH);
    delay(10000);
  }else{
    //DESLIGAR OS LEDS VERDES DO PEDESTRE
    digitalWrite(ledverde3,LOW);
    digitalWrite(ledverde4,LOW);
    //DESLIGAR OS LEDS VERMELHOS DO CARRO
    digitalWrite(ledverm1,LOW);
    digitalWrite(ledverm2,LOW);
    // LIGAR OS LEDS VERDES DO CARRO
    digitalWrite(ledverde1,HIGH);
    digitalWrite(ledverde2,HIGH);
    //LIGAR OS LEDS VERMELHOS DO PEDESTRE
    digitalWrite(ledverm3,HIGH);
    digitalWrite(ledverm4,HIGH);
  }
  
}





// SENSOR DIREITO
long direito(int trigger, int echo){ 
  // trigger porta de saida
  pinMode(trigger,OUTPUT);
  digitalWrite(trigger,LOW);//desligar porta
  delay(5);// espere 5 milisegundos
  //mandando o sinal
  digitalWrite(trigger,HIGH);
  delay(10);// espere 10 milisegundos
  digitalWrite(trigger,LOW);//desligar porta
  // echo porta de entrada
  pinMode(echo,INPUT);//definir porta como entrada
  //retorna os dados que a porta recebe
  return pulseIn(echo,HIGH);
}

// SENSOR ESQUERDO
long esquerdo(int trigger, int echo){ 
  // trigger porta de saida
  pinMode(trigger,OUTPUT);
  digitalWrite(trigger,LOW);//desligar porta
  delay(5);// espere 5 milisegundos
  //mandando o sinal
  digitalWrite(trigger,HIGH);
  delay(10);// espere 10 milisegundos
  digitalWrite(trigger,LOW);//desligar porta
  // echo porta de entrada
  pinMode(echo,INPUT);//definir porta como entrada
  //retorna os dados que a porta recebe
  return pulseIn(echo,HIGH);
}



## Imagem de montagem do circuito

