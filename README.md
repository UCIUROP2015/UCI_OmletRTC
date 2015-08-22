# OmletRTC project
#### WebRTC open source project enhancement and related integrated online service and product development at UC Irvine

## Overview
OmletRTC provides you utilize WebRTC "getUserMedia" API into your code to make your idea be real. 
We focus on video communication between peers ─ namely video chatting. Now you can create your own service in [Omlet Chat](http://www.omlet.me/) with OmletRTC easier and quickly

## What is WebRTC?
![alt img](https://github.com/UCIUROP2015/UCI_UROP_WEBRTC/blob/master/images/logo-webrtc.png)<br>
webRTC is a new webstandard being developed for peer-to-peer communication on the web. This means that browsers will be able to send information, without sending information through the server. Server side this will reduce load dramatically.

Currently the webRTC standard is very focused on the video & audio aspects of the project. In the future (hopefully near future!) they will begin implementing the data channel, which will allow arbitrary data to be sent peer-to-peer. For now the webRTC team is focused on stabalizing and optimizing the video and audio channels.

Unfortunately, a server (or two servers) will still be required for two reasons, The media for the page must be initially supplied, and the server, in conjunction with a [STUN server](http://en.wikipedia.org/wiki/STUN), is required to synchronize the connections.

## Why OmletRTC?
Using WebRTC for real-time communication, now we do not need a server for storage that usually costs much money as the service is getting bigger. However, it still needs a server for signals to handle user to connect one another. Setting a server is a big obstacle to apply WebRTC for trial or real-service on application market.<br>
  
## What Is Included ?
This release is composed of three components:
<ol>
<li>Web server based on express for URL redirection<br>
<li>HTML5 WebRTC application<br>
<li>Omlet API for web apps
</ol>

## Device Support
* Android 5.0+ (for using Omlet API)

## Browser Support
* Chrome 25.0+ (28.0+ for best performance)
* Firefox 22.0+
* Chrome 29.0+ on Android

## Installation
```bash
 npm install omletrtc.io
```

## Example code

### Omlet
```javascript
<script>
  // How to initialize documents information. For example,
  omletrtc.initConnection = function () {
    var info = {
      'id' : Omlet.getIdentity(),
      'numOfUser' : 0,
      'timestamp' : Date.now()
    };
    return info;
  };

  // How to update documents information
  // You can create, get and update documents using these function
  Omlet.document = {
    create: function(success, error),
    get: function(reference, success, error),
    update: function(reference, func, parameters, success, error),
    watch: function(reference, onUpdate, success, error),
    unwatch: function(reference, success, error)
  }
  
  // How to add message into documents
  // Function for parameter handling documentApi.update
  omletrtc.addMessage = function (old, parameters) {
    old.numOfUser = old.numOfUser + 1;
    old.timestamp = Date.now();
    return old;
  };
  
  // How to handle message
  omletrtc.handleMessage = function (doc) {
    if (doc.numOfUser > 2) return ;
    if (doc.id.name === Omlet.getIdentity().name) {
      log('[+] sender: ' + doc.id.name + ', receiver: ' + Omlet.getIdentity().name);
    }
  };
</script>
```

### Client

```html
<video id="localVideo" autoplay="autoplay"></video>
<video id="remoteVideo" autoplay="autoplay"></video>

<script src="/omletrtc.io.js"></script>
<script>
  navigator.getUserMedia(omletrtc.constraints, omletrtc.handleUserMedia, function (error) {
    log("[-] getUserMedia: " + error);
  });
</script>
```

### Server

```javascript
var omletrtc = require('omletrtc.io');
//then a bunch of callbacks are available
```


## Reference
* [Developers - Omlet](http://www.omlet.me/developers/)<br>
* [WebRTC 1.0: Real-time Communication Between Browsers](http://www.w3.org/TR/2015/WD-webrtc-20150210/)


## License
The MIT License. Please see [the license file](LICENSE) for more information.
