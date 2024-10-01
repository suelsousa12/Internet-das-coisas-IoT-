# LED de semaforo

## Introdução

## Materiais utilizados

## Explicação do código

// C++ code

// Variáveis dos LEDs
int ledVermelho = 4;
int ledAmarelo = 3;
int ledVerde = 2;

void setup() 
{ // Definir LEDs como saída
  pinMode(ledVermelho,OUTPUT);
  pinMode(ledAmarelo,OUTPUT);
  pinMode(ledVerde,OUTPUT);
}

void loop()
{
  //// Ligar o LED verde
  digitalWrite(ledVermelho,LOW);// Desligar vermelho
  digitalWrite(ledAmarelo,LOW);// Desligar amarelo
  digitalWrite(ledVerde,HIGH);// Ligar verde
  delay(2000); // Espere 2 segundos 
  
  // Ligar o LED vermelho
  digitalWrite(ledVermelho,HIGH);// Ligar vermelho
  digitalWrite(ledAmarelo,LOW);// Desligar amarelo
  digitalWrite(ledVerde,LOW);// Desligar verde
  delay(2000); // Espere 2 segundos 
  
   // Ligar o LED amarelo
  digitalWrite(ledVermelho,LOW);// Desligar vermelho
  digitalWrite(ledAmarelo,HIGH);// Ligar amarelo
  digitalWrite(ledVerde,LOW);// Desligar verde
  delay(1000); // Espere 1 segundo
}

## Imagem de montagem do circuito
