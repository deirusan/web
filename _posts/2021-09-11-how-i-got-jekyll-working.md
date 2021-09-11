---
layout: post
title:  "How I got this website running on Github Pages with Jekyll and a custom domain "
date:   2021-09-11 17:41:09 +0100
categories: jekyll
---

This is how I got my github pages + jekyll site working on macOS Big Sur *with* a custom domain.

After watching this great [tutorial on youtube by Bill Raymond](https://www.youtube.com/watch?v=EmSrQCDsMv4), I figured I could get my site up and running within half an hour. Bill holds your hand through the entire process of configuring your repo, installing jekyll, and creating your first blog post. 

Of course, whenever I think something is going to be easy, it turns out to be a lengthy stumble into one wall after another. I was thwarted almost immediately. I couldn't launch jekyll. I spent an hour trying to understand why my system hates me, why it couldn't find certain gems, and why my "bundle" refused to update. 

After a frenzied google search, I landed on a [walkthrough by Moncef Belyamani](https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/)) that solved all my ruby gem problems. 

Thank you, Moncef Belyamani, you're the real gem here.

I completed all his steps and then installed jekyll and bundler with the command:
`gem install --user-install bundler jekyll`.

Afterwards, I was able to launch my jekyll site and finish [Bill Raymond's tutorial](https://www.youtube.com/watch?v=EmSrQCDsMv4).  

## Notes on _config.yml
Bill's tutorial shows you how to configure a github pages site *without* a custom domain. For my site to render properly, I needed to leave the `base_url` empty, like this `""`, instead of specifying the name of the repo like Bill suggests.

## Notes on CNAME and A records
To get my custom domain working with github pages, I typed in my custom domain in the **Pages** settings of the repo. 

![github-pages-settings](/_posts/images/ghub-settings.png "Github pages custom domain")

Then I created a `CNAME` record that points to my github pages address.

![cname](/_posts/images/cname.png)

Finally, I created four `A` records, one for each of github's IP addresses:

- 185.199.111.153
- 185.199.109.153
- 185.199.110.153
- 185.199.108.153

Here's what one of the entries looks like for me.

![img](/_posts/images/Arecord.png)

And there you have it, a short chronicle of how this page was born. Thank you Bill and Moncef for the help!





