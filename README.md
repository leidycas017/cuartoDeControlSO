# Step-by-Step Guide to Programming and Developing a Control Circuit with the ESP32-WROOM-32

### Introduction
In this document, we propose to provide the reader with a step-by-step guide on how to design an application that simulates the operation of an industrial control room from where the equipment applied to a certain process is managed, which in this case is the operation of an electric oven, used in the casting of metals such as ferronickel, copper, aluminum, and others.

### Importance of this work
The automation and control of industrial processes are essential to improve efficiency, safety, and precision in manufacturing. This project not only serves as a practical introduction to programming and developing control systems with the ESP32-WROOM-32, but also provides a solid foundation for real-world applications in industry.

### Goal of the guide.
Guide engineering students and electronics and microcontroller enthusiasts in implementing a system that simulates the operation of an industrial control room. Although it is a relatively simple system, this project offers a gateway to the fascinating world of electronics.

We are greatly encouraged by the possibility that this document will serve as a clear and accessible guide for others to get the application up and running. We have avoided the use of terms and expressions that may confuse, to facilitate better use of this work.

### ESP32-WROOM-32 Overview
The ESP32 is a powerful and versatile microcontroller developed by Espressif Systems. It incorporates Wi-Fi and Bluetooth capabilities, making it ideal for Internet of Things (IoT) applications. Its dual-core architecture, together with its high processing speed and multiple integrated peripherals, allows it to handle complex tasks and various sensors and actuators. Additionally, it is compatible with a wide range of development environments, such as Arduino IDE and PlatformIO, making it easy to program and use in both hobbyist and professional projects. The ESP32 is known for its low power consumption and affordable cost, making it a popular choice for innovative developments in areas such as home automation, industrial automation, and wearable devices.

### Common control circuit applications

- Home automation: Control of lighting, security, heating, and appliances.
- Industrial automation: Monitoring and control of machinery and manufacturing processes.
- Internet of Things (IoT) projects: Environmental sensors, wearable devices, energy monitoring, and smart irrigation systems.
- Vehicles and transportation: Entertainment, navigation, and vehicle condition monitoring systems.
- Renewable energy: Management and monitoring of solar panels and energy storage systems.
- Medical and health devices: Monitoring vital signs and managing medical devices at home.
- Agriculture and environmental management: Monitoring of soil conditions and control of ventilation and irrigation systems.
- Home automation: Automation of household tasks and centralized management of smart devices.
- Security systems: Surveillance cameras, alarms, and motion sensors.
- Education and prototypes: educational projects, prototype development, and experimentation in electronics and programming.

### Materials and tools needed

In the implementation of this work, the following materials were required:
- 8 resistors of 560 ohms
- 8 LEDs (light emitters)
- ESP32-WROOM-32 microcontroller
- Wiring connections
- Breadboard
- Personal computer
- Cell pones
- WIFI network.

### Breadboard
It is ideal to have a voltage meter, and or an oscilloscope, however, for the implementation of this work we did not have these instruments and it was not necessary (a basic knowledge of electricity and electronics concepts is required).

### Programming tools
The code can be developed in C, C++, MicroPython language. It should be noted that we use Arduino's language, which is very similar to the syntax of the C language.

### Development environment
We install the Arduino IDE, which is a free software with a large community of code developers and instruments compatible with Arduino and ESP32 products. The IDE can be downloaded from the official Arduino website: https://www.arduino.cc/en/software.

### Additional equipment
As said in previous paragraphs, it is ideal to have measuring instruments, however, given the simplicity of the work, it was not required.

### Development environment configuration.

1. Install the Arduino IDE.
2. Select File > Preferences, and add the following URLs:
http://arduino.esp8266.com/stable/package_esp8266com_index.json,https://dl.espressif.com/dl/package_esp32_index.json,https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json

