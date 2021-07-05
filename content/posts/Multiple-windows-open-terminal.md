+++
author = "Giri Aakula"
title = "Run Multiple Services by One Click[Windows Terminal]"
date = "2020-10-05"
description = "Running multiple services in the windows terminal with in one go."
tags = [
    "windows","terminal","cmd","command prompt"
]
+++


![Computer Image](https://miro.medium.com/max/1400/0*V8hgPRiZpbQoL_-x)

We all there opening multiple windows of vs code one by one and typing *npm start* to run multiple services every time we restart our computer. This will easily become a huge task if you have more than 5 services. That’s where automation kicks in and saves our day. In this article, we will see how to automate this.

Lately, Microsoft is embracing open source and making few of their projects open to everyone. One of that project is *windows terminal*, which is a quite interesting project and organisers of this project have huge plans. We will use this terminal to automate our services. If you don’t know about windows terminal check their [docs](https://docs.microsoft.com/en-us/windows/terminal/).

In windows terminal, we can open multiple tabs using this command

```bash
wt -p "Command Prompt" `; new-tab -p "Windows PowerShell"
```

Above command open two tabs one with command prompt and another with PowerShell. If you want the third tab add this command at the end.

```bash
new-tab -p "Windows PowerShell"
```

The whole command to open three tabs now looks like this

```bash
wt -p "Command Prompt" `; new-tab -p "Windows PowerShell" `; new-tab -p "Windows PowerShell"
```

To open a terminal at a specific directory, run this

```bash
 wt -p "Windows PowerShell" -d C:\Users\gaakula\service1 `; new-tab -p "Windows PowerShell" -d C:\Users\gaakula\service2
```

The *-d* flag here indicates directory we want to open our terminal. As of now we successfully open two terminal windows at specific directories we want. The last thing to do is to run our command at that specific directory. For that, we have this command

```bash
 wt -p "Windows PowerShell" -d C:\Users\gaakula\service1 cmd /k npm start `; new-tab -p "Windows PowerShell" -d C:\Users\gaakula\service2 cmd /k npm start
```

The above command runs npm start command on both the tabs. That’s it we have successfully opened two services and ran them automatically with just one command. Let’s save this command in a batch file so that we don’t have to open the terminal and run this command every time. Open notepad and paste this command there and save the file with .bat extension. That's it, open that batch file to run your services.

Here we saw an example of two services it can be applied to any number of services we want. I am currently running 7 services and a docker-compose service. Here the code I’m using for that

```bash
 wt -p "Windows PowerShell" -d C:\Users\gaakula\Documents\My-hope\kibo_prompt_subscriber cmd /k npm start `;new-tab -p "Windows PowerShell" -d C:\Users\gaakula\Documents\My-hope\kibo_localenvironment cmd /k docker-compose up `;new-tab -p "Windows PowerShell" -d C:\Users\gaakula\Documents\My-hope\kibo_admin cmd /k npm start `;new-tab -p "Windows PowerShell" -d C:\Users\gaakula\Documents\My-hope\kibo_resources cmd /k npm start `;new-tab -p "Windows PowerShell" -d C:\Users\gaakula\Documents\My-hope\kibo_prescription cmd /k npm start `;new-tab -p "Windows PowerShell" -d C:\Users\gaakula\Documents\My-hope\kibo_patient cmd /k npm start `;new-tab -p "Windows PowerShell" -d C:\Users\gaakula\Documents\My-hope\kibo_account_admin cmd /k npm start `;new-tab -p "Windows PowerShell" -d C:\Users\gaakula\Documents\My-hope\kibo_symptoms cmd /k npm start
```

Hope this article helps you to make your dev life easier.

References:

[https://docs.microsoft.com/en-us/windows/terminal/](https://docs.microsoft.com/en-us/windows/terminal/)
