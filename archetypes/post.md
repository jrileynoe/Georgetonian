---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
month: {{ .Month }}
archives: "{{ dateFormat "2006" now }}"
issues: "{{ dateFormat "2006" now }}-{{ dateFormat "January" now }}"
tags: []
author: John SMITH
---
