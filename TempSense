#include <LiquidCrystal_I2C.h>
#include <OneWire.h>
#include <DallasTemperature.h>

#define SENSOR_PIN1 2  // The Arduino Nano pin connected to DS18B20 sensor's D2 pin
#define SENSOR_PIN2 3  // The Arduino Nano pin connected to DS18B20 sensor's D3 pin
#define SENSOR_PIN3 4  // The Arduino Nano pin connected to DS18B20 sensor's D4 pin
LiquidCrystal_I2C lcd(0x27, 16, 2); // I2C address 0x27, 16 column and 2 rows
OneWire oneWire1(SENSOR_PIN1);         // setup a oneWire instance for sensor A
OneWire oneWire2(SENSOR_PIN2);         // setup a oneWire instance for sensor B
OneWire oneWire3(SENSOR_PIN3);         // setup a oneWire instance for sensor C
DallasTemperature DS18B20_A(&oneWire1); // pass oneWire1 to DallasTemperature library
DallasTemperature DS18B20_B(&oneWire2); // pass oneWire2 to DallasTemperature library
DallasTemperature DS18B20_C(&oneWire3); // pass oneWire3 to DallasTemperature library

float temperature_C1;    // temperature in Celsius for sensor 1
float temperature_C2;    // temperature in Celsius for sensor 2
float temperature_C3;    // temperature in Celsius for sensor 3

void setup() {
  lcd.init(); // Initialize the LCD I2C display
  lcd.backlight(); // Just turns on the screens backlight


  lcd.setCursor(3, 0);          // move cursor to   (3, 0)
  lcd.print("TempSense");        // print message at (3, 0)
  delay(400);
  Serial.begin(9600); // Initialize the Serial to communicate with the Serial Monitor.
  DS18B20_A.begin();    // initialize sensor A
  DS18B20_B.begin();    // initialize sensor B
  DS18B20_C.begin();    // initialize sensor C


}

void loop() {
  DS18B20_A.requestTemperatures();             // send the command to get temperatures from sensor A
  temperature_C1 = DS18B20_A.getTempCByIndex(0);  // read temperature in Celsius 

  DS18B20_B.requestTemperatures();             // send the command to get temperatures from sensor B
  temperature_C2 = DS18B20_B.getTempCByIndex(0);  // read temperature in Celsius 

  DS18B20_C.requestTemperatures();             // send the command to get temperatures from sensor C
  temperature_C3 = DS18B20_C.getTempCByIndex(0);  // read temperature in Celsius 


  lcd.setCursor(0, 0); // sets the lcd cursor to that position

  lcd.print("Temp: "); // prints the word temp(temperature) on the lcd

  lcd.print((temperature_C1 + temperature_C2 + temperature_C3)/3);// prints on the lcd the average value given by the three sensors

  lcd.print("C");// prints 'C' to show that it's in celcious
  delay(3000);

  lcd.clear();
}
