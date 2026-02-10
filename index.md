---
layout: default
title: Inicio
---

<div class="home-grid-layout">

  <div class="main-column">
    <section class="featured-story">
      <p style="color: #63055d; font-weight: 700; text-transform: uppercase; font-size: 0.8rem;">Análisis Destacado</p>
      <h1 style="font-family: 'Playfair Display', serif; font-size: 2.5rem; margin-top: 10px;">Soberanía en Tiempos de Crisis: El Reto Nacional</h1>
      <p>Nuestra apuesta no es técnica, es política. La libertad de la nación depende de nuestra capacidad para decidir sobre nuestros recursos y nuestra tecnología.</p>
      <a href="/coyuntura" style="font-weight: 700; color: #63055d;">Leer investigación completa →</a>
    </section>

    <hr style="border: 0; border-top: 1px solid #eee; margin: 40px 0;">

    <section>
      <h3 style="font-family: 'Playfair Display', serif;">Pulso de la Nación (Cifras)</h3>
      <div class="data-dashboard">
        <div class="data-card">
          <h4>Soberanía Alimentaria</h4>
          <div class="data-value">55%</div>
          <p>De los alimentos básicos en Colombia son importados.</p>
        </div>
        <div class="data-card">
          <h4>Acceso Digital</h4>
          <div class="data-value">2.5 min</div>
          <p>Tiempo de carga promedio en zonas rurales.</p>
        </div>
      </div>
    </section>
  </div>

 <aside class="home-sidebar">
  <h3 class="sidebar-title">📢 Últimos Cacareos</h3>

  {% assign cacareos_ordenados = site.cacareos | sort: 'date' | reverse %}

  {% for post in cacareos_ordenados limit:5 %}
    <div class="sidebar-card">
      <div style="font-size: 0.7rem; font-weight: 700; color: #666;">
        #{{ post.number }} | {{ post.date | date: "%d/%m/%y" }}
      </div>
      <h4><a href="{{ post.url }}">{{ post.title }}</a></h4>
    </div>
  {% endfor %}

  <a href="/cacareos" style="display: block; margin-top: 20px; font-size: 0.8rem; font-weight: 700; color: #63055d; text-decoration: none;">
    Ver historial completo →
  </a>
</aside>

</div>
