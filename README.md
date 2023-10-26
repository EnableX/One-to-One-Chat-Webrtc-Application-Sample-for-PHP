# 1-to-1 RTC Chat Application: PHP & EnableX Web Toolkit Example

1-to-1 RTC Web Chat App: PHP & EnableX Web Toolkit 

Explore a Sample PHP Chat App showcasing the usage of EnableX platform APIs for seamless 1-to-1 RTC (Real-Time Communication) Applications. Develop your skills by hosting this app on your own devices, reducing the need for external servers. 

RTC Applications on the EnableX platform operate seamlessly on supported web browsers, eliminating the need for additional plugin downloads. 

This basic 1-to-1 Chat Application is crafted using HTML, CSS, Bootstrap, JavaScript, jQuery, PHP, and EnxRtc (EnableX Web Toolkit) 

>The details of the supported set of web browsers can be found here:
https://developer.enablex.io/video/browser-compatibility-of-enablex-video/


## 1. Important!

When developing a Client Application with EnxRtc.js make sure to include the updated EnxRtc.js polyfills from https://developer.enablex.io/video-api/client-api/web-toolkit/ for RTCPeerConnection and getUserMedia. Otherwise your application will not work in web browsers.


## 2. Trial

Sign up for a free trial https://portal.enablex.io/cpaas/trial-sign-up/ or try our multiparty video chat https://try.enablex.io/


## 3. Installation

### 3.1 Pre-Requisites

#### 3.1.1 App Id and App Key 

* Register with EnableX [https://portal.enablex.io/cpaas/trial-sign-up/] 
* Create your Application
* Get your App ID and App Key
* Clone this repository `git clone https://github.com/EnableX/One-to-One-Chat-Webrtc-Application-Sample-for-PHP.git --recursive` & follow the steps further 
* You can copy the app into any sub-directory of hosted Website on Apache

#### 3.1.2 SSL Certificates

The Application needs to run on https. So, you need to use a valid SSL Certificate for your Domain and point your application to use them. 

However you may use self-signed Certificate to run this application locally. There are many Web Sites to get a Self-Signed Certificate generated for you, Google it. Few among them are:

* https://letsencrypt.org/
* https://www.sslchecker.com/csr/self_signed
* https://www.akadia.com/services/ssh_test_certificate.html

Alternatively you can create your self-signed certificate as below
```javascript
  sudo openssl req -x509 -newkey rsa:4096 -keyout server.key -out server.crt -days 10000 -nodes
  sudo mv server.crt /etc/ssl/certs/ssl.crt
  sudo mv server.key /etc/ssl/private/ssl.key
```
Enable mod ssl and turn on ssl server
```javascript
  sudo a2enmod ssl
  sudo a2ensite default-ssl
  sudo service apache2 restart
```

#### 3.1.3 Configure

* Before you can run this application, configure the service by editing `api/config.php` file to use your app ID and app key

```javascript
  define("API_URL",	"https://api.enablex.io/v1");
  define("APP_ID",	"YOUR_APP_ID");
  define("APP_KEY",	"YOUR_APP_KEY");
```

### 3.2 Test 

* Open a browser and go to [https://yourdomain.com:4443/path-to-sample-app/client/](https://yourdomain.com:4443/path-to-sample-app/client/). The browser should load the App. 
* You need to Room ID to join. We have added a "Create Room" link below the login form. Click it to get a Room-Id prefilled in the form. 
* You can share the Room-ID with anyone to join your Conference.


## 4. Server API

EnableX Server API is a Rest API service meant to be called from Partners' Application Server to provision video enabled
meeting rooms. API Access is given to each Application through the assigned App ID and App Key. So, the App ID and App Key
are to be used as Username and Password respectively to pass as HTTP Basic Authentication header to access Server API.

For this application, the following Server API calls are used:
* https://developer.enablex.io/video-api/server-api/rooms-route/#create-room - To create room to carry out a video session
* https://developer.enablex.io/video-api/server-api/rooms-route/#create-token - To create Token for the given Room to join a session

To know more about Server API, go to:
https://developer.enablex.io/video-api/server-api/


## 5. Client API

Client End Point Application uses Web Toolkit EnxRtc.js to communicate with EnableX Servers to initiate and manage RTC Communications.

To know more about Client API, go to:
https://developer.enablex.io/video-api/client-api/
