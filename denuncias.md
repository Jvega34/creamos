---
layout: post
title: "Denuncia Ciudadana: Elecciones 8 de Marzo"
permalink: /denuncias/
---

<div class="post-content is-cacareo" markdown="1">

### 🛡️ Espacio de Denuncia Segura
Este portal ha sido diseñado para reportar irregularidades de forma **estrictamente anónima**. Los datos son almacenados en nuestra propia infraestructura de datos.

<form id="denunciaForm" style="max-width: 600px; margin: 2rem 0;">
  <label>Tipo de Irregularidad</label>
  <select id="tipo" required style="width: 100%; margin-bottom: 1rem; padding: 10px;">
    <option value="compra_votos">Compra de votos</option>
    <option value="constreñimiento">Constreñimiento al elector</option>
    <option value="trashumancia">Trasteo de votos (Trashumancia)</option>
    <option value="otros">Otros delitos electorales</option>
  </select>

  <label>Municipio / Puesto de Votación</label>
  <input type="text" id="ubicacion" placeholder="Ej: Bogotá - Unicentro" required style="width: 100%; margin-bottom: 1rem; padding: 10px;">

  <label>Descripción de los hechos</label>
  <textarea id="descripcion" rows="5" required style="width: 100%; margin-bottom: 1rem; padding: 10px;"></textarea>

  <button type="submit" id="btnEnviar" style="background: #63055d; color: white; padding: 15px 30px; border: none; cursor: pointer; font-weight: bold;">
    ENVIAR DENUNCIA ANÓNIMA
  </button>
</form>

<div id="mensaje" style="display:none; padding: 20px; background: #ffcc29; font-weight: bold;"></div>

<script>
document.getElementById('denunciaForm').addEventListener('submit', async (e) => {
  e.preventDefault();
  const btn = document.getElementById('btnEnviar');
  btn.innerText = 'PROCESANDO...';
  btn.disabled = true;

  const data = {
    tipo: document.getElementById('tipo').value,
    ubicacion: document.getElementById('ubicacion').value,
    descripcion: document.getElementById('descripcion').value
  };

  try {
    const response = await fetch('TU_URL_DE_CLOUD_FUNCTION', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(data)
    });

    if (response.ok) {
      document.getElementById('denunciaForm').style.display = 'none';
      const msg = document.getElementById('mensaje');
      msg.style.display = 'block';
      msg.innerText = '¡Denuncia registrada con éxito! Gracias por proteger la democracia.';
    }
  } catch (error) {
    alert('Error al enviar. Inténtalo de nuevo.');
    btn.disabled = false;
    btn.innerText = 'ENVIAR DENUNCIA ANÓNIMA';
  }
});
</script>

</div>
