---
title: {{ $term := index ( split .File.Dir "/") 1 }}"{{ replace $term "-" " " | title }}"
description: "This is the description for the {{ $term | title }} series"
date: {{ .Date }}
draft: false
---