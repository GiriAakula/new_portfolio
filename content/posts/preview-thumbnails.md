+++
author = "Giri Aakula"
title = "Videojs: How To Create Preview Thumbnails"
date = "2021-04-17"
description = "Creating youtube video preview thumbnails in videojs"
tags = [
    "videojs",
]
+++

![Thumbnail Preview Image](/images/thumbnail_preview.png)


Have you ever wondered how youtube shows the preview of the video on the progress bar? It is at times so useful especially in the videos over one hour long. I have to achieve this same thing at work. We are using videojs to build our custom player on top of it.

## How can we achieve this?

There are mainly two ways to achieve this. One is two generate so-called CSS sprites for the video beforehand and getting through an API. The second is to generate a WebVTT file beforehand for the video and getting the file through an API.

There is also another way where you can hardcode image files at specific timestamps of the video. This may be useful for the single video files on the website in which we will hardcode this in the code itself. But this is not suitable for a dynamic player like ours. You can find more about this in this [article](https://player.support.brightcove.com/plugins/display-thumbnail-previews-plugin.html).

You can generate thumbnails without generating stuff like sprite or WebVTT but the process is pretty slow and requires significant computing resources from the client side which is not likely on many occasions. You can know more about this in this [StackOverflow article](https://stackoverflow.com/questions/52900022/how-to-generate-video-preview-thumbnails-for-use-in-videojs).

We decided to go with generating sprite images beforehand and store them in a bucket and refer them with an id that is linked with video id whenever needed.

## Generating Sprites

We decided to use this library called video-thumbnail-generator from [Flavio Ribeiro](https://github.com/flavioribeiro). It is powered by FFMPEG under the hood and built using python on top of it. It is the tool we are looking for and it gets the job done. We may look for other alternatives in the future.

`https://github.com/flavioribeiro/video-thumbnail-generator`

Documentation in the repository is well written and can describe itself how to generate them. Keep in mind to generate the sprites with height and width that will match with the dimensions of the preview in the player. Other than that you can go on with the default settings.

These generated sprites which are typically in PNG or JPEG format need to be stored somewhere and exposed over an URL. I suggest storing them in a public bucket or something like that.

## Integrating Sprites With Player

Once sprites are ready it is now time to use them in our player. There is this awesome plugin called [videojs-sprite-thumbnails](https://github.com/blacktrash/videojs-sprite-thumbnails) which will seamlessly integrate sprites into our player.

Install the plugin

`npm install --save videojs-sprite-thumbnails`

Initiate the plugin

```html
<script src="//path/to/video.min.js"></script>
<script src="//path/to/videojs-sprite-thumbnails.min.js"></script>
<script>
  var player = videojs('my-video');

  // setup 160x90 thumbnails in sprite.jpg, 1 per second
  player.spriteThumbnails({
    url: 'https://example.com/sprite.jpg',
    width: 160,
    height: 90
  });
</script>
```

The width and height here should match with the sprite width and height. That’s it.. You’ve successfully generated thumbnail previews to your video. This is the working [example](https://medium.com/media/5ff2da860a144d2a0410a1d7aab560f1) of it.


#### Working Example Preview

![Working Example Preview](https://cdn-images-1.medium.com/max/2850/1*NchsKcfd6wyCIT1tC5lqDw.png)

