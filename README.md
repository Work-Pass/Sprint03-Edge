# Sprint03-Edge

----------------------------------------------------------------------------

Integrantes:

Filipe Prado Menezes / RM: 98765
Gabriel Gomes Catanzaro / RM: 93445
Pedro Henrique Salvitti / RM: 88166
Lucas Gomes Alcantara / RM: 98766

----------------------------------------------------------------------------

Código:
// Defina os pinos do sensor ultrassônico
const int triggerPin = 2;
const int echoPin = 3;

// Defina os pinos dos LEDs
const int redLedPin = 7;
const int greenLedPin = 8;

// Variáveis para armazenar as leituras do sensor
long duration;
int distance;

void setup() {
  pinMode(triggerPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(redLedPin, OUTPUT);
  pinMode(greenLedPin, OUTPUT);

  // Inicialmente, os LEDs estão apagados (verde para livre)
  digitalWrite(redLedPin, LOW);
  digitalWrite(greenLedPin, HIGH);
}

void loop() {
  // Gere um pulso no pino Trigger do sensor
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);

  // Meça o tempo de resposta no pino Echo
  duration = pulseIn(echoPin, HIGH);

  // Converta o tempo em distância (cm)
  distance = duration / 29 / 2;

  // Verifique a distância
  if (distance < 10) {
    // Se a distância for menor que 10 cm, o sensor detectou algo
    // Acenda o LED vermelho (indicando ocupado) e apague o LED verde
    digitalWrite(redLedPin, HIGH);
    digitalWrite(greenLedPin, LOW);
  } else {
    // Caso contrário, o sensor não detectou nada
    // Acenda o LED verde (indicando livre) e apague o LED vermelho
    digitalWrite(greenLedPin, HIGH);
    digitalWrite(redLedPin, LOW);
  }

  delay(1000); // Aguarde 1 segundo antes de fazer outra medição
}

----------------------------------------------------------------------------
