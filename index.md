---
layout: default
title: Inicio
---

{% assign latest_post = site.posts.first %}
<section class="featured-story">
  <p class="section-label">Análisis Destacado</p>
  <h1 class="main-headline">
    <a href="{{ latest_post.url }}" style="text-decoration:none; color:inherit;">{{ latest_post.title }}</a>
  </h1>
  <p class="lead-text">{{ latest_post.description }}</p>
  <a href="{{ latest_post.url }}" class="read-more-link">Leer investigación completa →</a>
</section>

<hr class="double-divider">

<section class="data-dashboard">
  <div class="column-title">Pulso de la Nación (Cifras Clave)</div>
  <div class="home-grid">
    <div class="data-card">
      <span class="badge">TRABAJO</span>
      <h3>55%</h3>
      <p>Tasa de informalidad laboral en Colombia al cierre de 2025.</p>
    </div>
    <div class="data-card">
      <span class="badge">SALUD</span>
      <h3>2.5 min</h3>
      <p>Frecuencia con la que se radica una tutela por derecho a la salud.</p>
    </div>
    <div class="data-card">
      <span class="badge">AMBIENTE</span>
      <h3>2.8x</h3>
      <p>Calidad del aire por encima del límite de la OMS.</p>
    </div>
  </div>
</section>

<hr class="double-divider">

<section class="recent-feed">
  <div class="column-title">Últimas Investigaciones</div>
  <div class="home-grid">
    {% for post in site.posts offset:1 limit:2 %}
    <div class="feed-column">
      <article class="feed-item-small">
        <span class="post-category" style="font-size: 0.6rem;">{{ post.category | capitalize }}</span>
        <h2 class="feed-title-small">
          <a href="{{ post.url }}">{{ post.title }}</a>
        </h2>
        <p class="feed-excerpt-small">{{ post.description | truncate: 120 }}</p>
      </article>
    </div>
    {% endfor %}
  </div>
</section>

<div class="home-quote" style="text-align: center; border-left: none; border-top: 1px solid #63055d; padding-top: 20px;">
  "¡Que no se apague la esperanza. De nuevo amanece, y el gallo vuelve a cantar!"
</div>
