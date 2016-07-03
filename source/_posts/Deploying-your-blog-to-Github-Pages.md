---
title: Deploying your blog to Github Pages with a custom CNAME
date: 2016-07-03 22:35:39
tags:
---


In this post, I will show how to use Hexo to deploy straight to github using Hexo's inbuilt deploy mechanism. I chose github pages because it is both easy to use as well as being free. As of writing this, Github Pages now uses https by default for all new sites, however this does not extend to using custom CNAMEs. If you decide you want HTTPS for your site (as you should), you can either choose to not use a custom CNAME, and use the standard https://mysite.github.io URL, or you can use a service like Cloudflare to add ssl to your site. I (for the time being) am not using https, but will probably look into doing this in the future.

## Deploying to Github Pages

The first thing you will need when deploying to Github Pages to actually create your repository! You can find detailed instructions for this [here](https://pages.github.com), but in reality all you really need to do is create a new repository with the name:
```
myusername.github.io (where myusername is your username)
```
Once you have done this, all static web page content you push should automatically be available at https://myusername.github.io. You can test this out by pushing any old html file to the repository, and trying to connect to it.

The next step is to add the hexo git deployer package to your project.
```
$ npm install --save hexo-deployer-git
```
And to also add the following to your _config.yaml:
```
  type: git
  repo: https://github.com/myusername/myusername.github.io.git                                                                                            
```
Now, all we need to do is compile our HTML and JS, and deploy. This can be done in the following step:
```
$ hexo generate --deploy
```
This will prompt you for your github credentials, and after you have put them in, Hexo should push everything to Github. Now, if you naviate to https://myusername.github.io, you should see your blog!

## Using a custom CNAME
Using a custom CNAME is also pretty straightforward. You can do this by first adding hexo-generator-cname:
```
npm install hexo-generator-cname --save
```
As well as this, you will also need to set the url key to your custom CNAME in the _config.yaml, as this is where the utility gets the CNAME from. For the curious, all this tool actually does is creates a file during the generate process called CNAME, that contains the custom CNAME inside. When pushed to the repository, Github picks up this file, and uses it to route request to that URL (presumably using the host header) to the correct Github Pages site.
