void setup() {
  pinMode(12, OUTPUT);
  pinMode(9, OUTPUT);

  pinMode(13, OUTPUT);
  pinMode(8, OUTPUT);

  pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
  
  delay(1000);
  
  digitalWrite(10, HIGH);
  digitalWrite(11, HIGH);
  delay(1000);
  digitalWrite(10, LOW);
  digitalWrite(11, LOW);
  delay(1000);
  digitalWrite(10, HIGH);
  digitalWrite(11, HIGH);
  delay(1000);
  digitalWrite(10, LOW);
  digitalWrite(11, LOW);
  delay(1000);
  digitalWrite(10, HIGH);
  digitalWrite(11, HIGH);
  delay(1000);
  digitalWrite(10, LOW);
  digitalWrite(11, LOW);
  delay(1000);
  digitalWrite(10, HIGH);
  digitalWrite(11, HIGH);
  delay(1000);
  digitalWrite(10, LOW);
  digitalWrite(11, LOW);
  delay(1000);
  digitalWrite(10, HIGH);
  digitalWrite(11, HIGH);
  delay(1000);
  digitalWrite(10, LOW);
  digitalWrite(11, LOW);
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
  
  lback();
  rforward();
  delay(3000);
  
  lforward();
  rback();
  delay(1000);
}

void lforward(){
  digitalWrite(12, HIGH);
  digitalWrite(9, LOW);
  analogWrite(3, 123);
  digitalWrite(10, HIGH);
}

void rforward(){
  digitalWrite(13, HIGH);
  digitalWrite(8, LOW);
  analogWrite(11, 123);
  digitalWrite(10, HIGH);
}

void lback(){
  digitalWrite(12, LOW);
  digitalWrite(9, LOW);
  analogWrite(3, 123);
  digitalWrite(11, HIGH);
}

void rback(){
  digitalWrite(13, LOW);
  digitalWrite(8, LOW);
  analogWrite(11, 123);
  digitalWrite(11, HIGH);
}

void lstop(){
  digitalWrite(9, LOW);
  digitalWrite(10, LOW);
  digitalWrite(11, LOW);
}

void rstop(){
  digitalWrite(8, LOW);
  digitalWrite(10, LOW);
  digitalWrite(11, LOW);
}
