---
title: 'Remote Download'
date: 2020-06-16
permalink: /posts/2020/06/remote-download/
tags:
  - research
---

## Downloading a file from Google Drive with CLI

1. Set the file sharing settings to "anyone with a link can view", then copy the file ID and paste into the following command

    $ wget --no-check-certificate -r 'https://drive.google.com/uc?id=COPY_ID_HERE&export=download' -O DOWNLOAD_FILENAME
