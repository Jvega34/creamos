---
layout: default
title: Explorar por Temas
permalink: /temas/
---

# Navegación por Ejes Temáticos

<div class="tags-archive">
  {% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
  {% assign sorted_tags = site_tags | split: ',' | sort %}
  
  {% for tag in sorted_tags %}
    <section id="{{ tag | slugify }}" style="margin-bottom: 50px;">
      <h2 style="border-bottom: 2px solid #63055d; color: #63055d; padding-bottom: 5px;">{{ tag }}</h2>
      <ul style="list-style: none; padding-left: 0;">
        {% for post in site.tags[tag] %}
          <li style="margin: 15px 0; border-bottom: 1px solid #eee; padding-bottom: 10px;">
            <span style="font-size: 0.8rem; color: #666;">{{ post.date | date: "%d/%m/%Y" }}</span> — 
            <a href="{{ post.url }}" style="font-weight: 700; text-decoration: none; color: #111;">{{ post.title }}</a>
            <span style="font-size: 0.7rem; text-transform: uppercase; margin-left: 10px; color: #63055d;">[{{ post.category }}]</span>
          </li>
        {% endfor %}
      </ul>
    </section>
  {% endfor %}
</div>
