---
layout: post
title: "Portal de Denuncia Ciudadana: Elecciones 8 de Marzo"
permalink: /denuncias/
description: "Canal seguro y 100% anónimo para reportar irregularidades electorales con evidencia multimedia."
---

<div class="post-content is-cacareo" markdown="1">

### 🛡️ Protege la Democracia con Evidencia Real
Este portal permite reportar irregularidades de forma **estrictamente anónima**. Ahora puedes adjuntar fotos o videos cortos para respaldar tu denuncia. Los datos se almacenan en la infraestructura privada de **Creamos** en Google Cloud.

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
      <input type="text" id="ubicacion" placeholder="Ej: Bogotá - Corferias" required style="width: 100%; padding: 12px; border: 1px solid #ccc; border-radius: 4px; font-size: 1rem;">
    </div>

    <div style="margin-bottom: 1.5rem;">
      <label style="display: block; font-weight: bold; margin-bottom: 0.5rem; font-family: 'Inter', sans-serif;">Descripción de los hechos</label>
      <textarea id="descripcion" rows="4" placeholder="Describe lo sucedido..." required style="width: 100%; padding: 12px; border: 1px solid #ccc; border-radius: 4px; font-size: 1rem; font-family: 'Inter', sans-serif;"></textarea>
    </div>

    <div style="margin-bottom: 1.5rem;">
      <label style="display: block; font-weight: bold; margin-bottom: 0.5rem; font-family: 'Inter', sans-serif;">Adjuntar Evidencia (Opcional - Máx 10MB)</label>
      <input type="file" id="archivo" accept="image/*,video/*" style="width: 100%; padding: 10px; background: #fff; border: 1px dashed #63055d; border-radius: 4px;">
      <small style="color: #666;">Formatos permitidos: JPG, PNG, MP4. Máximo 10MB.</small>
    </div>

    <button type="submit" id="btnEnviar" style="background: #63055d; color: white; padding: 15px 40px; border: none; border-radius: 4px; cursor: pointer; font-weight: bold; font-size: 1.1rem; width: 100%; transition: background 0.3s;">
      ENVIAR REPORTE ANÓNIMO
    </button>
  </form>

  <div id="statusMessage" style="display:none; margin-top: 2rem; padding: 20px; border-radius: 4px; text-align: center; font-weight: bold; font-family: 'Playfair Display', serif;">
  </div>
</div>

---

### Seguridad y Privacidad
1. **Anonimato de Archivos:** Al subir fotos, el sistema las procesa para romper vínculos con tu dispositivo.
2. **Uso de Datos:** La evidencia será analizada exclusivamente para el control social de la jornada electoral del 8 de marzo.
3. **Recomendación:** Si estás en un lugar con poca señal, evita subir videos pesados para asegurar que el reporte de texto llegue correctamente.

</div>

<script>
document.getElementById('denunciaForm').addEventListener('submit', async (e) => {
  e.preventDefault();
  
  const btn = document.getElementById('btnEnviar');
  const status = document.getElementById('statusMessage');
  const fileInput = document.getElementById('archivo');
  
  // URL de tu función en la región de México
  const endpoint = 'https://denuncias-electorales-creamos-493669349431.northamerica-south1.run.app';

  // Validación de tamaño de archivo (10MB)
  if (fileInput.files.length > 0 && fileInput.files[0].size > 10 * 1024 * 1024) {
    alert('El archivo supera el límite de 10MB. Por favor sube uno más liviano.');
    return;
  }

  btn.innerText = 'SUBIENDO EVIDENCIA...';
  btn.disabled = true;
  btn.style.opacity = '0.7';

  // Usamos FormData para permitir el envío del archivo multimedia
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
      body: formData // No necesita headers de Content-Type, el navegador los pone automáticamente para FormData
    });

    if (response.ok) {
      document.getElementById('denunciaForm').style.display = 'none';
      status.style.display = 'block';
      status.style.background = '#ffcc29';
      status.style.color = '#63055d';
      status.innerText = '¡Denuncia y evidencia recibidas con éxito! Gracias por proteger la transparencia electoral.';
    } else {
      throw new Error('Fallo en el servidor');
    }
  } catch (error) {
    console.error('Error:', error);
    status.style.display = 'block';
    status.style.background = '#f8d7da';
    status.style.color = '#721c24';
    status.innerText = 'Error al enviar. Por favor verifica tu conexión e intenta de nuevo.';
    btn.disabled = false;
    btn.innerText = 'REINTENTAR ENVÍO';
    btn.style.opacity = '1';
  }
});
</script>

<style>
  #btnEnviar:hover { background: #4a0346 !important; }
  .post-content label { color: #333; }
</style>
