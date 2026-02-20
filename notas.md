---
layout: default
title: "Notas, Crónicas y Opinión"
permalink: /notas/
---

<div class="category-header">
  <p class="section-label">Investigación, Memoria y Pensamiento</p>
  <h1 class="category-title">Notas, Crónicas y Opinión</h1>
  <p class="category-description">
    Un espacio para la profundidad: relatos de memoria, crónicas desde el territorio y reflexiones técnicas para la soberanía.
  </p>
</div>

<hr class="double-divider">

<div class="analysis-feed">
  {% assign entradas = site.notas | sort: 'date' | reverse %}
  {% for doc in entradas %}
    <article class="feed-item">
      <div class="feed-metadata">
        <span class="feed-date">{{ doc.date | date: "%e de %B, %Y" | 
          replace: "January", "Enero" | replace: "February", "Febrero" | replace: "March", "Marzo" | 
          replace: "April", "Abril" | replace: "May", "Mayo" | replace: "June", "Junio" | 
          replace: "July", "Julio" | replace: "August", "Agosto" | replace: "September", "Septiembre" | 
          replace: "October", "Octubre" | replace: "November", "Noviembre" | replace: "December", "Diciembre" 
        }}</span>
      </div>
      
      <h2 class="feed-title">
        <a href="{{ doc.url | relative_url }}">{{ doc.title }}</a>
      </h2>
      
      <p class="feed-excerpt">{{ doc.description | default: doc.excerpt | strip_html | truncatewords: 35 }}</p>
      
      <a href="{{ doc.url | relative_url }}" class="read-more-link">Continuar leyendo →</a>
    </article>
    <hr class="light-divider">
  {% else %}
    <p>Estamos preparando nuestras primeras crónicas. Vuelve pronto.</p>
  {% endfor %}
</div>
