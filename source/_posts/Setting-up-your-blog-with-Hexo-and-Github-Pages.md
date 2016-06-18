---
title: Setting up your blog with Hexo and Github Pages
date: 2016-06-18 18:02:25
tags:
---

In this post, we will explore how to create a blog using Hexo. In a future post, we will cover how to deploy your blog to Github Pages, and how to use a custom domain.

We will be doing this using two different tools to accomplish this:
- [Hexo](https://hexo.io/)
- [Github Pages](https://pages.github.com/)

## What is Hexo?
Hexo is a free, open source tool (using the MIT License) for generating static blog pages. It supports various plugins and themes, and is generally much, much easier than writing the HTML and JavaScript for your site yourself. There are a few different tools that do the same thing, such as Jekyll or Hugo. I chose Hexo primarily because I am more familiar with Node than with either Ruby or Go. If you haven't used Node before, don't worry - the use of Node here is quite trivial and doesn't require any in depth knowledge.

Hexo uses markdown files from which it generates your sites static content, so if you ever decide you want to move to a different tool you should be able to use your existing markdown files without too much hassle.

## Getting your Hexo project set up
To initially install Hexo onto your system, you will need to install the Hexo command line tool:
```
$ npm install hexo-cli -g
```
After this has finished, you will be able to initalise new Hexo projects on your machine. To do this, CD to where you want to create your new Hexo project, and run:
```
$ hexo init my-blog
$ cd my-blog
$ npm install
```
This creates a new directory, called my-blog, which will contain everything you need to start generating your static assets. This project is just a node project, and as such has an associated package.json, which contains all of your projects dependencies which npm will install.

You can verify that everything has worked by running
```
$ hexo server
```
in your browser. If everything has gone to plan, then navigating to http://localhost:4000 in your browser should show your brand new blog!

You may notice which you do this, however, that there are several things on your blog that don't look right. Take for example the name of your blog - you probably don't want to call your blog "Hexo". Open the file \_config.json in your favourite editor, and start personalising your blog :) You may also want to install a different theme to the default. This can be done by finding a theme that you like, cloning it to the themes directory, and setting it in the \_config.json file. Please note - themes require their own configuration, and will likely contain another \_config.json file which you will need to edit.

There you have it! Your new blog. There are only two problems with it:
1. There isn't any content!
2. You aren't hosting it anywhere, meaning only you can see it!

The first problem is easy enough to fix - start writing some new posts! The second problem is just as easy (probably even easier) to fix, using Github Pages. I will cover how to deploy your site to Github Pages in the next post.
