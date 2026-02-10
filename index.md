---
layout: default
title: Inicio
---

<div class="home-grid-layout">

  <div class="home-main-column">
    
    <section class="featured-story">
      <p class="section-label">Análisis de Coyuntura</p>
      <h1 class="main-headline">Soberanía en Tiempos de Crisis: El Reto Nacional</h1>
      <p class="lead-text">
        Nuestra apuesta no es técnica, es política. La libertad de la nación depende de nuestra capacidad para decidir sobre nuestros recursos y nuestra tecnología.
      </p>
      <a href="/coyuntura" class="read-more">Leer investigación completa →</a>
    </section>

    <hr class="double-divider">

    <section>
      <h3 class="column-title">Pulso de la Nación (Cifras)</h3>
      <div class="data-dashboard">
        <div class="data-card">
          <h4>Soberanía Alimentaria</h4>
          <div class="data-value">55<span>%</span></div>
          <p>De los alimentos básicos en Colombia siguen siendo importados.</p>
        </div>
        <div class="data-card">
          <h4>Acceso Digital</h4>
          <div class="data-value">2.5<span>min</span></div>
          <p>Es el tiempo promedio de carga en zonas rurales del país.</p>
        </div>
      </div>
    </section>

  </div>

  <aside class="home-sidebar">
    <h3 class="sidebar-title">📢 Últimos Cacareos</h3>

    {% for post in site.cacareos limit:5 %}
      <div class="sidebar-card">
        <div class="meta">#{{ post.number }} | {{ post.date | date: "%d/%m" }}</div>
        <h4><a href="{{ post.url }}">{{ post.title }}</a></h4>
      </div>
    {% endfor %}

    <div style="margin-top: 20px; text-align: center;">
      <a href="/cacareos" style="font-size: 0.8rem; font-weight: 700; color: #63055d; text-decoration: none;">Ver historial completo →</a>
    </div>
  </aside>

</div>
