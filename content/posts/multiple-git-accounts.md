+++
author = "Giri Aakula"
title = "How to add multiple git account on one computer?"
date = "2020-06-06"
description = "How to add multiple git account on one computer?"
tags = [
    "git","terminal","cmd","command prompt"
]
+++

![Multiple Github accounts pictorial representation](https://miro.medium.com/max/1400/0*e_LGVegnNJ5PzW5K.png)

## Introduction

A lot of us are using the same computer for personal and professional work. Because it is not easy and efficient to carry two computers wherever you go, right? Nowadays a lot of companies are using git to manage their codebase. Hence we are forced to login to our computers by our work git credentials.

A lot us have personal git accounts in where we store all of our personal projects. It is becoming very hard to access them, particularly on your work computer. Hence I’m going to show you how to manage multiple git accounts on the same computer.

### Generate an SSH Key

First, we have to generate an ssh key for our new git account. Type the below command in your command prompt to achieve that.

`ssh-keygen -t rsa -C "your-email-address"`

Once you click enter it will ask you where to store the key.

![](https://cdn-images-1.medium.com/max/3840/1*3PatFKDDPL6cuVK67RlgOQ.png)

Now give it a unique name so that we can identify further.

![](https://cdn-images-1.medium.com/max/3840/1*3nwrU9SvDKMui56iXkt8CQ.png)

### Get the SSH Key from Github

Go to your Github profile -> settings -> SSH and GPG keys and click on New SSH key.

Now go to your command prompt again and type in the following command to get the ssh key.

`type ~/.ssh/id_rsa_giri.pub`

Copy the entire output of the above command. It will be a giant string.

Now go to your GitHub, in the title field give it a name of your like. Paste the string you copied earlier in the key field. And click on add ssh key.

Now go to your terminal again and type the following.

`ssh-add ~/.ssh/id_rsa_giri`

If you did everything well you should get *identity added *as an output.

### Creating a config file

Our account got added to our computer but we need to tell git which account to use when. This can be achieved using a config file.

If you have vs code installed on your computer, open it in the current folder using *code . *in the terminal.

Go to ssh folder and create a new file with the name *config.*

Paste the following text in the file

```bash
 #Default GitHub
    Host github.com
     HostName github.com
     User git
     IdentityFile ~/.ssh/id_rsa
```

The above is the default GitHub account in our scenario it is the work account. We need to add our personal account now. Paste the following text below the above text.

```bash
#Personal GitHub
    **Host personal**
     HostName github.com
     User git
     IdentityFile ~/.ssh/id_rsa_**giri**
```

Instead of personal in the host, you can give whatever name you want. The Identify file should be pointed to our personal ssh key file.

![](https://cdn-images-1.medium.com/max/3840/1*yGK_VjEcgXEgbrX5x-DpRA.png)

That’s it! we’ve successfully added our second GitHub account. Now it’s time to test if this is working or not.

### Testing

Go to GitHub and create a new repository. Copy the git URL of that repository. It should look something like this

`[git@github.com](mailto:git@github.com):GiriAakula/Bangalore-BMTC-Bus-Station-Platform-Numbers-by-Bus-Service-Numbers.git`

Now, create a folder in your PC wherever you like. Open command prompt in the same folder and initialize a git repository in local by typing the following commands.

```bash
git init
git commit -am “first commit’
```

You’ve successfully initialized a repository and committed the changes. It’s time to push those changes to GitHub.

```bash
git remote add origin [git@](mailto:git@github.com)**pesonal**:GiriAakula/Bangalore-BMTC-Bus-Station-Platform-Numbers-by-Bus-Service-Numbers.git
git push origin master
```

Replace github.com with the host name we’ve given earlier in the config, which is personal in our case.

Now go to your GitHub repository and you can see that the changes are pushed.

##### References:

[Quick Tip: How to Work with GitHub and Multiple Accounts](https://code.tutsplus.com/tutorials/quick-tip-how-to-work-with-github-and-multiple-accounts--net-22574)

[How to manage multiple GitHub accounts on a single machine with SSH keys](https://www.freecodecamp.org/news/manage-multiple-github-accounts-the-ssh-way-2dadc30ccaca/)

[Multiple github accounts on the same computer?](https://stackoverflow.com/questions/3860112/multiple-github-accounts-on-the-same-computer)


