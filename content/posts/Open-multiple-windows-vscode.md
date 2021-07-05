+++
author = "Giri Aakula"
title = "How to open multiple windows in Visual Studio Code?"
date = "2020-05-12"
description = "How to add multiple git account on one computer?"
tags = [
    "git","terminal","cmd","command prompt"
]
+++

![Computer Image](https://miro.medium.com/max/1400/0*uuE3nswhwp1xKw7W)

At work, we are using microservices for our project. Hence it needs multiple instances of VScode to run parallel. This can be manageable if you have two or three services running in the background, but if you have more than five it easily becomes a pain in a**. We have around seven services running and every time to startup these process we need to open a new window in the specific folder manually.

It would take around 10–15 minutes to simply start these projects, which impacts my productivity hugely. There are some solutions available to solve this particular problem like workspaces in vscode. But workspaces put all our services in one window, which is not the solution that I am looking for.

Hence the only solution I got is to write a script that automatically opens multiple windows of vscode. I am using a windows machine so I wrote a batch script to automate this process.

```batch
cd C:\Users\gaakula\Documents\My-hope\service1
CALL code .
cd C:\Users\gaakula\Documents\My-hope\service2
CALL code .
cd C:\Users\gaakula\Documents\My-hope\service3
CALL code .
cd C:\Users\gaakula\Documents\My-hope\service4
CALL code .
cd C:\Users\gaakula\Documents\My-hope\service5
CALL code .
cd C:\Users\gaakula\Documents\My-hope\service6
CALL code .
pause
```

In the above script, we are cd’ing(going) into the directory where the code is present. After that, we are calling the vscode from there to open a directory in that directory and we are doing that for all our services. I think you can do the same in Linux and Mac machines. But you have to do some changes here and there in the above script to make it work in bash. I believe we don’t have to do any breaking changes in the above script to make it to work in bash.