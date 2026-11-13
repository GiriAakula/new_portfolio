+++
author = "Giri Aakula"
title = "Contributing a Google Analytics 4 extension to Video.js"
date = "2026-11-13"
description = "What I learned building and contributing a Google Analytics 4 extension across the Video.js ecosystem."
tags = [
    "videojs",
    "open-source",
    "javascript",
]
+++

I’ve been working with Video.js for about five years. At Vidgyor and Silverpush, my main job was building web and mobile video players on top of it. Over that time, I got to work on quite a few player features: analytics, Google IMA ads (pre-roll, mid-roll, and post-roll), and pause-banner ads, to name a few.

One feature I especially remember was making a banner ad feel like a video ad, complete with its own timer. Sometimes video ad inventory would come back empty, but banner ads were more likely to fill. So we used the banner as a fallback and kept the viewing experience moving. Small feature, but it made a real difference in those situations.

Working with Video.js for so long taught me its strengths, its quirks, and, yes, a few bugs too. I also got to know where it could be challenging. For me, the player could feel bulky, and building a fully custom UI on top of it was not always straightforward.

## Why I wanted to contribute

When I heard about Video.js v10 being rebuilt from the ground up, I got genuinely excited. This was a player I had spent years working with, so naturally I thought: *I should contribute something back.*

I started exploring the codebase and noticed there wasn’t a Google Analytics extension yet. A lot of teams already use Google Analytics, so adding a GA4 integration felt like a useful place to start. The project’s agent-assisted development workflow also made it easier for me to explore the structure and understand how the pieces fit together.

## Building the extension

I used Cursor to help me work through the code and build the extension, then opened [PR #9563](https://github.com/videojs/video.js/pull/9563). The contribution added GA4 event tracking and made the extension available through the Video.js HTML and React integrations, with CDN support and documentation as well.

Before opening the PR, I built a test page and checked that the events were firing as expected. I hosted the page on S3 and included the link in the pull request, so reviewers could try the integration for themselves.

The first version was only the beginning. Wesley Luyten ([luwes](https://github.com/luwes)) took the time to review it and share detailed feedback. I worked through multiple rounds of comments, fixing edge cases and refining the API. That back-and-forth helped me catch things I hadn’t considered at first, and made the final contribution much stronger.

The PR was merged on November 3, 2026. Seeing something I built become part of a project I’ve used for years felt surreal—in the best way.

I’m happy I got to give something back to Video.js. And this probably won’t be my last contribution. I’d love to keep helping with this extension and other parts of the project. Lets see, what comes next!
