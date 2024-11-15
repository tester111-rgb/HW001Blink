# HW001Blink
My frist Esp32
การจะใช้ เซนเซอร์ dht ต้องมีการเรียกใช้ libary ของ เซนเเซอร์ ซึ่งเซนเซอร์ แต่ล่ะตัวจะมี libary สำหรับตัวเซนเซอร์
<Adafruit_Sensor.h> และ <DHT.h>
คำสั่งที่เรียกใช้ คือ #include <Adafruit_Sensor> #include <dht> 
ไม่ต้องพิมพ์ เอาชื่อ dht ไป ค้นหาที่ libary ซ่ึงจะขึ้นมาทั้ง 2 ตัว
ดูที่ platformIo.ini แล้วคลิก link แล้วจะแสดงการใช้คำสั่ง ตรงที่ installation


#include <Adafruit_Sensor.h>
#include <DHT.h>

#define DHTPIN 18     
#define DHTTYPE   DHT11     

DHT dht(DHTPIN, DHTTYPE);


void setup() {
  Serial.begin(9600);
  // Initialize device.
  dht.begin();
  Serial.println("DHTxx Unified Sensor Example");
   
 
}

void loop() {
  // Delay between measurements.
  delay(500);
  // Get temperature event and print its value.
  
  float h =dht.readHumidity();
  float t =dht.readTemperature();
  
  // Check if any reads failed and exit early (to try again).
  if (isnan(h) || isnan(t)) {
    Serial.println("Failed to read from DHT sensor!");
    return;
  }
  Serial.print("Humidity: ");
  Serial.print(h);
  Serial.print("%  Temperature: ");
  Serial.print(t);
  Serial.print(" C ");
  }

