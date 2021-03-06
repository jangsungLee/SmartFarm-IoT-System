# SmartFarm-IoT-System-
  
# Build  
## Raspberry Pi  
initial step : qmake && sudo make  
after initial step : sudo make clean && sudo make  
  
## Windows  
windeployqt --release --qmldir --dir "실행파일이 있는 폴더경로"
  
# Note #
This Program is made when i have to make my graduation work.  
This can control BULB(Like : normal BULB(LED), Hot Bulb), Water Pump, Door Open/Close, PDLC ACTIVE/DISACTIVE remotely as well as on-site.  
When you want to control at on-site, you just have to input "*###*.  
then, you can show the control panel which can control the devices.  
Also, When you want to control via the Internet, you just have to access "http://iot.anudev.cf".  
The Internet site is only open for a short time. so, if you want to try this, you have to do that Modifying the IP part of JavaScript and c++ documents and building through qmake are required.  
(In the case of JavaScript, there is no need to build, and only c++ documents need to be built in qmake to create an executable file.)  
## Programs that must be executed ##
Reference Document : [Reference Document](https://github.com/jangsungLee/SmartFarm-IoT-System/raw/master/required_program/%EC%8B%A4%EC%8B%9C%EA%B0%84%20%EC%B9%B4%EB%A9%94%EB%9D%BC%20%EA%B4%80%EB%A0%A8%20%EC%84%A4%EC%A0%95%EB%B2%95.docx   "Programs")  
IIS : Need to be able to run classic asp on html page. [web page](https://github.com/jangsungLee/SmartFarm-IoT-System/tree/master/required_program/Web_Page  "Web Page Download link")  
RPI IP Teller(mediator) : [folder](https://github.com/jangsungLee/SmartFarm-IoT-System/tree/master/required_program/Mediator(RPI%20Position%20Teller)   "download folder")   
[RPI GUI Program(Main System and Web Application Server)](https://github.com/jangsungLee/SmartFarm-IoT-System/raw/master/QT_Project/doorLock_System   "download")  
Demo Video : https://blog.naver.com/hoan123432/222005532952  
Camera Streaming Server : "[OBS Studio](https://obsproject.com/ko/download  "OBS Studio link")" and "[ngnix](https://github.com/jangsungLee/SmartFarm-IoT-System/tree/master/required_program/nginx-rtmp  "ngnix link")" ("OBS Studio" --> "ngnix" --> Web Page)  
[HLS Recoder(C# Source Code - Visual Studio Project)](https://github.com/jangsungLee/SmartFarm-IoT-System/tree/master/required_program/Visual%20Studio%20Project/HLS_TO_MP4)   
![obs_studio setting capture](https://github.com/jangsungLee/SmartFarm-IoT-System/raw/master/QT_Project/obs_studio%20setting%20capture.PNG?raw=true)  
  
  
## RPI with hardware device(relay, motor driver) ###
### For BULB
   4(BCM - Name : BULB 1)        ===        		Relay_Switch_S_Pin  
  17(BCM - Name : BULB 2)        ===        		Relay_Switch_S_Pin  
  27(BCM - Name : BULB 3)        ===        		Relay_Switch_S_Pin  
  22(BCM - Name : BULB 4)                		    Relay_Switch_S_Pin  
  
### For HOT BULB  
   5(BCM - Name : HOT BULB 1)	   ===		        Relay_Switch_S_Pin   
   6(BCM - Name : HOT BULB 2)		 ===            Relay_Switch_S_Pin    
  13(BCM - Name : HOT BULB 3)		 ===            Relay_Switch_S_Pin    

### For PDLC
   19(BCM - NAME : PDLC)			   ===            Relay_Switch_S_Pin  

### For Door Open/Close (Motor)
   23(BCM - NAME : FORWARD/BACKWARD Singal)	      ===      MDD10A_DIR_PIN1, MDD10A_DIR_PIN2  
   24(BCM - NAME : PWM)				                    ===      MDD10A_PWM_PIN1, MDD10A_PWM_PIN2  
   25(BCM - NAME : SWITCH FOR OPEN  DETECTION)	  ===      SWITCH_ONE_OF_OUT_SIDE(LIMITED SWITCH)  
   12(BCM - NAME : SWITCH FOR CLOSE DETECTION)	  ===      SWITCH_ONE_OF_OUT_SIDE(LIMITED SWITCH)  
   ![Switch Connection](https://github.com/jangsungLee/SmartFarm-IoT-System/raw/master/QT_Project/door_sw_pin.jpg){: width="50%" height="50%"}  

### For Water Pump
   26(BCM - NAME : PWM)				                    ===     MD10C_PWM_PIN  
   18(BCM - NAME : FORWARD/BACKWARD Signal)	      ===     MD10C_DIR_PIN  
   
## For Sensor(Arduino)  
### Sketch(.ino)
[See Source Code](https://github.com/jangsungLee/SmartFarm-IoT-System/blob/master/Water_TEMPERATURE_HUMIDITY/Water_TEMPERATURE_HUMIDITY.ino)  
### Non Contact Water Sensor Connection
![Non Contact Water Sensor Connection](https://github.com/jangsungLee/SmartFarm-IoT-System/raw/master/QT_Project/FIT0212_Connection(Non-Contact%20Water-Level%20Sensor).png?raw=true)  
### SHT1x(Temperature and Humidity Sensor) Connection  
A2    ===   SDA  
A3    ===   SCL  
![SHT1x Connection](https://github.com/jangsungLee/SmartFarm-IoT-System/raw/master/QT_Project/SHT1X%20Connection.png?raw=true)  
### Brightness Sensor  
A4    ===   SDA  
A5    ===   SCL  

![DFRobot_VEML7700 Connection](https://github.com/jangsungLee/SmartFarm-IoT-System/raw/master/QT_Project/SEN0228_Arduino_Connection.png?raw=true)  



## special function key ##
"&#42;#0#&#42;" : raise window which can control system power(shutdown, reboot) and exit this program.  
"&#42;###&#42;" : raise window which can control hardware such ac relay switch, motor driver.  
"&#42;123&#42;"  : change password.  
"&#42;0000&#42;" : program exit.  
