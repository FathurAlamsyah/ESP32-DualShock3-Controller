#include <Ps3Controller.h>

int battery = 0;

#define R1 33
#define R2 25
#define R3 26
#define R4 27

void notify(){
  if(Ps3.event.button_down.cross){
    Serial.println("X Tekan");
    maju();
  }
  if(Ps3.event.button_up.cross){
    Serial.println("X Lepas");
    henti();
    allOff();
  }
  
  if( Ps3.event.button_down.down ){
    Serial.println("DWN Tekan");
    mundur();
  }
  
  if( Ps3.event.button_up.down ){
    Serial.println("DWN Lepas");
    henti();
    allOff();
  }

  if( Ps3.event.button_down.left ){
    Serial.println("LFT Tekan");
    kiri();
  }
  if( Ps3.event.button_up.left ){
    Serial.println("LFT Lepas");
    henti();
    allOff();
  }

  if( Ps3.event.button_down.right){
    Serial.println("RGT Tekan");
    kanan();
  }
  if( Ps3.event.button_up.right){
    Serial.println("RGT Lepas");
    henti();
    allOff();
  }

  if(Ps3.event.button_down.l1){
      Serial.println("L1 Tekan");
//      liftUp();
  }
  if(Ps3.event.button_up.l1){
      Serial.println("L1 Lepas");
//      liftStop();
  }

  if(Ps3.event.button_down.l2){
      Serial.println("L2 Tekan");
//      liftDwn();
  }
  if(Ps3.event.button_up.l2){
      Serial.println("L2 Lepas");
//      liftStop();
  }

  if( battery != Ps3.data.status.battery ){
        battery = Ps3.data.status.battery;
        Serial.print("The controller battery is ");
        if( battery == ps3_status_battery_charging )      Serial.println("charging");
        else if( battery == ps3_status_battery_full )     Serial.println("FULL");
        else if( battery == ps3_status_battery_high )     Serial.println("HIGH");
        else if( battery == ps3_status_battery_low)       Serial.println("LOW");
        else if( battery == ps3_status_battery_dying )    Serial.println("DYING");
        else if( battery == ps3_status_battery_shutdown ) Serial.println("SHUTDOWN");
        else Serial.println("UNDEFINED");
    }
//    Serial.println("==============");
//    Serial.println();
}

void onConnect(){
    Serial.println("Terkoneksi");
}

void allOff(){
  digitalWrite(R1,LOW);
  digitalWrite(R2,LOW);
  digitalWrite(R3,LOW);
  digitalWrite(R4,LOW);
}

void setup() {
  Serial.begin(115200);

  pinMode(R1,OUTPUT);
  pinMode(R2,OUTPUT);
  pinMode(R3,OUTPUT);
  pinMode(R4,OUTPUT);

  while(!Ps3.isConnected()){ 
    Ps3.begin("50:63:13:15:30:70");
    Serial.println(".");
    delay(100);
  }
  
  Ps3.attach(notify);
  Ps3.attachOnConnect(onConnect);

  Serial.println("Ready");

}

void loop() {
  if(!Ps3.isConnected())
    return;

  delay(1000);
  
}

void henti(){
  Serial.println("==STOP==");
  digitalWrite(R1,0);
  digitalWrite(R2,0);
  digitalWrite(R3,0);
  digitalWrite(R4,0);
}

void maju(){
  Serial.println("==MAJU==");
  digitalWrite(R1,HIGH);
  digitalWrite(R2,LOW);
  digitalWrite(R3,HIGH);
  digitalWrite(R4,LOW);
}

void mundur(){
  Serial.println("==MUNDUR==");
  digitalWrite(R1,LOW);
  digitalWrite(R2,HIGH);
  digitalWrite(R3,LOW);
  digitalWrite(R4,HIGH);
}

void kanan(){
  Serial.println("==KANAN==");
  digitalWrite(R1,HIGH);
  digitalWrite(R2,LOW);
  digitalWrite(R3,LOW);
  digitalWrite(R4,HIGH);
}

void kiri(){
  Serial.println("==KIRI==");
  digitalWrite(R1,LOW);
  digitalWrite(R2,HIGH);
  digitalWrite(R3,HIGH);
  digitalWrite(R4,LOW);
}

//void liftStop(){
//  analogWrite(liftA,0);
//  analogWrite(liftB,0);
//}
//
//void liftUp(){
//  analogWrite(liftA,250);
//  analogWrite(liftB,0);
//}
//
//void liftDwn(){
//  analogWrite(liftA,0);
//  analogWrite(liftB,250);
//}
