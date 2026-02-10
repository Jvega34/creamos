---
layout: default
title: Inicio
---

<div class="home-grid-layout">

  <div class="main-column">
    <section class="latest-posts">
      <h2 style="font-family: 'Playfair Display', serif; font-size: 1.8rem; color: #63055d; border-bottom: 3px solid #ffcc29; display: inline-block; padding-bottom: 5px; margin-bottom: 30px;">
        ÚLTIMAS ENTRADAS
      </h2>

      {% for post in site.posts limit:3 %}
      <article class="featured-story" style="margin-bottom: 40px;">
        <p style="color: #666; font-weight: 700; text-transform: uppercase; font-size: 0.75rem; margin-bottom: 5px;">
          {{ post.date | date: "%d/%m/%Y" }} | {{ post.categories | join: ", " }}
        </p>
        <h3 style="font-family: 'Playfair Display', serif; font-size: 2.2rem; margin-top: 0; line-height: 1.1;">
          <a href="{{ post.url }}" style="text-decoration: none; color: #111;">{{ post.title }}</a>
        </h3>
        <p style="font-size: 1.1rem; color: #444;">
          {{ post.excerpt | strip_html | truncatewords: 30 }}
        </p>
        <a href="{{ post.url }}" style="font-weight: 700; color: #63055d; text-decoration: none; border-bottom: 2px solid #ffcc29;">
          Leer investigación completa →
        </a>
      </article>
      {% if forloop.last == false %}
        <hr style="border: 0; border-top: 1px solid #eee; margin: 30px 0;">
      {% endif %}
      {% endfor %}
    </section>

    <section style="margin-top: 50px;">
      <h3 style="font-family: 'Playfair Display', serif; font-size: 1.5rem;">Pulso de la Nación (Cifras)</h3>
      <div class="data-dashboard">
        <div class="data-card">
          <h4>Soberanía Alimentaria</h4>
          <div class="data-value">55%</div>
          <p>Alimentos básicos importados.</p>
        </div>
        <div class="data-card">
          <h4>Acceso Digital</h4>
          <div class="data-value">2.5 min</div>
          <p>Tiempo de carga en zonas rurales.</p>
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
          #{{ post.number }} | {{ post.date | date: "%d/%m" }}
        </div>
        <h4><a href="{{ post.url }}" style="text-decoration: none; color: #111;">{{ post.title }}</a></h4>
      </div>
    {% endfor %}
    <a href="/cacareos" style="display: block; margin-top: 20px; font-size: 0.8rem; font-weight: 700; color: #63055d; text-decoration: none;">
      Ver historial completo →
    </a>
  </aside>

</div>
