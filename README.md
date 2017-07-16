# nCube-Rosemary
## Introduction
The nCube-Rosemary is defined middle server in oneM2M standard, and active as device gateway like local server. As a separate device it can storage resources also it can take remoteCSE as child resource. It plays the role of MN-CSE in the oneM2M standard. nCube-Rosemary is a kind of nCube but it can active like server because it contains CSE. So the nCube-Rosemary is same to Mobius on software level and they share the same type of oneM2M resource all most have same function. We can only use hardware environment to distinguish them.
## System stucture
<div align="center">
<img src="https://user-images.githubusercontent.com/29790334/28234222-3ef7135e-6938-11e7-9f0e-2d6d73a2047f.png" width="600"/>
</div>

## Installation
The nCube-Rosemary was developed with javascript of node.js and it also uses the MySQL to store data.
<div align="center">
<img src="https://user-images.githubusercontent.com/29790334/28209096-00fdcaa0-68cc-11e7-9d15-0a7dde6accb7.png" width="400"/>
</div><br/>

- [MySQL Server](https://www.mysql.com/downloads/)<br/>
The MySQL is an open source RDB database so that it is free and ligth. And RDB is very suitable for storing tree data just like oneM2M resource stucture. Most of nCube-Rosemary will work in a restricted hardware environment and the MySQL can work in most of embeded devices.

- [Node.js](https://nodejs.org/en/)<br/>
Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world. Node.js is very powerful in service impelementation because it provide a rich and free web service API. So, we use it to make RESTful API base on the oneM2M standard.

- [Mosquitto](https://mosquitto.org/)<br/>
Eclipse Mosquitto™ is an open source (EPL/EDL licensed) message broker that implements the MQTT protocol versions 3.1 and 3.1.1. MQTT provides a lightweight method of carrying out messaging using a publish/subscribe model. This makes it suitable for "Internet of Things" messaging such as with low power sensors or mobile devices such as phones, embedded computers or microcontrollers like the Arduino.

- [nCube-Rosemary](https://github.com/IoTKETI/nCube-Rosemary/archive/master.zip)<br/>
nCube-Rosemary is application base the node.js javascript. So we don't need to compile and install it before using.

## Configuration
- Import SQL script<br/>
When installation of MySQL Server finish. It also needs DB Schema for storing oneM2M resource in nCube-Rosemary. You can find this file in the nCube-Rosemary's source directory as below.
```
[nCube-Rosemary home]/mobius/mobiusdb.sql
```
- Run Mosquitto MQTT Broker<br/>
```
mosquitto -v
```
- Open the nCube-Rosemary source home directory.
- Install dependency libraries with command like below.
```
npm install
```
- Modify configuration file "conf_mn.json"
```
{
  "parent": {
    "cbname": "Mobius",             //CSEbase name
    "cbcseid": "/Mobius",           //CSEbase ID
    "cbhost": "203.253.128.161",    //CSEbase host IP
    "cbhostport": "7579",           //CSEbase http hosting port
    "cbprotocol": "http",           //CSEbase communication protocol
    "mqttbroker": "203.253.128.161" //MQTT Broker IP 
  },
  "csebaseport": "7599",            //MN-CSE HTTP hosting IP
  "dbpass": "dksklfdug2"            //Local MySQL root password
}
```
<div align="left">
<img src="https://user-images.githubusercontent.com/29790334/28210356-ea6875aa-68d1-11e7-9023-00747a2d8597.png" width="300"/>
</div><br/>

## Running
Use node.js application execution command to run the Rosemary
```
node rosemary.js
```

<div align="center">
<img src="https://user-images.githubusercontent.com/29790334/28234276-da780bc6-6938-11e7-8224-ae3676e843fa.png" width="700"/>
</div><br/>

## Dependency Libraries
These is dependency libraries for nCube-Rosemary 
- body-parser
- cbor
- coap
- crypto
- events
- express
- file-stream-rotator
- fs
- http
- https
- ip
- js2xmlparser
- merge
- morgan
- mqtt
- mysql
- shortid
- url
- util
- websocket
- xml2js
- xmlbuilder

## Document
If you want more detail please dowload the full [installation guide document](https://github.com/IoTKETI/nCube-Rosemary/raw/master/doc/Installation%20Guide_Rosemary_v2.0.0_KR.docx).

# Author
Il Yeup (iyahn@keti.re.kr; ryeubi@gmail.com)
