+++
author = "Giri Aakula"
title = "How to detect ID3 metadata in videojs?"
date = "2022-03-06"
description = "We will discuss id3 metadata in videojs."
tags = [
    "videojs",
]
+++

![Web Representation](/images/id3-metadata/metadata.webp)

# What is ID3 metadata?

An ID3 metadata is information that is embedded into a stream. It could be any stream hls or dash.

[Videojs](https://videojs.com) library supports all the above mentioned media formats.

We can detect id3 metadata from the video stream using videojs library.

```
playerInstance.textTracks().on('addtrack', function (e) {
    var track = e.track;
    if (track.label === 'Timed Metadata') {
        track.on('cuechange', function () {
            var myActiveCue = track.activeCues[0];
            if (myActiveCue && 'frame' in myActiveCue && myActiveCue.frame !== undefined) {
                let cueDataObj = myActiveCue.frame;
                console.log(cueDataObj, "id3 metadata")
            }
        });
    }
});
```

*playerInstance* - Instance of the player

Example - ```let playerInstance = new videojs("playerId")```

### Explanation:

Here we listen for *addTrack* event and on each add track we check if the label is Timed Metadata or not.

If the metadata is Timed Metadata then we will add an event listener for cuechange. This will fire on every cue change which means of every ts segment change in hls stream. We will get the id3 metadata in that frame by using some conditions.



Write to me if you have any offer for me - me@giriaakula.com

