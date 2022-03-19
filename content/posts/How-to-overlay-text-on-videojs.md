+++
author = "Giri Aakula"
title = "How to overlay text on videos using videojs?"
date = "2022-03-19"
description = "In this article I will explain how to overlay text on videos using videojs."
tags = [
    "videojs",
]
jsfiddle="https://jsfiddle.net/GiriAakula/nmL3wfta/3/embedded/html,result/dark/"
+++
 ![Screenshot of the overlay text](/images/videojs-overlay/Screenshot-example.png)

# Introduction

Videojs is a popular javascript library to do anything with videojs in web. As it is a very popular library, it has features that can do almost everything related to videos.

In this article we will learn about how to overlay a simple text on top of video. This is to show that this kind of thing is possible with videojs. You can build on top of this and can build complex UI's and features with the help of css and javascript.

# Step 1:

Install videojs libarary and setup your video within it.

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link href="https://vjs.zencdn.net/7.18.1/video-js.css" rel="stylesheet" />
</head>
<body>

        <video
          id="my-video"
          class="video-js vjs-big-play-centered"
          controls
          preload="auto"
          width="640"
          height="360"
          poster=""
          data-setup="{}"
        >
          <source src="./BigBuckBunny.mp4" type="video/mp4" />
          <p class="vjs-no-js">
            To view this video please enable JavaScript, and consider upgrading to a
            web browser that
            <a href="https://videojs.com/html5-video-support/" target="_blank"
              >supports HTML5 video</a
            >
          </p>
        </video>

        <script src="https://vjs.zencdn.net/7.18.1/video.min.js"></script>
</body>
</html>
```

In order to install videojs in your project you have to add a script file and a css file into your project.
```
<script src="https://vjs.zencdn.net/7.18.1/video.min.js"></script>
<link href="https://vjs.zencdn.net/7.18.1/video-js.css" rel="stylesheet" />
```

When I'm writing this article videojs is on version *7.18*. When you are reading this article videojs might be of later version. Hence I suggest to check with [videojs docs](https://videojs.com/getting-started) and update to latest version of videojs.


# Step 2:

Now you need to create a instance of videojs player. We can do that as shown below.

```
 let playerInstance = new videojs("my-video");

 Here "my-video" is the id of video element.
```

Once we have instance of player with us we can listen for player ready event and append our div element to the player.

```
 playerInstance.on("ready", () => {
    let div = document.createElement("div");
    div.innerHTML = `
    <p style=" margin: 0; color: black; font-size: 5rem; position: absolute;">Giri Aakula</p>
    `;
    playerInstance.el().appendChild(div)
})
```
# Conclusion

That's it! We have successfully overlayed a sample text on top of video. Now you can do some interesting things on top of this.
Very obvious use case could be to add a form and take user feedback after video completion.

<iframe width="100%" height="450px" src="//jsfiddle.net/GiriAakula/nmL3wfta/6/embedded/html,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>


Write to me if you have any questions - me@giriaakula.com