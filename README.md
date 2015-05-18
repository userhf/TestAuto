void setup() {
  Serial.begin(9600);
  
  pinMode(12, OUTPUT);
  pinMode(9, OUTPUT);

  pinMode(13, OUTPUT);
  pinMode(8, OUTPUT);

  delay(5000);
  
  lforward();
  rforward();
}
int ctr = 0;
void loop(){
  int far = 0;
  far = howFar();
  
  if (far == 0){
    ctr++;
    Serial.println(ctr);
  }
  else{
    Serial.println(far);
  }
  
  if (far > 10){
    lforward();
    rforward();
  }
  
  if (far <= 10){
    lstop();
    rstop();
        
    delay(2000);
    
    lback();
    rforward();
}
}

void lback(){
  digitalWrite(12, HIGH);
  digitalWrite(9, LOW);
  analogWrite(3, 123);
}

void rback(){
  digitalWrite(13, HIGH);
  digitalWrite(8, LOW);
  analogWrite(11, 123);
}

void lforward(){
  digitalWrite(12, LOW);
  digitalWrite(9, LOW);
  analogWrite(3, 123);
}

void rforward(){
  digitalWrite(13, LOW);
  digitalWrite(8, LOW);
  analogWrite(11, 123);
}

void lstop(){
  digitalWrite(9, HIGH);
}

void rstop(){
  digitalWrite(8, HIGH);
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
