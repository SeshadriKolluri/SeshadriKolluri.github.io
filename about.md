---
layout: page
title: Notes
permalink: /notes/
---
### Some of my recent notes on various topics, that I am learning or practicing. 

<ul class="post-list">
{% for post in site.posts %}
  <li>
    <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
    <h3>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
    </h3>
    {{ post.excerpt }} 
  </li>
{% endfor %}
</ul>