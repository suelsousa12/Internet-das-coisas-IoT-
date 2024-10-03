// C++ code

// Variável do LED
int ledvermelho = 4;
// Variável do sensor
int sensor = 3;
// Variável para salvar a porta que o servo está
int servo = 2;
/* Criando objeto do tipo servo motor para
usar as funções de controle do equipamento
(servo motor)*/
Servo objetoservo;


void setup()
{
  // Definindo LEd como saída de sinal
  pinMode(ledvermelho,OUTPUT);
  // Definindo sensor como entrada de sinal
  pinMode(sensor,INPUT);
  // A inicializando do servo na portadigital 2
  objetoservo.attach(servo);
  // Servo começa na posição 0
  objetoservo.write(0); 
}

void loop()
{
  
  // Se o robô se aproximar de algo ou alguém
  // Calcular a distância em centímetros
  int distancia = 0.01723 * digitalRead(sensor);

  
  // Se o robô se aproximar de algo ou alguém a menos de 100cm
  if(distancia<100){ 
  	
    // Ligar o LED vermelho
    digitalWrite(ledvermelho,HIGH);
    // Servo rotacionando a 90°
 	objetoservo.write(90);
 	delay(500);
  
    if(distancia>100){ 
  }else{
      //Desligar o LED vermelho
    digitalWrite(ledvermelho,LOW);
  }
  
}


// Sensor
long sensor(int trigger, int echo){ 
  // trigger porta de saida
  pinMode(trigger,OUTPUT);
  digitalWrite(trigger,LOW);//desligar porta
  delay(5);// Esperar 5 milisegundos
  //mandando o sinal
  digitalWrite(trigger,HIGH);
  delay(10);// espere 10 milisegundos
  digitalWrite(trigger,LOW);//desligar porta
  // echo porta de entrada
  pinMode(echo,INPUT);//Definir porta como entrada
  //retorna os dados que a porta recebe
  return pulseIn(echo,HIGH);
}

}
