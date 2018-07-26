---
layout: post
title:  "Real-time Applications With WebRTC"
date:   2018-07-04 08:48:46 -0400
categories: webrtc real-time
---

# WebRTC: Web Real-time Communications

If you want to make use of real-time capabilities on the Internet you basically have three options: ajax/polling, web sockets, and WebRTC. In this article we cover the different technologies used in real-time applications, their pros and cons, but we will emphasize the use of WebRTC and its characteristics.

### Ajax/polling
It is possible to develop a real-time app by using javascript to asynchronously poll the server for changes or new data. It is a very costly technique, and it presents a high latency due to overhead.

### Web Sockets

Websockets presents a better performance compared to polling, cause now you have a server and the hosts subscribe to rooms in it, every time a host broadcast a message to that room all the subscribers will receive that very same message. There is no direct connection between hosts, all the messages exchange are performed through the server. Latency is also an issue when using web sockets.

![image tooltip here](/assets/websocket.png)

## WebRTC

Finally, we are going to talk about WebRTC. The big star in this blog post.
The way WebRTC works is by enabling direct connection between hosts over the Internet. By having a direct connection you may have low latency. It is important to highlight the fact that it is not always possible to have a direct connection, due to NAT translations and firewalls for instance, and in cases like that the best option would fall back to web sockets.

### API's
WebRTC has several JavaScript APIs to enable video, audio or data sharing. See below:

- _getUserMedia()_: capture audio and video.
- _MediaRecorder_: record audio and video.
- _RTCPeerConnection_: stream audio and video between users.
- _RTCDataChannel_: stream data between users.

In order to establish a webRTC connection you need to exchange control messages between hosts. So, you need a signaling server in order to accomplish that requirement. You can develop your own, or use a server as a service.

![image tooltip here](/assets/webrtc.png)


References:
1. [WebRTC Project](https://webrtc.org "WebRTC Project's Home Page")
2. [WebRTC: Google Code Labs](https://codelabs.developers.google.com/codelabs/webrtc-web "Google Code Labs")
3. [Socket.io](https://socket.io "Web Sockets")
