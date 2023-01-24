
  # Freelance 1

  Note: Please ensure you have installed <code><a href="https://nodejs.org/en/download/">node js</a></code>

  To preview and run the project on your device:
  1) Open project folder in <a href="https://code.visualstudio.com/download">Visual Studio Code</a>
  2) In the terminal, run `npm install`
  3) Run `npm start` to view project in browser
  
#include <Ultrasonic.h>

const int triggerPin = D1;
const int echoPin = D2;
const int buzzerPin = D3;
const int ledPin = D4;
const int threshold = 5; // threshold distance in cm

Ultrasonic ultrasonic(triggerPin, echoPin);

void setup() {
  Serial.begin(9600);
  pinMode(buzzerPin, OUTPUT);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  long distance = ultrasonic.distanceRead();
  if (distance <= threshold) {
    digitalWrite(buzzerPin, HIGH);
    digitalWrite(ledPin, HIGH);
    Serial.print("Object detected within ");
    Serial.print(threshold);
    Serial.println("cm!");
  } else {
    digitalWrite(buzzerPin, LOW);
    digitalWrite(ledPin, LOW);
    Serial.print("Distance: ");
    Serial.print(distance);
    Serial.println("cm");
  }
  delay(100);
}
