# OmletRTC project
#### WebRTC open source project enhancement and related integrated online service and product devleopment at UC Irvine

## Overview
OmletRTC provides you utilize WebRTC "getUserMedia" API into your code to make your idea be real. 
We focus on video communication between peers─namely video chatting. Now you can create your own service in [Omlet Chat](http://www.omlet.me/) with OmletRTC easier and quickly

## What is WebRTC?
![alt img](https://github.com/UCIUROP2015/UCI_UROP_WEBRTC/blob/master/images/logo-webrtc.png)<br>
webRTC is a new webstandard being developed for peer-to-peer communication on the web. This means that browsers will be able to send information, without sending information through the server. Server side this will reduce load dramatically.

Currently the webRTC standard is very focused on the video & audio aspects of the project. In the future (hopefully near future!) they will begin implementing the data channel, which will allow arbitrary data to be sent peer-to-peer. For now the webRTC team is focused on stabalizing and optimizing the video and audio channels.

Unfortunately, a server (or two servers) will still be required for two reasons, The media for the page must be initially supplied, and the server, in conjunction with a [STUN server](http://en.wikipedia.org/wiki/STUN), is required to synchronize the connections.

## Why OmletRTC?
Using WebRTC for real-time communication, now we do not need a server for storage that usually costs much money as the service is getting bigger. However, it still needs a server for signals to handle user to connect one another. Setting a server is a big obstacle to apply WebRTC for trial or real-service on application market.<br>


## What is included ?
This release is composed of three components:

1. Web server based on socket.io for URL redirection
2. HTML5 WebRTC application
3. Omelt API for web apps

## Device support
* Android 5.0+ (for using Omlet API)

## Browser support
* Chrome 25.0+ (28.0+ for best performance)
* Firefox 22.0+
* Chrome 29.0+ on Android


## Example code

### Client

```html
<video id="localVideo" autoplay="autoplay"></video>
<video id="remoteVideo" autoplay="autoplay"></video>

<script src="/omletrtc.js"></script>
<script>

</script>
```

### Server

```javascript
var io = require('socket.io').listen(port);
//then a bunch of callbacks are available
```


### Reference
* [Developers - Omlet](http://www.omlet.me/developers/)<br>
* [WebRTC 1.0: Real-time Communication Between Browsers](http://www.w3.org/TR/2015/WD-webrtc-20150210/)


