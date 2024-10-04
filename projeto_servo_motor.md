# Alarme com sensor PIR

# Introdução
  O projeto consiste em ter um servo motor que movimenta uma hélice de 5 em 5 graus. Esse movimneto é a partir de um comando dado quando um botão é acionado pelo usuário do sistema. O usuário tem a opção de fazer com que a hélice se movimente em sentido horário e anti-horário. 

## Materiais utilizados
- 1 Arduino uno
- 1 Protoboard 400 pontos
- 1 Servo motor de 180°
- 2 Botões
- 2 Resistores de 220 ohms

## Explicação do código

// Biblioteca do servo motor
#include <Servo.h>


/* Criando objeto do tipo servo motor para
usar as funções de controle do equipamento
(servo motor)*/
Servo objetoservo;


// Variável para salvar a porta que o servo está
int servo = 2;
// Variável para a porta do botão
int botao1 = 4;
// Variável para a porta do botão
int botao2 = 7;
// Variável para posição do motor
int posicao = 0;


void setup()
{
  // A inicializando do servo na portadigital 2
  objetoservo.attach(servo);
  // Servo começa na posição 0
  objetoservo.write(0);
  // Definir botão como entrada
  pinMode(botao1,INPUT); 
  // Definir botão como entrada
  pinMode(botao2,INPUT); 
}

void loop()
{
 /* Se o botão for pressionado e a posição do servo motor
 estiver menor que 180° */
  if(digitalRead(botao1) == HIGH && posicao < 180){
    // Aumenta 5° de posição
    posicao=posicao+5;
    // Ordena o motor para nova posição
    objetoservo.write(posicao);
    delay(500);
  	}
  if(digitalRead(botao2) == HIGH && posicao < 180){
    // Diminui 5° de posição
   posicao=posicao-5;
    // Ordena o motor para nova posição
    objetoservo.write(posicao);
    delay(500);
  	}
}

## Imagem de montagem do circuito

![Projeto servo motor](projeto_servo_motor.png)