![SO1](https://github.com/leidycas017/cuartoDeControlSO/assets/58440602/9343520a-c405-4fbf-9161-d25742f55d0d)

### Installation of Libraries

In the development of this program, the <wifi.h> library is essential, which is already included in the library system that the Arduino IDE comes with by default.

### Electrical design
Since the ESP32 card is a circuit with low power consumption, according to the manufacturer's tables, each pin of the ESP32 can be drained of a current of up to 16 milliamps (This may vary depending on the version). The following resistance calculation was carried out:
R=(3.3-1)volt/(8 ma)=287ohmios 
A resistor with a standard value of 330 ohms was selected.

### Connection diagram of an LED to an ESP32 pin
![SO2](https://github.com/leidycas017/cuartoDeControlSO/assets/58440602/812e43c1-c1f6-4420-b017-2720b0768cab)

The diagram shown is just an example of how to connect an LED to an output pin. Note that in the diagram the LED is referenced to a GND pin (black wire).

### ESP32 pin diagram
![SO3](https://github.com/leidycas017/cuartoDeControlSO/assets/58440602/b3e75490-fe6c-4b9e-abbf-0222821e899f)
In this project, the following pins programmed in output mode were used:
{13, 12, 14, 27, 26, 25, 33, 32}

### General assembly circuit
An LED with a series resistance of 330 ohms and referenced for the GND pin (pin 14) was connected to each output pin.

![SO4](https://github.com/leidycas017/cuartoDeControlSO/assets/58440602/76d84603-d02e-44bc-a77c-9c23f43b507b)

### Basic structure of the code

•	Installation of Library <wifi.h>
•	Definition of pin arrangement.
•	Creation of WifiServer instance.
•	Pin configuration in output mode in the setup routine.
•	Connection to the WIFI network
•	Server startup
•	Loop execution for the cyclic execution of the handleCustomer() routine.
•	HandleCustomer() routine, used to detect requests from system users.
•	EnergizeMachine() routine, responsible for starting a machine.
•	ShutdownMaquina() routine, responsible for shutting down a machine.
•	Routine to display web page.
•	Routine to update equipment status.

Attached to this repository is the *.ino file that contains the application code.

### Start-up of the control system
After wiring the device, it is necessary to compile the program and load the source code into the device's memory.

![SO5](https://github.com/leidycas017/cuartoDeControlSO/assets/58440602/835fffc6-0186-4f4d-9aef-29b7ed71aae9)

Open the Arduino IDE

###	WIFI local network

For connection to the local network in the program code, there are two lines related to network credentials.
The network credentials are recorded in the ESP32's memory before you record your program must update the values to the values of your network.

```
const char* ssid = "InvitadoUdeA"; // This value must be changed
const char* password = ""; // This value must be changed
```

On the toolbar you see two circle-shaped buttons.

![SO6](https://github.com/leidycas017/cuartoDeControlSO/assets/58440602/4f824b6b-404c-4dc7-8741-e2b8f2dce55e)

With the leftmost button, you verify the code, with the center button you compile and download the program to the ESP32.

### IDE configuration and selection of the communication port
You must select the microcontroller you want to program in the IDE. Open the IDE and select the desired board from the Tool option.

![SO7](https://github.com/leidycas017/cuartoDeControlSO/assets/58440602/a047f40b-f461-4c88-baf0-b3e0b3f28a85)

Just as shown in the image.

### Selecting the connection port of your computer

You must connect the ESP32 board to the USB port that you have available.

![S7](https://github.com/leidycas017/cuartoDeControlSO/assets/58440602/2a9f7ea1-1845-47af-ada0-9183bc7df5e4)

### Choose a port number in the Arduino IDE as shown in the graph, which in our case was port 6

![S8](https://github.com/leidycas017/cuartoDeControlSO/assets/58440602/425daa2c-26ea-44a6-8322-156f5f9b9c0f)

### Download the program to the ESP32
Having the board connected to the ESP32, press the (Upload) button on the central toolbar.

Once this is done, the program compilation operation begins. 

![S9](https://github.com/leidycas017/cuartoDeControlSO/assets/58440602/17d6947e-e858-4b15-9d01-bbdc8824577f)

At this point, you have to be careful, when the first line of information of the compilation process appears, right at that moment you have to press the BOOT or FLASH button, (The recording enable button is a security system of the ESP32 board -WROOM-32) for a moment, from the moment the button is pressed and released, the engraving of the binary code on the plate begins.

*Note:  If you take too long to press the button as soon as the first compilation message appears, an error message will be generated in the recording process, and you will have to start the download process again.*

*The BOOT button is specific to the ESP32-WROOM-32 board; it prevents an intruder from recording malicious code.
The BOOT button is located on the left side of the board next to the USB connection cable.*

### As shown in the figure
![S10](https://github.com/leidycas017/cuartoDeControlSO/assets/58440602/d71f5fb8-513e-4251-bede-c4e27e6f14a1)

### Final recommendations
- You can redesign the HTML code to change the appearance of the graphical interface.
- You can add new machines and or remove them.
- As you can see in the connection diagram, the load (LED + resistor) is connected directly to the microcontroller pin. A better way to do this is to install an isolation device such as the 74HC244 chip. If you prefer, you can use optocouplers such as the PC817 chip. Any of these devices is compatible with the ESP32, the benefit obtained is to establish an insulation layer that protects the chip in case of electrical failures in the load to which the microcontroller is subjected.

### References
[1]	Carrasco, D. (2021, abril 25). WLAN en ESP32: Primeros pasos con el Wifi. ElectroSoftCloud. https://www.electrosoftcloud.com/wlan-en-esp32-primeros-pasos-con-el-wifi/
[2]	Barry, R., & The FreeRTOS Team. (n.d.). Mastering the FreeRTOS™ Real Time Kernel: A Hands-On Tutorial Guide. FreeRTOS. https://freertos.org/Documentation/Mastering-the-FreeRTOS-Real-Time-Kernel.v1.0.pdf
[3]	Pinillos, J. M. (2020, mayo 7). Básicos ESP32: Mapeo de pines y sensores internos. Tecnotízate. https://tecnotizate.es/esp32-mapeo-de-pines-y-sensores-internos/
[4]	Punto Flotante S.A. (2022). Manual básico NodeMCU ESP32 DevKit V1 Arduino IDE. https://www.puntoflotante.net/MANUAL-BASICO-NODEMCU-ESP32-ARDUINO.pdf
[5]	Espressif Systems. (n.d.). ESP-WROOM-32 Datasheet. Retrieved from https://www.alldatasheet.com/view.jsp?Searchword=Esp-wroom-32%20datasheet&gad_source=1&gclid=CjwKCAiAopuvBhBCEiwAm8jaMUrA9d3ZAeRBJZGn3q_aJnhFT3ny3V6c93gDRD1OtHYEOarCMxLaWRoCNPYQAvD_BwE
[6]	Electronics. (2021, julio). Especificaciones del módulo ESP32. Vasanza. https://vasanza.blogspot.com/2021/07/especificaciones-del-modulo-esp32.html
[7]	Espressif Systems. (s.f.). ESP32. https://www.espressif.com/en/products/socs/esp32
