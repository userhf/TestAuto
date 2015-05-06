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
  digitalWrite(7, HIGH);
  digitalWrite(6, HIGH);
  delay(1000);
  digitalWrite(7, LOW);
  digitalWrite(6, LOW);
  delay(1000);  
}

void loop(){
  lforward();
  rforward();
  delay(1000);
  
  lstop();
  rstop();
  delay(1000);
  
  lback();
  rback();
  delay(1000);
  
  lstop();
  rstop();
  delay(1000);
  
  lforward();
  rback();
  delay(1000);
  
  lstop();
  rstop();
  delay(1000);
  
  lback();
  rforward();
  delay(1000);
  
  lstop();
  rstop();
  delay(5000);
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
