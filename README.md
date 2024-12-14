# NIVEL-DE-AGUA-CON-LCD

## CODIGO

```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1 = 2;
const int led2 = 5;
const int led3 = 16;
const int led4 = 17;

#include <LiquidCrystal_I2C.h> //Libreria de LCD
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

// defines variables
long duration;
int distance;
int safetyDistance;
LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
lcd.init();
lcd.backlight();
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=2 && safetyDistance<=10)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
lcd.clear();  
lcd.setCursor(0, 4);
lcd.print("TANQUE 90% ");
delay(2000);
}
else if(safetyDistance>=11 && safetyDistance<=20) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
  lcd.clear(); 
  lcd.setCursor(0, 4);
  lcd.print("TANQUE 75% ");
  delay(2000);
}
else if(safetyDistance>=21 && safetyDistance<=30) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
  lcd.clear(); 
  lcd.setCursor(0, 4);
  lcd.print("TANQUE 50% ");
  delay(2000);
}
else if(safetyDistance>=31 && safetyDistance<=40) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
  lcd.clear(); 
  lcd.setCursor(0, 4);
  lcd.print("TANQUE 25% ");
  delay(2000);
}
else
{
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
  lcd.clear(); 
  lcd.setCursor(0, 4);
  lcd.print("TANQUE 0% ");
  delay(2000);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}
```

## LIBRERIA

1. LiquidCrystal I2C

## CONEXIÓN

![](https://github.com/RaulCasS/NIVEL-DE-AGUA-CON-LCD/blob/main/Captura%20de%20pantalla%202024-12-13%20232619.png?raw=true)

## RESULTADOS

![](https://github.com/RaulCasS/NIVEL-DE-AGUA-CON-LCD/blob/main/Captura%20de%20pantalla%202024-12-13%20232929.png?raw=true)
![](https://github.com/RaulCasS/NIVEL-DE-AGUA-CON-LCD/blob/main/Captura%20de%20pantalla%202024-12-13%20233042.png?raw=true)
![](https://github.com/RaulCasS/NIVEL-DE-AGUA-CON-LCD/blob/main/Captura%20de%20pantalla%202024-12-13%20233226.png?raw=true)
![](https://github.com/RaulCasS/NIVEL-DE-AGUA-CON-LCD/blob/main/Captura%20de%20pantalla%202024-12-13%20233457.png?raw=true)

### CRÉDITOS

Desarrollador por el Ing. Raúl Castañeda Sotelo

https://github.com/RaulCasS (GitHub)

