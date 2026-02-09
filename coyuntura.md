---
layout: default
title: Análisis de Coyuntura
---

<div class="category-header">
  <p class="section-label">Archivo de Investigaciones</p>
  <h1 class="category-title">Coyuntura Nacional</h1>
  <p class="category-description">Análisis técnico y político sobre la realidad colombiana, procesado desde nuestro laboratorio de datos.</p>
</div>

<hr class="double-divider">

<div class="analysis-feed">
  {% for post in site.categories.coyuntura %}
    <article class="feed-item">
      <div class="feed-metadata">
        <span class="feed-date">{{ post.date | date: "%e de %B, %Y" | replace: "January", "Enero" | replace: "February", "Febrero" | replace: "March", "Marzo" | replace: "April", "Abril" | replace: "May", "Mayo" | replace: "June", "Junio" | replace: "July", "Julio" | replace: "August", "Agosto" | replace: "September", "Septiembre" | replace: "October", "Octubre" | replace: "November", "Noviembre" | replace: "December", "Diciembre" }}</span>
        {% if post.tags %}
          <span class="feed-tags">| {% for tag in post.tags %} #{{ tag }} {% endfor %}</span>
        {% endif %}
      </div>
      
      <h2 class="feed-title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h2>
      
      <p class="feed-excerpt">{{ post.description | default: "Haz clic para leer el análisis detallado de este informe." }}</p>
      
      <a href="{{ post.url | relative_url }}" class="read-more-link">Leer investigación completa →</a>
    </article>
    <hr class="light-divider">
  {% else %}
    <p>Próximamente publicaremos nuevos análisis en esta sección.</p>
  {% endfor %}
</div>
