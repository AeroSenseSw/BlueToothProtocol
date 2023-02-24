# BlueToothProtocol
Aerosense Wavve Bluetooth Communication Protocol

# Introduction
This version is a protocol for Bluetooth configuration and reading of internal parameters for Aerosense Wavve heart & respiratory monitoring product communication. Please note that part of the protocol content requires the firmware version of the module. If there is no reply to the query command, it means that the current internal version of the device does not support the protocol

# Protocol
**All the character formats in the agreement are all English characters.** The device replies with data in the format of a string.

| No.        | Function    |  Send command format  | Device Reply|
| --------   | -----:   | :----: | -------- |
| 1          | Set wifi parameters                          |   (wifi ssid,wifi password)    | 0x01 |
| 2          | Set TCP server information                   |   [server ip ,port num]        |0x01 |
| 3          | Query device ip address                      |   i,                           |10.8.4.123  |
| 4          | Query the device firmware version number     |   v,                           | 0.0.3.4 |
| 5          | Query device wifi MAC address                |   m,                           |  A0:76:4E:47:6A:4C|
| 6          | Set static IP                                |   s, static iP, gateway;subnet mask; First DNS; Second DNS  |0x01 |

# Example
Example of setting a wifi parameters: </br>
*wifi ssid: test*</br>
*wifi ssid: test123*</br>

Mobile data sending: 
```
(test, test123)
```
Mobile data receiving:  </br>
```
0x01
```



Example of setting a static ip: </br>

*Static ip      192.168.10.24*</br>
*Gateway     192.168.10.33*</br>
*Subnet mask  255.255.255.0*</br>
*First DNS     8.8.8.8*</br>
*Second DNS   8.8.4.4*</br>

Mobile phone data sending: 
```
s,192.168.10.24;192.168.10.33;255.255.255.0;8.8.8.8;8.8.4.4
```
Mobile phone data receiving: 
```
0x01
```

***After the configuration is complete, the mobile phone disconnects the Bluetooth connection, and the Aerosense Wavve will automatically connect to WiFi and access the server***
