# IOT-AIRQUALITY-MONITOR

**COMPANY:** CODTECH IT SOLUTIONS

**NAME:** I ROHITH KUMAR

**INTERN ID:** CT04DG1391

**DOMAIN:** INTERNET OF THINGS

**DURATION:** 4 WEEKS

**MENTOR:** NEELA SANTOSH

# DESCRIPTION
An IoT air quality monitor functions by integrating sensing, processing, and communication. Specialized sensors detect various airborne pollutants like particulate matter (PM2.5, PM10), carbon monoxide (CO), carbon dioxide (CO2), and volatile organic compounds (VOCs). A microcontroller, such as an Arduino or ESP32, reads the analog or digital output from these sensors, converting the raw data into meaningful values.

This processed data is then transmitted wirelessly, typically via Wi-Fi, Bluetooth, or cellular networks, to a cloud-based platform. The cloud acts as a central hub for storing, analyzing, and visualizing the collected air quality information. Users can access this data in real-time through dedicated smartphone applications or web dashboards, often presented with an Air Quality Index (AQI) or specific pollutant concentrations. Advanced systems may also incorporate machine learning for predictive analytics or trigger alerts (e.g., via email or SMS) when pollutant levels exceed predefined safe thresholds, enabling timely interventions and promoting healthier environments

**COMPONENTS:**
Arduino Uno: The microcontroller, serving as the "brain," processing sensor data and controlling outputs.

Breadboard: A prototyping board used for easily connecting components without soldering.

MQ Gas Sensor (likely MQ-2, MQ-7, or MQ-135): The primary sensor for detecting gas concentrations. Its analog output is connected to the Arduino.

16x2 LCD Display: Used to show real-time air quality readings and other information.

Buzzer: An audible alarm, triggered when gas levels exceed a set threshold.

Potentiometer: Likely used to adjust the contrast of the LCD display.

Resistors: Current-limiting resistors are used with the buzzer and potentially with the LCD to protect components.

Jumper Wires: For making all the electrical connections between the components.

**CODE:**

**#include <LiquidCrystal.h>**

**LiquidCrystal lcd(12, 11, 5, 4, 3, 2);**

**int pin8 = 8;**

**int analogPin = A0;**  

**int sensorValue = 0;**        

**void setup() {**

  **pinMode(analogPin, INPUT);**
  
  **pinMode(pin8, OUTPUT);**
  
  **lcd.begin(16, 2);**
  
  **lcd.print("What is the air ");**
  
  **lcd.print("quality today?");**
  
  **Serial.begin(9600);**
  
 **lcd.display();**
 
**}**

**void loop() {**
  
  **delay(100);**
  
  **sensorValue = analogRead(analogPin);**  
  
  **Serial.print("Air Quality in PPM = ");**
  
  **Serial.println(sensorValue);**           

  **lcd.clear();**
  
  **lcd.setCursor(0,0);**
  
  **lcd.print ("Air Quality: ");**
  
  **lcd.print (sensorValue);**
  
  **if (sensorValue<=500)**

  **{**
  
   **Serial.print("Fresh Air ");**
   
   **Serial.print ("\r\n");**
   
   **lcd.setCursor(0,1);**
   
   **lcd.print("Fresh Air");**
   
   **}**
   
  **else if( sensorValue>=500 && sensorValue<=650 )**
  
   **{**
   
   **Serial.print("Poor Air");**
   
   **Serial.print ("\r\n");**
   
   **lcd.setCursor(0,1);**
   
  **lcd.print("Poor Air");**
  
   **}**
   
  **else if (sensorValue>=650 )**
  
   **{**
   
   **Serial.print("Very Poor Air");**
   
   **Serial.print ("\r\n");**
   
   **lcd.setCursor(0,1);**
   
   **lcd.print("Very Poor Air");**
   
   **}**
  
 **if (sensorValue >650) {**
 
 **digitalWrite(pin8, HIGH);**
    
  **}**
  
 **else {**
 
  **digitalWrite(pin8, LOW);**
  
  **}**
  
**}**
 
**OVERVIEW OF CODE:**
The provided Arduino code establishes a fundamental air quality monitoring system by continuously reading data from an analog gas sensor. Upon initialization, it sets up an LCD display and serial communication, displaying a welcome message. In its primary loop, the program acquires raw analog readings from the sensor, interpreting these values as a proxy for "Air Quality in PPM." This real-time sensor data is then presented to the user on both a 16x2 LCD screen and the Serial Monitor. Crucially, the code categorizes the detected air quality into "Fresh Air," "Poor Air," or "Very Poor Air" based on predefined thresholds for the raw sensor values. Furthermore, to provide an immediate alert, if the air quality falls into the "Very Poor" category (sensor value exceeding 650), a digital output pin (pin 8) is activated, presumably triggering a connected buzzer or LED, thereby offering both visual and potential audible warnings to the user about deteriorating air condition

**CIRCUIT DESIGN:**

<img width="1777" height="754" alt="Image" src="https://github.com/user-attachments/assets/a50e5aed-8a11-4a8f-9442-f23eb5149718" />
