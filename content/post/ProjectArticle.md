---
author: [
    "Riley Noe",
    "Hunter Nosek"
]
date: 2020-09-27
archives: "2020"
linktitle: Project Article
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: "Project Article: Building the Georgetonian"
weight: 10
issues: September 2020
categories: "ae"
---

![image](/post/g.jpg)

## Introduction

This article will describe Georgetonian, a website created by Riley Noe and Hunter Nosek. Sadly, this is just a personal website created in about a weeks time, not the official Georgetonian website. It is constructed using the Hugo static-site generator.

The repository for our website is on [Github](https://github.com/jrileynoe/Georgetonian).

[Go to the Support Web Site](www.youtube.com/i-love-hunter-nosek/)

## Choice of Theme

Going into this project, we had a decent idea of how our site needed to look. Specifically, we were looking for three main criteria:

* **Professional**: Not overly busy like most News Paper themes, but more robust than a typical blog site
* **Flexible**: Allowing us to easily alter the theme taxonomy allows us to scale our unique archive system using issues and categories
* **User-friendly**: In depth CSS style guides will lead to a site that anyone can quickly and easily manuever

We have found all three criteria in JeffProd.

Check out JeffProd's repository [Here!](https://github.com/Tazeg/hugo-blog-jeffprod/tree/bbe726e57038b97df811731330fe2c35f5043964)

## Modifications to the Theme


Our Newspaper has been regularly publishing physical newspapers since 1912. In transitioning the newspaper online, our goal was to accomodate the same file structure that has been used for over 100 years. To do this, we needed to create issues and categories taxonomies. We also changed the heading for articles so it would show the author's name and position.

### Support for issues

We publish almost every week of the school year. Each time we publish, the collection of articles is referred to as an Issue. To refer to a specific issue we must also include the year it was published as issue numbers restart at the beginning of every calendar year.

JeffProd already accomodates archives and tags; yet to build am issues taxonomy we must make four changes in our code. 

1. config.toml : This defines issue within the taxonomy.

```r
[taxonomies]
    tag = "tags"
    issue = "issues"
    archive = "archives"
    category = "categories"
```

2. Archetypes/post.md : We must add issues into the post archetype, so that the number is generated into the YAML frontmatter.

```r
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
month: {{ .Month }}
archives: "{{ dateFormat "2006" now }}"
issues: "{{ dateFormat "2006" now }}-{{ dateFormat "January" now }}"
tags: []
author: John SMITH
banner: ""
---
```

3. Layouts/issues/list.html : This creates a list of all the articles inside an issue. 

4. layout/Partials/widget-issues.html : This will create an Issue card on the side of the page. Any issues published on the website will appear. 

```r
<div class="card">
    <div class="card-content">
        <h1 class="title is-5">Issues</h1>
        {{ range $name, $taxonomy := .Site.Taxonomies.issues }}
            <span class="tag"><a href="{{ "issues" | absURL }}/{{ $name | urlize }}">Issue {{ $name }}</a></span>
        {{ end }}
    </div>
</div>
```

5. layout/Taxonomy/issue.html : This creates the landing page when trying to veiw all of the articles inside and issue. 


### Support for categories

Similar to our physical newpaper, every article is assigned to a specific page, or category. For example, an article about baseball will fall under the Sports category. Other categories include: News, Features, Arts & Entertainment, Opinion, and Backpage. The ability to easily switch categories is a crucial part of the reader's experience, which is why we decided to include each category in our header's menue bar. 

1. config.toml : Define a category inside the site taxonomy.

```r
[taxonomies]
    tag = "tags"
    issue = "issues"
    archive = "archives"
    category = "categories"
```

2. layouts/taxonomy/category : This .html document creates a landing page for any user that wants to look at all of the posts inside a specific category.


3. layouts/partials/header.html : This adds each category into the headers' main menue bar with a link to each page. 

```r 
<nav class="navbar is-fixed-top" role="navigation" aria-label="main navigation">
        <div class="navbar-brand">
            <a class="navbar-item" href="{{ .Site.BaseURL | absURL }}">Home</a>
            <a class="navbar-item" href="{{ "categories/news" | absURL }}">News</a>
            <a class="navbar-item" href="{{ "categories/sports" | absURL }}">Sports</a>
            <a class="navbar-item" href="{{ "categories/features" | absURL }}">Features</a>
            <a class="navbar-item" href="{{ "categories/arts&entertainment" | absURL }}">Arts & Entertainment</a>
            <a class="navbar-item" href="{{ "categories/opinon" | absURL }}">Opinion</a>
            <a class="navbar-item" href="{{ "categories/backpage" | absURL }}">BackPage</a>
            <a class="navbar-item" href="{{ "about" | absURL }}">About</a>
        </div>
    </nav>
```

## Article Heading

To add the title, author, and author position to an article, we had to alter the code in layouts/default/single.html. Specifically, I added the following code. I will publish the article title as a header. In a new line we see the word "By", the authors name, a ",", followed by author's position in italics. The cool part is that if the article doesnt have an author or position parameter, then the div tag is skipped. This is done using to if commands.


```go
   <div class="title">
                {{ .Title }}
            </div>
            <div>
                {{ if .Params.Author }}
                By {{ .Params.Author }}{{if .Params.Position }}, <i>{{ .Params.Position }}</i>
                {{end}}
                {{end}}
            </div>
            <div class="content">
                {{ .Content }}
            </div>
```



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

## To do List

There are a few things that we would like to further explore:

* I would like to create an admin dashboard using Forestry.io. This would allow Page Editors to upload articles for each Copy Editor to edit and save inside the website. Once all edits have been made, they can submit them for approval.

* A Search Bar would be great, because then users could search for a specific article, author, tag, category, issue etc. It would greatly increase our userfriendly-ness.

* On pages that show a list of articles, i.e. the home page, category pages, etc., I would like to show a Thumbnail of the article's picture if there is one. 

* I would like to give our followers the opportunity to subscribe to a weekly email.

* We need to add the ability to sort articles by author. This would allow people to read all of the articles written by a specific author.

* The taxonomy issues won't open a page. We haven't had enough time to fix this, so we would definitely get that sorted out.


