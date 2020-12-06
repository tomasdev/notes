---
layout:    post
title:     "How to integrate Drush into PuPHPet"
date:      2016-09-13 23:08:00
permalink: "/how-to-integrate-drush-into-puphpet"
---

Yeah. Long time without writing here. I have lost about 2 or 3 hours of my life trying to configure it. So I think it deserves a post so anyone googling can find it.
It is as simple as adding the following to your `config.yaml` file:

```
drush:
    install: '1'
    version: '8.x'
```

Yes. That's right. PuPHPet supports Drush already (I think because Puppet does.) Make sure you are already using `php` with `composer`, otherwise it won't work.