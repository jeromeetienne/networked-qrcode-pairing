# Networked QRCode Pairing

It all started by this [tweet](https://twitter.com/jerome_etienne/status/954390926209806336)

    IDEA: to pair 2 phones with webrtc, we could display a qrcode on one phone 
    and scan it with the other. Thus the two phones will know each other and 
    establish the connection 😎

I wanted to pair 2 phones together and have them play a game together.
It would be nice if say 2 persons in the same room could play a game.

So i did this proof of concept.

Here is the repository [github.com/jeromeetienne/networked-qrcode-pairing](https://github.com/jeromeetienne/networked-qrcode-pairing) repository on github

Here is a running [example with glitch](https://same-magazine.glitch.me/my-example.html)

# Principles
It is all done within the browser. So we leverage the url. The principles are simple:

- If the url of the page contains ```?roomName=fooBar```, then it will join the room fooBar.
- if the url doesn't contain any ```roomName``` parameters, we assume it is the first
player to join and we create a new room with a random roomName.
Other players will have to scan his qrCode to join his room.

# Implementation Details
The implementation is quite straight forward. It is just an assembly of the proper
piece of software.

- [aframe](https://aframe.io) for the 3d
- [networked-aframe](https://github.com/networked-aframe/networked-aframe) for the multi user part
- [jquery.qrcode](https://github.com/jeromeetienne/jquery-qrcode) for generate the qrCode. (an old project of mine from 7years ago.. gasp 😱)

[networked-aframe](https://github.com/networked-aframe/networked-aframe) is doing most of the work. 
It is a very nice project done by the excelent [@HaydenLee37](https://twitter.com/HaydenLee37).

It is the [Getting Started example from networked-aframe](https://github.com/networked-aframe/networked-aframe#getting-started).
Then i just added qrcode generated from [jquery.qrcode](https://github.com/jeromeetienne/jquery-qrcode).
Then i deployed it on [glitch](https://glitch.com/~same-magazine).

It went rather smoothly.


# How to use the demo

First you install all dependancies
```
npm install
```

Then you run the local server

```
npm start
```

# Deploy on glitch


# Issue with AR 
For this sharing mechanism to work, 
we need a qrcode reader able to launch the proper browser for our URL.
Usually it launch the default browser: chrome on android, safari on ios.
But here we would need to launch [WebARonARCore](https://github.com/google-ar/WebARonARCore)/[WebARonARKit](https://github.com/google-ar/WebARonARKit).

Maybe it would be fixed with a url scheme.
