---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
summary: "{{ replace .Name "-" " " | title }}"
slides: "/presentation/{{.Name}}"
---