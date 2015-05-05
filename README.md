void setup() {
  pinMode(12, OUTPUT);
  pinMode(9, OUTPUT);

  pinMode(13, OUTPUT);
  pinMode(8, OUTPUT);

  pinMode(10, OUTPUT);
  
  delay(1000);
  
  for(int ctr; ctr <= 10; ctr++){
    digitalWrite(10, HIGH);
    delay(500);
    digitalWrite(10, LOW);
    delay(1000);
  }
  
  digitalWrite(10, HIGH);
}

void lforward(){
  digitalWrite(12, HIGH);
  digitalWrite(9, LOW);
  analogWrite(3, 123);
}

void rforward(){
  digitalWrite(13, HIGH);
  digitalWrite(8, LOW);
  analogWrite(11, 123);
}

void lback(){
  digitalWrite(12, LOW);
  digitalWrite(9, LOW);
  analogWrite(3, 123);
}

void rback(){
  digitalWrite(13, LOW);
  digitalWrite(8, LOW);
  analogWrite(11, 123);
}

void lstop(){
  digitalWrite(9, LOW);
}

void rstop(){
  digitalWrite(8, LOW);
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
}
