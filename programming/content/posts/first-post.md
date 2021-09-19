---
title: "How to create a blog using Hugo"
date: 2021-09-19T19:02:57+02:00
draft: true
---
### What is Hugo?

Hugo is an open-source framework to simplify the process of creating static websites. We can find a lot of different templates we can use online, which are usually very simple but beautiful. Some of them are even pretty original [link](https://github.com/panr/hugo-theme-terminal).

Now that we had a brief introduction of what Hugo is, let us make the theory into practice.

### Installation

#### Windows

Installing Hugo on Windows is as easy as typing:

	choco install hugo
	

### Getting started

1. Create your site typing:

		hugo new site myblog
	

2. Download a templates

		git submodule add https://github.com/wlh320/hugo-theme-hulga.git themes/hulga
	 

3. Build and serve
	
		hugo -D serve
	
4. Go to localhost:1313 and check your new blog

5. Create content by writing

		hugo new post mypost
	