# Semáforo inteligente

# Introdução
  Este projeto tem a função de automatizar os semáforos de duas vias de sentidos opostos e facilitar a travessia de pedestres nas faixas das vias em horários de pico ou não. O projeto consiste em:
  
  - 2 semáforos com LEDs vermelho, amarelo e verde para as vias dos carros.
  - 2 semáforos com LEDs vermelho e verde, com sensosr de distância/proximidade (50cm) para os pedestres atravessarem na faixa da via.

  Os sinais das vias dos carros permanecem sempre com LED verde ligado, assim que um pedestre se aproxima da faixa de pedestre, o sensor do semáforo da faixa vai detectar a presença. Fazendo com que os sinais dos carros acionem o LED vermelho e os carros parem.Os pedestres tem 15 segundos para atravessar a faixa. Logo após esse tempo, se o sensor não detectar mais nada, o sinal da faixa acende o LED vermelho, enquanto o sinal da via acende o LED verde.


# Materiais utilizados
  - 1 arduino uno
  - 4 LEDs vermelhos
  - 2 LEDs amarelos
  - 4 LEDs verdes
  - 1 sensor de distância
  - 10 resistores de 1K Ohm
  - 

# Explicação do código


# Imagem de montagem do circuito

