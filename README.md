ArduTrx

Ham Radio Transceiver for Arduino with Dorji DRA818 module

![ArduTrx](http://blog.generationmake.de/images/12.jpg)

Schematic: http://blog.generationmake.de/file_download/1/dra-shield.pdf

![image](https://github.com/user-attachments/assets/7984e028-77fa-4030-85ad-b8c6864931a9)

![image](https://github.com/user-attachments/assets/6f5e371b-5574-401b-9ddb-fae8bc72d68b)

Description of circuit
**HF module (U1)**
A HF module from Dorji or NiceRF is used on the shield. 2 meter (144 MHz) or 70 centimeter (440 MHz) modules can be soldered.

**HF filter (L1..L3 and C1..C4)**
Unfortunatelly these HF modules produce spurious emissions. Therefore a HF filter is implemented on the shield. It is a chebyshev low pass filter and has a cutoff frequency of 185 MHz.

**voltage regulator LT1085 (U2)**
The HF modules allow a maximum voltage of 4.5 V (Dorji) or 5.5 V (NiceRF). Arduinos usually don't provide these voltages. But you only get the maximum HF power if you go to the voltage limits. Therefore ArduTrx uses a adjustable power regulator LT1085. The desired voltage can be set with the resistors R15 and R17. Additionally the modules draw up to 750 mA while transmit. This is too much for the voltage regulators on the Arduinos. The LT1085 on the ArduTrx shield can provide up to 3 A.

**audio driver LM4871 (U3)**
To make the audio output of the HF module hearable you need a speaker and an audio driver. ArduTrx shield uses a LM4871 which is optimal for battery powered circuits with low voltage and can drive high power with its differential output. The speaker can be connected to CN6. It is also possible the drive single ended loads like head phones on CN4.

**level shifter SN74LVC1T45 (U4, U5)**
ArduTrx can be used with 3.3V and 5V arduinos and these level shifters guarantee the right voltage level on the transmission lines.

**rotary encoder (SW1)**
The rotary encoder is only connected to the pins of the arduino and has no connection to the HF module. It can be used in Arduino programs to set the frequency of the HF module.

**programming switch (S1)**
The HF module needs a serial input from the arduino to change its configuration. Unfortunatelly this serial port of the Arduino is also used during programming of the Arduino and generates programming errors if it is also connected to HF module. So ArduTrx has a switch to open the serial connection to the HF module and allow programming (switch in off position). The switch has to be turned on if settings to the HF module have to be made.

**external power connector (CN7)**
This connector has the same function as the coaxial power connector on the Arduino board. It only uses an industrial connector and allows a safer connection. The input voltage can be measured with R35 and R36.

**antenna connector (CN1)**
The antenna connector is a SMA connector like it is used on many Hand-helds.

**hand mic connector (CN3 and CN4)**
CN3 and CN4 form a hand mic connector which is compatible to Kenwood or Baofeng.

https://www.dorji.com/docs/data/DRA818V.pdf

more information (in German): http://blog.generationmake.de/articles/8/arduino-shield-mit-dorji-dra818-transceiver-modul
