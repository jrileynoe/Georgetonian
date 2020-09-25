---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
archives: "{{ dateFormat "2006" now }}"
issues: {{ dateFormat "January 2006" now }}
tags: []
author: John SMITH
position: Staff Writer
categories: Sports
---
