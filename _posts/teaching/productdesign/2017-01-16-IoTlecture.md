---
categories: productdesign_lecture
layout: apd_default
title:  IoT Activities and Homework 1
published: true
---
# IoT Activities and Homework 1
by Max Yi Ren

## Activity 1: Introduction to ESP8266 Thing
Also read: [Hookup Guideline for ESP8266 Thing and Blynk][1]

### Item list
You will need the following during the class:

1. **The SparkFun ESP8266 Thing board**
2. **FTDI Basic -3.3V**
3. **SparkFun Cerberus USB Cable**
4. **Jumper Wires and a Breadboard**
5. **Arduino stackable header**
7. A Android/Apple **smart phone** and a **computer**. 

### Hardware setup
To test the basic functionality, we will use the following hookup.

<img src="/_images/tutorial_iot/hookup1.JPG" alt="Drawing" style="height: 400px;"/>
<img src="/_images/tutorial_iot/hookup2.JPG" alt="Drawing" style="height: 400px;"/>

### Software setup
The following setup should work for both Windows and Linux.

1. Download the [Arduino IDE][2] and install. It's free.
2. Open the Arduino IDE. Install ESP8266 Arduino Addon: 
  * Go to **File > Preference**, type
`http://arduino.esp8266.com/stable/package_esp8266com_index.json`
into the "Additional Board Manager URLs" text box. Hit OK.
  * Then go to **Tools > Boards > Boards Manager**, search "esp8266", and install it.
  * Go to **Tools > Boards**, select "ESP8266 Thing". If you don't see it, close and reopen the IDE.
3. On your smart phone, install "Blynk" and register. It's free.
4. Download the [Blynk library][blynklib]. Unzip it and move it to **%myDocuments%/Arduino/libraries**
(%myDocument% should be %your_user_name/documents% on Windows).

### A simple test
We can now test a simplest functionality: Using Blynk to switch on the LED at Digital 5 on the Thing. To do so,
create an Arduino sketch with the following code:

{% highlight C linenos %}
  #include <Wire.h>
  #include <ESP8266WiFi.h>
  #include <BlynkSimpleEsp8266.h>
  
  // You should get Auth Token in the Blynk App.
  // Go to the Project Settings (nut icon).
  char auth[] = "***"; // ***Type in your Blynk Token
  
  // Your WiFi credentials.
  // Set password to "" for open networks.
  char ssid[] = "***"; ***your wifi name
  char pass[] = "***"; ***and password
  
  void setup()
  {
    Blynk.begin(auth, ssid, pass);
  }
  
  void loop()
  {
    Blynk.run();
  }
{% endhighlight %}

Note that the campus wifi does not work for the Thing due to its security settings. 
You could, however, turn on hotspot on your phone and set up ssid and password from there. The Thing
 will then connect to your phone.

On Blynk, add a "Button" and link it to Digital 5.

<img src="/_images/tutorial_iot/blynkinterface.PNG" alt="Drawing" style="height: 400px;"/>
<img src="/_images/tutorial_iot/button.PNG" alt="Drawing" style="height: 400px;"/>


**Hint**: If you encounter the error: "warning: espcomm_sync failed...", there could be three reasons:

1. Check if the Thing is turned on! The switch is on one corner of the board. You should 
see a red light on once the board is turned on.
2. In the IDE, check **Tools>Port** to see which serial port you are using. 
Remember that both the Thing and the FTDI
are hooked up through USB, the one we should use is the USB Serial Port rather than Communications Port.
To find the right port, go to Device Manager (on Windows, it's under **Control Panel>System and 
Security>System**) and check "**Ports**". See figure below.
<img src="/_images/tutorial_iot/port.png" alt="Drawing" style="height: 400px;"/>
<img src="/_images/tutorial_iot/port2.png" alt="Drawing" style="height: 400px;"/>
<!--![Alt text](/_images/tutorial_iot/port.png)-->
<!--![Alt text](/_images/tutorial_iot/port2.png)-->

3. It could be that your soldering is not well done. 

In addition, sometimes this problem disappears when you re-upload, if your Port is chosen correctly.

## Validation
Before you move forward, I strongly recommend you to go through the cases 
from [the official guideline][1] to see
if your setup is all correct.

## Activity 2: Test one sensor

Pick one sensor from the [list][2]. Follow the hookup guide of that particular sensor and report your results.
Please also discuss potential applications of the sensor.

## Homework 1: Prepare an application report for the chosen sensor

The report should contain the following elements:

1. A narrative of the application

2. An introduction to the sensor

3. A schematic of the hookup

4. The Arduino code and related installation guide of necessary packages

5. The experiment and discussion

Notes:

* The report does not need to be long. But it should be informative so that others can reproduce your results by following
your instruction. 

* **Additional points** You get an additional 10 points (out of 100) if your report follows
the markdown format. See [the markdown version of this file][3] for example (click on the *raw* button). 
You may submit your images as a zip file if you do so. This allows me to easily
publish your report online for others to see.

* Submit your report to yiren@asu.edu with the exact title "MAE540 Homework 1 - Team number". If 
you are submitting a non-markdown file, please make sure it is in **pdf** format.

[1]: http://designinformaticslab.github.io/productdesign_tutorial/2016/11/19/sparkfunthing_tutorial.html
[2]: https://www.sparkfun.com/products/13754
[3]: https://github.com/DesignInformaticsLab/DesignInformaticsLab.github.io/tree/master/_posts/teaching/productdesign/2017-01-16-IoTlecture.md
[blynklib]: https://github.com/blynkkk/blynk-library