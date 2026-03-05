---
layout: post
title: "Portal de Denuncia Ciudadana: Elecciones 8 de Marzo"
permalink: /denuncias/
description: "Canal seguro y 100% anónimo para reportar irregularidades electorales en Colombia."
---

<div class="post-content is-cacareo" markdown="1">

### 🛡️ Protege la Democracia con Seguridad
Este espacio ha sido diseñado bajo estándares de **soberanía tecnológica**. No recolectamos tu dirección IP, nombre, ni correos electrónicos. La información viaja cifrada directamente a nuestra base de datos en **Google Cloud**.

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
      <input type="text" id="ubicacion" placeholder="Ej: Bogotá - Puesto Corferias" required style="width: 100%; padding: 12px; border: 1px solid #ccc; border-radius: 4px; font-size: 1rem;">
    </div>

    <div style="margin-bottom: 1.5rem;">
      <label style="display: block; font-weight: bold; margin-bottom: 0.5rem; font-family: 'Inter', sans-serif;">Descripción de los hechos</label>
      <textarea id="descripcion" rows="6" placeholder="Describe lo que viste con la mayor precisión posible..." required style="width: 100%; padding: 12px; border: 1px solid #ccc; border-radius: 4px; font-size: 1rem; font-family: 'Inter', sans-serif;"></textarea>
    </div>

    <button type="submit" id="btnEnviar" style="background: #63055d; color: white; padding: 15px 40px; border: none; border-radius: 4px; cursor: pointer; font-weight: bold; font-size: 1.1rem; width: 100%; transition: background 0.3s;">
      ENVIAR REPORTE ANÓNIMO
    </button>
  </form>

  <div id="statusMessage" style="display:none; margin-top: 2rem; padding: 20px; border-radius: 4px; text-align: center; font-weight: bold; font-family: 'Playfair Display', serif;">
  </div>
</div>

---

### Recomendaciones de Seguridad
1. **Anonimato Técnico:** Si vas a describir personas, evita usar nombres propios si no estás seguro; describe situaciones.
2. **Uso de Redes:** Si te encuentras en una zona de riesgo, te sugerimos realizar el reporte usando una conexión de datos móviles en lugar de un Wi-Fi público.
3. **Evidencia:** Por ahora este formulario solo recibe texto. Si tienes fotos o videos, resguárdalos en un lugar seguro; el equipo de **Creamos** podría habilitar canales de recepción multimedia más adelante.

</div>

<script>
document.getElementById('denunciaForm').addEventListener('submit', async (e) => {
  e.preventDefault();
  
  const btn = document.getElementById('btnEnviar');
  const status = document.getElementById('statusMessage');
  const endpoint = 'https://denuncias-electorales-creamos-493669349431.northamerica-south1.run.app';

  // Bloqueo de UI para evitar duplicados
  btn.innerText = 'PROCESANDO REPORTE...';
  btn.disabled = true;
  btn.style.opacity = '0.7';

  const payload = {
    tipo: document.getElementById('tipo').value,
    ubicacion: document.getElementById('ubicacion').value,
    descripcion: document.getElementById('descripcion').value
  };

  try {
    const response = await fetch(endpoint, {
      method: 'POST',
      mode: 'cors',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(payload)
    });

    if (response.ok) {
      document.getElementById('denunciaForm').style.display = 'none';
      status.style.display = 'block';
      status.style.background = '#ffcc29';
      status.style.color = '#63055d';
      status.innerText = '¡Denuncia recibida con éxito! Tu reporte ha sido almacenado de forma segura en nuestra base de datos. Gracias por tu compromiso con la democracia.';
    } else {
      throw new Error('Error en el servidor');
    }
  } catch (error) {
    console.error('Error de envío:', error);
    status.style.display = 'block';
    status.style.background = '#f8d7da';
    status.style.color = '#721c24';
    status.innerText = 'Hubo un problema al enviar el reporte. Por favor, revisa tu conexión e inténtalo de nuevo.';
    btn.disabled = false;
    btn.innerText = 'REINTENTAR ENVÍO ANÓNIMO';
    btn.style.opacity = '1';
  }
});
</script>

<style>
  #btnEnviar:hover {
    background: #4a0346 !important;
  }
  .post-content label {
    color: #333;
  }
</style>
