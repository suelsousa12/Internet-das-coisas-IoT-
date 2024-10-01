# Temperatura de ambiente

## Introdução


## Materiais utilizados
- 1 Arduino uno
- 1 Protoboard 400 pontos
- 1 Tela LCD 16 x 2
- 1 Resistor de 1K Ohm

## Explicação do código

// C++ code
// Biblioteca LCD com módulo
#include <LiquidCrystal_I2C.h>

// inicializar LCD
LiquidCrystal_I2C telalcd (0x20,16,2);

// Variável do sensor de temperatura
int sensorTMP = A0;

// capturar temperatura
int valorlido = 0;


void setup()
{
  // Definir o sensor como entrada
  pinMode(sensorTMP,INPUT);
  // Ligar a tela LCD
  telalcd.init();
  // Limpar os dados que aparecem
  telalcd.clear();
  // Aumentar a luminosidade do LCD
  telalcd.backlight();
}

void loop()
{
  // Capturar o valor da temperatura
  valorlido = analogRead(sensorTMP);
  // Converter o valor da tensão
  float tensao = (valorlido*5)/1024;
  // Converter a tensão em graus celsius
  float temperatura = (tensao-0.5)*100;
  
  // Imprimir valor da temperatura no LCD
  telalcd.setCursor(0,0);
  telalcd.print(temperatura);
  telalcd.print("abc");    
}



## Imagem de montagem do circuito
