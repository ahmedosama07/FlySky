/**
 * FlySky for arduino Mega
*/

//Left Motors
int Lpwm1 = 2;
int Rpwm1 = 3;
int Lpwm2 = 4;
int Rpwm2 = 5;

//Right Motors
int Lpwm3 = 6;
int Rpwm3 = 7;
int Lpwm4 = 8;
int Rpwm4 = 9;

int rc_channel1 = 10;
int rc_channel4 = 11;
int switchD = 12;

void setup() {
  pinMode(Lpwm1,OUTPUT);
  pinMode(Rpwm1,OUTPUT);
  pinMode(Lpwm2,OUTPUT);
  pinMode(Rpwm2,OUTPUT);
  pinMode(Lpwm3,OUTPUT);
  pinMode(Rpwm3,OUTPUT);
  pinMode(Lpwm4,OUTPUT);
  pinMode(Rpwm4,OUTPUT);

  pinMode(rc_channel1, INPUT);
  pinMode(rc_channel4, INPUT);
  pinMode(switchD, INPUT);

  Serial.begin(9600);
}

void loop() {
  int pwm = 0;
  int swd = pulseIn(switchD, HIGH, 25000);
  int rc1 = pulseIn(rc_channel1, HIGH, 25000);
  int rc4 = pulseIn(rc_channel4, HIGH, 25000);
  
  Serial.print("switch: ");
  Serial.print(swd);
  Serial.print(" raw channel4: ");
  Serial.print(rc4);

  if(rc1 == 0 || rc4 == 0){
    Serial.println("No Signal yasta");
    Forward(0);
    Backward(0);
    Right(0);
    Left(0);
  }
  else{
    if(rc1 > 1530){
      pwm = map(rc1, 1530, 2000, 0, 255);
      Forward(pwm);
      Serial.print("Moving forward:     Speed = ");
      Serial.println(pwm);
    }
    else if(rc1 < 1460){
      pwm = map(rc1, 1460, 1000, 0, 255);
      Backward(pwm);
      Serial.print("Moving backward:     Speed = ");
      Serial.println(pwm);
  }
  else{
    if(rc4 > 1530){
      pwm = map(rc4, 1530, 2000, 0, 255);
      Right(pwm);
      Serial.print("Moving Left:     Speed = ");
      Serial.println(pwm);
    }
    else if(rc4 < 1460){
      pwm = map(rc4, 1460, 1000, 0, 255);
      Left(pwm);
      Serial.print("Moving Left:     Speed = ");
      Serial.println(pwm);
  }
  else{
    Serial.println("At rest");
    Forward(0);
    Backward(0);
    Right(0);
    Left(0);
  }
  }
  delay(10);
}

void Forward(int velocity){
  analogWrite(Lpwm1,0);
  analogWrite(Rpwm1,velocity);
  analogWrite(Lpwm2,0);
  analogWrite(Rpwm2,velocity);
  analogWrite(Lpwm3,0);
  analogWrite(Rpwm3,velocity);
  analogWrite(Lpwm4,0);
  analogWrite(Rpwm4,velocity);
}
void Backward(int velocity){
  analogWrite(Lpwm1,velocity);
  analogWrite(Rpwm1,0);
  analogWrite(Lpwm2,velocity);
  analogWrite(Rpwm2,0);
  analogWrite(Lpwm3,velocity);
  analogWrite(Rpwm3,0);
  analogWrite(Lpwm4,velocity);
  analogWrite(Rpwm4,0);
}
void Right(int velocity){
  analogWrite(Lpwm1,0);
  analogWrite(Rpwm1,velocity);
  analogWrite(Lpwm2,0);
  analogWrite(Rpwm2,velocity);
  analogWrite(Lpwm3,velocity);
  analogWrite(Rpwm3,0);
  analogWrite(Lpwm4,velocity);
  analogWrite(Rpwm4,0);
}
void Left(int velocity){
  analogWrite(Lpwm1,velocity);
  analogWrite(Rpwm1,0);
  analogWrite(Lpwm2,velocity);
  analogWrite(Rpwm2,0);
  analogWrite(Lpwm3,0);
  analogWrite(Rpwm3,velocity);
  analogWrite(Lpwm4,0);
  analogWrite(Rpwm4,velocity);
}
