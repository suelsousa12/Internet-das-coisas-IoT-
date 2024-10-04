# Alarme com sensor PIR

# Introdução
  O projeto consiste em tocar um alarme através de um componente de sáida de sinal que emite frequência sonora, o buzzer piezo. 
  Ele emite esse alarme quando o sensor PIR detecta algo ou alguém próximo do sistema. 

## Materiais utilizados
- 1 Arduino uno
- 1 Protoboard 400 pontos
- 1 piezo
- Sensor PIR

## Explicação do código

int sensorPIR = 3;
int buzzer = 5;

void setup ()
{
  pinMode(sensorPIR,INPUT);
  pinMode(buzzer,OUTPUT);
}
void loop()
{
  int detectarPresenca = digitalRead(sensorPIR);
  if(detectarPresenca == 1){
    tone(buzzer,264);
  }else{
    noTone(buzzer);
  }
  
}

## Imagem de montagem do circuito

![Alarme com sensor PIR](alarme_com_sensor_pir.png)
