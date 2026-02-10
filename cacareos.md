---
layout: default
title: "Archivo de Cacareos"
permalink: /cacareos/
---

<div class="category-header" style="text-align: center; margin-bottom: 40px;">
  <p style="color: #63055d; font-weight: 700; text-transform: uppercase; font-size: 0.9rem; margin-bottom: 10px;">Comunicaciones Semanales</p>
  <h1 style="font-family: 'Playfair Display', serif; font-size: 3rem; margin-top: 0;">El Cacareo</h1>
  <p style="max-width: 600px; margin: 0 auto; color: #666; font-style: italic;">
    Nuestra cadena semanal de análisis rápido, temas diversos y formación popular. Palabra directa desde el territorio.
  </p>
</div>

<hr style="border: 0; border-top: 2px solid #ffcc29; width: 80px; margin: 0 auto 50px;">

<div class="cacareos-archive-list" style="max-width: 800px; margin: 0 auto;">
  {% assign cacareos_ordenados = site.cacareos | sort: 'date' | reverse %}
  {% for post in cacareos_ordenados %}
    <article style="margin-bottom: 30px; padding: 20px; border: 1px solid #eee; border-left: 5px solid #63055d; background: #fdfdfd; border-radius: 4px;">
      <div style="font-size: 0.75rem; font-weight: 700; color: #666; text-transform: uppercase; margin-bottom: 8px;">
        Cacareo #{{ post.number }} | {{ post.date | date: "%d de %B, %Y" | 
          replace: "January", "Enero" | replace: "February", "Febrero" | 
          replace: "March", "Marzo" | replace: "April", "Abril" | 
          replace: "May", "Mayo" | replace: "June", "Junio" | 
          replace: "July", "Julio" | replace: "August", "Agosto" | 
          replace: "September", "Septiembre" | replace: "October", "Octubre" | 
          replace: "November", "Noviembre" | replace: "December", "Diciembre" 
        }}
      </div>
      <h2 style="font-family: 'Playfair Display', serif; margin: 0; font-size: 1.6rem;">
        <a href="{{ post.url }}" style="text-decoration: none; color: #111;">{{ post.title }}</a>
      </h2>
      <p style="margin-top: 10px; color: #444;">{{ post.description }}</p>
      <a href="{{ post.url }}" style="font-size: 0.85rem; font-weight: 700; color: #63055d; text-decoration: none;">Seguir leyendo →</a>
    </article>
  {% endfor %}
</div>
