void setup() {
  pinMode(12, OUTPUT);
  pinMode(9, OUTPUT);

  pinMode(13, OUTPUT);
  pinMode(8, OUTPUT);

  pinMode(7, OUTPUT);
  pinMode(6, OUTPUT);
  
  delay(1000);
  digitalWrite(7, HIGH);
  digitalWrite(6, HIGH);
  delay(1000);
  digitalWrite(7, LOW);
  digitalWrite(6, LOW);
  delay(1000);
  digitalWrite(7, HIGH);
  digitalWrite(6, HIGH);
  delay(1000);
  digitalWrite(7, LOW);
  digitalWrite(6, LOW);
  delay(1000);  
}

void loop(){
  int ctr = 0;
  int far = 0;
  far = howFar();
  
  if (far < 30){
    if (ctr < 5){
      lforward();
      rback();
      delay(1000);
    }
    
    lstop();
    rstop();
    ctr++
  }
  
  else{
    lforward();
    rforward();
    delay(1000);
    
    lstop();
    rstop();
  }
}

void lforward(){
  digitalWrite(12, HIGH);
  digitalWrite(9, LOW);
  analogWrite(3, 123);
  digitalWrite(6, HIGH);
}

void rforward(){
  digitalWrite(13, HIGH);
  digitalWrite(8, LOW);
  analogWrite(11, 123);
  digitalWrite(6, HIGH);
}

void lback(){
  digitalWrite(12, LOW);
  digitalWrite(9, LOW);
  analogWrite(3, 123);
  digitalWrite(7, HIGH);
}

void rback(){
  digitalWrite(13, LOW);
  digitalWrite(8, LOW);
  analogWrite(11, 123);
  digitalWrite(7, HIGH);
}

void lstop(){
  digitalWrite(9, HIGH);
  digitalWrite(6, LOW);
  digitalWrite(7, LOW);
}

void rstop(){
  digitalWrite(8, HIGH);
  digitalWrite(6, LOW);
  digitalWrite(7, LOW);
}

int howFar(){
  int trigpin = 5;
  int echopin = 4;
  
  pinMode(trigpin, OUTPUT);
  pinMode(echopin, INPUT);
  
  int cm = 0;
  int duration = 0;
  
  digitalWrite(trigpin, LOW);
  delayMicroseconds(2);
  
  digitalWrite(trigpin, HIGH);
  delayMicroseconds(10);
  
  digitalWrite(trigpin, LOW);
  duration = pulseIn(echopin, HIGH);
  
  cm = duration / 58.2;
  
  return cm;
}
