---
layout:    post
title:     "How to install OpenImageIO in Mac OS X El Capitan"
date:      2016-12-16 00:04:00
permalink: "/how-to-install-openimageio-in-mac-os-x-el-capitan"
---

A little background: a colleague of mine was trying to install this useful library (to process RAW photo files as [Ian Wootten](http://www.ianwootten.co.uk/2014/09/15/processing-camera-raws-with-openimageio-and-python/) has written about) which doesn't have a very user-friendly README file on their GitHub repo. He was getting the following error:
```
Traceback (most recent call last):
  File "a.py", line 1, in <module>
    import OpenImageIO as oiio
ImportError: No module named OpenImageIO
```
1. In order to fix it, you need to have [Homebrew](http://brew.sh/) installed. If you already have it installed run ```brew update``` to make sure you have the latest version.
2. If you don't currently have it, install Python 2.7. You can do so running in your Terminal: `brew install python`. That should take care of installing `pip` as well (which is the Python package manager, and it is very useful most of the times, though it doesn't have `openimageio` support yet.)
3. We can then proceed to (finally) do `brew install homebrew/science/openimageio`, or the whole `science` module. I did only the first.
4. Because Homebrew likely installed the module .so file in a directory that's not being used by Python, we have to symlink the file to one that Python uses. You can locate the Homebrew file at `/usr/local/Cellar/openimageio/1.7.7_1/lib/python2.7/python/OpenImageIO.so` or similar.
5. Now, I was wondering **where does Python import modules from?** Running `python -c 'import sys; print sys.path'` would return an array of all paths where it tries to find modules on import. In my case, I just took the last "site-packages" one, which was `/Library/Python/2.7/site-packages` – Please note this path might defer with yours.
6. Last step, and this is all that matters, is taking the path from #4 and putting it into #5: `ln -s /usr/local/Cellar/openimageio/1.7.7_1/lib/python2.7/python/OpenImageIO.so /Library/Python/2.7/site-packages/OpenImageIO.so`

And you should now be good to go, to run any `import OpenImageIO.so as oiio` all you want. I hope this article saved you the 2 hours I've spent figuring it out.