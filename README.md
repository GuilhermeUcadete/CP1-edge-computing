# CP1-edge-computing  
Check Point 1 - Edge Computing |
 RM558418-Guilherme Ulacco | RM556517-Matheus Hostim | RM555372-Enzo Bonacasata | RM555351-Henrique Lomaski | RM558932-Luiz Guilherme | RM559097  Vinicius Augusto
 | 
CÓDIGO:

const int pinLDR = A0;  
const int pinLEDVerde = 10;  
const int pinLEDAmarelo = 9;  
const int pinLEDVermelho = 8;  
const int buzzerPin = 7; 

void setup() {
  pinMode(pinLEDVerde, OUTPUT);
  pinMode(pinLEDAmarelo, OUTPUT);
  pinMode(pinLEDVermelho, OUTPUT);
  pinMode(buzzerPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int valorLDR = analogRead(pinLDR); 
  Serial.print("Luminosidade: ");
  Serial.println(valorLDR);

  int limiarAlto = 800;  
  int limiarBaixo = 300;  

  if (valorLDR >= limiarAlto) {
    digitalWrite(pinLEDVerde, HIGH);
    digitalWrite(pinLEDAmarelo, LOW);
    digitalWrite(pinLEDVermelho, LOW);
    noTone(buzzerPin);
  } else if (valorLDR > limiarBaixo && valorLDR < limiarAlto) {
    digitalWrite(pinLEDVerde, LOW);
    digitalWrite(pinLEDAmarelo, HIGH);
    digitalWrite(pinLEDVermelho, LOW);
    tone(buzzerPin, 1000);
  } else {
    digitalWrite(pinLEDVerde, LOW);
    digitalWrite(pinLEDAmarelo, LOW);
    digitalWrite(pinLEDVermelho, HIGH);
    noTone(buzzerPin);
  }

  delay(1000);  
}
EXPLICAÇÃO:
O código é para um sistema que controla LEDs com base na luminosidade do ambiente. Ele usa um sensor de luminosidade (LDR) para medir a luz e decide qual LED ligar de acordo com a luminosidade medida.
No começo, o programa configura os pinos do Arduino para conectar o LDR, os LEDs e o buzzer. Depois, entra em um loop que faz o seguinte:
Lê o valor de luminosidade do LDR.
Compara esse valor com limiares predefinidos para determinar se a luz está alta, moderada ou baixa.
Com base nessa comparação, liga um LED específico e, se necessário, aciona o buzzer para indicar a condição de luminosidade.
Dessa forma, o sistema fornece feedback visual e sonoro sobre o ambiente, tornando mais fácil para o usuário entender os níveis de luz ao redor.

COMPONETNES:
Foi usado 3 leds, um verde, um amarelo, e um vermelho, e um fotorresistor interligado ao buzzer, que, dependendo da iluminosidade, ele ativa e emite um barulho para identificar uma temperatura a cima do esperado, nos 3 leds, tem 3 resistores, os 3 com uma resistencia de 311 ohms, e  1 resistor do fotoresistor, com 4734 ohms.

