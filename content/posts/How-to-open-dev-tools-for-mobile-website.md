+++
author = "Giri Aakula"
title = "How to inspect a website in mobile using chrome dev tools?"
date = "2022-05-02"
description = "How to inspect a website in mobile using chrome dev tools?"
tags = [
    "chrome","dev tools","mobile","mobile web"
]
+++

![An image illustrating mobile web](/images/mobile_web.jpeg)

Yesterday, I was doing routine work of coding websites using vanilla javascript. Evrything is going well except when I heard that we have to support mobile devices from now. Hence I started using wierd media quieries and started supporting all form factors.

Chrome dev tools has this feature to preview your website in mobile dimensions and make changes as needed. This is very helpful and get the job done most of the times.

Although, we can do all the mobile related things in the chrome dev tools, but it is yet not a real device. There are some issues like network and performance which we need to test on real mobile devices.


Using this trick we can open a website in real mobile device and connect to a computer and debug.


### 1. Connect computer and mobile:
- Connect your android phone and your computer (mac | windows | linux) using USB cable.
- Open your phone, go to Settings and in settings search for "usb debugging"
- Turn on USB Debugging

![An image illustrating mobile web](/images/debug.jpeg)

### 2. Open dev tools on chrome

- Go to chrome://inspect in chrome browser
- List of devices connected will appear
- The devices will only show if you have opened chrome browser in your phone.


![An image illustrating mobile web](/images/inspect.png)


That's it now you can open a new tab, open page of your choice and click inspect, dev tools will appear.

If you have any questions, write to me me@giriaakula.com