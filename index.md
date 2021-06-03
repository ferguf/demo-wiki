---
title: "Lumen Documentation Architecture and Engineering"
keywords: sample homepage
tags: [getting_started]
sidebar: mydoc_sidebar
toc: false
permalink: index.html
summary: The Home for all Lumen Technical Documentation for IP , Transport, Metro , Voice and Access networks. The home for Technology Update Notifications(TUNs) , High Level Designs (HLDs), Low Level Designs (LLDs), Device Configuration Templates (DCTs) and Service Configuration Template (SCTs).
---

{% include note.html content=" [Start here](mydoc_getting_started.html) for a overview of how to get started on the Technical documentation journey" %}

# Latest Publications

## TUNs

<ul >
    {% for post in site.posts limit:5 %}
    <li><a href="{{post.url | remove: '/'}}">{{post.title}}</a></li>
        {{ post.summary }}<br>
    {% endfor %}
</ul>

## HLDs

<ul >
{% assign sorted = site.hld | sort: 'date' |reverse %}
    {% for post in sorted limit:5 %}
    <li><a href="{{post.url | remove: '/'}}">{{post.title}}</a></li>
        {{ post.summary }}<br>
    {% endfor %}
</ul>

## LLDs


{% include links.html %}
