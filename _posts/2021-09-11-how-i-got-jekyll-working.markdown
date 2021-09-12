---
layout: post
title:  "How I got GitHub Pages and jekyll working with a custom domain on macOS Big Sur "
date:   2021-09-11 17:41:09 +0100
categories: jekyll
---

I wanted to create a blog with minimal costs because I'm sporadic in my writing — weeks and months can go by without producing anything useful. I also wanted a blogging platform free from feature bloat and that's easy to maintain. I figured a GitHub Pages site with `jekyll` would be a perfect fit for me.

What follows is a high-level overview of what I did to get my site working with a custom domain. I won't provide a detailed step-by-step guide because I'd rather point you to the sources that helped me. 

### My machine specs at the time of install
- macOS Big Sur 11.5.2
- oh-my-zsh shell
- Macbook Pro 15" 2019

### Step 1 - Watch Bill Raymond's tutorial
I don't have an aversion to reading documentation, but if I can watch a video that summarizes the process for me, then that's what I'll do. Watch [Bill's tutorial](https://www.youtube.com/watch?v=EmSrQCDsMv4) and let him hold your hand through configuring your GitHub repo, installing `jekyll`, and creating your first blog post. If you have a custom domain, be sure to add it in the settings of your GitHub Pages [(see below)](#step-2---configure-your-custom-domain).

#### Problems installing jekyll?
Bill's tutorial presents a seamless, happy experience. But in my case, I had to fight against my ruby installation for about an hour before I could install `jekyll` and `bundler`. I had `ruby v3.0` installed on my system and `rvm` managed the versions and gems. Because of this, I ran into all sorts of problems with missing gems, borked paths, and failed updates. I couldn't progress Bill's tutorial.

And since I know nothing about ruby, I turned to google for help.

After a frenzied google search, I found a [walkthrough by Moncef Belyamani](https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/) that solved all my ruby issues. In short, I ditched `rvm` in favor of `chruby` and downgraded from `ruby v3.0` to `ruby v2.7.2`. 

Afterwards, I could install `jekyll` and `bundler` successfully using the command: 

`gem install --user-install bundler jekyll`.

Thank you, Moncef Belyamani, you're the real gem here.

### Step 2 - Configure your custom domain DNS records 

#### CNAME and A records
To get my custom domain working with GitHub Pages, I typed in my custom domain in the **Pages** settings of the repo. 

![github-pages-settings](/assets/images/ghub-settings.png "Github pages custom domain")

Then I created a `CNAME` record with my domain provider that points to my GitHub Pages address.

![cname](/assets/images/cname.png)

Finally, I created four `A` records, one for each of GitHub's IP addresses:

- 185.199.111.153
- 185.199.109.153
- 185.199.110.153
- 185.199.108.153

Here's what one of the entries looks like for me.

![img](/assets/images/Arecord.png)

#### Notes on _config.yml
Bill's tutorial shows you how to configure a GitHub Pages site ***without*** a custom domain. For my site to render properly (i.e., all file paths work), I needed to leave the `base_url` empty, instead of specifying the name of the repo like Bill suggests.

```yaml
baseurl: "" # the subpath of your site, e.g. /blog (in my case it wasn't necessary to specify this, if so, it breaks the site)
url: "https://deirusan.github.io" # the base hostname & protocol for your site, e.g. http://example.com
```

And there you have it, a short chronicle of how this page was born. Thank you Bill and Moncef for the help — Good luck to everyone and happy blogging!





