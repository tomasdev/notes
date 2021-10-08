---
layout:    post
title:     "Where it all started"
date:      2017-08-01 06:22:40
permalink: "/where-it-all-started"
---

During 2013, there had been several interesting open-source projects. Since NodeJS was released back in 2009 the technology in web related stuff has done a highly visible turn.

Day after day is becoming more common to see native applications (both for mobile devices and desktop computers) being no more than a wrapper for a webapp. Examples are what can be built using frameworks such as [Cordova](https://cordova.apache.org/) or [node-webkit](https://github.com/rogerwang/node-webkit). Because now we can do both back-end and front-end, the possibilities are infinite.

I believe one of the key factors in this JavaScript peak –besides the API and the flexibility the language has– could be the introduction of [npm](https://www.npmjs.org/) as a repository for useful modules. That's what most developers use to share the modules everyone create but also the modules others create that one wants to use.

Twitter is a wonderful world. It allowed me to meet a lot of interesting people but also to interact with people I admired in the front-end world. It got me my last two jobs. And it's my _via_ to be -almost- up to date with news, trends and releases in the industry. There was this module around there, called [peerflix](https://github.com/mafintosh/peerflix), which allowed any programmer to download a torrent sequentially taking advantage of how torrents work and I bet everyone thought "hmmm interesting" at a glance. There was something missing for it.

Dan created a tiny user interface integrating peerflix with node-webkit, resulting in a handy shortcut app inside the Mac menu bar. But being a good programmer sometimes comes with a being not-so-good in design. Even though it was minimalistic, it wasn't as appealing as it could be. Then Abad came in, with a quite interesting visual concept.

<iframe src="//instagram.com/p/jbrZtqR8_k/embed/" width="612" height="710" frameborder="0" scrolling="no" allowtransparency="true"></iframe>

Time went by and it never got real. But Abad continued to iterate over it, expanding the idea a little bit more. He needed a programmer to implement it, so he asked in Twitter and [I replied back](https://twitter.com/tomasdev/statuses/426153117550657536) telling him I didn't want to be a rockstar but admitting I like to help.

I did enjoy a lot working on it _ad honorem_, because the idea was exciting and the interface was slick. At first [it was white](http://instagram.com/p/jso59IR8yA/), later to become the black version. I planned a roadmap, and we put all the code into a private GitHub repository (just to prevent spoilers, although we released some sneak peaks here and there,) inviting some friends who wanted to either try it out, or collaborate with it.

At the beginning it used [KimonoLabs](https://www.kimonolabs.com/) as scrapper to get the results for the Movies HD category in The Pirate Bay. And I matched the results with Open Subtitles API to let our lovely Spanish become available. Poster images and movie's information were coming from RottenTomatoes. This whole thing had a `localStorage` based cache to prevent requesting too many times the same information - movies don't mutate, do they? The mechanism triggered VLC to reproduce the movies. Nonetheless, with time we realized some formats, such as `.avi`, weren't very compatible and some codecs could prevent the movie to be reproduced partially ("streaming".)

It was time for a change.

I don't remember who, but someone in the team (by then) found out [YIFY](http://yts.re/) were one of the main uploaders to TPB HD Movies and they even uploaded everything in a useful `.mp4` format. We knew we could implement an HTML5 player and have a unique integrated experience. So we did. Luckily they had an API; so, no more scrapping.

After the first semi-public release (via DMs, mails or chats) to non-technical people we started getting a lot of good feedback and some bugs, as node-webkit runtime could be hard to guess sometimes. And we reached our RottenTomatoes limit of 10.000 requests per day (50 latest movies * ~200 people) we had to move it to TheMovieDB. And subtitles, most of the times, weren't matching the YIFY uploaded version (thing that we used to be able to "fix" with VLC capabilities.)

Then [Windows 7 support](http://instagram.com/p/kVR3Vktp9e/) came by, because not all of our friends have a Mac, it's quite expensive here in Argentina. I always had in mind to release it open-source as soon as we had something stable to give, and it was around time. We proudly [published in HackerNews](https://news.ycombinator.com/item?id=7244190) about it, and the doubts started to happen when people mentioned _"hey are you sure you want to use your real GitHub username for such an illegal thing?"_

As the application was starting to be used around the globe, I got a little stressed about the pull-requests going on and I decided to step away from the project. A bunch of friends just took it and continued its development. Obviously, the application [continued to be iterated](http://instagram.com/p/lG9On1x86I/) as feedback was received, but the [impact](http://www.vice.com/read/popcorn-time-is-just-like-netflix-except-everything-is-pirated-mb-test) [started](time.com/18867/popcorn-time-is-so-good-at-movie-piracy-its-scary/) to be so big everybody -I guess- started to feel the pressure. The rest of the story, you already know it.

**I want to thank everyone who committed at least one line of code, but specially to those who warned and helped us about possible legal issues.**

###Learnings

1. Open-source doesn't guarantee people will help you. It is more often you'll get a bug report or a feature request than a pull request to fix one of those.
2. People always want to have the victory but not always want to do what needs to be done. It's hard to differentiate between "noise makers" and those who really help.
3. [Ambition can be poison](http://signalvnoise.com/posts/3547-ambition-can-be-poison).
4. The best idea is the one you execute.
5. It is always good to have friends. Specially nerdy friends.
6. Never trust journalists.

###Why now?
Because I have read too many articles lying about the project or even what they would do if they knew the creators. The proof was always there: Instagram, GitHub, Twitter. And because, in the end, I'm proud of what we achieved.