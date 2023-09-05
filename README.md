// humidity_and_temp
//checking humidity and temperature using DHT 11 in Arduino uno board  
#include <DHT.h>

#define DHTPIN 10       // Pin connected to the DHT22 sensor
#define DHTTYPE DHT22   // Type of DHT sensor (DHT22)

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  
  Serial.begin(9600);
  dht.begin();
}

void loop() {
  delay(2000); // Wait for 2 seconds between readings

  float temperature = dht.readTemperature(); // Read temperature in Celsius
  float humidity = dht.readHumidity();       // Read humidity
   if (isnan(temperature) || isnan(humidity)) {
    Serial.println("Failed to read from DHT sensor!");
    return;
  }

  Serial.print("Temperature: ");
  Serial.print(temperature);
  Serial.print(" °C\t");
    

  Serial.print("Humidity: ");
  Serial.print(humidity);
  Serial.println("%");

  delay(2000); // Wait for 2 seconds before next reading
}
