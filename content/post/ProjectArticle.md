---
author: [
    "Riley Noe",
    "Hunter Nosek"
]
date: 2020-09-19
archives: "2020"
linktitle: Project Article
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Project Article
weight: 10
issues:
categories: 
---


# Building the Georgetonian

![image](/post/g.jpg)

## Introduction

This article will describe Georgetonian, a website created by Riley Noe and Hunter Nosek. Sadly, this is just a personal website created in about a weeks time. It is constructed using the Hugo static-site generator.

The repository is on Github (CONNECT LINK).

[Go to the Support Web Site](www.youtube.com/i-love-hunter-nosek/)

## Choice of Theme


## Modifications to the Theme

### Support for issues

### Support for categories

### Custom CSS

The styling of the theme was very bland. The colors were mostly grey, white, and black.

The main things that we wanted to do in our time working on this:

* Make the colors relevant to Georgetown College
* Add box shadows to the content boxes to make the website look more modern.

We named the file `blog.css` and placed it in my `static/css`directory in the root of our project so it overwrites the css in the theme.

Here's a look at all of the changes we made: 

```css
html,body {
    font-family: 'Open Sans', sans-serif;
    background: linear-gradient(to right, #ec9f05, #ff4e00);
    }
.hero-body {
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    }
.mysocial { color: hsl(0, 0%, 100%);}
.mysocial:hover { color: #1da1f2 }
.tile {
    box-shadow: black 3px 3px 3px;
}
.card {
    border-radius: 6px;
    box-shadow: black 3px 3px 3px;
}
.pagination-link{
    border-color: black;
    border-width: 2px;
    color: black;
    min-width: 2.25em;
}
.pagination-next{
    border-color: black;
    border-width: 2px;
    color: black;
    min-width: 2.25em;
}
.pagination-previous{
    border-color: black;
    border-width: 2px;
    color: black;
    min-width: 2.25em;
}
.navbar-brand{
    background: #f17836 ;
    align-items: stretch;
    display: flex;
    flex-shrink: 0;
    min-height: 3.25rem;
}
.navbar {
    background: #f17836 ;
}
.navbar-item{
    color: black;
}
.tag:not(body){
    background-color: #fd6a02;
    box-shadow: 1px 1px 1px black;
}
a {
    color: black;
}
a:hover {
    color: purple;
  }
a.navbar-item:hover{
      color: purple;
  }
.pagination-link.is-current{
      background-color: lightgray;
      border-color: black;
      color: black;
  }
img {
    float: right;
    margin: 0 auto;
    height: 165px;
}
```
