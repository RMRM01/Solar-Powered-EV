int Left1 = 2;
int Left2 = 3;
int Right1 = 4;
int Right2 = 5;

int trigPin = 9;
int echoPin = 10;

char command;
long duration;
float distanceCm;

void setup() {
  pinMode(Left1, OUTPUT);
  pinMode(Left2, OUTPUT);
  pinMode(Right1, OUTPUT);
  pinMode(Right2, OUTPUT);

  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);

  Serial.begin(9600);
}

void loop() {
  distanceCm = getDistance();

  if (distanceCm < 5) {
    stopCar();
  } else {
    if (Serial.available()) {
      command = Serial.read();
      moveCar(command);
    }
  }

  delay(100);
}

float getDistance() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);
  return duration * 0.034 / 2;
}

void moveCar(char cmd) {
  if (cmd == 'F') {
    digitalWrite(Left1, HIGH);
    digitalWrite(Left2, LOW);
    digitalWrite(Right1, HIGH);
    digitalWrite(Right2, LOW);
  }
  else if (cmd == 'B') {
    digitalWrite(Left1, LOW);
    digitalWrite(Left2, HIGH);
    digitalWrite(Right1, LOW);
    digitalWrite(Right2, HIGH);
  }
  else if (cmd == 'L') {
    digitalWrite(Left1, LOW);
    digitalWrite(Left2, HIGH);
    digitalWrite(Right1, HIGH);
    digitalWrite(Right2, LOW);
  }
  else if (cmd == 'R') {
    digitalWrite(Left1, HIGH);
    digitalWrite(Left2, LOW);
    digitalWrite(Right1, LOW);
    digitalWrite(Right2, HIGH);
  }
  else {
    stopCar();
  }
}

void stopCar() {
  digitalWrite(Left1, LOW);
  digitalWrite(Left2, LOW);
  digitalWrite(Right1, LOW);
  digitalWrite(Right2, LOW);
}
