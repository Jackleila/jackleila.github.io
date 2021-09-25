---
title: "How to easily create a blog using Hugo"
date: 2021-09-19T19:02:57+02:00
categories: [web]
tags: [hugo]
featured: true

draft: false
---
### What is Hugo?

Hugo is an open-source framework to simplify the process of creating static websites. There are a lot of different templates we can use online, which are usually very simple but beautiful. Some of them are even pretty original [such as this one inspired in Mr. Robot](https://github.com/panr/hugo-theme-terminal).

Now that we had a brief introduction of what Hugo is, let us make the theory into practice.

### Installation

#### Windows

We can install Hugo on Windows with Chocolatey:

	choco install hugo
	
Or with scoop:

	scoop install hugo

	
#### Linux and MacOS

We can use Homebrew for the installation:

	brew install hugo

		
Additionally, if you are using MacPorts on macOS, you can install with:
	
	port install hugo

		
### Getting started

1. Create your site typing:

		hugo new site myblog
	

2. Download a templates

		git submodule add https://github.com/wlh320/hugo-theme-hulga.git themes/hulga
	 
3. Create content by typing

		hugo new posts/mypost.md
		
		
4. Write content in posts/mypost.md

5. Hugo will build the content for you with the command

		hugo
	
6. You can serve the website on localhost with the following command:
	
		hugo -D serve
	
7. If you go to localhost:1313 you can check your new blog


	