---
layout: post
title: "Portal de Denuncia Ciudadana: Elecciones 8 de Marzo"
permalink: /denuncias/
description: "Canal seguro y 100% anónimo para reportar irregularidades electorales con evidencia multimedia."
---

<div class="post-content is-cacareo" markdown="1">

### 🛡️ Tu reporte es vital para la democracia
Este canal es **totalmente anónimo**. No rastreamos tu identidad. La información y evidencia multimedia viajan directamente a los servidores de **Creamos** bajo estrictos protocolos de seguridad.

<div class="denuncia-wrapper" style="background: #f9f9f9; padding: 2rem; border-radius: 8px; border: 1px solid #eee; margin: 2rem 0;">
  
  <form id="denunciaForm">
    <div style="margin-bottom: 1.5rem;">
      <label style="display: block; font-weight: bold; margin-bottom: 0.5rem; font-family: 'Inter', sans-serif;">Tipo de Irregularidad</label>
      <select id="tipo" required style="width: 100%; padding: 12px; border: 1px solid #ccc; border-radius: 4px; font-size: 1rem;">
        <option value="" disabled selected>Selecciona una opción...</option>
        <option value="compra_votos">Compra de votos / Ofrecimiento de dinero</option>
        <option value="constreñimiento">Constreñimiento al elector (Amenazas)</option>
        <option value="trashumancia">Trasteo de votos (Trashumancia)</option>
        <option value="publicidad_ilegal">Publicidad ilegal en puestos de votación</option>
        <option value="otros">Otros delitos electorales</option>
      </select>
    </div>

    <div style="margin-bottom: 1.5rem;">
      <label style="display: block; font-weight: bold; margin-bottom: 0.5rem; font-family: 'Inter', sans-serif;">Ubicación (Municipio y Puesto de Votación)</label>
      <input type="text" id="ubicacion" placeholder="Ej: Bogotá - Unicentro" required style="width: 100%; padding: 12px; border: 1px solid #ccc; border-radius: 4px; font-size: 1rem;">
    </div>

    <div style="margin-bottom: 1.5rem;">
      <label style="display: block; font-weight: bold; margin-bottom: 0.5rem; font-family: 'Inter', sans-serif;">Descripción de lo sucedido</label>
      <textarea id="descripcion" rows="4" placeholder="Describe los hechos..." required style="width: 100%; padding: 12px; border: 1px solid #ccc; border-radius: 4px; font-size: 1rem; font-family: 'Inter', sans-serif;"></textarea>
    </div>

    <div style="margin-bottom: 2rem;">
      <label style="display: block; font-weight: bold; margin-bottom: 0.5rem; font-family: 'Inter', sans-serif;">Adjuntar Foto o Video (Opcional - Máx 10MB)</label>
      <input type="file" id="archivo" accept="image/*,video/*" style="width: 100%; padding: 10px; border: 1px dashed #63055d; border-radius: 4px; background: #fff;">
    </div>

    <button type="submit" id="btnEnviar" style="background: #63055d; color: white; padding: 15px 40px; border: none; border-radius: 4px; cursor: pointer; font-weight: bold; font-size: 1.1rem; width: 100%;">
      ENVIAR REPORTE ANÓNIMO
    </button>
  </form>

  <div id="statusMessage" style="display:none; margin-top: 2rem; padding: 20px; border-radius: 4px; text-align: center; font-weight: bold; font-family: 'Playfair Display', serif;">
  </div>
</div>

</div>

<script>
document.getElementById('denunciaForm').addEventListener('submit', async (e) => {
  e.preventDefault();
  
  const btn = document.getElementById('btnEnviar');
  const status = document.getElementById('statusMessage');
  const fileInput = document.getElementById('archivo');
  const endpoint = 'https://denuncias-electorales-creamos-493669349431.northamerica-south1.run.app';

  if (fileInput.files.length > 0 && fileInput.files[0].size > 10 * 1024 * 1024) {
    alert('El archivo es demasiado grande (máximo 10MB).');
    return;
  }

  btn.innerText = 'ENVIANDO REPORTE...';
  btn.disabled = true;

  const formData = new FormData();
  formData.append('tipo', document.getElementById('tipo').value);
  formData.append('ubicacion', document.getElementById('ubicacion').value);
  formData.append('descripcion', document.getElementById('descripcion').value);
  
  if (fileInput.files[0]) {
    formData.append('archivo', fileInput.files[0]);
  }

  try {
    const response = await fetch(endpoint, {
      method: 'POST',
      mode: 'cors',
      body: formData
    });

    if (response.ok) {
      document.getElementById('denunciaForm').style.display = 'none';
      status.style.display = 'block';
      status.style.background = '#ffcc29';
      status.style.color = '#63055d';
      status.innerText = '¡Denuncia recibida con éxito! Gracias por tu valentía y compromiso.';
    } else {
      throw new Error('Error en el servidor');
    }
  } catch (error) {
    console.error('Error:', error);
    status.style.display = 'block';
    status.style.background = '#f8d7da';
    status.style.color = '#721c24';
    status.innerText = 'Hubo un error al enviar. Por favor, verifica tu conexión e inténtalo de nuevo.';
    btn.disabled = false;
    btn.innerText = 'REINTENTAR ENVÍO';
  }
});
</script>
